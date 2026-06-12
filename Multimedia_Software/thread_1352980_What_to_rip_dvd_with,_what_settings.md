---
title: "What to rip dvd with, what settings?"
date: 2009-12-12
forum: Multimedia Software
---

### Post by mrapoc on 2009-12-12
Basically 

What program is best for ripping dvds in your opinion

What settings?

I tried a few combinations, the program either didn't work, took ages or the finished video looked CRAP!

Storage size isn't too much of an issue, although I don't really want 10gb per dvd :P

I was looking at 2gb per dvd or something, but this looked terrible - how do pirates get away ripping to 700mb and it still looking good?

It will be for playback on stereo, but may as well rip to 5.1 in case of viewing in an 5.1 environment?

Cheers

---

### Post by SuperSonic4 on 2009-12-12
I would go with [handbrake (CLI)]("http://handbrake.fr/downloads.php") or k9copy.

x264 is a good video encoder but you may have to compile it yourself.

```
handbrake -i /dev/dvd -t 1 -e x264 -b 1024 -E ac3 -s 1 -o output.mkv
```

Where

[list]
[*]-i <device> = input device (ie the dvd drive)
[*]-e <encoder> = video encoder (I picked x264)
[*]-b  <num>= bitrate (higher the better but will lead to a larger file. I find 1024 (1Mbps) to be a good balance
[*]-E <encoder> = Audio encoder, ac3 is copy as is
[*]-s <num> = Subtitle track (leave out this option for no subs)
[*]-o <file> = output file
[/list]

Other options

[list]
[*]-B <num> = audio quality (not needed for ac3 - defaults to 160 for other encoders)
[*]-6 stereo,6ch = Mixing, in this case stereo and 5.1 sound.
[*]-S <num> = Target file size in MB
[/list]

You can find out more with ```
handbrake -h
```

---

### Post by mrapoc on 2009-12-12
gonna try

```
handbrake -i /dev/dvd -t 1 -e x264 -b 1024 -E ac3 -6 stereo,6ch -o BadBoys.mkv
```

cheers!

---

### Post by SuperSonic4 on 2009-12-12
> **mrapoc said:**
> gonna try

```
handbrake -i /dev/dvd -t 1 -e x264 -b 1024 -E ac3 -6 stereo,6ch -o BadBoys.mkv
```

cheers!

Looks ok to me, just be aware that the file may not be title 1.

You can also pass the -L flag instead of -t which will select the longest title

---

### Post by acron1 on 2009-12-24
I am not sure if it meets all of your requirements but DVD::RIP is what I use and it wotks quite well.

---

