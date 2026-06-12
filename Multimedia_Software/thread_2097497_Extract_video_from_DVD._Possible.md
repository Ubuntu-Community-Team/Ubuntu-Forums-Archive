---
title: "Extract video from DVD. Possible?"
date: 2012-12-23
forum: Multimedia Software
---

### Post by Ron Jones on 2012-12-23
I have a series of talks on DVD. Each DVD has two or three menu items. For example:
DVD 1 has: lecture 1, lecture 2 and lecture 3. For a total of 60 lectures on 25 [or so] disks.

I want to choose and extract my 10 favourite lectures, then burn them to 4 DVD's.

Creating the DVD from the separate files is the easy part [for me], as I will simply use DeVeDe to build the ISO.

It's the extraction of specific titles from the disk, to a file usable by DeVeDe that I need help with.

Can anyone recommend an effective way to do this?

For the record, there are no Copyright or DRM issues with these media files (it's a series of Bible studies that are freely distributable).

Thanks,

---

### Post by silverhaze06 on 2012-12-30
You can try vlc to record the video stream. or just type dvd ripper into the software center and choose from one of the many different programs out there. Such as, Thoggen, AcidRIP, DVD::RIP, HandBrake, k9copy, and ogmrip.

---

### Post by Merrattic on 2012-12-30
mplayer/mencoder can help you here. If you want to play a particular title with mplayer, say the fifth title, the syntax is:

```
mplayer dvd://5
```With this knowledge you can then extract the title from the dvd using mencoder, for example:
```
mencoder dvd://5 -oac copy -ovc copy output.mpg
``` (from memory, not tested ;))

---

### Post by SR_ELPIRATA on 2012-12-30
I've used the VLC option as well, and is quite interesting, being able to record something that you are seeing at the same time is quite fun. VLC is very powerful option. You have to open the advanced options, or you wont see the record option (IIRC)

ELP

---

### Post by andrew.46 on 2012-12-30
Not renowned for its straightforward commandline but you can use *tccat* to pull out specific tracks from a dvd, an example here:

[http://www.andrews-corner.org/fist.html#video](http://www.andrews-corner.org/fist.html#video)

Don't know if this will then work with DeVeDe as I have not used this application.

---

### Post by Ron Jones on 2013-01-02
In the end... to keep it simple, I loaded the DVD, dragged-and-drop the .VOB file over to the desktop, renamed it to *.mpeg, then used DeVeDe to mix-and-match mpeg files and spit out an ISO for each of the combinations I wanted.

Thanks all!

---

