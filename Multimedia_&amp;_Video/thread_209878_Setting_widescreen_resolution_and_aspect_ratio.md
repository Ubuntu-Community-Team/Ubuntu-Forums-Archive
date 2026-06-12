---
title: "Setting widescreen resolution and aspect ratio"
date: 2006-07-05
forum: Multimedia &amp; Video
---

### Post by Focher on 2006-07-05
Hi,

I have been fighting with setting up a Sony Bravia LCD as a widescreen monitor with Ubuntu 6.06 (and with Suse Linux Enterprise Desktop 10.1). The problem seems to be that the Intel 945G graphics adapter is not setting the proper screen resolution.

I have used 855resolution/915resolution to define a custom resolution of 1360x768 (including in the /etc/default/915resolution configuration file) and that resolution shows properly when I do a 915resolution -l command.

I also used gtf (1360 768 60) to create a Modeline (Modeline "1360x768_60" 84.72 1360 1424 1568 1776 768 769 772 795 -HSync +VSync).

However, when I restart the X server or reboot the machine, the virtual resolution is set to 1360x768 but the video signal remains at 1024x768. I can see this both visually and also the monitor shows this as the signal when I use the option to display the input signal.

Within Ubuntu, the System - Preferences - Screen Resolution shows 1360x768 plus the "old" options of 1024x768, 800x600, and 640x480. I have no idea where those "old" options are coming from because they display even if I delete them from the Modes line in the xorg.conf file.

I have checked within Windows XP and the Intel 945G driver works fine with the widescreen resolution of 1360x768, so I know it is supported on the Sony Bravia LCD.

The /var/log/Xorg.0.log file shows the mode

(II) I810(0): Supported additional Video Mode:
(II) I810(0): clock: 85.5 MHz   Image Size:  0 x 0 mm
(II) I810(0): h_active: 1360  h_sync: 1424  h_sync_end 1536 h_blank_end 1792 h_border: 0
(II) I810(0): v_active: 768  v_sync: 771  v_sync_end 777 v_blanking: 795 v_border: 0
(II) I810(0): Ranges: V min: 57  V max: 63 Hz, H min: 29  H max: 49 kHz, PixClock max 90 MHz

and also the available settings

(II) I810(0): SONY TV: Using default hsync range of 29.00-49.00 kHz
(II) I810(0): SONY TV: Using default vrefresh range of 57.00-63.00 Hz
(II) I810(0): Increasing the scanline pitch to allow tiling mode (1360 -> 2048).
(--) I810(0): Virtual size is 1360x768 (pitch 2048)
(**) I810(0): *Built-in mode "1360x768"
(**) I810(0):  Built-in mode "1024x768"
(**) I810(0):  Built-in mode "800x600"
(**) I810(0):  Built-in mode "640x480"
(II) I810(0): Attempting to use 60.26Hz refresh for mode "1360x768" (85c)
(II) I810(0): Attempting to use 60.00Hz refresh for mode "1024x768" (854)
(II) I810(0): Attempting to use 60.32Hz refresh for mode "800x600" (852)
(II) I810(0): Attempting to use 60.00Hz refresh for mode "640x480" (850)
(==) I810(0): DPI set to (75, 75)

However, the screen never actually goes into that display resolution.

Can anyone offer suggestions or an outright solution?

Any help is appreciated. Thanks.

---

### Post by pbr6000 on 2007-06-26
I also use a Sony Bravia LCD with a native resolution of 1366x768.  I've gathered from several other posts that "1360x768" is the correct resolution to use in these cases, but haven't had any luck getting my video card to output that signal when running Ubuntu.

I assume 855resolution/915resolution are specific to an Intel video card- Does anyone know of something comparable for an ATI x800xt?

--pbr

---

### Post by pbr6000 on 2007-06-26
By the way, I saw this line in your log file...

"(II) I810(0): Attempting to use 60.26Hz refresh for mode "1360x768" (85c)"

Why would it attempt to use 60.26Hz refresh instead of just plain 60Hz?

--pbr

---

