---
title: "Mythtv .23 opinions"
date: 2010-04-12
forum: Mythbuntu
---

### Post by williammanda on 2010-04-12
I was looking for people that have installed mythtv .23 to get their feedback of the changes and additions. Some of the changes / additions I have an interest in are:
1. Snappier frontend - does this address the delay after mythtv has been idle?
2. New mcc plugins - is there more than the MythNetvision? Also what do you think about the MythNetvision plugin?
3. Arclight Theme
4. 15% faster software H.264 decoder
5. Add support for 2.35:1 aspect ratio override - if I understand this correctly, you should be able to zoom in to fill the screen.
Thanks

---

### Post by SiHa on 2010-04-12
> **williammanda said:**
> 
1. Snappier frontend - does this address the delay after mythtv has been idle?


Please, God I hope so...

---

### Post by My Name on 2010-04-13
I had it on my acer revo and it was VERY unstable. I did however like the internet video plugin and the fact that mythweather works in the UK again. Apart from that, I see little difference and I have removed it for now until it is a bit more established. I wife on maternity leave that can't watch telly because something has screwed up is not a pretty site...

---

### Post by theRealGBee on 2010-04-13
> **My Name said:**
> I had it on my acer revo and it was VERY unstable.

It sounds like you or the packagers messed up the install/compile. 0.23 is considerably more stable than 0.22. There have been a few people installing 0.23 without cleaning out the old libraries from their system which was causing major instability, but that was a case of user error.

---

### Post by AKADAP on 2010-04-14
I am having trouble with things that are much more basic than you are asking questions about.

1) Analog tuners DO NOT WORK.
2) I must run "sudo /etc/init.d/alsa-utils restart" nearly every time, or the digital pass through only sends silence on SPDIF.
3) HDTV drops frames on a high end system with a high end ATI card with the ATI proprietary drivers even though the CPU usage is near zero. (seems to work better with the OS drivers.) Screen resolution is 2560x1600.
4) Changing channels the first time during live TV causes a long blank screen that eventually dumps me back into the main menu, restarting live TV successfully displays the channel.
5) Once past the first channel change abort, if you change channels too many times, MythTV front end will crash.
6) Commercial skipping quite often skips large chunks of the program.

---

### Post by iamlindoro on 2010-04-14
> **AKADAP said:**
> I am having trouble with things that are much more basic than you are asking questions about.

1) Analog tuners DO NOT WORK.

Odd, they work well here-- sure that you're not just having a driver problem?  Can you be more specific?  If you feel it's a bug, have you opened one?

> **AKADAP said:**
> 2) I must run "sudo /etc/init.d/alsa-utils restart" nearly every time, or the digital pass through only sends silence on SPDIF.

This seems a deeper issue with Ubuntu 10.04, I have seen that even after processes are killed, they will hold the sound node.  I have to kill the flash player and banshee constantly, even though they are not visible on the screen any more.

> **AKADAP said:**
> 3) HDTV drops frames on a high end system with a high end ATI card with the ATI proprietary drivers even though the CPU usage is near zero. (seems to work better with the OS drivers.) Screen resolution is 2560x1600.

This seems like a playback profile issue.  Are you using "Slim" as your playback profile?  If you're not, you ought to be.

> **AKADAP said:**
> 4) Changing channels the first time during live TV causes a long blank screen that eventually dumps me back into the main menu, restarting live TV successfully displays the channel.

What do your backend logs say?

> **AKADAP said:**
> 5) Once past the first channel change abort, if you change channels too many times, MythTV front end will crash.

Do you have backtraces?  Have you opened a ticket?

> **AKADAP said:**
> 6) Commercial skipping quite often skips large chunks of the program.

This is why auto-skip is off by default :).  Certain channel's broadcast methods make commercial skip a hit or miss affair.

---

### Post by iamlindoro on 2010-04-14
> **williammanda said:**
> I was looking for people that have installed mythtv .23 to get their feedback of the changes and additions. Some of the changes / additions I have an interest in are:
1. Snappier frontend - does this address the delay after mythtv has been idle?
2. New mcc plugins - is there more than the MythNetvision? Also what do you think about the MythNetvision plugin?
3. Arclight Theme
4. 15% faster software H.264 decoder
5. Add support for 2.35:1 aspect ratio override - if I understand this correctly, you should be able to zoom in to fill the screen.
Thanks

1) Yes, the mysql timeout thing has been cleared up.  The frontend should be more or less the same speed as in .22 otherwise, aside from new features the UI is largely the same.  There are some speedups in the loading of and moving around in the Watch Recordings screen.

2) MCC plugins I couldn't tell you about.  MythNetvision is the only new Myth plugin.

3) Abstain.

