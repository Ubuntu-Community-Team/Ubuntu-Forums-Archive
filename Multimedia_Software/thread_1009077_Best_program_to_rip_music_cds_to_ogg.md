---
title: "Best program to rip music cds to ogg"
date: 2008-12-12
forum: Multimedia Software
---

### Post by AmpersUK on 2008-12-12
I want to rip my entire music collection to the ogg-vorbis format. I only have around 250 CDs but it is a lot, and I am 69 so would like a program fast enough to complete the task before I go and meet the violin player in the sky.

I use Ubuntu 8.10. I have over a terabyte of hard disk unused space, and a fairly fast machine with two gigs of memory.

I last did this when I was a Windoze user using a "Creative" which was pretty fast.

---

### Post by kpkeerthi on 2008-12-12
[abcde]("http://ubuntuforums.org/showthread.php?t=109429")

---

### Post by logos34 on 2008-12-12
I use ABCDE too and think it's great, but it can can be a little frustrating for first-time users or those not entirely at home with the terminal.

Sound Juicer would probably be a better choice--you don't need anything fancy and it'll get the job done (and it has a gui).  To speed up the rip you can even disable cdparanoia in preferences (assuming your cds are in good condition)

[https://help.ubuntu.com/8.04/musicvideophotos/C/music.html#music-audiocds-ripping](https://help.ubuntu.com/8.04/musicvideophotos/C/music.html#music-audiocds-ripping)

---

### Post by AmpersUK on 2008-12-12
Thanks, I have downloaded it and tested it with one CD.

One question. It doesn't do Ogg-Vorbis, but I tried the lossless "flac" and that seems to play in Ubuntu but I am not sure if it will in my music player. Is there an add-on which will save to ogg-vorbis?

---

### Post by AmpersUK on 2008-12-12
I was answering logos34's post.

---

### Post by wolfen69 on 2008-12-12
sound juicer will save to ogg format which is what you want. if i am not mistaken, ogg-vorbis is a music file, and ogg-theora is a video file. why not just try it? it can't hurt.

---

### Post by logos34 on 2008-12-12
> **AmpersUK said:**
> Thanks, I have downloaded it and tested it with one CD.

One question. It doesn't do Ogg-Vorbis, but I tried the lossless "flac" and that seems to play in Ubuntu but I am not sure if it will in my music player. Is there an add-on which will save to ogg-vorbis?

maybe you're missing oggenc

sudo apt-get install vorbis-tools

now it should appear under 'cd-quality lossy' button

also do

sudo apt-get install ubuntu-restricted-extras


here's some other helpful links:

[https://help.ubuntu.com/community/CDRipping#Sound%20Juicer](https://help.ubuntu.com/community/CDRipping#Sound%20Juicer)
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

good luck

---

### Post by AmpersUK on 2008-12-12
> **wolfen69 said:**
> sound juicer will save to ogg format which is what you want. if i am not mistaken, ogg-vorbis is a music file, and ogg-theora is a video file. why not just try it? it can't hurt.

I couldn't understand your message but can now see why I can't.

I went to the owners website and looked at the preference screen and it has four radio buttons for the outpit, ogg-vorbis being one of them.

My version from the Ubunto "Applications/Add/Remove" menu is v 2.24.0 but has a pull-down menu instead of the radio buttons where the re are five choices:

.spx     Lossy
.wav    Lossless
.oga     CD Quality Lossy
.flac     CD Quality lossless
.m4a    CD Quality AAC

This time there is no Ogg. I thought .oga might be the same but this is listed as lossy and I thought ogg-v was lossless?

---

### Post by pseudonym on 2008-12-12
> **AmpersUK said:**
> I thought .oga might be the same but this is listed as lossy and I thought ogg-v was lossless?

Ogg is a lossy codec. FLAC, which you mentioned earlier, is lossless, but it creates large files (25MB+ depending on length) and is almost certainly not supported by any portable music players.

.oga and .ogg mean the same thing AFAIK (like .jpeg and .jpg). Maybe Sound Juicer just uses .oga? If you've installed vorbis-tools and ubuntu-restricted-extras you should have everything SoundJuicer needs.

---

### Post by gn2 on 2008-12-12
I use Grip which can be configured to run fully automated on insertion of a CD.
It will rip, encode, name and tag the tracks into a folder, which it will create and name, then spit the CD out when it's done.

---

### Post by FakeOutdoorsman on 2008-12-12
I've heard good things about Grip, but I use abcde to rip from cd to ogg vorbis.  It gets the job done and is fairly simple.  It will automatically tag and rename the files as well.  After I created a configuration file I just throw in the cd, open a terminal, and then run abcde.  For my configuration file, I copied the [ogg vorbis example](http://www.andrews-corner.org/abcde.html#ogg) from this excellent guide:

[abcde: Command Line Music CD Ripping for Linux](http://www.andrews-corner.org/abcde.html)

I recommend trying abcde, grip, and soundjuicer and use whatever you like most.

---

