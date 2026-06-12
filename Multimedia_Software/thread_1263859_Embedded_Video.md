---
title: "Embedded Video"
date: 2009-09-11
forum: Multimedia Software
---

### Post by Geffers on 2009-09-11
I would like to save a news clip embedded in a BBC web page.

I know how to use get_iplayer but I am not sure which, if any, news program the clip appeared in.

The page is still available, initial attempts to save something result in a .swf file but Totem gives the following error;

> 'GStreamer encountered a general supporting library error', 

VLC doesn't do anything.

If I drag and drop the .swf onto firefox I get > 'This content doesn't seem to be working, try again later'.

ffmpeg gave the following when I tried to convert it;

> [swf @ 0x89a2b00]Compressed SWF format not supported
/media/IOMEGA/9player.swf: I/O error occurred
Usually that means that input file is truncated and/or corrupted.

Can these be saved or are they locked in some way.

I am not particular about quality so any filetype would be acceptable.

Geffers

---

### Post by FakeOutdoorsman on 2009-09-11
What is the URL that the video is on?  Is it a UK only video?  I know BBC often restricts video viewing to UK only.

---

### Post by Geffers on 2009-09-12
> **FakeOutdoorsman said:**
> What is the URL that the video is on?  Is it a UK only video?  I know BBC often restricts video viewing to UK only.

I am based in the UK.

The URL is [http://news.bbc.co.uk/1/hi/uk/8234801.stm](http://news.bbc.co.uk/1/hi/uk/8234801.stm)

Reading on the net someone suggested to enter about:cache?device=disk into firefox.

After emptying the cache first I did so, there is the following line;
> [http://news.bbc.co.uk/player/emp/2.14.10344_10753/9player.swf](http://news.bbc.co.uk/player/emp/2.14.10344_10753/9player.swf)
 but if I use firefox's menu item of 'save link as' I get > RME1ZG_n.xhtml.part

There are no other .swf listed so am baffled why the 'save' defaults with a .part extension.

It appears that Firefox's 'save link as' gives a part extension for every listed cache entry, even jpg and gif files

Geffers

---

