---
title: "Mythbuntu 9.04 codec+conversion-problem"
date: 2010-05-31
forum: Mythbuntu
---

### Post by new_tolinux on 2010-05-31
Hi,

Yesterday I installed Mythbuntu 9.04 on an old PC (1.6Ghz/640MB ram).
I did try 9.10, but both recording and live-tv failed, so therefore it became 9.04. Maybe 10.04 is another option in a few months, but I rather keep away from it untill the major bugs are fixed (probably at least 2 months from now).

I did set mpeg4 as the video codec to use and MP3 as the audio codec, but in my logs I find:
NVR(/dev/video0):Unknown video codec. Please go into the TV Settings, Recording Profiles and setup the four 'Software Encoders' profiles. Assuming RTjpeg for now.
NVR(/dev/video0) Error: Unknown audio codec

The card is a PCTV Rave (detected as VL4 / Pinnacle PCTV Stereo (saa7134)). The card is working: I can watch LiveTV, I can watch my recordings and I have sound.

I don't know what RTjpeg's quality is like compared to MPEG2 or MPEG4, so if the quality is better RTjpeg's fine with me.
Only problem I have is that I can't do anything with .nuv and I know that I can edit .avi-files and how to do it.

I tried lots of things, the last one was mythnuv2mkv to convert it to xvid but after running for many hours that leaves me only with a bunch of errors and an .avi-SUSPECT file instead of something I can use.

How to get that computer producing the highest quality possible:
In Windows 2000 I had (in Mythbuntu I have) : 
* resolution 768x576 (640x480)
* raw DSVD MPEG2-files (.nuv)

I like to have things working, because the only annoying thing in windows was that I was unable to schedule and was unable to program channels, so I had to have a list with channel-freqs and I had to start the recording manually. That's something Mythbuntu does perfectly, but since I'm unable to use anything I record outside mythbuntu it's also pretty useless.

Some additional information:
used commandline:
```
mythnuv2mkv.sh --contype=avi,xvid --quality=576 --pass=two  --copydir=/home/tv/Video/ --chanid=1060 --starttime=20100529015500  --outputchecks=NOSIZE,NOVIDINFO,NOSIZERATIO,NOFRAMECOUNT,NOSCAN
```Output  of mythnuv2mkv:
```
ERROR 1054 (42S22) at line 1: Unknown column 'subtitle' in 'field  list'
01/06,14:08 [20934] START Checking  /var/lib/mythtv/recordings/1060_20100529015500.avi.
01/06,14:08 [20934] INFO Checking output size.
01/06,14:08 [20934] INFO Checking output video info.
01/06,14:08 [20934] INFO Checking input/output size ratio.
01/06,14:08 [20934] INFO Checking input/output frame count.
01/06,14:11 [20934] INFO Input frames 104962  /var/lib/mythtv/recordings/1060_20100529015500.nuv.
01/06,14:11 [20934] INFO Output frames 104960  /var/lib/mythtv/recordings/1060_20100529015500.avi.
01/06,14:11 [20934] INFO Scanning output for errors. (Takes a long time)
01/06,14:33 [20934] ERROR mplayer error count too great (86037 > 8)  on /var/lib/mythtv/recordings/1060_20100529015500.avi.
01/06,14:33 [20934] INFO You can change the error limit variable  MPLAYER_ERROR_COUNT at top of script or
01/06,14:33 [20934] INFO The check can be disabled with  --outputchecks=NOSCAN
01/06,14:33 [20934] ERROR  /var/lib/mythtv/recordings/1060_20100529015500.avi may be faulty. Saved  as /var/lib/mythtv/recordings/1060_20100529015500.avi-SUSPECT.  /var/lib/mythtv/recordings/1060_20100529015500.nuv kept.
--------------------------------------------------------------------------------
01/06,14:33 [20934] INFO Output checks set to  NOSIZE,NOVIDINFO,NOSIZERATIO,NOFRAMECOUNT,NOSCAN.
01/06,14:33 [20934] INFO Exiting. Errored.
ERROR 1054 (42S22) at line 1: Unknown column 'subtitle' in 'field  list'
```

---

### Post by new_tolinux on 2010-06-02
bump

---

### Post by new_tolinux on 2010-06-03
After some tweaking I'm a bit further.
I now can produce .avi-SUSPECT files with mythnuv2mkv that I can actually edit, but the errors remain.

Because they're .avi-SUSPECT, they are still named channel_starttime.avi-SUSPECT and are still in the /var/lib/mythv/recordings/ folder instead of the output-folder I specified.
The moving part is something I can do with a script, but I can't manage to rename them properly with a script.

---

### Post by new_tolinux on 2010-07-06
I'm giving up waiting for a solution, so although it's not solved I mark it as solved.

It all works, well, at least more or less.
Not perfect, but not too much of a hassle either.

---

### Post by klc5555 on 2010-07-06
Mythbuntu doesn't necessarily by default include all the codecs you need out-of-the-box.

In addition to installing the restricted codecs from the mythbuntu control center, it sounds as though you may not have the faac package installed to support mpeg4 encoding. You may also be missing the libavifile package that gives you .avi support.

---

### Post by new_tolinux on 2010-07-06
It does produce avi's through mythnuv2mkv, which if I'm correct is a very big script to get mythconv working.

On the other hand, I have another computer here (almost same specs, but 1.5Gb memory instead of 600Mb), and I'm thinking of swapping the disks and the card to that computer. Since it's got another motherboard I guess a reinstall will be needed.
I guess I'll try 10.4 on it first, since it's out for a few months yet, and if that doesn't work (like 9.10 here) I can always put the 9.04 CD in the drive again.
Maybe that will also solve some problems, since 9.04 is probably a bit out-dated.

---

