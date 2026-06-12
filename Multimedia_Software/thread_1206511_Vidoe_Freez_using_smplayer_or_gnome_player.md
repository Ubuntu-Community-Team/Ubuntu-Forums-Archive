---
title: "Vidoe Freez using smplayer or gnome player"
date: 2009-07-07
forum: Multimedia Software
---

### Post by gawadelnil2002 on 2009-07-07
hey guys i THOUGHT someday that i will not meet any problem with ubuntu again but for my bad luck ,after i installed smplayer .67 something like that from smplayer ppa and i installed too mplayer from its ppa and it works well except vidoe play back get freez for a second during play back and then go easy on playing again, and i didnt notice that alot before cause i was watching short videos with smplayer but today when i was watching a movie i noticed it and is very very annoying that every 3 minutes or 2 the video freez for second and then move again nothing like nothing happened i thought it's compiz and i stoped it but that didnt solve anything i made some search on google and i got alot of things most of it say that pluse audio is the probelm, and some one posted a solution and he said that he got it from fedora forums , any way i wanna try this solution but i didnt want to start trying before asking our experts her in the forums 


that is the link for the solution i saw wrote by [B][-dk-]("http://smplayer.berlios.de/forums/profile.php?id=657")
[http://smplayer.berlios.de/forums/viewtopic.php?id=928](http://smplayer.berlios.de/forums/viewtopic.php?id=928)

note: im using juanty
[/B]

---

### Post by jerrrys on 2009-07-07
things that may help

[http://ubuntuforums.org/showthread.php?t=938471&highlight=dvd+playback](http://ubuntuforums.org/showthread.php?t=938471&highlight=dvd+playback)

i notice an improvement with win32 when playing off the internet...

also, do you have ubuntu restricted extras installed (located in synaptic package manager)?

from your description it may be that your video buffer is just reloading. i use vlc player myself so i don't know for sure, but you may be able to enlarge your video buffer.

like i said.  this may help, but can't hurt...

---

### Post by rvm4000 on 2009-07-07
You may try first to change the audio output to pulse or oss (preferences -> general -> audio). smplayer uses by default alsa, but it seems alsa doesn't work well in jaunty when pulseaudio is installed.

---

