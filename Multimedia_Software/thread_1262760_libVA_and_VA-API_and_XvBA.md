---
title: "libVA and VA-API and XvBA"
date: 2009-09-10
forum: Multimedia Software
---

### Post by hanbin973 on 2009-09-10
From a month ago, libva started to support XvBA and VDPAU. That means, vdpau and xvba is in a work to make it a backend of va-api.

So I compiled mplayer-vaapi really succesfully with out error. but vainfo keep makes problem.

it says

```
libva: libva version 0.30.4-sds4
libva: va_getDriverName() returns 0
libva: Trying to open /usr/lib/dri/fglrx_drv_video.so
libva: Trying to open /usr/lib32/dri/fglrx_drv_video.so
libva: va_openDriver() returns -1
[vo_vaapi] vaInitialize(): unknown libva error

```

I don't have such library.... I know how to do this in intel, but I'm a hd3200 + hd3450 user.
one of them supports uvd2. 

Anyone help me?

---

### Post by GraceDivine on 2009-09-20
I have the same problem on both a Mobility HD 2600 and HD3870 on my desktop.
Xvba is vaporware so I'm not putting the blame into that, but perhaps the latest fglrx proprietary drivers (9.9) broke vaapi support?

---

### Post by hanbin973 on 2009-09-21
I found the reason but now way to solve;;

fglrx_drv_video.so is not in the Catalyst driver.

Its in the xvba-video pacakage that is restricted. 

[http://www.splitted-desktop.com/~gbeauchesne/xvba-video/](http://www.splitted-desktop.com/~gbeauchesne/xvba-video/)


Vdapu Backend also needs a package called vdpau-video. 
But one thing is.... vdpau-video is opened and xvba-vidoe is not;;
hmmm.... 

I have no idea why the developer is not opening the thing.
.....

Also if we see this [http://gwenole.beauchesne.info/en/blog/2009/06/22/video_decode_acceleration_benchmarks](http://gwenole.beauchesne.info/en/blog/2009/06/22/video_decode_acceleration_benchmarks) , we can now xvba-video is working and avaliable ( I don't know about the bug or something ).

hmmm?

---

### Post by t.alex on 2009-11-03
> **hanbin973 said:**
> 
I have no idea why the developer is not opening the thing.


well it's open now!

[http://www.phoronix.com/scan.php?page=article&item=amd_xvba_vaapi&num=1](http://www.phoronix.com/scan.php?page=article&item=amd_xvba_vaapi&num=1)

:popcorn:

---

### Post by epi 1:10,000 on 2009-11-03
Bumpady bump bump:popcorn:

---

### Post by damvcoool on 2010-03-03
Does anyone know if packages that come from Karmic or Lucid may have support for this libraries without the need to recompile, something like just enabling a setting after these libraries have been installed?

Maybe some GStreamer love?

---

### Post by Yellow Pasque on 2010-03-03
From what I understand, the colors are messed up when using XvBA in the recent Catalyst drivers.

---

### Post by Lampi on 2010-03-06
> **Temüjin said:**
> From what I understand, the colors are messed up when using XvBA in the recent Catalyst drivers.
colors are fine now with latest software builds of fglrx/xvba + vaapi.

@damvcoool: I don't think it will be ready for lucid - it's in debian unstable now - lots of ongoing work on that project. just build it yourself with the howto on splitted-desktop or use the installer script on [the kanotix fileserver]("http://kanotix.com/files/fix/mplayer-vaapi-latest.txt")

---

### Post by markbuntu on 2010-03-06
There is an extensive how-to around here somewhere....

---

