---
title: "I've tried several guides but I am still having problems with my nvidia card."
date: 2006-11-02
forum: Multimedia &amp; Video
---

### Post by DianWei on 2006-11-02
As far as I understand, 
running
```
nvidia-settings
```
seems to indicate that my drivers are installed at least somewhat. However, opengl-ish apps such as most of the screensavers have stopped working right. I read that you should test whether or not your driver is working correctly by typing 
```
glxinfo | grep rendering
```
however this only outputs:
```
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
...
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".

```

I am thinking that my xorg.conf may be set up incorrectly, and this may have to do with using linux-686 image kernels before the upgrade to 6.10, as it seems linux-generic has taken its place. 

Among the oddities in my xorg.conf that might be relevant to the problem is this section
```
Section "Device"
    Identifier     "NVIDIA Corporation NV6 [Vanta/Vanta LT]"
    Driver         "nvidia"
EndSection
```
Looking at the rest of the xorg file, it appears some options should be in between the Driver line and the EndSection line.

If it helps any here is my card information as gleaned from nvidia-settings (no laughing)

Graphics Processor: Vanta/Vanta LT
Bus Type: AGP
VBIOS Version: 02.05.13.03.00
Video Memory:  16 MB
IRQ: 11
Operating System: Linux-x86
NVIDIA Driver Version: 1.0-7184

Below is a link to a pastebin of my xorg.conf
[http://www.copypot.com/1056](http://www.copypot.com/1056)

Sorry to bother you guys. I have searched, and I hope that my question has not already been answered somewhere.

---

