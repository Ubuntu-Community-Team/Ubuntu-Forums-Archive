---
title: "One channel being odd"
date: 2008-09-12
forum: Mythbuntu
---

### Post by lionsnob on 2008-09-12
Hi all,

I live near Detroit, and recordings of WXYZ (ABC) from the ATSC transmission are very choppy (audio cuts out, causes the picture to briefly slow-motion itself).  Other channels are fine, regardless of being 720p or 1080i.  From the log it looks like an audio issue (see below).  Both of my frontends experience the problem.  One is passing PCM via SPDIF and the other is bitstreaming the AC3.  Has anyone seen this before?  Is there an audio setting that I can adjust to stop this?

```
2008-09-12 15:21:29.903 XMLParse::LoadTheme using /usr/share/mythtv/themes/Mythbuntu-8.04-wide/ui.xml
2008-09-12 15:21:31.909 AFD: Opened codec 0x8346f50, id(MPEG2VIDEO) type(Video)
2008-09-12 15:21:31.909 AFD: codec AC3 has 6 channels
2008-09-12 15:21:31.910 AFD: Opened codec 0x83111d0, id(AC3) type(Audio)
2008-09-12 15:21:31.910 AFD: codec AC3 has 2 channels
2008-09-12 15:21:31.911 AFD: Opened codec 0x855f810, id(AC3) type(Audio)
2008-09-12 15:21:32.003 [mpeg2video @ 0xb73ffa88]qscale == 0
2008-09-12 15:21:32.003 [mpeg2video @ 0xb73ffa88]Warning MVs not available
2008-09-12 15:21:32.572 AFD: Opened codec 0x8830a40, id(MPEG2VIDEO) type(Video)
2008-09-12 15:21:32.572 AFD: codec AC3 has 6 channels
2008-09-12 15:21:32.573 AFD: Opened codec 0x84faa80, id(AC3) type(Audio)
2008-09-12 15:21:32.573 AFD: codec AC3 has 2 channels
2008-09-12 15:21:32.574 AFD: Opened codec 0x82e0130, id(AC3) type(Audio)
2008-09-12 15:21:33.763 [mpeg2video @ 0xb73ffa88]ac-tex damaged at 56 22
2008-09-12 15:21:33.763 [mpeg2video @ 0xb73ffa88]Warning MVs not available
2008-09-12 15:21:33.789 TV: Attempting to change from None to WatchingPreRecorded
2008-09-12 15:21:33.892 DPMS Deactivated 
2008-09-12 15:21:34.075 AFD: Opened codec 0x8346f50, id(MPEG2VIDEO) type(Video)
2008-09-12 15:21:34.076 AFD: codec AC3 has 6 channels
2008-09-12 15:21:34.077 AFD: Opened codec 0x83111d0, id(AC3) type(Audio)
2008-09-12 15:21:34.077 AFD: codec AC3 has 2 channels
2008-09-12 15:21:34.077 AFD: Opened codec 0x831e9a0, id(AC3) type(Audio)
2008-09-12 15:21:34.081 Opening audio device 'spdif'. ch 2(2) sr 48000
2008-09-12 15:21:34.081 Opening ALSA audio device 'spdif'.
ALSA lib control.c:909:(snd_ctl_open_noupdate) Invalid CTL /dev/mixer
2008-09-12 15:21:34.100 AudioOutput Warning: Mixer attach error -2: No such file or directory
			Check Mixer Name in Setup: '/dev/mixer'
2008-09-12 15:21:34.230 VideoOutputXv: XVideo Adaptor Name: 'NV17 Video Texture'
2008-09-12 15:21:34.319 OSD Theme Dimensions W: 640 H: 480
2008-09-12 15:21:34.509 TV: Changing from None to WatchingPreRecorded
2008-09-12 15:21:34.516 Realtime priority would require SUID as root.
2008-09-12 15:21:34.612 Video sync method can't support double framerate (refresh rate too low for bob deint)
2008-09-12 15:21:34.613 Video timing method: USleep with busy wait
2008-09-12 15:21:34.626 NVP::AddAudioData():p1: Audio buffer overflow, audio data lost!
2008-09-12 15:21:34.626 NVP::AddAudioData():p1: Audio buffer overflow, audio data lost!
2008-09-12 15:21:34.627 NVP::AddAudioData():p1: Audio buffer overflow, audio data lost!
2008-09-12 15:21:34.627 NVP::AddAudioData():p1: Audio buffer overflow, audio data lost!
2008-09-12 15:21:34.628 NVP::AddAudioData():p1: Audio buffer overflow, audio data lost!
2008-09-12 15:21:34.628 NVP::AddAudioData():p1: Audio buffer overflow, audio data lost!
2008-09-12 15:21:34.629 NVP::AddAudioData():p1: Audio buffer overflow, audio data lost!
2008-09-12 15:21:34.629 NVP::AddAudioData():p1: Audio buffer overflow, audio data lost!
2008-09-12 15:21:34.630 NVP::AddAudioData():p1: Audio buffer overflow, audio data lost!
2008-09-12 15:21:34.630 NVP::AddAudioData():p1: Audio buffer overflow, audio data lost!
2008-09-12 15:21:34.630 NVP::AddAudioData():p1: Audio buffer overflow, audio data lost!
2008-09-12 15:21:34.631 NVP::AddAudioData():p1: Audio buffer overflow, audio data lost!
2008-09-12 15:21:34.632 NVP::AddAudioData():p1: Audio buffer overflow, audio data lost!
2008-09-12 15:21:34.632 NVP::AddAudioData():p1: Audio buffer overflow, audio data lost!
2008-09-12 15:21:34.632 NVP::AddAudioData():p1: Audio buffer overflow, audio data lost!
2008-09-12 15:21:34.633 NVP::AddAudioData():p1: Audio buffer overflow, audio data lost!
2008-09-12 15:21:34.633 NVP::AddAudioData():p1: Audio buffer overflow, audio data lost!
2008-09-12 15:21:34.634 NVP::AddAudioData():p1: Audio buffer overflow, audio data lost!
2008-09-12 15:21:34.634 NVP::AddAudioData():p1: Audio buffer overflow, audio data lost!
2008-09-12 15:21:34.635 NVP::AddAudioData():p1: Audio buffer overflow, audio data lost!
2008-09-12 15:21:34.635 NVP::AddAudioData():p1: Audio buffer overflow, audio data lost!
2008-09-12 15:21:34.636 NVP::AddAudioData():p1: Audio buffer overflow, audio data lost!
2008-09-12 15:21:34.636 NVP::AddAudioData():p1: Audio buffer overflow, audio data lost!
2008-09-12 15:21:34.639 NVP::AddAudioData():p1: Audio buffer overflow, audio data lost!
2008-09-12 15:21:34.684 NVP::AddAudioData():p1: Audio buffer overflow, audio data lost!
2008-09-12 15:21:34.753 NVP::AddAudioData():p1: Audio buffer overflow, audio data lost!
2008-09-12 15:21:35.760 WriteAudio: buffer underrun
2008-09-12 15:21:35.770 WriteAudio: buffer underrun
2008-09-12 15:21:35.777 WriteAudio: buffer underrun
2008-09-12 15:21:36.799 WriteAudio: buffer underrun
2008-09-12 15:21:38.232 WriteAudio: buffer underrun
2008-09-12 15:21:39.698 WriteAudio: buffer underrun
2008-09-12 15:21:41.167 WriteAudio: buffer underrun
2008-09-12 15:21:42.636 WriteAudio: buffer underrun
2008-09-12 15:21:44.069 WriteAudio: buffer underrun
2008-09-12 15:21:45.572 WriteAudio: buffer underrun
2008-09-12 15:21:47.090 WriteAudio: buffer underrun
2008-09-12 15:21:48.488 TV: Attempting to change from WatchingPreRecorded to None
2008-09-12 15:21:48.559 TV: Changing from WatchingPreRecorded to None
2008-09-12 15:21:48.618 DPMS Reactivated.
2008-09-12 15:21:48.828 AFD: Opened codec 0x970a2f0, id(MPEG2VIDEO) type(Video)
2008-09-12 15:21:48.828 AFD: codec AC3 has 6 channels
2008-09-12 15:21:48.829 AFD: Opened codec 0x8323960, id(AC3) type(Audio)
2008-09-12 15:21:48.829 AFD: codec AC3 has 2 channels
2008-09-12 15:21:48.830 AFD: Opened codec 0x836a130, id(AC3) type(Audio)
2008-09-12 15:21:48.910 [mpeg2video @ 0xb73ffa88]qscale == 0
2008-09-12 15:21:48.910 [mpeg2video @ 0xb73ffa88]Warning MVs not available
2008-09-12 15:21:49.375 AFD: Opened codec 0x8323960, id(MPEG2VIDEO) type(Video)
2008-09-12 15:21:49.375 AFD: codec AC3 has 6 channels
2008-09-12 15:21:49.376 AFD: Opened codec 0x855ee80, id(AC3) type(Audio)
2008-09-12 15:21:49.376 AFD: codec AC3 has 2 channels
2008-09-12 15:21:49.377 AFD: Opened codec 0x8306660, id(AC3) type(Audio)
2008-09-12 15:21:50.370 AFD: Opened codec 0x8323960, id(MPEG2VIDEO) type(Video)
2008-09-12 15:21:50.370 AFD: codec AC3 has 6 channels
2008-09-12 15:21:50.371 AFD: Opened codec 0x8306660, id(AC3) type(Audio)
2008-09-12 15:21:50.371 AFD: codec AC3 has 2 channels
2008-09-12 15:21:50.372 AFD: Opened codec 0x836e350, id(AC3) type(Audio)
```

