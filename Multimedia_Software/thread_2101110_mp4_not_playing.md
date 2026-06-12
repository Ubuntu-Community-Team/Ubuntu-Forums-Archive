---
title: "mp4 not playing"
date: 2013-01-03
forum: Multimedia Software
---

### Post by witblits1970 on 2013-01-03
i have a video on my box that is in MP4 format. mplayer nor any other video players  do not recognise and therefore not play the file.  how do i convert the file to AVI or divx format so i can watch the video?
 thanks

---

### Post by evilsoup on 2013-01-03
Do you have ubuntu-restricted-extras (or lubuntu-restricted extras for lubuntu, etc) installed? You can find it in the Software Centre (you may have to click 'show x technical items'), or from the command-line (press 'ctrl+alt+t' to bring up a terminal emulator window) you can use

```

sudo apt-get install ubuntu-restricted-extras

```

You'll have to enter your password either way.  This solves 90% of video and audio problems on Ubuntu.

---

### Post by andrew.46 on 2013-01-03
> **witblits1970 said:**
> i have a video on my box that is in MP4 format. mplayer nor any other video players  do not recognise and therefore not play the file.  how do i convert the file to AVI or divx format so i can watch the video?

I suspect you have an mp4 container that holds probably an audio stream and a video stream, at least one of which is giving you trouble (rather than the mp4 container itself). If evilsoup's suggestion does not fix the issue can you upload the file somewhere so I can have a look?

---

