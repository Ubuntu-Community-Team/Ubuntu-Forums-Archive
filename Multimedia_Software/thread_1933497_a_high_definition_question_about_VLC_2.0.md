---
title: "a high definition question about VLC 2.0"
date: 2012-02-29
forum: Multimedia Software
---

### Post by shantiq on 2012-02-29
ok so just updated to 2.0 using [**this route**]("http://www.techdrivein.com/2012/02/vlc-20-twoflower-released-install-in.html") for 11.10


and first thing i did was to test a 1920x1080 vid to see if it now can handle that   but noooooooo   still stutters    [SMplayer never has a problem with those]



which brings me to my question

2.0 is meant to experimentally handle Bluray and looking i see external drives can cost as little as 30 dollars/pounds/euros    so i was thinking of maybe trying that


but since VLC 2.0 seems to still be in pain with 1080 maybe it is still too early for Bluray


now any of you already there and if so how is it going    ?   any tips?


**PS**  maybe my 1080p problem with VLC has to do with my video output settings   what would you guys suggest as optimum  ?


Thank you in advance for all useful info

---

### Post by Yellow Pasque on 2012-02-29
> maybe my 1080p problem with VLC has to do with my video output settings what would you guys suggest as optimum ?

It depends on your GPU and video driver.

---

### Post by shantiq on 2012-02-29
hi there Temujin

not sure you saw the bit where i mention that it is perfect with SMplayer
only Vlc does not handle  it


my hardware side is up to par i think here [ i could be mistaken]

[ATTACH]213504[/ATTACH]

---

### Post by Yellow Pasque on 2012-02-29
VLC does not support vdpau directly (you have to use va-api wrapper) whereas mplayer does. That's why I asked about your GPU/driver..

---

### Post by shantiq on 2012-03-01
ok so can one add va-api wrapper easily or is it not possible?

---

### Post by shantiq on 2012-03-01
=======

---

### Post by Yellow Pasque on 2012-03-01
Assuming you're actually using an nvidia card with binary driver (you never said):
```
sudo apt-get install vdpau-va-driver vainfo
vainfo
```
Make sure vainfo outputs something reasonable. I forget if you have to configure it to use vdpau.

---

### Post by shantiq on 2012-03-01
if this what you mean printing it out?

> vainfo
libva: libva version 0.32.0
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
libva: va_getDriverName() returns 0
libva: Trying to open /usr/lib/dri/nvidia_drv_video.so
libva: va_openDriver() returns 0
vainfo: VA API version: 0.32
vainfo: Driver version: Splitted-Desktop Systems VDPAU backend for VA-API - 0.7.3
vainfo: Supported profile and entrypoints
      VAProfileMPEG2Simple            :	VAEntrypointVLD
      VAProfileMPEG2Main              :	VAEntrypointVLD
      VAProfileMPEG4Simple            :	VAEntrypointVLD
      VAProfileMPEG4AdvancedSimple    :	VAEntrypointVLD
      VAProfileH264Main               :	VAEntrypointVLD
      VAProfileH264High               :	VAEntrypointVLD
      VAProfileVC1Simple              :	VAEntrypointVLD
      VAProfileVC1Main                :	VAEntrypointVLD
      VAProfileVC1Advanced            :	VAEntrypointVLD


---

### Post by Yellow Pasque on 2012-03-01
Yes, that looks correct. Now, turn on video decode accelration in VLC (Tools -> Preferences -> Input & Codecs -> check "Use GPU Accelerated Decoding").

---

### Post by shantiq on 2012-03-02
thank you maybe a little bit less checking   but still not working right stops and starts   no flow

---

### Post by andrew.46 on 2012-03-10
In a completely subjective and non-scientific comparison I have found that SMPlayer/MPlayer + vdpau gives better playback than vlc + vaapi. I would be interested to hear what others think....
[B]
Edit:[/B] BTW shantiq if you want to confirm that your copy of vlc is using hardware acceleration try something like the following:

```

andrew@skamandros~/media/YouTube$ **[COLOR="Red"]cvlc --ffmpeg-hw Cold_Chisel_Bow_River.mp4[/COLOR]** 
VLC media player 2.0.0 Twoflower (revision 2.0.0-0-g421a4fc)
[0x132c048] dummy interface: using the dummy interface module...
libva: libva version 0.32.0-sds2
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
libva: va_getDriverName() returns 0
libva: Trying to open /usr/lib64/va/drivers/nvidia_drv_video.so
libva: va_openDriver() returns 0
**[COLOR="Red"][0x714478] avcodec decoder: Using VA API version 0.32 for hardware decoding.[/COLOR]**


```

---

### Post by shantiq on 2012-03-11
thank you for tip Andrew and it looks good i think

> cvlc --ffmpeg-hw Sarah_Silverman.mkv
VLC media player 2.0.1 Twoflower (revision 2.0.0+git20120229+r120)
[0xc33098] dummy interface: using the dummy interface module...
libva: libva version 0.32.0
Xlib:  extension "XFree86-DRI" missing on display ":0".
libva: va_getDriverName() returns 0
libva: Trying to open /usr/lib/dri/nvidia_drv_video.so
libva: va_openDriver() returns 0
[0xba2968] [COLOR="DarkRed"]**avcodec decoder: Using VA API version 0.32 for hardware decoding**[/COLOR].


But for 1080p  still SMplayer the only beast here on my setup:o

---

### Post by andrew.46 on 2012-03-13
Mind you, I picked up a decent high definition clip:

```

wget http://downloads.dvdloc8.com/trailers/divxdigest/star_wars_blu-ray-trailer.zip

```

and watched it a few times on vlc and SMPlayer and I have to confess I am no longer quite so sure.....

---

### Post by krayzie906 on 2012-03-13
Have you tried tinkering with video output settings? I have Nvidia card, and I personally use **OpenGL** output, but **DirectX **works well too.

[IMG]http://i.imgur.com/LMyrZ.jpg[/IMG]

(found image on web, not on my computer now)

---

### Post by shantiq on 2012-03-13
thanx guys but still no dice these are my choices here



[ATTACH]214250[/ATTACH]

---

### Post by papibe on 2012-03-13
> **shantiq said:**
> ...stops and starts   no flow
Is the file on the network, or is it local?

Could you confirm that for that particular file SMplayer has no problem, but VLC do?

Regards.

---

### Post by shantiq on 2012-03-14
> **papibe said:**
> Is the file on the network, or is it local?

Could you confirm that for that particular file SMplayer has no problem, but VLC do?

Regards.



well quite simply all 1920x1080p files play on SMplayer faultlessly and NONE on vlc     on vlc they check and stutter


i thought 2.0 would have cured that but not

and clearly not a hardware issue as SMplayer is happy




:KS

---

