---
title: "sudo gives 3d acceleration, no 3d accel without it!?"
date: 2006-02-28
forum: Multimedia &amp; Video
---

### Post by lox on 2006-02-28
lox@CP256946-A:~$ fglrxinfo
libGL error: failed to open DRM: Operation not permitted
libGL error: reverting to (slow) indirect rendering
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.2.1)

lox@CP256946-A:~$ sudo fglrxinfo
Password:
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON X800 GTO Generic
OpenGL version string: 2.0.5642 (8.22.5)

is there a way to make it so all users have 3d acceleration?
thanks in advance!

---

### Post by Corvillus on 2006-02-28
I think you have to put users in the "video" group to get 3D acceleration privileges. You can do this by doing.
```
sudo gpasswd -a username video
```
for each user you wish to have access to video acceleration.

---

### Post by lox on 2006-03-01
will try when i get home, thank you

---

### Post by florizs on 2006-03-01
If you run fgrlx-configure it asks you who should be able to acces the video drivers. I believe it is an option in the xorg.conf file.
I had the same issue once and it appeared i had run fgrlx-configure badly.

---

