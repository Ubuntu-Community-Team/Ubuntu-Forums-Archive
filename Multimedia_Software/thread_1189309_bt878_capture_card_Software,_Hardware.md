---
title: "bt878 capture card Software, Hardware?"
date: 2009-06-16
forum: Multimedia Software
---

### Post by LinuxGamer_ on 2009-06-16
Hello, I have a Brooktree 878 cap card and I am running on Ubuntu 8.04 and I have it set up with my composite cables & installed and what I was wondering is what software and hardware I need for this to successfully work in Totem? (Having my footage, its video gameplay, upload and play on Totem.) Let alone how do I know if I'm recording when I play? I passed the hardware test with the sound and video. If you know any suggestions please reply back. Thank you.

---

### Post by LinuxGamer_ on 2009-06-16
Bump

---

### Post by LinuxGamer_ on 2009-06-18
Bump

---

### Post by xzero1 on 2009-06-18
Install tvtime, which will allow you to view the video inputs. In order to capture video, this must be done in software. Linux treats the card as a video4linux device. Totem is a movie *player* and it wont capture video unless there is a plugin I don't know about.

---

### Post by LinuxGamer_ on 2009-06-19
> **xzero1 said:**
> Install tvtime, which will allow you to view the video inputs. In order to capture video, this must be done in software. Linux treats the card as a video4linux device. Totem is a movie *player* and it wont capture video unless there is a plugin I don't know about.

Sounds good, where can I get this "TvTime"?

---

### Post by fillintheblanks on 2009-06-19
Applications > add/remove...

---

### Post by LinuxGamer_ on 2009-06-19
Ok cool thanks one question though for "Default Frequency Table" do I choose cable or Broadcast? I'm trying to record video which would be on my line F.

---

### Post by LinuxGamer_ on 2009-06-19
Alright. I got it to play on my computer, 2 things though. Audio? I'm not receiving any audio. Do I need to do some tuning? How do I start recording? Like, what do I have to navigate to get to for it to record and save? Or is it streaming?

---

### Post by LinuxGamer_ on 2009-06-20
Basically what I'm meaning to ask is how do I know when I'm recording _AND_ how do I create a video file for my recording and how do I save?

---

### Post by xzero1 on 2009-06-20
> **LinuxGamer_ said:**
> Basically what I'm meaning to ask is how do I know when I'm recording _AND_ how do I create a video file for my recording and how do I save?

These threads should help...
[http://ubuntuforums.org/showthread.php?t=728390&highlight=mencoder](http://ubuntuforums.org/showthread.php?t=728390&highlight=mencoder)
[http://ubuntuforums.org/showthread.php?t=367238&highlight=mencoder](http://ubuntuforums.org/showthread.php?t=367238&highlight=mencoder)

Now, since you are encoding realtime in software you may need to encode to mpeg2 or something else instead of x264 depending on your cpu speed. If you can find a gui for mencoder that supports your card that should simplify setting things up.

---

### Post by LinuxGamer_ on 2009-06-20
> **xzero1 said:**
> These threads should help...
[http://ubuntuforums.org/showthread.php?t=728390&highlight=mencoder](http://ubuntuforums.org/showthread.php?t=728390&highlight=mencoder)
[http://ubuntuforums.org/showthread.php?t=367238&highlight=mencoder](http://ubuntuforums.org/showthread.php?t=367238&highlight=mencoder)

Now, since you are encoding realtime in software you may need to encode to mpeg2 or something else instead of x264 depending on your cpu speed. If you can find a gui for mencoder that supports your card that should simplify setting things up.
  Computer speed is 1.7 Gigahertz . I think that should answer the first question on wether I need to encode to Mpeg2. Anyways, I'm not that great with computers so how exactly do I encode to MPEG2?

---

### Post by LinuxGamer_ on 2009-06-20
bump

---

### Post by LinuxGamer_ on 2009-06-21
bump again.

---

### Post by xzero1 on 2009-06-22
Sorry, I don't use that card anymore but the command lines should be similar. In any case it must be tweaked to match your hardware.

---

### Post by LinuxGamer_ on 2009-06-23
Well, what I'm trying to do is create a file for my video. My video streams (other words plays as it goes) on TvTime at the same rate as my TV. My video source is Composite 1 and my TV standard is NTSC, according to  when I right click and look at what my video source is and TV standard. So, where is Mencoder or where is it on the screen of TvTime?

---

### Post by LinuxGamer_ on 2009-06-23
Wait, when you used TvTime what card did you use? Was it the Bt878 because I looked at the TvTime support site and it doesn't say the bt 878 is supported. Or does it go by another label?

---

### Post by sagex24 on 2009-06-24
Is it possible using the program cheese and choosing the camera to record from as the capture card, that would work?

---

### Post by LinuxGamer_ on 2009-06-24
> **sagex24 said:**
> Is it possible using the program cheese and choosing the camera to record from as the capture card, that would work?

I don't know what you're talking about sorry. 1.) Never heard of the program cheese. 2.) If it turns out that this program "Cheese" works as a encoder or file maker for my capture then I'd say it COULD work.

---

### Post by sagex24 on 2009-06-26
Its not really some advanced program, its this thing i have on my laptop that lets you take pictures and videos form the laptop camera, but you have the option to select a different camera.  You can save the files after.  You would have to use something else to change the file type though, i'm pretty sure.

---

### Post by LinuxGamer_ on 2009-06-27
> **sagex24 said:**
> Its not really some advanced program, its this thing i have on my laptop that lets you take pictures and videos form the laptop camera, but you have the option to select a different camera.  You can save the files after.  You would have to use something else to change the file type though, i'm pretty sure.
Installed, doesn't give me a choice to change video source.

---

### Post by LinuxGamer_ on 2009-07-02
Bump

---

### Post by LinuxGamer_ on 2009-07-04
Bump_

---

### Post by LinuxGamer_ on 2009-07-06
Bump

---

### Post by LinuxGamer_ on 2009-07-08
bump

---

### Post by LinuxGamer_ on 2009-07-10
What I'm looking for is how to change my video source on the application "Cheese" to the one on my capture card.

---

