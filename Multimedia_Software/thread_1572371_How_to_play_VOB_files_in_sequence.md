---
title: "How to play VOB files in sequence"
date: 2010-09-11
forum: Multimedia Software
---

### Post by BMU1 on 2010-09-11
I'm new to this. The VIDEO_TS folder has a bunch of VOB files sequentially names along with BUP and IFO files. But when I start up VLC and choose 'Open Dir' and point to the VIDEO_TS file, it plays a short trailer of the movie and does not move onto the rest of the VOB files. Is there a was to play them sequentially? or is the only way to select the files in the order in which to play them and then play them all?

---

### Post by mc4man on 2010-09-11
Some versions of vlc may have trouble if opening a VIDEO_TS  from vlc as a dir. (though it should work.

You could try opening vlc and then dragging and dropping the VIDEO_TS onto vlc.
or
From vlc -> Media -> Open Disc and for Disc device click on and browse to your VIDEO_TS or the folder holding the VIDEO_TS  then click 'open' -> 'play'. Don't browse inside the VIDEO_TS 

screen shows browsing to the containing folder.

The other possibility is the dvd navigation is the issue, whether from the dvd authoring or related to your rip.

If so and if you know the title number than that can also be set - see screen, Chapter can be 0 or 1 to start at beginning

You'll also notice that by clicking 'show more options', that the address is also shown, that can be used from the cli
Ex - open the movie with debug output
> vlc -vv  dvd:///home/doug/Desktop/NOC0NNW1/VIDEO_TS

or movie - title1 - chapter 1 
> vlc dvd:///home/doug/Desktop/NOC0NNW1/VIDEO_TS@1:1

---

### Post by mc4man on 2010-09-11
d. posted, might as well use

Edit:
If you don't know the titleset for the main movie or just want to start directly in movie, no menus, then you can try clicking the No dvd menus box (dvdsimple

a cli is also seen in screen

---

### Post by BMU1 on 2010-09-18
**mc4man** - wow! thanks for that detailed response. I did open disk and browsed to the folder containing the VIDEO_TS folder and changed the starting position video=1 and chapter=1 and it started from the first VOB file. I havent watched the entire movie yet but hopefully it will play in sequence.

**wcharlot** - The VIDEO_TS folder contains BUP and IFO files as well.

---

