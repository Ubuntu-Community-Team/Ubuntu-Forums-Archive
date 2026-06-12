---
title: "[solved] xubuntu and vlc: does vlc remember the last file?"
date: 2013-07-11
forum: Multimedia Software
---

### Post by rb76543 on 2013-07-11
i recently changed from debian/gnome to debian/xfce4.

i have a directory with about 300 videos in it. under gnome (vlc version 1.1.3), when i started vlc and clicked on "open file", the cursor would be on the last one i played, making it easy to progress through the list.

but now, under xfce4 (vlc version 2.0.3), whether i use a playlist or not (i never used playlists with gnome, btw), when i start vlc, the cursor is always at the first file, and i have to remember where i left off. the vlc forum people could not answer why this is, and assumed that gnome was helping vlc remember the last file played.

so, the question is: if i switch to xubuntu, does vlc position the cursor on the last file you played?

---

### Post by rb76543 on 2013-07-12
if someone is using xubuntu and vlc, could you check this for me? if you have a directory with more than one video in it. play any video other than the first one. then exit vlc, and restart it. then "open file", and tell me if the cursor is on the file you last played.

thanks to anyone who will do this for me. if it works, i plan to switch to xubuntu because i watch a few videos each night, and it is very convenient to restart where i left off.

---

### Post by howefield on 2013-07-12
VLC 2.0.5 Twoflower and Xubuntu 12.10. Reverts back to first file in the folder.

---

### Post by rb76543 on 2013-07-12
thanks for the reply. 

it's interesting that vlc under xfce4 does go back to the last directory used, but whichever entity that saved that information unfortunately decided the file name was not worth saving as well.

of course, there's nothing stopping me from adding functionality that i want. maybe I'll look into it.

---

### Post by mc4man on 2013-07-12
It seems the most common behavior is to just open the last used folder, irregardless of whether Xubuntu, Ubuntu or even Windows, at least with vlc 2.x
There is only a 'open recent media'  list but obviously not what you want.

---

### Post by rb76543 on 2013-07-15
ok, i found what i wanted. forget VLC, and get UMPlayer. load a playlist, play a few files, and exit.

then  restart, but instead of loading the playlist, click on the playlist  icon, and it comes up with the cursor on the last file played.

and thanks again to all who helped.

---

