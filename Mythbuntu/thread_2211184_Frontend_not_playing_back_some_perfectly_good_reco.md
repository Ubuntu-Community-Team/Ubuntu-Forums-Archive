---
title: "Frontend not playing back some perfectly good recordings"
date: 2014-03-14
forum: Mythbuntu
---

### Post by yonkiman on 2014-03-14
I've had this problem for a few weeks and it hasn't gone away with frequent updating.  Myth records a show, commflags it, generates a snapshot for it, and it shows up normally in my mythfrontend.  But when I try to play it, I get "Please Wait..." for about 10 seconds, followed by the "Delete and rerecord/Delete/Save so I can watch again?" requester I get at the end of a show.  It won't play the show.  But I can find the file on my hard drive and it plays fine in Movie Player and VLC (and it's in good enough shape to commflag and make a snapshot).  A program recorded immediately after that program (same channel, no retuning) plays back fine in Myth.  Has anyone else seen this?

Ubutntu 12.04, Myth 0.27 with fixes (LP-PPA-Mythbuntu-0.27), haugphage HD-PVR (the only tuner in the system), everything worked reliably until a few weeks ago.

---

### Post by blm-ubunet on 2014-03-14
Can you try to play the problem recording file with:
mythfrontend -O FFMPEGTS=1 -v playback
or mythavtest "filename" -O FFMPEGTS=1

Do any recordings cause you problems before commflagging ?

---

### Post by yonkiman on 2014-03-15
> **blm-ubunet said:**
> Can you try to play the problem recording file with:
mythfrontend -O FFMPEGTS=1 -v playback
That worked.

> or mythavtest "filename" -O FFMPEGTS=1
That worked, too (though I had to put the filename at the end, **mythavtest -O FFMPEGTS=1 2745_20140314060000.mpg**).

> Do any recordings cause you problems before commflagging ?
Some recordings do seem to fail commflagging (though they play back OK).  That's happened for years; I haven't really pursued that...  Is that related to this?

Thanks!

---

### Post by blm-ubunet on 2014-03-15
Can you try this on a problem recording?
```
mythcommflag --rebuild --file "filename"
```
and then try playing without the FFMPEGTS override..

---

### Post by yonkiman on 2014-03-16
> **blm-ubunet said:**
> Can you try this on a problem recording?
```
mythcommflag --rebuild --file "filename"
```
and then try playing without the FFMPEGTS override..

The rebuild failed, and it still wouldn't play without the FFMPEGTS override.  mythcommflag output:
```
2014-03-16 06:56:31.573892 C  mythcommflag version: fixes/0.27 [v0.27-186-g480589a] www.mythtv.org
2014-03-16 06:56:31.573912 C  Qt version: compile: 4.8.1, runtime: 4.8.1
MythTV Commercial Flagger, building seek table for:
    The Daily Show With Jon Stewart
Rebuild started at Sun Mar 16 06:56:31 2014
No I-frames found, rewinding...
Rebuild completed at Sun Mar 16 06:56:42 2014
2014-03-16 06:56:42.062527 E  RingBuf(2745_20140314060000.mpg): Took more than 10 seconds to be allowed to read, aborting.
2014-03-16 06:56:42.062613 E  decoding error
			eno: Unknown error 541478725 (541478725)
2014-03-16 06:56:42.062706 E  AFD: av_seek_frame(ic, -1, 387056, 0) -- error
2014-03-16 06:56:42.062885 E  decoding error
			eno: Unknown error 541478725 (541478725)

```

---

### Post by blm-ubunet on 2014-03-16
The error message
> No I-frames found, rewinding.
Implies that it did not probe far enough or was incorrectly identifying keyframes..
HD-PVR uses a dodgy H264 format of widely spaced IDR & seekable I frames.
The format changes with video resolution (HD is the problem).
Do your problem recordings have a common source or video resolution?

Try to run mythcommflag with the override.

