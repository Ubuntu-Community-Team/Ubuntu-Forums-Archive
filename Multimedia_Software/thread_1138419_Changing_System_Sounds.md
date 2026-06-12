---
title: "Changing System Sounds"
date: 2009-04-26
forum: Multimedia Software
---

### Post by locosmurf on 2009-04-26
Ok so I feel Like I have a weird problem. I have been trying to customise my sound scheme in Jaunty but can't seem to do it. I have sound, the current default scheme works perfectly, but I can't change them. When I do, it won't play the sound with the test button and restarting reverts it back to default. I've tried changing everything to run pulseaudio, I've tried using different file extensions (the ones I've tried so far: wav, ogg, and mp3). I'm at a loss what to do. help?

---

### Post by ausmuso on 2009-04-28
I had the same problem with Intrepid: I could find no easy way to change the system sounds.
I managed do it the hard way, though.

All system sounds are save in folder /usr/share/sounds/ubuntu/stereo
Directory and file permissions are set so only root can change them. If you want to avoid to many sudos then simply do a "sudo nautilus" and use nautilus to change permissions to the  /usr/share/sounds/ubuntu/stereo folder - and everything in it - so anybody can change anything.

Look inside the folder and you'll see all the standard Ubuntu sounds, like
desktop-login.ogg, dialog-warning.ogg, etc. You can now replace these sounds by the sounds you want, provided they have the same filenames and file format as the old ones.

Note that most files are in Ogg-Vorbis format, the sound format of the True Believers. Use your favourite converter software to generate the necessary .ogg files. If you haven't got one, use apt-get or synaptic to download the vorbis-tools and use oggenc
	oggenc somefile.wav   will produce the file somefile.ogg

There may be more elegant ways to do all this but this way worked for me.

---

### Post by locosmurf on 2009-04-29
I actually managed to get it to work after trying .ogg files again. I'm not sure exactly what went wrong the first time but I'll try to figure it out and post back. Thanks for the advice though!

---