---

### Post by emillan on 2008-10-13
Did you ever figure this one out?  I'm in the exact same situation. I'm running a fully up-to-date Mythbuntu 8.04 system.  Everything works great except primetime programming on the local ABC affiliate. (A syndicated show which ran during late night was just fine.)

Searching reveals others with the same or similar problem, but no solution yet.

If push comes to shove, I'll try transcoding the programs on that channel and see if that might make them watchable.  And maybe, just maybe 8.10 might come to the rescue...

---

### Post by SiHa on 2008-10-14
There's a checkbox 'Enable aggressive audio buffering' in the general (I think) setup menu in Mythfrontend. 

Have you tried that?

---

### Post by emillan on 2008-10-15
> **SiHa said:**
> There's a checkbox 'Enable aggressive audio buffering' in the general (I think) setup menu in Mythfrontend. 

Have you tried that?

I did, and the problem is present either way.

I tried transcoding the program into one with MP3 audio (to get away from what appears to be an AC3 problem) and the problem persisted.

I may try playing around with the playback profiles or transcoding another way.

Or maybe I'll take a deep breath and upgrade to the 8.10 beta.

---

### Post by lionsnob on 2008-10-29
I did figure it out.  Apparently the signal was too STRONG for my pcHDTV 5500 to handle.  I split the signal and the channel was fine, but others started to degrade.  I hope that after 8.10 comes out to install two 800i cards I have lying around.  The new kernel in 8.10 supports the 800i and the 800i supposedly has better tuning hardware built in.

