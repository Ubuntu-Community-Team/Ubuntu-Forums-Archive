---
title: "Realtek 8111D problems"
date: 2009-10-07
forum: Networking &amp; Wireless
---

### Post by TheoL on 2009-10-07
Hi,
 
I have just installed Ubuntu Server 8.04 LTS on an intel D945GSEJT motherboard. 
 
This is an Intel Atom based motherboard includes the Realtek 8111D Gigabit ethernet controller.
 
The module loaded to suppoprt this is the r8169 module. However, I found the operation to be intermittent.
 
1. The first time the unit was powered up, it detected and correctly initialized the network interface.
2. Subsequent power cycles "randomly" work. Sometimes the device is not recognised and does not even load the driver, and other times the driver loads, but the network traffic is discarded. In this state, ifconfig shows a random number for the RX packets dropped. (I mean random - and it changes to a new random number every time you run ifconfig).
 
With this driver, there was about a 1-in-20 chance that network intialized correctly.
 
Searching this and other forums, there seem to be similar problems on other systems.
 
I downloaded the the latest Linux driver source from the Realtek website and build and installed the new driver. The new driver module is r8168 - and this now seems to work OK. I have some more testing to do - but for now I can unload and load the driver - and it works every time. 
 
The build process I used was a bit of a hack and guess based on a few how-to's - and I am not sure I did a good job. For one thing the "dmesg | grep r8168" instruction includes:
 
r8168: no version for the "struct_module" found: kernel tainted.
 
 
A couple of questions:
1. Is the newer driver included in the newer versions of Ubuntu?
2. If not already in the newer kernels - how does one go about getting it added?
3. Is there a good "how-to" for building a single kernel (driver) module without re-compiling the entire kernel? 
4. Should I worry about the "kernel tainted" message.
 
Thanks
 
Update: See [http://ubuntuforums.org/showthread.php?t=1022411](http://ubuntuforums.org/showthread.php?t=1022411) - provides step by step instructions to add the new driver ...

---

