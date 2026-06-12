---
title: "Ripping DVD quality settings"
date: 2008-11-12
forum: Multimedia Software
---

### Post by muzikoverdose on 2008-11-12
This is more of a curiousity, so please feel free to delete/remove this post if required. I'm in the process of backing up my DVD collection to avi files (im very low on space).  Now, if I were to hypothetically download a movie, then it's more than likely that this film will have a resolution of over 640*480 and a bitrate over 800, all in a 700mb pack.  No matter what I do or what program I use (tried AcidRip, dvd::rip and im now onto OGMrip) I can't get settings this high for 700mb.  Can anyone shed any light?  I can't seem to find any conclusive info around the internets. 

Many thanks in advance.

---

### Post by xc3RnbFO8P on 2008-11-12
Here is a example (in Avidemux).
Xvid (mpeg-4 ASP xvid4)

Configure:
Main> Two Pass Video Size (700 mb, max 100 min)
Motion & Misc:
Motion search precision, 6  Ultra High
VHQ mode, 4 Wide Search
Check **As Input**

Filter:
Noise
crop

Audio:
Mp3 (ABR)

---

### Post by muzikoverdose on 2008-11-12
Oh cool i'll give it a go soon & run a comparison with OGMrip.  Thanks for the help.

---

### Post by muzikoverdose on 2008-11-12
I had a go at it, but have another question.  The mounted ISO has 4 vob parts that make up various parts of the film.  AviDemux only seems to be able to do one at a time. Is there a way to make it see all parts as a whole?  If I click on any part but the first, it asks if I want to append the mpegs.  if I click yes and hit the playback, nothing has been added to the film.

---

### Post by xc3RnbFO8P on 2008-11-13
Use DVD:RIP to rip dvd to hd.
DVD:RIP
Storage:
New Project (name of the DVD)
Choose DVD device 
Copy data from DVD to harddisk before encoding
Rip Title:
Read DVD table of contents
Rip selected titles chapters
/home/your folder/dvdrip-data

---

