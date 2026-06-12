---
title: "Sound via HDMI but not via MB audio chip"
date: 2010-11-06
forum: Multimedia Software
---

### Post by anatolik on 2010-11-06
Hi,

Recently I installed Ubuntu 10.10 64bit and I have a problem with it.

I have a motherboard with internal audio card as well as I have ATI 2600 card. When I just installed Ubuntu 10.10 sound via motherboard worked perfectly.

But some time later it disappeared. Actually "Output device" that represents audio card disappeared. See screenshot of the Audio Settings dialog.

I made 2 thing - most likely that one of them cause this problem:
  - I tried to setup Panasonic Plasma TV as a second monitor via HDMI output of my video card (ATI 2600).
  - I added maven-backports repository (new kernel or new audio driver??)

Have anybody seen this problem? Are any pointers how to fix it? If you need any additional info - let me know I'll be glad to provide it.

---

### Post by lidex on 2010-11-06
Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.
[Terminal="Applications->Accessories->Terminal"]

---

### Post by anatolik on 2010-11-07
> **lidex said:**
> Use the alsa-info-script to provide detailed information.

Here is the alsa-script information [http://www.alsa-project.org/db/?f=387dcab3baaf159260fd3a0eb911872bee0f8e9f](http://www.alsa-project.org/db/?f=387dcab3baaf159260fd3a0eb911872bee0f8e9f)

Thanks for the tip.

---

### Post by lidex on 2010-11-07
Alsa is definitely not seeing your onboard sound card. If lshw doesn't see it, go into your bios and make sure it's enabled.
```
sudo lshw -C multimedia
```

---

### Post by anatolik on 2010-11-07
> **lidex said:**
> Alsa is definitely not seeing your onboard sound card. If lshw doesn't see it, go into your bios and make sure it's enabled.
```
sudo lshw -C multimedia
```

You are right. The chipset Audio has been disabled in BIOS. I feel like total noob <facepalm>.

I was confused because it worked before, but then stopped when I tried to setup ATI dual-monitor system. I don't remember when I disabled audio in BIOS, probably i did it accidently.

Thanks a lot, lidex.

---

