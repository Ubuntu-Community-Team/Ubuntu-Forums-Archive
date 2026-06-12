---
title: "Poor DVD playback"
date: 2007-02-26
forum: Multimedia &amp; Video
---

### Post by Praill on 2007-02-26
Hello Everyone,

I'm having an issue with DVD playback quality. It is incredibly poor regardless of player (xine, vlc, mplayer, and totem are all the ones I've tried). I can play all mpeg, avi, wmv, etc formats perfectly fine, and it will play DVDs but the quality is horrendous. Also, the drive rips at crazy speeds to produce even the poorest quality images. Sound is fine.

I'm using a Dell Inspiron 6400 with an ATI x1400. The driver is installed properly and works with several games including World of Warcraft through wine.
Here is my fglrxinfo output:

```
$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Mobility Radeon X1400
OpenGL version string: 2.0.6334 (8.34.8)
```

I have tried  using vlc and mplayer from the repositories as well as compiling from source, and the problem remains either way.
A google of this issue returns few results except one or two pages that suggest this is an ati driver related problem.

Has anyone experienced a similar issue and found a resolution? Perhaps an xorg setting? Any information is greatly appreciated.

---

### Post by Spr0k3t on 2007-02-26
I'm sorry, but unless you have proof of purchase for being able to play DVDs on your lin....

Just kidding.  Check into gxine to help get the output smoother.  I don't have an ATI, but it's smooth as glass on my nVidia and integrated Intel 915 chipsets, so you should fair well with it.

Oh man, just noticed you tried xine... hmm... I'm off beat for this one.  Any other takers?

---

### Post by Brynster on 2007-02-26
have you installed libdvdcss codec?

I know this is to play back encrypted dvds but i di notice an improvement on playback quality on non encrypted dvds after i had installed this. PLEASE ENSURE THAT IT IS LEGAL IN YOU COUNTRY TO HAVE THIS INSTALLED AS SOME NATIONS ARE A LITTLE BACKWARDS IN PLAY BACK OF DVDS ON PC'S *cough *cough *USA * cough.

---

### Post by Praill on 2007-02-26
Haha, thanks for the disclaimer.
I wont say what country I'm in, but I do have libdvdcss2.

---

### Post by ubu-for on 2007-02-26
> **Praill said:**
> Hello Everyone,

I'm having an issue with DVD playback quality. It is incredibly poor regardless of player (xine, vlc, mplayer, and totem are all the ones I've tried). I can play all mpeg, avi, wmv, etc formats perfectly fine, and it will play DVDs but the quality is horrendous. Also, the drive rips at crazy speeds to produce even the poorest quality images. Sound is fine.

I'm using a Dell Inspiron 6400 with an ATI x1400. The driver is installed properly and works with several games including World of Warcraft through wine.
Here is my fglrxinfo output:

```
$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Mobility Radeon X1400
OpenGL version string: 2.0.6334 (8.34.8)
```

I have tried  using vlc and mplayer from the repositories as well as compiling from source, and the problem remains either way.
A google of this issue returns few results except one or two pages that suggest this is an ati driver related problem.

Has anyone experienced a similar issue and found a resolution? Perhaps an xorg setting? Any information is greatly appreciated.

DMA on or off?

```
sudo hdparm /dev/dvd
```

[ HOWTO: Speed up CD/DVD-ROM](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_speed_up_CD.2FDVD-ROM)

---

### Post by Praill on 2007-02-26
Thanks for all your help, but unfortunately the problem is I'm an idiot.
The DVD in question is simply bad quality to begin with. Its a copy of a movie made with a DVD burner and, for some reason, is just bad quality. I have several other DVDs that copied fine, but this one didnt.

Anyways, no need to tell me I'm dumb, I already know :) 

Thanks again.

---

### Post by ubu-for on 2007-02-26
> **Praill said:**
> The DVD in question is simply bad quality to begin with. Its a copy of a movie made with a DVD burner and, for some reason, is just bad quality. I have several other DVDs that copied fine, but this one didnt.

No problem! ;)

> **Praill said:**
> Thanks again.

