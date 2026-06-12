---
title: "Dell Mini 9 wireless not working."
date: 2009-10-30
forum: Networking &amp; Wireless
---

### Post by T-Keith on 2009-10-30
I have a Dell mini 9 that came with Dell's 8.04.  I upgraded to 9.04 NBR which I loved.  Now that 9.10 is out, I thought I'd try it.  But for some reason running off the usb drive wireless will not work.  I used the hardware drivers utility to activate the STA driver, then restarted, but it says that the driver is activated but not in use.  I tried reinstalling, using synaptic, the B43 driver, but it nothing worked.  Same thing with the RC.

Could it be that Ubuntu's "benchmark" computer doesn't even work properly?

---

### Post by Leprechaun7 on 2009-11-01
I've got same exact problem, everything seems fine but no wireless detected. This is not good.

---

### Post by GexNZ on 2009-11-01
Same problem on a Dell Mini 10v.  Installed to the disk off a USB key, rebooted into Ubuntu, sound and video working fine.  But the wireless doesn't seem to be working.

Followed instructions on [http://ubuntuforums.org/showthread.php?t=1304978&highlight=dell+mini+wireless](http://ubuntuforums.org/showthread.php?t=1304978&highlight=dell+mini+wireless) and now its working fine.

To fix it run:
sudo apt-get install bcmwl-kernel-source (or install via Synaptic)

Reboot and you're good to go!

---

### Post by T-Keith on 2009-11-01
That fix did not work for me.  AFAIK, the hardware drivers utility does the same thing.  I tried uninstalling and resinstalling through synaptic and it still did not work.  However after having trouble installing Kubuntu on my desktop from the same flash drive, I'm beginning to suspect the drive.  Although check for disc errors came up with no errors.

---

### Post by kouakou on 2009-12-13
> **GexNZ said:**
> Same problem on a Dell Mini 10v.  Installed to the disk off a USB key, rebooted into Ubuntu, sound and video working fine.  But the wireless doesn't seem to be working.

Followed instructions on [http://ubuntuforums.org/showthread.php?t=1304978&highlight=dell+mini+wireless](http://ubuntuforums.org/showthread.php?t=1304978&highlight=dell+mini+wireless) and now its working fine.

To fix it run:
sudo apt-get install bcmwl-kernel-source (or install via Synaptic)

Reboot and you're good to go!

worked like a charm.....Thank you ...

---

### Post by texaswriter on 2010-01-14
Disclaimer: This post will only serve those who were using Jaunty Jackelope [9.04] AND had the Broadcom-STA wireless drivers [proprietary] ALREADY WORKING. Or in other words, if upgrading to 9.10 made this driver stop "working": i.e. if u open "System" "Administration" "Hardware Drivers" and there is a message that says "This driver is activated but not currently in use" for the Broadcom STA wireless driver, then this message is for you.

There is probably a way to do this automatically, but I don't know how. Open a terminal and enter the following line
> sudo modprobe wlVoila, give network mangler a few seconds to digest it and it should load your wireless internet backup. 

Good luck, and if this post helped you, please thank or kudos the author. 

Also, if you know of a way to make that auto start, please reply to this or mail me...

---

### Post by bitbytebit on 2010-02-09
modprobe wl worked like a charm.

for the specific instance above, this is indeed the fix.

did you ever find out how to make it automatic though?

---

