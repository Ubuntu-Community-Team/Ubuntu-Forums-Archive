---
title: "ripping and encoding to mp3 problem"
date: 2007-08-24
forum: Multimedia &amp; Video
---

### Post by christianvaldes on 2007-08-24
I have migrated from Fedora Core 5 to Ubuntu.

Grip

How do I get the mp3 encoding working?

Sound Juicer

How do I get the mp3 encoding working?

---

### Post by bapoumba on 2007-08-24
I'm assuming you have installed feisty.
Please install **ubuntu-restricted-extras** (a meta package for most of the codecs). You need to enable the multiverse repositories.

---

### Post by christianvaldes on 2007-08-24
I seem to having a problem with the ripping into wav.
They cd rips but sounds horrible. 

Playing it from the cd player and it sounds horrible.

The cd is a brand new one and I also just 3 others.  The same thing happens.

I believe the problem is that the cd is not configured to play properly...

never mind the ripping....

please help

---

### Post by christianvaldes on 2007-08-24
cdda2wav -D /dev/hdc -t 1+1

I run this command and I can rip a file to wav but it is really scratchy and sounds horrible

I actually got the ripping and the mp3 encoding working but it sounds horrible cause the problem is right from the initial wav file

hope someone can help

---

### Post by christianvaldes on 2007-08-25
my motherboard is an m2npv-vm
has on board soundcard
I just tried installing ubuntu on my laptop and did not even do any updates and its playing the audio perfect and ripping with sound-juicer....

someone help

It must be a hardware issue with my am2 processor m2npv-vm motherboard....
I will try another soundcard and see it I get success........

---

### Post by christianvaldes on 2007-08-26
I narrowed down the problem to the wrong driver is being used for the DVD Writer.

DVD/CD Rewritable Drive Unit
SONY
MODEL NO DWQ120A

I swamped this drive with another DVD Drive and the issue has been solved.
Thou I have not bothered fixing the driver problem with the former drive.
If anybody knows how to do that, then it would be a good idea to post it here so the next person will know what to do.

---

### Post by bapoumba on 2007-08-27
Thanks for posting the way you got out of this problem. Sorry I could not help you better than this :)

---

### Post by christianvaldes on 2007-08-30
> **bapoumba said:**
> Thanks for posting the way you got out of this problem. Sorry I could not help you better than this :)

you helped plenty
just a strange problem after all the steps were taken and in turned out that the DVD writer was another problem that came up

---

