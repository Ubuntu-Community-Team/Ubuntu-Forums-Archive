---
title: "Enabling Broadcom driver causes kernel panic and lock-up in Natty"
date: 2011-05-12
forum: Networking &amp; Wireless
---

### Post by thonuz on 2011-05-12
I have the Broadcom BCM4321 wireless device. When I enable the Broadcom ata driver in additional hardware my wireless will work for a few minutes until I get a kernel panic error and my entire system freezes up. This happens only with the new kernel natty is using. I tried 2.6.39 and its the same. Earlier versions of ubuntu did not do this.
I have also tried installing the driver manually but get:  error: implicit declaration of function ‘init_MUTEX’ and so cannot get the .ko file in the top directory.

I don't know what to do other than go back to an earlier version of ubuntu,
What did they do in the new kernel to break this?
Thanks anyone.

---

### Post by josephmills on 2011-05-12
please see post number 44 [http://ubuntuforums.org/showthread.php?t=1748245&page=5](http://ubuntuforums.org/showthread.php?t=1748245&page=5) thanks let us know what going on.

---

### Post by thonuz on 2011-05-13
Thanks for the link. I tried from post 44 installing the broadcom-sta-source + broadcom-sta-common for my card which gives me no wireless:(:


The earlier posts there basically lead up to giving you the same thing: 
--firmware-b43-installer" and "b43-fwcutter" in Synaptic package manager. Then install them-- This is not an  alternative solution. It worked, I got wireless, system freeze after 10 minutes (or kernel panic). 

If its the proprietary driver is their an open source driver that works?

---

