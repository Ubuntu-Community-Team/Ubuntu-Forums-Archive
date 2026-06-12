---
title: "Compiling Hephex in ubuntu 7.10 amd64"
date: 2008-01-22
forum: Multimedia Production
---

### Post by diPSy on 2008-01-22
Try compile Gephex, but every time get some errors. Any1 have detaled manual, how i can compile it? Very need this tool...

---

### Post by Weevil on 2008-04-15
Hi diPSy,

Next time try to post some more information on what errors you got and what you've already tried to get it to work.

The french Ubuntu guys made a special Ubuntu howto which I followed, see it at
 [http://ubuntufromscratch.wordpress.com/2007/12/20/compiler-gephex-045-darcs/](http://ubuntufromscratch.wordpress.com/2007/12/20/compiler-gephex-045-darcs/)

or translation in English at
 [http://translate.google.com/translate?u=http%3A%2F%2Fforum.ubuntu-fr.org%2Fviewtopic.php%3Fid%3D183807&langpair=fr%7Cen&hl=en&ie=UTF8](http://translate.google.com/translate?u=http%3A%2F%2Fforum.ubuntu-fr.org%2Fviewtopic.php%3Fid%3D183807&langpair=fr%7Cen&hl=en&ie=UTF8)


It didn't work for me completely so I added the following steps - note that this is just my try&retry method;

- Install checkinstall and do 'sudo checkinstall' instead of 'sudo make install'

- Install the frei0r plugins

- After running the ./configure script check what dependencies are missing that you might need, install them and configure again untill you're satisfied

- running 'sudo checkinstall' quit on me several times complaining it couldn't find some directory or file. For some reason some Makefiles inside subdirectories couldn't get permission to create their folders. In my case just creating the directories /usr/local/lib/gephex-0.4, usr/local/lib/gephex-0.4/modules and /usr/loca/lib/gephex-0.4/types and then running 'sudo checkinstall' again was sufficient. Just keep trying untill it installs ok :)



Hope this helps!

 Weevil

---

