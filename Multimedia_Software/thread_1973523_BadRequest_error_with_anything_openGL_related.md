---
title: "BadRequest error with anything openGL related"
date: 2012-05-04
forum: Multimedia Software
---

### Post by matyoung89 on 2012-05-04
Hi all,
I am running ubuntu 11.10 32 bit off of my HP Envy 15 (AMD Radeon(TM) HD 7690M GDDR5 graphics).
I have apparently activated the proprietary drivers successfully, however if I run glxinfo, fglrxinfo or fgl_glxgears I get the following error message

X Error of failed request: BadRequest (invalid request code or no such operation)
Major opcode of failed request: 155 (GLX)
Minor opcode of failed request: 19 (X_GLXQueryServerString)
Serial number of failed request: 12
Current serial number in output stream: 12

Even though the Addition Drivers program reports that fglrx is activated and currently in use, I suspect there is something wrong with the driver installation as /usr/bin/aticonfig returns

no supported adapters detected

and my xorg.conf contains no device section and no reference to the driver. just:

Section "Screen"
    Identifier    "Default Screen"
    DefaultDepth    24
EndSection

Section "Module"
    Load    "glx"
EndSection

I literally have no idea how to proceed, any help would be greatly appreciated.
Thanks,
Mat.

---

