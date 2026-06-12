---
title: "Rendering Video Crashes Computer"
date: 2022-03-10
forum: Multimedia Software
---

### Post by Rick St. George on 2022-03-10
Strange - my computer shuts down when attempting to render video, with both DeVeDeNG and Kdenlive. Have all updates and latest OS "UbuntuStudio v20.04 LTS".

Any ideas Why??

Tried searching archives but anything more than 2 words and Search FAILS.

Thanks!

---

### Post by #&amp;thj^% on 2022-03-10
I have one of your older ones here: [https://ubuntuforums.org/archive/index.php/t-2336852.html](https://ubuntuforums.org/archive/index.php/t-2336852.html)
Your Machine Specs may help as well.

---

### Post by Rick St. George on 2022-03-10
Looks like DeVeDe is unstable ... Noticed this in Synaptic Pkg. Mgr.

> 
devede (4.15.0-2) unstable; urgency=medium

  * Team upload.
  * Change scour build-dependency to not use Python 2 packages
    (Closes: #942947).

 -- Stuart Prescott <stuart@debian.org>  Thu, 16 Jan 2020 12:23:57 +1100

devede (4.15.0-1) unstable; urgency=medium



ALSO, get this Error when attempting to Add Kdenlive Debug Symbols;

> 
W: Download is performed unsandboxed as root as file '/root/.synaptic/tmp//tmp_cl' couldn't be accessed by user '_apt'. - pkgAcquire::Run (13: Permission denied)


Is there a good alternative that works in Ubuntu? Simply trying to Convert / Burn an MP4 video file.

Thanks!

---

### Post by #&amp;thj^% on 2022-03-10
Have you used HandBrake and Makemkv?

---

### Post by Rick St. George on 2022-03-10
SYSTEM INFO

Mobo:
MSI 990FXA-GD65 v2R

CPU:
AMD FX-8320 Vishera 8 core ... with a Cooler Master GeminII S524 Version 2 CPU Air Cooler with 120 mm Silenx FP Fan, 2 more Fans - 1 Front, 1 Rear (70 CFM)

RAM:
2 x 8GB Corsair Vengence DDR3 1600 Mhz (PC3 12800)

GPU:
ASUS Nvidia GeForce GT610 w/2GB DDR3 Ram (running 2 monitors)

PSU:
Enermax ENP450AST 450 Watt

SSD: Samsung 840 EVO 250GB SATA III

OS:
UbuntuStudio-64 v20.04 LTS

----------------------------

And NO, I haven't tried Handbrake or Makemkv. Will it make a difference?  Will try and report back. Thanks!

---

### Post by #&amp;thj^% on 2022-03-10
> **Rick St. George said:**
> SYSTEM INFO

Mobo:
MSI 990FXA-GD65 v2R

CPU:
AMD FX-8320 Vishera 8 core ... with a Cooler Master GeminII S524 Version 2 CPU Air Cooler with 120 mm Silenx FP Fan, 2 more Fans - 1 Front, 1 Rear (70 CFM)

RAM:
2 x 8GB Corsair Vengence DDR3 1600 Mhz (PC3 12800)

GPU:
ASUS Nvidia GeForce GT610 w/2GB DDR3 Ram (running 2 monitors)

PSU:
Enermax ENP450AST 450 Watt

SSD: Samsung 840 EVO 250GB SATA III

OS:
UbuntuStudio-64 v20.04 LTS

----------------------------

And NO, I haven't tried Handbrake or Makemkv. Will it make a difference?  Will try and report back. Thanks!
Overall Looks like the same system more or less from your 2017 post.
I really like Makemkv:[https://connectwww.com/how-to-install-makemkv-on-ubuntu-mkv-converter/61127/](https://connectwww.com/how-to-install-makemkv-on-ubuntu-mkv-converter/61127/)
I absolutely hated the snap version, so a heads-up there.

---

### Post by deadflowr on 2022-03-10
unstable in context is reference to the repository it came from or was in at the time of the changelog entry.
unstable is the branch from Debian that Ubuntu pulls it's packages from.

---

### Post by Rick St. George on 2022-03-11
> **1fallen said:**
> Overall Looks like the same system more or less from your 2017 post.
I really like Makemkv:[https://connectwww.com/how-to-install-makemkv-on-ubuntu-mkv-converter/61127/](https://connectwww.com/how-to-install-makemkv-on-ubuntu-mkv-converter/61127/)
I absolutely hated the snap version, so a heads-up there.

I looked at MakeMKV, but it only Rips video from a disk. 

What I'm trying to accomplish is take an MP4 Video, Convert and Burn to a DVD so everyone can enjoy the video.

Is there not a good program, or 2 or 3, that can accomplish this task?

Thanks for any help!

---

### Post by #&amp;thj^% on 2022-03-11
Outside of the ones you have had issues with,  this HandBrake  and xfburn   [DVDStyler]("https://www.dvdstyler.org/en/")  comes to mind.
Are you not concerned about the cause of the shutdown though?

---

### Post by Yellow Pasque on 2022-03-13
Overheating?

---

### Post by Rick St. George on 2022-03-23
> **1fallen said:**
> 
Are you not concerned about the cause of the shutdown though?


In looking at my previous post (see link in #2 above), I installed "cpufrequtils" but  "sysv-rc-conf" was not available. 
Here is my output;

```

~$ sudo modprobe cpufreq_conservative

~$ sudo echo conservative > /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor
bash: /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor: Permission denied

```

So still unable to change it. Not sure if that would keep GPU from overheating. Not sure why these Video Burning programs are using the GPU ???

System Fans are cooling system effectively. But either CPU or GPU is overheating and shutting down system. Any ideas???
Thanks!

---

### Post by SeijiSensei on 2022-03-23
> **Rick St. George said:**
> What I'm trying to accomplish is take an MP4 Video, Convert and Burn to a DVD so everyone can enjoy the video.
I've used Handbrake for that task, converting an mp4 to the traditional DVD format. Has that not worked for you?

KDEnlive is overkill is you don't need to edit the video, create overlays, etc.

These days a lot of TVs have USB ports and can play MP4 video directly off a thumb drive. Support for open formats like Matroska ("mkv") and flac audio is more spotty.

---

### Post by #&amp;thj^% on 2022-03-23
> **Rick St. George said:**
> 
System Fans are cooling system effectively. But either CPU or GPU is overheating and shutting down system. Any ideas???
Thanks!
Just as a first thought, whens the last time you blew this little baby out?
That dust that statically accumulates acts like a heater, or a very warm heating blanket.
Second thought and less likely hardware failing, but this machine I assume is the same one from a year or more ago, and most likely to have died by now.

---

### Post by Rick St. George on 2022-03-23
> **SeijiSensei said:**
> I've used Handbrake for that task, converting an mp4 to the traditional DVD format. Has that not worked for you?

KDEnlive is overkill is you don't need to edit the video, create overlays, etc.

These days a lot of TVs have USB ports and can play MP4 video directly off a thumb drive. Support for open formats like Matroska ("mkv") and flac audio is more spotty.

Thanks Sensei, but I tried to use handbrake to convert, but ONLY wants to save in MP4 format, under General, 
and Web / Devices / Production don't apply.

---

### Post by Rick St. George on 2022-03-23
> **1fallen said:**
> Just as a first thought, whens the last time you blew this little baby out?


Checked to make sure, since I moved here a year ago. Clean as a whistle.

---

### Post by #&amp;thj^% on 2022-03-23
It's been a while so I'm not sure I've asked this, but have you checked out a [cooling pad,]("https://www.amazon.com/laptop-cooling-pad/s?k=laptop+cooling+pad") just for these occasions.

---

### Post by Rick St. George on 2022-03-23
> **1fallen said:**
> It's been a while so I'm not sure I've asked this, but have you checked out a [cooling pad,]("https://www.amazon.com/laptop-cooling-pad/s?k=laptop+cooling+pad") just for these occasions.

NO, this is a desktop sitting on the floor, with good air circulation.
And Brasero burns an unusable DVD, not recognized in DVD player (which plays others fine).

---

### Post by #&amp;thj^% on 2022-03-23
Ah Ha, duly noted. ;)
I used to have to pull a case side panel off and blow a fan at it.
I would if not already, look at a better heat sink with a cooling fan.
This is most certainly a CPU temp problem, if this keeps happening your going to shorten your machines/MoBo life

---

### Post by Yellow Pasque on 2022-03-23
STOP using RANDOM CAPS if you want people to take you seriously....

---

### Post by Rick St. George on 2022-03-24
I believe I'll try a new GPU. Any suggestions for this big machine with 8 core AMD in the $100 range?

SYSTEM INFO

Mobo:
MSI 990FXA-GD65 v2R

CPU:
AMD FX-8320 Vishera 8 core

RAM:
2 x 8GB Corsair Vengence 1600 Mhz

GPU:
ASUS GT610 w/2GB DDR3 Ram (running 2 monitors)

PSU:
Enermax ENP450AST 450 Watt

OS:
UbuntuStudio-64 v16.04 LTS


I have an AMD FX-8350 cooled by a big Noctua with two 140mm fans.

---

### Post by #&amp;thj^% on 2022-03-24
Rick before I did that i would look at a better cooling fan, those fx cpus ran hot under certain loads.
I have used this one before: [https://www.newegg.com/cryorig-air-cooler-series-h7/p/13C-000U-00005](https://www.newegg.com/cryorig-air-cooler-series-h7/p/13C-000U-00005)
Mine currently is ```
Info: 6-core model: AMD Ryzen 5 4600H with Radeon Graphics bits: 64
    type: MT MCP cache: L2: 3 MiB
  Speed (MHz): avg: 1735 min/max: 1400/3000 cores: 1: 2986 2: 3875 3: 1397
    4: 1397 5: 1397 6: 1397 7: 1398 8: 1398 9: 1397 10: 1396 11: 1397 12: 1394
```
GPU's
```
Graphics:
  Device-1: NVIDIA TU117M [GeForce GTX 1650 Ti Mobile] driver: nvidia
    v: 510.54
  Device-2: AMD Renoir driver: amdgpu v: kernel
  Device-3: Syntek Integrated Camera type: USB driver: uvcvideo
  Display: x11 server: X.Org v: 1.21.1.3 driver: X:
    loaded: modesetting,nvidia unloaded: fbdev,vesa gpu: amdgpu
    resolution: 1920x1080~120Hz
  OpenGL:
    renderer: AMD RENOIR (DRM 3.42.0 5.15.31-hardened1-1-hardened LLVM 13.0.1)
    v: 4.6 Mesa 21.3.7

```
and when I render or transcode video's cpu gets real warm, while both gpu's stay within a comfortable danger zone like 40 to 45 degrees celsius.

But if your bent on the GPU here are some I have personally tested.
At a Glance:
[list]
    [*]ZOTAC GeForce GT 1030
    [*]XFX RX 550 2GB
    [*]ZOTAC GeForce GT 730
    [*]Asus AMD Radeon R7 250
    [*]GeForce GT 740 OC
    [*]Nvidia GeForce GTX 750Ti
    [*]Asus GeForce GTX 650Ti
[/list]
at the time they were in that price range.
EDIT: BTW: this just came to mind, check the seat of the heat sink, and if this is still the original when bought, you may try to clean and re-paste with new Thermal Paste. (It does wear out quickly)
Thermal paste is one of the most critical components of any PC build. It's what ensures direct even contact between the CPU and cooling sink and fan

---

