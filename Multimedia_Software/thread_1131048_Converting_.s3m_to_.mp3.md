---
title: "Converting .s3m to .mp3"
date: 2009-04-20
forum: Multimedia Software
---

### Post by ekidd91 on 2009-04-20
I've got an .s3m file that I want on my mp3 player, is there a way to convert it to .mp3 (or at least a more common format) in Ubuntu?

---

### Post by logos34 on 2009-04-20
maybe convert to .wav, then to .mp3 using foobar2000 on wine 

I think you'll need this codec plugin:

> DUMB Module Decoder (foo_dumb) Plays your favorite module files, and then some. (MOD, S3M, XM, IT, 669, PTM, PSM, MTM, UMX)

---

### Post by mc4man on 2009-04-20
I would think that you could use vlc to convert to .wav, then deal with as needed.
(just tried with a .s3m, took only about 3 secs to convert 3 min. song to .wav

---

### Post by logos34 on 2009-04-20
hmm, I didn't know vlc supports s3m...not listed on their [formats]("http://www.videolan.org/vlc/features.html") page.

I guess you could also use ffmpeg, provided it was compiled with MOD support option enabled.

---

### Post by ekidd91 on 2009-04-21
Thanks, used VLC to convert it; had no idea VLC converted media or supported .s3m.

---

### Post by cb951303 on 2009-04-21
you can use milkytracker (it's in repos) to export it to wav.
but personally, IMHO the most accurate module player is "dumb". you can look for libdump in repos. although I'm not sure I think it comes with a command line wav converter utility.

---

### Post by andrew.46 on 2009-04-21
Hi logos34,

> **logos34 said:**
> hmm, I didn't know vlc supports s3m...not listed on their [formats]("http://www.videolan.org/vlc/features.html") page.

I guess you could also use ffmpeg, provided it was compiled with MOD support option enabled.

Well you are ahead of me anyway as I have not heard of s3m files before :-). But I have had a look at FFmpeg and could not see how to enable MOD support?

Andrew

---

### Post by logos34 on 2009-04-21
> **andrew.46 said:**
> Hi logos34,



Well you are ahead of me anyway as I have not heard of s3m files before :-). But I have had a look at FFmpeg and could not see how to enable MOD support?

I thought I saw an option for that...apparently not on second glance.

Looks like mc4man's suggestion of vlc is the simplest and fastest way.  CLI solutions are always so elegant!

---

