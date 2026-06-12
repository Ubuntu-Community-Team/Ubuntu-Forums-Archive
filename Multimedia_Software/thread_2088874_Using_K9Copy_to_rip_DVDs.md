---
title: "Using K9Copy to rip DVDs"
date: 2012-11-27
forum: Multimedia Software
---

### Post by pieman711 on 2012-11-27
I've just had a go at ripping my MASH DVDs to my ubuntu PC so I can watch them through my Raspbmc rasberry pi without having to use a DVD player. It seems to have ripped ok and plays back on ubuntu, but if i try and stream through a samba share to my Pi or android phone I only get the audio and no video. 
Also the file sizes are huge, about 800mb per half hour episode. Is there any way to shrink these? Any recommended file size output that doesn't hamper quality too much?
I'm currently using the wizard and outputting as a .avi file. 
Any advice would be great thanks.

---

### Post by Zteam on 2012-11-28
You can adjust the file size in K9copy, go to settings -> mpeg 4 -> video -> filesize

---

### Post by cottfcfan on 2012-11-29
Have you tried using dvdrip?
I found the output quality better than k9copy.
If you manually set the Video Bitrate Calculation to 1800 kbit/s, then a 2 hour DVD will take up about 1800mb, with good quality video.
Of course you can adjust that to suit.

---

### Post by pieman711 on 2012-11-29
thanks for your replies. I realised the mistake I was making was notchanging the setting to xvid on the last page of the wizard and then changing the file size. I've got it working so that it streams now. Is there any general recommendation when it comes to file size? I've gone for 180mb for a 30 min episode but that was really plucked out of the air. 
I'm having trouble with file names too. there are 8 episodes to a dvd each called ' title 1' etc. each episode comes out as a separate .avi fileand I want to have them called in the format MASH.s01e**.avi. can I do thisin k9 or do I have to manually rename them after.
I've just noticed cottfc that you live in hull. near I movedinto Hessle in the summer, where abouts do you live?

---

### Post by evilsoup on 2012-11-29
You will probably be better off using h.264 video in an MP4 rather than xvid: it has higher compression (smaller files for the same quality), and the raspberry pi can decode h.264 in the GPU, so it should run perfectly well.

I don't use K9Copy, so I don't know if it supports h.264; I rip an ISO & convert it using handbrake, from [this PPA](https://launchpad.net/~stebbins/+archive/handbrake-releases).

---

### Post by pieman711 on 2012-11-29
I had a bit of a play with handbrake but think I prefer K9. I'll give h.264 a go and see how it runs. Any recommendation for a good file size for either format? Do you have more freedom for individual title name output in handbrake? I can't find an option for it on k9, it just automatically puts incremental numbers after the file, annoyingly starting from 0 rather than 1,

---

### Post by evilsoup on 2012-11-29
I tend to choose a quality, rather than worrying about size; but with quality set to 19 (with x264, lower number=better quality, the scale goes from 0 - completely lossless - to 51 - crap; quality 18 is 'visually lossless' IIRC) a 91-minute film came out at 875 MB. That's using AC3 passthrough for the sound, so if you compress the sound to AAC or something, you'd get an even smaller size. According to [this](https://ffmpeg.org/trac/ffmpeg/wiki/x264EncodingGuide), setting the quality level to 25 (still acceptable quality for most people) should half that size.

So a quality of 19 would net you around 288 MB for a 30-minute video (actually slightly more, taking into account the audio), while a quality of 25 *should* get you about half of that.

It's been a while since I've ripped a TV series, but I think you have to name each episode manually in handbrake, when you add them to the encode queue.

---

### Post by pieman711 on 2012-11-29
great thanks for the information. I'll give that a go. I've got about 750gb of harddrive space but so far I have 8 series of mash and at 24 episodes a series I'm worried it may build up quickly. Plus I have other things on there too.

---

### Post by evilsoup on 2012-11-29
8*24*300MB adds up to 57.6 GB
So you could manage it, but that's a fairly large-ish chunk of space. Of course, that's with a crf number of 19, trying higher numbers will reduce the file sizes. I would suggest that you try out a few different quality levels & use the highest number that is of acceptable quality.

---

### Post by frank cox on 2012-12-01
> **pieman711 said:**
> thanks for your replies. I realised the mistake I was making was notchanging the setting to xvid on the last page of the wizard and then changing the file size. I've got it working so that it streams now. Is there any general recommendation when it comes to file size? I've gone for 180mb for a 30 min episode but that was really plucked out of the air. 
I'm having trouble with file names too. there are 8 episodes to a dvd each called ' title 1' etc. each episode comes out as a separate .avi fileand I want to have them called in the format MASH.s01e**.avi. can I do thisin k9 or do I have to manually rename them after.
I've just noticed cottfc that you live in hull. near I movedinto Hessle in the summer, where abouts do you live?

I agree, avi files will never compress like mpegs .

---

### Post by monkeybrain2012 on 2012-12-01
> **evilsoup said:**
> You will probably be better off using h.264 video in an MP4 rather than xvid: it has higher compression (smaller files for the same quality), and the raspberry pi can decode h.264 in the GPU, so it should run perfectly well.

I don't use K9Copy, so I don't know if it supports h.264; I rip an ISO & convert it using handbrake, from [this PPA](https://launchpad.net/~stebbins/+archive/handbrake-releases).

+1 for handbrake, by far the best. Tried dvdrip, always seems to be some problem. Heard that k9copy is good too but the developer has quit and it is no longer maintained.

---

### Post by wayneandleanne on 2012-12-03
+2 For Handbrake it's so easy to use

---

