---
title: "How Do I Get 1680x1050 with NVIDEA"
date: 2008-04-27
forum: Multimedia Software
---

### Post by wbsorsby on 2008-04-27
I just installed Ubuntu 8.04 on a new PC and can't get 1680x1050 resolution. The original video driver handled 1680x1050 but wasn't true 1680x1050.

Using displayconfig-gtk I found an NVIDEA driver, but it only goes to 1400x1050.

Anybody know what driver I need? and where is it?

Thanks.

---

### Post by Anthony M on 2008-04-27
Do you have nvidia-glx-new installed?

---

### Post by wbsorsby on 2008-04-27
Thanks, Anthony. At your suggestion I installed nvidia-glx-new, but still have a limit or 1400 x 1050.

I don't even have the Virtual 1680 x 1050 capability any more like I had originally, but I'm not sure whether that's a problem with the "new" NVIDEA driver. I lost the virtual 1680 x 1050 when I first went the default NVIDEA driver.

Do I need to manually edit the xorg.conf to put 1680 x 1050 back in? Surely not ... Shouldn't that be automatic with the NVIDEA driver?

---

### Post by Anthony M on 2008-04-27
I am still a noob myself, but I am running integrated NVIDIA 7025 graphics at 1680x1050 resolution. The NVIDIA packages I have installed according to synaptic are:

nvidia-glx-new
nvidia-kernel-common
xserver-xorg-video-nv

I dont know how helpful that is....

EDIT: Do you have the restricted NVIDIA driver enabled in System>Administration>Hardware Drivers?

---

### Post by wbsorsby on 2008-04-27
That looks like a clue. Yes, the restricted driver is enabled, but status for it is: **not in use!** 

I'm confused now. In trying to enable it, it crashed! Now it is not enabled and won't let me enable it, even with a reboot. This is not looking good.

I do have all the other three packages you listed. I tried uninstalling the nvidea-glx-new to get to a clean slate, but no joy there either. Even if I switch to VESA driver I still can't uninstall the nvidea-glx-new driver. Something's not right.

---

### Post by wbsorsby on 2008-04-27
Got it now! 

Thanks, Anthony. Your comment on enabling the restricted NVIDIA driver in System>Administration>Hardware Drivers was the key piece. 

I was able to resolve the problems finally by:
- reinstalling nvidea-glx-new
- reconfiguring X with: sudo dpkg-reconfigure -phigh xserver-xorg
- running: sudo displayconfig-gtk
- fiddling with parameters until it accepted the new nvidea (took a while) 
- selecting configuration in: System>Preferences>Screen Resolution
- rebooting

On reboot, the system came up in 1680x1050 resolution.

Regards,
Bill

Edit: I'll add at this point that my system is:
Gateway GT5656 with integrated NVIDEA GeForce 6150 SE video

---

### Post by Anthony M on 2008-04-27
Glad you got it worked out!

---

