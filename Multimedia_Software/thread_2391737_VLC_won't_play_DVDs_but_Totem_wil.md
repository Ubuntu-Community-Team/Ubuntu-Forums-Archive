---
title: "VLC won't play DVDs but Totem wil"
date: 2018-05-12
forum: Multimedia Software
---

### Post by jeo7 on 2018-05-12
I'm running Ubuntu 18.04. I'm still trying to work out my drivers for my Radeon R7 series. This may or may not be a driver problem so that is why I am posting it here.

I can play DVDs fine with Totem. No problems whatsoever except that the audio sounds weak. However VLC Player doesn't want to play them at all. I can't get past the menu on the DVD. If I do get past the menu, it's a mash of pixellated nonsense. This is somewhat surprising since VLC is said to play media that other players cannot or will not. The reason I want to run VLC is because you can take the volume up above maximum.

Ubuntu-restricted-extras is installed.

Has this happened to anyone else? Does anyone have any idea of how to remedy it?

I will appreciate it very much for any help I receive.

---

### Post by monkeybrain20122 on 2018-05-12
Did you install vlc from the solfware centre? If so it is a snap package and apparently cannot access devices such as dvd drive. If that is the case first remove vlc from the software centre, then install the normal .deb
```
sudo apt install vlc
```

But you probably don't want to have to use the command line everytime because you may not know the name of the pkg, you want to try things out etc

so install the synaptic package manager, it doesn't have the fancy pictures of the software centre but it has a lot more software and you can search for them by categories, also you don't get snap from synaptic.

```
sudo apt install synaptic
```

---

### Post by mc4man on 2018-05-12
> **monkeybrain20122 said:**
> Did you install vlc from the solfware centre? If so it is a snap package and apparently cannot access devices such as dvd drive. 
The snap vlc may be able to access optical drives but absolutely can't use libdvdcss2 to decrypt commercial dvd's. Could be the case here as DVD_VIDEO menus aren't css encrypted.
Also the default for vlc is to automatically use hardware acceleration, no hardware from the last 15 years or so needs that for DVD_VIDEO (mpeg2

---

### Post by monkeybrain20122 on 2018-05-12
> **mc4man said:**
> The snap vlc may be able to access optical drives ..

Maybe it has improved then... I tried out the snap version in 17.10, it couldn't even play music CDs, let alone video dvds. It also couldn't play audio files from external hdd. Haven't tried it again since.

---

### Post by jeo7 on 2018-05-12
When VLC is run from the terminal, the following is the result:

```

$ vlc
VLC media player 3.0.1 Vetinari (revision 3.0.1-0-gec0f700fcc)
[0000563210a81570] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
[0000563210a854e0] main playlist: playlist is empty
libdvdnav: Using dvdnav version 6.0.0
libdvdnav: DVD Title: THE_LAST_JEDI
libdvdnav: DVD Serial Number: 4C423C0B
libdvdnav: DVD Title (Alternative): THE_LAST_JEDI
libdvdnav: DVD disk reports itself with Region mask 0x00f60000. Regions: 1 4

libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient

libdvdread: Get key for /VIDEO_TS/VIDEO_TS.VOB at 0x0002285c
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x00022a7b
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_0.VOB at 0x00022b55
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_1.VOB at 0x00022e4c
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_0.VOB at 0x00022e64
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_1.VOB at 0x00022e7c
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_04_0.VOB at 0x00022ea6
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_04_1.VOB at 0x00044802
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_05_0.VOB at 0x00044827
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_05_1.VOB at 0x00044836
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_06_1.VOB at 0x00044ad6
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_07_1.VOB at 0x00044b28
libdvdread: Elapsed time 0
libdvdread: Found 7 VTS's
libdvdread: Elapsed time 0
Segmentation fault (core dumped)

```

---

### Post by mc4man on 2018-05-12
> **monkeybrain20122 said:**
> Maybe it has improved then... I tried out the snap version in 17.10, it couldn't even play music CDs, let alone video dvds. It also couldn't play audio files from external hdd. Haven't tried it again since.
Yeah, it's improved but the strict confinement & lack of transparency for some snaps are nothing I'm interested in myself.
The so-so vetting is ripe for malware, the main reason for confinement.., though confinement doesn't mean safe.

---

### Post by jeo7 on 2018-05-14
Thanks all for your help, but i got so sick of solving one problem after another and playing whack-a-mole that I removed Ubuntu 18.04 and replaced it with Linux Mint. I'm happy with Linux Mint because it got all the drivers and codecs correct from the start. No more screen flickering. No more problems playing DVDs with VLC. No more hesitating video with Totem and mp4s. It just works.

I'm not done with Ubuntu 18.04. I will put it on another computer with an Intel processor and NVIDIA graphics which I understand are better supported in Ubuntu than my AMD processor with AMD Radeon graphics. It's just a shame that I put myself and you guys through so much trouble. 

Thanks again! I really do appreciate it.

---

