---
title: "Help Needed"
date: 2006-02-23
forum: Networking &amp; Wireless
---

### Post by wiltometer on 2006-02-23
Hi All,

I am new to this Linux thingymajig, sick of Windows and associated problems, (interesting that it displays the Ubuntu home page incorrectly).

Anyway, from the many Linux families out there I decided to give first stab to Ubuntu, so I downloaded the "Live disk" However I hit a problem almost immediately with my hardware. The prog doesnt seem to find my SAGEM ADSL modem connected by USB to PC. I dont know where to start to even try to address the problem!

I also remember having to load a disk for the drivers and activation etc when I was sent the modem..... Is all this type of stuff by-passed with Linux type systems and UBUNTU?

I am not a complete dummy, I have done some machine code and some basic a long time ago at college, but I am rusty, please keep any Advises as idiot proof as possible.

Thanks in anticipation!

Wiltometer.

---

### Post by wiltometer on 2006-02-23
I only wish my problem was a bit interesting, good job Ive got windows still running or I wouldnt be here at all.

Come on you were new once!

---

### Post by Lambert on 2006-02-23
Yes we were all new but not all of us have the same set up. Give it some time, answers sometimes come days after first post. The person with the answer needs to see this.

I know nothing about adsl. I can only suggest searching if you haven't and see if this link offers you anything.

[https://wiki.ubuntu.com/ADSLPPPoE](https://wiki.ubuntu.com/ADSLPPPoE)

---

### Post by wiltometer on 2006-02-23
Lambert,

Thanks for your trouble to guide.

I will print off that and follow instructions.

I still cant figure how it will bypass installation disk, if it does that I will be more than pleased with LINUX.

Wiltometer.

---

### Post by wiltometer on 2006-02-23
Lambert-seeing that somehow I have managed to strike at least one chord,

I have inputed said commands

dpkg-s pppoeconfig


and sadly I have fell at the first hurdle in that the command is not recognised. Is this phenomenon peculiar to the LIVE version that i am attemting to operate.

wiltometer

---

### Post by wiltometer on 2006-02-24
still struggling here!

---

### Post by wrtrdood on 2006-02-24
[QUOTE=wiltometer]

dpkg-s pppoeconfig

wiltometer[/QUOTE]

not recognized because it should be entered as shown:

dpkg -s pppoeconf

The command is dpkg.  This programs has switches of which -s is one which will provide a status report of the package.  This is simply to determine whether or not the pppoeconf package is installed.  If not, you'll have to follow the instructions for doing that.

---

### Post by wiltometer on 2006-02-24
thanks, will try.

---

