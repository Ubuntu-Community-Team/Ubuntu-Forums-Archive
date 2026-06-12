---
title: "extract mkv files OR fix distortion"
date: 2009-09-29
forum: Multimedia Software
---

### Post by pythonscript on 2009-09-29
I have an mkv file that has somehow gotten warped, because the movie resolution is about 10 x 800 (I hope I have that right). In other words, the movie is about 1 cm wide, but the height is as high as my screen. Does anyone know how to fix this? I don't know if I can extract the original movie file (with audio, of course) from the mkv file, or if anyone knows of an ubuntu tool that can fix this. I'd really appreciate it!

---

### Post by Judo on 2009-09-29
The chances of the file being corrupted are very, very low.  It's much more likely that your media player is set to play at some ridiculous aspect ratio.  (From time to time, I manage to hit the right hotkeys to do this.)

If your media player has an option to change the aspect ratio, try different things until you find the right one.

If it really is the file, open it with mkvmerge-gui (known as MKV File Creator in the menu and in the mkvtoolnix-gui package) and force the correct aspect ratio in the "Format specific options" tab.

---

### Post by pythonscript on 2009-09-30
I'm using vlc media player, and it plays other mkv files correctly. Does this still mean the aspect ratio could be off? I'll try the toolkit when I'm back in my apartment. Thanks!

---

### Post by pythonscript on 2009-10-03
How can I change the aspect ratio in VLC media player when I'm playing a video?

---

