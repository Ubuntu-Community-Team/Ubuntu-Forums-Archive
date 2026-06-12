---
title: "Netgear 150 and Ubuntu 12.04"
date: 2013-02-27
forum: Networking &amp; Wireless
---

### Post by mtclare on 2013-02-27
So I am staying at a hotel and I need wi-fi to connect to the internet. I bought a 25$ netgear USB adapter and expected it to work right out of the box.
 
Well, it occasionally works but its very slow and disconnects often. Its as bad as can be without not working at all.
 
I know its not the hotel's wifi because I have a laptop with windows that connects and stays connected just fine.
 
Is there any adapter that is just plug and play for Ubuntu 12.04? I don't want to spend hours with ndiswrapper (I have already tried) trying to fix this.
 
Thank you.

---

### Post by ahallubuntu on 2013-02-27
~

---

### Post by kurt18947 on 2013-02-27
I agree with ahallubuntu re the RTL8188CUS adapters.  They're useful for laptops, they only protrude about 3/8"/1 cm.  I've always had to build the driver though using the included installer script.  It's pretty simple if you're at all comfortable with terminal/bash commands - it's copy/paste.  My experience with the native driver for the RTL8188CUS is about like your present Netgear - it may connect, or it may not.  And if it does, it'll soon disconnect.

A couple other adapters that are truly plug -n- play for me are Dlink DWA-131 & it's twin Trendnet TEW-649UB.  They're both RealTek 8192SU chipsets.  They do have an issue with resuming after suspend but that's pretty easy to fix.  Another more involved solution would be to replace the internal wifi card in your laptop with one that's more linux friendly.  There are more potholes doing this but it's the cleanest most convenient solution if you machine will accommodate it.  Some notebooks whitelist WiFI cards - they will only work with certain ones.

Edit for anyone searching.  There is apparently a new version of the Dlink DWA-131 that IS NOT plug 'n' play.  I just read this in another thread so heads up.  The new one is v.2 firmware.

---

### Post by sir4taye on 2013-04-06
since 11.10, I've had trouble with my Ralink RT2870/RT3070 chipset keeping data flowing. Connection stays connected, but data slows excruciatingly slow or stops all together intermitantly. Even using the rt2800usb driver.

kurt18947, when you say > **kurt18947 said:**
>  I've always had to build the driver though using the included installer script.  It's pretty simple if you're at all comfortable with terminal/bash commands - it's copy/paste.  My experience with the native driver for the RTL8188CUS is about like your present Netgear - it may connect, or it may not.  And if it does, it'll soon disconnect.
,
do you mean that you setup drivers yourself? Using ndiswrapper, or???

Step by step direction would be helpful on how you have great success with the RT2870/RT3070 chipset.

---

### Post by kurt18947 on 2013-04-07
> **sir4taye said:**
> since 11.10, I've had trouble with my Ralink RT2870/RT3070 chipset keeping data flowing. Connection stays connected, but data slows excruciatingly slow or stops all together intermitantly. Even using the rt2800usb driver.

kurt18947, when you say ,
do you mean that you setup drivers yourself? Using ndiswrapper, or???

Step by step direction would be helpful on how you have great success with the RT2870/RT3070 chipset.

I have no experience with the RT2870/RT3070 chipset.  I *did* purchase a cheap micro adapter off Ebay  that uses an RT5370 chipset.  It's plug 'n' play in 12.04 and later but the signal strength is fairly weak compared to other adapters.  Perhaps the fact that it is a generic $6 device has something to do with that:tongue:.  I use RealTek's driver for the Edimax EW-7811Un which uses a RealTek 8188CUs chip.  Here is a thread I started earlier that I hope is understandable.  If not, please post back and I'll try to clarify.

[http://ubuntuforums.org/showthread.php?t=2092934&highlight=8188CUs](http://ubuntuforums.org/showthread.php?t=2092934&highlight=8188CUs).

Do note that you want to keep this download where you can find it again.  If you update and get a new kernel version, it'll likely disable the wifi adapter.  Rerun the install script and you should be back in business.  On a positive note, the Edimax EW-7811Un seems semi-functional using the native driver in 13.04.  I say semi-functional because it occasionally locks up.  Unplugging, waiting a second and plugging back in seems to solve the problem.

---

### Post by norwest29 on 2013-04-16
how do i exactly replace the driver for RTL8188CUS? i've copied/pasted the text (from the "install.sh" file it came with) in terminal. #noob
.

---

### Post by ahallubuntu on 2013-04-16
~

---

