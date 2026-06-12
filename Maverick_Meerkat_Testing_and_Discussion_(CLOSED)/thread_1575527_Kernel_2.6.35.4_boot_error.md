---
title: "Kernel 2.6.35.4 boot error"
date: 2010-09-15
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by M4570D0N on 2010-09-15
I am currently running Linux Mint 9 gnome on an HP DV5t. I recently updated the kernel to 2.6.35.4 from 2.6.32-24 a few days ago. Everything has run rather smoothly so far (and even corrected a few bugs I was experiencing with the old kernel)  with the exception of 2 related boot issues. 

First, is the boot splash. After choosing the kernel from the grub menu, instead of seeing the Linux Mint text, Logo, and the 4 progress dots below it centered on the screen, I see Linux Mint in large plain text flash on the center of the screen for a split second, and then "Linux Mint" shows up in very tiny plain text with the 4 dots, but no Mint Logo. It is also not centered on the screen but about 200 pixels down and about 200 pixels to the right of the top left corner of the screen (1200x800 screen). This is normally not an issue, but it would be nice if it displayed as it is supposed to. How might I troubleshoot this?

The second issue is much more serious. About and hour ago I turned on the laptop and after selecting the kernel from grub it started booting. However, a wall of text appeared, with something about init ureadahead at the bottom, but I did not have a chance to read it before the screen went blank and a window popped up with a warning message stating that "Ubuntu is operating in low graphics mode" with this below it:

(EE) intel (0): [drm] failed to set the drm interface version
(EE) intel (0): Failed to become DRM master
(EE) intel (0): failed to get resources. Bad file description
(EE) intel (0): Kernel modsetting setup failed
(EE) Screen(s) found, but none have a usable configuration

clicking the ok button, it asked if I wanted to continue in low graphics for this session, reconfigure graphics, restart x, exit to console, and maybe one other option. I went to the console and restarted the computer. When the grub menu came up I selected 2.6.35.4 again (note: not recovery mode). This time, the boot splash showed up correctly for the first and only time ever since the kernel was updated, and it booted up to the log in screen in less than 20sec. 

Anyone know what could have caused this error? Not sure what additional data/code I may need to post up, but I'll post up additional info if asked.

---

### Post by Noz3001 on 2010-09-15
Try adding nomodeset to the kernel line in grub. It looks like a radeon driver?

---

### Post by M4570D0N on 2010-09-20
> **Noz3001 said:**
> Try adding nomodeset to the kernel line in grub. It looks like a radeon driver?

Sorry I did not respond earlier. I have now had this error occur a few more times. I have a dual-boot setup with Mint9 and Windows 7. I've noticed that the error occurs either the first or the second boot up into Linux after I had booted into Windows 7. I'm thinking it might be an issue with Windows not properly releasing it? I have not tried adding nomodeset yet, as I wanted to verify that I would be using the correct solution to address correct problem. Please forgive my n00bish ignorance, but I'm still rather new to Linux and have never needed to add "nomodeset" before. How might I view what software/drivers the system would be using if I were to add it, before I actually add it? 

Also, if this helps, here's the output from dmesg:

```
~ $ dmesg | grep drm
[    1.170992] [drm] Initialized drm 1.1.0 20060810
[    1.230196] [drm] detected 63M stolen memory, trimming to 32M
[    1.230312]   alloc irq_desc for 48 on node -1
[    1.230315]   alloc kstat_irqs on node -1
[    1.230324] i915 0000:00:02.0: irq 48 for MSI/MSI-X
[    1.230338] [drm] set up 32M of stolen space
[    1.230472] [drm:init_ring_common] *ERROR* render ring head not reset to zero ctl 00000000 head 02001000 tail 00000000 start 02001000
[    1.230517] [drm:init_ring_common] *ERROR* render ring head forced to zero ctl 00000000 head 00000000 tail 00000000 start 02001000
[    2.436805] fb0: inteldrmfb frame buffer device
[    2.436806] drm: registered panic notifier
[    2.445862] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
```This brings up another related question I have, but I may need to ask it in another thread. Here's some more info on my notebook:

VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07) 
Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
OpenGL Renderer: Mesa DRI Mobile Intel® GM45 Express Chipset GEM 20091221 2009Q4

Given that, why did Linux install anything related to the i915 when I installed the OS? Is that actually correct?

 I'm also not aware of any Radeon drivers currently installed on here that would be the cause of the error I'm having.

If there's any additional code I need to post, let me know.

---

### Post by cariboo on 2010-09-20
the i915 driver is correct for your chipset. There are many other video drivers installed during installation, they are not loaded if the chipset for that driver isn't detected.

---

