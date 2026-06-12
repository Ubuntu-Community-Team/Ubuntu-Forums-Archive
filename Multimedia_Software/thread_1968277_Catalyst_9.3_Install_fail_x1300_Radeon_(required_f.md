---
title: "Catalyst 9.3 Install fail x1300 Radeon (required for dual head)"
date: 2012-04-28
forum: Multimedia Software
---

### Post by MainframeGuy on 2012-04-28
I moved to Pengolin and recently from Natty, the migration has thrown up some issues and the first I need to address is getting my dual head back!

Natty default gave me that support (go Narwal!) but Pengolin is struggling to find his precision.

My researchs so far led me to reckon I need the ATI 9.3 version, but when I run it the script falls over with ....
```

Error: ./default_policy.sh does not support version
default:v2:i686:lib::none:3.2.0-24-generic-pae; make sure that the version is being
correctly set by --iscurrentdistro
```

Can a more experience person help from here on out?

I have read things about fglrx (floating point graphics?) and am contemplating trying 
```
sudo apt-get install fglrx-updates
```
but reluctant in case I mess things up further,

I already forgot my card was not NVIDIA and having tried that script am paranoid it may have messed with my pengolin ;( !

[EDIT] tried that and other things suggested on an HD5470 post, but still no joy :( 

Worried the message means my 12.04 haS COST ME MY DUAL HEAD (panicing caps!)[/EDIT]

---

### Post by MainframeGuy on 2012-04-28
noticing the script file seems to be 64 bit and knowing i have installed the 32 bit linux (silly of me really, on 64 bit hardware, but hey, it is what it is).... I read that 
> 32-Bit packages must be installed for 64-Bit Linux drivers to install or work.
Could this be the issue?  And if it is can someone shed light on how to get those 32-Bit packages on please?

[EDIT] tried to find this myself, but everything relates to installing 32 bit packages on a 64 bit system.... so thought I should clarify, my Pengolin migration leaves me with Ubuntu 32 bit and the Ati install seems to be 64 bit.... I cannot find a 32 bit one, so presumably I need something to make the script run?  Or am I way off the mark here? [/EDIT]

---

### Post by MainframeGuy on 2012-04-29
UPDATE - after many and various changes on my last reboot I have mirrored displays, my new problem is how to get the desktop to extend to both screens, and I am unsure if this is driver related or a generic issue with 12.04, since I read quite a few reports of broken dual head.... would appreciate advice before I invest further time an effort in the drivers.

Oh, and I think the i386-64 file is the only one and should work with my 32 bit; my thinking is they wrote a script for 54 and built in the 32 bit support, unless anyone can tell me different?  I'm thinking the drivers may even be running if I have both screens up, am I right?  

sorry to go on and on...

UPDATE 2!

Having ALMOST got dual head to work I was looking around and realised GDM has gone and there is something new (lightdn?) so when I restarted that to try and check the new settings the next reboot would not only fail to let me login - but lost all passowrds, and resetting from root prompt gives authentication errors!  This is documented across multiple other posts - which eventually take you here [https://bugs.launchpad.net/evdev/+bug/921236/comments/64](https://bugs.launchpad.net/evdev/+bug/921236/comments/64) which tells me this is basically broken at this time....

I am presently resizing the partition to try a fresh install but undecided whether to make this 64 bit since need to download that....

Anyway - the drivers seem the least of my worries now! ;)

---

### Post by mörgæs on 2012-05-02
I'm struggling with the same Radeon card. 

When you say it worked in 11.10, was it a 32 or 64 bit installation?

---

### Post by MainframeGuy on 2012-05-02
> **mörgæs said:**
> I'm struggling with the same Radeon card. 

When you say it worked in 11.10, was it a 32 or 64 bit installation?
that was 32-bit... I have only just made the jump to 64.

I never had any issues with the card and dual head worked "out of the box" as far as I remember.  DO NOT STRUGGLE WITH THIS IF YOU ARE RUNNING 12.04 AND DUAL HEAD, the dual head bug may well break your system badly.

---

### Post by mörgæs on 2012-05-02
Thanks for the warning. 

I'll give it a try in a 64 bit Xubuntu 11.10 when I get home.

---

### Post by The Rnegade on 2012-05-02
> **MainframeGuy said:**
> I moved to Pengolin and recently from Natty, the migration has thrown up some issues and the first I need to address is getting my dual head back!

Natty default gave me that support (go Narwal!) but Pengolin is struggling to find his precision.

My researchs so far led me to reckon I need the ATI 9.3 version, but when I run it the script falls over with ....
```

Error: ./default_policy.sh does not support version
default:v2:i686:lib::none:3.2.0-24-generic-pae; make sure that the version is being
correctly set by --iscurrentdistro
```Can a more experience person help from here on out?

I have read things about fglrx (floating point graphics?) and am contemplating trying 
```
sudo apt-get install fglrx-updates
```but reluctant in case I mess things up further,

I already forgot my card was not NVIDIA and having tried that script am paranoid it may have messed with my pengolin ;( !

[EDIT] tried that and other things suggested on an HD5470 post, but still no joy :( 

Worried the message means my 12.04 haS COST ME MY DUAL HEAD (panicing caps!)[/EDIT]

I used to run a dual as well, anyways youre gonna want the latest fglrx driver, so you'll want to install updates, next mess around in the catalyst control center for a while. It's been a while since i did this but i remeber having the same problem, so just make sure everything is enabled that needs to be. also you might need to amend your xorg.conf

---

### Post by MainframeGuy on 2012-05-02
> **mörgæs said:**
> Thanks for the warning. 

I'll give it a try in a 64 bit Xubuntu 11.10 when I get home.

do let me know how you get on, I suppose it is just possible it could work for a clean install and only screw up under a migration, which would mean I could proceed towards dual head again under 12.04, (albeit with caution! :) )

---

