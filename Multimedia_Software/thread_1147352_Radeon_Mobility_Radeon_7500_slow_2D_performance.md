---
title: "Radeon Mobility Radeon 7500 slow 2D performance"
date: 2009-05-03
forum: Multimedia Software
---

### Post by sailor420 on 2009-05-03
Hi all,

I installed a clean Jaunty install on my IBM T40 laptop with Radeon Mobility 7500 video card yesterday. So far it's all straight out of the box. Everything is working very well so far, with one exception--my 2D performance is pretty miserable. Windows are slow to draw, minimizing/maximizing takes a long time, alt-tab is almost unusable, and scrolling webpages is very jerky. CPU usage is pretty low most of the time.

Any ideas on what I can do to solve this? It's the only thing (well, that and wireless, but that's another conversation) keeping me from really making use of Ubuntu as my primary OS.

Info that may be useful:
--xorg.conf is blank, so I'm assuming it's using whatever defaults were provided by the installation.
--System information > Display:

-Display-
Resolution		: 1024x768 pixels
Vendor		: The X.Org Foundation
Version		: 1.6.0
-Monitors-
Monitor 0		: 1024x768 pixels
-Extensions-
BIG-REQUESTS
Composite
DAMAGE
DOUBLE-BUFFER
DPMS
DRI2
GLX
Generic Event Extension
MIT-SCREEN-SAVER
MIT-SHM
RANDR
RECORD
RENDER
SECURITY
SGI-GLX
SHAPE
SYNC
X-Resource
XC-MISC
XFIXES
XFree86-DGA
XFree86-DRI
XFree86-VidModeExtension
XINERAMA
XInputExtension
XKEYBOARD
XTEST
XVideo
-OpenGL-
Vendor		: Tungsten Graphics, Inc.
Renderer		: Mesa DRI Radeon 20061018 AGP 4x x86/MMX/SSE2 TCL
Version		: 1.3 Mesa 7.4
Direct Rendering		: Yes


Thanks for any help, and let me know if there's anymore information that I can provide.

---

### Post by sailor420 on 2009-05-03
So after a bit more tweaking, it does actually appear that the CPU usage spike during when using alt-tab, scrolling web browser, or opening/closing/moving windows, which makes me wonder if it's using the card at all for 2D rendering. Is there any way to check this?

---

### Post by sailor420 on 2009-05-04
*bump*

Anyone? This is driving me crazy--the machine is practically unusable...

Thanks for any help!

---

### Post by sailor420 on 2009-05-05
It appears I've gotten this working. In case someone else has a similar problem or a similar system (IBM T40 with Radeon Mobility 7500 video card), I'll post what I did here.

This thread was a huge help: [http://ubuntuforums.org/showthread.php?t=1051571](http://ubuntuforums.org/showthread.php?t=1051571)

I took the above and tweaked with it a bit more, and ended up with the below "Device" section in my xorg.conf. Things are now much, much faster, and I can run Compiz with just about any effects with no slowdown.

```

Section "Device"
    Identifier    "Configured Video Device"
    Option "AGPMode" "4"
    Option "AGPFastWrite" "True"
    Option "EnablePageFlip" "True"
    Option "AGPMode" "4"
    Option "AGPSize" "64"
    Option "RingSize" "8"
    Option "BufferSize" "2"
    Option "EnableDepthMoves" "true"
    Option "RenderAccel" "true"
    # Eyecandy Stuff
    Option "AccelMethod" "XAA"
    Option "EnablePageFlip" "true
    Option "DDCMode"
    Option "SubPixelOrder" "NONE"
    Option "ColorTiling" "false"
    Option "MigrationHeuristic" "greedy"
EndSection

```

---

### Post by Sixti on 2009-05-14
Hello,

Here are the best Options to Mobility Radeon 7500 in my opinion:

        Option     "AGPMode"                    "4"
        Option     "AGPFastWrite"               "on"
        Option     "EnablePageFlip"             "on"
        Option     "DynamicClocks"              "on" - extend your battery life when in standby
        Option     "AccelMethod"                "XAA" - best performance with Firefox

I know that glxgears is not the perfect benchmark, but I could increase the 3D by 20% using it as a reference. Compiz is working, but when you open some windows the performance is bad, and I prefer to turn it off. Another trick that I use to increse the performance is to set Metacity to reduced_resources under gconf-editor.

But I feel a slow response in 2D, using apps like Firefox and Thunderbird.

I hope I could help you.

---

### Post by parsifal_ on 2009-07-26
This was very helpful. I was able to set up my Thinkpad R40 to have good video performance. Thanks!

---

### Post by Orb2069 on 2009-11-07
> **sailor420 said:**
> I
I took the above and tweaked with it a bit more, and ended up with the below "Device" section in my xorg.conf. Things are now much, much faster, and I can run Compiz with just about any effects with no slowdown.
[/code]

Thanks! came here with this exact problem, and your config worked great for me! :D

---

