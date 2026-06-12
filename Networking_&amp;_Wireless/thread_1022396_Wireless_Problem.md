---
title: "Wireless Problem"
date: 2008-12-26
forum: Networking &amp; Wireless
---

### Post by adwol on 2008-12-26
Hi,

I have been using ubuntu on my laptop with no problems for ages now. I recently installed it on a desktop computer and the wireless doesn't work. I tried a number of things. 

Running lshw, I find my network card and wireless card both with drivers and both with virtual interfaces. Both these interfaces are disabled. I cannot enable them and they seem enabled in the GUI.

I tried ndiswrapper initially but I don't think it worked properly. Is this likely to be a driver problem and if so should I try ndiswrapper again?

Any help would be much appreciated,
Adam

---

### Post by AlexBellisBrown on 2008-12-26
What is the make and model of the Wifi card?

---

### Post by DWade on 2008-12-26
Also,

Was it working before you updated or did it not work from the beginning after a fresh install?

or  Did you use aptoncd, or copy packages to /var to install updates and programs after install, and then tried to setup wireless.


I am having a problem with the network manager applet, with kernel 2.6.27.11, I had to uninstall it.  My aircard was no longer recognized with the new kernel.  but works perfectly with 2.6.27.7 and 2.6.27.9.

---

### Post by adwol on 2008-12-27
Its a belkin F5D7000 and is quite old which is maybe why it doesnt work.

It was a completely fresh install on a previously windows PC. I initially thought there wasn't a driver for the card but using lshw, there is a standard one for the broadcom chipset.

I downloaded the belkin driver from their website and tried to use that. It doesn't appear to have a .inf file but I found a .ntf file or something which looked like an inf and renamed it. This seemed to work with ndiswrapper except that my wireless still doesn't work!

Do you still think its a driver problem?

---

### Post by AlexBellisBrown on 2008-12-27
Most likely, yes. Have you read this thread? [http://ubuntuforums.org/showthread.php?t=338070](http://ubuntuforums.org/showthread.php?t=338070)

---

