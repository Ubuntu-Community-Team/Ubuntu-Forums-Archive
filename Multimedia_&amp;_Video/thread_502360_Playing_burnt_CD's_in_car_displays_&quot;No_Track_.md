---
title: "Playing burnt CD's in car displays &quot;No Track Title&quot;"
date: 2007-07-16
forum: Multimedia &amp; Video
---

### Post by frediE on 2007-07-16
I am using serpentine 0.7-4ubuntu3 (feisty) to burn an Audio CD and when I play it in my car it displays "No Track Title".  It sounds as though it is missing the CD-Text but not sure.  I also tried Brasero with no luck.  I know I have done this before because most of the CD's in my car display the Track Title and Disk Title, not sure what has changed.

Any thoughts or hints would be great.  Thanks!

---

### Post by wolfen69 on 2007-07-16
were they tagged correctly?

---

### Post by frediE on 2007-07-16
when I right click on the *.mp3 files, I do see the Title, Artist, and Album information.  I also saw the information in Serpentine under Track #, Title, Artist, and Duration.

Should I confirm with any other method?  any other thoughts?  :-)

---

### Post by wolfen69 on 2007-07-16
try using k3b to burn audio cd's. remember to also download- libk3b2-mp3. if that doesnt work, im not sure what the problem is.

---

### Post by frediE on 2007-07-16
K3B worked to burn audio cd with text!!!!  

Too bad I couldn't get the default Ubuntu Serpentine to work but, I got bigger fish to fry today and this keeps me rocken'  (to bad the music i burned su*ked)  :-)

Oh, side note, I like using the default Gnome apps but that's what is nice about linux, click to install... don't like just remove... do like... happy.

Thanks wolfen69!

---

### Post by cogumbreiro on 2007-08-13
Serpentine uses libnautilus-cd-burner to record CDs. Unfortunately this has no support for audio-cd. I have requested this feature long time ago, but their maintainers have not implemented it yet (at least that I am aware of).

---

### Post by frediE on 2007-08-15
Thats weak.  Seems like if one were burning an audio cd that they would want to see the audio text.  Its too bad that I could not get any of the other Gnome apps to burn the cd-text either?

---

### Post by ziffnabb on 2007-08-15
Hmm, I am using K3B to burn audio as well - but I don't get any track names either.  I am using it for .wav files though - truck does not have mp3 - next one will.  I now it's not the cd player because I've done it using nero and that other os that I abandoned 8 months ago.

Ziffnabb

---

### Post by dabl on 2007-08-15
I use K3b too.  I was recording some .wav files that I made from old record albums, and I manually entered the "CD Text" -- track titles, artist/album name, etc., but never got any of it to display on playback.  I figured I'm just K3b-stupid --- are there any tips on how to get that to work?

Thanks!  :)

---

