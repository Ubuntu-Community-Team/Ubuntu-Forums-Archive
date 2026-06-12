---
title: "nvidia will not install"
date: 2008-10-29
forum: Multimedia Software
---

### Post by kaitwospirit on 2008-10-29
I just updated to 8.10 today. I was using [this]("http://ubuntu-virginia.ubuntuforums.org/showthread.php?p=5267395") script after having manually installed the nvidia driver for my Dell Latitude C840 laptop. However, the update seems to have broken it... and nvidia, and now the nvidia driver simply will not reinstall. I've tried doing it manually (it tells me that it can't install the driver) and with EnvyNG. On reboot with EnvyNG, the following happens:

In that text scroll you get while booting up, I see: "Running DKMS auto installation [something something] nvidia [something something]... FAILED"

Then Ubuntu tells me I'll have to enter low graphics mode, with the following errors:
(EE) module ABI major version (0) doesn't match the server's version (1)
(EE) Failed to load module "glx" (module requirement mismatch, 0)
(EE) Failed to load /usr/lib/xorg/modules/drivers//nvidia_drv.so
(EE) Failed to load module "nvidia" (loader failed, 7)
(EE) No drivers available.

I can give more information if necessary. I just don't have a clue what's wrong or where to begin. Can anyone help?

---

### Post by cariboo on 2008-10-30
Remove anything that has to do with nvidia in synaptic, then try loading the module again. It is set up totally different from the way hardy does it.

Jim

---

### Post by kaitwospirit on 2008-10-30
Problem is that I upgraded without anything in synaptic that pertains to nvidia installed. I've also noticed that the nvidia driver does not show up in the list of restricted drivers, though it did in the last version of ubuntu.

I think I might have had to edit a configuration file at some point while manually installing nvidia in order to get things to work. I know my xorg.conf is fine because I've restored to default at least three times over the course of the past day or so. Are there any other files I might have edited that would have a chance of causing me problems here?

---

### Post by cariboo on 2008-10-30
The Nvidia drivers in Intrepid are totally different from the drivers in Hardy. Depending on the model of your video card, there are three different drivers. Editing a configuration file won't help. You will have to completely remove the old drivers, then you can install the new ones.

Jim

---

### Post by kaitwospirit on 2008-10-30
Okay, I've uninstalled EnvyNG and all associated drivers and that hasn't helped, and that was the only thing installed through synaptic that had anything to do with the nvidia driver. I've checked thoroughly. 

Trying to reenable has not helped at all, which is pretty much what I expected, so I just uninstalled them again. The kernel update today didn't help me either. Additionally, no restricted drivers show up in the Hardware Drivers list, still.

The only thing I could imagine that could be wrong is that some file has blocked my system from "seeing" nvidia somehow, or that the old driver is somehow still installed (though that wouldn't seem to make sense after the kernel update).

---

### Post by kaitwospirit on 2008-10-30
Is there anything at all other than xorg.conf I might have edited in manually installing my driver that would be causing me problems now?

---

