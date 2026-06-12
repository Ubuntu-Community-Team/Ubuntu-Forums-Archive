---
title: "dosemu full-screen... and X?"
date: 2012-11-14
forum: Multimedia Software
---

### Post by ray field on 2012-11-14
I am a big user of dosemu, which is stable enough under Ubuntu.

However, from time to time I end up with a release/hardware combination under which fullscreen dosemu (or xdosemu) fails or becomes unusable. For the most part I've ended up blaming Nvidia -- for example, with this GeForce 8400 under 12.04 and 10.04 on my desktop box, fullscreen works well enough, but under 12.04 ONLY with the nvidia-173 driver.  Otoh, however with 12.04 on my Lenovo netbook, the fullscreen dosemu fonts are too small, and under 12.10 in this desktop box, fullscreen dosemu is basically unusable with *any* of the Nvidia drivers.

After months of scratching my head, however, it dawned on me that maybe I can fix the problem by tweaking X. Not that I know anything about it -- however, this excerpt from the dosemu readme gives a basic idea how dosemu interacts. I am hoping it might help someone point me in the right direction.

[B]8.3. The VGA Emulator

In X, a VGA card is emulated. The same happens if you use the SDL library using dosemu -S. This emulation (vgaemu) enables X to run graphics modes.

Some features:

    Video memory. 1 Mb is allocated. It is mapped with mmap() in the VGA memory region of DOSEMU (0xa00000-0xbfffff) to support bank switching. This is very i386-Linux specific, don't be surprised if it doesn't work under NetBSD or another Linux flavour (Alpha/Sparc/MIPS/etc).

    The DAC (Digital to Analog Converter). The DAC is completely emulated, except for the pelmask. This is not difficult to implement, but it is terribly slow because a change in the pelmask requires a complete redraw of the screen. Fortunately, the pelmask changes aren't used often so nobody will notice ;-)

    The attribute controller is emulated.

    The emulator emulates a basic Trident TVGA8900C graphics card. All standard VGA modes are emulated, most VGA hardware features (mode-X, 320x240 and so on), some Trident extensions, and on top of that many high-resolution VESA 2.0 modes, that were not present in the original Trident card. Some (very few) programs, such as Fast Tracker, play intimately with the VGA hardware and may not work. As vgaemu improves these problems should disappear.

    Nearly full VESA 2.0 support.

    A VESA compatible video BIOS is mapped at 0xc00000. It is small because it only contains some glue code and the BIOS fonts (8x8, 8x14, 8x16).

    support for hi- and true-color modes (using Trident SVGA mode numbers and bank switching)

    Support for mode-X type graphics modes (non-chain4 modes as used by e.g. DOOM)

    gamma correction for graphics modes

    video memory size is configurable via dosemu.conf

    initial graphics window size is configurable

    The current hi- (16bpp) and true (24/32bpp) color support does not allow resizing of the graphics window and gamma correction is ignored.

As the typical graphics mode with 320x200x8 will be used often with large scalings and modern graphics boards are pretty fast, Steffen Winterfeldt added something to eat up your CPU time: you can turn on the bilinear interpolation. It greatly improves the display quality (but is rather slow as I haven't had time yet to implement an optimized version - it's plain C for now). If the bilinear filter is too slow, you might instead try the linear filter which interpolates only horizontally.

Note that (bi)linear filtering is not available on all VGA/X display combinations. The standard drawing routines are used instead in such cases.

If a VGA mode is not supported on your current X display, the graphics screen will just remain black. Note that this does not mean that DOSEMU has crashed.

The only unsupported VBE function is VGA state save/restore. But this functionality is rarely used and its lack should not cause too much problems.

VBE allows you to use the horizontal and vertical scrolling function even in text modes. This feature is not implemented.

If you think it causes problems, the linear frame buffer (LFB) can be turned of via dosemu.conf as well as the protected mode interface. Note, however, that LFB modes are faster than banked modes, even in DOSEMU.

The default VBE mode list defines a lot of medium resolution modes suitable for games (like Duke3D). You can still create your own modes via dosemu.conf. Note that you cannot define the same mode twice; the second (and all subsequent) definitions will be ignored.

Modes that are defined but cannot be supported due to lack of video memory or because they cannot be displayed on your X display, are marked as unsupported in the VBE mode list (but are still in it).

The current interface between VGAEmu and X will try to update all invalid video pages at a time. This may, particularly in hi-res VBE/SVGA modes, considerably disturb DOSEMU's signal handling. That cannot be helped for the moment, but will be addressed soon (by running an extra update thread).

If you really think that this is the cause of your problem, you might try to play with veut.max_max_len in env/video/render.c. This variable limits the amount of video memory that is updated during one timer interrupt. This way you can dramatically reduce the load of screen updates, but at the same rate reduce your display quality.

Gamma correction works in both 4 and 8 bit modes. It must be specified as a float value, e.g. $_X_gamma=(1.0). Higher values give brighter graphics, lower make them darker. Reasonable values are within a range of 0.5 ... 2.0.

You can specify the video memory size that the VGA emulator should use in dosemu.conf. The value will be rounded up to the nearest 256 kbyte boundary. You should stick to typical values like 1024, 2048 or 4096 as not to confuse DOS applications. Note that whatever value you give, 4 bit modes are only supported up to a size of 800x600.

You can influence the initial size of the graphics window in various ways. Normally it will have the same size (in pixel) as the VGA graphics mode, except for mode 0x13 (320x200, 256 colors), which will be scaled by the value of mode13fact (defaults to 2). Alternatively, you can directly specify a window size in dosemu.conf via $_X_winsize. You can still resize the window later.

The config option $_X_fixed_aspect allows you to fix the aspect ratio of the graphics window while resizing it. Alternatively, $_X_aspect_43 ties the aspect ratio to a value of 4:3. The idea behind this is that, whatever the actual resolution of a graphics mode is in DOS, it is displayed on a 4:3 monitor. This way you won't run into problems with modes such as 640x200 (or even 320x200) which would look somewhat distorted otherwise.

For planar modes (for instance, most 16 colour modes, but also certain 256-colour modes: mode-X), vgaemu has to switch to partial cpu emulation. This can be slow, but expect it to improve over time.

[/B]

---

### Post by ray field on 2012-11-14
To give a little more detail: another problem is, often when returning from fullscreen dosemu, the resolution of the Unity desktop is degraded -- from 1920x1080 to something like 800x600. I have to reboot to regain it.

---