4) This is a huge deal and accomplished by the latest ffmpeg sync.  The glory goes to the ffmpeg devs but the improvement is real (irrelevant if you're using VDPAU, this is software decode).

5) This is an aspect ratio override, not a zoom mode.  This is a way to tell the video player that your screen is 2.35:1.  Almost nobody's is so it shouldn't be relevant for much of anybody.

---

### Post by AKADAP on 2010-04-14
> **iamlindoro said:**
> Odd, they work well here-- sure that you're not just having a driver problem?  Can you be more specific?  If you feel it's a bug, have you opened one?


This one may be about to be fixed, see this thread:[http://www.mythtvtalk.com/forum/general/13034-no-livetv-nor-recording-0-23-fixes-23820-ubuntu-10-04-beta-2-a.html](http://www.mythtvtalk.com/forum/general/13034-no-livetv-nor-recording-0-23-fixes-23820-ubuntu-10-04-beta-2-a.html)
It appears that someone cast a pointer into an int which works on 32 bit systems, but not on 64 bit systems.
> 

This seems like a playback profile issue.  Are you using "Slim" as your playback profile?  If you're not, you ought to be.


No, any profile that does not include "openGL" on the ATI proprietary driver causes tearing, which is more annoying than dropped frames.
I'm using custom with rendering done with "Standard" Decoder, "openGL" renderer, and "Greedy High Motion" deinterlacer. 
This works fine on about half of the versions that are released via the daily builds, so about every other day, this works without dropping frames, on other days, video is jerky.
> 

What do your backend logs say?


When this occurs, I get a message box with the text: "Error opening jump program file buffer".
This seems to occur when changing from a standard definition channel to a High Definition channel.
This is a log of one of the failures.
```
2010-04-14 17:04:48.271 MainServer::ANN Playback
2010-04-14 17:04:48.276 adding: Compromise as a client (events: 0)
2010-04-14 17:04:48.278 MainServer::ANN Monitor
2010-04-14 17:04:48.285 adding: Compromise as a client (events: 1)
2010-04-14 17:05:03.221 MainServer::ANN Playback
2010-04-14 17:05:03.224 adding: Compromise as a client (events: 0)
2010-04-14 17:05:03.227 TVRec(1): Changing from None to WatchingLiveTV
2010-04-14 17:05:03.235 TVRec(1): HW Tuner: 1->1
2010-04-14 17:05:03.269 AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 14 min
2010-04-14 17:05:03.298 ProgramInfo(): Updated pathname '':'' -> '1009_20100414170503.mpg'
2010-04-14 17:05:03.329 ProgramInfo(): Updated pathname '':'' -> '1009_20100414170503.mpg'
2010-04-14 17:05:03.462 ProgramInfo(): Updated pathname '':'' -> '1009_20100414170503.mpg'
2010-04-14 17:05:03.516 ProgramInfo(): Updated pathname '':'' -> '1009_20100414170503.mpg'
2010-04-14 17:05:03.571 ProgramInfo(): Updated pathname '':'' -> '1009_20100414170503.mpg'
2010-04-14 17:05:03.894 ProgramInfo(): Updated pathname '':'' -> '1009_20100414170503.mpg'
2010-04-14 17:05:03.897 Finished recording MysteryQuest "Return of the Amityville Horror": channel 1009
2010-04-14 17:05:03.903 recording already exists...
2010-04-14 17:05:03.911 ProgramInfo(): Updated pathname '':'' -> '1009_20100414170503.mpg'
2010-04-14 17:05:03.916 ProgramInfo(): Updated pathname '':'' -> '1009_20100414170503.mpg'
2010-04-14 17:05:03.918 Finished recording MysteryQuest "Return of the Amityville Horror": channel 1009
2010-04-14 17:05:03.922 ProgramInfo(1009_20100414170503.mpg), Warning: MarkAsInUse(false, 'recorder'->'') -- use has changed since first setting as in use.
2010-04-14 17:05:03.932 ProgramInfo(1009_20100414170503.mpg), Warning: MarkAsInUse requires a key to delete in use mark
2010-04-14 17:05:03.934 ProgramInfo(): Updated pathname '':'' -> '1009_20100414170504.mpg'
2010-04-14 17:05:03.969 AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 14 min
2010-04-14 17:05:03.977 ProgramInfo(): Updated pathname '':'' -> '1009_20100414170503.mpg'
2010-04-14 17:05:03.979 ProgramInfo(): Updated pathname '':'' -> '1009_20100414170504.mpg'
2010-04-14 17:05:03.988 ProgramInfo(): Updated pathname '':'' -> '1009_20100414170503.mpg'
2010-04-14 17:05:03.990 ProgramInfo(): Updated pathname '':'' -> '1009_20100414170504.mpg'
2010-04-14 17:05:06.108 RecBase(1:/dev/dvb/adapter0/frontend0): GetKeyframePositions(1,9223372036854775807,#1) out of 2
2010-04-14 17:05:06.170 RecBase(1:/dev/dvb/adapter0/frontend0): GetKeyframePositions(1,9223372036854775807,#1) out of 2
2010-04-14 17:05:12.680 TVRec(1): HW Tuner: 1->1
2010-04-14 17:05:12.880 ProgramInfo(): Updated pathname '':'' -> '1009_20100414170504.mpg'
2010-04-14 17:05:12.884 ProgramInfo(): Updated pathname '':'' -> '1009_20100414170504.mpg'
2010-04-14 17:05:12.886 Finished recording MysteryQuest "Return of the Amityville Horror": channel 1009
2010-04-14 17:05:12.926 mythbackend version: branches/release-0-23-fixes [24120] www.mythtv.org
2010-04-14 17:05:12.934 Using runtime prefix = /usr
2010-04-14 17:05:12.935 Using configuration directory = /home/mythtv/.mythtv
2010-04-14 17:05:12.937 Empty LocalHostName.
2010-04-14 17:05:12.938 Using localhost value of Compromise
2010-04-14 17:05:12.944 New DB connection, total: 1
2010-04-14 17:05:12.948 Connected to database 'mythconverg' at host: localhost
2010-04-14 17:05:12.949 Closing DB connection named 'DBManager0'
2010-04-14 17:05:12.952 Connected to database 'mythconverg' at host: localhost
2010-04-14 17:05:12.956 Current MythTV Schema Version (DBSchemaVer): 1254
2010-04-14 17:05:12.959 ProgramInfo(): Updated pathname '':'' -> '1009_20100414170504.mpg'
2010-04-14 17:05:13.112 AFD: Opened codec 0x246f8b0, id(MPEG2VIDEO) type(Video)
2010-04-14 17:05:13.113 AFD: codec AC3 has 2 channels
2010-04-14 17:05:13.115 AFD: Opened codec 0x2473890, id(AC3) type(Audio)
2010-04-14 17:05:13.138 Preview: Grabbed preview '/var/lib/mythtv/recordings/1009_20100414170504.mpg' 528x480@484s
2010-04-14 17:05:13.167 AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 14 min
2010-04-14 17:05:13.175 ProgramInfo(): Updated pathname '':'' -> '1111_20100414170512.mpg'
2010-04-14 17:05:13.180 ProgramInfo(): Updated pathname '':'' -> '1009_20100414170504.mpg'
2010-04-14 17:05:13.189 ~MythContext waiting for threads to exit.
2010-04-14 17:05:13.217 RecBase(1:/dev/dvb/adapter0/frontend0): GetKeyframePositions(238,9223372036854775807,#0) out of 9
2010-04-14 17:05:13.220 ProgramInfo(): Updated pathname '':'' -> '1111_20100414170512.mpg'
2010-04-14 17:05:13.226 ProgramInfo(): Updated pathname '':'' -> '1009_20100414170504.mpg'
2010-04-14 17:05:14.829 ProgramInfo(): Updated pathname '':'' -> '1111_20100414170512.mpg'
2010-04-14 17:05:14.832 Finished recording NBC11 News: The Bay Area at 5: channel 1111
2010-04-14 17:05:14.840 ProgramInfo(): Updated pathname '':'' -> '1111_20100414170512.mpg'
2010-04-14 17:05:14.847 ProgramInfo(): Updated pathname '':'' -> '1111_20100414170512.mpg'
2010-04-14 17:05:14.850 Finished recording NBC11 News: The Bay Area at 5: channel 1111
2010-04-14 17:05:14.854 ProgramInfo(1111_20100414170512.mpg), Warning: MarkAsInUse(false, 'recorder'->'') -- use has changed since first setting as in use.
2010-04-14 17:05:14.862 ProgramInfo(1111_20100414170512.mpg), Warning: MarkAsInUse requires a key to delete in use mark
2010-04-14 17:05:14.867 ProgramInfo(): Updated pathname '':'' -> '1111_20100414170514.mpg'
2010-04-14 17:05:14.872 AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 14 min
2010-04-14 17:05:14.886 ProgramInfo(): Updated pathname '':'' -> '1111_20100414170512.mpg'
2010-04-14 17:05:14.889 ProgramInfo(): Updated pathname '':'' -> '1111_20100414170514.mpg'
2010-04-14 17:05:14.928 ProgramInfo(): Updated pathname '':'' -> '1111_20100414170512.mpg'
2010-04-14 17:05:14.932 ProgramInfo(): Updated pathname '':'' -> '1111_20100414170514.mpg'
2010-04-14 17:05:21.558 ProgramInfo(): Updated pathname '':'' -> '1111_20100414170514.mpg'
2010-04-14 17:05:21.560 TVRec(1): Changing from WatchingLiveTV to None
2010-04-14 17:05:21.564 ProgramInfo(1111_20100414170514.mpg), Error: Unknown type, recording width was 0
2010-04-14 17:05:21.744 ProgramInfo(): Updated pathname '':'' -> '1111_20100414170514.mpg'
2010-04-14 17:05:21.747 Finished recording NBC11 News: The Bay Area at 5: channel 1111
2010-04-14 17:05:21.794 ProgramInfo(): Updated pathname '':'' -> '1111_20100414170514.mpg'
2010-04-14 17:05:21.807 MainServer::ANN Playback
2010-04-14 17:05:21.815 adding: Compromise as a client (events: 0)
2010-04-14 17:05:21.817 TVRec(1): Changing from None to WatchingLiveTV
2010-04-14 17:05:21.824 TVRec(1): HW Tuner: 1->1
2010-04-14 17:05:21.857 AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 14 min
2010-04-14 17:05:21.885 ProgramInfo(): Updated pathname '':'' -> '1111_20100414170521.mpg'
2010-04-14 17:05:21.908 ProgramInfo(): Updated pathname '':'' -> '1111_20100414170521.mpg'
2010-04-14 17:05:21.912 ProgramInfo(): Updated pathname '':'' -> '1111_20100414170514.mpg'
2010-04-14 17:05:21.920 ProgramInfo(): Updated pathname '':'' -> '1111_20100414170521.mpg'
2010-04-14 17:05:21.924 TVRec(1): Changing from WatchingLiveTV to None
2010-04-14 17:05:22.126 ProgramInfo(): Updated pathname '':'' -> '1111_20100414170521.mpg'
2010-04-14 17:05:22.129 Finished recording NBC11 News: The Bay Area at 5: channel 1111
2010-04-14 17:05:22.183 ProgramInfo(): Updated pathname '':'' -> '1111_20100414170521.mpg'
2010-04-14 17:05:26.906 ProgramInfo(): Updated pathname '':'' -> '1111_20100414170521.mpg'
```
> 

Do you have backtraces?  Have you opened a ticket?


I don't know how to do a "backtrace", I don't channel surf too often, so no, I have not opened a ticket on this one.
> 

This is why auto-skip is off by default :).  Certain channel's broadcast methods make commercial skip a hit or miss affair.

  This problem will probably always exist. It could be greatly improved if I could set it up so that it would show the first second of the commercial break so I could tell for sure that it actually was a commercial. I have set it up to show the last second of the commercial break, but there is no option to have it show both the first second and the last second.
  To go along with this, some keyboard command to go back to the beginning of the skipped section and play through it would be helpful when I catch it making a mistake.
  Currently when I catch it making a mistake, I MUST turn off commercial skipping to be able to view the part of the program that was mistakenly flagged as a commercial.

