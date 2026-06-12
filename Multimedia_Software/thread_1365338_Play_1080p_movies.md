---
title: "Play 1080p movies"
date: 2009-12-27
forum: Multimedia Software
---

### Post by dzooky on 2009-12-27
Hi guys
I have laptop HP Pavilion DV6646US with graphic card GeForce 7150M Somewhere on the internet I find that differences between 7000 & 7150 is that 7150 support decoding of HD movies.

On my ubuntu I try many players but it did play smoothly.
I try play movies on windows XP also and there is everything OK.

Can somebody help me
Thanks

---

### Post by ram4nd on 2009-12-27
Have you VLC, Totem or mplayer? I think it's behind processor not GPU. Linux uses 85% of your cpu speed max, you can put it to 100% with [http://blog.ubuntu-tweak.com/](http://blog.ubuntu-tweak.com/)

---

### Post by lovinglinux on 2009-12-27
You cannot really compare Ubuntu Karmic Koala with Windows XP, since the last one is very old and requires less resources. Nevertheless, I believe playing HD videos also depends on processor power. For instance, I had a P4 until a couple of weeks ago and I wasn't able to play 720p movies without lagging and freezing. I have upgraded to a Core 2 Duo and it plays perfectly now. I'm using the same video card, which is a nvidia 7300GT.

---

### Post by dzooky on 2009-12-27
@ram4nd: I tried VLC, mplayer, XBMC, Moovida and always the same. And also I tried Ubuntu tweak. 

