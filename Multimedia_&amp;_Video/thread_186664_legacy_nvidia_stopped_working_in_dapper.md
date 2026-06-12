---
title: "legacy nvidia stopped working in dapper"
date: 2006-06-02
forum: Multimedia &amp; Video
---

### Post by nicco on 2006-06-02
Hi, I have an old nvidia card and have to use the nvidia-glx-legacy package. It worked in breezy but after upgrading I get in /var/log/Xorg.0.log:

(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(--) NVIDIA(0): Linear framebuffer at 0xD0000000 
(--) NVIDIA(0): MMIO registers at 0xDE000000
(EE) NVIDIA(0): Failed to load the NVIDIA kernel module!
(EE) NVIDIA(0):  *** Aborting ***
(II) UnloadModule: "nvidia"
(EE) Screen(s) found, but none have a usable configuration.

Fatal server error:
no screens found

I have specified the correct BusID in xorg.conf also tried "nvidia-glx-config enable", but nothing works.

Any hints?

---

### Post by Sarisar on 2006-06-02
I had the same problem.  Edit the xorg.conf (sudo nano /etc/X11/xorg.conf) and change nvidia to nv and that should fix it.

And I had to read it on another forum post myself :P

---

### Post by nicco on 2006-06-02
Thanks, that worked! I thought "nv" was a really old and non-optimized driver? At least it used to be, perhaps they replaced it with the glx-legacy driver...

---

### Post by Sarisar on 2006-06-02
Probably, but at least we have some form of a GUI now.  Looks like there is some issue with Nvidia (according to the forums anyway) so give it a few days and someone should fix it :)

Glad I could help

---

### Post by Sarisar on 2006-06-02
Oh, you may want to try to read [this forum thread]("http://ubuntuforums.org/showthread.php?t=139264") about nvidia drivers.

---

### Post by nicco on 2006-06-02
Thanks for the link! Turns out the only thing I needed to do was install the linux-restricted-modules-2.6.15-23-686 package. I had -386 but I'm using a 686 kernel. D'oh! ;)

---

### Post by RandomGeek on 2006-06-06
I have exactly the same problem, but I'm running the 386 kernel.

I have an old Dell Inspiron lappy with a GForce2-Go.  It worked great in breezy, it seems borked in Dapper though.  Ive searched the forums but I can't find a solution to get the 3D working :-(

When I do load with the (legacy) driver enabled it freezes and displays a flashing white line in the top left of the screen. I have to hard-reboot and use recovery mode to swap the xorg.conf file back to using NV.

Any other ideas out there?

---

### Post by strips on 2006-06-09
You don't need to boot a rescue disc to change the xorg file. Just select the rescuemode in grub and login as root. This depends if you have a root password. Not sure what you should do if you only use sudo.

I have used Dapper a while now with a GF2 Pro and it's a bit unstable. About half the times I boot, X hangs when the Nvidia splash should show. Irritating. I have just done som shuffling on the PCI cards in the computer and upgraded the RAM so I'll see if this continues.

Havent testet so much in the final kernel yet.

PS. Remember that you need the linux-restricted-modules-xxx package.

---

### Post by BobSongs on 2006-07-06
Here's my solution to getting 3D acceleration.

1) Ensure the 686 kernel with the legacy nVidia kernel is installed/upgraded.

2) Install **nvidia-glx-legacy** from Synaptic. Ensure you've got all the repositories open.

3) Kill X (Ctrl + Alt + F1) and type **sudo /etc/init.d/gdm stop**.

4) Enter: **sudo nvidia-glx-config enable**

5) If your system complains that the original xorg.conf was modified and that it cannot run do: **sudo nano /etc/X11/xorg.conf** and replace "nv" with "nvidia" in the driver section (it's a bit of a drive, so bring iced tea with you). Save the file and restart the system.

---

