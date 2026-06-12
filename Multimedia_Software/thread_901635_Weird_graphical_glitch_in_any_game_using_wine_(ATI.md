---
title: "Weird graphical glitch in any game using wine (ATI)"
date: 2008-08-26
forum: Multimedia Software
---

### Post by xocekim on 2008-08-26
Hi all,

Im trying to move over to Linux from Windows for good but I would really like to get some games working on it, especially World of Warcraft.

I have and ATI Radeon X1950XTX and this is what I see when I launch WoW, I have also tried this with Age of Conan with same results.

[IMG]http://fishy.org.uk/fullscreen.jpg[/IMG]

Had to take the picture with a camera as when I print screen for a screenshot and paste, it looks like...
[IMG]http://fishy.org.uk/screenshot.jpg[/IMG]
Which is what it *should* look like.

I have tried several Linux distrobutions, Ubuntu (ofcourse), Debian, Fedora and OpenSuSE. Trying both the distro provided fglrx drivers and the latest ATI ones. And using Wine 1.0+, always with the same problem

glxinfo always says direct rendering: yes and fglrxinfo reports perfectly too.

```
#glxinfo | grep direct
direct rendering: Yes
#fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: Radeon X1950 Series
OpenGL version string: 2.1.7769 Release
```

Xorg.0.log does not have any errors, but I do keep getting alot of warnings saying..
```
(WW) AIGLX: 3D driver claims to not support visual 0x72
```

All the games work fine within Windows. I have also tried turning all visual effects off (Compiz etc) and changing the game config files to switch between OpenGL and Direct3D

Could anyone shed some light on what the problem may be?

Thanks

---

### Post by didli on 2008-08-31
Exactly the same problem here with an ATI X800 GTO Sapphire. All games i tried to run using wine is affected, both with the distro provided fglrx drivers or the latest ATI drivers [Catalyst 8.8 ].
Any chance to get a clue about this ?

---

### Post by Elephantman5 on 2008-08-31
That's why I run Nvidia...

---

