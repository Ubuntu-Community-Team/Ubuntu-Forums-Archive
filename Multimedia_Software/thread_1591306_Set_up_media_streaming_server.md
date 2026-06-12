---
title: "Set up media streaming server"
date: 2010-10-09
forum: Multimedia Software
---

### Post by TonyChaos on 2010-10-09
I was wondering if there was a thread that could give me a step by step on how to stream media securely over the internet from my desktop to my laptop.

I have a ton of movie and tv shows on my hard drive and instead of carrying around a backup of them on an external drive, I'd like to be able to type in a web address to view a list of files available to just stream.

Someone help me out?

Thanks!

---

### Post by P4man on 2010-10-09
I dont know any linux app thats any good for what you want.

Orb is superb, and probably exactly what you are looking for, but its windows only (ive seen people run it in a VM on top of linux though). 

More over, videoquality is rather disappointing. I would suggest you try Orb on a windows machine and see for yourself if this is really an alternative to carrying a full copy. I think you will find its not. Its nice to have but even running on a LAN its just not good enough IMHO to be used as the default way for your media.

---

### Post by Alessandro.g89 on 2010-10-09
I'm doing this by myself, so I can help you. But first, you should check how fast is your home's internet connection in upload (NOT download). If your video stuff has too high bitrates you will need to transcode during or before streaming.

---

### Post by TonyChaos on 2010-10-23
> **Alessandro.g89 said:**
> I'm doing this by myself, so I can help you. But first, you should check how fast is your home's internet connection in upload (NOT download). If your video stuff has too high bitrates you will need to transcode during or before streaming.

My home upload speed is 1.42MB/s and everything has been converted into dvd quality Mmpeg4. Is the upload speed enough and will I have to reconvert my files to .avi or something?

---

### Post by Alessandro.g89 on 2010-10-24
> **TonyChaos said:**
> My home upload speed is 1.42MB/s and everything has been converted into dvd quality Mmpeg4. Is the upload speed enough and will I have to reconvert my files to .avi or something?
network speed is (almost) always expressed in Mega_bits_ per second. did you mean 1.42 Mega_bits_/s or Mega_bytes_/s?
(in both cases you can have good quality :) )

now let's talk about your files:
- mpeg4 means they have .mp4 extension? that would be good, since this file format can be streamed (.avi can't :P )
- how did you encode them? at which bitrate? CBR, VBR or 2-pass?
if bitrate is lower then network speed, they're ok for streaming

---

### Post by TonyChaos on 2010-11-29
> **Alessandro.g89 said:**
> network speed is (almost) always expressed in Mega_bits_ per second. did you mean 1.42 Mega_bits_/s or Mega_bytes_/s?
(in both cases you can have good quality :) )

now let's talk about your files:
- mpeg4 means they have .mp4 extension? that would be good, since this file format can be streamed (.avi can't :P )
- how did you encode them? at which bitrate? CBR, VBR or 2-pass?
if bitrate is lower then network speed, they're ok for streaming

They're encoded with 2-pass and I believe the bitrate was just the default for the videos given by WinFF when I converted them. They actually have an .mpg extension, as I usually burned them to a DVD in DeVeDe within Ubuntu. Also, before they were .mpg, they were in an .avi container.

---

### Post by TonyChaos on 2010-11-29
Also, it's 1.42 Megabits per second.

---

