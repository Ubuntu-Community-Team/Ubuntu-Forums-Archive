---
title: "menCODER Audio Record (Xbox 360)"
date: 2010-06-03
forum: Multimedia Software
---

### Post by Jake007g on 2010-06-03
So I've gotten pretty nice quality video capturing my Xbox 360 through easyCAP, but I've spent the last 4 days (About 10 hours) trying to get the audio to record. Also, I cannot seem to get it to record in my specified dimensions or FPS. Here is my current menCODER .sh script:

> mencoder tv:// -tv device=/dev/video0:input=1:norm=PAL-60:adevice=/dev/audio1:audiorate=48000:amode=1:forceaudio -vf pp=md:fps=60:mpeg4:width=1920: height=1080 -o Recording -ovc lavc -lavcopts vcodec=mpeg4:vbitrate=8000:aspect=16/9 -oac mp3lame -lameopts cbr:br=128

I am using Ubuntu (Studio) 10.04, and I'm from Europe so PAL is my TV standard. 

Most importantly, what I would like to know is, how to find which 'device' (/dev/audio etc) my easyCAP's audio is linked to, or if that isn't the problem with my script, how I can get the audio to record.

Also if possible, all though I'm not that bothered about this part, how I could get menCODER to actually record my footage in 1920x1080 @ 60fps (It currently records in 720x480 @ 29.97 FPS for some reason).

Many thanks in advance, from your friendly Ubuntu noob 

-Jake :)

---

### Post by Jake007g on 2010-06-03
Off to bed, would appreciate it if someone could reply by the time I'll be waking up :D

---

### Post by Jake007g on 2010-06-04
Bump

---

### Post by Jake007g on 2010-06-06
Please if ANYBODY knows anything that might help me work it out, please reply!

I really want to get the sound working so I can start making videos for my YouTube channel again!

---

### Post by Jake007g on 2010-06-07
I'm so desperate for help with this!

---

### Post by Breambutt on 2010-06-07
Wait, what is this easyCAP you speak of? I only found a cheap S-Video USB thingie via Google and ranted away:

720x480 @ 29.97 is the NTSC standard for analog TV. There's no point in recording 1920x1080 @ 60 as it would only be scaled to a horrid mess from 720x480 anyway, not to mention it would require pretty hardcore hardware and a fast hard drive RAID array or a Raptor.

S-Video / composite isn't capable of such thing, so basically you'd have to go component (1080i) or HDMI and those interfaces will cost exclusively over $200.

And last but definitely the least, AFAIK Suxbox games are 1280x720 native so recording them with anything above that would be pointless.

As for the audio capture, I suppose you just have line-in muted or something if it has an USB connector and a separate audio cable on the PC end. I don't think those things are supposed to act as individual audio devices.

---

### Post by Jake007g on 2010-06-07
Ok, thanks for the help. I've scaled down the dimensions/fps to 720x480@29.97, I'll have a play around with my audio settings and see what I can come up with.

---

