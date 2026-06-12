---
title: "Matroska freezes"
date: 2007-07-16
forum: Multimedia &amp; Video
---

### Post by xlinuks on 2007-07-16
Hi
I have a few matroska (.mkv) files of 2.2 GB each and when playing them with any player (VLC, kaffeine) the playback freezes every few milliseconds, as if the video were 10 frames/sec (in fact it has about 23 frames/sec, 1280x720). I don't have problems with any other video format though.
The VLC player shows that for every 3000 blocks about  500 frames are lost..

I have Ubuntu FF, 3.4Ghz pentium, 2GB ram, Nvidia 7600GT 256MB RAM. I have installed all the codecs I have found in add/remove applications section.

Has anybody any tips?

---

### Post by pgroudas on 2007-07-16
Is the video encoded h264?  x264 decoding of hi-definition video is extremely cpu intensive and can bring even faster cpu's to their knees, although I'm not sure thats the case for you (3.4 ghz is pretty fast), but it could be that it's the cpu's older architecture (I'm assuming here your's is a pentium 4?) that is causing the problem.  

If the video is divx or xvid, then I have no idea what the problem could be.

---

### Post by kostkon on 2007-07-16
Do your* VLC* or *Kaffeine* use the **Xv** extension? You need to use it in order to get* motion compensation hardware  accelerated video playback*. Also, you need to use the *nvidia* driver in order the motion compensation to work, I  think; I am not sure if the open source driver *nv* supports it.

---

### Post by pgroudas on 2007-07-16
> **kostkon said:**
> Do your* VLC* or *Kaffeine* use the **Xv** extension? You need to use it in order to get* motion compensation hardware  accelerated video playback*. Also, you need to use the *nvidia* driver in order the motion compensation to work, I  think; I am not sure if the open source driver *nv* supports it.

As far as I know, hardware acceleration is only enabled for mpeg-2 video for nvidia cards under linux.

---

### Post by xlinuks on 2007-07-17
Thanks all who have replied, I've been frustrated so I deleted those movies (before I saw your posts).
I will mark your tips and try them out next time I come across such a file. As to my CPU here what the Ubuntu Sysinfo program says:
Vendor: GenuineIntel
CPUs: 2   //this is weird, I have ONE CPU
Model Name: Intel(R) Pentium(R) D CPU 3.40GHz
Frequency: 2400.000 MHz
L2 cache: 2048 KB
Bogomips: 6799.16 (have no clue what it means)
Numbering: family(15) model(6) stepping(4)
Flags: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc pni monitor ds_cpl est cid cx16 xtpr lahf_lm

The system ram type is DDR II 6400 (if that matters)

---

