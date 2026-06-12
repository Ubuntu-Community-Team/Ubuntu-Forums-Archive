---
title: "Restricted Drivers Manager won't enable NVIDIA"
date: 2007-04-19
forum: Multimedia &amp; Video
---

### Post by zachwlewis on 2007-04-19
I have an SLI enabled nVidia graphics setup in my computer, and I want to enable the drivers for Ubuntu 7.04.

I open the Restricted Drivers manager and check "NVIDIA accelerated graphics driver." A dialog appears and I click "Enable Driver." The dialog disappears, but the box is not checked.

I don't know much about Linux, so I would need a clear walk through of how to do command line things. :)

---

### Post by Flaystus on 2007-04-20
I'm getting the same exact problem. Except I'm not SLI just plane old 6600GT PCIexpress :cry:

---

### Post by hunterP on 2007-04-20
i am having same issue with the nvidia restricted drivers not being installed using the restricted drivers manager.  my lspci output is as follows:

```
01:00.0 VGA compatible controller: nVidia Corporation NV41.9 [GeForce Go 6800 Ultra] (rev a2)

```

---

### Post by Huffalump on 2007-04-20
Me, too.  The drivers will install but X can't use them under Feisty.  They used to work just fine under Edgy, but now I'm forced to use "nv" just to get any GUI at all.

Also, where is this Restricted Drivers Manager?  I never found it.  (It's not under System > Administration where I'd been told to look.)


Edit: I upgraded to the Beta about 1 hour before final, which means my menu is missing Restricted Drivers Manager as well as Desktop Effects.    They say the last Beta is the same as the Final, but obviously that's not true because I don't have those menu items and do not know how to launch them via command line.

---

### Post by barmazal on 2007-04-20
join all of you, it gives me to enable but give me low refresh rate on my default resolution

my graphics card 6600GT AGP, screen LG Flatron F770p ( should run 1280x980 on 85hz) when it does on 70hz also my eyes hurt with these settings while i do graphics

thanks if help me wih that you Ubuntu gurus.

---

### Post by MetalMusicAddict on 2007-04-20
After the drivers are downloaded and supposedly enabled does it change the driver entry in your xorg.conf to "nvidia" from "nv"?


If you dont know what Im talking about please do this in a terminal and post the contents. 
[B]
gedit /etc/X11/xorg.conf[/B]

---

### Post by Huffalump on 2007-04-20
> **MetalMusicAddict said:**
> After the drivers are downloaded and supposedly enabled does it change the driver entry in your xorg.conf to "nvidia" from "nv"?


If you dont know what Im talking about please do this in a terminal and post the contents. 
[B]
gedit /etc/X11/xorg.conf[/B]


How do I enable them via the Restricted Drivers Manager when there is no item in the menus of the 1-hour-before-final-Beta?

Also, if I manually edit xorg.conf to be "nvidia" then X never starts (Failed to load module wfb)

---

### Post by MetalMusicAddict on 2007-04-20
> **Huffalump said:**
> Also, if I manually edit xorg.conf to be "nvidia" then X never starts (Failed to load module wfb)

If you edited the xorg.conf already then just try: **sudo apt-get install linux-generic nvidia-glx** then reboot.

---

### Post by Huffalump on 2007-04-20
> **MetalMusicAddict said:**
> If you edited the xorg.conf already then just try: **sudo apt-get install linux-generic nvidia-glx** then reboot.

linux-generic did not update because it was already the latest version.

Previously, I had nvidia-glx-new, but upon install of nvidia-glx it was removed, of course.  So, it installed and I rebooted.  This time the error message was different.  Something about an API mismatch for the nVidia kernel version 1.0-9755 but X has 1.0-9631 (my hunch is that this means I should stick with nvidia-glx-new instead, but trust me when I say I'm glad for your help.)

What should I try next?  I'm back to nv, just to get a GUI at all right now.

---

### Post by MetalMusicAddict on 2007-04-20
> **Huffalump said:**
> What should I try next?  I'm back to nv, just to get a GUI at all right now.

From Synaptic reinstall the kernel modules and nvidia-glx.

---

### Post by Huffalump on 2007-04-20
> **MetalMusicAddict said:**
> From Synaptic reinstall the kernel modules and nvidia-glx.

Okay, I did that.  From Synaptic, reinstall anything linux-* (kernel pieces, headers, image, etc) and nvidia-glx.  Then updated the xorg.conf to "nvidia" and reboot.  I got the same error about API mismatch kernel module version is 1.0-9755 but X has 1.0-9631.

---

### Post by MetalMusicAddict on 2007-04-20
I see now. It is because you installed nvidia-glx-new.

I would make sure your set to "nv". "Mark for complete removal" the restricted modules for your kernel. Make sure you've done the same for nvidia-glx-new as well.

Then reboot. When you get back into Ubuntu install nvidia-glx and change the xorg. Reboot.

In the end this is the issue. If you look in Synaptic at nvidia-glx and -new you will see that the version numbers go along with your error.

---

### Post by MetalMusicAddict on 2007-04-20
Huffalump. Also, what card do you have?

I just found out via you about nvidia-glx-new. **-new** drops support for some older cards. So you might to use:nvidia-glx or nvidia-glx-legacy.

---

### Post by Huffalump on 2007-04-20
Well, I got the gist of what you were saying.  There's a version conflict and I need to flush things out.  So I tried it a few times, removing more and more.  In the end, I marked for complete removal:

linux-generic
linux-headers-2.6.20*
linux-image-2.6.20*
linux-image-generic
linux-restricted-modules*
linux-restricted-modules-common*
linux-restricted-modules-generic
nvidia-glx
nvidia-glx-new (just to be sure, even though it was not installed)

xorg.conf set to nv

reboot

Installed nvidia-glx via Synaptic.  Set xorg.conf to nvidia.  Reboot.  Same error yet again.  What else would need to be flushed?

EDIT: Just saw your comment.  GeForce FX 5600, which means I should be okay with nvidia-glx-new as far I could understand after reading the nVidia notes.

---

