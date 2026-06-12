---
title: "SimpleScreenRecorder audio"
date: 2017-08-19
forum: Multimedia Software
---

### Post by RobGoss on 2017-08-19
Hello everyone, I was hoping someone has some insight on how to get this working, I'm trying to record using SimpleScreenRecorder and I am unable to hear any audio, this is the message I receive when I use SCP 


 Megssage I receive:

Videos requires to install plugins to play media files of the following type: MPEG-4 AAC decoder 


Question? Does SimpleScreenRecorder also record your voice audio when using it if your using a headset?


Thanks so much all

---

### Post by TheFu on 2017-08-19
SSR can record whatever audio input you have setup to be recorded.  That is controlled by ALSA or Pulse Audio settings.  Also, it is easier/better to use vorbis for audio than proprietary AAC.

If you intent to make screencasts, an external USB mic is really worth the price.  Get a Yeti or at least a Samson mic. They do make a difference.  Having a little sound chamber would be helpful too.  I've tried a highly rated Plantronics USB headset and a logitech gaming headset, but found the audio recording from it to worse than the built in mic on my laptop. The samson has a built-in monitor port. I don't own a Yeti, but _everyone_ says they are the best for the price for screencasting.

---

### Post by RobGoss on 2017-08-19
Thanks Thefu, Yes I have a number of USB mics including a Audio technica, but my question is I can't hear any audio after using SSR not sure why


WHat does this mean?, Videos requires to install plugins to play media files of the following type: MPEG-4 AAC decoder

---

### Post by TheFu on 2017-08-19
Pulse audio.  Unless you are running Lubuntu, which uses ALSA directly.

Pulse Audio dies on my whenever I change the output or inputs from 1 program to another.  Before firefox stopped supporting ALSA, I would just purge pulse-audio and manually configure ALSA. Sound worked perfectly then.

Now I have a script that restarts pulse whenever I notice it isn't working.  Yesterday, had to run that script about 10 times.

The DE we run seems to be extremely important for audio.  I don't run any DE, so that could be why pulse sucks.

---

### Post by RobGoss on 2017-08-19
OK after playing around with a few settings with my  **Audio Technica,** microphone and making sure all the inputs and outputs, were correct. I then decided to check the** SSR **software it self, I notice at the **Audio:** section it was set to **Vorbis** file type, I've never even use anything like this so I just viewed the list and selected the MP3. Everything seems to be working now and sounds GREAT

I also notice there was no **MP4** selection from the options not sure why

**See attached below**

Thanks so much for the tips Thefu much appreciated have a wonderful weekend until next time

---

### Post by TheFu on 2017-08-19
vorbis is what webm uses.  It is the F/LOSS, multi-channel, audio format after ogg.  It fits more detail into the same bitrates than any other popular audio codec that is lossy.  Obviously, lossless audio formats will have more detail.  Basically, vorbis is a replacement for mp3, AAC, DTS, AC3, ogg that is included in all the browsers made since there aren't any patents tying it down.  I don't know of any HW playback devices that do not support vorbis audio which have been made in the last 5 yrs.

[https://lifehacker.com/5927052/whats-the-difference-between-all-these-audio-formats-and-which-one-should-i-use](https://lifehacker.com/5927052/whats-the-difference-between-all-these-audio-formats-and-which-one-should-i-use) has an old take on these things.

OTOH, if you want good enough audio, then mp3 is fine.

My settings for SSR on a chromebook (core i3) are h.264/superfast video with 128bit vorbis for audio put into an mkv container.  That is about the same quality as 192Kbps MP3.  I have pulse audio selected as the audio input and usually record the entire screen at 10 fps for video.  For a screencast, 10fps is fine and really saves storage.  If I need higher frame rates, I use a hardware device that sits between the computer HDMI output and the projector.  1080p@ 30fps without impacting the computer at all.

MP4 is just a container and pretty much everyone has moved to MKV containers which hold the same stuff, are supported everywhere and much more flexible.  .MKV is an amazing container - almost limitless - in fact, google made up .webm based on .mkv just with extremely limited audio and video codecs.  I've never seen a video or audio format that wouldn't go into an MKV container AND be compressed better.  Even lossless audio gets compressed (think ZIP) when put into an MKV.

---

### Post by RobGoss on 2017-08-19
Sounds like you have a nice setup, thanks so much for the help as always

---

