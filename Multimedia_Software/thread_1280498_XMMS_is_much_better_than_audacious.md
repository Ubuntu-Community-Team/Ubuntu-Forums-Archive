---
title: "XMMS is much better than audacious"
date: 2009-10-02
forum: Multimedia Software
---

### Post by Zeemvel on 2009-10-02
XMMS 1, the good oldscool player, is much better than audacious.

Not only is audacious slower. Audacious has many bugs that XMMS doesn't have. Audacious can't scroll properly in a track of 600 minutes, and yes I have such one. Audacious sometimes stops playing properly after my PC has been very slow due to a java application that was hanging. From that moment on until a reboot, audacious will skip half a second sometimes, totally wasting the enjoyment of the music. XMMS is immune for that annoying behaviour. Audacious also can't handle some file types in a folder if you use "add dir" in the playlist to add all your music at once to it, and will end up duplicating the file 10000000 times in the playlist, making it gigantically slow. Again no problem for XMMS.

Basically, I have reverted from audacious to XMMS on two different PC's to be able to properly listen to music and in both cases going to XMMS fixed my problems. It's clear which player is superior here. The only sad thing is XMMS doesn't receive any fixes anymore and was removed from the default Ubuntu repository.

Why was development of XMMS stopped and all that effort directed to a slower, buggier, player instead?

---

### Post by lloyd_b on 2009-10-02
> **Zeemvel said:**
> XMMS 1, the good oldscool player, is much better than audacious.

Not only is audacious slower. Audacious has many bugs that XMMS doesn't have. Audacious can't scroll properly in a track of 600 minutes, and yes I have such one. Audacious sometimes stops playing properly after my PC has been very slow due to a java application that was hanging. From that moment on until a reboot, audacious will skip half a second sometimes, totally wasting the enjoyment of the music. XMMS is immune for that annoying behaviour. Audacious also can't handle some file types in a folder if you use "add dir" in the playlist to add all your music at once to it, and will end up duplicating the file 10000000 times in the playlist, making it gigantically slow. Again no problem for XMMS.

Basically, I have reverted from audacious to XMMS on two different PC's to be able to properly listen to music and in both cases going to XMMS fixed my problems. It's clear which player is superior here. The only sad thing is XMMS doesn't receive any fixes anymore and was removed from the default Ubuntu repository.

Why was development of XMMS stopped and all that effort directed to a slower, buggier, player instead?

Er - XMMS was *not* stopped in favor of Audacious.  Development on XMMS 1 died out while XMMS 2 was under development.  XMMS 2 is in the repos (which is why they dropped XMMS 1, I suspect).

Lloyd B.

---

### Post by Zeemvel on 2009-10-03
Hmm, I think I tried installing XMMS2 too, but it didn't work, it said something about "xmmsd" isn't running or something similar like that. Is XMMS2 something with both a GUI and a server or something? In any case, I installed all packages related to xmms2 that were available in ubuntu, and yet the GUI gave that message about the thing not running.

I installed XMMS1 from an alternative repo (because it's not on the official one anymore) and it works great, you start its GUI and BAM! it's ready to play your music, like it should :).

---

### Post by Ginsly on 2009-10-07
> **Zeemvel said:**
> Hmm, I think I tried installing XMMS2 too, but it didn't work, it said something about "xmmsd" isn't running or something similar like that. Is XMMS2 something with both a GUI and a server or something? In any case, I installed all packages related to xmms2 that were available in ubuntu, and yet the GUI gave that message about the thing not running.

I installed XMMS1 from an alternative repo (because it's not on the official one anymore) and it works great, you start its GUI and BAM! it's ready to play your music, like it should :).

xmms2 is a client and server media player yes. You will need to install a client program too. (gxmms2 is a good one)

You just need to start the xmms2 daemon before you start the client gui. 
To do this run this command....
```
xmms2d
```

Then start up the client gui. Or you can install the xmms2tray package, which allows you to start/stop the daemon from your system tray...
(you will have to build the media library the first time you use it, before it will play anything)

---

### Post by blazk on 2009-10-26
Its 2009 and I'm still in love with XMMS! too bad GTK1 libraries are no longer in repos (Karmic). Had to compile everything from sources:/. But it's worth it - xmms with it's low resource usage works great on my eeepc!

attached a comparison screenshot. omg xmms looks gorgeous!

---

### Post by vinutux on 2009-10-26
> **blazk said:**
> Its 2009 and I'm still in love with XMMS! too bad GTK1 libraries are no longer in repos (Karmic). Had to compile everything from sources:/. But it's worth it - xmms with it's low resource usage works great on my eeepc!

attached a comparison screenshot. omg xmms looks gorgeous!

What ? XMMS the project died more than a dacade......

Then evolved as beep media player > Then spitted > Audacious and BMPX > Bmpx died and reborn as Youki....| Audasious Still going on.......

I don't have any serious problems with audacious...it simple and more modern from the legacy of XMMS...........

---

### Post by Yellow Pasque on 2009-10-27
> **Zeemvel said:**
> Why was development of XMMS stopped and all that effort directed to a slower, buggier, player instead?

A lot of open-source developer politics. [http://www.opensound.com/](http://www.opensound.com/)

---