---

### Post by iamlindoro on 2010-04-14
> **AKADAP said:**
> This one may be about to be fixed, see this thread:[http://www.mythtvtalk.com/forum/general/13034-no-livetv-nor-recording-0-23-fixes-23820-ubuntu-10-04-beta-2-a.html](http://www.mythtvtalk.com/forum/general/13034-no-livetv-nor-recording-0-23-fixes-23820-ubuntu-10-04-beta-2-a.html)
It appears that someone cast a pointer into an int which works on 32 bit systems, but not on 64 bit systems.

OK, so in some cases on 64 bit systems when using RTJPEG there was an issue (That we couldn't actually reproduce).  Yes, it's fixed in .23-fixes and trunk.  It definitely wasn't "analog tuners are broken," though.  Simply swapping to MPEG-4 as your codec would have done the trick.  Moot now as it's fixed.

> **AKADAP said:**
> No, any profile that does not include "openGL" on the ATI proprietary driver causes tearing, which is more annoying than dropped frames.
I'm using custom with rendering done with "Standard" Decoder, "openGL" renderer, and "Greedy High Motion" deinterlacer. 
This works fine on about half of the versions that are released via the daily builds, so about every other day, this works without dropping frames, on other days, video is jerky.

Can *probably* mostly blame the GL quirks of the fglrx driver, but admittedly the GL renderer has been a bit neglected.  This will improve substantially for .24-25ish as we're moving to much tighter GL integration.  It is probable/possible that with Xv there is a solution to the tearing, though-- on the nVidia side it means disabling the composite extension and turning off Compiz.

> **AKADAP said:**
> When this occurs, I get a message box with the text: "Error opening jump program file buffer".
This seems to occur when changing from a standard definition channel to a High Definition channel.
This is a log of one of the failures.

No obvious smoking gun there, but I'm in the same television market as you with no LiveTV failures.  Unfortunately not all tuners behave equivalently, and I don't use any LiveTV except for testing.  Meh.


> **AKADAP said:**
> I don't know how to do a "backtrace", I don't channel surf too often, so no, I have not opened a ticket on this one.

Search the term "Debugging" on the myth wiki, that will give you ubuntu specific backtrace instructions.  We're willing to have a look if you can get a good BT and open a ticket.

---

### Post by lank23 on 2010-04-14
been using mythbuntu 10.04 with Mythtv 0.23 for couple months now, no issues sense I fix a boot order problem that was not allowing my PVR-150 to be used [http://ubuntuforums.org/showthread.php?t=1414630]("http://ubuntuforums.org/showthread.php?t=1414630").

Fire wire capture and channel changing work like a charm with Fios QIP-7100 STB if the encryption flag is not set. 

This is my set-up.

Hardware:
QIP 7100 HD
VIA Technologies, Inc. VT6306


Mythtv FireWire setup.
Mythbuntu 10.04a Mythtv 0.23
Model = DCT-6200 "seems to be the closest model to my QIP-7100"
100Mbps
Broadcast
allow FireWire reset
RingBuffer 14100

lank23

---

### Post by AKADAP on 2010-04-15
> **iamlindoro said:**
> OK, so in some cases on 64 bit systems when using RTJPEG there was an issue (That we couldn't actually reproduce).  Yes, it's fixed in .23-fixes and trunk.  It definitely wasn't "analog tuners are broken," though.  Simply swapping to MPEG-4 as your codec would have done the trick.  Moot now as it's fixed.


I'll have to try that tomorrow (myth is recording now and I don't want to interrupt it).
I have spent most of the last year attempting to get the analog tuner working, asking questions on many forums, and trying many things with no luck, but that is one thing I did not try.
> 

Can *probably* mostly blame the GL quirks of the fglrx driver, but admittedly the GL renderer has been a bit neglected.  This will improve substantially for .24-25ish as we're moving to much tighter GL integration.  It is probable/possible that with Xv there is a solution to the tearing, though-- on the nVidia side it means disabling the composite extension and turning off Compiz.


Yes the open source ATI driver works better for video, but it absolutely kills google earth.
> 

No obvious smoking gun there, but I'm in the same television market as you with no LiveTV failures.  Unfortunately not all tuners behave equivalently, and I don't use any LiveTV except for testing.  Meh.

Search the term "Debugging" on the myth wiki, that will give you ubuntu specific backtrace instructions.  We're willing to have a look if you can get a good BT and open a ticket.

I attempted to reproduce the multiple channel changes bug, and after going through all of the cable channels, then switching to by south pointing antenna and changing channels a few more times, I finally had a failure. It was exactly the same failure as the first channel change though (a message box with the text: "Error opening jump program file buffer"), not what I remembered. What I remember is the UI locking up, it stops paying attention to the keyboard, and I have to alt-tab to get to another window so I can kill the front end.

I did manage to reproduce that behavior (UI lockup) by trying to use the "e" key to edit a channel (Jade) that has recently become encrypted. I have had this lockup occur frequently when using the "e" key, so much so that I usually use Mythweb to edit channels.

Background info:
I have 5 tuners: 2 HDHomeRun boxes with 2 tuners each, and an ATI HDTV Wonder. One of the HDHomeRun tuners is on an antenna pointed northwest, another HDHomeRun is on an antenna pointed south, and the rest are on cable.

---

### Post by AKADAP on 2010-04-15
I updated to a version of MythTV that should include the fix, but that did not fix the problem with analog tuners.

---

### Post by iamlindoro on 2010-04-15
> **AKADAP said:**
> I updated to a version of MythTV that should include the fix, but that did not fix the problem with analog tuners.

What revision did you update to?

---

### Post by iamlindoro on 2010-04-15
Fix was applied in r24133.

[http://svn.mythtv.org/trac/changeset/24133/branches/release-0-23-fixes](http://svn.mythtv.org/trac/changeset/24133/branches/release-0-23-fixes)

---

### Post by AKADAP on 2010-04-15
> **iamlindoro said:**
> what revision did you update to?

24133

---

### Post by AKADAP on 2010-04-15
> **iamlindoro said:**
> Fix was applied in r24133.

[http://svn.mythtv.org/trac/changeset/24133/branches/release-0-23-fixes](http://svn.mythtv.org/trac/changeset/24133/branches/release-0-23-fixes)

The change you link to claims it was added in 24126, so I would assume so.

---

### Post by AKADAP on 2010-04-15
> **iamlindoro said:**
> Fix was applied in r24133.

[http://svn.mythtv.org/trac/changeset/24133/branches/release-0-23-fixes](http://svn.mythtv.org/trac/changeset/24133/branches/release-0-23-fixes)

Looking at that diff, I don't see how the old code could cause a problem.
I don't like what was done with the new code either.
Instead of tmp < (int)out_len, which could change out_len from positive to negative if it is large enough, I would think that (lzo_uint)tmp < out_len would be a better choice.
As far as I can tell, tmp is always zero.

But then I don't know the definition of lzo_uint, and don't know what the rest of the code looks like.

---

### Post by iamlindoro on 2010-04-15
If your issue is not resolved, the then issue you originally linked and claimed to have is not the issue you have.  You should post to the myth user's list and we'll see if we can give you some help.

---

### Post by dannyboy79 on 2010-04-16
> **AKADAP said:**
> I am having trouble with things that are much more basic than you are asking questions about.

1) Analog tuners DO NOT WORK.


what tuners do you have? i have a pvr-350 and a pvr-500, i am running
mythtv
0.23.0+fixes24098-0ubuntu0+mythbuntu2
from the mythbuntu  auto-builds repo.

the analog tuners work GREAT! the picture isn't the best, but what do you expect with an analog signal.

---

### Post by AKADAP on 2010-04-16
> **dannyboy79 said:**
> what tuners do you have? i have a pvr-350 and a pvr-500, i am running
mythtv
0.23.0+fixes24098-0ubuntu0+mythbuntu2
from the mythbuntu  auto-builds repo.

the analog tuners work GREAT! the picture isn't the best, but what do you expect with an analog signal.

It is an ATI HDTV Wonder. The digital portion of this tuner works fine, the analog portion only gives me a blank screen and silence.

I once got video (no sound) out of it via liveTV, but it has never repeated.

I just tested again, and instead of a blank screen, I got flickering garbage. At least it was different.

---

### Post by movieman on 2010-04-17
> **AKADAP said:**
> But then I don't know the definition of lzo_uint, and don't know what the rest of the code looks like.

According to another link posted here, lzo_uint is 64-bits, but the variable was defined as 32-bits, so when the called function writes through the pointer it trashes the stack.

This is why casts are a colossal source of hard to find bugs. I don't even remember the last time I wrote a cast other than to get the address of a base class of a multiply derived C++ class.

---

### Post by AKADAP on 2010-04-17
> **iamlindoro said:**
> If your issue is not resolved, the then issue you originally linked and claimed to have is not the issue you have.  You should post to the myth user's list and we'll see if we can give you some help.

Posted there two days ago, no response.

---

### Post by AKADAP on 2010-04-17
> **movieman said:**
> According to another link posted here, lzo_uint is 64-bits, but the variable was defined as 32-bits, so when the called function writes through the pointer it trashes the stack.

This is why casts are a colossal source of hard to find bugs. I don't even remember the last time I wrote a cast other than to get the address of a base class of a multiply derived C++ class.

I see, they passed a pointer to a local 32 bit int to a function that expected a pointer to a 64 bit value, so it was killing something on the stack adjacent to that local 32 bit int.

---

### Post by williammanda on 2010-04-18
Well I installed lucid beta 2 with mcc and mythbuntu beta 2 on four computers this weekend and this is what I found:

> 1. Snappier frontend - does this address the delay after mythtv has been idle?

Yes it does!

> 2. New mcc plugins - is there more than the MythNetvision? Also what do you think about the MythNetvision plugin?

I haven't tried it yet due to getting all this basic functionality working first.

> 3. Arclight Theme

Same as #2.

> 4. 15% faster software H.264 decoder

Not quite sure how to test this feature but I will once I get some HD network shows recorded.

> 5. Add support for 2.35:1 aspect ratio override - if I understand this correctly, you should be able to zoom in to fill the screen.

This was answered in an earlier response.

I did find a bug when trying to load codecs through mcc. See this post:

[http://ubuntuforums.org/showthread.php?t=1456587]("http://ubuntuforums.org/showthread.php?t=1456587")

Also the screensaver issue with both different installations is fixed.

I will post more as I progress further with my installation but this version of mythtv and mythbuntu seems much better.

---

### Post by williammanda on 2010-04-18
> 3. Arclight Theme 

I tried it and it is nice but I still perfer the mythbuntu wide theme.

---

### Post by dannyboy79 on 2010-04-18
wish there were more themes for standard box style tv's. there's only one that I can see, all others are widescreen. otherwise, LOVE IT!!!!!

---

### Post by AKADAP on 2010-05-01
> **AKADAP said:**
> Posted there two days ago, no response.

Got a response, and because of it made a bit of progress.
I have proven that the analog tuner is not broken, only the software is broken.

Per a suggestion on that mailing list:
I ran mythbackendsetup to stop the mythTV backend from running.
As super user, I ran the following script:
```
#!/bin/sh
#
# unload hdtv wonder modules
#
/sbin/modprobe -r cx8800
/sbin/modprobe -r cx88_dvb
/sbin/modprobe -r nxt200x
/usr/bin/pkill pulseaudio; /sbin/modprobe -r cx88_alsa
/sbin/modprobe -r tuner
/sbin/modprobe -r tuner_simple
/sbin/modprobe -r tuner_types
/sbin/modprobe -r tda9887
/sbin/modprobe -r tda8290
#
# reload hdtv wonder modules
#
/sbin/modprobe cx88_dvb
/sbin/modprobe cx8800 video_nr=1 vbi_nr=1
/sbin/modprobe cx88_alsa index=1

```
Then I ran:
```

mplayer tv://32 -tv device=/dev/video1:driver=v4l2:chanlist=us-cable:alsa:adevice=hw.1,0:amode=1:audiorate=48000:forceaudio:volume=100:immediatemode=0:norm=NTSC
```

up pops a window showing video with sound!
Unfortunately, when I exited mythbackendsetup, and tried to view live TV, the analog tuner was missing.
Worse, I have since updated to Ubuntu 10.04, and now mythfrontend segmentation faults when I try to run liveTV

---

### Post by pauna on 2010-05-10
> **AKADAP said:**
> 
Worse, I have since updated to Ubuntu 10.04, and now mythfrontend segmentation faults when I try to run liveTV

Yep, I'm not too happy about Mythbuntu 10.04 and mythtv 0.23 either.

1) Putting DVD into the player caused mythfrontend to crash and drop to desktop (presumably fixed now in weekly builds, 6 days ago it was still broken).

2) Most program changes on DVB-T LiveTV crash mythbackend and thus mythfrontend drops to desktop. And I'm talking about the program changing in the same channel in the DVB-T transport stream, for example from a TV series to news.

0.22 was much more stable.

---

### Post by iamlindoro on 2010-05-10
> **pauna said:**
> Yep, I'm not too happy about Mythbuntu 10.04 and mythtv 0.23 either.

1) Putting DVD into the player caused mythfrontend to crash and drop to desktop (presumably fixed now in weekly builds, 6 days ago it was still broken).

2) Most program changes on DVB-T LiveTV crash mythbackend and thus mythfrontend drops to desktop. And I'm talking about the program changing in the same channel in the DVB-T transport stream, for example from a TV series to news.

0.22 was much more stable.


1) What weekly builds?  Auto-builds are nightly, this was fixed several weeks ago.  .23 was only officially released this morning anyway.  If you haven't gotten updates, then you're not running auto-builds.

2) Have you opened a bug with a sample and verbose logs that causes such a problem?

