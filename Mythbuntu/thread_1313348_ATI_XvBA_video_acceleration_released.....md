---
title: "ATI XvBA video acceleration released....?"
date: 2009-11-03
forum: Mythbuntu
---

### Post by epi 1:10,000 on 2009-11-03
[http://www.phoronix.com/scan.php?page=article&item=amd_xvba_vaapi&num=1](http://www.phoronix.com/scan.php?page=article&item=amd_xvba_vaapi&num=1)

Does anyone know where to get the libraries and how to enable VA-API?

---

### Post by Devport on 2009-11-03
Rewritten report of my **failed attempt** of installing xvba-video :

1. Installed libva1_0.31.0-1+sds7 ( dependency of xvba-video )

[http://www.splitted-desktop.com/~gbeauchesne/libva/pkgs/](http://www.splitted-desktop.com/~gbeauchesne/libva/pkgs/)

2. Installed xvba-video_0.5.1-1

[http://www.splitted-desktop.com/~gbeauchesne/xvba-video/](http://www.splitted-desktop.com/~gbeauchesne/xvba-video/)

3. Testing

For apps supporting vaapi see

[http://www.splitted-desktop.com/~gbeauchesne/](http://www.splitted-desktop.com/~gbeauchesne/)

Installed libva-dev

[http://www.splitted-desktop.com/~gbeauchesne/libva/pkgs/](http://www.splitted-desktop.com/~gbeauchesne/libva/pkgs/)

Installed libx11-dev

Downloaded and unpacked hwdecode-demos-0.7.4

[http://www.splitted-desktop.com/~gbeauchesne/hwdecode-demos/](http://www.splitted-desktop.com/~gbeauchesne/hwdecode-demos/)

Removed the dprintf stuff from debug.h / debug.c.

Build hwdemos by running

```
cd [path-to-hwdecode-demos]
autoconf
./configure
make
```

**Build worked fine but running e.g. vaapi_h264 failes with**

```
Display type 'x11'
Hardware accelerator 'vaapi'
libva: libva version 0.31.0-sds3
libva: va_getDriverName() returns 0
libva: Trying to open /usr/lib/va/drivers/fglrx_drv_video.so
libva: va_openDriver() returns 0
[hwdecode_demos] vaPutSurface(): the requested function is not implemented
ERROR: display failed

```

Since everything installed fine I have no idea why it doesnt work.

Update 05.11. - Still not working with updated packages from 04.11.

---

### Post by epi 1:10,000 on 2009-11-03
I'm on Ubuntu 9.04 32 bit  i386  w/ these libs

libamdxvba1    version 2:8.600-0ubuntu2

libstdc++5     version 1:3.3.6-17ubuntu1 


I added Brandon Snider PPA to sources but I can't find the libraries @ step # 4. No libva1_0.31/No xvba-video in synaptic.

---

### Post by Devport on 2009-11-03
> **epi 1:10,000 said:**
> I'm on Ubuntu 9.04 w/ these libs

libamdxvba1    version 2:8.600-0ubuntu2

libstdc++5     version 1:3.3.6-17ubuntu1 


I added Brandon Snider PPA to sources but I can't find the libraries @ step # 4. No libva1_0.31/No xvba-video in synaptic.

I downloaded the package manually - choose "View package details" on the ppa website and download libva1_0.31.0-1+sds4~nvidiavdpauppa1_amd64.deb or the one for your arch. For xvba-video see the next step.

---

### Post by Devport on 2009-11-03
I just found out there are better / more up to date packages of libva at the xvba-video website. I changed the guide now for use of those packages. See step 1.

[http://www.splitted-desktop.com/~gbeauchesne/](http://www.splitted-desktop.com/~gbeauchesne/)

---

### Post by epi 1:10,000 on 2009-11-03
downloaded and extracted mplayer-vaapi-latest.tar.bz2 from

[http://www.splitted-desktop.com/~gbeauchesne/mplayer-vaapi/]("http://www.splitted-desktop.com/%7Egbeauchesne/mplayer-vaapi/")

but I'm not sure how to use it to recompile mplayer version 2:1.0~RC2-0ubuntu19+medibuntu1. Where can I get a more recent mplayer?  I'm reading over the read me file...... Are there any more dev files I need?  What directory should the mplayer-vaapi-20091015 be moved to?

---

### Post by Devport on 2009-11-03
I dont know about mplayer, but before fighting with that beast you could try to build hwdecode-demos which is way easier and it will indicate if the setup works ( in my case it doesnt work so I will have to wait for updated xvba packages :( ).

---

### Post by epi 1:10,000 on 2009-11-03
We may have to wait a couple more days for more support from ATI and Splitted Desktop.

---

### Post by Devport on 2009-11-05
Yesterday some packages have been updated but it still doesn`t work. There is an app called vainfo which gives

```
libva: libva version 0.31.0-sds3
libva: va_getDriverName() returns 0
libva: Trying to open /usr/lib/va/drivers/fglrx_drv_video.so
libva: va_openDriver() returns 0
vainfo: VA API version: 0.31
vainfo: Driver version: Splitted-Desktop Systems XvBA backend for VA API - 0.5.1
vainfo: Supported profile and entrypoints
      VAProfileMPEG2Simple            :	VAEntrypointIDCT
      VAProfileMPEG2Main              :	VAEntrypointIDCT
      VAProfileH264High               :	VAEntrypointVLD
      VAProfileVC1Advanced            :	VAEntrypointVLD

```

To me it seems that it fails to access the driver`s libamdxvba. We would need to know which fglrx driver version the author is using.

Maybe or rather hopefully he is using an unreleased version of fglrx so it may work with the next driver release 9.11.

---

### Post by »John« on 2009-11-08
[This article]("http://www.phoronix.com/scan.php?page=article&item=amd_xvba_vaapi") along with their earlier XvBA coverage suggests it may never work on GPUs without [UVD2]("http://en.wikipedia.org/wiki/Unified_Video_Decoder#UVD_2") ([R600]("http://en.wikipedia.org/wiki/Radeon_R600") and older generations), so anyone using these chips is probably out of luck, including me. For the rest, it should be a simple matter of fglrx version.

---

### Post by neztiti on 2010-05-22
thanks guys 4 the guide - works fine on ati 3450hd on lucid

---

### Post by taz4hvn on 2010-05-23
neztiti, would you mind giving us precise instructions about what you did to get it working ?
giving the guide a try on Lucid gave me nothing but : 
"Error opening/initializing the selected video_out (-vo) device."
thx.

---

### Post by neztiti on 2010-06-05
> **taz4hvn said:**
> neztiti, would you mind giving us precise instructions about what you did to get it working ?
giving the guide a try on Lucid gave me nothing but : 
"Error opening/initializing the selected video_out (-vo) device."
thx.

did u tried new "ati-driver-installer-10-5-x86.x86_64.run" ??

---

### Post by neztiti on 2010-06-05
ok - after new installtion for new ubuntu 10.4 i get 

root@neztiti-desktop:/home/neztiti# vainfo
libva: libva version 0.31.0-sds6
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
libva: va_getDriverName() returns 0
libva: Trying to open /usr/lib/va/drivers/fglrx_drv_video.so
libva: va_openDriver() returns 0
vainfo: VA API version: 0.31
vainfo: Driver version: Splitted-Desktop Systems XvBA backend for VA API - 0.6.11
vainfo: Supported profile and entrypoints
      VAProfileMPEG2Simple            :	VAEntrypointIDCT
      VAProfileMPEG2Main              :	VAEntrypointIDCT
      VAProfileH264High               :	VAEntrypointVLD
      VAProfileVC1Advanced            :	VAEntrypointVLD

---

### Post by Ko$ on 2010-12-20
h264 works just fine with -va xvmc:

mplayer -vo vaapi -va xvmc l.mkv

---

