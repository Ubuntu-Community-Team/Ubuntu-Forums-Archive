---
title: "Convert to MTV"
date: 2007-08-01
forum: Multimedia &amp; Video
---

### Post by slasherx2 on 2007-08-01
Hi all.

I recently purchased an MP4 player watch from some china website. The watch is really nice and all that but I have one problem. It needs the videos converting into MTV format to be able to play them. 

I was wondering if anyone knows of a converter I could install on my Ubuntu side of things to convert other video files into MTV??

I have tried running the converter that came with the watch through wine and crossover office but that didn't work :(

---

### Post by N008 on 2007-08-05
> **slasherx2 said:**
> Hi all.

I recently purchased an MP4 player watch from some china website. The watch is really nice and all that but I have one problem. It needs the videos converting into MTV format to be able to play them. 

I was wondering if anyone knows of a converter I could install on my Ubuntu side of things to convert other video files into MTV??

I have tried running the converter that came with the watch through wine and crossover office but that didn't work :(

yea i tried it thru wine too but it didn't work does anyone know how to get directx9? cause it's needed

---

### Post by clubsoda on 2007-12-23
Very interesting.

See this [description of the MTV movie format](http://wiki.multimedia.cx/index.php?title=MTV) for some details.  It looks like the Chinese and Korean device manufacturers are showing the finger to the European and U.S. patent holders (of MP4, MPG, WMV) by inventing a video standard of their own!! :-P Surely companies in the West would never be so pretentious or exclusive. :---)  However, it's not as high-tech or secretive as you might imagine, basically just raw images interspersed with MP3 for the audio track.  

MTV files were supported by **ffplay** (part of the **ffmpeg** package) but it seems to be broken these days:-```
ffplay /media/MPIO\ MG200/MPIO\ Sample\ Movie.mtv 
[mp3 @ 0xb7f71610]Could not find codec parameters (Audio: mp3, 128 kb/s)
```The header on that sample movie is not AMV but ALIAVI, which probably means that the MTV format has been extended to something like M-JPEG, i.e. a sequence of JPEG images instead of raw RGB, making for smaller files.  MJPEG is so close to MPEG-2 that it's not funny, but somehow fell through the cracks in terms of patent protection, perhaps because no official standard was released.  With the MPEG-2 patent portfolio itself winding down over the next few years, hopefully all of this will go away...  [quote="slasherx2"]I was wondering if anyone knows of a converter I could install on my Ubuntu side of things to convert other video files into MTV??[/quote]Ffmpeg should do it, although it may need an update, depending on your device.

Why would the MP3 hardware manufacturers cobble together a new video format for the sake of a few dollars of royalties?  Well, when you consider those guys are getting only $15 for your average $100 player *[Citation needed]* :twisted: it's a big deal!  Of course, they still end up paying royalties on the software which converts all those formats to MTV but software royalty rates are typically only one third of the cost. 

Then again, who wants to watch moving pictures at 128x128 pixels anyway? :confused:

---

### Post by patslap on 2007-12-27
Go to [http://www.bytessence.com/bamvc.html](http://www.bytessence.com/bamvc.html) and there is a linux version of .amv converter software.

See my other post at [http://ubuntuforums.org/showthread.php?t=650597](http://ubuntuforums.org/showthread.php?t=650597) for info on installation

---

