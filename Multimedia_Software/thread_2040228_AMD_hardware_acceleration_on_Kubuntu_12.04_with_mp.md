---
title: "AMD hardware acceleration on Kubuntu 12.04 with mplayer"
date: 2012-08-10
forum: Multimedia Software
---

### Post by smeerlap on 2012-08-10
hi, this is my first post and I thought I would share this information because it has been quite hard for me to find.

This is how I was able to use mplayer with hardware acceleration on a AMD HTPC board. I have a C-60 Ontario (1Ghz dual core with Radeon 6290), this might also work on E-350 Zacate (1.6Ghz dual core with Radeon 6310) (please confirm).

Although the CPU is quite weak (1Ghz)... I am able to play huge x264 (1080p) movies: smoothly and fluently on a board that cost only 70 euros.

Hardware:
[Asus C60M1-i]("http://www.asus.com/Motherboards/AMD_CPU_on_Board/C60M1I/")

[LIST]
[*]make sure you have the proprietary drivers.
I do not know if this is mandatory but I did this anyway.
See [https://help.ubuntu.com/community/BinaryDriverHowto/ATI]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI")...
In Kubuntu 12.04, you will find it in the KDE menu **Applications > System > Additional Drivers**
[*]You should be able to install all these without any extra PPA repository.
```
sudo apt-get install xvba-va-driver libva-glx1 libva-egl1 vainfo
```
[*]vainfo should now give you something that looks like:
```
me@doos:~$ sudo vainfo
libva: VA-API version 0.32.0
Xlib:  extension "XFree86-DRI" missing on display ":0".
libva: va_getDriverName() returns 0
libva: Trying to open /usr/lib/x86_64-linux-gnu/dri/fglrx_drv_video.so
libva: va_openDriver() returns 0
vainfo: VA-API version: 0.32 (libva 1.0.15)
vainfo: Driver version: Splitted-Desktop Systems XvBA backend for VA-API - 0.7.8
vainfo: Supported profile and entrypoints
      VAProfileH264High               : VAEntrypointVLD
      VAProfileVC1Advanced            : VAEntrypointVLD
```
[*]The stock mplayer does not support libva or vaapi.
You won't find those when you do:
```
me@doos:~$ mplayer -vo help
```
[*]There is an mplayer with vaapi enabled.
I found it here: [https://launchpad.net/~sander-vangrieken/+archive/vaapi]("https://launchpad.net/~sander-vangrieken/+archive/vaapi")
To install it:
```
sudo add-apt-repository ppa:sander-vangrieken/vaapi
sudo apt-get update
sudo apt-get install mplayer-vaapi
```
[*]now get a bag of popcorn and some Belgian beer
```
me@doos:~$ mplayer -vo vaapi big_buck_bunny_1080p_h264.mov
```
[/LIST]

---

### Post by QIII on 2012-08-10
Ah!  Big Buck Bunny!  Mrs. QIII scolds me when I let the grands watch that.  Says he's mean to the squirrel.

---

### Post by Linuxisfast on 2012-08-21
vlc does gpu acceleration fine with amd as well, need to do the above, install vlc and enable gpu acceleration under inputs and codecs.

---

### Post by oebantoe on 2012-08-29
Cool PC name :p

---

### Post by repelsteel on 2013-01-30
> **smeerlap said:**
> 

This is how I was able to use mplayer with hardware acceleration on a AMD HTPC board. I have a C-60 Ontario (1Ghz dual core with Radeon 6290), this might also work on E-350 Zacate (1.6Ghz dual core with Radeon 6310) (please confirm).
```
sudo apt-get install xvba-va-driver libva-glx1 libva-egl1 vainfo
```

Thanks buddy, i needed this. I use asus eee 1015BX-whi026s with C-60  and hdmi out.  Now finally VLC gpu acceleration works in Mint 13!

---

### Post by Yellow Pasque on 2013-01-30
XBMC is another alternative if you're using fglrx/Catalyst driver: [http://wiki.cchtml.com/index.php/Ubuntu_Quantal_Installation_Guide#Using_XBMC_player_.28XvBA.29](http://wiki.cchtml.com/index.php/Ubuntu_Quantal_Installation_Guide#Using_XBMC_player_.28XvBA.29)

---

### Post by smeerlap on 2013-01-30
For making an XBMC box, see
[http://youresuchageek.blogspot.fr/2012/06/xbmc-install-and-config-howto-for-linux.html]("http://youresuchageek.blogspot.fr/2012/06/xbmc-install-and-config-howto-for-linux.html")

---

