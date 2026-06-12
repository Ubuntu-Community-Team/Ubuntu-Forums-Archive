---
title: "Problems getting DVDs to play using MPLAYER with DXR3 (Hollywood +) card"
date: 2006-12-17
forum: Multimedia &amp; Video
---

### Post by markofealing on 2006-12-17
My configuration:

PIII 450 with 320Mb RAM
Ubuntu Edgy (6.10)
Hollywood Plus DXR3 card
Matrox G400 AGP video card (using the patched Matrox DEB driver for xserver bug #65876)

Packages installed:

[INDENT]apt-get install mplayer
apt-get install em8300[/INDENT]

MPLAYER should be able to drive the DXR3 card and preferable through the TV Out socket, but so far I've failed to get this to work! 

MPLAYER works beautifully if you specify a -vo x11 or -vo xv in the command line, and it will even scale with the -zoom switch! However if you use  any of the following options after -vo:

        xmga    Matrox G200/G4x0/G550 overlay in X11 window (using /dev/mga_vid)
        mga     Matrox G200/G4x0/G550 overlay (/dev/mga_vid)
        dxr3    DXR3/H+ video out

you get the following error in this case mplayer -vo mga IceAge.avi      

[FONT="Courier New"]
open: No such file or directory
Couldn't open: /dev/mga_vid
Error opening/initializing the selected video_out (-vo) device.[/FONT]

So checking /dev/mga_vid, I discover there is no such driver. So did a find and found /usr/lib/mplayer/vidix/mga_vid.so. Looks good so replaced mga which defaults to /dev/mga_vid to the former and got 

[FONT="Courier New"]
Error opening/initializing the selected video_out (-vo) device.[/FONT]

Having browsed through the manual (man mplayer) which is very comprehensive, especially the section on the DXR3 -vo option:[FONT="Courier New"]

       dxr3 (DXR3 only)
              Sigma Designs em8300 MPEG decoder chip (Creative DXR3, Sigma Designs Hollywood Plus) specific video output driver.  Also see
              the lavc video filter.
                 overlay
                      Activates the overlay instead of TVOut.
                 prebuf
                      Turns on prebuffering.
                 sync
                      Will turn on the new sync-engine.
                 norm=<norm>
                      Specifies the TV norm.
                         0: Does not change current norm (default).
                         1: Auto-adjust using PAL/NTSC.
                         2: Auto-adjust using PAL/PAL-60.
                         3: PAL
                         4: PAL-60
                         5: NTSC

                 <0-3>
                      Specifies the device number to use if you have more than one em8300 card.[/FONT]

I can't see where I'm going wrong.

HELP PLEASE!! ](*,)

P.S. 

I was expecting to see the /dev/em8300 drivers when I installed that package, and although the program did run which requested whether I had a creative of Hollywood plus card and to choose the chipset (which I did) the drivers never appeared! I'm getting the feeling that this is some sort of bug in edgy, but I'm very happy to be proved wrong!

---

