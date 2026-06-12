---
title: "help with nic install"
date: 2010-02-06
forum: Networking &amp; Wireless
---

### Post by ulao on 2010-02-06
Hey guys, never really had to install a driver on linux before, I always just found a card that worked. but this time I need to get a specific card working. In this case the intel pro 1000 ( e1000 ), I ran the make install and seemed to go well, I tried to load the module ( modprobe e1000 )and it did not report an error ( not sure how to tell if that worked ) I do not have a eth0, or any other eth but the lo. What would be the next step in try to get this working? I dont see any issue in dmesg? 

I'm not able to put much in here because I have no net connection.. Kinda sucks.. I do have a e1000.k0 file in kernel/drivers.net I always though it was .o ?

---

### Post by chili555 on 2010-02-06
> I always though it was .o ?It was, a few years ago.> it did not report an error ( not sure how to tell if that worked )That's how you know! No error means no problem.

There was no need to compile from a tarball as e1000 is in the kernel already. If it did not attach to your device and create an interface, there's a bigger, underlying problem. Let's see what the kernel reports:```
dmesg | grep e1000
```Thanks.

---

### Post by ulao on 2010-02-06
I tried a search myself and found nothing.  I did try a grep and also reported nothing. 

> e1000 is in the kernel already. Yeah this is what bugs me, my server picked it right up ( umbuntu ) my workstation did not (kubuntu) but my server is 8. something and my WS is 9.10 . I forget the thread but did a make on it because of the advice in that thread. However it did not work.. 

**Update: here is the link for reference [http://ubuntu-ky.ubuntuforums.org/showthread.php?t=601222](http://ubuntu-ky.ubuntuforums.org/showthread.php?t=601222)**

Thx for the help, what would be the next move?

---

### Post by chili555 on 2010-02-06
How about this, please:```
lspci -nn | grep Ethernet
```Let's troubleshoot from square one.

---

### Post by ulao on 2010-02-06
Huh not familiar with lspci, guessing some sort of pci inquiry.  I did so ( paying attention to case ) "Ethernet" found nothing?  Staring to think the pci card is not registering in the pci slot.. Going to re-seat it and report back.

---

### Post by ulao on 2010-02-06
Well it does not show in the pci device listing, but I'm not sure if that is a must or not. I tested the car on another system, and its ok. It is a bit strange that the network activity light is not flashing, normally it does even if the os is up. Tried another boot up with no luck. Going to change out the MB and report back, but guessing its not a linux thing after all.

---

### Post by chili555 on 2010-02-06
> Huh not familiar with lspci, guessing some sort of pci inquiry.It means 'list all PCI devices.' Qualifiers allow varying degrees of detail. grep means just show details matching a pattern; in this case, those with Ethernet in the name.> guessing its not a linux thing after all.That's my suspicion, as well. I will be fascinated to hear the outcome.

---

### Post by ulao on 2010-02-06
Will do..

Turn out I dont have the same mother board on hand, I know on windows systems it can be a bad thing to change out boards with other chip sets. what about linun?

---

### Post by chili555 on 2010-02-06
It's a non-issue. I love to swap mother-boards, drives, memory, NICs, etc. and never have a problem, unless, of course, the device in question is defective.

---

### Post by ulao on 2010-02-07
Well I tested 4 boards and all of them can not see this nic. So I had no choice but to swap out a completely different board. The system tried just about every video mode and gave up.  but the good news is I have the nic working just fine. So now I will try to figure out the video, guess I need to start a new thread huh?

---

### Post by chili555 on 2010-02-07
Yessir; ideally, over in Multimedia & Video.

Glad the ethernet is working.

---

