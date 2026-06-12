---
title: "Trim &amp; Concatenate AVI clips from my Powershot 630a"
date: 2008-07-13
forum: Multimedia Software
---

### Post by ionFreeman on 2008-07-13
That's really all I want to do. I want to take off the bit where people say 'action' at the beginning, and stick the files all together. I may develop fancier needs later, but that would be enough.

I have WinFF (I've successfully transferred these clips to my iPod) and Cinelerra. Cinelerra will occasionally play a clip, but usually does something uninterpretable. Concatenating clips hasn't been working at all. Cinelerra's huge problem, though, is that it feels the audio is too loud. I can't find a way to fix that -- the application seems to add noise, just to make the point that each clip was recorded too loud. It sounds acceptable in VLC.

I heard kino was much easier to use, so I went and got it. However! It'll only work on raw video files. So, now I want to convert my avi files to raw video files. This is my current problem -- my goal is just to get these things trimmed and concatenated.

So, WinFF asks me a lot of questions I don't know the answers to. And, since I get unplayable files out the other end, some of them must be key. How do I find out the answers to these questions?

Video Bitrate:
Frame Rate: 30
Video Size: 640 x 480
Aspect Ratio: 4:3 (I got this by dividing the previous numbers by 120 and sticking a colon in between them. I'm suspicious that the computer doesn't feel up to integer division)
Audio Bitrate:
Sample Rate: 
AC':

So... what bitrates and sample rate should I use? What does AC' even mean? What's its value?

Help!

---

### Post by Vivaldi Gloria on 2008-07-14
Give avidemux a try. Very easy to use.

---

### Post by ionFreeman on 2008-07-22
Kino suddenly started noticing avi files. I'm not sure what changed -- I already had ffmpeg, as I already had winFF. But, that worked great.

---

