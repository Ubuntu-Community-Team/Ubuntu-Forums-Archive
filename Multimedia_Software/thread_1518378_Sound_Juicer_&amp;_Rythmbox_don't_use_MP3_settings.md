---
title: "Sound Juicer &amp; Rythmbox don't use MP3 settings, I think"
date: 2010-06-26
forum: Multimedia Software
---

### Post by lduperval on 2010-06-26
Hi,

I'm trying to get about ~192kbps MP3's using Sound Juicer and rythmbox but no matter what I do, I always get 128kbps files. I'm trying to use vbr and my pipeline is this:

audio/x-raw-int,rate=44100,channels=2 ! lame name=enc mode=4 vbr-quality=0 ! id3v2mux

which should actually give me about 240kbps. But when I look at the properties, the bit rate is always around 128.

Any ideas (other than "Don't use it")?

Thanks,

L

P.S. If you feel strongly that the only answer is "don't use it" then I'm willing to try another program which will give similar results and uses CDBB and MusicBrainz as a backend database (a lot of he CDs I use are on MusicBrainz but not CDDB)

---

### Post by hansdown on 2010-06-26
Hi lduperval.

Do you have 

```
ubuntu-restricted-extras
```

from synaptic installed?

---

### Post by mc4man on 2010-06-26
If you're on karmic can suggest rubyripper - starting in lucid the gui version has some 'time to rip' issues (though still quite usable in cli
Can point the way if you wish to try 
(I use abcde, but that's a cli only

As far a gstreamer and mp3 - 
if you want to muddle thru this - readable and writeable means you can set if you get the syntax correct.
maximize your terminal before running

```
gst-inspect-0.10 lame
```
A quick look suggests that for vbr you need to also enable it in addition to setting quality, maybe like this
```
audio/x-raw-int,rate=44100,channels=2 ! lame name=enc mode=4 vbr=4 vbr-quality=0 ! id3v2mux

```
A vbr-quality=2 maybe around 192 or so

---