---

### Post by AKADAP on 2010-05-10
> **AKADAP said:**
> Worse, I have since updated to Ubuntu 10.04, and now mythfrontend segmentation faults when I try to run liveTV

I have found a workaround for this: switch to a different renderer than OpenGL.
OpenGL appears to be broken in 10.04. It also kills google earth, but I have not yet found a workaround for that.

---

### Post by pauna on 2010-05-10
> **iamlindoro said:**
> 1) What weekly builds?  Auto-builds are nightly, this was fixed several weeks ago.  .23 was only officially released this morning anyway.  If you haven't gotten updates, then you're not running auto-builds.


Sorry about the terminology, in myth 0.22 they were at some point called weekly builds? Anyway, I did go to auto-builds on the 4th of May and after applying the mythbuntu-repos.deb and updating, the DVD stuff wasn't working then. 

From the discussion in [https://bugs.launchpad.net/mythbuntu/+bug/549593](https://bugs.launchpad.net/mythbuntu/+bug/549593) I'd say there was no solution as of a couple of days ago to that problem. 

However, it is working now with the latest auto-builds.

> 
2) Have you opened a bug with a sample and verbose logs that causes such a problem?

By a sample you mean a piece of the transport stream with the issue? Getting that sample may be a bit challenging since the frontend and apparently the backend as well are crashing.

