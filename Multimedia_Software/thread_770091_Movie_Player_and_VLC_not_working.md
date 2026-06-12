---
title: "Movie Player and VLC not working"
date: 2008-04-27
forum: Multimedia Software
---

### Post by alexjohnc3 on 2008-04-27
When I try to play any audio with the default program, Movie Player, it doesn't work. I don't know if this is a result of upgrading to Hardy Heron or because I downloaded the Last.Fm program from the Medibuntu repository via Add/Remove Programs sd I didn't play any music audio until just after downloading the Last.Fm program. The audio is still working because Mplayer Movie Player works and so do Flash files online.

---

### Post by alexjohnc3 on 2008-04-27
Also, I've tried reinstalling both VLC and Movie Player, but that didn't do any good. When VLC attempts to play music, I don't hear any sound, and when Movie Player does, unless I move the position of the time of the audio being played (not sure how to word that exactly), it just sits there at the very beginning of the song. After I move it, it seems to kind of freeze up every few seconds.

---

### Post by robgaskell on 2008-04-27
Same problem here, have audio in a couple of programs (Amarok, Firefox) but not VLC or Movie Player.

---

### Post by alexjohnc3 on 2008-04-27
Can anyone help though...? -____-

---

### Post by pheger on 2008-04-28
I had the exact same issue after upgrading to version 8. I found this resolution for movieplayer and VLC which both worked for me!

[http://ubuntuforums.org/showpost.php?p=2434848&postcount=6](http://ubuntuforums.org/showpost.php?p=2434848&postcount=6)

Good luck,
Pascal

---

### Post by alexjohnc3 on 2008-04-30
> **pheger said:**
> I had the exact same issue after upgrading to version 8. I found this resolution for movieplayer and VLC which both worked for me!

[http://ubuntuforums.org/showpost.php?p=2434848&postcount=6](http://ubuntuforums.org/showpost.php?p=2434848&postcount=6)

Good luck,
Pascal
Thanks for the advice, but I just reinstalled it (I had already done this though...) and it's working fine for both VLC and Movie Player. I don't have any idea why. :\

---

### Post by strigare on 2008-04-30
I am having the same problem here and reinstalling didn't help :(

---

### Post by strigare on 2008-04-30
Ok, I fixed the problem for VLC:

Settings->Preferences->Audio->Output Modules->Audio Output Module

And there I selected "ALSA audio output"

Now VLC is working, but totem, songbird and rythmbox are not. I guess the problem is that ALSA is not set as the default but I don't now how to set it.

---

### Post by strigare on 2008-04-30
Ok, fixed it, it was really stupid XD

System->Preferences->Sound->Music and Movies

In "Sound Playback" instead of autodetect choose "ALSA"

Really stupid :P

---

