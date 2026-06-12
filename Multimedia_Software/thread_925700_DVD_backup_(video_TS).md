---
title: "DVD backup (video_TS)"
date: 2008-09-20
forum: Multimedia Software
---

### Post by second.exodous on 2008-09-20
Hey, I want to backup some DVD's on ubuntu, but can't find out how to do it.  On mac I used to use MacTheRipper, it made a 1:1 copy of a DVD that I could burn to a blank DVD.  I have DVD+R DL, so I want a 1:1 copy, not shrunk down/encoded in anyway.

I have wine installed and have DVD Decrypter installed, but it can't see my DVD rom.  I've tried a few things but can't get that working.

So, anyway, what is the best way to make a 1:1 DVD backup.  I have wine and am willing to use a windows program to do it if needs be.

I want to say again I don't want to shrink or encode to a video file, I just want the video_ts and audio_ts folders that I can just burn to a dvd.

Thanx,
Stan

---

### Post by second.exodous on 2008-09-20
Ah, RTFM, I went to the appDB on DVDDecrypter and it works under win nt 4.0 mode, so I'm trying it right now.

---

### Post by iansane on 2008-10-07
You don't have to have all that special software. Apparently a dvd can be copied with the cp command if as you say, you don't want any extra compression or encoding. It's a matter of just copying the files that are on the dvd. You don't have to be able to decrypt or decode it to just copy it. I wish someone had told me this a long time ago instead of suggesting all these pain in the *** complicated programs.

I just tested on a copyright protected one which I think is legal. (one copy for home use.) Right?

```

cp /dev/sda1 movie.iso

```

Or I think I could have copied straight to my burner if the files fit. Not waisting a dvd to find out but it should be

```

cp /dev/sda1 /dev/sda0

```

or when it's mounted to /media/cdrom just go there and make an iso with all the folders and files that are in there.

---

### Post by cariboo on 2008-10-07
The simple command line way to do it is in a terminal type:

```
dd if=/dev/scd0 if=movie.iso
```

This will create an exact duplicate of your dvd

Jim

---

