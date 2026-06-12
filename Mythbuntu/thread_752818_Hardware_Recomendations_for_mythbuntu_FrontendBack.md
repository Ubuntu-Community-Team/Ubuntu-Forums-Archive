---
title: "Hardware Recomendations for mythbuntu Frontend/Backend"
date: 2008-04-12
forum: Mythbuntu
---

### Post by pinkmonkey on 2008-04-12
The hard drive in my MCE box endoed today and took a Face plant.I was getting tired of the bugs in MCE anyway so I'm not to upset.... but I will miss recording tv untill I build something new. I would like to try mythbuntu with a backend and a frontend.  I plan on repurposing my old box as the backend and building a silent frontend. I just need to know what will work and what wont.

My current setup is.
Board: ASUS P4S800D X
Processor: P4 2.4
1 G' of ram
Tuner:  WinTV 250
Video Card: Geforce 6200
MCE Remote... and IR reciever/blaster


What I would like to do. Record TV (off course). Change TV on my STB with the IR Blaster. Playback HD in 720p. And not to spend an arm and leg getting there. Any help would be greatly appreciated

---

### Post by reyhan on 2008-04-12
this is the minimum and  Recommended System Requirements
   
 * 1.0 GHz x86 or x86_64 Processor
    * 192 MB of system memory (RAM)
    * 2 GB of disk space (Frontend Role)
    * 20 GB of disk space (Backend Role)
    * Graphics card capable of 1024x768 resolution
    * Supported TV Tuner Card (Backend Role)

Recommended System Requirements:

    * 2.0 Ghz x86 or x86_64 Processor*
    * 1024 MB of system memory (RAM)
    * 10 GB disk space (Frontend Role)
    * 80 GB+ disk space (Backend Role)**
    * nVidia 128MB Graphics Card w/ TV-Out or equivalent***
    * Supported TV Tuner Card (Backend Role)

* A 3.0 Ghz processor is recommended for frontend installations using HD video due to the increased load upon decoding. A lower end processor can be used however with multiple functions on a single machine (ie - Frontend/Backend Install) it is not recommended.

** 80 GB of disk space allows approx 70 GB of usable space for media. However with HD Format it is recommended to use 160 GB HDD or larger.

*** Although nVidia is recommended, ATI, VIA, or Intel graphics cards are supported and will work. Currently, nVidia provides a higher level of support. Also the graphics recommendation is based on HDTV capable output processing.

Note: A good estimate for converting hard disk space to hours of recordings are as follows:

    * Standard Definition (Analog) 2.2 GB / Hour
    * High Definition (HDTV) 7 GB / Hour

Long Answer

Long answer:

CPU: Lots of different ideas here. Simply put. Using a hardware encoding capture card, you need around 800mhz for watching standard definition and recording another (or watching live tv). You need 3Ghz for High-Definition.
More in depth and complicated answer

* A PIII/733MHz system can encode one video stream using the MPEG-4 codec using 480x480 capture resolution. This does not allow for live TV watching, but does allow for encoding video and then watching it later.
* A developer states that his AMD1800+ system can almost encode two MPEG-4 video streams and watch one program simultaneously.
* A PIII/800MHz system with 512MB RAM can encode one video stream using the RTjpeg codec with 480x480 capture resolution and play it back simultaneously, thereby allowing live TV watching.
* A dual Celeron/450MHz is able to view a 480x480 MPEG-4/3300kbps file created on a different system with 30% CPU usage.
* A P4 2.4GHz machine can encode two 3300Kbps 480x480 MPEG-4 files and simultaneously serve content to a remote frontend.
* I think I could watch (not watch and record at the same time) High-Definition with a AMD Athlon 2600+ and an nVidia 5500. I never got to test this though as I built a new Athlon X2 3800+.

Hard Drive: This depends on what you want to record, and how much you want to keep at a time. I've seen around 1.7-2GB per 30 minutes of Standard Definition from a PVR-150. 6.4-7GB per hour of High-Def.

RAM: 256MB should be the bare minimum. I wouldn't build a system without at least 512MB, and would probably lean toward 1GB.

Video Card: This kinda depends on what you want your system to do. I use an on board Nvidia 6200. I connect to my TV via VGA. I can do HD fine on this card with XvMC activated and bob 2x. I have also used a Gigabyte Geforce 7300GS with comes with a dongle for Component out and also svideo out. IMHO, stay far far far away from ATI. Nothing good can come from that. If you already have a video card and still need a way for TV out, I believe that the PVR-350 has video out via S-Video.

Sound Card: Unfortunately, I just use on board sound because I don't have a nice card here. I'm looking for suggestions on this. (they need to work nicely)

Remote: I recommend the Windows Media Center (MCEUSB2) remote. It is a great remote and if you don't have one, then get one. And if you have one, then buy another and give it to a friend. If all your friends already have one too, then build another frontend and buy another MCEUSB2 for it.

Tuners:

* Standard Definition: PVR-150, works OOB, has hardware encoder, comes in low profile. The PVR-500 has 2 encoders on a single card, but doesn't come in low profile.
* High Definition: HDHomerun. Dual HD tuner and it connects via ethernet so you can free up a pci slot. If you want something internal, then I recommend the pcHDTV 5500. Works great OOB, high quality, also has an analog tuner, but doesn't have a hardware encoder for the analog encoder. (FYI, High-Def doesn't need a hardware encoder because it comes already in mpeg2ts)

---

### Post by pinkmonkey on 2008-04-12
Thanks Reyhan, I've read that before, but I read it again to make sure I wasn't missing something. So it looks like the p4 2.4 will work fine for the backend. But I'm still looking for some answers will the WinTV 250 work with Mythbuntu, all anyone ever recommends is the 150 and 500. And if I store my HD content on the Backend will it play properly.And I am also looking for advice on some specific hardware that people have used for their frontends that works well with few glitches.Even a hardware list of tried and tested components. Any help would be appreciated I want my first MythTV experience to be great and I wouldn't want any hardware issues to ruin it.

---

### Post by tgm4883 on 2008-04-14
This might not be exactly what you are looking for but here

[http://linux.weilandhomes.com/hardware](http://linux.weilandhomes.com/hardware)

---

