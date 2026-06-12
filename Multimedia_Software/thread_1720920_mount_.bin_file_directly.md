---
title: "mount .bin file directly?"
date: 2011-04-03
forum: Multimedia Software
---

### Post by jiapei100 on 2011-04-03
Hi, all:

I happen to come across a requirement to mount a .bin file, instead of a .ios one. I followed the following 2 messages:

[http://ubuntuforums.org/showthread.php?t=93706&page=2](http://ubuntuforums.org/showthread.php?t=93706&page=2)
[http://www.linuxforums.org/forum/ubuntu-linux/97586-mount-cue-bin-image.html](http://www.linuxforums.org/forum/ubuntu-linux/97586-mount-cue-bin-image.html)

which needs to convert the original .bin file to a .ios file first by commands:
```
sudo apt-get install bchunk
cd [directory of your image]
bchunk image.bin image.cue image.iso
```

Afterwards, I can mount it using some tool like gISOMount or Gmount-iso.

My question is, is there a method to mount .bin file without converting to .iso?


Rgds
JIA

---

### Post by rocksockdoc on 2012-01-07
> **jiapei100 said:**
>  is there a method to mount .bin file without converting to .iso?

I just mounted the bin file without converting to an iso first over here:

[LIST]
[*]Desktop Environments: [SOLVED]                          [What player or converter do I use to play/convert a 'bin' and 'cue' video file?]("http://ubuntuforums.org/showthread.php?t=1905315"), by rocksockdoc
[/LIST]
I also converted it to an iso and mounted that too.

So, both work just fine.
 [IMG]http://ubuntuforums.org/attachment.php?attachmentid=210388&stc=1&d=1325930288[/IMG]

---

