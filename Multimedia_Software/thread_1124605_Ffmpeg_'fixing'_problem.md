---
title: "Ffmpeg 'fixing' problem"
date: 2009-04-13
forum: Multimedia Software
---

### Post by JCrue on 2009-04-13
Hey,

I'm following [https://wiki.ubuntu.com/ffmpeg](https://wiki.ubuntu.com/ffmpeg), I get to ./configure with the amr_nb and amr_wb switches, but get 

"Unknown option "--enable-amr_nb". 
See ./configure --help for available options." 

I'm on intrepid. 

Any help?

---

### Post by mc4man on 2009-04-13
ck. your ./configure --help to be sure 
atm with a *recent* ffmpeg it's
--enable-libamr-nb 
--enable-libamr-wb

(make sure you have the -dev's, libamrnb-dev, ect.

---

### Post by FakeOutdoorsman on 2009-04-13
Start out with this guide:
[HOWTO: Install and use the latest FFmpeg and x264]("http://ubuntuforums.org/showthread.php?t=786095")

You will need some additional steps to use AMR.  First install the amr development packages from the [Medibuntu](http://medibuntu.org) repository:
```
sudo apt-get install libamrnb-dev libamrwb-dev
```
Then when you configure FFmpeg (step 4 in the guide), you will need to add additional configuration options:
```
--enable-nonfree --enable-libamr-nb --enable-libamr-wb
```

---

### Post by JCrue on 2009-04-14
Ah, thanks loads :).

---

