---
title: "No DVI output with Breezy"
date: 2006-01-11
forum: Multimedia &amp; Video
---

### Post by SolidAndShade on 2006-01-11
I've gotten the Nvidia driver installed and working with my 6150/430 motherboard, but there's one problem. The board has both DVI and RGB output ports, but when X starts the DVI port stops working and I can only get a screen by hooking my monitor to the RGB port. Does anyone know what might be going on and/or how to fix this? Thanks. My motherboard is an MSI K8NGM2-FID GF6150 939, and some relevant text from my Xorg log file is appended below.


X Window System Version 6.8.2 (Ubuntu 6.8.2-77 20051010174819 [email]root@crested.warthogs.hbd.com[/email])
Release Date: 9 February 2005
X Protocol Version 11, Revision 0, Release 6.8.2
Build Operating System: Linux 2.6.8.1 x86_64 [ELF] 
Current Operating System: Linux 2.6.12-10-amd64-k8-smp #1 SMP Thu Dec 22 11:27:46 UTC 2005 x86_64

(II) Setting vga for screen 0.
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(--) NVIDIA(0): Linear framebuffer at 0xD0000000
(--) NVIDIA(0): MMIO registers at 0xFD000000
(II) NVIDIA(0): NVIDIA GPU detected as: GeForce 6150
(--) NVIDIA(0): VideoBIOS: 05.51.22.28.00
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(--) NVIDIA(0): VideoRAM: 65536 kBytes
(II) NVIDIA(0): Connected display device(s): DFP-0, TV-0
(WW) NVIDIA(0): Multiple displays connected, but only one display allowed;
(WW) NVIDIA(0):      using first display
(--) NVIDIA(0): Detected TV Encoder: NVIDIA
(--) NVIDIA(0): TV-0: maximum pixel clock: 400 MHz
(II) NVIDIA(0): Frequency information for TV-0:
(II) NVIDIA(0):   HorizSync   : 28.000-64.000 kHz
(II) NVIDIA(0):   VertRefresh : 43.000-60.000 Hz
(II) NVIDIA(0):      (HorizSync from HorizSync in X Config Monitor section)
(II) NVIDIA(0):      (VertRefresh from VertRefresh in X Config Monitor
(II) NVIDIA(0):      section)
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/X11R6/lib/modules/linux/libint10.a
(II) NVIDIA(0): Primary V_BIOS segment is: 0xc000
(II) NVIDIA(0): Generic Monitor: Using hsync range of 28.00-64.00 kHz
(II) NVIDIA(0): Generic Monitor: Using vrefresh range of 43.00-60.00 Hz
(II) NVIDIA(0): Clock range:  12.00 to 400.00 MHz

---

### Post by ajkeys on 2006-01-31
I can report the same problem, except I have a Geforce 6600GT (not onboard) PCIExpress. I can pinpoint it to the nvidia drivers, because if they are not installed and X uses the generic driver it works fine for me. Also fixxxer is having the same problem in this [thread]("http://www.ubuntuforums.org/showthread.php?t=115010").

---

### Post by fvgm on 2006-11-03
I was having the SAME PROBLEM with ATI Radeon 9250 + fglrx driver
Everythinh goes blank when x starts...
anyone can help?

---

### Post by Goliash on 2006-11-10
I have unfortunately the same problem but with Dapper, fglrx and Radeon 9200. When KDE starts, screen goes blank on DVI (d-sub works).

---

