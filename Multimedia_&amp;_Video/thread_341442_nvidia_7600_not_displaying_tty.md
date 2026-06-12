---
title: "nvidia 7600 not displaying tty"
date: 2007-01-18
forum: Multimedia &amp; Video
---

### Post by niemand on 2007-01-18
I have installed Ubuntu 6.06 (not my first install by far) and have nearly everything working on my new laptop (MSI 171772-2). In fact it has all worked right out of the box including the wireless. The only problem I am having is with the video.

I have the proprietary nvidia drivers installed and glx is loading and working without any problems. It correctly decides that the display is 1680x1050 and X11 runs just fine. If I then do a ctrl-alt-F1 I seen nothng at all. However, if I login (blind) and type 'cat > /tmp/t.t' and then some text and then go back to X11 (ctrl-alt-F7), then I find the file with the text that I have typed in it. So, the tty is working just fine; the display is not. Actually, none of the 6 ttys show any display but they do accept input.

When the machine boots I see the BIOS splash and the Ubuntu splash along with all associated text unitl it starts X. The display is blank during shutdown. I am way too chicken to set the init level to 3 in inittab and have not successfully gotten GRUB to let me do it for one boot either.

I have modified my xorg.conf and removed (commented out) some items like DPMS and DRI just to see if they are the problem children. They are not, or, at the very least, they are not the only problem children. I have also browsed through the Xorg.0.log and found not unexpected errors (missing watcom devices but who cares) or any signs that things are wrong. Hence, I have no idea why the ttys are blank and thus this post.

Things that I think are pertinent:

from xorg.conf

Section "Device"
        Identifier      "NVIDIA Corporation NVIDIA Default Card"
        Driver          "nvidia"
        BusID           "PCI:4:0:0"
EndSection

       SubSection "Display"
                Depth           24
                Modes           "1680x1050" #"1024x768" "800x600" "640x480"
        EndSubSection

Section "Module"
        Load    "i2c"
        Load    "bitmap"
        Load    "ddc"
        Load    "dri"
        Load    "extmod"
        Load    "freetype"
        Load    "glx"
        Load    "int10"
        Load    "type1"
        Load    "vbe"
EndSection


from Xorg.0.log

<...snip...>
(II) Setting vga for screen 0.
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Enabling RENDER acceleration
(II) NVIDIA(0): NVIDIA GPU GeForce Go 7600 at PCI:4:0:0
(--) NVIDIA(0): VideoRAM: 262144 kBytes
(--) NVIDIA(0): VideoBIOS: 05.73.22.42.03
(II) NVIDIA(0): Detected PCI Express Link width: 16X
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(--) NVIDIA(0): Connected display device(s) on GeForce Go 7600 at PCI:4:0:0:
(--) NVIDIA(0):     Seiko (DFP-0)
(--) NVIDIA(0): Seiko (DFP-0): 330.0 MHz maximum pixel clock
(--) NVIDIA(0): Seiko (DFP-0): Internal Dual Link LVDS
(II) NVIDIA(0): Assigned Display Device: DFP-0
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "1680x1050"
(II) NVIDIA(0): Virtual screen size determined to be 1680 x 1050
(--) NVIDIA(0): DPI set to (115, 115); computed from "UseEdidDpi" X config option
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
<...snip...>
(II) NVIDIA(0): Setting mode "1680x1050"

I have searched the forum and the web to no avail. I want to say thanks in advance for any and all help as well.

---

### Post by niemand on 2007-01-22
So, the mystery is deepening. I connected a second monitor to the DVI output of the laptop. When the machine booted, I watched everything in stereo until X11 started. At that time, the monitor off the DVI output simply went black and stayed black. I hit the F2 key a couple of times but it never warmed back up so I am thinking I need to activate the second output via software instead of that little switch. I do not think it will fix my missing TTYs, but it is just another bread crumb leading to the mystery.

---

### Post by Foxmike on 2007-02-14
Well, I got the exact same problem with my desktop running NVIDIA Geforce 6200 over AGP8x, proprietary drivers installed.

I have tried to put "vga=792" at the end of the kernel line in /boot/grub/menu.lst but it didn't change anything.  I installed NVIDIA drivers from this guide (which is great by the way!, thanks tseliot!): [http://doc.gwos.org/index.php/Latest_Nvidia_Edgy](http://doc.gwos.org/index.php/Latest_Nvidia_Edgy), and at the end (problems section) the author suggest to put out that "splash" at the end of the kernel list.

Still to be tried, but i like to get that splash screen!...

Anyone has any idea of what it could take to fix that?

Thank you!

-FM

EDIT: Ok, this doesn't work... To me it looks like a video driver problem... let's investigate the xorg.conf....

---

