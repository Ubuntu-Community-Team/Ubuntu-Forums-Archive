---
title: "m4v to dvd"
date: 2009-12-18
forum: Multimedia Software
---

### Post by Xswitch on 2009-12-18
Hi all...  I have scoured the net and haven't been able to find a solution to this conversion.  Handbrake allowed me to copy the video to my PC, but how do I copy the file to another dvd that plays in a standard dvd player?  Do I need to purchase software to do this?  

Thanks all...

---

### Post by qyot27 on 2009-12-18
When you say '.m4v', you could be referring to two separate things:

1) Standard MP4 container with H.264 or MPEG-4 ASP video and MP3, AAC, and/or AC3 audio.

2) Standard MP4 container with H.264 and AAC and/or AC3 audio, but encrypted because it's one of the non-Plus purchases from the iTunes Store*.

1) can be easily converted to DVD-compliant MPEG-2 and AC3 with ffmpeg (or HCenc for MPEG-2, if you want to run it in Wine, and Aften for AC3).  For 2), you're out of luck.  With 1), after you convert it to MPEG-2, you'll want to use a DVD authoring program to make sure the file structure is correct for DVD - it'll also handle making the menu.  Unfortunately I have pretty much zero experience with Linux-based DVD authoring apps.  Bombono DVD is the most promising one that I've tried, though.


*not all video purchases from iTunes are protected.  I'd wager that most of the Music Videos are in the Plus category, especially the free ones.  The TV episodes and whatforth are not, however.

---

### Post by FakeOutdoorsman on 2009-12-18
For a single video DVD without a menu.  First convert the video with FFmpeg and then do the authoring:
```
ffmpeg -i input.m4v -target ntsc-dvd output.mpg
dvdauthor --title -o dvd -f output.mpg
dvdauthor -o dvd -T
```
Now make the ISO file:
```
mkisofs -dvd-video -o dvdimage.iso ~/dvd
```
Then burn the ISO to DVD disc:
```
growisofs -dvd-compat -Z /dev/dvd=dvdimage.iso
```

---

### Post by howefield on 2009-12-18
> **Xswitch said:**
> ...how do I copy the file to another dvd that plays in a standard dvd player?

Download Devede with Synaptic Package Manager. It will handle m4v amongst several others.

---

### Post by stinger30au on 2009-12-18
to rip a dvd you need to install k9copy

sudo apt-get install k9copy

tell it to burn the data to hdd somewhere

burn the data back to dvd with k3b

sudo apt-get install k3b

burn to dvd -r discs

play in standard dvd player

have fun

---

### Post by driven1 on 2010-09-27
> **FakeOutdoorsman said:**
> Here's how I do it for a single video DVD without a menu.  First convert the video with FFmpeg and then do the authoring:
```
ffmpeg -i input.m4v -target ntsc-dvd output.mpg
dvdauthor --title -o dvd -f output.mpg
dvdauthor -o dvd -T
```
Now make the ISO file:
```
mkisofs -dvd-video -o dvdimage.iso ~/dvd
```
Then burn the ISO to DVD disc:
```
growisofs -speed=1 -dvd-compat -Z /dev/dvd=dvdimage.iso
```
I added *-speed=1* to the above command for use with lower quality discs.

I need a solution to this same challenge. A search turned up this thread. This was crazy easy. Thanks for the help. :popcorn:

---

### Post by @H.264 on 2011-01-19
...and how make it WITH menu?

---

### Post by Wobblybob on 2011-03-23
> **@H.264 said:**
> ...and how make it WITH menu?

DeVeDe will make menus and convert m4v to dvd iso

---

### Post by groovydaddy on 2011-04-16
I found this solution from Google on the Ubuntu forum; thanks for posting.  I'm getting an error when trying my conversion.  Apparently, there is a bug with Mencoder that is preventing DeVeDe from performing conversions from M4V to ISO.  Does anyone know where this problem should be reported, or if there is a workaround for this?

---

### Post by VMC on 2011-07-06
> **FakeOutdoorsman said:**
> For a single video DVD without a menu.  First convert the video with FFmpeg and then do the authoring:
```
ffmpeg -i input.m4v -target ntsc-dvd output.mpg
dvdauthor --title -o dvd -f output.mpg
dvdauthor -o dvd -T
```
Now make the ISO file:
```
mkisofs -dvd-video -o dvdimage.iso ~/dvd
```
Then burn the ISO to DVD disc:
```
growisofs -dvd-compat -Z /dev/dvd=dvdimage.iso
```

This worked perfectly. DeVeDe doesn't convert from m4p to mpg. So that doesn't work for home dvd players.

---

### Post by libspero on 2012-08-30
> **Wobblybob said:**
> DeVeDe will make menus and convert m4v to dvd iso

Sorry to drag up an old thread..  but just wanted to add that I can vouch for DeVeDe.

Just converted m4v's to playable DVD easily and with no hassle. 

Thanks for the thread and the advice!

---

