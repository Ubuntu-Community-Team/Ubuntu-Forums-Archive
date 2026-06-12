---
title: "Enabling OpenCL in 14.04 (worked in 13.10)"
date: 2014-04-22
forum: Multimedia Software
---

### Post by The Bright Side on 2014-04-22
Hello Ubuntu fans,

I'm hoping you can help me with this issue. Since I installed Ubuntu Gnome 14.04 and the latest NVidia driver 331, the photo workflow software [Darktable]("http://www.darktable.org") no longer runs with OpenCL support. I filed a bug [here]("http://www.darktable.org/redmine/issues/9913#change-24913"), and the developer told me this:

> As darktable's log output tells you the library libOpenCL could not be found. darktable relies on your [COLOR="#FF0000"]system's dynamic linker[/COLOR] that it knows the place of that library (libOpenCL.so). Let's assume this file is present on your system (check with '[COLOR="#FF0000"]locate libOpenCL[/COLOR]') then it might sit in a place where [COLOR="#FF0000"]ld.so[/COLOR] does not look for it. Consult '[COLOR="#FF0000"]man ldconfig[/COLOR]' to learn how to fix that.

I highlighted the parts I'd need help with:

[LIST]
[*]How can I find and modify the "dynamic linker"?
[*]Is "locate libOpenCL" a command that I can type into the terminal just like this? If it is, is it case sensitive?
[*]If not, how do I perform a system-wide search for libopencl.so?
[*]Is "ld.so" this dynamic linker he speaks of? If so, can I simply edit it with gedit?
[/LIST]

I'm in the office right now and don't have access to my home PC, but I hope in the meantime, you guys can give me some pointers... This seems to go a little deeper under the hood of Ubuntu than I'm used to going, and I'd love to learn the technical backgrounds. The thing is, OpenCL worked just fine in the past few Ubuntu releases, it's only this one where it's gone.

Yesterday, I tried looking for this libopencl.so file on my PC, but when I used the Nautilus search (even when running Nautilus in super user mode), it wouldn't search outside the "Home" folder. (either that, or it couldn't find any "libopencl" references outside my "Home" folder).

If those OpenCL libraries are missing from my PC, do you know how I can install them? I thought they'd come with the graphics driver.

---

