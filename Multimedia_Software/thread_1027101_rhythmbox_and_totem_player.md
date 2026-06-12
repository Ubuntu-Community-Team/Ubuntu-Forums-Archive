---
title: "rhythmbox and totem player"
date: 2008-12-31
forum: Multimedia Software
---

### Post by usman idrees on 2008-12-31
hi 
when ever i insert an audio cd and double click on a song, it goes to totem movie player, it streams over there but does not play any song.i donot know what to do. can i use totem player as audio player ?
plz reply.....

---

### Post by zenryou on 2008-12-31
I'm no linux guru but you may just need to install some codecs, try installing all the gstreamer stuff and all the xmms2 stuff.  I followed a tutorial on how to install ubuntu and after installing all this I can play just about every media.

---

### Post by wolfen69 on 2008-12-31
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

### Post by mc4man on 2008-12-31
> can i use totem player as audio player ?
As an **audio cd **player no. (totem-gstreamer

There are lots of players (amarok, banshee, exaile, audacious, totem-xine ect.) but for the moment just try rhythmbox.

First click on Places -> Home Folder. When that opens click on Edit -> Preferences -> Media and you'll see a box for CD Audio. In the drop down choose Rhythmbox.

Now when you insert an audio cd rhythmbox will open.

If you want to double left click on a .wav and have rhythmbox open (instead of totem) then d. click on the audio cd icon. 
Then on one of the .wavs -> right click -> properties -> open with. Find rhythmbox in the list and select it. If for some reason it's not in the list then click 'add' and find it there.

You do not need additional codecs and or libs to play audio cd's or .wav's

(i like Amarok because it's one of the few players where you can stick a cd in the drive(s) and it will start playing automatically

---

