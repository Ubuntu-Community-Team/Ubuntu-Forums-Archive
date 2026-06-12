---
title: "Banshee - Object Reference not set to an instance of an object"
date: 2008-06-04
forum: Multimedia Software
---

### Post by KillaW0lf04 on 2008-06-04
Hey guys i have a problem with banshee i was hoping one or more of you could help me solve.

Sometimes when i try importing new music into my library (Music->Import Media->Import Files) i get the following error in an error report: "Object Reference not set to an instance of an Object". I was wondering if someone could explain to me why this is happening and how i can avoid it?

---

### Post by pnavarrc on 2009-02-02
Hi, this work for me:

Create a file in tour device, named .is_audio_player . In this file, I wrote the following lines:

audio_folders=Music/
folder_depth=2
output_formats=audio/mp3

Music/ is the folder where I want my audio files. I hope this will help you,

      Pablo.

---

### Post by karamu on 2009-07-25
I was having the same problem trying to sync my Gigabeat MP3 player and that tip seemed to have done the trick- thanks a lot!

---

### Post by zool--- on 2010-08-07
This has done the trick for me!

But weirdly Banshee seems unable to write down the meta-tag on the player, so I only get the file names - no cover nor ID.

---

