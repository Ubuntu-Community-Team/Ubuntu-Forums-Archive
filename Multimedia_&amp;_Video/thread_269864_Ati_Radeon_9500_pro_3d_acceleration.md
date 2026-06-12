---
title: "Ati Radeon 9500 pro 3d acceleration"
date: 2006-10-02
forum: Multimedia &amp; Video
---

### Post by DwalerXIII on 2006-10-02
hello,

I have a graphics card like mentiond in the subject.
All is working but a lot slower then in WinXP.

Whe I type the fglrxinfo command I get the following result.

fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.4.1)

What I can make of this is that there is an indirect 3d rendering or something like that.
Is there a way to improve the 3d rendering results?

Blender is working fine but Celestia (a space simulator) is extremely slow.

---

### Post by DwalerXIII on 2006-10-03
I solved the problem. Great thanks to EasyUbuntu!!!
Now everyting runs very smooth!
My fglrxinfo command gives the following result:

fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9500 Generic
OpenGL version string: 2.0.5814 (8.25.18)

---

