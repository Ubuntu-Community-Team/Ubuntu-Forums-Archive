---
title: "Spotify in WINE means no sound in other programs, and vice versa"
date: 2009-08-22
forum: Multimedia Software
---

### Post by ojohnsen79 on 2009-08-22
I've tried searching for any answers on this, but I've come up short so far.

My problem is that whenever I listen to Spotify in WINE, any other program in Ubuntu is dead silent.  Doesn't matter if it's Youtube in Firefor, or MP3 files in VLC.  And just the same the other way around.  If I have Youtube in Firefox active when I try to start up Spotify, I get an error message saying that Spotify has problems with my sound card.

A friend of mine is able to run both Spotify and other programs at the same time without any problems, so I know that it's possible.  Unfortunately, he doesn't know what causes my system to fail.

Can anyone help me?

---

### Post by ojohnsen79 on 2009-08-23
Nobody knows anything about this?

---

### Post by UltraAnders on 2009-08-29
I'm getting the same problem ... but I've no idea how to fix it. Which Wine sound drivers are you and your friend using? I'm using OSS.

---

### Post by howefield on 2009-08-29
Which version of wine are you using ?

I am using 1.28 and spotify works perfectly and plays nice with the other sound apps.

If you are using the wine from Ubuntus` repository, have you followed the instructions here ?

[http://www.spotify.com/en/help/faq/wine/](http://www.spotify.com/en/help/faq/wine/)

---

### Post by UltraAnders on 2009-08-29
I'm using 1.1.28 from the "http://wine.budgetdedicated.com/apt jaunty main" repo.

---

### Post by Farwalker on 2009-08-29
I'm running into the same problem (It's not exclusive to Spotify)- in my case, World of Warcraft (again, under Wine 1.1.28, though from the Hardy repos) either gets an exclusive lock on the sound when started, or plays no sound if another application (or applications) has control of sound.

I'm running 64-bit Kubuntu Hardy, don't know about the OP.

I've tried Wine with Alsa, with OSS, and with aoss... in every case, it doesn't want to play nice with other sound-using processes.

Stumped.

---

### Post by UltraAnders on 2009-08-29
32-bit Jaunty here. Been using the sound test facility in winecfg, which fails if there is another app using sound. Have also tried all the different audio drivers in both "full" and "emulated" hardware acceleration.

---

### Post by dj-toonz on 2009-08-29
I've had the same problem, but going into the wine config & changing the audio from pulse audio to alsa fixed it for me

---

### Post by howefield on 2009-08-29
> **dj-toonz said:**
> I've had the same problem, but going into the wine config & changing the audio from pulse audio to alsa fixed it for me

Just to confirm what dj-toonz has written, mine was already at alsa, might be why I had no issues.

---

### Post by UltraAnders on 2009-08-30
Cheers all, working with Alsa drivers (Emulation) after a reset.

---

### Post by aldursys on 2009-08-30
Fixed properly in the upcoming Karmic release if you use my Wine1.2 package.

[http://www.3spoken.co.uk/2009/08/making-wine-sound-work-with-pulseaudio.html](http://www.3spoken.co.uk/2009/08/making-wine-sound-work-with-pulseaudio.html)

---

