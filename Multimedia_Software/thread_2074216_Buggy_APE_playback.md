---
title: "Buggy APE playback"
date: 2012-10-21
forum: Multimedia Software
---

### Post by PippoPalmieri on 2012-10-21
Hello everyone,
I recently upgraded to 12.10 and my ape music started acting weird.
It is recognized by my music player, clementine, but the player cant define the track length and it can't play it properly. I tried several players, they all have the same issues, except for VLC. Why? Maybe VLC doesn't use gstreamer-ffmpeg?
I started clementine from terminal to check for errors during playback, but there were none, it just skipped to the next track after a buggy playback of the first few seconds.
I tried reinstalling gstreamer, to no avail.
Is there someone who can help me? I have no idea how to fix this.
Thank you!

By the way, I can't even convert my ape files to flac, because then the flac file would sound just as buggy as the ape (other flac files work though).
I don't even understand why my friend rips lossless music to ape, that's one lame format. :confused:

Oh, and mp3 and other formats work just fine.

---

### Post by shantiq on 2012-10-21
just a thought is ape  [mac] [stands for Monkey's Audio Console]  installed on your upgrade setup


if you run this in your terminal


```
mac
```


do you get?

```
0000:~$ mac
--- Monkey's Audio Console Front End (v 3.99) (c) Matthew T. Ashland ---
Proper Usage: [EXE] [Input File] [Output File] [Mode]

Modes: 
    Compress (fast): '-c1000'
    Compress (normal): '-c2000'
    Compress (high): '-c3000'
    Compress (extra high): '-c4000'
    Compress (insane): '-c5000'
    Decompress: '-d'
    Verify: '-v'
    Convert: '-nXXXX'

Examples:
    Compress: mac.exe "Metallica - One.wav" "Metallica - One.ape" -c2000
    Decompress: mac.exe "Metallica - One.ape" "Metallica - One.wav" -d
    Verify: mac.exe "Metallica - One.ape" -v
    (note: int filenames must be put inside of quotations)
```


if not install **[==>it]("http://ubuntuforums.org/showthread.php?t=1480971&highlight=ape+shantiq")**



it **might** improve things; just av a go :KS  it might be the programs you use need it there   and the upgrade might have knocked it out of the way

---

### Post by PippoPalmieri on 2012-10-21
I already have it and i get the same exact output...

---

### Post by shantiq on 2012-10-21
---------------

---

### Post by AndreyKhl on 2012-10-22
I have exactly the same issue on a newly installed Ubuntu 12.10 x64. APE playback jammed in all players, which I've tried: clementine, rhytmbox, totem.

All other audio and video formats and containers (mp3, flac, avi, mkv, etc.) plays normally.

Any clues?

---

### Post by Panagiotis Papadakos on 2012-10-23
I also have the same problem. And mac reports:

```
--- Monkey's Audio Console Front End (v 3.99) (c) Matthew T. Ashland ---
Proper Usage: [EXE] [Input File] [Output File] [Mode]

Modes: 
    Compress (fast): '-c1000'
    Compress (normal): '-c2000'
    Compress (high): '-c3000'
    Compress (extra high): '-c4000'
    Compress (insane): '-c5000'
    Decompress: '-d'
    Verify: '-v'
    Convert: '-nXXXX'

Examples:
    Compress: mac.exe "Metallica - One.wav" "Metallica - One.ape" -c2000
    Decompress: mac.exe "Metallica - One.ape" "Metallica - One.wav" -d
    Verify: mac.exe "Metallica - One.ape" -v
    (note: int filenames must be put inside of quotations)
```

---

### Post by AndreyKhl on 2012-10-24
It seems the problem is in gstreamer-0.10's ape plugin integrated in the ubuntu 12.10's repository.
I've tried vlc to play ape+cue - works great, but vlc has one very annoying bug: when it starts playing any song it changes song's title to something strange, particularly "F:" (sic!). I really do not understand where vlc gets that string on linux. :confused: :)
But I found that deadbeef player has no dependencies to gstreamer (just like vlc) when playing ape. So deadbeef plays ape+cue while gstreamer dependend players can't.

---

### Post by PippoPalmieri on 2012-10-25
This looks like an issue for a lot of people....
Did someone find a workaround?

---

### Post by Panagiotis Papadakos on 2012-10-25
I opened a bug:
[https://bugs.launchpad.net/ubuntu/+source/gstreamer0.10-ffmpeg/+bug/1071263](https://bugs.launchpad.net/ubuntu/+source/gstreamer0.10-ffmpeg/+bug/1071263)

---

### Post by mogorvabb on 2012-11-25
same here.. I use will audacious with built in codecs..

---

### Post by andrew.46 on 2012-11-28
Perhaps try MPlayer / SMPlayer...

---

### Post by mogorvabb on 2013-02-05
audacious play ok /built in codec/

this is gstreamer bug..

The problem is specific only 449 Kbps 44.1 KHz 16 bits 2 Monkeys Audio chan figure beginning at the beginning of the buffer /paused/ would be as if he is ok.

Previous versions /dapper,hardy, lucid/ were ok

---

