
Parsing (loading the module)
============================

Run (example):
  `python3 demo1.py`

Launching a server
==================

May need to install [jsonrpclib](https://github.com/tcalmant/jsonrpclib) (for python3).

Go to the folder where CoreNLP is installed (usually the Scripts/ folder) and run:

```
CORENLP="stanford-corenlp-full-2014-08-27" python3 -m corenlp
```

To remove copula relations (other flags can be passed in the same way):

```
  CORENLP="stanford-corenlp-full-2014-08-27" CORENLP_OPTIONS="-parse.flags \" -makeCopulaHead\"" python3 -m corenlp
```

Current algorithm is designed to work with copula relations removed.


Parsing using a server
======================

We assume that a server is launched.

Run (example):
```
  python3 demo2.py
```

Using a server enables to parse quicker than loading the module each time.


Presentation of the output using dot
====================================

We assume that a server is launched.

You can have a dot file using the following: `python3 > demo.dot` (then, write
your sentence).

You can also have directly a ps file using the following: `python3 demo3.py | dot -Tps > demo.ps`

More laziness: `echo "What is the birth date of the first president of the United States?" | python3 demo3.py | dot -Tps > demo.ps`


Tree simplification
===================

We assume that a server is launched.

Run the same thing as before, replacing `demo3.py` by `demo4.py`.

More conveniently, use the script `displaygraph`:
```
./displaygraph.sh Who wrote \"Lucy in the Sky with Diamonds\" and \"Let It Be\"?
```


Description of demo files
=========================

* `demo1.py`: parsing without a server. Output the direct answer of CoreNLP (copula relations not removed)
* `demo2.py`: Start server before. Output the dependency relations from CoreNLP
* `demo3.py`: Start server before. Print the dependency graph from CoreNLP
* `demo4.py`: Start server before. Print the dependency graph after preprocessing simplifications (merging of some nodes)
* `demo5.py`: Start server before. Print the dependency graph after dependency analysis
* `demo6.py`: Start server before. Full algorithm, output triples from question
* `demo7.py`: Start server before. Full algorithm, output standardized triples tree from question
