---
title: "Gridwars2 Music Problem"
date: 2007-05-29
forum: Multimedia &amp; Video
---

### Post by Archel on 2007-05-29
When I play Gridwars2 I get the sound effects but not the music. The sound effects are .wav and the music is .it so that's got to be the problem. I used Synaptic Package Manager and downloaded everything with 'alsa' in it's name. I'm sure there has to be some kind of installation after that, but I'm not sure how. Please help me get rid of the problem. I'm using Ububuntu.

Thanks.

---

### Post by BigSilly on 2007-05-29
I don't think there's a way to solve this. The .it files are Impulse Tracker audio files. I have the same problem as you, and after searching around the net, I couldn't find a solution. Perhaps a very clever Linux audio expert is going to come along soon...

---

### Post by Archel on 2007-05-29
What if we find a .it/.wav converter and make the songs into wavs? maybe that can help?

---

### Post by Archel on 2007-05-30
I think that it can be fixed by configuring alsa but I don't know how.

---

### Post by hseiken on 2008-02-08
Hey, if you look in the directory tree, there's a file called BASS.DLL.  This would normally be used to play the .it files as it's a windows dynamic link library designed to play such files and is used in the semi-popular music player XMPLAY.  The linux version, FOR SOME UNKNOWN REASON still tries to access this file to play music instead of using a native linux .it player.  

So the solution?  

Well, since Gridwars completely locks the soundcare, I've got my PSP playing music (MY MUSIC) through my stereo speakers and turned up my laptop speakers loud enough to be heard at the same volume as my stereo speakers.  

Maybe that's not the solution you were looking for, but it's going to be the only way unless the port gets BASS.SO or something and if I recall (i'm not looking it up right now), there's no linux version of the BASS player.  

Sorry.  But if you do use my solution, at least you can listen to whatever you want.  I threw on some nasty drum and bass and it completely turned the intensity up x100.  

:)

---

### Post by Joe Bedan on 2008-04-28
Oddly enough I ran it using strace and searched through the output for the names of the music files and got nothing.  It seems like the program doesn't even try to load them.

---