---

### Post by discoverpc on 2008-11-30
for me the issue is that once it goes into a commercial it get this error
"Audio buffer overflow, audio data lost!"

going to try a dedicated audio card to see if the issue goes away.

---

### Post by emillan on 2008-12-01
I've been meaning to post a follow-up to this for awhile now.

I did upgrade to 8.10 and the problem persists.

My situation appears to be that ABC is the only station broadcasting a 5.1 audio track with the others broadcasting stereo. The 5.1 provokes the problem on my system.

It seems to be a known issue fixed in Myth 0.22 and backported to 0.21, but hasn't yet made it into a Mythbuntu distribution.  I'm hoping this fix will become available once the weekly builds for Intrepid/8.10 become available.

Some links:

[http://svn.mythtv.org/trac/ticket/5313](http://svn.mythtv.org/trac/ticket/5313)
[http://www.acetylcholine.com/phpbb/viewtopic.php?p=251857](http://www.acetylcholine.com/phpbb/viewtopic.php?p=251857)

---

### Post by emillan on 2008-12-01
One last bit: Until a better fix comes along, I can play my "problem" recordings with VLC and they play perfectly.

---

### Post by dmfrey on 2008-12-01
i have noticed this as well.  Is it possible to setup a special player command on just this channel to always use vlc when playing this channel live, or a recording from this channel?  I am thinking along the lines of a video stored under mythvideo where you can specify a unique player command when editing an individual video?  Is something like that possible?

(I hope that I am not mis-interpreting that video edit screen, but i am not at home to confirm it :) )

---

### Post by emillan on 2008-12-01
> **dmfrey said:**
> Is it possible to setup a special player command on just this channel to always use vlc when playing this channel live, or a recording from this channel?  ...

There's no sanctioned way I know of (which isn't saying all that much), but I was thinking about making a "Play with VLC" user job.  If that didn't pan out, I might try using Mythrename ([http://www.mythtv.org/wiki/index.php/Mythrename.pl](http://www.mythtv.org/wiki/index.php/Mythrename.pl)) to rename the recordings so that they're easier to find in VLC.

