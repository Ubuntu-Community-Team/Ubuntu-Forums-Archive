---
title: "Why is the MythBuntu AMD64 version sooo slow?"
date: 2011-09-18
forum: Mythbuntu
---

### Post by SpareTimeGizmos on 2011-09-18
I have an Acer Revo R1600 (230 Atom CPU, NVIDIA ION graphics) that I want to set up as a front end only system. If I install the AMD64 version of MythBuntu 10.04 then playback is choppy and breaks up. The mythfrontend.real process is using about 105% of the CPU and the Xserver is using about 75%. 
 
But if I boot the i386 version of Mythbuntu 10.04 from CD on the exact same hardware and play the exact same video from the same backend, the playback is beautiful and the total CPU utilization for front end + X server combined is only about 40%.
 
In both cases I'm playing a standard def, 480i, video and yes, I am using the NVidia restricted drivers. And yes, I tried the trick of adding "UseEvents" "True" to xorg.conf - it made no difference.
 
What am I doing wrong with the 64bit version?

---

### Post by LowSky on 2011-09-18
is vdpau enabled... sounds like it isn't

---

### Post by SpareTimeGizmos on 2011-09-18
> **LowSky said:**
> is vdpau enabled... sounds like it isn't
 
Hey, thanks. For the record I went to 
[INDENT]*Utilities/Setup -> Setup -> TV Settings -> Playback -> Playback Profiles *
[/INDENT]and picked *VDPAU Normal.*
 
That does make a difference - the video actually plays smoothly now with no skips. The CPU usage for the X server has dropped to about 1% (!!), however the mythfrontend is still running 100%+. 
 
Even still, the AMD64 version still uses more than twice the CPU to play the same video as the i386 version. What gives? That seems completely backward, not to mention that it means I'll have to redo my installation to use the i386 version :(

---

### Post by ian dobson on 2011-09-19
Hi,

There must be something very funny with your config.

My underclocked (1.2GHz) e5200 only hits about 10-15% load when playing back 1080p videos. Check if the open-gl is enabled or not. Also have a look in the mythfrontend log file, maybe there could be a hint to what is wrong.

Regards
Ian Dobson

---

### Post by SpareTimeGizmos on 2011-09-19
> **ian dobson said:**
> Hi,
 
There must be something very funny with your config.
 

 
FWIW, I did a little more fooling around and made an interesting discovery.
 
A little background - I have two program sources on my Myth backend. One is a HDHomeRun box that receives OTA broadcasts and clear QAM programs from Comcast (Comcast doesn't have many clear QAM programs anymore, but that's another story). The other source is a WinPVR USB2 capture device connected to a Comcast cable box to capture encrypted QAM programs. *The WinPVR has a built in, hardware, MPEG encoder. *The HDHR does to, in effect, since it receives digital content directly and never decodes it. Mythbackend just captures the MPEG data in whatever format the source provides; it doesn't transcode it.
 
I discovered that programs recoded from the HDHR play back with about 10% CPU utilization in Mythfrontend, where as programs recoded from the PVRUSB2 play back with about 110% CPU utilization! So there's something about the format of the PVRUSB MPEG data that makes Mythbackend really busy.
 
Doing an ffmpeg -i on a file recorded by the HDHR shows 
[INDENT]Stream #0.0[0xa00]: Video: mpeg2video, yuv420p, 528x480 [PAR 40:33 DAR 4:3], 15000 kb/s, 29.97 tbr, 90k tbn, 59.94 tbc
Stream #0.1[0xa01](eng): Audio: ac3, 48000 Hz, stereo, s16, 128 kb/s
[/INDENT]these are the files that play "fast", with low CPU overhead.
 
Files recorded by the PVRUSB2 are
[INDENT]Stream #0.0[0x1e0]: Video: mpeg2video, yuv420p, 480x480 [PAR 4:3 DAR 4:3], 6000 kb/s, 29.97 tbr, 90k tbn, 59.94 tbc
Stream #0.1[0x1c0]: Audio: mp2, 32000 Hz, stereo, s16, 384 kb/s
 
