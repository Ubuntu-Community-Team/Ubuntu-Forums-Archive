---
title: "How do people convert Blu Rays?"
date: 2010-02-07
forum: Multimedia Software
---

### Post by AmbiguousOutlier on 2010-02-07
Hello, I've just installed makeMKV and I ripped a blu-ray to a 30gb mkv file. First question has this retained the full 1080p resolution and DD 5.1?

Do people compress this further into a smaller file. I've only got 4tb of HDD space? that's a little more than a 130 films I can rip. 

Is there a program I can use to compress this file further and also control what the output file resolution and sound is?

---

### Post by solitaire on 2010-02-07
What settings are you using?

To squese a Blu-Ray down use the following settigs: 
(or tweek them till its a small file that looks good)

Codec..........: H.264
Resolution.....: 1920x1080
Bitrate........: 10.0-20.0 Mbps
Framerate......: 24fps
Audio..........: AC3 Dolby Digital 5.1CH Surround (640kbs)
Subtitles......: None
Extension......: M2TS

That gives a 1080p movie at round the 6.4Gb mark

---

### Post by Joe of loath on 2010-02-07
Sorry, have to laugh at the 'Only 4TB' bit :P

I think you can convert with FFmpeg, might take a while though. I'm afraid I don't know any GUI tool for it though.

---

### Post by AmbiguousOutlier on 2010-02-07
> **solitaire said:**
> What settings are you using?

To squese a Blu-Ray down use the following settigs: 
(or tweek them till its a small file that looks good)

Codec..........: H.264
Resolution.....: 1920x1080
Bitrate........: 10.0-20.0 Mbps
Framerate......: 24fps
Audio..........: AC3 Dolby Digital 5.1CH Surround (640kbs)
Subtitles......: None
Extension......: M2TS

That gives a 1080p movie at round the 6.4Gb mark

What are you using? makeMKV doesn't have any settings to change.

> **Joe of loath said:**
> Sorry, have to laugh at the 'Only 4TB' bit :P

I am thinking of getting one of these;

[http://www.seagate.com/blackarmor/](http://www.seagate.com/blackarmor/)

4x 2tb

---

### Post by FakeOutdoorsman on 2010-02-07
> **RhysGM said:**
> Hello, I've just installed makeMKV and I ripped a blu-ray to a 30gb mkv file. First question has this retained the full 1080p resolution and DD 5.1?

Do people compress this further into a smaller file. I've only got 4tb of HDD space? that's a little more than a 130 films I can rip. 

Is there a program I can use to compress this file further and also control what the output file resolution and sound is?

I've never heard of makeMKV, but I also recommend FFmpeg and can help you with an example command.  You want a smaller file.  Do you mean file size, or a frame size smaller than full 1080 resolution, or both?  What is the target device for your re-encoded videos (computer, phone, gaming console, web, dvd, etc)?

---

### Post by AmbiguousOutlier on 2010-02-08
> **FakeOutdoorsman said:**
> I've never heard of makeMKV, but I also recommend FFmpeg and can help you with an example command.  You want a smaller file.  Do you mean file size, or a frame size smaller than full 1080 resolution, or both?  What is the target device for your re-encoded videos (computer, phone, gaming console, web, dvd, etc)?

I want to play ripped blu-rays on my computer via XBMC live. Ideally I would like to keep 1080, and just shrink the file as much as possible without loosing too much quality. Keeping both a DD5.1/DTS and a 2 channel Audio stream. Including subtitles if possible. I would like to keep the file size to under 10gb.

---

### Post by lingenfr on 2010-10-02
I am not sure why this is [SOLVED] unless the original poster found and solution and then didn't share it. I also can use MakeMKV to rip the BR to play on my computer. I supposed I could even store them on my NAS at that size, but I would still like to be able to rip something that will play on my handheld devices. I have not found any way to do that. ffmpeg is OK if someone will share their settings. If you have one for ipod, i think that will work for any of my devices (i.e. Nokia N810, etc). Thanks.

---

### Post by Phloston on 2010-10-07
I find Handbrake very useful for compressing video files. I have never used it when the source is a MKV from MakeMKV though.

[http://handbrake.fr/](http://handbrake.fr/)

---

### Post by lingenfr on 2010-10-07
I agree. I tried HB, but could not output a usable file.

---

### Post by alphacrucis2 on 2010-10-08
Allegedly, avidemux can convert mkv to various alternative formats. I haven't tried it myself

---

### Post by lingenfr on 2010-10-11
Yes, same story as ffmpeg for me. It works, but I could not get a file that worked well with ipod and similar format devices. I would like to get down to a 700MB 320x240 (or similar) xvid or H264 and mp3 file. I either end up with a file that is huge or just doesn't work. I used trial and error and ended up with a lot of error. I just don't know enough about the options to make the right adjustments.

---

### Post by coskierken on 2010-10-13
I have used Handbrake to take a 6.4G mkv file down to an Iphone 4format of 700MB.  It plays great on the I4.  I don't do this all the time.  You can us HB to create the mkv straight from the BR, also.  I would use the 2 pass option, though.  If you try to take it too small, you will drop frames.

---

### Post by halj32 on 2010-10-13
> **Joe of loath said:**
> Sorry, have to laugh at the 'Only 4TB' bit :P

I think you can convert with FFmpeg, might take a while though. I'm afraid I don't know any GUI tool for it though.

the gui tool for ffmpeg is WinFF
works on Linux & windows

[http://winff.org/html_new/](http://winff.org/html_new/)

enjoy

---

### Post by lingenfr on 2010-10-14
> **coskierken said:**
> I have used Handbrake to take a 6.4G mkv file down to an Iphone 4format of 700MB.  It plays great on the I4.  I don't do this all the time.  You can us HB to create the mkv straight from the BR, also.  I would use the 2 pass option, though.  If you try to take it too small, you will drop frames.

Please share what settings worked for you.

---

