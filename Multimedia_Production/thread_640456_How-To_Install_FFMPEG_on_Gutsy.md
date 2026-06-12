---
title: "How-To: Install FFMPEG on Gutsy"
date: 2007-12-14
forum: Multimedia Production
---

### Post by philc on 2007-12-14
Yesterday I took some time to install FFMPEG on both my Debian Etch server and my Ubuntu Gutsy desktop.

My main aim was to support output for H.264 video, AAC audio in a QuickTime MOV container.

AAC is achieved with laac. H.264 through x264.

Of course I also built FFMPEG to support a multitude of other decode and encode options.

This is the Debian Etch tutorial:

[http://slashdot.org/~PhillC/journal/190325](http://slashdot.org/~PhillC/journal/190325)

It has more information about how, why and what you're doing.

This is the Ubuntu Gutsy write-up:

[http://slashdot.org/~PhillC/journal/190344](http://slashdot.org/~PhillC/journal/190344)

It really just lists the commands used. So, if you want to actually understand what you're doing, read the Debian Etch version first.

I hope this helps someone and please do let me know if you have any improvements on what I did.

---

### Post by FakeOutdoorsman on 2007-12-14
Also take a look at the Ubuntu wiki entry for [Ipod Video Encoding]("https://help.ubuntu.com/community/iPodVideoEncoding") which shows how to install and use ffmpeg.

---

### Post by philc on 2007-12-14
Thanks. That is a particularly useful tutorial regarding how to use FFMPEG for H264 encoding.

---

### Post by crush304 on 2007-12-14
[http://www.medibuntu.org/index.php]("http://www.medibuntu.org/index.php")

---

### Post by crush304 on 2007-12-14
you might also be interested in [http://www.debian-multimedia.org]("http://www.debian-multimedia.org") but I don't know what options their ffmpeg was compiled with

---

### Post by philc on 2007-12-14
> **crush304 said:**
> you might also be interested in [http://www.debian-multimedia.org]("http://www.debian-multimedia.org") but I don't know what options their ffmpeg was compiled with

I got all the FFMPEG dependencies from [http://www.debian-multimedia.org](http://www.debian-multimedia.org) by adding them to my sources.list, then grabbed the latest FFMPEG from SVN.

---

