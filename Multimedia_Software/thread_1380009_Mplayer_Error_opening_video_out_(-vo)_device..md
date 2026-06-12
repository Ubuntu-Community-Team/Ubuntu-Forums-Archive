---
title: "Mplayer: Error opening video_out (-vo) device."
date: 2010-01-13
forum: Multimedia Software
---

### Post by howcanireachthesekids on 2010-01-13
I have searched google and the forums  !

I get that error when trying to open an .flv or .avi file. Anyway to fix it ?

Here is the output of gui.conf
```
**http://pastebin.com/fb3c024d**
```Here is the output of mplayer -vo help
```
fsjal@fsjal-localhost:~$ mplayer -vo help
MPlayer SVN-r29237-4.4.1 (C) 2000-2009 MPlayer Team
Available video output drivers:
    xmga    Matrox G200/G4x0/G550 overlay in X11 window (using /dev/mga_vid)
    mga    Matrox G200/G4x0/G550 overlay (/dev/mga_vid)
    tdfxfb    3Dfx Banshee/Voodoo3/Voodoo5
    3dfx    3dfx (/dev/3dfx)
    xv    X11/Xv
    vdpau    VDPAU with X11
    x11    X11 ( XImage/Shm )
    xover    General X11 driver for overlay capable video output drivers
    gl    X11 (OpenGL)
    gl2    X11 (OpenGL) - multiple textures version
    dga    DGA ( Direct Graphic Access V2.0 )
    sdl    SDL YUV/RGB/BGR renderer (SDL v1.1.7+ only!)
    fbdev    Framebuffer Device
    fbdev2    Framebuffer Device
    svga    SVGAlib
    caca    libcaca
    v4l2    V4L2 MPEG Video Decoder Output
    directfb    Direct Framebuffer Device
    dfbmga    DirectFB / Matrox G200/G400/G450/G550
    xvidix    X11 (VIDIX)
    cvidix    console VIDIX
    null    Null video output
    xvmc    XVideo Motion Compensation
    mpegpes    MPEG-PES to DVB card
    yuv4mpeg    yuv4mpeg output for mjpegtools
    png    PNG file
    jpeg    JPEG file
    gif89a    animated GIF output
    tga    Targa output
    pnm    PPM/PGM/PGMYUV file
    md5sum    md5sum of each frame


```Ubuntu Karmic Koala x86 with latest updates, installed Mplayer with the only command of sudo apt-get install mplayer
I have an Nvidia 9200M GS

thanks in advance guys.

---

### Post by gradinaruvasile on 2010-01-13
Remove the .conf file. When you start mplayer, it will generate a new one.

And from command line you may specify the video out (vo) device - xv is recommended, its the standard X video:

mplayer -vo xv moviename

---

### Post by howcanireachthesekids on 2010-01-13
> **gradinaruvasile said:**
> Remove the .conf file. When you start mplayer, it will generate a new one.

And from command line you may specify the video out (vo) device - xv is recommended, its the standard X video:

mplayer -vo xv moviename

ok i removed the gui.conf file and re-opened Mplayer, still the same error

about this m**player -vo xv moviename **do i have to do that everytime for different filenames ? :o
how can i do it only once and for all, lets say for .flv files

EDIT : ok i went to the directory where file.flv is and i tried opening it, it opened successfully without any error but it doesn't show any video. nor does it say to download any codec or plugin. it however shows the thumbnail in file explorer

---

### Post by howcanireachthesekids on 2010-01-13
bump for help

---

### Post by gradinaruvasile on 2010-01-13
Open it from the command line (terminal). What output do you have?

---

