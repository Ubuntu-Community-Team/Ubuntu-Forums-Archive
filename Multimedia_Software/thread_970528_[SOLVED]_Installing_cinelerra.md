---
title: "[SOLVED] Installing cinelerra"
date: 2008-11-04
forum: Multimedia Software
---

### Post by tostrye on 2008-11-04
I am trying to install cinelerra because I hate winblows and never want to use it again. I am using this tutorial: [http://nexthing.wordpress.com/2007/12/20/cinelerra-installation-under-ubuntu-gutsy-710/](http://nexthing.wordpress.com/2007/12/20/cinelerra-installation-under-ubuntu-gutsy-710/) but when i do 'sudo apt-get install cinelerra' i get 
Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  cinelerra: Depends: libfftw3-3 but it is not installable
             Depends: libopenexr2ldbl (>= 1.2.2) but it is not installable
             Depends: libquicktimehv (= 1:2.1.0-2svn20082807ubuntuubuntu1) but it is not going to be installed
E: Broken packages

:popcorn:

---

### Post by moviemaniac on 2008-11-04
Just follow the instructions on the cinelerra page and you should be good:

[http://cinelerra.org/getting_cinelerra.php](http://cinelerra.org/getting_cinelerra.php)

The problem lies within unsatisfiable dependencies caused by an old version of cinelerra that's linked in the tutorial you followed.

---

