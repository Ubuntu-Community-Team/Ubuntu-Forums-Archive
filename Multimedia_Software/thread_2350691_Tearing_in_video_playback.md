---
title: "Tearing in video playback"
date: 2017-01-26
forum: Multimedia Software
---

### Post by orestis-0 on 2017-01-26
Hello, 

I have a laptop with i5-7200U and nvidia 940MX with the latest closed nvidia drivers offered from the official ubuntu repos. When I watch videos there is some tearing. The problem appears with different apps(stremio, vlc, smplayer), different video formats(mkv, mp4) and with both cards(nvidia and intel). I tried it in Unity and openbox with the same results. It is not a problem with the files as I tried it in another laptop and it was working perfectly.

P.S. I don't have tearing problems with chrome in youtube or other online videos.

---

### Post by orestis-0 on 2017-01-26
Edit: If I i watch a tearing test video on youtube it happens there too...

---

### Post by Keith_Helms on 2017-01-28
If this is an Optimus system with dual Intel and Nvidia graphics, then the last I heard a fix for tearing while using the Nvidia driver is still in the works.

If it is not an Optimus system then there are some things you can try.  I was recently having tearing on the TV connected to my PC with HDMI and making a couple of changes solved it.  First I had to go into nvidia-settings and make sure Sync to VBlank was set under OpenGL settings.  Then I had to make a couple of changes to /etc/X11/xorg.conf.  Actually, I had to use the nvidia-settings save configuration option to create xorg.conf before I could change it.  Once it existed, I add the following:

```

Section "Device"
    Identifier     "Device1"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce GT 430"
    **Option         "TripleBuffer" "True"**
    BusID          "PCI:1:0:0"
    Screen          1
EndSection

[B]Section "Extensions"
    Option "Composite" "Disable"
EndSection[/B]

```

---

### Post by SeijiSensei on 2017-01-28
With SMPlayer, are you using the vdpau video driver or the default xv one?  Look in Options > Preferences and choose the Video tab.  Select vdpau from the driver drop-down.  This will use the hardware decoder on the NVIDIA card for content encoded with H.264 instead of the software decoder. Any better?

---

### Post by mc4man on 2017-01-28
> **orestis-0 said:**
> Hello, 

I have a laptop with i5-7200U and nvidia 940MX 
When using the nvidia drivers (thru nvidia-prime) tearing is 100% expected.
When using the Intel iGPU & Unity/compiz there should be no tearing though seeing as though it's a newer cpu maybe there's an issue.
I've got a i7-6XXXX & nvidia 965m machine, maybe i'll check it out at some point on a live session, no interest yet in installing Ubuntu on that hardware.

As far as openbox, no idea though wouldn't be surprised if there is tearing on it..

---

