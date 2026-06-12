---
title: "Live-TV gets stuck after a while - but playback seems to work properly"
date: 2015-10-22
forum: Mythbuntu
---

### Post by Steve666 on 2015-10-22
I am runng a recent mythtv 0.27 version. Backend and frontend are running on the same machine, data files are running via 1000 Mbit line on a NAS.
The system was working properly so far but due to a crash I had to reinstall it. Now I have the following issue:

For some reasons Live-TV gets stuck after a while 5-20 Minutes but only for the DVB-S tuner which means also always HDTV.
DVB-T live TV works without the effect (and of course there is no HDTV).
Also there is no problem to record via DVB-S and playback the recording afterwards.

I changed already the playback profile from VDPAU to standard. But it does not solve the issue.

Looking into the log file of mythfrontend, there is the following pattern:
 mythfrontend.real: mythfrontend[5051]: I Decoder ringbuffer.cpp:1164 (WaitForAvail) RingBuf(/media/mythtv/livetv/13110_20151021221535.mpg): Waited 16.0 seconds for data #012#011#011#011to become available... 19240 < 32768
 mythfrontend.real: mythfrontend[5051]: E Decoder ringbuffer.cpp:1171 (WaitForAvail) RingBuf(/media/mythtv/livetv/13110_20151021221535.mpg): Waited 16 seconds for data, aborting.
 mythfrontend.real: mythfrontend[5051]: N CoreContext mythplayer.cpp:2130 (PrebufferEnoughFrames) Player(5): Waited 158666ms for video buffers AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAP
 mythfrontend.real: mythfrontend[5051]: E CoreContext mythplayer.cpp:2153 (PrebufferEnoughFrames) Player(5): Waited too long for decoder to fill video buffers. Exiting..

looking into the forum, there were issues with such log entries a few years ago but the conclusions are rather vague and some a refering to issues that should have been fixed in the meantime.

Any idea where the issue could be?

---

### Post by Steve666 on 2015-10-26
I am driving crazy. Since the issue appeared I made several tests.
It is still the case that the video gets stuck after a few minutes.
I tried to pause for a minute but it still appears.
Strange enough it always works if I record the LiveTV and play it directly afterwards with a distance of 30 seconds.
But I understood that LiveTV is doing actually the same thing as well.
I changed the frame buffer size but it still did not help.
There is something strange in the code which makes still the difference between LiveTV and a recorded mpeg.

Hope that someone else has either the same issue or has figured out what could be the resolution.

---

### Post by Steve666 on 2015-10-27
Further testing:
I changed the livetv folder to a local ssd drive and the issue did not appear after an hour of live-TV watching.
Thus I thought that there is a performance problem compared to the NAS connected via a GB line.
But measuring the read/write performance showed me that the NAS works with 45-70 MB/s which should be enough if I am not wrong.
Then I checked the rights setting of the NAS folders. There was a slight difference to the one on the local ssd since the "s" flag was not set for the mythtv folders so that mythtv created files with its own mythtv-user's group id which was not defined on the NAS.
Thus I changed it so that new files are now created with the owner and group id's defined by the folder. Even though I still get once a while the video buffer entries in the log file, mythfrontend is now not getting stuck at least after some tests.
Not sure if this was the cause now since the rights settings should have worked before due to the correct owner settings of the files but maybe I did not understand a detail with the group id setting in case the group is not defined.

I'll keep the thread still open until I am sure that the issue is not happening again.

---

### Post by Steve666 on 2015-10-27
unfortunatly the problem appeared again... not sure what I still can test, mabye it is a sound issue since I observed also some lines in the log about "ALSA: snd_pcm_info_get_card: Operation not permitted".
Any idea is still welcome.

---

### Post by Steve666 on 2015-10-30
looks the issue is related to the performance of the storage for the LiveTV folder.
I switched back the folder to a local SSD and it runs now for a couple of days well.
Interesting  is that I used previous mythtv releases with a NAS. In the past with  transfer rates of about 20 MB/s, nowadays with 45 to 70 MB/s.
Maybe  someone from the coding side can judge what was changed inside the  software that those transfer rates are not sufficient anymore and that  we need much faster rates now.

---

