---
title: "ATI RADEON X1300 64mb installation problem"
date: 2007-02-27
forum: Multimedia &amp; Video
---

### Post by genghiskhano on 2007-02-27
Hello everyone,
Last week I installed my Radeon X1300 using the following guide:

[http://m.domaindlx.com/LinuxHelp/ati/ati.htm](http://m.domaindlx.com/LinuxHelp/ati/ati.htm)

I got a bunch of errors but at the end when I ran $fglrxinfo I got the right out put for my card and when I ran $fgl_glxgear I got the gears and everything seem to be installed right, the only problem is that when I click on the ATI icon it gave me an error about the path not being correct.

After reinstalling Ubuntu 6.10 on my computer(did it cos I removed gnome and I had a lot of errors) I decided to reinstall the drivers following this guide:

[http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide)
everything got installed and I didn't have any installation errors but when I run $fglrxinfo I get this output:

Xlib:  extension "XFree86-DRI" missing on display ":0.0".
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.5.1)

and when I run $fgl_glxgears a screen flashes for like a nano second and then I get the following output:

Xlib:  extension "XFree86-DRI" missing on display ":0.0".
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  142 (GLX)
  Minor opcode of failed request:  5 (X_GLXMakeCurrent)
  Serial number of failed request:  30
  Current serial number in output stream:  30
ATI control opens file but it refers to the mesa driver.

thanks for your help

---

