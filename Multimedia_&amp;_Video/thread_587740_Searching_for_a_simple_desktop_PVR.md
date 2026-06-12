---
title: "Searching for a simple desktop PVR"
date: 2007-10-23
forum: Multimedia &amp; Video
---

### Post by brettg on 2007-10-23
Hey All

I'm just revisiting an old chestnut that I have been bashing my head against intermittantly for the last couple of years.

The goal. To record TV from my analog BT48 card [Avermedia 98] 

Firstly, you should know that this is for a desktop PC, not a loungeroom based media extender, therefore the MythTV/FreeVo style options are not appropriate.

What I want is a small application through which I can watch TV either fullscreen or in a window. I currently do this using either vlc/v4l, KdeTV or TVTime.

The problem: None of these have an easily accessible record function.

I would like to be able to press a "red record button" to start recording whenever it takes my fancy.

I've mucked about with vlc/v4l in pvr mode but as far as I can tell this only works from the command line and does not allow for simultaneous viewing of the stream because it simply redirects stdout from the screen to a file or IP address.

The windoze craplet that came with the card way back in 98 does what I want, but I simply cannot find a simple TV viewer that can also record at request for linux.

Does anyone have any recommendations that might suit? Maybe I'm not using vlc properly? Maybe there is a tv app that I haven't found via googling.

Any input would be most welcome!

---

### Post by msubzwari on 2007-10-23
Check out DVR

[http://www.pierrox.net/dvr/](http://www.pierrox.net/dvr/)

It has a video preview feature during capture as seen on screen shots here.

[http://www.pierrox.net/dvr/screenshots/3.99.3/](http://www.pierrox.net/dvr/screenshots/3.99.3/)

see the second last screen shot.

Cannot say how good or bad this software is though as have not used it personally.

---

### Post by brettg on 2007-10-23
Hi

Thanks for the input. 

I have looked at DVR in the past, but gave up when I discovered that when you install the package no effort is made whatsoever to inform the new user what the actual executable file is called. man dvr returns nothing, the website returns nothing, locate pvr likewise,

Anyway, after your post I decided to re-investigate and it appears nothing has changed. 

However, this time I looked a bit further and found a link on their site to their old depreciated website. It was on there that I found an oblique reference to "dvr-qtgui". 

Now there's an intuitive name for you.

I certainly hope that the rest of the project is presented better than that but I will now re look at dvr and see how it goes. 

Thanks again

---

