---
title: "Totem, Mplayer crash on X error &quot;insufficient resources&quot;"
date: 2008-07-10
forum: Multimedia Software
---

### Post by Douglas Royds on 2008-07-10
All video programs crash with the error "X11 error: BadAlloc (insufficient resources for operation)" when I play video > 640x480 (eg. DVD, DV) - Totem, mplayer, xine, vlc, avidemux, kdenlive, they all crash.

This is not a physical limitation of the laptop - these programs all worked fine under Feisty, and I was a happy little DVD viewer. It fell apart with the Gutsy upgrade, I believe. Mplayer can play DVDs (barely) with the -vo x11 option (this is an xv problem), but the laptop doesn't really have the snot for that - I need this graphic chip working.

The laptop has a SiS chipset. I have just done a fresh install of Ubuntu Hardy. Interestingly, there is now no reference to SiS in xorg.conf at all. Looks like Xorg is doing it all automatically, clever wee thing:

    $ grep -i SIS /var/log/Xorg.0.log
    (--) PCI:*(1:0:0) Silicon Integrated Systems [SiS] 630/730 PCI/AGP ...
    ...
    (--) SIS(0): VideoRAM: 8192 KB
    (II) SIS(0): Using 4096K of framebuffer memory at offset 0K
    (--) SIS(0): Hardware supports two video overlays
    ...

This kind of all looks OK to me.

Suggestions?

---

### Post by Douglas Royds on 2008-07-11
Tried these, without success:

[LIST=1]
[*]Can't set the video memory from the bios - it seems to be permanently set at 8Mb
[*]Lowering the resolution with xrandr didn't help - not even 640x480
[*]Turning off extension MIT-SHM in xorg.conf didn't help
[*]mplayer -vo sdl didn't help
[/LIST]

---

### Post by Tim Crumpton on 2008-08-09
I have just fixed this problem on my own machine (Sony Vaio T1XP).
I discovered I had caused it myself by trying to get rid of the message "opera: X Shared memory extension is not available. ZPixmap not supported"

I got rid of the error message above by adding the following to my /etc/X11/xorg.conf file:
#Section "Device"
#	Identifier	"Configured Video Device"
#	Option "AccelMethod" "XAA" #not EXA
#EndSection

This worked, but left me with the same problem you found. Commenting out my own code block, and restarting gdm, had mplayer working again. I guess I am using EXA now.

I can live with the error message. It has no detrimental effect, I was just being tidy.

Tim Crumpton, Altrincham

---

