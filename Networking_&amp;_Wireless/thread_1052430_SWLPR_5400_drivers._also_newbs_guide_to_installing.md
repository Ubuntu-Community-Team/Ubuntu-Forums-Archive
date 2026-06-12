---
title: "SWLPR 5400 drivers. also newbs guide to installing drivers"
date: 2009-01-27
forum: Networking &amp; Wireless
---

### Post by rattis on 2009-01-27
I'm having trouble using my SWLPR 5400 wireless card to conenct. with it in the machine an the windows drivers running through the clever conversion application the xubuntu doesn't even start up.

So does anyone have any drivers available? Or can I DL an application on my mac and transfer via USB that will sort it?

I have the linux drivers that came with the product, but they are very beta-product-esq. And I don't know how to get them into a usable format. They are in the form of three .tar.gz files with some other seemingly random files like makedrv and ifcfg-wlan0.

A pointer to a newbs guide to doing this kind of stuff would be great.

---

### Post by nixscripter on 2009-01-28
You can use the Windows drivers in Linux (if they are for Windows XP) with a package called **ndiswrapper**. A howto can be found here: [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

Hope this helps.

---

### Post by fuzzyworbles on 2009-01-28
this tar.bz file your talking about is probably source code, too. if you wanted, you could just compile them. to do that you'll need the kernel headers. it's easier than you think. just get the headers in synaptic for the kernel you're currently running (run: uname -r) and read the INSTALL or COMPILE or README files that are undoubtedly in the tar.gz file you downloaded. (which probably just tell you to run make, make install, and modprobe)

---

### Post by rattis on 2009-01-29
The trouble is that I understand the words you've written but not the order you've put them in!

After trying ndiswrapper (found a youtube video of how to do it!) in terminal and in GUI (windows wireless drivers) it still failed to bot with the card in the machine.

Simple solution was to reinstall with the card in, and the wired ethernet card connectted when installing, seemed to work fine until when half way through playing a video from my network mounted drive it froze and now gives a light blue screen on start before getting to the login screen. Hoping it's a graphics driver issue (should be easyish to solve) and not a NIC issue.

---

### Post by nixscripter on 2009-01-29
I couldn't tell from your description; does the wireless card work?

---

### Post by rattis on 2009-01-30
It does now. It seems that just reinstalling xubuntu completely with the wired ethernet connected solves everything.

---

### Post by nixscripter on 2009-01-30
In that case, please mark the thread as Solved.

---

