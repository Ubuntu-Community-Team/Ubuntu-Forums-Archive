---
title: "Rhythmbox and Magnatune/Jamendo"
date: 2009-03-17
forum: Multimedia Software
---

### Post by SR_ELPIRATA on 2009-03-17
Hey all:

In the most recent update... something was screwed up and now I cannot browse neither Magnatune nor Jamendo's content via Rhythmbox. It simply says that its "loading Magnatune catalogue" but never ends.

The times that did, in the first days after the udpate, It would read like 75 hours of music and still you werent able to browse their content. Before the update, I could browse the contents and the total ammount of music said to be of 23 days and some 50 minutes.

I'm wondering if anyone else has been having this problem.

Also, would like to know if I can roll back this update and see if it fixes it.

Thanks in advance...

ELP

---

### Post by mcg on 2009-04-01
I have this problem as well.  Did you ever solve it?

---

### Post by SR_ELPIRATA on 2009-04-02
No. What I did was to NOT do the updates for the Rythmbox software on another hard disk installation I had. Im using that installation and is working, but I have to keep an extra eye on the updates... so it doesnt happen again.

I also forgot that I was best to report this as a bug, perhaps then we'll get a fix.

ELP

---

### Post by francesco.spegni on 2009-04-10
I'm having this problem too. Lunching rhythmbox from a terminal, i obtain the "infamous" 

File "/usr/lib/python2.5/xml/sax/handler.py", line 38, in fatalError
    raise exception
xml.sax._exceptions.SAXParseException: <unknown>:1878:24: not well-formed (invalid token)

expection (and other similar ones). I tried everything i found on the web (reinstalling rhythmbox, deleting the magnatune and jamendo information from my ~/.gnome2/ directory... but nothing worked until now...)

hope the new upgrades will fix it...

---

### Post by SR_ELPIRATA on 2009-04-16
Ok, I did what we were supposed to do and found the problem and solution :)

Once I reported the problem from inside Rhythmbox, and put the relevant stuff about magnatune catalogue not loading up... it took me to a list of similar Rhythmbox bugs.

This one made it:

[https://bugs.launchpad.net/ubuntu/+source/rhythmbox/+bug/343118](https://bugs.launchpad.net/ubuntu/+source/rhythmbox/+bug/343118)

It explains a very simple workaround to perform. The thing to eliminate is not exactly at the specified column but you can spot it easily nearby (in my case in column 26).

It took 3 deletions in my case and now I can browse the catalogue again. I guess a similar thing is for jamendo (there's another bug listing for jamendo... which is this one:

[https://bugs.launchpad.net/bugs/203428](https://bugs.launchpad.net/bugs/203428)

But I dont listen to jamendo much, I just crave Magnatune.

The character in question in gedit is:

[http://stormraider.net/error-to-delete.png](http://stormraider.net/error-to-delete.png)

Happy Magnatuning :)

ELP

---

### Post by mcg on 2009-04-16
Magnatune started working for me without this change.  Perhaps Magnatune removed the offending character?

---

### Post by SR_ELPIRATA on 2009-04-16
Probably, I read on Launchpad that they had told them about the offending characters.

---

### Post by francesco.spegni on 2009-04-17
thanks a lot, it worked :)

---

