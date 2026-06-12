---
title: "Newbie question: Audio CDs locked/protected?"
date: 2009-10-12
forum: Multimedia Software
---

### Post by boontoo on 2009-10-12
Hello. I tried searching about this but could not find anything regarding my specific problem.

I recently sold my Macs and switched to a Dell Mini 9 with Ubuntu 8.04. I also just got an external CD drive to rip and burn audio CDs.

When I insert an audio CD, I notice that all the tracks are locked. If I drag and drop the WAV files to a folder on my Mini (as I used to do with my Macs), the copies come out scrambled.

I gather there is some kind of copy protection being applied to audio CDs. The CDs in question are of my own music (home recordings), so I own all the copyrights. Why can't I freely copy my own files?

I know I can import the tracks with Rhythmbox Music Player, but it appears that I cannot rip uncompressed WAV files. It looks as if I must choose among various compressions (MP3, Ogg, FLAC).

Is there a way to unlock audio CDs for simple WAV-to-WAV ripping/copying?

Thanks.

---

### Post by DrMelon on 2009-10-12
First and foremost, you are using quite a dated version of Ubuntu. May I suggest updating to 8.10 or 9.04? There may be software that you don't have which is included in those updates.

Secondly, there should be a program in the Applications->Sound & Video menu called "Audio CD Extractor" or "Sound Juicer". That should help you.

---

### Post by mc4man on 2009-10-12
The lock icon you see doesn't indicate any 'protection', only that the files are 'read only'. (which makes sense because you can write/edit to your audio cd.

You should be able to drag and drop though not a preferred method, why they are 'scrambled' is a bit of mystery. Have you tried playing one of those d&d'ed files with another player? ( non-gstreamer

While I use rubyripper, rhythmbox can rip to .wav, Just go edit -> preferences -> music and choose "Voice, Lossless (Wav audio)"

---

### Post by boontoo on 2009-10-12
Thanks for the replies. I found Sound Juicer (also called Audio Extractor). It offers only the same compressed options of Rhythmbox. I tried using the Voice Lossless setting the other day, and it makes everything mono. I don't see a preference for WAV in stereo. I will look for Rubyripper and try it. 

As for updating my Ubuntu, I have thought about doing that but have not got around to it yet. The computer came with 8.04, so I've just been getting used to what I have. I will update it eventually, once I have a bit more confidence my Linux use. Thanks for the suggestion.

---

### Post by mc4man on 2009-10-12
Didn't realize that it only ripped to mono, though that can be changed by editing the gstreamer pipeline or by creating a new one

```
audio/x-raw-int,rate=44100,channels=2 ! wavenc name=enc
```

I'd try RR, here's a how to, there is now a ppa so you don't need to build.

see here
[http://ubuntuforums.org/showthread.php?t=799621&highlight=rubyripper](http://ubuntuforums.org/showthread.php?t=799621&highlight=rubyripper)

The page on ppa
[http://ubuntuforums.org/showthread.php?t=799621&page=9](http://ubuntuforums.org/showthread.php?t=799621&page=9)

I put up an all .deb, (linked on above page), may pull soon ( nothing wrong with it, only that in karmic all recommends are now  auto installed so packages I marked a recommended maybe people don't want

---

### Post by boontoo on 2009-10-12
> **mc4man said:**
> ```
audio/x-raw-int,rate=44100,channels=2 ! wavenc name=enc
```

Where do I enter this code? I tried pasting it into a terminal window, but nothing happened. Sorry, I am new to all of this.

---

### Post by boontoo on 2009-10-12
OK, I figured it out. Thanks for the code. I simply opened Rhythmbox's preferences and used the code to create a new option for ripping stereo WAV files.

Now a question about MP3 ripping.

The default setting encodes music from an audio CD as 128K MP3 files, and this is the code:

**audio/x-raw-int,rate=44100,channels=2 ! lame name=enc mode=0 vbr-quality=6 ! id3v2mux**

What if I want my MP3 files to be 256 Kbps? Can I modify the code above for this? I'm guessing I should change where it says "quality=6."

Or should I just use Sound Converter to turn the imported/ripped WAV files into MP3s instead of using Rhythmbox?

Thanks again. I am learning ...

---

### Post by mc4man on 2009-10-12
Myself don't use the gstreamer apps too much....

I'd probably be a little careful if editing the mp3 profile, if you wanted a higher quality vbr mp3 then lowering the # should be ok. (0-9, 0 being the highest quality.

If I remember soundconverter has some limited options as far as mp3, for vbr  it probaly max's out at the gstreamer profile or thereabouts, ( not 100% sure

If you wanted a cbr at 256 then I'd think soundconverter would do that.

While initially a bit of a bear to figure out, soundkonverter offers more flexibility

---

### Post by boontoo on 2009-10-12
OK, thanks. I might mess around with 0-9 in the code. 

Sound Converter offers both a straight CBR 256 setting and a VBR setting with a "target" of 256. What's strange about the VBR setting is that the rate ends up being closer to 160, or at least that's what EasyTAG says when I move the MP3s over to edit the tags. So I'm not sure what I'm actually getting when I set Sound Converter to its highest VBR setting. I've been using the CBR 256 setting instead.

I'll check out Sound Konverter too. Thanks.

---

