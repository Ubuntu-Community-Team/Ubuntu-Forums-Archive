---
title: "MP3 Quality in Soundjuicer"
date: 2008-08-06
forum: Multimedia Software
---

### Post by CarlosinFL on 2008-08-06
I am currently ripping CD's as MP3's with Soundjuicer. I am wondering what is the best quality MP3 I can get from ripping a disk to MP3? The "GStreamer Pipeline" settings in Soundjuicer shows as follows:

```
audio/x-raw-int,rate=44100,channels=2 ! lame name=enc mode=0 vbr-quality=6 ! id3v2mux
```

Is there a way I can improve the quality of MP3 files since disk space is not a concern at all.

Thanks for any info!

---

### Post by tech9 on 2008-08-06
> **Carlwill said:**
> I am currently ripping CD's as MP3's with Soundjuicer. I am wondering what is the best quality MP3 I can get from ripping a disk to MP3? The "GStreamer Pipeline" settings in Soundjuicer shows as follows:

```
audio/x-raw-int,rate=44100,channels=2 ! lame name=enc mode=0 vbr-quality=6 ! id3v2mux
```Is there a way I can improve the quality of MP3 files since disk space is not a concern at all.

Thanks for any info!

 I believe that you can set it to a higher bit rate than that for better quality

---

### Post by CarlosinFL on 2008-08-06
Sorry I am not a MP3 / sound file guru so I don't know what the max quality setting is. Does anyone know what the magic # would be? Obviously I want the best quality MP3 available.

Anyone know what needs to be changed? I assume the 44100 rate parameter is what I need to change but to what, I have no idea.

Thanks for any help!

---

### Post by tech9 on 2008-08-06
Check this link out...