---

### Post by dmfrey on 2008-12-02
> **emillan said:**
> There's no sanctioned way I know of (which isn't saying all that much), but I was thinking about making a "Play with VLC" user job.  If that didn't pan out, I might try using Mythrename ([http://www.mythtv.org/wiki/index.php/Mythrename.pl](http://www.mythtv.org/wiki/index.php/Mythrename.pl)) to rename the recordings so that they're easier to find in VLC.

That was actually my next thought :)
This, I feel, is going to be causing me some more issues now that I have my pcHDTV card setup.  I find some channels have audio, others don't.  It is no longer just one channel.  I have noticed that Fox and ABC in my area give me the same issues (beautiful picture, no sound).

---

### Post by uncle hammy on 2008-12-02
I have the same problem with an ABC affiliate here in Grand Rapids.  My issue is the video runs at about 1.5 speed, and is always ahead of the audio...until a commercial, which runs fine, then it starts all over again when the show restarts.  It is present on both live and recorded shows (HD only).  I happen to have 2 ABC affiliates available, so I just stoppped using this one.

I actually posted about it [http://ubuntuforums.org/showthread.php?t=932926](http://ubuntuforums.org/showthread.php?t=932926)

However, using Settings>TV>Playback>Enable Open GL For Video Timing fixes the issue for me.  I also had to use XvMC when I had this setting enabled, because I had bad tearing otherwise, regardless of the combinations of VBlank I set in the NVidia settings.  

A further note, I installed 8.10 on one of my frontends (the only one I'm able to), and the 177 series NVidia drivers allowed me to use OpenGL timing without XVmc, with no tearing.

Hope that helps.

---

### Post by emillan on 2008-12-02
> **uncle hammy said:**
> However, using Settings>TV>Playback>Enable Open GL For Video Timing fixes the issue for me.

It's definitely better with this setting on.  Thanks a bunch for pointing it out.

There's still some weirdness about--the odd times mentioned in the other thread and the occasional instances where the video goes extra fast for a brief instance--but now the audio and video are in synch and so it's very watchable now where before it wasn't.  Thanks again!

---

### Post by dmfrey on 2008-12-03
> **uncle hammy said:**
> I have the same problem with an ABC affiliate here in Grand Rapids.  My issue is the video runs at about 1.5 speed, and is always ahead of the audio...until a commercial, which runs fine, then it starts all over again when the show restarts.  It is present on both live and recorded shows (HD only).  I happen to have 2 ABC affiliates available, so I just stoppped using this one.

I actually posted about it [http://ubuntuforums.org/showthread.php?t=932926](http://ubuntuforums.org/showthread.php?t=932926)

However, using Settings>TV>Playback>Enable Open GL For Video Timing fixes the issue for me.  I also had to use XvMC when I had this setting enabled, because I had bad tearing otherwise, regardless of the combinations of VBlank I set in the NVidia settings.  

A further note, I installed 8.10 on one of my frontends (the only one I'm able to), and the 177 series NVidia drivers allowed me to use OpenGL timing without XVmc, with no tearing.

Hope that helps.

I am almost there.  I get some that work and some that don't.  I will try vlc on the ones that don't.  But it is definitely better than it was.

---

