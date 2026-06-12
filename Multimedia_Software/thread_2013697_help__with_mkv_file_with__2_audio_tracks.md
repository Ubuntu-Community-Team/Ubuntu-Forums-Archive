---
title: "help  with mkv file with  2 audio tracks"
date: 2012-07-01
forum: Multimedia Software
---

### Post by iceman30ad on 2012-07-01
i am probably trying to ask the wrong question so ill just tell you what i am trying to do 
 current set up ubuntu 12.04

have mkv file with dutch and english audio 

dutch is track 1 and english is track 2

xbmc will only play track 1 and i need it to play track 2 for my daughter

so question is how to set xbmc to play only english tracks 
or how to swap track 2 in to track 1

---

### Post by ron999 on 2012-07-01
> **iceman30ad said:**
> ... to play only english tracks 
or how to swap track 2 in to track 1
Hi
Consider using **mkvmergeGUI** to make a new mkv file...
Either import
video track + English audio track only
or import
video track + English audio track 1 and Dutch audio track 2
```
sudo apt-get install mkvtoolnix-gui
```

---

### Post by alenis on 2012-07-01
I can't answer your first question because I don't use xbmc.

If it doesn't let you choose the audsio track, open the mkv file with mkvmerge gui, click on the second (english) audio track, and select "yes" in the "default track flag" (or something like that: I am using the Italian verison right now), then click start muxing. At the end, you shuld hav ethe same file with the english track as default. If it doesn't work, use mkvmerg egui to remove the dutch track (just click on the checkbox and remove the checkmark). Start muxing and then play. 

Or install vlc and play the original file with it. It easily lets you choose audio tracks.

---

### Post by iceman30ad on 2012-07-01
thank you both 
 @alenis vlc works wonders but its not a picture orented gui which helps keep my daughter busy keeping noise in the back ground while she plays in her room with out me having to find the next file for her

---

