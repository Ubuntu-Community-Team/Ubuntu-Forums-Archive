---
title: "dexconf not behaving as documented."
date: 2011-02-23
forum: Multimedia Software
---

### Post by AKADAP on 2011-02-23
For some reason, my system does not have a xorg.conf file, so I tried to get one created with dexconf

When I run it, I get no error messages, but it does not create the xorg.conf file like the documentation says it should, and it returns an error code of 10. The documentation claims that only 0 and 1 are possible return codes.

This is what I get:
```
$ sudo dexconf
$ echo $?
10

```

Is a xorg.conf still being used?
Is the documentation for dexconf out of date?

This all started from this little bit of infuriating instructions:

> LIBGL_DEBUG=verbose glxinfo

Make sure your OpenGL renderer string does not say "software rasterizer" because that would mean you have no 3D hardware acceleration.

from here: [https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

It tells me to make sure that it does not say "software rasterizer", but gives no hint of what I should do if it does.

---

### Post by AKADAP on 2011-03-01
I have reported this as a bug:

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/726983](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/726983)

Lets see if I get an answer that way.

---

