---
title: "DWA 552 causing serious problems"
date: 2009-05-07
forum: Networking &amp; Wireless
---

### Post by 3gotist on 2009-05-07
After some serious googling, I've decided to just post this problem and hope to get some help with it.

I have a D-Link DWA 552 wireless adapter installed in my PC. The card works perfectly in Vista (dual boot) but completely freezes up my system when I try to connect to a network from Ubuntu. Versions I've tested so far are 8.10 and 9.04. 9.04 is freezing as soon as it boots to the desktop now, as well.

I've done a fair bit of reading on this subject, and it seems like I'm not the only one having this issue. I'd try using madwifi, but when people start talking about compiling things from source and monkeying about with the kernel, I get pretty sketched out. 

I could probably still return the card if I had to. If that's what it comes down to, is there a make/model of PCI wireless adapter that 100% works out of the box with the newer releases of Ubuntu?

---

### Post by dkartik on 2009-06-14
I'm having the same problems.  It seems like every few seconds or minutes, my connection drops with the DWA-552.  I'm really getting sick of it, and don't want to have to go out and get a new wireless card.  Can anyone out there help?

---

### Post by eiceak14 on 2009-06-14
I'm having the same problems with it as well. I'm running 2.6.30-020630-generic ... i've compiled the latest wireless-compat-2.6; And done everything else that I 'understand' how to do.  ath9k still drops out after only a few moments of being connected.  I basically had to drop down to the b/g version of their card and use ath5k.  My wireless connection works perfectly with that setup.

---

### Post by 3gotist on 2009-06-18
So I rearranged some furniture to put my computer within reach of my router via a cat-5 cable run through the floor into the basement, where I live. Having done that, I did some more searching around and found a decent tutorial for installing madwifi. In the end, that didn't work either. More searching for answers, and finally I came across instructions for getting and installing drivers from Linux Wireless.

[http://wireless.kernel.org/en/users/Download]("http://wireless.kernel.org/en/users/Download")

Read through it once, followed the instructions, and I am now running flawlessly with my DWA-552.

---

### Post by OceanWinds on 2009-07-21
I am having the same issues, and cannot seem to follow the work around.  I am an Ubuntu noob though.  *sigh*

---

### Post by OceanWinds on 2009-07-21
well found a way way easier work around... good for noobs like me.

Anyway I found a tutorial regarding wicd.  It can be installed via the synaptic package manager.  Search wicd and install it.  At the same time it removes the network manager...   and voila!  wireless now works like a charm :)

---

