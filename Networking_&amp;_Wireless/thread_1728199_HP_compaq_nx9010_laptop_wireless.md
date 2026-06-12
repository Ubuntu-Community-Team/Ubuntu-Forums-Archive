---
title: "HP compaq nx9010 laptop wireless"
date: 2011-04-13
forum: Networking &amp; Wireless
---

### Post by EtherJones on 2011-04-13
Hello.

I am an Ubuntu newbie.

I just installed Ubuntu 9.10 unto an HP compaq nx9010 laptop.  I cannot get the wireless to work.  Can someone talk me through this?

I booted the same machine from CD with Lucid Puppy Linux 520 and wireless works fine.

So it's not a hardware problem.

Thank you.

**

---

### Post by josephmills on 2011-04-13
> **EtherJones said:**
> Hello.

I am an Ubuntu newbie.

I just installed Ubuntu 9.10 unto an HP compaq nx9010 laptop.  I cannot get the wireless to work.  Can someone talk me through this?

I booted the same machine from CD with Lucid Puppy Linux 520 and wireless works fine.

So it's not a hardware problem.

Thank you.

**
could you post ```
lspci
``````
iwconfig
``````
rfkill list
```also when was the last time that you upgraded and updated?

---

### Post by josephmills on 2011-04-13
could you please post ```
lspci
``````
iwconfig
``````
rfkill list
```also when was the last time that you upgraded and updated?

---

### Post by mikewhatever on 2011-04-13
Some wireless cards simply need the driver installed. Have you checked under System->Administration->Hardware Drivers yet?

PS: Unrelated, but still, Karmic only has two weeks of support left. You had better install Lucid (10.04), which is the LTS release.

---

### Post by EtherJones on 2011-04-13
> **mikewhatever said:**
> Some wireless cards simply need the driver installed. Have you checked under System->Administration->Hardware Drivers yet?

No.  Like I said, I am a newbie.  I thought the installation would take care of all that.   The much-smaller and less-ambitious Puppy Linux worked out-of-the-box, so I was expecting no less from Ubuntu.  I will try your suggestion.  How do I get to "System" in Ubuntu?

> PS: Unrelated, but still, Karmic only has two weeks of support left. You had better install Lucid (10.04), which is the LTS release.

What is Karmic?

**

---

### Post by EtherJones on 2011-04-13
> **josephmills said:**
> when was the last time that you upgraded and updated?

This is a fresh install (today) of Ubuntu 9.10, from a CD given me by a friend.  I told it to wipe out the previous OS and do a fresh install.   I figured that since the target machine (HP compaq nx9010 laptop) is older than the 9.10 release, and was popular in its day, that 9.10 would have built-in support for it.

> could you post lspci, iwconfig, and rfkill

I'll try. I assume I need to get to a command window and just type in those commands?  Is there a way to redirect the output to a file?

**

---

### Post by josephmills on 2011-04-13
yes there is go to Applications-->Accessories--> Terminal (or ctrl+alt+t ) 
then type in the codes copy and paste by the way welcome to Ubuntu :D

---

### Post by mikewhatever on 2011-04-13
> **EtherJones said:**
> No.  Like I said, I am a newbie.  I thought the installation would take care of all that.   The much-smaller and less-ambitious Puppy Linux worked out-of-the-box, so I was expecting no less from Ubuntu.  I will try your suggestion.  How do I get to "System" in Ubuntu?



What is Karmic?

**

There should be a menu, top left, one of the entries should be System.
Karmic Koala was the code name of Ubuntu 9.10, the one you've installed according to the original post.

---

### Post by EtherJones on 2011-04-13
> **josephmills said:**
> yes there is go to Applications-->Accessories--> Terminal (or ctrl+alt+t ) 
then type in the codes copy and paste by the way welcome to Ubuntu :D

Done.  See attached screenshots.


**

---

### Post by EtherJones on 2011-04-13
> **mikewhatever said:**
> Some wireless cards simply need the driver installed. Have you checked under System->Administration->Hardware Drivers yet?


See attached screenshot.

---

### Post by EtherJones on 2011-04-14
> **EtherJones said:**
> Done.  See attached screenshots.


Is there anyone who can interpret the screenshots and suggest what to try next?

I was hoping there was a network setup "wizard" in Ubuntu that would walk me thru the steps.

In Puppy Linux 520, all I had to do was click on the network icon in the tray and in 3 easy steps I had the wireless card working.  So I know the wireless card is working; I just can't get it to work in Ubuntu.

**

---

