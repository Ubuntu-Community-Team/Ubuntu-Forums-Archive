---
title: "Speed up video"
date: 2011-04-20
forum: Multimedia Software
---

### Post by Fibonacci on 2011-04-20
Hello.

I have a video file in which the audio runs faster than the video, so they quickly go out of sync.
The way to fix it would be to separate the audio and video streams, speed up the video (the audio is FINE, it's the video that's wrong), and then recombining them.

What is the easiest way for doing that?

---

### Post by oracle2b on 2011-04-20
Are you talking about reencoding the video to sync the playback or do you you want to just sync the audio just for playback? you can use VlC or SMplayer to sync audio playback. 

**VLC**:
MENU-> Tools -> Track Syncronization.
Advance audio over video

**Smplayer**:
Menu -> Play -> Speed -> *choose whatever suits you*

or 

Menu -> Audio -> -/+ audio delay

or 

-/+ key to delay or speedup audio playback.

I'm not sure how to reencode for synced playback.

---

### Post by Joe of loath on 2011-04-20
In VLC, you fiddle with the sync, then simply click 'save as'.

---

### Post by alphacrucis2 on 2011-04-20
> **Joe of loath said:**
> In VLC, you fiddle with the sync, then simply click 'save as'.

The trouble is the VLC sync just assumes a fixed offset I think. You can advance or delay but it wouldn't help correct a problem where the video and audio are replaying at different speeds, which is how I interpreted the OP's problem. AFAIK it would require recoding the video as that is the bit that is wrong. Some sort of video editing software would be necessary

---

### Post by Fibonacci on 2011-04-20
> **oracle2b said:**
> Are you talking about reencoding the video to sync the playback or do you you want to just sync the audio just for playback? you can use VlC or SMplayer to sync audio playback. 

**VLC**:
MENU-> Tools -> Track Syncronization.
Advance audio over video

**Smplayer**:
Menu -> Play -> Speed -> *choose whatever suits you*

or 

Menu -> Audio -> -/+ audio delay

or 

-/+ key to delay or speedup audio playback.

I'm not sure how to reencode for synced playback.

> **alphacrucis2 said:**
> The trouble is the VLC sync just assumes a fixed offset I think. You can advance or delay but it wouldn't help correct a problem where the video and audio are replaying at different speeds, which is how I interpreted the OP's problem. AFAIK it would require recoding the video as that is the bit that is wrong. Some sort of video editing software would be necessary

Exactly, and the same goes for MPlayer. I said the audio runs faster that the video, not that it starts later.

---

### Post by SeijiSensei on 2011-04-20
> **Fibonacci said:**
> What is the easiest way for doing that?

There isn't an "easy" way to do this.  What kind of file and what audio and video codecs?  If they're in the Matroska container (.mkv), try installing [mkvtoolnix]("http://www.bunkus.org/videotools/mkvtoolnix/") from the repositories to disassemble the streams.  How you change the timings is beyond my ken, though.  If it's in some other container like AVI or WMV, you might be able to use mencoder or ffmpeg for this.

---

### Post by Fibonacci on 2011-04-20
> **SeijiSensei said:**
> There isn't an "easy" way to do this.  What kind of file and what audio and video codecs?  If they're in the Matroska container (.mkv), try installing [mkvtoolnix]("http://www.bunkus.org/videotools/mkvtoolnix/") from the repositories to disassemble the streams.  How you change the timings is beyond my ken, though.  If it's in some other container like AVI or WMV, you might be able to use mencoder or ffmpeg for this.

It's an FLV container, and I have already kinda figured out how to separate the audio and video.
I'm still trying to find out how to speed the video up and how to recombine the files.

---

### Post by FakeOutdoorsman on 2011-04-21
You can use mkvmerge, part of mkvtoolnix that SeijiSensei mentioned, to delay or stretch individual streams. mkvmerge also has a GUI available too.

Another, more complicated option that I could think of is to use FFmpeg with the *setpts* filter to change the speed of the video to fit your audio or use SoX to manipulate the audio to fit the video.

---

