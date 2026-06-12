---
title: "Second graphics card (NVIDIA) only as a Framebuffer"
date: 2006-10-31
forum: Multimedia &amp; Video
---

### Post by shanz1999 on 2006-10-31
I have Ubuntu Dapper Drake.

$ uname -a
[INDENT]Linux eswlin01 2.6.15-27-386 #1 PREEMPT Sat Sep 16 01:51:59 UTC 2006 i686 GNU/Linux[/INDENT]

My first graphics card is an NVIDIA GeForce2 MX/MX 400 which I use on my main monitor.
I have just installed a new NVIDIA GeForce FX 5200 (which has VGA, DVI & TVOUT connectors) and second monitor.  I only want to use the second card and monitor to play with the card's framebuffer.  I will not need to run an X window on it since I intend to interface directly with the low-level /dev/fb* device (as X does).

I don't know whether I need to install any NVIDIA drivers for the second card at all?  I have read that I could use VESAFB?

The second monitor has a flashing green power light indicating that it is receiving no signal.

This is what I know ...

$/sbin/lspci | grep -i vga
    01:00.0    NV11[GeForce2 MX/MX 400]
    02:02.0    NV34[GeForce FX 5200]

$/dev/ls -als fb*
    0 crw-rw---- 1 root video 29, 0 2006-10-31 15:25 fb0
    0 crw-rw---- 1 root video 29, 1 2006-10-31 15:25 fb1
    0 crw-rw---- 1 root video 29, 2 2006-10-31 15:25 fb2
 
$fbset -i -fb /dev/fb0
[INDENT]mode "640x400-70"
    # D: 25.176 MHz, H: 31.469 kHz, V: 69.932 Hz
    geometry 640 400 640 400 4
    timings 39721 40 24 39 9 96 2
    rgba 6/0,6/0,6/0,0/0
endmode

Frame buffer device information:
    Name        : VGA16 VGA
    Address     : 0xa0000
    Size        : 65536
    Type        : VGA 16 colors in 4 planes
    Visual      : PSEUDOCOLOR
    XPanStep    : 8
    YPanStep    : 1
    YWrapStep   : 0
    LineLength  : 80
    Accelerator : No[/INDENT]

$fbset -i -fb /dev/fb1
[INDENT]mode "640x480-60"
    # D: 25.176 MHz, H: 31.469 kHz, V: 59.942 Hz
    geometry 640 480 640 32767 8
    timings 39721 40 24 32 11 96 2
    accel true
    rgba 8/0,8/0,8/0,0/0
endmode

Frame buffer device information:
    Name        : NV11
    Address     : 0xc0000000
    Size        : 67108864
    Type        : PACKED PIXELS
    Visual      : PSEUDOCOLOR
    XPanStep    : 8
    YPanStep    : 1
    YWrapStep   : 0
    LineLength  : 0
    MMIO Address: 0xfb000000
    MMIO Size   : 16777216
    Accelerator : nVidia Arch 10[/INDENT]

$fbset -i -fb /dev/fb2
[INDENT]mode "640x480-60"
    # D: 25.176 MHz, H: 31.469 kHz, V: 59.942 Hz
    geometry 640 480 640 3072 8
    timings 39721 40 24 32 11 96 2
    accel true
    rgba 8/0,8/0,8/0,0/0
endmode

Frame buffer device information:
    Name        : NV32
    Address     : 0xd0000000
    Size        : 2097152
    Type        : PACKED PIXELS
    Visual      : PSEUDOCOLOR
    XPanStep    : 8
    YPanStep    : 1
    YWrapStep   : 0
    LineLength  : 0
    MMIO Address: 0xff000000
    MMIO Size   : 16777216
    Accelerator : nVidia Arch 30[/INDENT]

I have downloaded ezfb [http://www.akrobiz.com/ezfb/]("http://www.akrobiz.com/ezfb/")

and hope to use one of it's example programs to get something displayed on my second (framebuffer) monitor.

Can anyone help me?  I am not getting anything on the second monitor at all - not even a solid green power light!

I have attached my .config file.

Thanks.

---

