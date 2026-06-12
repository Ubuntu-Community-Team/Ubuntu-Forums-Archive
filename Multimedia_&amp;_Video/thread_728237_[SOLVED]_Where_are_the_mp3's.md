---
title: "[SOLVED] Where are the mp3's ?"
date: 2008-03-18
forum: Multimedia &amp; Video
---

### Post by CasPol on 2008-03-18
Hi there;

I am using "Grip" to rip CD's and convert the ripped files to MP3.

Grip is doing this fine, but when the ripping and converting is complete I cannot find the mp3 files anywhere on my hard drive ?

Any ideas anyone ?

---

### Post by ajgreeny on 2008-03-18
If they exist you will find them with ```
locate mp3
```

---

### Post by x1a4 on 2008-03-18
Hi,

Have you checked Grip's settings to see what the correct directory is? 

BTW, forget MP3s, use [OGG]("http://www.fsf.org/resources/formats/playogg") instead.  Unlike mp3, ogg is an open format and has superior compression.  On average you can reduce file size by about 20% without sacrificing sound quality.

---

### Post by fredfjr on 2008-03-18
> **x1a4 said:**
> Hi,
BTW, forget MP3s, use [OGG]("http://www.fsf.org/resources/formats/playogg").  Unlike mp3, ogg is an open format and has superior compression.  On average you can reduce file size by about 20% without sacrificing sound quality.

This suggestion is good if he plans to keep the files on his hard drive.  Should he want to load them onto a mobile music player he'll have to make sure that player supports playing .ogg files.  Just something to keep in mind...

---

### Post by roderick on 2008-03-18
Any vendors making portable OGG players? I'd like that :)

---

### Post by x1a4 on 2008-03-18
> **roderick said:**
> Any vendors making portable OGG players? I'd like that :)

I use [iRiver]("http://www.iriver.com/") which is quite good.  [xiph.org]("http://wiki.xiph.org/index.php/PortablePlayers") has a pretty comprehensive list.

---

### Post by logos34 on 2008-03-18
> **CasPol said:**
> Grip is doing this fine, but when the ripping and converting is complete I cannot find the mp3 files anywhere on my hard drive ?

Verify your encoder executable path and commandline is correct.  Grip will still rip but it just won't encode anything if it can't find the codec/setting is wrong.  You should be using lame 3.97.

Here's a good howto:
[http://ubuntuforums.org/showthread.php?t=183125hp%3Ft=25151](http://ubuntuforums.org/showthread.php?t=183125hp%3Ft=25151)

---

### Post by CasPol on 2008-03-19
Grip rips fine, also encoding is set correctly. The only problem is that I cannot find the encoded file on the Hard Drive. I checked with "locate mp3" but yielded nothing.

Any more ideas?

---

### Post by logos34 on 2008-03-19
> **CasPol said:**
> Grip rips fine, also encoding is set correctly. The only problem is that I cannot find the encoded file on the Hard Drive. I checked with "locate mp3" but yielded nothing.

Any more ideas?

Post screenshots of config>rip>ripper tab and config>encode>encoder tab

---

### Post by CasPol on 2008-03-21
Thanks guys;

Found them with the help of "Beagle" .

---

