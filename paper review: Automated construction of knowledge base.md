## Over view: tasks in KB construction and their correspondence with human's cognitive processes

[caption id="attachment_99" align="alignnone" width="660"]<img src="http://www.geekwei.com/wp-content/uploads/2017/07/Screen-Shot-2017-07-09-at-1.43.07-PM-1024x508.png" alt="" width="660" height="327" class="size-large wp-image-99" /> automated construction of KB and in terms of human cognition...[/caption]

A good review of the field is:
> M. Nickel et al., “A Review of Relational Machine Learning for Knowledge Graphs,” Proceedings of the IEEE 104, no. 1 (January 2016): 11–33, doi:10.1109/JPROC.2015.2483592.



## never-ending language learning (NELL)
>Tom M. Mitchell et al., “Never Ending Learning.,” in AAAI, 2015, 2302–2310, [link](http://www.aaai.org/ocs/index.php/AAAI/AAAI15/paper/download/10049/9557).
>Andrew Carlson et al., “Toward an Architecture for Never-Ending Language Learning.,” in AAAI, vol. 5, 2010, 3, [link](https://www.cs.cmu.edu/afs/cs.cmu.edu/Web/People/acarlson/papers/carlson-aaai10.pdf).
### what can it do?
<img src="http://www.geekwei.com/wp-content/uploads/2017/07/Screen-Shot-2017-07-09-at-1.45.51-PM.png" alt="" width="1202" height="658" class="alignnone size-full wp-image-100" />

example of each task:

+ lexical pattern and contexts-- Coupled Pattern Learner (CPL); OpenEval
Eg1: hearts full of X => X isA emotion; X ranks second in Y => relation (X teamPlaysInLeague Y) 
Eg2: context includes vitamin => apple is a fruit (not company)

+ learn new ontology (category and relation) -- OntExt
Eg:  for the category pair ⟨drug,disease⟩, the sentence *Prozac may cause migraines* might be extracted. New relations such as DrugHasSideEffect(x,y) can then be learnt.

+ confidence in knowledge -- Knowledge Integrator (KI)
Eg: a piece of knowledge will be rated as reliable either from high confidence from one source, or medium-confidence but has been proposed by multiple sources 

+ infer new relations -- NFOIL(in 2010 NELL) or Path Ranking Algorithm (PRA, in 2015 NELL)
Eg1, athleteInLeague(X , NBA) => athletePlaysSport(X , basketball); 
Eg2,  cityCapitalOfState(X , Y ), cityInCountry(X , USA) => cityInState(X , Y ).

+ active inquiry 
Eg1 Coupled SEAL (CSEAL): given *sparrow, swan and kingbird" are instances of "bird", search for html pages with tables including those seed instances, and infer other items in the table as instances of "bird".

### data
+ NELL knowledge base [browser](http://rtw.ml.cmu.edu/rtw/kbbrowser/), including all the facts as well as the confidence. Both categories and relations are organized in some tree structure (*manually set or automatically learnt*?).
+ rule learning [process](http://rtw.ml.cmu.edu/aaai10_online/rule_stats.txt) in 2010 NELL 

## Tensor Factorization (RESCAL)
Maximilian Nickel, Volker Tresp, and Hans-Peter Kriegel, “Factorizing Yago: Scalable Machine Learning for Linked Data,” in Proceedings of the 21st International Conference on World Wide Web (ACM, 2012), 271–280, [link](http://dl.acm.org/citation.cfm?id=2187874).

M. Nickel et al., “A Review of Relational Machine Learning for Knowledge Graphs,” Proceedings of the IEEE 104, no. 1 (January 2016): 11–33, doi:10.1109/JPROC.2015.2483592.

### What can it do?
<img src="http://www.geekwei.com/wp-content/uploads/2017/07/Screen-Shot-2017-07-09-at-1.47.34-PM.png" alt="" width="1040" height="286" class="alignnone size-full wp-image-101" />

Note: this is an algorithm that factorizes triplets (x-Relation-y) with latent variable model and compute the likelihood that this triplet being true. Thus, there's a large space of possible scenarios.

Experiments that the authors have mentioned include:

+ infer the "type-of" link by other link structures ("link prediction experiment"). 
Eg: deleting all the information in KB about "x" isTypeof "Location" but keep other relations; then ask "Washington square" isTypeof what? //these are my understanding...not sure if it's correct

+ infer unknown relation by combining existing relations. ("collective learning")
Eg: how to know Friedrich Schiller is a  __(country) writer? By combining the links of <x isBornIn y> and <y isCityInCountry z>. The key is to detect the correlations between these links.

+ extract taxonomies by clustering instances


## Alice (Lifelong Learning Agent)
Michele Banko and Oren Etzioni, “Strategies for Lifelong Knowledge Extraction from the Web,” in Proceedings of the 4th International Conference on Knowledge Capture (ACM, 2007), 95–102, [link](http://dl.acm.org/citation.cfm?id=1298425).

### what can it do?
General task: to add a collection of abstract assertions about nutrition from a 2.5-million-page Web crawl constructed to contain documents in the domain.

<img src="http://www.geekwei.com/wp-content/uploads/2017/07/Screen-Shot-2017-07-09-at-1.51.04-PM.png" alt="" width="1130" height="372" class="alignnone size-full wp-image-102" />

+ learn new ontology (category)
Eg: learn new category such as "healthy food" from predetermined constraining lexical patterns (*buckwheat is a  {? food }* -- the concept of buckwheat and food are already learnt)

+ learn abstract proposition (a.k.a theory learning)
Eg: *Provide( fruit, {vitamin})* is deduced from the set of tuples { (oranges, provide, vi- tamin c), (bananas, provide, a source of B vitamins), (an avocado, provides, niacin)}. The key challenge is how to find a suitable level of generalization: compare *Provide({fruit}, {vitamin})* versus *Provide({food}, {substance})*, the latter is apparently too general.

+ active search constraint under certain topic
How to prioritizes subsequent theory-learning tasks? 

Eg: Given the goal is to learn theories about nutrition, after learning the proposition that * MayPrevent({antioxidant}, {disease})*, the learner shouldn't switch to learn more about all the properties on {disease}.

### data
Using [wordnet](http://wordnetweb.princeton.edu/perl/webwn) as seed knowledge. Can't find the results of this specific work.
More follow-ups from the UW Turing center in the [Open Information Extractor](http://openie.allenai.org/) project page, including [relations](http://relgrams.cs.stonybrook.edu/) and [Horn clause](http://projectsweb.cs.washington.edu/research/sherlock-hornclauses/) (propositions) 

## Learning by Reading (LbR) 
Dirk Hovy et al., “Unsupervised Discovery of Domain-Specific Knowledge from Text,” [link](http://dl.acm.org/citation.cfm?id=2002472.2002651)

### What can it do?
<img src="http://www.geekwei.com/wp-content/uploads/2017/07/Screen-Shot-2017-07-09-at-1.52.17-PM.png" alt="" width="1110" height="522" class="alignnone size-full wp-image-103" />

+ learn new categories from sentences.
Eg: “quarterback/NN Steve/NNP Young/NNP, ...”; "Steve Young, the quarterback of his team, said...”; "Steve Young is the quarterback of the 49ers"
still, from predetermined constraining lexical patterns similar to Alice and Probase.
Challenge: no supervision / seed knowledge at all.