[http://ubuntuforums.org/showthread.php?t=295698&page=3](http://ubuntuforums.org/showthread.php?t=295698&page=3)

it looks like you can increase the bitrate at the end of the string...

```
audio/x-raw-int,rate=44100,channels=2!lame name=enc bitrate=256
```

---

### Post by CarlosinFL on 2008-08-06
> **tech9 said:**
> Check this link out...

[http://ubuntuforums.org/showthread.php?t=295698&page=3](http://ubuntuforums.org/showthread.php?t=295698&page=3)

it looks like you can increase the bitrate at the end of the string...

```
audio/x-raw-int,rate=44100,channels=2!lame name=enc bitrate=256
```

So according to that link it appears I can set the rate to 320?

> Per MP3 entry on Wikipedia, [http://en.wikipedia.org/wiki/MP3](http://en.wikipedia.org/wiki/MP3)
Bit rates available in MPEG-1 Layer 3 are 32, 40, 48, 56, 64, 80, 96, 112, 128,
160, 192, 224, 256 and 320 kbit/s

When I do a rip now, is there a way to see what the default rate is set to?

---

### Post by tech9 on 2008-08-06
> **Carlwill said:**
> So according to that link it appears I can set the rate to 320?



When I do a rip now, is there a way to see what the default rate is set to?

 Yes, you could set it to 320, not sure how to check the default rate, but I am sure you will know when you hear better sound quality from setting the rate higher.

Good Luck!

---

### Post by CarlosinFL on 2008-08-11
When I change Soundjuicer with the following settings:

```
audio/x-raw-int,rate=44100,channels=2!lame name=enc bitrate=320
```

I then lose information and I don't understand why the information is present at 128 quality and then when I change the quality to 320, the data is all gone.

---

### Post by mc4man on 2008-08-11
if this was your setting in sound-juicer
> audio/x-raw-int,rate=44100,channels=2 ! lame name=enc mode=0 vbr-quality=[COLOR="Red"]6[/COLOR] ! id3v2mux 
then try _just changing what's in red_. Vbr is better than cbr and specifying a bitrate. Vbr works off of quality settings 0-9 with 0 being the highest, 9 the worst. 0-2 quality are hard to tell the difference

When you ck. properties the bitrate shown will be the average. (an _average_ vbr of around 200 is generally what you'll see and as transparent as mp3 is going to get

see here for add. info and some settings for grip

[http://ubuntuforums.org/showthread.php?p=5546268#post5546268](http://ubuntuforums.org/showthread.php?p=5546268#post5546268)

---

### Post by CarlosinFL on 2008-08-11
Awesome info! Thanks. Going to try setting vbr to "0".

---

### Post by CarlosinFL on 2008-08-21
On this new Ubuntu 8.04 machine I have the following:

```
audio/x-raw-int,rate=44100,channels=2!lame name=enc bitrate=320
```

I am guessing the bitrate=320 is the highest quality, right? By default there is nothing that indicates vbr quality like shown above on my laptop...

---

### Post by Bruce R on 2008-08-27
Hi Folks
Try the following GStreamer profile and you should be impressed
audio/x-raw-int,rate=44100,channels=2 ! lame name=enc mode=1
vbr=4 vbr-min-bitrate=32 vbr-max-bitrate=320 vbr-quality=3 ! id3v2mux

---

### Post by CarlosinFL on 2008-08-27
> **Bruce R said:**
> Hi Folks
Try the following GStreamer profile and you should be impressed
audio/x-raw-int,rate=44100,channels=2 ! lame name=enc mode=1
vbr=4 vbr-min-bitrate=32 vbr-max-bitrate=320 vbr-quality=3 ! id3v2mux

Very cool. I will give it a shot!

---

### Post by jimmysheldon on 2008-08-27
> **Bruce R said:**
> Hi Folks
Try the following GStreamer profile and you should be impressed
audio/x-raw-int,rate=44100,channels=2 ! lame name=enc mode=1
vbr=4 vbr-min-bitrate=32 vbr-max-bitrate=320 vbr-quality=3 ! id3v2mux

I tried the sgtreamer profile, and when i look at the properties for the files it says the bitrate is 128. i'm guessing that means i'm still ripping at 128 :(


any other suggestions, or am i just missing something obvious here.

---

### Post by CarlosinFL on 2008-08-27
Oh that sucks. I am looking to get 320. :(

---

### Post by jimmysheldon on 2008-08-30
it's all working fine now. i made the new profile, but forgot to select that as the profile i wanted to use.. silly me. working and sounding beautiful now.

---

### Post by CarlosinFL on 2008-09-02
It appears that with the suggestion posted above, I can rip the disk at 320kbps however I lose information data which is annoying however when I rip at 120kbps, I have the data present. Notice the examples below. The one showing data was burned using the 120kbps & the one missing data was burned with the suggested string above at 320kbps.

So basically I want to combine the ripping in 320kbps and also keeping the information data that I get when I rip at 120kbps. I would think this would be possible but I don't know what I am doing wrong.

When I rip at 320, I am using below which has no artist info:

audio/x-raw-int,rate=44100,channels=2!lame name=enc bitrate=320

When I rip at 120, I am using below which has artist info:

audio/x-raw-int,rate=44100,channels=2 ! lame name=enc mode=0 vbr-quality=6 ! id3v2mux

Anyone know how to fix this?

---

### Post by wxnker on 2008-10-29
Try this:

audio/x-raw-int,rate=44100,channels=2 ! lame name=enc bitrate=320 ! id3v2mux

---

### Post by dbuvens on 2008-12-08
Thank you to everybody who replied in this thread. It helped me a lot!

---

### Post by tsh on 2008-12-26
From what I can tell, there is a bug in gstreamer which prevents any of the more obvious ways of improving bit-rate from taking effect. I've just ripped 20 CDs at 128k CBR, and am not happy - since i checked I was using preset=standard.

Necessary options are 
quality=3
vbr_max_bitrate=320

I'd almost believe this was an attempt to make us think that one of the open lossy compressors gives better quality, since the original bug was opened over a year ago.
[http://bugzilla.gnome.org/show_bug.cgi?id=498004](http://bugzilla.gnome.org/show_bug.cgi?id=498004)

My Gstreamer pipeline looks like this:

audio/x-raw-int,rate=44100,channels=2 ! lame name=enc mode=0 quality=3 preset=standard vbr-max-bitrate=320 ! id3v2mux

---

### Post by ebozzz on 2008-12-28
This will get you the best MP3 quality.....

audio/x-raw-int,rate=44100,channels=2 ! lame preset=insane ! id3v2mux

---

### Post by Cavsfan on 2009-08-28
> **ebozzz said:**
> This will get you the best MP3 quality.....

audio/x-raw-int,rate=44100,channels=2 ! lame preset=insane ! id3v2mux

Hope it is OK to revive this older post, but I am using Sound Juicer which has the same Gstreamer pipeline line for MP3 encoding and this worked perfectly to rip 320 bit MP3s!

Thanks ebozzz!

---

### Post by greenjumper on 2010-06-22
> **Cavsfan said:**
> Hope it is OK to revive this older post, but I am using Sound Juicer which has the same Gstreamer pipeline line for MP3 encoding and this worked perfectly to rip 320 bit MP3s!

Thanks ebozzz!

I can confirm this worked for me too! Thanks!

---

