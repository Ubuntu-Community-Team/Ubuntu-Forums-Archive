---
title: "Feisty, nvidia-glx-legacy, nvidia-settings"
date: 2007-04-21
forum: Multimedia &amp; Video
---

### Post by muecker on 2007-04-21
My Nvidia GEForce4 card is old enough that I have to use the legacy drivers.  I use my machine to record through MythTV and watch the recordings on my TV, hooked up through svidio.  Under Edgy this worked fine except that I have to execute nvidia-settings to set the flicker and color saturation or I end up a horrible looking black and white picture.  Yesterday I upgraded to Feisty and the TV output still works, but nvidia-settings does not so I cannot correct the picture on the TV.  I get the following errors:

ERROR: NV-CONTROL extension version 1.6 is too old; the minimimum required
       version is 1.9.
ERROR: Unable to determine number of NVIDIA GPUs on ':0.0'.
ERROR: Unable to determine number of NVIDIA Frame Lock Devices on ':0.0'.

When I look at the screen, all I see is the configuration screen but not the rest of the tabs.  How do I get flicker-free color on my TV again and/or get nvidia-settings to work?

Thank you.
Myron

---

### Post by Ziox on 2007-04-21
apparently, you need to update nv-control to version 1.9...or reinstall the legacy driver. Also, when you can get nvidia-settings to work again, open it via alt-f2.

hit alt-f2,
enter gksudo nvidia-settings
adjust what you need to adjust
then save it to the xorg.conf file
and then quit....

that should make it so that you don't have to execute nv-settings every single time.

---

### Post by muecker on 2007-04-21
I'm not sure what it means to update the NV-CONTROL, I think that is internal to the driver.  When I search through Synaptic for NV-CONTROL, I get the nvidia-settings.  Maybe I should mention that I installed nvidia-settings, nvidia-xconfig and nvidia-glx-legacy through apt.  This has been working fine under Edgy for months but no longer works under Feisty.

I read through every possible setting for the xorg.conf and did not find anything about setting the saturation or flicker.

I just looked and there is a bug on this issue: [https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.20/+bug/105138]("https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.20/+bug/105138")

---

### Post by dcstar on 2007-05-01
> **muecker said:**
> I'm not sure what it means to update the NV-CONTROL, I think that is internal to the driver.  When I search through Synaptic for NV-CONTROL, I get the nvidia-settings.  Maybe I should mention that I installed nvidia-settings, nvidia-xconfig and nvidia-glx-legacy through apt.  This has been working fine under Edgy for months but no longer works under Feisty.

I read through every possible setting for the xorg.conf and did not find anything about setting the saturation or flicker.

I just looked and there is a bug on this issue: [https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.20/+bug/105138]("https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.20/+bug/105138")

Install the Edgy version of nvidia-settings:

[http://ubuntuforums.org/showpost.php?p=2570017&postcount=9](http://ubuntuforums.org/showpost.php?p=2570017&postcount=9)

---

### Post by steevc on 2007-05-13
> **dcstar said:**
> Install the Edgy version of nvidia-settings:

[http://ubuntuforums.org/showpost.php?p=2570017&postcount=9](http://ubuntuforums.org/showpost.php?p=2570017&postcount=9)

There's a zip file attached to that post. How do I install it?

---

### Post by macktheknife on 2007-05-13
> **steevc said:**
> There's a zip file attached to that post. How do I install it?

i was about to ask the same question.  I'm having the same problem as everyone else.

---

### Post by csick919 on 2007-05-14
i found a deb of the same version here:
[http://www.gtlib.gatech.edu/pub/ubuntu/pool/restricted/n/nvidia-settings/nvidia-settings_1.0-3ubuntu7_i386.deb]("http://www.gtlib.gatech.edu/pub/ubuntu/pool/restricted/n/nvidia-settings/nvidia-settings_1.0-3ubuntu7_i386.deb")

seems to work.

---

### Post by astromech on 2007-05-23
> **steevc said:**
> There's a zip file attached to that post. How do I install it?    I got one here [http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=nvidia-settings&searchon=names&subword=1&version=edgy&release=all](http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=nvidia-settings&searchon=names&subword=1&version=edgy&release=all)    finally one that works.   But I  got an error message: ERROR: Error parsing configuration file '/root/.nvidia-settings-rc' on line
       14: 'ShowQuitDialog = Yes' (Unrecognized attribute name).
Any thoughts on the error message ,anyone?

---

