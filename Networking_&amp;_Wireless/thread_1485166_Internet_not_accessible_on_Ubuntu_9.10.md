---
title: "Internet not accessible on Ubuntu 9.10"
date: 2010-05-16
forum: Networking &amp; Wireless
---

### Post by CloudOne11 on 2010-05-16
Hello friends..
I just installed Ubuntu 9.10.. It installed without any problem.. But I am unable to access internet on it.. I am using broadband service for internet.. 
The icon on the upper right corner shows a signal tower.. I tried many solutions from forum like adding ip manually, i tried to ping ubuntu.com but it shows check the address.. As if it is not detecting internet at all..
Please help me resolving it... As I am totally stuck without internet..
Thanks in advance..

---

### Post by foresthill on 2010-05-16
Is your connection wired or wireless? Sounds like wireless the way you describe it. And if it's wireless have you tried running a cable from your router to the computer?

---

### Post by CloudOne11 on 2010-05-16
It is wired connection.. It comes from router to my laptop.. it works fine on Windows 7.. 
I just tried editing nm-system-settings.con, managed=true, reading one of the posts from forum.. it also did not work.. :(
Please help....

---

### Post by Iowan on 2010-05-16
Post results of **sudo lshw -C network** Ask if you need help opening a terminal or transferring the file to an Internet-enabled machine.

---

### Post by CloudOne11 on 2010-05-16
@Iowan

Here is the result of the command..

*-network DISABLED
       description: Wireless interface
       product: AR9285 Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wmaster0
       version: 01
       serial: 78:dd:08:c4:6f:7f
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath9k latency=0 multicast=yes wireless=IEEE 802.11bgn
       resources: irq:16 memory:f4a00000-f4a0ffff
  *-network UNCLAIMED
       description: Ethernet controller
       product: Marvell Technology Group Ltd.
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:04:00.0
       version: 11
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:f2220000-f2223fff ioport:a000(size=256) memory:f2200000-f221ffff(prefetchable)



I am switching back n forth between Windows and Ubuntu for internet.. :)
Pls guide me...

---

### Post by CloudOne11 on 2010-05-16
2nd one in the list seems to be my wired connection..
pls help me guys.. waiting for your reply.. :)

---

### Post by foresthill on 2010-05-16
This is not my area of expertise, but I would suggest disabling the wireless connection in your bios. My suspicion is that Ubuntu is not sure which connection to use, so disabling one of them might allow the other to work.

Hopefully someone else will come along who knows more than I do, but until then, you might experiment with this.

---

### Post by CloudOne11 on 2010-05-16
@foresthill
Will try it.. But i am constantly switching between Ubuntu and Windows 7.. disabling wireless from BIOS wont let me use it in Windows later..

Guys, please suggest some solution.. I am not able to do anything without internet..

---

### Post by Talon2 on 2010-05-16
Here are a couple of things to consider:

- I'd recommend you install 10.04, not 9.10.  10.04 is the current release.

- Did you select a source in the Network Manager Applett (see top panel, near the right side.)  In some cases, it is necessary to tell Network Manager what to use.

---

### Post by CloudOne11 on 2010-05-16
yes.. looks like i will have to switch to 9.04..
I tried all the solutions i can found on net and nothing works.. :(
Actually it is not showing anything in network manager pallet.

---

### Post by CloudOne11 on 2010-05-17
I read in some posts that if we remove Network Manager and install WICD, then they are able to access internet. I have removed network manager completely.
As I am unable to access net at all on Ubuntu, apt will not work in my case.
Where can i download the .deb file for wicd with all dependencies from windows and install them on Ubuntu? I will have to install them manually.
Thanks in advance.

---