@lovinglinux: I have I have turion X2 with 2x1.9GHz. 
I'm really sad why it's workin on win dbut on linux no :(

---

### Post by cascade9 on 2009-12-27
> **dzooky said:**
> Hi guys
I have laptop HP Pavilion DV6646US with graphic card GeForce 7150M Somewhere on the internet I find that differences between 7000 & 7150 is that 7150 support decoding of HD movies.

On my ubuntu I try many players but it did play smoothly.
I try play movies on windows XP also and there is everything OK.

Can somebody help me
Thanks

There is 2 different sorts of 'hardware decoding' for nVidia CPUs. 

nVidia Pure video- supports geforce 7xxx. I'm not sure if that includes the 7000, but I think that the 7000 was another 'M' model in which case it should-
[http://www.nvidia.com/page/purevideo_support.html](http://www.nvidia.com/page/purevideo_support.html)

VDPAU (Video Decode and Presentation API for Unix), which is pretty much 'pure video' for linux/solaris/freeBSD. 7xxx NOT supported-
[http://www.mythtv.org/wiki/VDPAU#Supported_Cards](http://www.mythtv.org/wiki/VDPAU#Supported_Cards)

> **lovinglinux said:**
> You cannot really compare Ubuntu Karmic Koala with Windows XP, since the last one is very old and requires less resources. Nevertheless, I believe playing HD videos also depends on processor power. For instance, I had a P4 until a couple of weeks ago and I wasn't able to play 720p movies without lagging and freezing. I have upgraded to a Core 2 Duo and it plays perfectly now. I'm using the same video card, which is a nvidia 7300GT.

Win XP needs less resources? I dont think so. Even with a stock ubuntu install, it uses a bit more RAM than XP, and a minimal install will use quite a bit less than Windows XP will. 

If you have of got an 8xxx series card, your old P4 would have played HD fine. If the 7xxx supported VDPAU, that would have been fine as well.

---

### Post by dzooky on 2009-12-27
> **cascade9 said:**
> There is 2 different sorts of 'hardware decoding' for nVidia CPUs. 

nVidia Pure video- supports geforce 7xxx. I'm not sure if that includes the 7000, but I think that the 7000 was another 'M' model in which case it should-
[http://www.nvidia.com/page/purevideo_support.html](http://www.nvidia.com/page/purevideo_support.html)

VDPAU (Video Decode and Presentation API for Unix), which is pretty much 'pure video' for linux/solaris/freeBSD. 7xxx NOT supported-
[http://www.mythtv.org/wiki/VDPAU#Supported_Cards](http://www.mythtv.org/wiki/VDPAU#Supported_Cards)


I have exactly graphic card GeForce 7150M. The "M" means that it is mobile (I found it on the web)
From [**this**]("http://en.wikipedia.org/wiki/VDPAU") wiki side i know that VPDAU is supported from GeForce 8400GS and higher.
My card support VP1 (Pure Video) and from [**this site**]("http://en.wikipedia.org/wiki/Nvidia_PureVideo") it means that my card support "Realtime decoding of H.264 high-profile L4.1, VC-1 Advanced Profile L3, and MPEG-2 MP@HL (1080p30) decoding @ 40 Mbps"

On the [**another page**]("http://en.wikipedia.org/wiki/VaAPI") I find something VA API. I tried Mplayer VAAPI but I've got error 

```
libva: libva version 0.31.0-sds4
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
libva: va_getDriverName() returns 0
libva: Trying to open /usr/lib/va/drivers/nvidia_drv_video.so
libva: va_openDriver() returns -1
[vo_vaapi] vaInitialize(): unknown libva error
Error opening/initializing the selected video_out (-vo) device.

```

---

### Post by gradinaruvasile on 2009-12-27
> **dzooky said:**
> Hi guys
I have laptop HP Pavilion DV6646US with graphic card GeForce 7150M Somewhere on the internet I find that differences between 7000 & 7150 is that 7150 support decoding of HD movies.

On my ubuntu I try many players but it did play smoothly.
I try play movies on windows XP also and there is everything OK.

Can somebody help me
Thanks

Your card is NOT supported by VDPAU under Linux. 
Under Windows it supports VP1 (PureVideo set 1).

[http://en.wikipedia.org/wiki/VDPAU](http://en.wikipedia.org/wiki/VDPAU)

Only the 8 series (including Quadro NVS 135M, 140M) and newer cards are supported.I tested Quadro NVS 135M & 140M (laptop), NVS 285 (desktop), Nvidia 8200 (IGP), Nvidia 7600 (desktop). 
With the 135M, 140M and the 8200 IGP i was able to play 1080p movies at 10% CPU usage with mplayer. 
The NVS 285 and 7600 did not support VDPAU. The 285 should have in theory, but it did not work.

The best performer was the 8200 integrated (on Asus M3N78-VM mobo) with a lowly Athlon 3200+/AM2 single core CPU. Even with Compiz on (with transparent cube, atlantis plugin, transparent+blurred window bars) it played perfectly (full screen) under Ubuntu 9.04 (Gnome) with the 195.22 and 195.30 Nvidia drivers.

---

### Post by dzooky on 2009-12-27
> **gradinaruvasile said:**
> Your card is NOT supported by VDPAU under Linux. 
Under Windows it supports VP1 (PureVideo set 1).

[http://en.wikipedia.org/wiki/VDPAU](http://en.wikipedia.org/wiki/VDPAU)

Yes I know that VDPAU is not supported, but about VP1 in linux?

---

### Post by gradinaruvasile on 2009-12-27
PureVideo is Windows technology. It's the equivalent of VDPAU in Linux. Or rather the other way around.

---

### Post by solitaire on 2009-12-27
it also depends on the format of the 720p movie! running from a Blu-Ray disk will be slower than a .MKV file.

I can output to my 1080p screen; 720p encoded mkv (and the odd 1080p encoded mkv) files using my laptop Celeron 2Ghz (Intel GM965 intergrated graphics) I have to use "cvlc" other players cause sync and tearing issues.

It also depends on the drivers you use...

---

### Post by cascade9 on 2009-12-28
> **gradinaruvasile said:**
> PureVideo is Windows technology. It's the equivalent of VDPAU in Linux. Or rather the other way around.

Yeah, I really should have made that clear in my post...sorry about that. 

> **solitaire said:**
> it also depends on the format of the 720p movie! running from a Blu-Ray disk will be slower than a .MKV file.

I can output to my 1080p screen; 720p encoded mkv (and the odd 1080p encoded mkv) files using my laptop Celeron 2Ghz (Intel GM965 intergrated graphics) I have to use "cvlc" other players cause sync and tearing issues.

It also depends on the drivers you use...

Intel grpahics dont have the hardware decoding capabilities of nVidia (under linux or windows) or ATI (windows only so far, hopefully that is fixed at some point). If you had a (supported) nVidia card, you wouldn't have the sync and tearing issues. Well, you shouldn't anyway, no doubt some driver version has had some issues.

---

### Post by bluebyt on 2009-12-28
I have the same problem. My computer is slow and the video playback is unwatchable with Ubuntu (P4 1.7Ghz, Video card FX5200, 512Meg Ram)

My card nvidia FX5200 doesn't supported the VDPAU.

This is sad, because with WinXP the video playback play perfectly!

On the other hand, I have another computer a Coreduo and this one have no problem to play any movie.

---

### Post by lovinglinux on 2009-12-29
> **bluebyt said:**
> I have the same problem. My computer is slow and the video playback is unwatchable with Ubuntu (P4 1.7Ghz, Video card FX5200, 512Meg Ram)

My card nvidia FX5200 doesn't supported the VDPAU.

This is sad, because with WinXP the video playback play perfectly!

On the other hand, I have another computer a Coreduo and this one have no problem to play any movie.

Interesting thread. I didn't know about VDPAU support. So our card doesn't support it, but the Core2 Duo can handle the extra load.

---

