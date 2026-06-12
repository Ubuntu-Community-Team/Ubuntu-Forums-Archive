---
title: "Music Problems"
date: 2008-03-10
forum: Multimedia &amp; Video
---

### Post by feeop on 2008-03-10
Hello all. I am new to Ubuntu and have so far had no difficulties. However, now that I have my music files installed (all mp3), I can't seem to get Rhythmbox or Amarok to work. This is the error I received, Pls help and Thx in advance

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

---

### Post by mangurt on 2008-03-10
Greetings,
It seems that you need to run dpkg --configure -a  In order to do this, open terminal, and type

sudo dpkg --configure -a

Then enter your password.  That  should fix the problem.

---

### Post by feeop on 2008-03-10
Thx, however after doing that, now I get this

Software index is broken

It is impossible to install or remove any software. Please use the package manager "Synaptic" or run "sudo apt-get install -f" in a terminal to fix this issue at first.

---

