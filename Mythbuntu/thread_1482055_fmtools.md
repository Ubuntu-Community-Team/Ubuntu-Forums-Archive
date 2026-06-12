---
title: "fmtools"
date: 2010-05-13
forum: Mythbuntu
---

### Post by goffa72 on 2010-05-13
Hi all

I'm trying to get fmtools to work in mythbuntu 10.04 and all I get is static, fmtools works with 8.10 and other radio programs work.

Have read about an issue with V4L2 compatibility with fmtools 1.0.4 

I have tried the .deb package from here [http://packages.debian.org/sid/fmtools](http://packages.debian.org/sid/fmtools) for v 2.0.3 It has been made fmtools compatible with V4L2 but I still only get static (tunes for about 1/2 a second only).

I want to be able to use this with mythtv ([http://www.mythtv.org/wiki/fm_radio](http://www.mythtv.org/wiki/fm_radio)) so another radio program is not suitable unless it can be controlled from the command line. This worked fine in 8.10 

Any ideas on getting fmtools to work or an alternative.

Thanks

---

### Post by ian dobson on 2010-05-13
Hi,

I don't know what tuner you have, but I had good results with the ivtv-radio program from the ivtv package.Using:-

```
ivtv-radio  -f $Frequency -d $IVTVDevice -c \"sox -t raw -r 48000 -w -s -c2 %s -t ogg - |nc  $ClientIP $RemotePort\
```

I can beam the radio over my network.

Regards
Ian Dobson

---

### Post by goffa72 on 2010-05-14
Thanks for your suggestion Ian.

I have a winfast 1800H card with the Xceive xc3028 tuner, I don't think this works with ivtv. 

Anyway I have made some progress, I can get fmtools to work if the xfce4-radio-plugin is installed but there is a catch, the tuner needs to be first initiated using the plugin before it can be controlled and tuned using fmtools. So if I want to use fmtools first I must start the radio by some other means, which I would prefer not to do.

---

