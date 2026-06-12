---
title: "What video card work well with Beryl + Dual monitor setup?"
date: 2006-11-26
forum: Multimedia &amp; Video
---

### Post by bluefox on 2006-11-26
Hi, I have dual 17' LCD setup with 1280 x 1024 on both (2560 x 1024). I tried different version of fglrx driver with Xgl but it simply won't let me run under dual screen mode. I'm currently using Radeon 9800 in AIGLX with 6.10 Edgy and MergeFB. When I'm running Beryl though, it won't display any background image, the desktop is completely blank with a black line at my right screen. I think it is limited by the ATI hardware that only supports 2048 x 2048 pixmap.

Well I want to try the awesome 3d effects in Beryl real bad ](*,). I'm wondering if anyone could kindly suggest some cheap video card that works well with Beryl in dual monitor setup? :mrgreen: Thanks a million!

---

### Post by ~LoKe on 2006-11-26
My $100 7300GT is running two 1907FP's at 1280x1024 each.  The card has dual DVI, which is awesome.  I've got Beryl and TwinView running just fine.

---

### Post by Leed on 2006-11-27
I got beryl running on my Home system with two screens using a GeForce 5200MX card, both screens (VideoSeven L17EB) hooked on the same card. 

But getting there was quite a struggle, so don't give up if your card doesn't work on first try. 

Of course me not using an ATI is no big help to you... The hardest bit was getting the correct display drivers up and enabling TwinView. 


Be warned, Beryl in TwinView mode is weird, the Emerald Box turns into an Octagon and upon turning the content of the screens switches.

---

### Post by ~LoKe on 2006-11-27
> **Leed said:**
> I got beryl running on my Home system with two screens using a GeForce 5200MX card, both screens (VideoSeven L17EB) hooked on the same card. 

But getting there was quite a struggle, so don't give up if your card doesn't work on first try. 

Of course me not using an ATI is no big help to you... The hardest bit was getting the correct display drivers up and enabling TwinView. 


Be warned, Beryl in TwinView mode is weird, the Emerald Box turns into an Octagon and upon turning the content of the screens switches.

At least with the SVN, you can change the behaviour.

---

### Post by galv on 2006-11-28
> **~LoKe said:**
> I've got Beryl and TwinView running just fine.

How did you do that? Can you give some hints?

---

### Post by bluefox on 2006-11-28
Wow even GeForce 5200MX works with dual screen setup? ATI should be ashamed of themselves. [-(

---

### Post by ~LoKe on 2006-11-28
> **galv said:**
> How did you do that? Can you give some hints?

What problem are you having?  TwinView?

---

### Post by Leed on 2006-12-01
@Galv

First critical step is getting the right drivers (nv), upon standard ubuntu install one of the screens will look pretty ugly when plugged in :rolleyes: 

With the nvidia packet from one of the standard repositories, TwinView will already run, but not beryl. 

eventually I got the beta drivers from this HowTo:
[http://ubuntuguide.org/wiki/Ubuntu:Edgy#How_to_install_Beta_Graphics_Driver_.28NVIDIA.29]("http://ubuntuguide.org/wiki/Ubuntu:Edgy#How_to_install_Beta_Graphics_Driver_.28NVIDIA.29")

then you'll need to edit your xorg.conf file, but first make sure you have a backup, it's almost sure to fail on first attempt
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_gfxold
```

In the "screen" section I added the following code
```

#Beryl settings
 Identifier     "Default Screen"
 Device         "NVIDIA Corporation NV34 [GeForce FX 5200]"
 Monitor        "L17AS"
 DefaultDepth   "24"
 Option         "AddARGBGLXVisuals" "True"
 Option         "DisableGLXRootClipping" "True"
#End Beryl
 Option         "TwinView" "True"
 Option         "TwinViewOrientation" "LeftOf"
 Option         "RenderAccel" "True"
 Option         "TrippleBuffer "True"

```

Also I added Beryl using the following HowTo:
[http://ubuntuguide.org/wiki/Ubuntu:Edgy#How_to_install_Beta_Graphics_Driver_.28NVIDIA.29]("http://ubuntuguide.org/wiki/Ubuntu:Edgy#How_to_install_Beta_Graphics_Driver_.28NVIDIA.29")


...All in all took some repairing after several times that X Server wouldn't start anymore [COLOR="Red"]SO AGAIN, DO BACKUP THE xorg.conf FILE[/COLOR], apart from that things worked pretty nice

good luck trying
Dave

---

### Post by acegolfer on 2006-12-13
My 6200AGP card handles twinview and beryl very well.

---

### Post by Cryptic1911 on 2006-12-13
I have a 256mb 6600gt with dual 20.1's at 1600x1200 (3200x1200 for both). works awesome.. no chop at all.:cool:

---

