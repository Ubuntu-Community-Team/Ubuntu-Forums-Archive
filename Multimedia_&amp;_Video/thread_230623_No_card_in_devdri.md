---
title: "No card in /dev/dri"
date: 2006-08-06
forum: Multimedia &amp; Video
---

### Post by Barney2006 on 2006-08-06
Hello guys :)
I'm new to the forum and this is my first post :-D

I've got a problem with my 3D acceleration on a ATI RADEON 9600TX (yep, TX), it's not enabled... so 

fglrxinfo
gives me

display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.4.1)

and 


/var/log/xorg.0.log
gives me

...
(WW) fglrx(0): Specified desktop setup not supported: 8
...
(EE) fglrx(0): Fail to initialize ASIC in kernel.
...
(II) fglrx(0): doing DRIScreenInit
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: Open failed
[drm] failed to load kernel module "fglrx"
(II) fglrx(0): [drm] drmOpen failed
(EE) fglrx(0): DRIScreenInit failed!
...


My /dev/dri folder is empty btw.


Any ideas? On Breezy it worked all well :(


EDIT: I don't want to downgrade to breezy. If you need more information just post me what you want. Thanks.

---