### Post by niemand on 2007-02-19
I have tried various futzing with the config.xorg and have not found anything suitable yet. I also tried various glx switches with no changes either. I am half tempted to roll back to the open driver and see if the problem persists with it as well. However, I find myself just a little too busy to get to that. Let me know how you fair.

---

### Post by charles.g.moore on 2007-03-28
I have the same problem, I know that if I change back to the 'nv' driver I get my tty back.
The only thing is no 3D acceleration with 'nv'

Did you eventually get a fix?  If so let me know...

---

### Post by niemand on 2007-03-28
I have not had any time to put into fixing it, so no I have not fixed it.

I have half considered making two X configuiration that I would choose when booting, but never got to it. There are occasions where I need the 3D acceleration and occasions where I know it will not be needed. I would rather not have to choose though. I keep hoping that NVidia will release a new driver where this will not be a problem anymore. Since the nv driver does allow tty's, then it really must be an NVidia driver problem.

---

### Post by charles.g.moore on 2007-03-29
> **niemand said:**
> I have installed Ubuntu 6.06 (not my first install by far) and have nearly everything working on my new laptop (MSI 171772-2). In fact it has all worked right out of the box including the wireless. The only problem I am having is with the video.

I have the proprietary nvidia drivers installed and glx is loading and working without any problems. It correctly decides that the display is 1680x1050 and X11 runs just fine. If I then do a ctrl-alt-F1 I seen nothng at all. However, if I login (blind) and type 'cat > /tmp/t.t' and then some text and then go back to X11 (ctrl-alt-F7), then I find the file with the text that I have typed in it. So, the tty is working just fine; the display is not. Actually, none of the 6 ttys show any display but they do accept input.

When the machine boots I see the BIOS splash and the Ubuntu splash along with all associated text unitl it starts X. The display is blank during shutdown. I am way too chicken to set the init level to 3 in inittab and have not successfully gotten GRUB to let me do it for one boot either.

I have modified my xorg.conf and removed (commented out) some items like DPMS and DRI just to see if they are the problem children. They are not, or, at the very least, they are not the only problem children. I have also browsed through the Xorg.0.log and found not unexpected errors (missing watcom devices but who cares) or any signs that things are wrong. Hence, I have no idea why the ttys are blank and thus this post.

Things that I think are pertinent:

from xorg.conf

Section "Device"
        Identifier      "NVIDIA Corporation NVIDIA Default Card"
        Driver          "nvidia"
        BusID           "PCI:4:0:0"
EndSection

       SubSection "Display"
                Depth           24
                Modes           "1680x1050" #"1024x768" "800x600" "640x480"
        EndSubSection

Section "Module"
        Load    "i2c"
        Load    "bitmap"
        Load    "ddc"
        Load    "dri"
        Load    "extmod"
        Load    "freetype"
        Load    "glx"
        Load    "int10"
        Load    "type1"
        Load    "vbe"
EndSection


from Xorg.0.log

<...snip...>
(II) Setting vga for screen 0.
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Enabling RENDER acceleration
(II) NVIDIA(0): NVIDIA GPU GeForce Go 7600 at PCI:4:0:0
(--) NVIDIA(0): VideoRAM: 262144 kBytes
(--) NVIDIA(0): VideoBIOS: 05.73.22.42.03
(II) NVIDIA(0): Detected PCI Express Link width: 16X
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(--) NVIDIA(0): Connected display device(s) on GeForce Go 7600 at PCI:4:0:0:
(--) NVIDIA(0):     Seiko (DFP-0)
(--) NVIDIA(0): Seiko (DFP-0): 330.0 MHz maximum pixel clock
(--) NVIDIA(0): Seiko (DFP-0): Internal Dual Link LVDS
(II) NVIDIA(0): Assigned Display Device: DFP-0
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "1680x1050"
(II) NVIDIA(0): Virtual screen size determined to be 1680 x 1050
(--) NVIDIA(0): DPI set to (115, 115); computed from "UseEdidDpi" X config option
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
<...snip...>
(II) NVIDIA(0): Setting mode "1680x1050"

I have searched the forum and the web to no avail. I want to say thanks in advance for any and all help as well.


niemand,
Take a look at my post and do what tseliot suggested, it worked perfectly for me.  I have no splash screen but it does not matter to me.

[http://www.ubuntuforums.org/showthread.php?t=395580](http://www.ubuntuforums.org/showthread.php?t=395580)

I now have my terminal screens back :) 

Thanks again to tseliot for the fix!!!

---

### Post by hardyn on 2007-03-29
same with 6600 go.... and im not going back to NV... its a really horrible driver for notebooks.

---

### Post by niemand on 2007-03-30
I got rid of the splash from the boot line and I have ttys back. I thought I had tried that before and it did not work, but whatever. It is working now.

Thanks.

---

