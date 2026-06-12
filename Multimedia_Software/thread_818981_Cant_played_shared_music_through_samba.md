---
title: "Cant played shared music through samba"
date: 2008-06-04
forum: Multimedia Software
---

### Post by speedjunkie on 2008-06-04
I recently acquired a ibm thinkpad and put xubuntu 7.10 (gutsy) on it.  I also have a desktop running ubuntu 8.04 (hardy).  I have set-up samba on the desktop so I can share my Music and other files between the two computers.  I can open the samba shares, read the files (documents) and even write new files, I just cant play shared music.  I am trying to play it through totem and I get an error saying "Totem could not play 'smb://speedjunkie/music/f/Finger Eleven/Finger Eleven/11 - One Thing.mp3' There is no input plug-in to handle the location of this movie."  I also tried to import the music into rythmbox and it gave me this error "The gstreamer plugins to decode 'MP3' files cannot be found".  I looked and I couldnt find the gstreamer plugin it was trying to find.  Amarok also gave me the same "no suitable input plugin".  Anyone have any ideas as to what I should do?

---

### Post by cariboo on 2008-06-05
You can install kubuntu-restricted extras through synaptic. This should get you what you need to play mp3's.

Jim

---

### Post by kostkon on 2008-06-05
> **speedjunkie said:**
> I recently acquired a ibm thinkpad and put xubuntu 7.10 (gutsy) on it.  I also have a desktop running ubuntu 8.04 (hardy).  I have set-up samba on the desktop so I can share my Music and other files between the two computers.  I can open the samba shares, read the files (documents) and even write new files, I just cant play shared music.  I am trying to play it through totem and I get an error saying "Totem could not play 'smb://speedjunkie/music/f/Finger Eleven/Finger Eleven/11 - One Thing.mp3' There is no input plug-in to handle the location of this movie."  I also tried to import the music into rythmbox and it gave me this error "The gstreamer plugins to decode 'MP3' files cannot be found".  I looked and I couldnt find the gstreamer plugin it was trying to find.  Amarok also gave me the same "no suitable input plugin".  Anyone have any ideas as to what I should do?
Indeed, you are missing the necessary codecs. I use Rhythmbox and I can play my shared music through samba just fine.

---

### Post by speedjunkie on 2008-06-05
actually, i have the xubuntu restricted extras, and kubuntu restricted extras packages installed and I still cant play my shared music through samba.  If i were to copy it onto the desktop it playes just fine.  I am going to try and upgrade to hardy and see if that fixes anything.

---

### Post by speedjunkie on 2008-06-05
Well after installing ubuntu restricted extras, I have imported all my songs into rythmbox and they are playable.  I guess playing shared music in amarok and totem arent possible.

---

