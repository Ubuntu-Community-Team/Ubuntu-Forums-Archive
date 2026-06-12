---
title: "ati 4850 choppy video with restricted drivers"
date: 2009-06-14
forum: Multimedia Software
---

### Post by danbyrne on 2009-06-14
Hi all

First of all, congrats on a VERY nice looking and functional distro, I was origonally using SuSE/Debian and I think I've found my new OS.

I have a radeon HD 4850 and an X-Fi extreme music card (not the best combination to start with, I know :-)) Sound is working fine with the exception of missing 5.1 but video is another story...

I enabled the restricted driver for the video but was getting a choppy display i.e. when moving a window around with Compiz installed or watching a movie. Initially when going fullscreen it would freeze the whole system but that issue is now fixed by adding 'no-xv' to gstreamer properties. I tried downloading the newest binaries from ati.com, and enabling vertical sync but still no luck, videos are unwatchable. Next step is disabling compiz I suppose, although that's a bit of a shame.

Any help would be very much appreciated as I've spent about 2 hours googling and experimenting. Would hate to go back to Windows 7 but need this working as a multimedia system as it's hooked up to the plasma in the front room.

Cheers!

```


Section "ServerLayout"
        Identifier     "aticonfig Layout"
        Screen      0  "Default Screen" 0 0
EndSection

Section "Files"
EndSection

Section "Module"
        Load  "glx"
EndSection

Section "Monitor"
        Identifier   "Configured Monitor"
EndSection

Section "Device"
        Identifier  "Configured Video Device"
        Driver      "fglrx"
        Option      "Capabilities" "0x00000800"
        BusID       "PCI:1:0:0"
EndSection

Section "Screen"
        Identifier "Default Screen"
        Device     "Configured Video Device"
        Monitor    "Configured Monitor"
        DefaultDepth     24
EndSection



```

---

### Post by theApokalypsis on 2009-06-15
AMD's drivers are still pretty spotty performance for compiz, also with making your CPU do the video work.

Although I just read about a 9.6 revision of the catalyst driver [here]("http://www.phoronix.com/scan.php?page=news_item&px=NzMyOA") with updates for playback, dual monitor etc. Im going to check it out myself.


I have a 4850, If still trouble I would suggest using the open source drivers for the time being (no compiz but 3D support is on the horizon) and great accelerated playback. radeon/radeonhd (xserver-xorg-video-ati or -radeon)


their comparison wiki [http://wiki.x.org/wiki/RadeonFeature]("http://wiki.x.org/wiki/RadeonFeature")

---

