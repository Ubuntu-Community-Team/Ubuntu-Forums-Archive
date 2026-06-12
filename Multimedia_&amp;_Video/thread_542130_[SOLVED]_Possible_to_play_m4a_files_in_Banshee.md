---
title: "[SOLVED] Possible to play m4a files in Banshee?"
date: 2007-09-03
forum: Multimedia &amp; Video
---

### Post by motoperpetuo on 2007-09-03
I've got about 25gb of music that I ripped into m4a in iTunes when I was exclusively a Windows user (yes, it eventually occurred to me that it would probably be better to rip CDs to mp3, but too late). 

My m4a files play just fine in gxine, but I hate the interface (I think I had to download something to get it to work, but it does now). Banshee's interface is awesome, but it won't play my m4a's, only the 20% or so of my music that is in mp3 format. I'm hoping I won't have to re-rip hundreds of CDs or convert from one lossy format to another to get my music that's currently in m4a format to work on Banshee. 

Any ideas? I imagine this must be a common problem, but I haven't been able to find anything that addresses it specifically here. Thanks!

---

### Post by motoperpetuo on 2007-09-03
ok, so i installed amarok, and it seems to play my m4a's just fine and with a much better interface for music than gxine. wonder why they won't play on banshee. maybe because they're on an NTFS partition?

---

### Post by LameHephaistos on 2007-09-18
Could someone who knows the answer to the original question post it (if it exists)? I much prefer banshee to amarok but I can't figure out how to to get m4a's to play in it either. I'd like to keep using banshee if I can. Thanks.

---

### Post by LameHephaistos on 2007-09-20
Well, I got it working using automatix2. Not sure what package it installed that I hadn't already, but anyone who's having trouble getting proper codecs installed should definitely try it out. [http://www.getautomatix.com/](http://www.getautomatix.com/)

---

### Post by zmjjmz on 2007-09-21
I installed the legal audio codecs, but it still won't work... does this mean I need the AUD-DVD codec?

---

### Post by deruberhanyok on 2007-11-20
I realize this is an old post, but, since an answer was never posted, here's one: Banshee uses gstreamer. It will play M4A files just fine if you install the right gstreamer plugins package, in this case it should be 'gstreamer0.10-plugins-bad-multiverse'.

First you have t go to system/admin/software sources and make sure the 'multiverse' repository is enabled. If it is not, enable it and let it rebuild the package listing.

Then go into add/remote programs, select 'show all available' from the top right drop-down box and search for 'gstreamer.' Currently, fourth on the list is "GStreamer plugins for aac, xvid, mpeg2, faad," that's the one you want.

You could also install it using synaptic. After making sure the multiverse repository is enabled, just search for 'gstreamer0.10-plugins-bad-multiverse'.

---

### Post by AJerman on 2007-11-23
Thanks for posting this. I had been looking for what the packages were called in Gutsy. I found a lot of links pointing to the faad plugins, but those aren't accurate on Gutsy. gstreamer0.10-plugins-bad-multiverse worked perfect.

I know I really need to convert my m4a crap to something else, at least mp3, but I haven't gotten around to it.

---

