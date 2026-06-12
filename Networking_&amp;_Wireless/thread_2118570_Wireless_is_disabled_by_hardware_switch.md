---
title: "Wireless is disabled by hardware switch"
date: 2013-02-20
forum: Networking &amp; Wireless
---

### Post by Berzerkerwar on 2013-02-20
I have an old Compaq Presario CQ50 that I installed Ubuntu on. However, the wireless won't work. The light that should be blue when it's on is orange (for off), and it says wireless is disabled by hardware switch under wireless networks. I have tried things like sudo rfkill unblock all, but to no avail, I have also tried to go to the additional drivers and I switched the Broadcom Corporation: BCM4312 802.11b/g from "Do not use this device" to Using Broadcom, but it doesn't help at all. If anyone knows how I can fix this problem I'd appreciate it, thanks in advance! :)

---

### Post by Berzerkerwar on 2013-02-21
I have an old Compaq Presario CQ50 that I installed Ubuntu on. However, the wireless won't work. The light that should be blue when it's on is orange (for off), and it says wireless is disabled by hardware switch under wireless networks. I have tried things like sudo rfkill unblock all, but to no avail, I have also tried to go to the additional drivers and I switched the Broadcom Corporation: BCM4312 802.11b/g from "Do not use this device" to Using Broadcom, but it doesn't help at all. If anyone knows how I can fix this problem I'd appreciate it, thanks in advance!

---

### Post by Mark Phelps on 2013-02-21
I know how I "fixed" it with an old Compaq laptop I had running Ubuntu -- I went into Windows, turned ON the switch (it lit blue) and taped cardboard over the switch so it couldn't be turned off -- and rebooted into Ubuntu.

Sorry, but I searched for years for solutions to this from inside Ubuntu -- and found nothing.

Maybe you'll have better luck than me ...

---

### Post by ageofsteam on 2013-02-21
Just curious: did you have the wireless turned "off" when you installed Ubuntu?  I have a Sony laptop with a wifi switch, and unless I have it turned on when installing Ubuntu, it won't work & I have to reinstall it again.  (As I've used that comp for most of my weird linux experiments, I've had to reinstall A LOT.)  I'm not sure that yours would be the same as my Sony, but I thought it might be worth mentioning...

---

### Post by QIII on 2013-02-21
*Threads **merged.***

Please do not create duplicate threads.  It dilutes the community's effort to help you and causes confusion.

Thanks and best wishes!

---

### Post by varunendra on 2013-02-22
> **QIII said:**
> *Threads **merged.***
..and moved to Networking & Wireless.

-------------
@ Berzerkerwar,
I'd like to confirm if the basic things are okay. Please post outputs of-
```
lspci -nnk | grep -iA2 net
lsmod
rfkill list all
```

Also, take a look at this thread : [http://ubuntuforums.org/showthread.php?p=12489467](http://ubuntuforums.org/showthread.php?p=12489467)

---

### Post by Jack Waugh on 2013-07-13
At least once, I do/observe this sequence:  Power off my CQ50 with a wireless dongle plugged into it.  Power it on and hit the function key for information.  Observe that the wireless light is orange, and the light on the dongle is off.  Check that the computer is indeed a CQ50 as shown on the screen.  Three-fingered salute.  Wireless light turns blue, but dongle light stays off.  Boot to a Lubuntu 12.04 (precise pangolin) 32-bit live CD.  Right-click on network-manager icon in system tray.  Wait for CD to churn.  Observe that **the "enable wireless" option is not greyed out!**  Choose "enable wireless".  Observe that the light on the dongle comes on.  Left-click the network-manager icon and observe that the menu offers local access points both under the internal radio and the dongle.  Shut down O/S and remove CD.  Boot from internal magnetic disk to various types of desktop session.  Observe that dongle light remains on.

So, it looks as though powering off gives one a fresh start toward re-enabling wireless.

---

### Post by dontquoteme on 2013-07-13
I had network manager generate this error yesterday. (Exact same errors about hardware...)
In a fit of temper.... went to software centre....

Used software centre - WICD Network Manager - downloaded WICD.
WICD got connectivity back.
Top panel - switch On WIFI (or toggle to switch Wifi off)


Suddenly Network Manager works as normal.

I'm keeping WICD installed - as my insurance plan against this glitch.

Hope this solution works for you guys too.  Simple solutions are the best :)

---

