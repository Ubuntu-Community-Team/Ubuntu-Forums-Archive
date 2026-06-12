---
title: "M4A Audio detected as Video in Nautilus"
date: 2006-07-17
forum: Multimedia &amp; Video
---

### Post by bludhound on 2006-07-17
Hello guys. I'm experiencing a small annoyance here - I associated all my m4a files with Rhythmbox, and I'm sure they are all audio, cuz I encoded them to m4a when I was in Windows, mostly using iTunes for the encoding. However, when I try to double-click on them in Nautilus, I get this error message:


Cannot open Linkin_Park_-_From_The_Inside.m4a

The filename "Linkin_Park_-_From_The_Inside.m4a" indicates that this file is of type "MPEG-4 audio". The contents of the file indicate that the file is of type "MPEG-4 video". If you open this file, the file might present a security risk to your system.

Do not open the file unless you created the file yourself, or received the file from a trusted source. To open the file, rename the file to the correct extension for "MPEG-4 video", then open the file normally. Alternatively, use the Open With menu to choose a specific application for the file. 


And the error is right, I am able to open it with the 'Open With' menu on a per-open basis.

Alternatively, I can get it to play by opening RhythmBox, then selecting the Import option from the RhythmBox menu.

I tried disabling the thumbnailers in GConf, and I verified that thumbnails were indeed disabled. No luck either.

Have anyone experienced this problem? Should I file this in Launchpad?

---

### Post by Jagot on 2006-07-17
I've never experienced that one before.  Do you have the gstreamer0.10-plugins-bad-multiverse package installed?

---

### Post by bludhound on 2006-07-17
Yep, I did. The problem seem to occur no matter which audio player I associate with m4a files (RhythmBox, XMMS, MPlayer). It seems that it is either GNOME's or Nautilus' mime-detection mechanism. I listed out the mime type in Nautilus, and it's detected as an MP4 *Video*.

---

### Post by MGStreak on 2007-05-15
I'm having the same problem... and I know I've installed all the plugins/codecs I could find.  The files seem to play fine, but those m4a's which I had encoded in iTunes before I switched to Ubuntu are read as audio files, whereas the files I have encoded (ripped) using ANY program I can find are listed as audio until I click on them, at which time the file type suddenly switches to video!!!

Can anyone offer a suggestion?

---

### Post by RanulfWolfSage on 2007-06-13
Nobody has a suggestion for this? I just converted some files to m4a on my Ubuntu Fiesty Fawn 7.04, and as soon as I associated the media player and tried to double click them I got the error message. There has to be a way to convince Ubuntu that these are audio files, or at the least, tell it to stop popping up that warning and preventing opening from double-click. Any ideas at all?

---

### Post by ron999 on 2008-01-30
Bump :lolflag:

---

### Post by bitmonkey on 2008-02-15
Another bump. I'm experiencing this same issue in FreeBSD 6.2 stable.

Paul

---

### Post by cozmicharlie on 2008-02-15
First you need to understand that m4a and mpeg are what they call containers.  They are not music codes but containers that can hold a number of different codecs.  aac is a code or file format - but by itself you cannot add things like tags.  So, you need to wrap it in a container and that is usually m4a.  However, m4a and mpeg4 are the same thing except m4a is used exclusively for audio and mpeg4 is used for audio and/or video.  Ubuntu shows the m4a as mpeg - it doesn't matter they are the same.  Most decoders in Ubuntu use ffmpeg to convert to aac - this decodes the files  puts it into the mpeg4 or m4a container.  That is why they show up as video but they are audio so don't worry.

A note about aac - aac is not Apple Lossless - True Apple Lossless is ALAC.  Apple is worse than Microsoft about not sharing code so their is no ALAC transcoding support for Ubuntu or any Linux distro (you can play ALAC but you can not rip music from a cd to ALAC in Ubuntu).   

Now to fix the problem.  What you need to do is ignore the warning and set it to open using whatever player you use.  So for example if you want Rythmbox then right click on the music file>open with>rythmbox.  If Rythmbox is not in the list then search "open with other application".  If you still cannot find the program go to "use custom command>browse and browse the usr/bin folder to find the bin file that opens the application.  Once you do that you have associated the m4a file with the application and any time you double click it should just open in that application.

---

### Post by ron999 on 2008-02-15
OK, I think I understand.

But I use two methods to aac encode with Ubuntu.
One is ffmpeg and the other is from rootkit (part of mp4tools).

The ffmpeg encoded files show as MPEG-4 video.
The rootkit encoded files show as MPEG-4 audio.

When I use MediaInfo on the files it shows:-
The ffmpeg ones are format MPEG-4 and codec is AAC.
The rootkit ones are format iTunes and codec AAC SBR.

So it looks as though, like you said, the ffmpeg encoding uses a 'work around' but the rootkit encoding doesn't.

