---
title: "Wireless USB Adapter Problems"
date: 2006-02-13
forum: Networking &amp; Wireless
---

### Post by samIarent on 2006-02-13
Ok, first off I would like to say that I have not been using Linux for that long. I used Fedora Core 4 for about a year or two, and found it slow, tedious, and what have you. On the verge of switching to another OS (I was thinking about switching to a MAC, but decided against it), somebody told me to try Ubuntu. I installed Ubuntu, erased my Fedora partition (I never did anything on it), and am now trying to set up my wireless USB adapter (which I did not use on Fedora, mind you). I checked the wiki on this site as well as that on Ndiswrapper's, and have followed all instructions carefully. Yet I cannot get my adapter to work. I'll go more into detail now.

I have a Netgear WG111 v2 802.11G Wireless USB 2.0 adapter (I'm getting this from the box itself). I installed ndiswrapper via synaptic (I don't think it's the latest version, but most cards work without the latest, right?), inserted the disk that came with the adapter, and ran the following command:

```
sudo ndiswrapper -i /cdrom0/driver/win2000/netv1112.inf
```

After I run that, I see:

```
Installing netv1112
```

Per the instructions on HowToSetUpNdiswrapper, I then entered:

```
sudo modprobe ndiswrapper
```

I opened up the network configuration tool, but did not see my USB adapter. So I ran:

```
ndiswrapper -l
```

Which produced:

```
netv1112 driver present
```

The driver installed itself properly, yet I cannot use my wireless adapter. I checked the connection, it was secure and in the right port (the USB symbol goes up!). Can anybody offer me any help with this?

---

### Post by samIarent on 2006-02-14
I hate to double post, but I still have yet to figure out why this isn't working...I've checked my connections several times by plugging in the adapter and putting it back in securely, but this doesn't do anything. Could it be that I have a bad USB port? If so, where could I buy another one, or at least a portx to USB adapter? I'm at a loss for what to do...

---

### Post by joehill on 2006-02-15
Maybe I'm not qualified to answer because I'm having my own ndiswrapper problems but for what it's worth...

You may want to check the ndiswrapper wiki ([http://ndiswrapper.sourceforge.net/mediawiki/](http://ndiswrapper.sourceforge.net/mediawiki/)) and look at the long list of cards people have tried and see where they got their drivers.  You may have to try a driver or two from different sources to find the one that works.  HowTos I've looked at have said DO NOT use the driver that came with the card but rather one that has been tested to work, but in my case, the card works (most of the time) with the driver it shipped with and NOT with the one listed on the wiki, so you may have to experiment.

Try to find your exact card on the "List of cards known to work" page and download the driver they suggest, and if you can't find your specific card, you may find a driver that works with the same chipset.  Do "lspci" to find the number assigned to your card (0000:02:06, etc.), then do "lspci -n" to find out the pciid (mine is 14e4:4318 (rev 2)).  Make sure any driver you try to use has the pciid you get from "lspci -n".  I searched through the ndiswrapper wiki list of cards to find others who had used that same chipset and gotten it to work and looked at the tweaks they used.

I hope this helps.

---

### Post by francisco_athens on 2006-02-19
"lsusb" command gives a more concise list if using a USB based device. you should not get only "driver present" from ndiswrapper -l, but also something like "hardware detected."  That will mean that ndiswrapper is working (at least reconizing that hardware).  
For a while I thought that my wg111v1 was a v2 variant (as was posted on the box) but inspecting the output of lsusb and checking the serial number of the device informed me of its true v1 nature!  

Good luck!

---

### Post by samIarent on 2006-02-27
Ok, so I tried lspci and lspci -n. After I ran lspci, I received the following:
```

0000:00:00.0 Host Bridge: Silicon Integrated Systems [SiS] 5600 Host (rev 11)

0000:00:00.1 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE] (rec d0)

0000:00:01.0 Isa bridge:Silicon Integrated Systems [SiS] SiS85C503/5513 (LPC bridge) (rev b1) 

0000:00:01.1 ff00: Silicon Integrated Systems [SiS] ACPI

0000:00:02.0 PCI bridge: Silicon Integrated Systems [SiS] virtual PCI-to-PCI Bridge  (AGP)

0000:01:00.0 Vga compatible controller Silicon Integrated Systems [SiS] 86c326 5598/6326 (rev 0b)

```

When I run "lspci -n", I get:
```

0000:00:00 0600: 1039:5600 (rev11)
0000:00:00.1 0101: 1039:5513 (rev d0)
0000:00:01.0 0601: 1039:0008 (rev b1)
0000:00:01.1 ff00: 1039:0009
0000:00:02.0 0604: 1039:0001
0000:01:00.0 0300: 1039:6326 (rev 0b)

```

When I enter "lsusb" into terminal, it registers as though I had entered a regular word (example, typing "qwerty" will merely skip to the next line). Whenever I specify some parameters (example, lsusb -D lsusb -v), I am told that I am not entering them correctly, at which point the different options for the command appear. Does this mean that, for whatever reason, my adapter is not being recognised?

Ok, so now that I have listed the strings that I received from lspci/lspci -n, can somebody tell me what I need to do? I'm not able to make sense of it. I've only started working with Linux, and I figure that if I can get over this hurdle, then I'll never have another OS for my home computer. 

Oh, and if I need a new wireless card, does anybody have any suggestions? Prefferably something cheap and easy to install. But I'm not picky, I'll take almost anything at this point.

---

