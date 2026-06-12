---
title: "Driver problems for ATI RV380 [Radeon X600]"
date: 2008-05-22
forum: Multimedia Software
---

### Post by yee379 on 2008-05-22
Hi,

I am using a Hardy installation for basically use of XBMC (uses opengl).

as the title says, i am using a Radeon X600. This is a summary of my problems:

- i get very nice 3D using the radeon driver. However, when i play movies using xbmc, every movie is in green :( everything else seems fine tho (their forum's suggest using a different driver).
- using the 'ati' driver doesn't appear to have any 3d acceleration
- using the fglrx driver i also do not appear to get any 3d acceleration

can anyone concur these findings? offer any suggestions?

thanks!

Yee.

---

### Post by Ren Höek on 2008-05-22
> **yee379 said:**
> Hi,

I am using a Hardy installation for basically use of XBMC (uses opengl).

as the title says, i am using a Radeon X600. This is a summary of my problems:

- i get very nice 3D using the radeon driver. However, when i play movies using xbmc, every movie is in green :( everything else seems fine tho (their forum's suggest using a different driver).
- using the 'ati' driver doesn't appear to have any 3d acceleration
- using the fglrx driver i also do not appear to get any 3d acceleration

can anyone concur these findings? offer any suggestions?

thanks!

Yee.

'ati' is not a real driver, it just helps to take the right open source driver...

With fglrx, it can really get tricky to get it running.
How have you installed the driver?
This is a really good guide:
[http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide)

If you have installed the fglrx driver correctly and don't get direct rendering after reboot, can you please post the results of
```

$ cat /var/log/Xorg.0.log | grep "(WW)\|(FF)"

```
and
```

$ LIBGL_DEBUG=verbose fglrxinfo

```
?

---

### Post by yee379 on 2008-05-24
i think the driver works! :) i used the envy program install previously, but i could never get the ati driver to appear (it was always mesa regardless of what i did)

i changed my kernel from -server to -generic and followed your link; with fglrx i now get:

display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON X600 Series
OpenGL version string: 2.1.7412 Release

yippee!

however, with xbmc, i still get a green screen when i play video :( i'll ask on their forum... thanks very much! ;)

---

