---
title: "Need an MP3 player program"
date: 2006-08-14
forum: Multimedia &amp; Video
---

### Post by sbelew on 2006-08-14
Can anyone recommend a good MP3 player application? I haveseveral hundred MP3 files stored on the network, that I access through Samba. I want to be able to make playlists. Ive tried rhythmbox and Amarok, no luck with them. I can get them to play in Kaboodle and a few others, but no real playlist support.

---

### Post by kaffelars on 2006-08-14
I think you could mount the Samba-shares av cifs filesystems, for instance as /media/music, and then you would be able to use them in varios music players.

---

### Post by kaffelars on 2006-08-15
Hate to be the first to answer my own post, but still:
I played around a bit with Rhythmbox 0.9.4 yesterday (the one installed by [Automatix]("http://www.getautomatix.org") and was *very* pleased.
I could import all the music from my Samba share (I only have shortcuts for them on the desktop, they do not have their own mountpoints in /etc/fstab).

Sbelew, I think you should get Automatix and give that newer Rhythmbox a try :)

I might even try to compile the 0.9.5 version too see what it's got up it's sleeve.. ;)

---

