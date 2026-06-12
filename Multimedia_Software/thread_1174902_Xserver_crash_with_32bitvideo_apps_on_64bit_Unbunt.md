---
title: "Xserver crash with 32bitvideo apps on 64bit Unbuntu 8.10"
date: 2009-05-31
forum: Multimedia Software
---

### Post by wonkware on 2009-05-31
What's the deal with 64bit Ubuntu and running 32bit apps that use video or any kind
of rendering.

I have an Intel DG35EC with a QuadCore processor and 8G of RAM.  The onboard video is an 82G35 Express Integrated Graphics Controller.  I'm running 64bit Ubuntu 8.10 and everything works fine in 64bit mode.  I can run compiz-fusion with the rotating cube desktop, etc.

The problem comes in when I try to run anything that runs 32bit and does something which requires some-kind (not exactly sure) of special rendering.  The 3 big offenders are the Android emulator, VirtualBox trying to run a 32bit XP instance, and Wine trying to run anything.

The app itself seems to run fine but in it's communication with the X-server (which it talks
to over a mounted socket) the X-Server crashes with a Segmentation Violation.  Really.  How can a client app -- which sends rendering requests -- crash the server app?  But I digress...

In any case I spent like 6 hours yesterday Google'ing down all manner of keywords and phrases I found in logs, output, and using strace:
    /var/log/messages
    /var/log/Xorg.0.log
    xrandr
    glxinfo
    lspci
    compiz-check

And installing all manner of packages for each lead I was trying to run down.

In the end I found that for these 32bit apps to run I needed to run 'compiz --replace &' (which I discovered by accident) after I logged into a new X session.  The problem with this is that although it seems to be working for the moment it seems to be a rather fragile solution because the output from compiz is not very encouraging:[INDENT]Detected PCI ID for VGA: 
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1600x1200) to maximum 3D texture size (2048): Passed.
Checking for Software Rasterizer: Not present. 
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
Starting gtk-window-decorator
  [/INDENT]See, the thing is all other indicators are that everything is running fine regarding rendering.  Consider this:[INDENT]$ glxinfo | egrep "Mesa|direct"
direct rendering: Yes
OpenGL renderer string: Mesa DRI Intel(R) 965G 20061102
OpenGL version string: 1.4 Mesa 7.2
[/INDENT](I have seen reference to a new version of Mesa but I can't find it using the currently configured apt-get sources) and this:[INDENT]$ export LIBGL_DEBUG=verbose;glxgears
libGL: XF86DRIGetClientDriverName: 1.9.0 i965 (screen 0)
libGL: OpenDriver: trying /usr/lib/dri/tls/i965_dri.so
libGL: OpenDriver: trying /usr/lib/dri/i965_dri.so
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 4, (OK)
drmOpenByBusid: Searching for BusID pci:0000:00:02.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 4, (OK)
drmOpenByBusid: drmOpenMinor returns 4
drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
libGL error: 
Can't open configuration file /etc/drirc: No such file or directory.
libGL error: 
Can't open configuration file /home/jeffp/.drirc: No such file or directory.
6000 frames in 5.0 seconds = 1199.910 FPS
6203 frames in 5.0 seconds = 1240.462 FPS
[/INDENT]1200+ Frames Per Second!?  This app (glxgears) is *the* most referenced
benchmark for testing your video configuration and most problems I found
on the web were people complaining about 20fps - 60fps.  Clearly I am not
in that group.

Things seem to run fine except that I can't run some things without the compiz
hack, but I found that by accident and it feels more than a little suspect, and since
I just found the solution yesterday I don't have any feel for how stable it is.
So I'm thinking maybe all I did was find a haphazard band-aid and there is
a more robust solution which somebody can help me with.

Any help would be greatly appreciated.  Thanks.

/J

---

