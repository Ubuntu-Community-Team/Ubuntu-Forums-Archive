---
title: "matroska converting"
date: 2007-11-10
forum: Multimedia &amp; Video
---

### Post by GeneticFlea on 2007-11-10
hey everyone, Ive got got 6 episodes of Planet Earth in Matroska Format (.mkv) and i want to burn them to a data dvd and watch them on my dvd player. The player supports the most common formats (avi, divx, mp4) but not .mkv. Ive been trying to find a converter for Ubuntu 7.10 without success yet. anyone have any suggestions or knows how to do this?

thanks!

---

### Post by Hopworks on 2007-11-18
> **GeneticFlea said:**
> hey everyone, Ive got got 6 episodes of Planet Earth in Matroska Format (.mkv) and i want to burn them to a data dvd and watch them on my dvd player. The player supports the most common formats (avi, divx, mp4) but not .mkv. Ive been trying to find a converter for Ubuntu 7.10 without success yet. anyone have any suggestions or knows how to do this?

thanks!
I too am interested in creating a DVD using one or more MKV files. I've been reading a lot today about it, and trying to get avidemux 2.4 working (I have it installed, and a menu shortcut, but clicking does nothing :()

So I'll watch this thread, and if I figure it out, I'll post how I did it. Please do the same if you find a way. I have several 1.1gb MKV files and I'd like to put four at a time on a 4.7 DVD, with a menu if possible.

Hop

---

### Post by Darkade on 2007-11-18
I suggest you try MediaCoder, it works great for me but you'll need to install it under wine, before you get picky about it being a windows application visit media coder wepage [http://mediacoder.sourceforge.net/](http://mediacoder.sourceforge.net/)

---

### Post by Hopworks on 2007-11-18
> **Darkade said:**
> I suggest you try MediaCoder, it works great for me but you'll need to install it under wine, before you get picky about it being a windows application visit media coder wepage [http://mediacoder.sourceforge.net/](http://mediacoder.sourceforge.net/)
Cool, I'll give that a shot. Especially since I have been beating my skull against a Windows-made block wall all morning trying to get various apps to do what I want. ](*,) VLC just gives me a file with audio, no video, no matter what I do. Well, sometimes I get an exception error and the ability to tell Micro$oft about it. :mad:

---

### Post by Hopworks on 2007-11-18
OK, it looks like I have MediaCode 0.6.0 Build 3980 installed, and it is working. All I need to know now is the settings. Any recommendations for converting my MKV file to something I can use to burn a DVD with? There are a lot of options, thankfully. Here are my file details...
```
General #0
Complete name        : Z:\home\public\server\my_mkv.mkv
Format               : Matroska
File size            : 1.07 GiB
PlayTime             : 43mn 2s
Bit rate             : 3572 Kbps
Encoded date         : UTC 2007-11-10 09:22:18
Writing application  : mkvmerge v2.0.0 ('After The Rain Has Fallen') built on Jan 13 2007 19:58:56
Writing library      : libebml v0.7.7 + libmatroska v0.8.0

Video #0
Codec                : MPEG-4 AVC
Codec/Info           : MPEG4 ISO advanced profile
PlayTime             : 42mn 59s
Width                : 1280 pixels
Height               : 720 pixels
Aspect ratio         : 16/9
Frame rate           : 23.976 fps
Language             : English

Audio #0
Codec                : AC3
Codec/Info           : Dolby AC3
Channel(s)           : 2 channels
Sampling rate        : 48 KHz

```

Thanks a BUNCH for that mediacoder tip. I hope this does it for me! :)

Hop

---

### Post by Hopworks on 2007-11-18
Hmmm! OK! It works, kinda.

I have video and audio. The video looks real nice, very clean. I can't see any quality degradation at all, but the audio is off. The sound quality also sounds equally good. I have no way to visually check that outside of using my ears, but it sounds the same.

But the audio is way off, like 5 seconds, maybe more behind the video. I'm going to research that right now and see if there is an offset setting, or something I missed in the settings, but it's narrowing down to a solution here.

I'm playing with the settings, transcoding 1 minute snips of the MKV and viewing the results. I bumped up the bit rate dramatically from the default 800kbps. Maybe that is the problem. I'll try one with the reduced bit rate.

**EDIT!*** I found the audio delay adjustment right when I went to do my next test. It's on the 'TIME' tab. I'll set mine to -5000ms and see what happens* :shock:
**EDIT UPDATE*** The audio delay setting does affect the result, but it's all over the place. Off one minute, right on the next. So much for it being a set amount of milliseconds off.*

THANKS AGAIN! I really appreciate that tip about MediaCoder!! I hope I can solve that audio issue, but this is the closest I've been to what I want all morning! 

YOU ROCK! :guitar:

Hop

AFTERTHOUGHT: For some reason, MediaCoder causes my TightVNC to lose connection while transcoding. Just an FYI. I'm curious if anyone else has had that problem. I generally work on my Linux box using my Windows laptop via TightVNC. It's really no biggy, just a slight annoyance.

---

### Post by Hopworks on 2007-11-18
](*,):-k:evil: .... :-({|=

I'm pulling my freaking hair out over this audio issue. GeneticFlea, when you get back to this thread, and try the things we posted about, I'm real curious if you have the same audio issues.

I know it isn't hardware, or OS related, because I tried MediaCoder on my Core 2 Duo Windows laptop with the exact same results, save for processing time. And I tried nearly every setting my small mind could imagine. I guess what is left to try is to do this with a differently encoded MKV file and see if I have the same problems.

And I haven't tried splitting the audio and video, and multiplex it back again. I've come this far, it's worth learning about I guess.

It's a small victory, but at least I know it isn't wine, or Linux, or the hardware, because I really WANT to do this under Linux.

Darkade, or anyone else that knows, I would really appreciate some settings advice from someone that knows more about this sort of thing. In the meantime, I'll play with transcoding other file types to see if I can duplicate the issue with other audio encoding. And now that I said that, I'm wondering if it might be a codec? But then I'm sure the results on my two vastly different systems would vary, at least a little. Still, some advice about specific codecs would also be welcome.

Thanks for your time!

Hop

---

### Post by Darkade on 2007-11-18
That's kind o curious to me becouse for me media coder has always worked 'out of the box' I think it's a good shot to try encoding another mkv file or to split the video and the audio.
i really can't try encoding some mkv files my self because I'm having some trouble with my own wine at the time (please check here and tell me if you have any ideas [http://ubuntuforums.org/showthread.php?t=615827](http://ubuntuforums.org/showthread.php?t=615827))  but I will let you know if I find out something.

---

### Post by rsambuca on 2007-11-19
I have never used Matroska myself, but I can fiddle around with it when I get a chance to see if I can help out.  Only thing is, does anyone have a link to a small video with the matroska container that I can use?

---

### Post by Hopworks on 2007-11-19
> **rsambuca said:**
> I have never used Matroska myself, but I can fiddle around with it when I get a chance to see if I can help out.  Only thing is, does anyone have a link to a small video with the matroska container that I can use?

I'll try to encode one later today, and offer it to ya from my site. Problem is, I don't know if I can duplicate the exact build the author used on the MKV files I'm trying to transcode. I'm guessing he has some serious hardware, with an audio bit rate of 384kbps, and a video rate of over 2300kpbs.

I could offer the whole MKV, but it's huge by testing standards, at 1.1gb.

Thanks rsambuca for your attention on this matter, as with all my other video grabbing adventures. I'm at my wits-end. I've tried everything, and this dream is currently, officially, stalled.

Hop

---