Output from MediaInfo:-
```
ron@ron-desktop:~$ MediaInfo "/home/ron/suzz.m4a"
General #0
Complete name        : /home/ron/suzz.m4a
Format               : MPEG-4
Format/Info          : ISO 14496-1 Base Media
Format/Family        : MPEG-4
File size            : 48.4 MiB
PlayTime             : 59mn 510ms
Bit rate             : 115 Kbps
StreamSize           : 1.16 MiB
Encoded date         : UTC 1970-01-01 00:00:00
Tagged date          : UTC 1970-01-01 00:00:00

Audio #0
Codec                : AAC
Codec/Family         : AAC
PlayTime             : 59mn 509ms
Bit rate             : 112 Kbps
Channel(s)           : 2 channels
Sampling rate        : 44 KHz
Resolution           : 16 bits
StreamSize           : 47.3 MiB
Encoded date         : UTC 1970-01-01 00:00:00
Tagged date          : UTC 1970-01-01 00:00:00

ron@ron-desktop:~$ MediaInfo "/home/ron/bottomend.m4a"
General #0
Complete name        : /home/ron/bottomend.m4a
Format               : iTunes
Format/Info          : Apple AAC audio with iTunes info
Format/Family        : MPEG-4
File size            : 213 KiB
PlayTime             : 53s 126ms
Bit rate             : 33 Kbps
StreamSize           : 5.59 KiB
Encoded date         : UTC 2008-01-21 01:05:55
Tagged date          : UTC 2008-01-21 01:05:55

Audio #0
Codec                : AAC SBR
PlayTime             : 53s 127ms
Bit rate             : 32 Kbps
Bit rate mode        : CBR
Channel(s)           : 1 channel
Sampling rate        : 96 KHz
Resolution           : 16 bits
StreamSize           : 208 KiB
Encoded date         : UTC 2008-01-21 01:05:55
Tagged date          : UTC 2008-01-21 01:05:55


```

---

### Post by cozmicharlie on 2008-02-15
> **ron999 said:**
> OK, I think I understand.

But I use two methods to aac encode with Ubuntu.
One is ffmpeg and the other is from rootkit (part of mp4tools).

The ffmpeg encoded files show as MPEG-4 video.
The rootkit encoded files show as MPEG-4 audio.

When I use MediaInfo on the files it shows:-
The ffmpeg ones are format MPEG-4 and codec is AAC.
The rootkit ones are format iTunes and codec AAC SBR.

So it looks as though, like you said, the ffmpeg encoding uses a 'work around' but the rootkit encoding doesn't.

Output from MediaInfo:-
```
ron@ron-desktop:~$ MediaInfo "/home/ron/suzz.m4a"
General #0
Complete name        : /home/ron/suzz.m4a
Format               : MPEG-4
Format/Info          : ISO 14496-1 Base Media
Format/Family        : MPEG-4
File size            : 48.4 MiB
PlayTime             : 59mn 510ms
Bit rate             : 115 Kbps
StreamSize           : 1.16 MiB
Encoded date         : UTC 1970-01-01 00:00:00
Tagged date          : UTC 1970-01-01 00:00:00

Audio #0
Codec                : AAC
Codec/Family         : AAC
PlayTime             : 59mn 509ms
Bit rate             : 112 Kbps
Channel(s)           : 2 channels
Sampling rate        : 44 KHz
Resolution           : 16 bits
StreamSize           : 47.3 MiB
Encoded date         : UTC 1970-01-01 00:00:00
Tagged date          : UTC 1970-01-01 00:00:00

ron@ron-desktop:~$ MediaInfo "/home/ron/bottomend.m4a"
General #0
Complete name        : /home/ron/bottomend.m4a
Format               : iTunes
Format/Info          : Apple AAC audio with iTunes info
Format/Family        : MPEG-4
File size            : 213 KiB
PlayTime             : 53s 126ms
Bit rate             : 33 Kbps
StreamSize           : 5.59 KiB
Encoded date         : UTC 2008-01-21 01:05:55
Tagged date          : UTC 2008-01-21 01:05:55

Audio #0
Codec                : AAC SBR
PlayTime             : 53s 127ms
Bit rate             : 32 Kbps
Bit rate mode        : CBR
Channel(s)           : 1 channel
Sampling rate        : 96 KHz
Resolution           : 16 bits
StreamSize           : 208 KiB
Encoded date         : UTC 2008-01-21 01:05:55
Tagged date          : UTC 2008-01-21 01:05:55


```

From what I can see based on the file size 213 kib vs 48.4 mib you are right.  I was not familair with rootkit so thanks for the info.  It does illustrate the point though that m4a is only a container so how the files show up depends on how they are coded as you illustrated.  I use pacpl to decode and it uses ffmpeg so it looks like rootkit is the way to go.

Did you try associating the program with a player when you open as I described and did that work for you?

---

### Post by ron999 on 2008-02-15
Hi
The rootkit encoder is fab.:):)
It encodes at 32Kbps but sounds good cos it's HE-AAC+ (SBR+PS).

I haven't associated the files with anything. That's not a problem, I can 'open with' whatever I like.
It's just irritating seeing audio files listed as videos.:confused:

---

### Post by cozmicharlie on 2008-02-15
> **ron999 said:**
> OK, I think I understand.

