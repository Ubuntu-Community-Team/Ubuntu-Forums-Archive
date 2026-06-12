---
title: "Share /var/lib/ between 9.10/9.04 dual boot?"
date: 2010-02-14
forum: Mythbuntu
---

### Post by laffinet on 2010-02-14
Hi !

I'm running 9.04 as my "production" system and decided to install 9.10 as a dual to see whether I like it enough to switch over.

Question: can I share my /var/lib (which sits on a separate partition) between the two installs without running into problems?

I've noticed that /var/lib contains not only the mytthv folders (and even there 9.10 has a few additional ones), but also other stuff. Is this going to cause issues, eg one install modifying stuff that the other can't deal with? 

Thanks.

---

### Post by scottishnarn on 2010-02-15
Short answer: Don't do it. 

Slightly longer answer:
I have a dual boot for a couple of weeks everytime I upgrade things. Basically it takes a couple of weeks to get enough time to get everything working (in between recording and watching shows), iron out any issues and set things up how I like. Then when I'm satisfied that everything works I mount my recordings partition and import all my data from the old database into the new database and then I have to run ```
mythcommflag --rebuild
``` which rebuilds the seek table allowing me to fast forward and stuff (nothing to do with actual commercial flagging, I don't use it). This usually takes several hours. 

This is just for recordings. In var you also have software which will change with versions and log files which will just get really messed up if you have two different versions writing to the same file. Trying to pin down what is causing any errors will be a nightmare. 

So back to the short version: Don't do it. Use one for testing until you have it stable and then move over.

---

