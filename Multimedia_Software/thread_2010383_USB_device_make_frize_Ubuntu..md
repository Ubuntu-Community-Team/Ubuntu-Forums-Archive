---
title: "USB device make frize Ubuntu."
date: 2012-06-25
forum: Multimedia Software
---

### Post by checcouniud on 2012-06-25
Ok i try to make solve a problem related to an "USB Audio DAC".

So i few days ago I bought a USB Audio DAC (basically an external sound card) that according to the producers works and is recognized as a normal USB Device by all OS (linux included).

However, after few seconds that i connected it to the USB port and turn it on my Ubuntu system FROZED. (the problem is always reproducible) . I realized that since i turn on the usb device a mobprobe process take 100% of a CPU (see attachment).

To solve the problem i was suggested to update ubuntu in order to update the kernel. So i updated from 10.04 to 10.10, And the device STARTED TO  WORK perfectly.

After, i have realized that the update had ****** up my audio settings.  Problem that i was well aware of since i bought the present computer and that i have described and solved previously here(I am currently using the same PC):
[http://ubuntuforums.org/showthread.php?p=9835780#post9835780](http://ubuntuforums.org/showthread.php?p=9835780#post9835780)

To solve the general audio problem i performed my usual procedure:

sudo apt-get --purge remove linux-alsa-driver-modules-$(uname -r)
sudo apt-get install linux-backports-modules-alsa-$(uname -r)

After which my USB deviced started to Froze Ubuntu again as before.


So in conclusion the operation on the alsa-modules does something that gives problems to the USB device.  

Does anybody understand the issue? ANd has a solution to make both alsamixer and the USB audio DAC work.

Thank you in advice for any help

Any idea
best

---

