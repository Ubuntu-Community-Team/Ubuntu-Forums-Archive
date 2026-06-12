---
title: "mp3s: incorrect times and bitrates after lucid install"
date: 2010-05-14
forum: Multimedia Software
---

### Post by pikeman47 on 2010-05-14
A few days ago I decided to do a fresh install of lucid on my computer. After doing so I noticed while importing my music into rhythmbox that the bitrate readings were wrong (i.e. an album of mp3s encoded at V2 displaying all at a bitrate of 96kbps) for my VBR files (CBR files do display correctly) and certain files were displaying extremely incorrect song lengths (i.e. a song that is actually 5:22 long displaying as 1186:57:35 long). Once noticing this, I investigated and saw that when opening the files properties in nautilus, the bitrates were still incorrect and the lengths of all songs (VBR and CBR) were displayed as 0. When analyzing the files with the program MediaInfo, it returns the proper bitrates and song titles, thus showing that it is not an issue with my files but with my system. Prior to installing lucid fresh, I was running karmic and never experienced any of these issues. Rhythmbox always used to display an average bitrate for VBR files (I assume it was an average, but by any measure it was much higher than the values being displayed currently). Does anybody know how I could go about fixing this problem because little things like this are a pet peeve of mine.

Thanks!

---

### Post by oxf on 2010-05-14
> **pikeman47 said:**
> A few days ago I decided to do a fresh install of lucid on my computer. After doing so I noticed while importing my music into rhythmbox that the bitrate readings were wrong (i.e. an album of mp3s encoded at V2 displaying all at a bitrate of 96kbps) for my VBR files (CBR files do display correctly) and certain files were displaying extremely incorrect song lengths (i.e. a song that is actually 5:22 long displaying as 1186:57:35 long). Once noticing this, I investigated and saw that when opening the files properties in nautilus, the bitrates were still incorrect and the lengths of all songs (VBR and CBR) were displayed as 0. When analyzing the files with the program MediaInfo, it returns the proper bitrates and song titles, thus showing that it is not an issue with my files but with my system. Prior to installing lucid fresh, I was running karmic and never experienced any of these issues. Rhythmbox always used to display an average bitrate for VBR files (I assume it was an average, but by any measure it was much higher than the values being displayed currently). Does anybody know how I could go about fixing this problem because little things like this are a pet peeve of mine.

Thanks!
Hi..

Well this isn't going to answer question as such. However, I can only say I had a lot of problems using Rhythmbox/soundjuicer under Karmic and Jaunty  much the same as you describe. I never got any answers here but searching around revealed that it was a common bug, something with Gstreamer if I remember correctly, which was never solved in Launchpad. 

I would get totally incorrect times and bitrates too exactly along the lines  you get (5 min track displayed as 30 mins etc, way off VBR's etc) I never looked at them using Media info so maybe they were correct all along...who knows? 
Yes a pet peeve indeed I switched to ruby ripper

---

### Post by pveurshout on 2010-10-31
This problem still exists in Maverick, although I must say I never had any troubles in Karmic. Does anyone know whether there's a fix for this already?

---