But I use two methods to aac encode with Ubuntu.
One is ffmpeg and the other is from rootkit (part of mp4tools).

The ffmpeg encoded files show as MPEG-4 video.
The rootkit encoded files show as MPEG-4 audio.

When I use MediaInfo on the files it shows:-
The ffmpeg ones are format MPEG-4 and codec is AAC.
The rootkit ones are format iTunes and codec AAC SBR.

So it looks as though, like you said, the ffmpeg encoding uses a 'work around' but the rootkit encoding doesn't.
[/CODE]

A quick question.  The instructions for using rootkit are not easy to find.  How do you get the .aac into an m4a container?  It says to use mp4box but I cannot find anything that explains how to so this.

---

### Post by cozmicharlie on 2008-02-15
> **ron999 said:**
> OK, I think I understand.

But I use two methods to aac encode with Ubuntu.
One is ffmpeg and the other is from rootkit (part of mp4tools).

The ffmpeg encoded files show as MPEG-4 video.
The rootkit encoded files show as MPEG-4 audio.

When I use MediaInfo on the files it shows:-
The ffmpeg ones are format MPEG-4 and codec is AAC.
The rootkit ones are format iTunes and codec AAC SBR.

So it looks as though, like you said, the ffmpeg encoding uses a 'work around' but the rootkit encoding doesn't.

Output from MediaInfo:-
```
ron@ron-desktop:~$ MediaInfo "/home/ron/suzz.m4a"
General #0
Complete name        : /home/ron/suzz.m4a
Format               : MPEG-4
Format/Info          : ISO 14496-1 Base Media
Format/Family        : MPEG-4
File size            : 48.4 MiB
PlayTime             : 59mn 510ms
Bit rate             : 115 Kbps
StreamSize           : 1.16 MiB
Encoded date         : UTC 1970-01-01 00:00:00
Tagged date          : UTC 1970-01-01 00:00:00

Audio #0
Codec                : AAC
Codec/Family         : AAC
PlayTime             : 59mn 509ms
Bit rate             : 112 Kbps
Channel(s)           : 2 channels
Sampling rate        : 44 KHz
Resolution           : 16 bits
StreamSize           : 47.3 MiB
Encoded date         : UTC 1970-01-01 00:00:00
Tagged date          : UTC 1970-01-01 00:00:00

ron@ron-desktop:~$ MediaInfo "/home/ron/bottomend.m4a"
General #0
Complete name        : /home/ron/bottomend.m4a
Format               : iTunes
Format/Info          : Apple AAC audio with iTunes info
Format/Family        : MPEG-4
File size            : 213 KiB
PlayTime             : 53s 126ms
Bit rate             : 33 Kbps
StreamSize           : 5.59 KiB
Encoded date         : UTC 2008-01-21 01:05:55
Tagged date          : UTC 2008-01-21 01:05:55

Audio #0
Codec                : AAC SBR
PlayTime             : 53s 127ms
Bit rate             : 32 Kbps
Bit rate mode        : CBR
Channel(s)           : 1 channel
Sampling rate        : 96 KHz
Resolution           : 16 bits
StreamSize           : 208 KiB
Encoded date         : UTC 2008-01-21 01:05:55
Tagged date          : UTC 2008-01-21 01:05:55


```

From what I can see based on the file size 213 kib vs 48.4 mib you are right.  I was not familiar with rootkit so thanks for the info.  It does illustrate the point though that m4a is only a container so how the files show up depends on how they are coded as you illustrated.  I use pacpl to decode and it uses ffmpeg so it looks like rootkit is the way to go.

Did you try associating the program with a player when you open as I described and did that work for you?

---

### Post by ron999 on 2008-02-15
Hi
First things first.
I do have a problem with those MPEG-4 video files. If I just click them I get an error message - see the screenshot attached.
But if I right-click 'open with' then that's OK.

******

I had problems with mp4tools.
It's OK for Gutsy but I'm still using Feisty.
So I couldn't install the whole mp4tools.
But I got help from rootkit on this thread (from post #10).
Thread:-[http://ubuntuforums.org/showthread.php?t=628434]("http://ubuntuforums.org/showthread.php?t=628434")
I just installed the he-aac+ encoder on its own.

To wrap the aac in mp4 I originally used command:-
**MP4Box -add <audio.aac> <audio.mp4>**

But he advised me to use instead:-
**MP4Box -new -sbrx -no-sys -add <audio.aac> <audio.mp4>**

Eventually I combined the MP4Box instruction together with normalization and encode in another script called mkaacplus.

So my final command just needs to be:-
**mkaacplus <input.wav> <output.m4a> 32**

Edit. I forgot to attach the screenshot, but it says "The file name indicates that it's blah blah.... but the contents show that it's blah blah..."

---

### Post by cozmicharlie on 2008-02-15
Well I'm stumped.   I don't have the problem and my files show up as video also but I can open them by clicking.  Maybe it is a problem in Fiesty - I have Gutsy and it works fine.  Sorry I can't be of more help.  I even did a search of the forums and could not find any posts that might help.

---