You're welcome!

---

### Post by Praill on 2007-02-27
I hate to bring this back up, but your suggestion has got me exploring again.
I've always noticed that with any DVD if i play it in a window much smaller than half the screen, the frames become garbled and choppy.
I also noticed this:

```
$ hdparm /dev/dvd

/dev/scd0:
 readonly     =  0 (off)
 readahead    = 256 (on)
 HDIO_GETGEO failed: Inappropriate ioctl for device
```

and this:

```
hdparm -d 1 /dev/dvd

/dev/dvd:
 setting using_dma to 1 (on)
 HDIO_SET_DMA failed: Function not implemented
```

A google of this problem led me to a couple mailing lists that suggested recompiling the kernel. They included steps, that i didnt understand, and Im sure omitted some steps that I wouldnt understand. :)

Ive never recompiled the kernel before so I wouldnt know how. I consider myself an intermediate linux user so if anyone could provide some advice regarding setting up dma on my drive i would appreciate it.

---

### Post by ubu-for on 2007-02-27
> **Praill said:**
> A google of this problem led me to a couple mailing lists that suggested recompiling the kernel. They included steps, that i didnt understand, and Im sure omitted some steps that I wouldnt understand.

Don't recompile the kernel!

> **ubu-for said:**
> [ HOWTO: Speed up CD/DVD-ROM](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_speed_up_CD.2FDVD-ROM)

Just follow this guide.

---

### Post by Praill on 2007-02-27
Thanks again for helping me ubu-for.

I followed the instructions on that page re: the appending of hdparm.conf and the problem seems to remain.
Perhaps I'm being too picky though. Like I said, the quality hit only occurs when i shrink the media to a size smaller than its native resolution. When I view the DVD in fullscreen its at a bare-able quality.
However I'm still receiving these outputs from hdparm:

```
tom@tom-i6400:~$ sudo hdparm /dev/dvd
/dev/dvd:
 readonly     =  0 (off)
 readahead    = 256 (on)
 HDIO_GETGEO failed: Inappropriate ioctl for device

tom@tom-i6400:~$ sudo hdparm -d1 /dev/dvd
/dev/dvd:
 setting using_dma to 1 (on)
 HDIO_SET_DMA failed: Function not implemented
```

its the same output for cdrom aswell since, I believe, both are just a link to /dev/scd0

I switched over to my windows xp partition and noticed the problem repeated when using the win32 version of vlc. However the problem was corrected in windows' native media player. 
I then googled the problem regarding 'vlc choppy video' and discovered that vlc is notorious for disabling digital memory addressing even in windows. :mad: 

I'm going to let this go for now, but if an occasion arrises where the lack of digital memory addressing is preventing dvd writing then I might post again.

Again, thanks so much for all your help.

---

### Post by ubu-for on 2007-02-27
I'm not sure if DMA is still off or not on your system.

**To turn on DMA temporarily**, try this.

```
sudo hdparm -c1 -d1 /dev/hda
```

Don't use "/dev/hda" but open Nautilus (file manager), go to the root file system, open the "dev" folder, go to the "dvd" file, right click on "dvd" file, choose preferences and use the link destination "/dev/..." instead.

Now you should get something similar to this.

```
~$ hdparm /dev/dvd

/dev/cdrom:
 IO_support   =  1 (32-bit)
 unmaskirq    =  1 (on)
 using_dma    =  1 (on)
 keepsettings =  0 (off)
 readonly     =  0 (off)
 readahead    = 256 (on)
 HDIO_GETGEO failed: Inappropriate ioctl for device
```

**To turn on DMA permanently**, try this.

```
 sudo gedit /etc/hdparm.conf
```

Add to the end.

```
/dev/hda {
       io32_support = 1  
       dma = on
       keep_settings_over_reset = 1
}
```

Use again the link destination "/dev/..." instead of "/dev/hda".

An alternative to VLC and Totem with Gstreamer plugin could be "Ogle" + "Ogle-gui".

---

### Post by ubu-for on 2007-02-27
Have you installed "libdvdread3"?

---

