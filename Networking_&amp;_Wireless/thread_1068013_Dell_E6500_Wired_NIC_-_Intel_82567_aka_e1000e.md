---
title: "Dell E6500 Wired NIC - Intel 82567 aka e1000e"
date: 2009-02-12
forum: Networking &amp; Wireless
---

### Post by outlawpsd on 2009-02-12
I am in need of help badly.  I am completly new to linux and I have been unable to get my wired NIC on my laptop to work. I jsut installed Ubuntu 8.1 last weekend and ran all the updates via my wireless. Everything else works perfectly so I am hoping this is an easy fix.  I spent two days searching for the anwser but no luck so far.  Kernal version is 2.6.27-11.  Sudo modprobe e1000e gives this result:

[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee10000 (reserved)
[    0.000000] PM: Registered nosave memory: 00000000fee00000 - 00000000fee10000
[    0.000000] PM: Registered nosave memory: 00000000fee10000 - 00000000ffe60000
[    1.816118] e1000e: Intel(R) PRO/1000 Network Driver - 0.3.3.3-k6
[    1.816120] e1000e: Copyright (c) 1999-2008 Intel Corporation.
[    1.816184] e1000e 0000:00:19.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[    1.816195] e1000e 0000:00:19.0: setting latency timer to 64
[    1.880633] e1000e 0000:00:19.0: PCI INT A disabled
[    1.880663] e1000e: probe of 0000:00:19.0 failed with err -5

Not sure what to do from this point forawrd.  I have the patched kernal do no luck getting it ruuning.  Also I did check to see if it was in the blacklist but it is not here either.

---

### Post by outlawpsd on 2009-02-13
bump

---

### Post by outlawpsd on 2009-02-13
i did a lshw -C network and this is what I got:  

*-network UNCLAIMED     
       description: Ethernet controller
       product: 82567LM Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: cap_list
       configuration: latency=0

What does it mean by network unclaimed?

---

### Post by outlawpsd on 2009-02-13
Would I have a better chance of getting help if I posted this in the Laptop forum?  I am really need to get this working.

---

### Post by quinnten83 on 2009-02-14
I think ppl just don't know the answer, that is why they haven't replied.
I have a similar problem of sorts. Neither on my compaq evo n610c or dell lattitude D630 does the NIC function, they both worked fine under 8.04.
I solved my problem by downloading WICD and installed it. you'll need to remove network-manager first.
I tried open suse today, and had the same problem. It just might be newe drivers in the kernel for some network cards, or I don't know.
Open suse was running kde 4.2, and ubuntu was running gnome. It really isn't clear what is causing this.

---

### Post by outlawpsd on 2009-02-14
Well here is some more info if it helps anyone.  I did not want the boot screen to be on, I wanted to see what was going on during boot up and I noticed something.  I am getting a statement in between the time the kernels are displayed and all the text begins streaming down the page saying something to the affect that there is a NV Corruption and it coming from the NIC.  However its not corrupt because when I put the other hard drive I have in the laptop that has Windows XP on it, the NIC in question works perfectly.  Hope the update helps.

---

### Post by odium1 on 2009-02-15
what kernel are you running?

type this in the term and post the results:
```
uname -a
```

---

### Post by chili555 on 2009-02-15
This sounds scary!

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/263555/](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/263555/)

If you Google '82567LM ubuntu eeprom', you will read lots of scary stuff.  It is evidently fixed in kernel 2.6.27-14, whereas Ubuntu has only progressed to 2.6.27-11.> However its not corrupt because when I put the other hard drive I have in the laptop that has Windows XP on it, the NIC in question works perfectly.What is corrupt in Linux is not necessarily corrupt in Wndows and vice versa.

If it were me, I would blacklist e1000e and I would save a copy of my eeprom with:```
sudo ethtool -e eth0 > savemyeep.txt
```I hope someone else will jump in here with additional insight.

---

### Post by outlawpsd on 2009-02-15
2.6.27-11-generic.  I downloaded Ubuntu two weekends ago and installed it.  All updates applied from the update service.  

As a side note I even tried booting with the 2.6.27-7-generic that was listed among the choices of kernals to boot from when you first power up.  It did not work either.

---

### Post by outlawpsd on 2009-02-15
Chili - correct me if I am wrong but all the information I have read, and there is a lot of miss information out there so hopefully we can get it straighted out here, the bug was fixed in mid October of 2008 with kernel 2.6.26-6.  Actually anything higher the way I understand and from what I have read.  

So that lead me to the next quest then.  How do I install 2.6.27.14 so I can get the NIC in question to work?

---

### Post by chili555 on 2009-02-15
> the bug was fixed in mid October of 2008 with kernel 2.6.26-6I didn't see that. Doesn't mean it didn't happen; it may mean i'm just old and near-sighted!

Do you have a link you can refer me to?

---

### Post by outlawpsd on 2009-02-15
Chili -

Here is one of many of the links that I have found on the e1000e driver specific to the Intrepid kernel.

[http://fpreto.wordpress.com/2008/10/06/e1000e-driver-is-back-on-intrepid/](http://fpreto.wordpress.com/2008/10/06/e1000e-driver-is-back-on-intrepid/)

All other articles are from around the same time period - beginning to mid October.  

To follow the whole blog you can go here:

[http://en.wordpress.com/tag/e1000e/](http://en.wordpress.com/tag/e1000e/) 

Can you explain more on what it would take to go to a new kernel like you mentioned in your previous post.  Please keep in mind that I have only been using Linux now for 2 weeks.  :)

---

### Post by chili555 on 2009-02-16
Before you actually install it, I suggest trying it on a Live CD to be sure it works as expected. I suggest downloading the appropriate .iso image here: [http://cdimage.ubuntu.com/daily-live/20090216/](http://cdimage.ubuntu.com/daily-live/20090216/) (probably the i386.iso) and burning the .iso image to a CD. Then run the live CD and see if your ethernet works and connects. If so, we can install the Jaunty kernel. I will write a separate post covering that, however, let's "try before buy."

---

### Post by chili555 on 2009-02-16
If, and only if, you determine that the Jaunty kernel fixes your problem, install the kernel permanently like this:

*Open System -> Admin -> Synaptic
*Open Settings -> Repositories -> Third Party Software
*Click 'Add' and copy and paste this line:```
deb http://archive.ubuntu.com/ubuntu/ jaunty main restricted
```
*When you close Repositories, you will be prompted to reload, so press Reload.
*Search Synaptic for 'linux-image-generic.' You will see that there is a listing for 2.6.27-xx but a later version, 2.6.28.7-7 is available. 
*Mark it for upgrade and click 'Apply.'
*Reboot
*Remove the Jaunty from Synaptic immediately!!!

---

### Post by outlawpsd on 2009-02-17
Well I downloaded the latest Live CD and ran it last night.  It still does not see my NIC.  No sure what that means.  Is there a resource that I can look at to see exactly what driver is compiled in the kernel?  I would be curious to see the version that is being installed.

---

### Post by chili555 on 2009-02-17
```
modinfo e1000e
```It will show something like:> ~$ modinfo e1000e
filename:       /lib/modules/2.6.27-11-generic/kernel/drivers/net/e1000e/e1000e.ko
version:        0.3.3.3-k6Did you try explicitly inserting the module:```
sudo modprobe e1000e
```Then does:```
ifconfig
```show your eth0 interface?

---

### Post by odium1 on 2009-02-17
i would download **kernelcheck** and get it to build the latest kernel (2.6.28-*) and try that one. [http://kcheck.sourceforge.net/]("http://kcheck.sourceforge.net/") that link should work.

---

