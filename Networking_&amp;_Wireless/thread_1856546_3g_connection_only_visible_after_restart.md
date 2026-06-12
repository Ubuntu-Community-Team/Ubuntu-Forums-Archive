---
title: "3g connection only visible after restart"
date: 2011-10-08
forum: Networking &amp; Wireless
---

### Post by Ekeout on 2011-10-08
Hi.

I'm using 11.04 without any major updates (on 3g internet connection). 
I'm using the default connection for 3 ireland in the network manager, and it works alright.

The issue is that under the connections menu (the two arrows in the top panel) the "Mobile Broadband" category doesn't appear if I don't restart the system once after I have powered the machine on, meaning there's no "Three Ireland default" menu item there to use to connect without first restarting. (The 3g modem is connected when the machine is powered on)

lsusb reports the 3g modem as "Huawei Technologies Co., Ltd. E220 HSDPA Modem / E270 HSDPA/HSUPA Mode" and I'm running the OS on a HP 530 laptop.

Any suggestions?

---

### Post by iamnotthemessiah on 2011-10-08
this has solved it for me before for me before, simply go to 'edit connections' - mobile broadband tab delete your connection in the connection manager and create a new one.hope it does for u too

---

### Post by alexfish on 2011-10-09
hi

if there  are configuration problems try using sakis3g .. use the menu ;; configure device only
**[*Sakis3G* - All-in-one script]("http://www.google.co.uk/url?sa=t&source=web&cd=1&sqi=2&ved=0CCQQFjAA&url=http%3A%2F%2Fwww.sakis3g.org%2F&rct=j&q=sakis3g&ei=XnKRTufGI8WXhQef1ekH&usg=AFQjCNFR0OA7GJQY3djYswddHkMjARyyDw&cad=rja")**

if using 11.04  sakis3g will look in the etc/usb_modeswitch.d files for the device

also look here ::  [Natty, known bugs, fixes and work arounds]("http://ubuntuforums.org/showthread.php?t=1749312") post  #[**30 :::**]("http://ubuntuforums.org/showpost.php?p=10793568&postcount=30")

alexfish
[]("http://ubuntuforums.org/showpost.php?p=10793568&postcount=30")

---

### Post by Ekeout on 2011-10-09
Thanks for your replies.

I tried recreating the connection, to no avail.

alexfish: I'm afraid that's all a bit over my head. For example, just running the sakis3gscript requires 15 A4s to explain? [http://wiki.sakis3g.org/wiki/index.php?title=Sakis3G_invocation](http://wiki.sakis3g.org/wiki/index.php?title=Sakis3G_invocation)

Switching..I don't know what it means in this context.

The issue is very reliable in that the 3g connection cat never shows up after poweron, and sometimes the machine needs to be rebooted twice before it does.

When it is detected however, it is always recognized (after any number of resets) until poweroff and on again,.

I'll read on about the sakisscript and stuff anyway and become wiser. It's just that Ubuntu is for human beings until something doesn't work and then that slogan becomes sort of n/a. Which is understandable.

---

### Post by alexfish on 2011-10-10
sakis3g can be called from the terminal, or can sometimes be run from the source file if downloaded or copied to the home directory, there is a how install sakis3g here,
[[COLOR=#000000]How To : Mobile Broadband Connections [ Ubuntu 10.10 : 10.04 : 9.10 ][/COLOR]]("http://ubuntuforums.org/showthread.php?t=1466490") post #5
 
sakis3g will use any menu/dialoge boxes available on the system , most linux distro's have them, should be no need to use the terminal commands to configure the device,
 
from what i am seeing , it most likely a problem  loading the driver after mode_switching ,, sakis3g will resolve this.
 
post back here if you require further help on installing or running sakis3g from the source file
 
regards
 
alexfish

---

