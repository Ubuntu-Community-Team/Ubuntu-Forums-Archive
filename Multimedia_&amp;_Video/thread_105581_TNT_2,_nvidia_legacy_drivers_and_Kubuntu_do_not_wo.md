---
title: "TNT 2, nvidia legacy drivers and Kubuntu do not work together"
date: 2005-12-18
forum: Multimedia &amp; Video
---

### Post by grzebo on 2005-12-18
Hello,
I spent past 20 hours searching for a way to use Nvidia driver version 7174 under Kubuntu.

My card is TNT 2, my system is Ubuntu Breezy Badger with 2.6.12-9-k7 kernel.

I did pretty much everything that I could find on Google, and the card still does not work.

What happens is: when I turn on kdm or run startx the screen goes blank, blinks once (as if from changing resolution) and then the whole system hangs.

I installed the driver from the legacy package, provided correct kernel headers, used correct version of the GCC. The nodes in /dev/nvidia[0-7] and /dev/nvidiactl are being created correctly (when I create them manually, it makes no difference).

I use an xorg.conf that worked with my previous sytem (but with 2.4 kernel), so that's not the problem either. I also modified valnilla xorg.conf manually, but to no avail.

I did about a hundred different things that were supposed to help, according to posts from different forums (uninstalled udev, commented out glx in xorg.conf, and many more I don't remember), and have lost all hope of making this work.

Does anyone have any ideas?

Thank you in advance for your help.

Grzegorz Borek



The relevant logs are:
=================================================
/var/log/Xorg.0.log:

(...)
(II) Setting vga for screen 0.
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(--) NVIDIA(0): Linear framebuffer at 0xCA000000
(--) NVIDIA(0): MMIO registers at 0xCC000000
(EE) NVIDIA(0): Failed to initialize the NVIDIA graphics device!
(EE) NVIDIA(0):  *** Aborting ***
(II) UnloadModule: "nvidia"
(EE) Screen(s) found, but none have a usable configuration.

Fatal server error:
no screens found

Please consult the The X.Org Foundation support
         at [http://wiki.X.Org](http://wiki.X.Org)
 for help.
Please also check the log file at "/var/log/Xorg.0.log" for additional information.

=======================================
/var/log/messages:

Dec 18 16:17:25 localhost kernel: [4294752.561000] nvidia: module license 'NVIDIA' taints kernel.
Dec 18 16:17:25 localhost kernel: [4294752.595000] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 5
Dec 18 16:17:25 localhost kernel: [4294752.595000] ACPI: PCI Interrupt 0000:01:00.0[A] -> Link[LNKA] -> GSI 5 (level, low) -> IRQ 5
Dec 18 16:17:25 localhost kernel: [4294752.596000] NVRM: loading NVIDIA Linux x86 NVIDIA Kernel Module  1.0-7174  Tue Mar 22 06:44:39 PST 2005

[and that's when the system stopped]

---

