---
title: "[TUTORIAL] - updating jack"
date: 2008-02-13
forum: Multimedia &amp; Video
---

### Post by Mr.Johnny on 2008-02-13
Hi!

I don't know if many of you had problems updating jack, but I had and took me a few weeks to discover how to update it properly, so I hope this helps someone.

1 - If you don't have it installed, install subversion, libtool, and automake (thru the synaptic package manager or command prompt), besides the proper compiler - let me know if anything's missing, I think that's all you need.

2- get the latest jack version (this will create a directory named jack in you current location, so be in your home folder or something): 
svn co [http://subversion.jackaudio.org/jack/trunk/jack](http://subversion.jackaudio.org/jack/trunk/jack)

3- cd to the newly created directoy named jack and type: 
sh ./autogen.sg --prefix=/usr

(use "--prefix=/usr" because by default it uses /usr/local and I that can cause problems for other programas finding libs and the program)

then the usual "make" and "make install" with root priviledges.

(note: newer jack  versions already set up the proper /dev/shm thing, so we don't need to change that)

ps: If you want to update qjackctl as well, don't forget to run ./configure with the --prefix=/usr option as well.

And basically not doing these steps was the cause of all my problems as all this time I was only compiling and installing the downloadable tarball... I hope you get it working straight away with this.

---

