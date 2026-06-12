---
title: "Setting resolution and refresh rate"
date: 2006-08-04
forum: Multimedia &amp; Video
---

### Post by Nordkraft on 2006-08-04
Hi there,

I'm trying to get the correct resolution and refresh rate set up for my monitor, a Sun/Sony GDM-5410 ( [http://www.sunshack.org/data/sh/2.1/infoserver.central/data/syshbk/Devices/Monitor/MONITOR_Color_21_Prem_Flat_CRT.html](http://www.sunshack.org/data/sh/2.1/infoserver.central/data/syshbk/Devices/Monitor/MONITOR_Color_21_Prem_Flat_CRT.html) ); my gfx is an ATI Radeon X1900XTX.

As the specs say it has HorizSync 30 - 121 kHz, VertRef. 	
48 - 160 Hz, which I put in my xorg.conf. The Gnome system>pref.>res. enables me to choose 1280x1024@100 and @90, but for some reason choosing these does not change the ref. rate above 85 :confused: . Any suggestions as to how I might fix this?

Cheers!

---

### Post by patrick295767 on 2006-08-04
> **Nordkraft said:**
> Hi there,

I'm trying to get the correct resolution and refresh rate set up for my monitor, a Sun/Sony GDM-5410 ( [http://www.sunshack.org/data/sh/2.1/infoserver.central/data/syshbk/Devices/Monitor/MONITOR_Color_21_Prem_Flat_CRT.html](http://www.sunshack.org/data/sh/2.1/infoserver.central/data/syshbk/Devices/Monitor/MONITOR_Color_21_Prem_Flat_CRT.html) ); my gfx is an ATI Radeon X1900XTX.

As the specs say it has HorizSync 30 - 121 kHz, VertRef. 	
48 - 160 Hz, which I put in my xorg.conf. The Gnome system>pref.>res. enables me to choose 1280x1024@100 and @90, but for some reason choosing these does not change the ref. rate above 85 :confused: . Any suggestions as to how I might fix this?

Cheers!

```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by Nordkraft on 2006-08-04
Will this mess up my otherwise perfectly ok working xorg.conf file?

---

### Post by Nordkraft on 2006-08-04
Ok. Backed up my xorg.conf and tried the 

sudo dpkg-reconfigure xserver-xorg

The xserver didn't start up instead my monitor made a very unpleasant sound, sort of high frequency noise, and I had the feeling some sort of "out of sync"-stuff was goin on:shock: , so I switched it off and returned to my original .conf-file. No idea if monitor-smashing was actually taking place, but I didn't like it. Guess I'm sticking with 85 and a working monitor.

Thanks anyway. 

Cheers!

---

