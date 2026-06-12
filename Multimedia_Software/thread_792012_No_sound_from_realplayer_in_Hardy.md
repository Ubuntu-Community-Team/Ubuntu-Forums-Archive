---
title: "No sound from realplayer in Hardy"
date: 2008-05-12
forum: Multimedia Software
---

### Post by gjb1002 on 2008-05-12
Hi all,

I'm new to Ubuntu, and after a great deal of wrestling and googling I managed to make my wireless network operate. Feeling confident, I set my sites on making BBC radio work...

I installed Realplayer (v11) and its Firefox plugin. Realplayer looks like it's working but no sound comes out. Sound works in other applications (at least "beep") It seems like this is an old issue given the amount of hits for "no sound realplayer ubuntu" on Google...

The favourite solution seems to be to hack the start script to use "aoss realplay.bin" instead of realplay.bin directly. Or to preload libaoss.lib. Neither worked for me.

(At this point I discovered somewhere that you can install Realplayer via the package installer, and that this was the "recommended way", so did that and got version 10 instead.)

Then I noticed [here]("https://help.ubuntu.com/community/RealPlayerInstallationMethods#head-b03f8c871759a69a4d6251c4683bca8329b1a679") that someone else had had problems with "the Alsa hacks" in Hardy and had used Pulsaaudio instead, so I installed that but still no sound.

Then I despaired. Any ideas?

Geoff

---

### Post by tiggsy on 2008-05-14
Yes, fed up with silence. Good to get the old radio back on. Besides, without it I just don't know what's happening offline.

---

### Post by AlanR8 on 2008-05-14
You don't need Real Player.

I assume you're running Firefox. Install the Mplayer plug in from the repos and it will also install the full version of Mplayer.

You should now be able to play the Beeb music service! I can.

---

### Post by gjb1002 on 2008-05-17
Thanks Alan.

Unfortunately this didn't help. I installed mplayer but it does much the same thing as realplayer, it appears to be working but no sound comes out.

Any other ideas, anybody? Is "beep" a good way to check if my sound card is working correctly?

Regards,
Geoff

---

### Post by AlanR8 on 2008-05-17
You could try removing Real Player and making sure you don't have either the Xine or VLC Mozilla plug ins installed. In fact, uninstall/purge MPlayer as well. Then reinstall the MPlayer plug in......

---

### Post by gjb1002 on 2008-05-17
Removed both RealPlayer installations, the other packages weren't installed from the start. Even after a reinstall of mplayer it still behaves the same unfortunately...

Geoff

---

### Post by gjb1002 on 2008-05-21
Fixed it myself. The moral of the story is: "beep" producing sounds is not proof that your sound card is working. (I presume it just accesses the speakers directly)

Once I switched attention away from mplayer and realplayer to making the sound card work I got it working by following the standard How-to on this site.

---

