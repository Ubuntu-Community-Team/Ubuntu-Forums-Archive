---
title: "rt3090 WiFi card users, your help is needed."
date: 2011-05-05
forum: Networking &amp; Wireless
---

### Post by csh on 2011-05-05
I do want to install the latest version (11.04) of Ubuntu safely on my Netbook without freeze.

There is a bug that affect Ubuntu 10.10. Bug #662288 ( [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/662288](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/662288) ). This bug will cause freeze when the driver module is unloaded. I removed Ubuntu from my Netbook because of this.

I don't want to make my Netbook freeze anymore because soft reboot (using magic keys) not working and hard reboot caused some damage on internal hardware. I took back my Netbook from warranty claim not long ago. So, I don't wish that there is anymore freeze.

According to the bug report page, that bug was fixed. But, is the bug fixes come with the published live CD image? Or, do I have to install a separate update after installing Ubuntu?

If I have to install a separate update after installing Ubuntu, that mean my Netbook will still freeze during Ubuntu installation.

So, your answers to my above questions will be highly appreciated.

Thank you!

---

### Post by csh on 2011-05-06
Can someone reply please.

---

### Post by MartyBuntu on 2011-05-06
Did you try the blacklist workaround as mentioned in the bug report?

It worked for my Ralink card.

---

### Post by Sven6210 on 2011-05-09
You can have a look on my how-to at [http://ubuntuforums.org/showthread.php?t=1476007&highlight=RT3090](http://ubuntuforums.org/showthread.php?t=1476007&highlight=RT3090)

It also works for the RaLink RT3090, you just need to replace the "[FONT=Verdana, sans-serif]RT2860" with "RT3090".

Disadvantage of this procedure:
[/FONT]
[LIST]
[*]You need to recompile the driver each time you make a major kernel-update. The backports I have tried so far did not work very well
[/LIST]
Advantage of this procedure:

[LIST]
[*]On my EeeBox B202 and my friends EeePC 1015 P it works very well and reliable
[/LIST]

The manual should also work for newer releases of Ubuntu, I am still running Ubuntu 10.04 LTS on my systems.

Good luck

Sven

---

