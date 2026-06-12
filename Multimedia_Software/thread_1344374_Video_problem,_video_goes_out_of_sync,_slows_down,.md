---
title: "Video problem, video goes out of sync, slows down, and stops at times, then speeds up"
date: 2009-12-02
forum: Multimedia Software
---

### Post by psychcf on 2009-12-02
Since I've upgraded to 9.04, I've had an issue with video playback that's really annoying. I was hoping it would be fixed in 9.10 but no luck. It's probably a configuration issue.

Anyways, when I open something up in either mplayer or movie player, the audio always plays back flawlessly, but at times the video will slow down (frames aren't dropped). The video actually plays back slower, and usually slows down until it's stuck on one frame. After a few seconds it speeds up to above normal speeds, and then goes back to normal playback speed when it's in-sync with the audio.

When watching movies with subtitles, the subtitles are in sync with the video (eg, if the video slows down, the subtitles slow down with it).

This happens frequently, maybe once every 2-5 minutes.

After testing VLC for 20 minutes, I had no problems with playback.

I've got an Nvidia 8800 GT, a core 2 duo proc, and running 9.10 with compiz.

Any thoughts?

---

### Post by psychcf on 2009-12-11
bump, still having problems

---

### Post by edvar on 2009-12-15
I'm having a similar problem. Video slows down and audio playback is at normal speed. I thought it was a problem with XBMC but it also happens on MPlayer and VLC.

---

### Post by psychcf on 2009-12-15
I should also add in that I'm running 64 bit

---

### Post by edvar on 2009-12-15
I'm running Karmic i386 with the latest NVIDIA Driver (190). My graphics card is a 8800 GTS running on an old intel Core2Quad 2.4Ghz. Sound card is an onboard Intel (Intel Corporation 82801I (ICH9 Family) HD Audio Controller) connected via SPDIF ( IEC958 ) to my receiver. Sound output using Pulseaudio.

---

### Post by thegargravarr on 2010-01-17
I recently had the same problem (periodically slow video yet audio does not slow down) after upgrading to 9.10 (Karmic). I seem to have fixed the issue however:

Some people mentioned pulse audio as a culprit so I completely removed pulse audio (and associated packages) and re-installed the xvid/gstreamer codecs.

After rebooting I had no sound at all, so I re-installed pulse audio and so far have not had any problems with the video running out of sync.

I have seen some mention of rebooting fixing the issue for short periods of time so if I do have further issues i will report back.

---

### Post by BentFX on 2011-09-20
Ubuntu 10.04 amd64

I use pulseaudio and have it configured to send output back on an input channel.

I had the same, or very similar issue. Here's how I solved it...

1) Installed preempt kernel. Not certain if this is necessary, since it by itself did not solve the issue.

2) In paprefs, on the Simultaneous Output tab, uncheck "Add virtual output for simultaneous output on all local sound cards." Since I only have one sound card this is not needed.

3) In pavucontrol, on the Input Devices tab, at the bottom Show > Monitors. Click the green check mark for "Monitor of Internal Audio Analog Stereo."

I think the "Monitor of Internal Analog Stereo" item may be named differently depending on your sound card. Anyhow, I think, at least in my case, it was the "simultaneous output" option in paprefs that was causing the problem.

I enjoy a good puzzle, and audio in Ubuntu is like a Rubik's Cube, except there are fewer correct solutions.

---

