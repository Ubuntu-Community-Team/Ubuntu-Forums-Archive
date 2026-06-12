---
title: "Incorrect program length reported in MythTV"
date: 2010-03-30
forum: Mythbuntu
---

### Post by R3M3 on 2010-03-30
I've been having a problem with a regularly recorded program in MythTV (recorded with a Hauppauge HVR-1950 from a over-the-air ATSC source). 

The program records, but upon playback, the reported length is too short (~40 min versus 60 min). It's not that a portion got cut off, it's that the counter moves too slowly - after 10 minutes of wall-time playback, the counter says I'm only ~7 min in. In addition to that, the audio sync gets completely messed up, with people speaking before their lips start moving. 

It's just the one program - everything else records fine.  This has only started to happen in the past month or so - before that everything was fine. I have tried rebuilding the seek table for the files [(http://www.mythtv.org/wiki/Repairing_the_Seektable)]("http://www.mythtv.org/wiki/Repairing_the_Seektable") both with mythcommflag and mythtranscode, but that doesn't seem to help. I thought it might be an reception issue or something with the channel itself, but I recently recorded the program on the other sub-channel  (e.g both X.1 and X.2 at the same time) and that was reported to be the full 60 min. I also haven't noticed an issue with other programs on the same subchannel, but at different times.

Any thoughts as to the cause? (I can live with the miss-reported time, but the non-synchronized audio makes it unwatchable.)

---

### Post by SiHa on 2010-03-31
Perhaps it's being broadcast with a wierd framerate. What happens if you (maybe losslessly) transcode it and then watch?

---

### Post by JMcFly on 2010-03-31
I have noticed the same thing, programs will report ~37min length but seem to playback fun, not sped up or missing chunks.

---

### Post by R3M3 on 2010-04-02
Interesting ... If I try to transcode through the MythTV Frontend (Watch Recordings -> "i" -> Job Options -> Begin Transcoding) I either get an error, or I get a transcoded program with the same issue, depending on the profile/recording (I tested each profile, each with a different recording).

However, if I invoke mythtranscode from the command line, using the -m, -i and -o options to create a separate output .mpg file, that output file does not seem to have the same issue (when checked in Totem Movie Player - I wasn't sure how to invoke the MythTV internal player from the command line). Totem shows a *similar* error to MythTV when invoked on the original file, but instead of being too short, it's too long - 80 min for Totem, vs. 40 min for MythTV vs. 60 min actual.

Anyone have a fix? Manually invoking mythtranscode from the command line after every recording is going to be annoying, especially as I don't know how to import the generated file back into MythTV.

Oh, and since I didn't mention this before, I'm using MythTV version 0.22.0+fixes (22594) (the current version) installed over regular Ubuntu 9.10 Karmic.

---

### Post by mathog on 2010-04-02
> **JMcFly said:**
> I have noticed the same thing, programs will report ~37min length but seem to playback fun, not sped up or missing chunks.

We see this too, but only on 8:00PM shows broadcast on NBC (Mercy, Chuck) and Telemundo (a Spanish language network owned by NBC, for the show El Clon).  All of these come out at 52 minutes instead of 60.  Could be something about the way these shows are encoded.

---

### Post by iamlindoro on 2010-04-02
All durations in MythTV are estimations, this is necessarily so because (particularly on certain content, usually interlaced) it is possible to use a repeat_pict flag to make a single frame appear twice, etc.  This is a common optimization by broadcasters to reduce bandwidth needed.  Myth can only make an approximation of duration based on the number of frames and the present framerate.

---

### Post by R3M3 on 2010-04-04
> **iamlindoro said:**
> All durations in MythTV are estimations

I don't know about anyone else, but what I am experiencing is not simply an estimation issue. The reported length is not just a minute or two off, it's 30-40% off. The "advance 10 min" feature runs through the program in 4 presses, vs. 6 for other programs of the same length.

Finally, and most importantly, **the audio and video are not syncronized**. (Well, they are when you first start playing, even when you start in the middle of the recording, or fast forward/reverse to a new position, but in a minute or so they are not together anymore.)

While using mythtranscode on the command line to create a new (separate) file appears to fix the issue for the new file, invoking transcoding through the mythfrontend interface does not seem to accomplish anything, resulting in either errors or a recoding with the same problems as before.

---

### Post by admered1 on 2010-04-12
I have exactly the same issue, but with minimal audio sync issues and a huge discrepancy in displayed time vs actual time. In my case, a one hour program will claim to be around 23 minutes long and will cut off early when played. I have had success running the mythcommflag tool on the command line and using the --rebuild flag. This seems to fix all the problems.

---

### Post by FunkyProgramLength on 2010-04-24
I had the same problem. Short program length and increasing audio vs video drift.


I found a solution to the sync problem that works in the main program.

I enabled the "opengl vertical sync for timing" option and it fixed the sync issue. Program length still shows as short though.

Main menu -> utilities/setup -> setup -> TV Settings -> Playback ->Enable OpenGL vertical sync for timing.

Please post an "it worked" if this fixes it for you too.

---

### Post by R3M3 on 2010-05-04
Sorry for taking so long on the response - I had to wait until I got another recording that showed the same issue. (Computer issue meant that last weeks showing didn't record.)

> **FunkyProgramLength said:**
> I enabled the "opengl vertical sync for timing" option and it fixed the sync issue. Program length still shows as short though.

Thank you! It works! Just what I was looking for.

---

