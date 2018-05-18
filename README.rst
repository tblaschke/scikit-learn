.. -*- mode: rst -*-

scikit-learn
============

scikit-learn is a Python module for machine learning built on top of
SciPy and distributed under the 3-Clause BSD license.

The project was started in 2007 by David Cournapeau as a Google Summer
of Code project, and since then many volunteers have contributed. See
the `AUTHORS.rst <AUTHORS.rst>`_ file for a complete list of contributors.

It is currently maintained by a team of volunteers.

Website: http://scikit-learn.org


Modifications
-------------

This repo contains some changes for libsvm and liblinear such they utilize openmp. This allows to train single SVM model
much faster on modern multi-core machines. Be aware that openmp can cause trouble using multiprocessing.Pool

Installation
------------

Dependencies
~~~~~~~~~~~~

scikit-learn requires:

- Python (>= 2.7 or >= 3.4)
- NumPy (>= 1.8.2)
- SciPy (>= 0.13.3)

For running the examples Matplotlib >= 1.3.1 is required. A few examples
require scikit-image >= 0.9.3 and a few examples require pandas >= 0.13.1.

scikit-learn also uses CBLAS, the C interface to the Basic Linear Algebra
Subprograms library. scikit-learn comes with a reference implementation, but
the system CBLAS will be detected by the build system and used if present.
CBLAS exists in many implementations; see `Linear algebra libraries
<http://scikit-learn.org/stable/modules/computational_performance.html#linear-algebra-libraries>`_
for known issues.

User installation
~~~~~~~~~~~~~~~~~

Check out the source and switch to the 0.19 tag::

    git clone https://github.com/tblaschke/scikit-learn.git
    cd scikit-learn
    git checkout 0.19.1
    CFLAGS="-fopenmp -DCV_OMP=1" CXXFLAGS="-fofopenmp -DCV_OMP=1" LDFLAGS=-lgomp python setup.py build
    python setup.py install
