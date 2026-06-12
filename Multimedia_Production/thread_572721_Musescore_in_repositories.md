---
title: "Musescore in repositories?"
date: 2007-10-10
forum: Multimedia Production
---

### Post by panta rei on 2007-10-10
Hi!

There is a development of a great piece of software for music composition / score editing called Musescore:  [http://mscore.sourceforge.net](http://mscore.sourceforge.net)
When matured, it can be a serious Linux-native competitor to commercial software like Finale or Sibelius. The program's UI and basic functionality looks quite similar to Sibelius, which is in my opinion a cool idea because this is exactly what many musicians among Linux users miss. As far as I know Musescore is the best option for WYSIWYG score editing in Linux (at least for me) altough it is still in early stage.
The authors seem to keep working on it and brought it to version 0.7 few weeks ago. The software is already quite usable but I haven't found it in any repositories for Ubuntu (or Ubuntu Studio). The packages already exist for some other distributions. In Ubuntu, users are required to compile it from sources which is a pain in the neck for many of them since most of the musicans are probably not programmers... (including me - altough I have some  basic programming skills already since 8-bit computers era :) )  People are reporting errors when compiling and often end up stuck without having the software working properly.

Well, so my qestion is: [B]Is there a repository from which Musescore can be installed in Ubuntu?
It would be nice to have it in one of the common Ubuntu repositories so that people can install and update it without any hassle!
[/B]
Any comments welcome!

---

### Post by Jussi01 on 2007-10-11
Please FIle a needs packaging bug on Launchpad. This looks to be a good program, so hopefully we will have it into the repositories for hardy.

Thanks 

Jussi

---

### Post by UbuWu on 2007-10-11
Musescore 0.7 deb: [http://www.mediafire.com/?4tlaoz3cztm](http://www.mediafire.com/?4tlaoz3cztm)

---

### Post by panta rei on 2007-10-11
Cool! Thanks for the link!!!

Is someone who already has a Launchpad account willing to file a packaging need as Jussi suggested? (I am quite new here and Launchpad is a way I haven't discovered yet...) It would still be nice to have Musescore in repositories.

Thanks

Panta rei

---

### Post by UbuWu on 2007-10-14
Sure: [https://bugs.launchpad.net/ubuntu/+bug/152650](https://bugs.launchpad.net/ubuntu/+bug/152650)

---

### Post by SteinbergerNate on 2007-10-16
just tried installing the deb and it says:
Error: Dependency is not satisfiable: libqt4-core
however, I went into synaptic and it shows that libqt4-core is in fact already installed.

---

### Post by 1002285 on 2007-10-26
It is in Musix's repository, although only the version 0.5 or sth.
I tried to install it, adding Musix's repository line to my /etc/apt/sources.list - deb [ftp://musix.ourproject.org/pub/musix/deb/](ftp://musix.ourproject.org/pub/musix/deb/) ./
and when I told my system:
sudo aptitude install mscore
it kind of tried to do it, but stopped at the point "logging in" in the very beginning.
I don't know whether there is a way around that.

---

