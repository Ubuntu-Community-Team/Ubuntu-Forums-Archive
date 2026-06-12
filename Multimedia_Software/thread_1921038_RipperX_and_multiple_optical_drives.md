---
title: "RipperX and multiple optical drives"
date: 2012-02-06
forum: Multimedia Software
---

### Post by Welly Wu on 2012-02-06
I have an ASUS N61JV-X2 notebook PC with Crucial 8 gigabytes of dual channel DDR3 1,066 MHz SDRAM and an Intel 2nd Generation 2.5" 34nm MLC NAND Flash X25-M 160 gigabyte Solid State Drive. I also have a LG GSA-5163D external USB 2 Super-Multi dual layer DVD burner and CD burner drive. I use RipperX and Sound Juicer. Sound Juicer allows me to specify which optical drive that I want to rip and encode into .FLAC loss less audio files. RipperX does not have that option in its configuration. Is there a way for me to specify my LG optical drive to be used in conjunction with RipperX? The reason why I ask is due to the fact that the LG is much much faster and I prefer to use RipperX because it has access to CDDB which pulls the CD metadata much more reliably than MusicBrainz which Sound Juicer uses. It seems that CDDB has a larger database of CDs than MusicBrainz. Please reply if you can help me with specific step-by-step instructions on how to use my LG optical drive with RipperX. Thank you.

---

### Post by Rodney9 on 2012-02-06
Asunder and Ripoff both will let you select where to extract to.

Rodney

---

### Post by shawnbrito on 2012-10-25
I know this thread is pretty old.. But for others out there - there is a simple way of getting this done.. There is a way to load the designated CDROM drive...  
Simple goto the configurations -> WAV Tab -> Extra Command Options...
and type:
**[COLOR=Red]-d  "/dev/srd03"[/COLOR]**
Or what ever your CDROM drive name is...  Thats it...

---

