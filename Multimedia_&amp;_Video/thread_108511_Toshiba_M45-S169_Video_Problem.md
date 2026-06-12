---
title: "Toshiba M45-S169 Video Problem"
date: 2005-12-26
forum: Multimedia &amp; Video
---

### Post by rickyjones on 2005-12-26
Hi everyone! I just got a new laptop, and being a new user of Ubuntu I figured it would be a good idea to install Ubuntu. The install went great, and everything seems to be working the way it should be, however I have a small issue with my video card.

Upon installation, the default drivers only support 1024x768, but my display is optimized for 1280x800. I tried following the how-to located at [https://wiki.ubuntu.com/BinaryDriverHowto/ATI]("https://wiki.ubuntu.com/BinaryDriverHowto/ATI"). Everything seemed to be going well until I got to the following command:
```
sudo apt-get install fakeroot gcc-3.4 module-assistant build-essential debhelper
```
Apparently "module-assistant" cannot be located, neither can gcc-3.4. I decided that it should be OK to just go forward, so I did the next few steps. However, I was unable to do the following command (because I couldn't install the module-assistant package...)
```
then do: sudo module-assistant build,install fglrx-kernel
```
I already had "fglrx" as the driver in my xorg.conf file, so I went ahead and rebooted. Now my resolution is at 1280x800, but I think I lost 3D functionality. When I run fgl_glxgears, it errors out with thef ollowing:
```

Using GLX_SGIX_pbuffer
X Error of failed request: BadMatch (invalid parameter attributes)
    Major opcode of failed request: 143 (GLX)
    Minor opcode of failed request: 5 (X_GLXMakeCurrent)
    Serial number of failed request: 32
    Current serial number in output stream: 32

```
When I run fglrxinfo I get the following output:
```

display: :0.0 screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.2.1)

```

As far as I can tell, everything is correct in the xorg.conf file. Before I followed the howto, I had a lower resolution, but the fgl_glxgears ran without issue.

Any help would be greatly appreciated (and sorry for the long post!)

Thanks!
-Richard

---

