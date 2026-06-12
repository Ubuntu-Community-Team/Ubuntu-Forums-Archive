---
title: "Problems with Handbrake"
date: 2008-11-18
forum: Multimedia Software
---

### Post by king vash on 2008-11-18
I have installed Handbrake from source (SVN 1924 and 1926) and have problems with random exiting during conversion. 

running "ghb" (the gui) from terminal I got 
"segmentation fault" or something similar

The last chapter of all my movie seem to have zero length and only a few blocks (HandBrakeCLI -i /media/cdrom0/VIDEO_TS -t 0) removing this chapter may or may not help.

Repeatedly trying to convert the dvd will eventually result in a successful conversion.

I have attached a log (~/.config/ghb/EncoderLogs) of one of the conversions.

---

