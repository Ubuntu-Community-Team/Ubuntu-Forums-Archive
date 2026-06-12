---
title: "How can I burn a .AVI to a 4GB DVD?"
date: 2007-06-23
forum: Multimedia &amp; Video
---

### Post by hyrule_man on 2007-06-23
I have a DL drive, but those things are expensive!! O_O  So... Yeah.. Topic..

---

### Post by Schalken on 2007-06-23
For the purpose of playing with a computer or a DVD player? In other words, as a video DVD or a data DVD, respectively?

---

### Post by hyrule_man on 2007-06-23
I'm wanting to play it in a DVD player, or my 360, OR my PS2... Whatever gets it on my TV screen... Lol.

---

### Post by lukew on 2007-06-23
> **hyrule_man said:**
> I have a DL drive, but those things are expensive!! O_O  So... Yeah.. Topic..

Hi,

It is actually very simple. First you need to convert all media types to mpg. This will work for a lot of file types not just avi's.


ffmpeg -i myfile.avi -target pal-dvd /tmp/dvd.mpg
	
Then make an iso of your movie.

mkiso movie.mpg
	

Or if you havce multiple mpgs to burn and would like a menu systsem

todisc -files 1.mpg 2mpg -titles "One" "Two" -out movie_dvd

This will create raw files which you can burn with k3b as a dvd project.


TOVID

[http://tovid.wikia.com](http://tovid.wikia.com)

Install Dependancies

sudo apt-get update && sudo apt-get install mplayer mencoder mjpegtools ffmpeg python python-dev python-wxgtk2.6 python-imaging imagemagick dvdauthor dvd+rw-tools vcdimager transcode sox normalize-audio txt2tags lsdvd python-cairo

install tovid.

tovid also have a gui was helps with a lot of the above. (tovidgui)

Luke

---

### Post by kelvin spratt on 2007-06-23
if you don't want menus give DEVEDE a go, you do not need to convert the image first, i use it all the time save as an ISO. and burn image. You can do a short test preview and check the results, if its not already in synaptic download from here
[http://www.getdeb.net/](http://www.getdeb.net/)   when you've done your preview if you have a sound problem you can go to 
the DEVEDE site at the bottom or the page is a patch for mencoder as it has a bug but do the preview first as i don't have the problem with my system the Dvd when burned should play in all Home DVD players and computers i would sugest you use verbatim to burn too as i have 100% success with this media.

---

### Post by hyrule_man on 2007-06-23
Hey, thanks a million man. I booted up DEVEDE, started burning, woke up, wrote "AKIRA" on the disk, threw it in my 360, and now I'm watching Akira on my TV. Thanks again! :KS

---

### Post by kelvin spratt on 2007-06-23
your welcome

---