Could be related to
[https://code.mythtv.org/trac/ticket/12010](https://code.mythtv.org/trac/ticket/12010)
There is a patch attached to a post link there..

You should get some improvement by setting "start on SEQ" in BE tuner setup.
This forces the recording to start "clean". Later changes to code makes this happen for all recordings.

---

### Post by yonkiman on 2014-03-16
> **blm-ubunet said:**
> The error message implies that it did not probe far enough or was incorrectly identifying keyframes..
HD-PVR uses a dodgy H264 format of widely spaced IDR & seekable I frames.
The format changes with video resolution (HD is the problem).
Do your problem recordings have a common source or video resolution?

That's the strange thing - I only have one source (cablebox->component->HD-PVR->Myth), and the problem seems to occur randomly.  Sometimes (including the example shown) it will tune to a channel, record the first 30 minute show with the problem, but the show immediately after it (no channel change) records and plays back fine.  Commflagging has always been intermittent for me (sometimes it skips commercials on playback and sometimes it doesn't), but until recently the shows always PLAYED...

> Try to run mythcommflag with the override.
The override didn't seem to work for me - I got the same failure I had before...

> Could be related to
[https://code.mythtv.org/trac/ticket/12010](https://code.mythtv.org/trac/ticket/12010)
There is a patch attached to a post link there..
I've never tried using a patch before - would I need to recompile with the patch every time there was a FIXES update?

> 
You should get some improvement by setting "start on SEQ" in BE tuner setup.
This forces the recording to start "clean". Later changes to code makes this happen for all recordings.
I like the sound of that, but I couldn't find a tuner setup field in my BE gui or mythweb.  Where can I find "start on SEQ"?

Thanks again for all your help!

---

### Post by blm-ubunet on 2014-03-17
Assuming you are in US..
You may have one source but multiple possible channels & US broadcasters appear to change video formats at ad breaks & program transitions.
The HD-PVR always encodes the output stream at the same video format as input.

The SEQ start option might only appear for DVB type tuners..
I think it appears in 2nd screen of mythtv-setup (input connections?) on the 2nd sub-screen.

I would think you are better to not use mythcommflag, it is messing up the seektable etc & making playback problems worse.
I tried & failed to find a recent commit to 0.27+fixes that could have caused your problem.

Can you provide a 100MB clip (that must include the recording file start) ?
The best tool to make a clip is 'dd if="recording-filename" bs=512 count=200K" of=outputfile.mpg'.

---

### Post by yonkiman on 2014-03-17
> **blm-ubunet said:**
> Assuming you are in US..
Yes.

> You may have one source but multiple possible channels & US broadcasters appear to change video formats at ad breaks & program transitions.
The HD-PVR always encodes the output stream at the same video format as input.

I think I get what you're saying, but I'm not sure I understand.  The HD-PVR gets an analog component (YPbPr) signal from my cablebox.  So all the Hauppauge 1212 HD-PVR sees are the analog signals (composite hsync and vsync on the green channel) from my cablebox.  It doesn't see I-frames or B-frames or any other digital format info - it's just analog video + sync signal.  The example I'm having trouble with happens to be The Daily Show followed by The Colbert Report - they are produced on the same day by the same station and (I'm fairly certain) processed and finalized/mastered using identical hardware (the last step is likely even the same machine).  So for those two reasons I don't think it's likely to be anything digital-format-related in the incoming analog video signal path that the HD-PVR sees.

> The SEQ start option might only appear for DVB type tuners..
I think it appears in 2nd screen of mythtv-setup (input connections?) on the 2nd sub-screen.
I think you're right - I don't see it.  But as I said above, the HD-PVR doesn't see any incoming digital info (unless I'm way off base and its embedded in the sync or blanking).

> I would think you are better to not use mythcommflag, it is messing up the seektable etc & making playback problems worse.
I tried & failed to find a recent commit to 0.27+fixes that could have caused your problem.
OK, well I appreciate all the time you've spent on this.

> Can you provide a 100MB clip (that must include the recording file start) ?
The best tool to make a clip is 'dd if="recording-filename" bs=512 count=200K" of=outputfile.mpg'.

