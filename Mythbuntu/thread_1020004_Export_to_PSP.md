---
title: "Export to PSP"
date: 2008-12-23
forum: Mythbuntu
---

### Post by lingenfr on 2008-12-23
I've tried nuvexport and mythexport with no joy. Anyone got this working?

*** The solution is posted in #15.

---

### Post by rhpot1991 on 2009-03-09
> **lingenfr said:**
> I've tried nuvexport and mythexport with no joy. Anyone got this working?

What exactly is the issue?

---

### Post by lingenfr on 2009-03-14
I believe you are the mythexport expert, so I will start there. I installed mythexport from the repositories and added a user job. The user job completes but does nothing. I have checked the logs and can't find anything that points me in the right direction.

With nuvexport, I can't find one that supports aac, etc that the PSP needs.

---

### Post by rhpot1991 on 2009-03-15
> **lingenfr said:**
> I believe you are the mythexport expert, so I will start there. I installed mythexport from the repositories and added a user job. The user job completes but does nothing. I have checked the logs and can't find anything that points me in the right direction.


Lets start by finding out what version you are using, run the following:
```
dpkg -l mythexport |grep ^ii
```

---

### Post by lingenfr on 2009-03-15
> **rhpot1991 said:**
> Lets start by finding out what version you are using, run the following:
```
dpkg -l mythexport |grep ^ii
```

ii  mythexport                                 1.0.3-0ubuntu1                                       Export MythTV recording to portable media players

---

### Post by rhpot1991 on 2009-03-15
> **lingenfr said:**
> ii  mythexport                                 1.0.3-0ubuntu1                                       Export MythTV recording to portable media players

I recommend upgrading to the latest version: [http://ubuntuforums.org/showthread.php?t=1085950](http://ubuntuforums.org/showthread.php?t=1085950)

Give it another run after that, if it still is not working paste your user job in here.

---

### Post by lingenfr on 2009-03-16
Is it safe to turn on proposed, upgrade mythexport ad then turn proposed off again? I don't want to hose my backend. Thanks.

---

### Post by rhpot1991 on 2009-03-16
> **lingenfr said:**
> Is it safe to turn on proposed, upgrade mythexport ad then turn proposed off again? I don't want to hose my backend. Thanks.

Yep, just turn it on then:
```
sudo apt-get update
sudo apt-get install mythtv
```

Then turn it back off when you are done, this way it will only upgrade MythExport.

---

### Post by lingenfr on 2009-03-16
Yeah. It seems to have worked. I had a userjob for ipod and that seems to have worked. I have not loaded the file to the ipod yet, but at least it completed and plays on the PC. Unfortunately, in searching for something that works I don't have my PSP line. I am still googling. I thought that I had found a page that had two different userjobs one higher res appropriate for TV output and one lower res for watching on the PSP. I can't find that page yet. Thanks again. Once I can post a working userjob I will mark this solved.

---

### Post by rhpot1991 on 2009-03-16
> **lingenfr said:**
> Yeah. It seems to have worked. I had a userjob for ipod and that seems to have worked. I have not loaded the file to the ipod yet, but at least it completed and plays on the PC. Unfortunately, in searching for something that works I don't have my PSP line. I am still googling. I thought that I had found a page that had two different userjobs one higher res appropriate for TV output and one lower res for watching on the PSP. I can't find that page yet. Thanks again. Once I can post a working userjob I will mark this solved.

You should be able to just switch out ipod with psp (except h.264) and make sure your resolution is not larger than 480 x 272 (I believe this number is firmware dependant).  You should be able to start there and tweak it.

---

### Post by lingenfr on 2009-03-17
Not sure what you mean, except h.264. The PSP does h.264 as well. The 480x272 and 600 bitrate are probably more than I need for just watching my weekly shows on the way to work. I thought I had seen a lower res setting that was known to work. I will look at it tomorrow.

---

### Post by rhpot1991 on 2009-03-17
> **lingenfr said:**
> Not sure what you mean, except h.264. The PSP does h.264 as well. The 480x272 and 600 bitrate are probably more than I need for just watching my weekly shows on the way to work. I thought I had seen a lower res setting that was known to work. I will look at it tomorrow.

I take that back, in prior versions the h.264 ffmpeg line didn't work so I disabled it.  This has been updated in the latest release, which is still in a testing stage.

---

### Post by lingenfr on 2009-03-17
Well, this line for ipod completes:

mythexport exportdir=/var/lib/mythtv/videos/ipod starttime=%STARTTIME% chanid=%CHANID% size=320x240 aspect=4:3 audio_bitrate=192kb video_bitrate=600kb export_device=ipod export_codec=mpeg4

and this one for psp doesn't:

mythexport exportdir=/var/lib/mythtv/videos/psp starttime=%STARTTIME% chanid=%CHANID% size=320x181 aspect=16:9 audio_bitrate=128kb video_bitrate=300kb export_device=psp export_codec=mpeg4

I was trying to get down to a lower res, smaller file.

---

### Post by rhpot1991 on 2009-03-18
> **lingenfr said:**
> Well, this line for ipod completes:

mythexport exportdir=/var/lib/mythtv/videos/ipod starttime=%STARTTIME% chanid=%CHANID% size=320x240 aspect=4:3 audio_bitrate=192kb video_bitrate=600kb export_device=ipod export_codec=mpeg4

and this one for psp doesn't:

mythexport exportdir=/var/lib/mythtv/videos/psp starttime=%STARTTIME% chanid=%CHANID% size=320x181 aspect=16:9 audio_bitrate=128kb video_bitrate=300kb export_device=psp export_codec=mpeg4

I was trying to get down to a lower res, smaller file.

Here is what to do then, add "debug" to that line, then run it again.  This time it will just throw a ffmpeg line into the /var/log/mythtv/mythbackend.log file.  Take that ffmpeg line and run it, should tell you what went wrong.  Your size looks a little funny, I'm thinking that might be an issue.

---

### Post by lingenfr on 2009-03-18
OK, I got one working. Here it is:

mythexport exportdir=/var/lib/mythtv/videos/psp starttime=%STARTTIME% chanid=%CHANID% size=368x192 aspect=4:3 audio_bitrate=128kb video_bitrate=1200kb export_device=psp export_codec=h264

I renamed the resulting file with the required M4V00000.MP4 type file name.

I also played it with mplayer, used Edit->Take Screenshot and saved the file. Then I opened it with GIMP, scaled it to 160x120 and saved it as a JPG. Then I renamed it to match the video name with a THM extension.

I coped the video and my thumbnail to my PSP in /MP_ROOT/100MNV01/ and yeah.

I will continue fooling around to see if I can get reasonable quality in a smaller filesize. I will also post a working line for a high res version. Thanks for your help rhpot1991.

---

