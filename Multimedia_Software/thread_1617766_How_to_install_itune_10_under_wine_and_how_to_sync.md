---
title: "How to install itune 10 under wine and how to sync it with my iphone??? help"
date: 2010-11-09
forum: Multimedia Software
---

### Post by fatharraxman on 2010-11-09
I wanna update my iPhone please help me with the root commands for this simple task

---

### Post by Chronon on 2010-11-09
I think you will need to install Windows in a virtual machine (or find some other way of running Windows) and use iTunes with that.  AFAIK, iTunes doesn't work well in WINE.

---

### Post by Saner on 2010-11-10
When i had to sync a iPod (never used one before so it was all new to me) I couldnt get it to sync with itunes 7 (showed as Silver on WineHQ) 

in the end I had to use a VMware trial to get it working with windows in a virtual machine, Virtualbox wouldnt work when I tried it.

---

### Post by fatharraxman on 2010-11-13
please am very novice in ubuntu and computer at all what is virtual machine what do you mean??
I got only ubuntu in my 160 gb memory harddisk 
if you know any web site about how to install widows in a vertual machine with easy understood instruction please show me gratefully
:P

---

### Post by Chronon on 2010-11-13
[COLOR="Silver"]Well, I don't know the specs of your machine and whether it's advisable to install Windows in a VM or as a dual boot.  Installing it in a VM gives you convenience but there's overhead associated with running a system inside of another system.  The entire system lives in a virtual hard drive that's just a file on your current system.  Here's the community documentation on the virtualization software I use: [https://help.ubuntu.com/community/VirtualBox](https://help.ubuntu.com/community/VirtualBox)

My desktop computer runs Windows XP reasonably well as a guest (virtual) system.  I have, in the past, installed iTunes and used it to synch an iPod Touch  2nd Generation.  (I was even able to share folders between my guest Windows system and my host Ubuntu system, permitting me to drag files from my home folder directly to the device.)  

I believe you will need the non-free version (it is still free of charge but does not bear the freedoms necessary to call it free software) to get USB access in the virtual system.  [http://www.virtualbox.org/wiki/Editions](http://www.virtualbox.org/wiki/Editions)

You will need a Windows install disk with valid license to install it either this way or as a dual-boot.[/COLOR]

-----------------------------

If you just want to update your phone once (like a firmware update) I would just use someone's Windows or Mac system and update using that.

---