I couldn't upload the clip here, so here's a DropBox link to it:
[https://www.dropbox.com/s/nepbtcw41ga4sav/sample1.mpg](https://www.dropbox.com/s/nepbtcw41ga4sav/sample1.mpg)

Cheers,
Fred

---

### Post by blm-ubunet on 2014-03-18
Analogue video has resolution & refreshrate..it is a serial (self clocking) data stream of sorts.

The HD-PVR is an encoder not a transcoder. If your STB outputs 720p60 you get mpeg-ts stream H264 at 720p60.
The analogue video input controls the output video format.
AIUI it is common for US broadcasts to have ads at 720p60 & programs as 1080i30.

Neither of those 2 TV programs (you mention) mean anything to me..is the sample recording an example of this program transition?

If (you believe) there is no change in the analogue video signal then what causes the recording glitch?
In my corner, broadcasting is like BBC standard & has completely seamless transitions from programs & adverts, even keyframes do not necessarily occur at transitions.

The "SEQ start" is a setting that affects the way MythTV starts recording the mpeg-ts stream from HD-PVR. It is not a setting that affects HD-PVR directly.
All DVB-T(2)/S(2) tuners output mpeg-ts streams just like HD-PVR.

Result with your sample1.mpg on master (git) + my patches:
- plays fine (in Videos).
- can build seektable with mythvcommflag --rebuild --video "full path to recording".
- seeking is fast & mostly fine* (slight macroblocking)..

* seeking/keyframes in multiple international HD-PVR HD samples are not quite perfect. I think this is caused by the use of seekable I -frames. (non-exact decoder start points).

---

### Post by yonkiman on 2014-03-26
> **blm-ubunet said:**
> Analogue video has resolution & refreshrate..it is a serial (self clocking) data stream of sorts.
The HD-PVR is an encoder not a transcoder. If your STB outputs 720p60 you get mpeg-ts stream H264 at 720p60.
The analogue video input controls the output video format.
AIUI it is common for US broadcasts to have ads at 720p60 & programs as 1080i30.

Ahh...I get what you're saying now.

> Neither of those 2 TV programs (you mention) mean anything to me..is the sample recording an example of this program transition?
All I was trying to say is that the programs are virtually identical in terms of production.  But you're right - there's not necessarily any corellation between the commercial content/format.

> If (you believe) there is no change in the analogue video signal then what causes the recording glitch?
I'm sure the signal changes at commercial breaks - I thought you were talking about changes happening more often, like every time the scene changes (which is why I was confused since this is analog video).  Now that I understand what you're talking about (format changing from program to commercial to commercial, etc.)  I retract my "no change" statement.  :-)

> The "SEQ start" is a setting that affects the way MythTV starts recording the mpeg-ts stream from HD-PVR. It is not a setting that affects HD-PVR directly.
All DVB-T(2)/S(2) tuners output mpeg-ts streams just like HD-PVR.
OK

> 
Result with your sample1.mpg on master (git) + my patches:
- plays fine (in Videos).
- can build seektable with mythvcommflag --rebuild --video "full path to recording".
- seeking is fast & mostly fine* (slight macroblocking)..

* seeking/keyframes in multiple international HD-PVR HD samples are not quite perfect. I think this is caused by the use of seekable I -frames. (non-exact decoder start points).
I'm not knowledgeable at that level of detail.  But I have some new info.  My PBS (public TV) recording are already set to not flag commercials.  And one of them was behaving the same way:
 - Wouldn't play at all with MythTV launched with default settings
 - Played but "skipped around" (in an hour of video, there were about 30 sections where audio and video would skip a few seconds out of sync with each other) a bit when launched with "mythfrontend -O FFMPEGTS=1 -v playback".
So I'm thinking the digital stream is being digitzed/encoded badly - either my HD-PVR hardware has gotten flakey (seems most likely since I haven't seen anyone else complaining about this) or something's happened to the linux side of the capture/decoding.

---

### Post by yonkiman on 2014-03-26
I should clarify that the title is not correct - these actually are not "perfectly good recordings"...they have video/audio glitches they shouldn't have...

---

### Post by yonkiman on 2014-03-27
OK, I think I found the problem (time will tell).  I hadn't updated my HD-PVR firmware in some time (it used to work fine, so I didn't want to mess with it).  I was running 1.5.7.0 from July 2010, and just upgraded to the latest (1.7.1.30059 from March 2012). I have high hopes since [this faq]("http://www.mythtv.org/wiki/Hauppauge_HD-PVR#Firmware_Versions") seems to mention a problem similar to what blm-ubunet has been talking to me about: 
> Previous versions would not handle the input signal switching its resolution making it hard to use reliably in MythTV. 1.7.1 now it rides right through without exiting the recording!

Thanks again blm-ubunet!

-Fred

---

