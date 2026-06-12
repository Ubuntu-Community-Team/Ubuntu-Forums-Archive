---
title: "Dual-Screen: Unable to set the second flat screen to 1680x1050"
date: 2007-09-23
forum: Multimedia &amp; Video
---

### Post by J4nus on 2007-09-23
I know there is other threads on this subject but there are all unresolved.

[http://ubuntuforums.org/showthread.php?t=417664](http://ubuntuforums.org/showthread.php?t=417664)
[http://ubuntuforums.org/showthread.php?t=272234](http://ubuntuforums.org/showthread.php?t=272234)

I have a motherboard ASUS M2NPV-VM with a built-in nvidia card. 
This card has 2 heads: VGA and DVI.

I have 2 flat screen: ACER AL2016W (connected via VGA) and ACER AL2032 WA (connected via DVI).

On windows, I can get the resolution 1680x1050 on the 2 screens but it doesn't work on GNU/Linux :( So the card support this resolution..


On the ACER AL2016W (vga), it works perfectly but on the ACER AL2032 WA (dvi), the maximum working resolution is 1280x1024 :(

I'm using the last driver: 100.14.19

I tried the dual-desktop and the dualview modes.
You will find the log and the configuration file in attachment of this post.


I think that the problem is here:

(--) NVIDIA(0): Memory: 524288 kBytes
(--) NVIDIA(0): VideoBIOS: 05.51.22.33.07
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(--) NVIDIA(0): Connected display device(s) on GeForce 6150 at PCI:0:5:0:
(--) NVIDIA(0):     Acer AL2016W (CRT-0)
(--) NVIDIA(0):     Acer MFM DVI (DFP-0)
(--) NVIDIA(0): Acer AL2016W (CRT-0): 350.0 MHz maximum pixel clock
(--) NVIDIA(0): Acer MFM DVI (DFP-0): 310.0 MHz maximum pixel clock
(--) NVIDIA(0): Acer MFM DVI (DFP-0): Internal Dual Link TMDS
(II) NVIDIA(0): Assigned Display Devices: CRT-0, DFP-0
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "1680x1050,1680x1050"
(II) NVIDIA(0): Virtual screen size determined to be 1680 x 1050
(++) NVIDIA(0): DPI set to (100, 100); computed from -dpi X commandline option
(WW) NVIDIA(0): 32-bit ARGB GLX visuals are only supported in depth 24.
(WW) NVIDIA(0): Disabling 32-bit ARGB GLX visuals.
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:


The maximum pixel clock seems to be too low to allow the correct resolution.



Do you have an idea ? Is it a mistake in the configuration or a bug ?

Thanks in advance!

---

