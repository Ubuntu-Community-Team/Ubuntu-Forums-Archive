---
title: "MPlayer without X on Gateway MX3417"
date: 2007-10-29
forum: Multimedia &amp; Video
---

### Post by hayawardh on 2007-10-29
Hi all, 

I would like to get mplayer to play videos without X, on the command line. 
I am running Gateway MX3417 (AMD64, nVidia, Ubuntu Feisty)

mplayer -vo help
Available video output drivers:
        xmga    Matrox G200/G4x0/G550 overlay in X11 window (using /dev/mga_vid)
        mga     Matrox G200/G4x0/G550 overlay (/dev/mga_vid)
        tdfxfb  3Dfx Banshee/Voodoo3/Voodoo5
        3dfx    3dfx (/dev/3dfx)
        xv      X11/Xv
        x11     X11 ( XImage/Shm )
        xover   General X11 driver for overlay capable video output drivers
        gl      X11 (OpenGL)
        gl2     X11 (OpenGL) - multiple textures version
        dga     DGA ( Direct Graphic Access V2.0 )
        sdl     SDL YUV/RGB/BGR renderer (SDL v1.1.7+ only!)
        ggi     General Graphics Interface (GGI) output
        fbdev   Framebuffer Device
        fbdev2  Framebuffer Device
        aa      AAlib
        caca    libcaca
        dxr3    DXR3/H+ video out
        xvidix  X11 (VIDIX)
        cvidix  console VIDIX
        null    Null video output
        xvmc    XVideo Motion Compensation
        mpegpes Mpeg-PES to DVB card
        yuv4mpeg        yuv4mpeg output for mjpegtools
        png     PNG file
        jpeg    JPEG file
        gif89a  animated GIF output
        tga     Targa output
        pnm     PPM/PGM/PGMYUV file
        md5sum  md5sum of each frame

If I am right, I need to -vo vesa for playing without X, but vesa is not listed. 
mplayer -vo caca plays using color ascii successfully, but not good enough quality as expected. 

What should I do? 
Thanks.
Hayawardh

---

