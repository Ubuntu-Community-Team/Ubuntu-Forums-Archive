---
title: "Twinhan alpha, no channels"
date: 2007-07-29
forum: Multimedia &amp; Video
---

### Post by Hayesio on 2007-07-29
Hi everyone.

I have a Twinhan alpha DTV USB dongle (7045a) that I've been trying to get running for weeks now and I was wondering if anybody could help me out?   I know these is a few other posts up with the same problem but they haven't helped me and I thought I would refresh the issue.

I have added the firmware (dvb-usb-vp7045-01.fw) and the device seems to be recognized and working fine - until I search for channels.  No chennals are found.  I've been using Kaffeine and Mythtv. The device is also present in the "Hardware information."  

The dongle works fine with XP on VMWare Workstation 6, so theres nothing wrong with the hardware or reception.

I'm dieing to get this running in Ubuntu, I hate running that big slug every time I want to watch TV, so any help would be greatly appretiated.

Regards

Hayesio

---

### Post by Supremacy on 2007-07-30
> **Hayesio said:**
> Hi everyone.

I have a Twinhan alpha DTV USB dongle (7045a) that I've been trying to get running for weeks now and I was wondering if anybody could help me out?   I know these is a few other posts up with the same problem but they haven't helped me and I thought I would refresh the issue.

I have added the firmware (dvb-usb-vp7045-01.fw) and the device seems to be recognized and working fine - until I search for channels.  No chennals are found.  I've been using Kaffeine and Mythtv. The device is also present in the "Hardware information."  

The dongle works fine with XP on VMWare Workstation 6, so theres nothing wrong with the hardware or reception.

I'm dieing to get this running in Ubuntu, I hate running that big slug every time I want to watch TV, so any help would be greatly appretiated.

Regards

Hayesio

I have one too. I have mine working perfectly. I can't exactly remember how to do it, but I believe you need to add the device to MythTV. I'd search for MythTV instructions.

You will need to wait quite a while for it to scan channels and add them to the daabse (uses MySQL to store them).

Regards,
Supremacy

---

### Post by Hayesio on 2007-08-01
I've tried setting it up with MythTV a dozen times - it detects the device, seems to set up without any problems, but when I scan for channels nothing is found.  Mythtv even displays the name of the dongle when i select the capture card.

I used this page as a guide:
[http://parker1.co.uk/mythtv_ubuntu.php](http://parker1.co.uk/mythtv_ubuntu.php)

According to this page -
 [http://www.flamingspork.com/blog/2006/09/05/twinhan-usb-dtv-dongle-not-working/](http://www.flamingspork.com/blog/2006/09/05/twinhan-usb-dtv-dongle-not-working/)
Twinhan have resently changed the dongles chip set from MT352 to    TDA10046.  

Supremacy, do you have the old chipset or the new one (TDA10046)?

Regards

---

