---
title: "Unable to locate (and install) Ubuntu Applications on the Web"
date: 2009-04-04
forum: Networking &amp; Wireless
---

### Post by barbeerh on 2009-04-04
Wasn't sure if this belonged in this section, but after spending an hour working with someone with a good knowledge of how to work with Ubuntu, we are still working with it.

The problem is that I would like to download and install several applications for ubuntu 8.10. 

From the terminal:

barbeerh@ubuntu:~$ sudo apt-get install ubuntu-restricted-extras
[sudo] password for barbeerh: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package ubuntu-restricted-extras
barbeerh@ubuntu:~$ 


Trying another in the terminal, again:

barbeerh@ubuntu:~$ sudo apt-get install xchat
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package xchat
barbeerh@ubuntu:~$ 


We tried to do a remote desktop session so he could look at himself, but it will not let him connect in spite of the fact that I have the options set to allow him.

His idea is that maybe my network is not allowing me to download the files due to bandwidth issues.  He also suggested that the installation of ubuntu 8.10 itself might be corrupted.  I am going to reinstall ubuntu 8.10 in the morning and will see what I can do with my network. 

If any has any suggestions or thoughts, you would have my gratitude.

---

### Post by superprash2003 on 2009-04-05
you need to open port 5900 for remote desktop to work..

---

### Post by barbeerh on 2009-04-08
Okay, update on issue:

As it turned out, my friend's advice on the problem was what fixed it.

I reinstalled Ubuntu 8.10 on my computer.  The difference, however, was instead of installing it while on Windows XP, I instead did it the more conventional way on the boot menu.  I can't say with certainty what happened, but I assume that doing it through the former method did not install critical components necessary to locate and install important packages from the Web.  Either way, I can now and I hope this helps anyone with a similar problem.

---

