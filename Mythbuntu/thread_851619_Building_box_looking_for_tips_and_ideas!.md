---
title: "Building box looking for tips and ideas!"
date: 2008-07-06
forum: Mythbuntu
---

### Post by k420 on 2008-07-06
I am new to mythubuntu but an user of ubuntu for 4 years.  My specs for parts as of right now are a Acer t-180 here are the specs

Processor             	 AMD Athlon 64 X2 2 GHz
Chipset 	         NVIDIA GeForce 6100
Installed Memory 	 1 GB (DDR2 SDRAM)
TV card                  hauppage 1800
Display                  Vizio 37" hooked up by RGB cable

Now I have Time Warner Digital Cable with a dvr made by Scientific Atlanta box. Is there any advice you can give me should i cancel my dvr( if this is the case can i access all the Channels easily and record series)  What is your all's advice. I haven't recieved the hauppage card.  So haven't set anything up yet beside's getting the video resolution right with the tv.

---

### Post by OffAxis on 2008-07-07
According to the mythtv wiki [http://mythtv.org/wiki/index.php/Hauppauge_HVR-1800](http://mythtv.org/wiki/index.php/Hauppauge_HVR-1800)
your card only works with a digital signal, so make sure that's what your set top box is outputting.

---

### Post by k420 on 2008-07-07
Well i have time warner cable with a scientific atlanta Explorer 8240HDC.  I get the HD channels that they offer and it has a dvr.  Now if i plug this cable box into a windows vista machine with IEEE 1394 cable it starts trying to install drivers but it doesnt find any any i really didnt want to try to hard.

---

### Post by mrand on 2008-07-07
> **OffAxis said:**
> According to the mythtv wiki [http://mythtv.org/wiki/index.php/Hauppauge_HVR-1800](http://mythtv.org/wiki/index.php/Hauppauge_HVR-1800)
your card only works with a digital signal, so make sure that's what your set top box is outputting.Until very recently, the card was only usable as a QAM tuner.  You'd likely plug that directly into the cable, not into the your STB.  I don't recall hearing of a cable box which outputs QAM - if they did, that would solve a LOT of problems.

Having said that, analog support is going to be available for it soon (may require some manual work on your part until pulled into the distributions, and probably not bug-free): [http://www.linuxtv.org/pipermail/linux-dvb/2008-June/026666.html](http://www.linuxtv.org/pipermail/linux-dvb/2008-June/026666.html) 

> **k420 said:**
> Well i have time warner cable with a scientific atlanta Explorer 8240HDC.  I get the HD channels that they offer and it has a dvr.  Now if i plug this cable box into a windows vista machine with IEEE 1394 cable it starts trying to install drivers but it doesnt find any any i really didnt want to try to hard.Hmmm... you didn't mention 1394 eariler.  While using that would be ideal, what you you may find (depending on your specific Time Warner division), is that many channels are blocked (called 5C encryption).  Or maybe you'll get lucky and be in an area that doesn't block many channels.  It is definitely worth a try (and you don't have to wait on the HVR-1800 to arrive).

When the HVR-1800 does arrive, I'd hope to use it like so:

1. Digital input: direct to cable
2. Analog input : output of STB (might not be well supported yet)
3. 1394 connection: use for controlling the channel on the STB 

Item 3 assumes that you can't get lots of channels via 1394.  If you do get all your channels via 1394, connect analog direct to cable as well.

   [INDENT]Marc[/INDENT]

---

### Post by volkswagner on 2008-07-07
HD, HD, HD.  This is the thorny subject.  To record HD channels provided by CATV, it is hard to compete with their own DVR box.  Until component capture becomes mainstream, the free channels may be all you will get with firewire.  I still think if you can get a reliable firewire connection, than it is a great additional capture device.  If you use the cable box for live tv (not via myth) you may get missed recordings or reduce the reliability for the firewire connection.  If you are ok with down scaling the HD content via an svid capture to an analog card than, you will be happy to get rid of the Time warner DVR.  

Depending on how many boxes you have and how your cable co. handles billing, you may be able to get an additional box for the same price per month.  This will give you two tuners or one to dedicate to tv/myth.

If you are up and running, I would run through the add a tuner and see how myth picks up your box.

---

### Post by k420 on 2008-07-09
Well i just recieved my card today so i am gonna hook it up to night and do a new install of mythbuntu on the machine.  will let you guys know how your sugegstions panned out.  thanks guys or gals.

---

