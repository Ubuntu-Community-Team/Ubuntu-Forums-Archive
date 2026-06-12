---
title: "Ripping CD's in Ubuntu 9.04"
date: 2009-07-22
forum: Multimedia Software
---

### Post by CarlosinFL on 2009-07-22
I am looking to rip my entire CD collection to MP3 files. I only have 9.04 and would like to stream the MP3's over my surround sound system at home. This means I really want a quality bit rate. Size of the individual file does not really concern me. I would like to use something loss-less but many media players don't support it so I assumed I would just go with the best quality MP3 file I can rip. Now my question is how can I rip the highest quality MP3 on my Ubuntu system? I have Sound-Juicer installed and it shows the following:

```
audio/x-raw-int,rate=44100,channels=2 ! lame name=enc mode=0 vbr-quality=6 ! id3v2mux
```

---

### Post by hibliss on 2009-07-22
This is a little old, but a decent guide -- [http://mellowd.co.uk/test2/index.php?entry=entry080818-171921]("http://mellowd.co.uk/test2/index.php?entry=entry080818-171921")

This is the same thing, on the forums. A script is included to partially automate the process -- [http://ubuntuforums.org/showthread.php?t=892874]("http://ubuntuforums.org/showthread.php?t=892874")

Going from CD-FLAC-MP3 is really your best bet. By the way, what device will you be streaming to on your home stereo system? A lot of devices can be coerced in to playing FLAC via transcoding, like the PS3 and Xbox360.

---

### Post by CarlosinFL on 2009-07-22
I will be using the PS3. Are you saying that I can rip everything in FLAC format and stream this via my XBOX and or PS3?

---

### Post by hibliss on 2009-07-22
> **Carlwill said:**
> I will be using the PS3. Are you saying that I can rip everything in FLAC format and stream this via my XBOX and or PS3?

Yes I am. I do it :D

I use FUPPES as a UPnP Media Server. There are plenty of others available, ushare is in the repos, or you can use PS3 Media Server (which you can find on Google Code). There are a ton, I think there may even be one or two in the repos.

For me, it is an easy choice between FUPPES and Mediatomb. You will have to play with the fuppes.cfg file (or the Mediatomb equivalent if you choose Mediatomb) to setup transcoding. It is fairly easy, and I trascode not just audio, but videos that the PS3 will not play natively (MKV being the only tough one to get to work, it is a tricky container).

There are several guides floating around if you spend some time on Google, and getting your fuppes.cfg file setup properly for transcoding can take a day or two, but it is well worth it. Check out this thread to get started (it is for the 360) -- [http://ubuntuforums.org/showthread.php?t=984325&highlight=FUPPES+PS3]("http://ubuntuforums.org/showthread.php?t=984325&highlight=FUPPES+PS3")

I can post my FUPPES.cfg file as an example so you can see my transcoding options. Will do that tonight when I get home.

---

### Post by Teabicky on 2009-07-22
> **hibliss said:**
> 

Going from CD-FLAC-MP3 is really your best bet.

Good idea, I never thought of it.  I use itunes (on windows) to rip all my cd's because I like to use 320kbps AAC format.  A bit off topic but do you know a programme that will convert 320 aac?  I think sound converter only goes up to 256kbps (It does go to 320 with mp3 for anybody interested.).

---

### Post by hibliss on 2009-07-22
All I use is LAME to go to MP3.

I will say that AAC sounds very close to LAME V0, and anyone who could notice any difference either has Superman ears or spent tens of thousands on their stereo system.

---

### Post by Teabicky on 2009-07-22
I think that at high rates 256kbps and above then there is very little difference (not noticeable to human ears anyway).  The difference between the two is noticeable at rates of 128kbps and lower.  I use aac when possible but do have quite a few mp3's too (from 7digital.com and play.com).  I might start ripping cd's to flac and converting them to 320 mp3 when I am using ubuntu.  It will save me booting up windows just too rip a cd.

---

### Post by hibliss on 2009-07-22
> **Teabicky said:**
> I might start ripping cd's to flac and converting them to 320 mp3 when I am using ubuntu.  It will save me booting up windows just too rip a cd.

320 is a bit of a waste. You end up encoding silence at the highest quality. Using the presets in LAME for V0 or -V2 is a better choice. Variable bitrate file so when there are silent spots in the song or frequency variances, the bitrate dips to compensate and you end up with a smaller file size with the same quality. V0 vs 320 there is no noticeable difference.

Even with -V2 there is no noticeable difference, and the size difference is huge.

See the chart in this wiki article -- [http://wiki.hydrogenaudio.org/index.php?title=Lame]("http://wiki.hydrogenaudio.org/index.php?title=Lame")

[IMG]http://wiki.hydrogenaudio.org/images/2/2c/Lame-chart-2.png[/IMG]

---

### Post by Teabicky on 2009-07-22
I mistakenly thought that variable bit rate was also an option with 320kpbs, it appears that it isn't.  

Although most music brought from 7digital.com and play.com is 320kbps anyway, so in that case I have no option.

---

### Post by CarlosinFL on 2009-07-23
Can I rip CD's at 320kbps using Sound Juicer?

---

### Post by hibliss on 2009-07-23
Yes you apparently can, I have never used it, but it is just a frontend for LAME. 

Check the chart above, you are better off using -V0 or -V2

---

### Post by vinutux on 2009-07-23
> **Carlwill said:**
> Can I rip CD's at 320kbps using Sound Juicer?

yeh...but y not opt .ogg (ogg theora).....it is far better in quality with lesser size compared to mp3...


**[http://www.vorbis.com/faq/#sound]("http://www.vorbis.com/faq/#sound")**

---

### Post by igorzwx on 2009-07-23
ogg was never good for me.
Why not flac?

---

### Post by vinutux on 2009-07-24
> **igorzwx said:**
> ogg was never good for me.
Why not flac?

Flac is loseless...means without compression (need more space)...Ogg, mp3 and aac are lossy formats with highly compressed for reducing file size....

---