System messages show the only real error:
```

May 10 22:55:21 mythbox kernel: [ 3988.153409] mythfrontend.re[2374]: segfault at 5c ip 00007f7a612f50db sp 00007f7a3d281450 error 6 in libmythtv-0.23.so.0.23.0[7f7a60be3000+cbf000]

```

Backend log:
```

2010-05-10 22:55:19.840 Finished recording Uusi Kino: Eurooppalaisia visioita: channel 1001
2010-05-10 22:55:20.060 AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 14 min
2010-05-10 22:55:20.335 TVRec(18): RingBufferChanged()
2010-05-10 22:55:20.369 ProgramInfo(): Updated pathname '':'' -> '1001_20100510224838.mpg'
2010-05-10 22:55:20.517 ProgramInfo(): Updated pathname '':'' -> '1001_20100510224838.mpg'
2010-05-10 22:55:20.642 ProgramInfo(): Updated pathname '':'' -> '1001_20100510225518.mpg'
2010-05-10 22:55:20.725 Finished recording Uusi Kino: Eurooppalaisia visioita: channel 1001
2010-05-10 22:55:21.006 ProgramInfo(): Updated pathname '':'' -> '1001_20100510224838.mpg'
2010-05-10 22:55:27.345 mythbackend version: branches/release-0-23-fixes [24509] www.mythtv.org
2010-05-10 22:55:27.424 Using runtime prefix = /usr

```