[/INDENT]It's probably obvious to everyone but me, but how come the files encoded in the PVRUSB2 format take sooo much more CPU time to play?

---

### Post by SpareTimeGizmos on 2011-09-19
> **SpareTimeGizmos said:**
> Stream #0.1[0x1c0]: Audio: mp2, 32000 Hz, stereo, s16, 384 kb/s
Just for fun, I used ffmpeg to transcode the audio on one of these recordings to AC3 format, 48kHz 128kbps. Didn't change the video at all ("-vcodec copy") ... You guessed it - the result plays great, with a CPU utilization of about 10%.
 
So something about playing MP2 audio is really, really expensive in Mythtv. Is it supposed to be like that?
 
Yes, I could just set up an automatic transcoding job in Mythbackend to convert all my PVRUSB2 recordings, but I'd like to understand what's going on. Better yet, I'd like to know if there's a way to get MP2s to play faster.

---

### Post by SpareTimeGizmos on 2011-09-19
> **SpareTimeGizmos said:**
> So something about playing MP2 audio is really, really expensive in Mythtv. 
 
One more followup - I tried playing both versions (AC3 audio and MP2 audio) with mplayer, and both play comparably with about 14% CPU utilization.
 
So there's something funky going on in MythPlayer....

---

### Post by nickrout on 2011-09-19
> **SpareTimeGizmos said:**
> One more followup - I tried playing both versions (AC3 audio and MP2 audio) with mplayer, and both play comparably with about 14% CPU utilization.
 
So there's something funky going on in MythPlayer....

In which case you need to be looking at your logs and/or filing a bug.

---

### Post by ian dobson on 2011-09-20
Hi,

What audio output are you using (Over HDMI?)

Check your audio options in the frontend, Maybe you've got some strange/conflicting options set. 

Also have a look in the frontend log (/var/log/mythtv/mythfrontend.log), myth is usually quite talkative and quite often gives "clues" as to what is wrong.

Regards
Ian Dobson

---

### Post by tobiz on 2011-09-21
I'm running an AMD64 mythbuntu 8.10 (see signature) for nearly 2 years now and have never had any problems with it being slow, and I'm not using VDPAU either. There must be a problem with your setup.

---

### Post by SpareTimeGizmos on 2011-09-22
To follow up - I don't really have a solution as such, but I've narrowed down the problem to the resampling that ALSA does to convert the 32kHz audio to 48kHz. If I play the MP2 sound directly to the analog output then I can avoid the resampling and don't have the overhead.
 
Unfortunately I *do* want to use HDMI audio and my TV doesn't understand 32kHz sampling, so it has to be resampled to 48kHz. Also, if you want to use the mixed-analog or mixed-digital devices for output, then you're forced to resample. By streamlining my asound.conf I've gotten it to where the overhead for playing the 32kHz audio thru HDMI is only about 40-50% of the CPU. I guess I'll just have to live with that. I find it hugely ironic that, with the ION hardware acceleration going, it takes way more CPU power to play the audio track then it does to play the video! 
 
The real problem is not the resampling itself, but the fact that it's much slower in the 64bit MythBuntu version than it is in the 32bit version. My guess would be that somebody compiled or linked some ALSA module in the 64 bit distro with the wrong options. I don't know for sure, though, and at this point I've already wasted too much time figuring this out.
 
FWIW, this is with the 10.04LTS version. If you're using a different one (like the 8.04 somebody mentioned) then obviously your results will be different.
 
Thanks for all the suggestions.

---

### Post by ian dobson on 2011-09-23
Hi,

Maybe try updating your kernel to a newer version (From 11.04 maybe).

I must admit I had some performance problems with 10.04 and never found what it was. But recoding audio for some recordings would explain it.

edit: I imagine you just need to install linux-image-generic-lts-backport-natty  to get the 10.04 kernel.

Regards
Ian Dobson

---

