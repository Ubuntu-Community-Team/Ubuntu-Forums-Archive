---
title: "mplayer and mythlcdserver / lcdproc"
date: 2009-06-17
forum: Mythbuntu
---

### Post by Callandor64 on 2009-06-17
Hi everybody,

I use the internal myth player for live tv and recordings, but also have video clips that are played through mplayer.

Is there a way to get the mplayer details displayed on a pc case LCD display as is done by mythlcdserver during tv playback using the internal viewer?  At the moment only the system date and time are displayed during mplayer playback.  I understand that mythlcdserver runs as an lcdproc plugin/client.  Is there any way to extend the mythlcdserver functionality to scrape playback information form mplayer, or anything else that can achieve the same ends?

Cheers and beers,

Callandor64

---

### Post by ian dobson on 2009-06-19
Hi,

You probably want to look at the "-identify" and "-msglevel" options for mplayer. I'd imagine you'll need to kill mythlcdserver before starting mplayer then restart it when mplayer is finished. And call the script to start mplayer.

something like:-

#!/bin/sh
killall -9 mythlcdserver
mplayer -identify -msglevel 1 %0
mythlcdserver

Just an idea, I've never tried it myself.

Regards
Ian Dobson

---

### Post by Callandor64 on 2009-06-19
Hi Ian,

I agree that stopping mythlcdserver is important, however it doesn't seem that simple.  For one, mythtv checks for the server and tries to restart it pretty rapidly if it can't see it.

Also, the -identify option will print video file details to the terminal window, and this will then require hackery to spray onto the lcd display.  In particular, the progress through the file isn't massively human readable.

The problem is then piping this to lcdproc.

Thanks for taking the time to reply though!

Best regards,

Callandor64

---