And the frontend:
```

2010-05-10 22:55:20.171 AFD: Opened codec 0x5061990, id(MPEG2VIDEO) type(Video)
2010-05-10 22:55:20.171 AFD: codec MP3 has 0 channels
2010-05-10 22:55:20.172 AFD: Opened codec 0x2b12ae0, id(MP3) type(Audio)
2010-05-10 22:55:20.172 AFD: Opened codec 0x5098430, id(DVB_SUBTITLE) type(Subtitle)
2010-05-10 22:55:20.172 NVP(1): Disabling Audio, params(0,0,0)
2010-05-10 22:55:20.241 [mpeg2video @ 0x7f7a602bc360]mpeg_decode_postinit() failure
2010-05-10 22:55:20.241 AFD Error: Unknown decoding error
2010-05-10 22:55:20.241 [mpeg2video @ 0x7f7a602bc360]mpeg_decode_postinit() failure
2010-05-10 22:55:20.241 AFD Error: Unknown decoding error
2010-05-10 22:55:20.241 [mpeg2video @ 0x7f7a602bc360]mpeg_decode_postinit() failure
2010-05-10 22:55:20.241 AFD Error: Unknown decoding error
2010-05-10 22:55:20.242 [mpeg2video @ 0x7f7a602bc360]mpeg_decode_postinit() failure
2010-05-10 22:55:20.242 AFD Error: Unknown decoding error
2010-05-10 22:55:20.242 [mpeg2video @ 0x7f7a602bc360]mpeg_decode_postinit() failure
2010-05-10 22:55:20.242 AFD Error: Unknown decoding error
2010-05-10 22:55:20.242 [mpeg2video @ 0x7f7a602bc360]mpeg_decode_postinit() failure
2010-05-10 22:55:20.242 AFD Error: Unknown decoding error
2010-05-10 22:55:20.242 [mpeg2video @ 0x7f7a602bc360]mpeg_decode_postinit() failure
2010-05-10 22:55:20.242 AFD Error: Unknown decoding error
2010-05-10 22:55:20.242 AFD: Setting channels to 0
2010-05-10 22:55:20.286 Opening audio device 'default'. ch 2(2) sr 48000 (reenc 0)
2010-05-10 22:55:20.286 Opening ALSA audio device 'iec958:{ AES0 0x02 }'.
2010-05-10 22:55:20.386 NVP(1): Enabling Audio
2010-05-10 22:55:20.388 Opening audio device 'default'. ch 2(2) sr 48000 (reenc 0)
2010-05-10 22:55:20.389 Opening ALSA audio device 'iec958:{ AES0 0x02 }'.
2010-05-10 22:55:20.394 [mpeg2video @ 0x7f7a602bc360]mpeg_decode_postinit() failure
2010-05-10 22:55:20.394 AFD Error: Unknown decoding error
2010-05-10 22:55:20.395 [mpeg2video @ 0x7f7a602bc360]mpeg_decode_postinit() failure
2010-05-10 22:55:20.395 AFD Error: Unknown decoding error
2010-05-10 22:55:20.395 [mpeg2video @ 0x7f7a602bc360]mpeg_decode_postinit() failure
2010-05-10 22:55:20.395 AFD Error: Unknown decoding error
2010-05-10 22:55:20.395 [mpeg2video @ 0x7f7a602bc360]mpeg_decode_postinit() failure
2010-05-10 22:55:20.395 AFD Error: Unknown decoding error
Starting mythfrontend.real..
2010-05-10 23:15:08.119 mythfrontend version: branches/release-0-23-fixes [24509] www.mythtv.org
2010-05-10 23:15:08.120 Using runtime prefix = /usr

```

The 20 minute gap there is because I was investigating what had happened and did not restart mythfrontend immediately.

As for more verbose logs, I've enabled apport but it is refusing to handle the crash dump since I've got only 512 megs of memory (but loads of swap). As per discussions on IRC I now understand that this is in the low end in the current world, but I'm not quite convinced yet that low memory is crashing the MythTV.

Since apport is not working, what can I do to get more meaningful logs out of my box? I can reproduce this consistently just by keeping LiveTV running at particular times.

---

### Post by pauna on 2010-05-17
By the way, my frontend crash issue was 
[http://svn.mythtv.org/trac/ticket/8443](http://svn.mythtv.org/trac/ticket/8443) and it has now been corrected.

---

