---
title: "Python 2.5 Support"
date: 2010-09-03
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by salisbury.joseph on 2010-09-03
Hello there.

I'm having some issues with python 2.5 support in Maverick.

As the Google App Engine SDK requires python 2.5 to function correctly, I do require this version - it's not due to disliking 2.6.

Can someone help me as to how to install python 2.5?

---

### Post by etu on 2010-09-03
I suspect the same problem with appengine.

Trying to install Python2.5 is a funny loop:


[FONT="Courier New"]$ sudo apt-get install python2.5
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package python2.5 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  python2.5-minimal

E: Package 'python2.5' has no installation candidate
$ sudo apt-get install python2.5-minimal
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package python2.5-minimal is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  python2.5

E: Package 'python2.5-minimal' has no installation candidate[/FONT]

---

### Post by seeker5528 on 2010-09-04
Pyton 2.5 was removed, looking at [http://packages.ubuntu.com](http://packages.ubuntu.com) it looks like Karmic was the last version to include it. It's been out of Debian unstable/testing for a while too. 

You could try downloading the karmic versions of the relevant python2.5* packages:

 [http://packages.ubuntu.com/search?keywords=python2.5&searchon=names&suite=karmic&section=all](http://packages.ubuntu.com/search?keywords=python2.5&searchon=names&suite=karmic&section=all)

But dependency issues may prevent them from being installed in Maverick.

Later, Seeker

---

### Post by davec64 on 2010-09-04
You can install 2.5 and 2.6 side by side, but I can't find the original howto I read explaining it. i did find this old one relating to putting 2.6 along side a running 2.5. I think it would probably work in reverse putting the 2.5 on an existing 2.6.

[http://www.talino.org/tutorials/install-python-261-without-trashing-ubuntu/]("http://www.talino.org/tutorials/install-python-261-without-trashing-ubuntu/")

Best of luck!

EDIT:

Also found this relating to Jaunty:
[http://superuser.com/questions/28822/preferred-way-to-install-multiple-python-versions-on-ubuntu-jaunty]("http://superuser.com/questions/28822/preferred-way-to-install-multiple-python-versions-on-ubuntu-jaunty")

---

### Post by salisbury.joseph on 2010-09-05
That's the problem - even though it is entirely possible, there are just no packages for it.

---

### Post by dino99 on 2010-09-05
seems you need to fall back to HARDY repo to find python2.5

[http://packages.ubuntu.com/en/hardy/python](http://packages.ubuntu.com/en/hardy/python)

(might be scary about dependencies, maybe you need to install hardy side by side on your system)

if you try it on lucid/maverick, follow this link to set it as default for your needs:

[http://tareqalam.wordpress.com/2008/11/28/change-the-default-python-version-in-ubuntu/](http://tareqalam.wordpress.com/2008/11/28/change-the-default-python-version-in-ubuntu/)

---

