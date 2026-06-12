---
title: "How to rip audio cds to image?"
date: 2007-08-19
forum: Multimedia &amp; Video
---

### Post by shaggy999 on 2007-08-19
I'm trying to rip an audio cd to an image, but nothing is working. I was told to use the following command:

```
dd if=/dev/cdrom of=image.iso
```

But this is what I get:


```
dd: reading `/dev/cdrom': Input/output error
0+0 records in
0+0 records out
0 bytes (0 B) copied, 0.00401978 seconds, 0.0 kB/s
```

I was thinking that maybe my drive was referenced as something else, so I checked fstab and it lists my drive as /dev/scd0, but when I try that I get the same error. Anybody have any idea what's going on?

---

### Post by Bachstelze on 2007-08-19
Same error here, I think it's because Audio CDs have no filesystem on them, so you can't copy their data directly.

---

### Post by shaggy999 on 2007-08-19
That sucks if it's true. But I know audio CDs can be ripped as images because I can do it in windows. There's gotta be a way to do it.

---

### Post by rsambuca on 2007-08-19
What if you just put in the audio cd, and then when it appears on your desktop, right-click it and press copy disc, and then copy to file?  It seemed to work on my setup.

---

### Post by rsambuca on 2007-08-19
Hmmm... doesn't seem to work afterall.  The iso image is exactly the same size as the audio cd, but when I try to do anything with the iso file, I get an error stating it is not an iso9660 file.  Maybe if you copy to .bin or .cue or .raw instead?

---

### Post by MetalMusicAddict on 2007-08-19
> **rsambuca said:**
> What if you just put in the audio cd, and then when it appears on your desktop, right-click it and press copy disc, and then copy to file?  It seemed to work on my setup.

This works but it doesn't retain the data for the disk. ie: track names.

The process below will get you a image of your audio CD that retains the disk info. "--device" will be specific to your machine.

With the disk in, the 1st command is:
```
[SIZE="1"]cdrdao read-cd --read-raw --datafile ~/image.bin --device /dev/scd0 --driver generic-mmc-raw ~/image.toc[/SIZE]
```

2nd command is:
```
[SIZE="1"]cdrdao write --device ATAPI:0,0,0 ~/image.toc[/SIZE]
```

Now what's weird is this is almost the same process as right-clicking on the disk and coping the disk in that it create a image and .toc file but the disk info is gone. So odd.

[THIS]("http://www.linux-gamers.net/modules/wiwimod/index.php?page=HOWTO+CD-IMAGES") page was used as reference. Theres also a step in there to make a .cue file. If you do that step a you can find a .deb for bin2iso [HERE]("http://zedmatrix2.free.fr/bin2iso/bin2iso_1.9b-3_i386.deb"). (converted with alien)

---

