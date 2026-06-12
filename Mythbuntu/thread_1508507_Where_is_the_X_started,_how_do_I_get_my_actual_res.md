---
title: "Where is the X started, how do I get my actual resolution"
date: 2010-06-13
forum: Mythbuntu
---

### Post by Saubazi on 2010-06-13
I am new to XFCE I used fluxbox in my previous mythtv box but basically at the moment I would really like to be sure that my computer is running at 1080i. 

I just connected it on my LCD-TV on HDMI socket and everything looks fine, I am however, not fully sure that it is really the res I want, most probably yes.

I would use --verbose 6 option for X-start but do not know where to add it.

On the other hand this looks like 1080...
(--) Jun 13 08:02:17 NVIDIA(0): Memory: 1048576 kBytes
(--) Jun 13 08:02:17 NVIDIA(0): VideoBIOS: 70.16.27.00.23
(II) Jun 13 08:02:17 NVIDIA(0): Detected PCI Express Link width: 16X
(--) Jun 13 08:02:17 NVIDIA(0): Interlaced video modes are supported on this GPU
(--) Jun 13 08:02:17 NVIDIA(0): Connected display device(s) on GeForce GT 220 at PCI:1:0:0:
(--) Jun 13 08:02:17 NVIDIA(0):     SAMSUNG (DFP-0)
(--) Jun 13 08:02:17 NVIDIA(0): SAMSUNG (DFP-0): 330.0 MHz maximum pixel clock
(--) Jun 13 08:02:17 NVIDIA(0): SAMSUNG (DFP-0): Internal Dual Link TMDS
(II) Jun 13 08:02:17 NVIDIA(0): Assigned Display Device: DFP-0
(==) Jun 13 08:02:17 NVIDIA(0): 
(==) Jun 13 08:02:17 NVIDIA(0): No modes were requested; the default mode "nvidia-auto-select"
(==) Jun 13 08:02:17 NVIDIA(0):     will be used as the requested mode.
(==) Jun 13 08:02:17 NVIDIA(0): 
(II) Jun 13 08:02:17 NVIDIA(0): Validated modes:
(II) Jun 13 08:02:17 NVIDIA(0):     "nvidia-auto-select"
(II) Jun 13 08:02:17 NVIDIA(0): Virtual screen size determined to be 1920 x 1080
(**) Jun 13 08:02:17 NVIDIA(0): DPI set to (100, 100); computed from "DPI" X config option
(==) Jun 13 08:02:17 NVIDIA(0): Enabling 32-bit ARGB GLX visuals.
(--) Depth 24 pixmap format is 32 bpp
(II) Jun 13 08:02:17 NVIDIA: Using 768.00 MB of virtual memory for indirect framebuffer


On the other hand if recall correctly virtual screen size is not the "real screen size" so how do I know that res is not something else and desktop set to 1080i?

I have namely a bigger overscan problem on desktop as I had in my previous hardware...

---

### Post by nickrout on 2010-06-13
xwininfo -root

less /var/log/Xorg.0.log

---

### Post by ian dobson on 2010-06-13
Hi,

If your running 10.04 have a look in /etc/init. 10.04 uses upstart to start most deamons. I think gdm is the xserver start service.

Regards
Ian Dobson

---

### Post by Saubazi on 2010-06-13
Strange...

I get this...

$xwininfo -root

xwininfo: Window id: 0x15d (the root window) (has no name)

  Absolute upper-left X:  0
  Absolute upper-left Y:  0
  Relative upper-left X:  0
  Relative upper-left Y:  0
  Width: 1366
  Height: 768
  Depth: 24
  Visual: 0x21
  Visual Class: TrueColor
  Border width: 0
  Class: InputOutput
  Colormap: 0x20 (installed)
  Bit Gravity State: NorthWestGravity
  Window Gravity State: NorthWestGravity
  Backing Store State: NotUseful
  Save Under State: no
  Map State: IsViewable
  Override Redirect State: no
  Corners:  +0+0  -0+0  -0-0  +0-0
  -geometry 1366x768+0+0

But when I use appearance wizard it comes down to 1682x859 with offset 21x0 before I see the arrows...but then on the other hand it apparently screwed up the display size - so this one is not really working.

Manually I come to about 1840x1020 with 45x30 offset for optimal display.
So I guess the card is really running with 1920x1080 with some overscanning. I'll have to see how it turns out with HDMI cable

---

