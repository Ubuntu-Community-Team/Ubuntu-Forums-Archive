---
title: "trouble with morse code practice mp3's"
date: 2010-10-07
forum: Multimedia Software
---

### Post by jhefferon on 2010-10-07
Hello,

I don't know anything about sound so I apologize if this is a dopey question.  I have Ubuntu 10.04.1 LTS on a 5 year old Intel laptop (the sound device just says "Internal stereo audio").

I am trying to burn morse code practice .mp3 files to a CD.  The files come from the ham radio club folks, at [http://www.arrl.org/20-wpm-code-archive](http://www.arrl.org/20-wpm-code-archive) .  I am getting a wavering chirping that I perceive comes before a dot or dash that begins a sequence, as: chirp-dot-dash-dash chirp-dot.  It is bad enough that it makes listening to the practice file hard.  I get chirping both if I listen to the file, and if I burn it to a CD and then listen in the car (which is what I want to do).

Ordinarily, if I play non-morse mp3's from the web then they sound fine (I don't do that very often so I may have missed other cases).  My preferred applications widget says I am using Rythmbox.  I tried to use K3b to burn the CD's but it said the file format of these .mp3 files was not recognized, while Ubuntu's default burner took them but produced chirpy CD's.

Is it possible that this is a newer version of the .mp3 format?  My son burned some for me in the past (I think on Windows) but I'm moving up in speed so I need new ones.  If it is a newer version of the format, is there any way to burn them under Linux?

Thanks,
Jim

---

### Post by P4man on 2010-10-07
It "sounds" like (no pun intended) the problem is in the MP3s themselves and then there isnt much you can do about it. Can you link directly one of the problematic MP3s so we can try them?

---

### Post by ron999 on 2010-10-07
Hi
The downloaded morse files play OK for me with VLC media player.
But they sound terrible when played in mPlayer.
Just as you described - chirps.
It's because they are recorded at a low bit-rate and low sample-rate.

You can re-sample them using LAME encoder.
Please try one or two using commands like this:-

```
[FONT="Courier New"][SIZE="4"]lame --resample 44.1 022320WPM.mp3 022320WPM_new.mp3[/SIZE]
[/FONT]
```
See if the new versions sound OK.

You can see below the difference between the original and the resampled version.

Original

> 
Complete name                    : 022320WPM.mp3
Format                           : MPEG Audio
File size                        : 1 004 KiB
Duration                         : 8mn 34s
Overall bit rate                 : 16.0 Kbps

Audio
Format                           : MPEG Audio
Format version                   : Version 2.5
Format profile                   : Layer 3
Duration                         : 8mn 34s
Bit rate mode                    : Constant
Bit rate                         : [COLOR="Red"]16.0 Kbps[/COLOR]
Channel(s)                       : 1 channel
Sampling rate                    : [COLOR="Red"]8 000 Hz[/COLOR]
Stream size                      : 1 004 KiB (100%)

Resampled

> 
Complete name                    : 022320WPM_new.mp3
Format                           : MPEG Audio
File size                        : 3.92 MiB
Duration                         : 8mn 34s
Overall bit rate                 : 64.0 Kbps
Writing library                  : LAME3.98r

Audio
Format                           : MPEG Audio
Format version                   : Version 1
Format profile                   : Layer 3
Duration                         : 8mn 34s
Bit rate mode                    : Constant
Bit rate                         : [COLOR="Red"]64.0 Kbps[/COLOR]
Channel(s)                       : 1 channel
Sampling rate                    : [COLOR="Red"]44.1 KHz[/COLOR]
Stream size                      : 3.92 MiB (100%)
Writing library                  : LAME3.98r
Encoding settings                : -m m -V 4 -q 3 -lowpass 16.5 -b 64

---

### Post by P4man on 2010-10-07
You got it Ron. I tried in Totem, VLC and checked in audacity and they all played fine, but with (s)mplayer they are horrible indeed. I dont know what Brasero uses to transcode, but its probably choking on the same issue (bug I might say). Nice catch.

edit: rythmbox also plays it fine here though. I can only reproduce it using (s)Mplayer? But that might well use the same backend as Brasero (the cd burning tool).

---

### Post by jhefferon on 2010-10-07
Thanks so much; the resampling did the trick.  I owe you.

Jim

---

