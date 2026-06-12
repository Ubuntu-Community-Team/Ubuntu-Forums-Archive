---
title: "TPLinked Wifi usb TL WN727N has stopped working after upgrade to 11.10"
date: 2012-02-05
forum: Networking &amp; Wireless
---

### Post by huzefa420 on 2012-02-05
Hi all,

My wifi has stopped working since I upgraded to Ubuntu 11.10. I have a generic Intel Deskop and am using the TP Link TL WN727N wifi usb adapter. For reasons too long to explain, I do not have access to a wired connection for this desktop but I can copy stuff onto a USB with my windows laptop for installation on the ubuntu machine. 

iwconfig only gives me 
lo no wireless extensions. 
eth0 no wireless extensions.

lsmod not showing an wlan module

I have tried many many things to no avail. There is a static green light on my wireless usb stick. FYI was working fine before the upgrade (though when I did the last upgrade, I had to add a few lines to blacklist.conf to make it work, those lines are still there, I tried removing them, restarting, then readding, restarting, but no luck). 

Would really appreciate some help with this. 

Thx, 
Huzefa

---

### Post by westie457 on 2012-02-05
Welcome to UF

Try the suggestions in this thread [http://ubuntuforums.org/showthread.php?t=1903536](http://ubuntuforums.org/showthread.php?t=1903536)

If they do not work post here again and we will try something else.

Thank you

---

### Post by huzefa420 on 2012-02-05
Hi Westie457,

Thanks for the quick reply! Unfortunately that solution requires a wired connection which I don't have access to on the linux machine. 

My wifi works on my windows laptop, any way I can download files here, transfer them on a usb and then run the updates offline?

Thx,
Huzefa

---

### Post by huzefa420 on 2012-02-06
Bump! 

My poor mom is going nuts without the internet on her computer :(

---

### Post by barong234 on 2012-02-06
first off all you need to add the firmware to your kernel, then add driver, reboot the machine it should work.

---

### Post by anymoose on 2012-03-20
HI! This is the definitive fix for Ubuntu 11.10 and TL-WN727N(V3)

Use this link (only) if kernel version is shown below;
Ubuntu 11.10

ls /lib/modules

3.0.0-12-generic

Web Link;
[http://ubuntuforums.org/showthread.php?t=1903935&highlight=5370](http://ubuntuforums.org/showthread.php?t=1903935&highlight=5370)

Use user Chili555 post #2. Everything is done in post #2 ie no
files to download no compilation, no other changes. This fix
must be entered carefully; all spelling, spaces and capital/lc
letters *must* be correct. Worked for me after reboot. Test
your adapter with MS-Win XP with Included utility on CD ahead 
of time, if possible.

Not sure if this will work in Ubuntu live filesystem on CD for
obvious reasons. Works when filesystem is on HD disk and USB stick.

Signed; Anymoose

---

