---
title: "fglrx loads sometimes, sometimes no"
date: 2007-08-02
forum: Multimedia &amp; Video
---

### Post by Saija on 2007-08-02
Hi

I'm having problems with the fglrx driver, i just used the instructions provided by the [ubuntu wiki]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI#head-99489608eb537a1a0346cdd3ad34209d7887714a") and the installations was just fine, but sometimes when i logon and try to load Quake 3 the game doesn't load, then i go to the konsole(yes, i'm running KDE) the ouput of fgl_glxgears is:

> Using GLX_SGIX_pbuffer
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  142 (GLX)
  Minor opcode of failed request:  5 (X_GLXMakeCurrent)
  Serial number of failed request:  33
  Current serial number in output stream:  33


then i check the fglrxinfo and this is the output:

> display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (1.5 Mesa 6.5.2)


to correct this i just close the kde session and log again and then magically the fgl_glxgears show the colored gears spinning and rotating.

this behavior also happens when i logon in fluxbox(i've kde & fluxbox installed here)

so, my question is: somebody has the same problem? somebody know how solve it?

Thanks !! :)

PS1: i've a Ati Radeon X550 PCIE, the drivers i've installed is the ati-driver-installer-8.38.6-x86.x86_64.run, running on Kubuntu Feisty Fawn with the  2.6.20-16-generic kernel

PS2: Sorry if this post is in some other place in the site just tell me and i'll make the corrections, thanks.

---

### Post by Saija on 2007-08-03
Hi

Sorry for autorespond me but somebody knows how to fix this? :confused:

Thanks

---

