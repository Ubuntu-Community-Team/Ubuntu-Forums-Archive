---
title: "ipython users: testing help"
date: 2011-02-18
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by MadCow108 on 2011-02-18
debian yesterday updated ipython (very good interactive python shell) to 0.10.1 which mainly fixes bugs but also adds some features.
I constantly use this program and also require one of the new features (SGE cluster support) thus I would like to have it in natty.

As it is quite close to feature freeze (24.2) I would like to request a merge relative soon.
But it introduces a new upstream release and it was only been in debian a very short time so I would feel safer when some ipython users with a little extra time could test the new version in natty for serious regressions to the old version 0.10.
For this purpose I have created a ppa with the new version:

[https://launchpad.net/~jtaylor/+archive/ipython/](https://launchpad.net/~jtaylor/+archive/ipython/)

sudo apt-add-repository ppa:jtaylor/ipython

any help is greatly appreciated.

---

### Post by SevenMachines on 2011-02-19
No problems so far, i'll keep using it and let you know if anything obvious crops up

---

### Post by afoglia on 2011-03-10
Is this the version currently in natty?  I'm running 0.10.1-1.  And I just discovered it crashes when trying to plot via matplotlib/pylab.  (Rather annoying to discover this in the middle of a tutorial...)

Here's the example code:

{code}
$ ipython -pylab
Python 2.7.1+ (r271:86832, Feb 24 2011, 15:00:15) 
Type "copyright", "credits" or "license" for more information.

IPython 0.10.1 -- An enhanced Interactive Python.
?         -> Introduction and overview of IPython's features.
%quickref -> Quick reference.
help      -> Python's own help system.
object?   -> Details about 'object'. ?object also works, ?? prints more.
 
  Welcome to pylab, a matplotlib-based Python environment.
  For more information, type 'help(pylab)'.

In [1]: plot([0,1,2])
Segmentation fault (core dumped)
{/code}

This also happens if I run ipython without the -pylab option and import pylab myself.  And I've tried a few different backends to no effect.

This is already described as [this debian bug]("http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=617432").  Is there someone on the Ubuntu end we can prod to look into this before the release?

---

### Post by MadCow108 on 2011-03-10
I am aware of this bug in debian but I could _not_ reproduce it in natty which now also has 0.10.1
Not good when it now appears also in ubuntu as it is a real showstopper:O

It seems to be related to mesa drivers. see [http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=612529](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=612529)
I'll do some testing as soon as my natty boots again :/

---

### Post by MadCow108 on 2011-03-10
yup natty updated their mesa 2 days ago and not ipython is broke there too :(

---

### Post by MadCow108 on 2011-03-11
its actually a really old bug reintroduced:
[https://bugs.launchpad.net/ubuntu/+source/mesa/+bug/259219](https://bugs.launchpad.net/ubuntu/+source/mesa/+bug/259219)

workaround:
LD_PRELOAD=/usr/lib/libstdc++.so.6 ipython

---

