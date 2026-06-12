---
title: "TV card blocks sound"
date: 2006-06-20
forum: Multimedia &amp; Video
---

### Post by Krister Hallergard on 2006-06-20
With Kubuntu Dapper I often have no sound from audio and video programs, except Xine, amaroK and Kaffeine, which always work.  KInfo Center shows:
     Audio devices
     0:  SAA7134 PCM
     1:  VIA8237 (DUPLEX)
VIA8237 is my onbord sound card, and when it boots as "0" all sounds function, but when the TV Card SAA7134 boots as "0" I get no sound except for Xine engine applications.

This did not happen with Breezy or with other distros.  Please advice!

---

### Post by Krister Hallergard on 2006-06-22
Thought I found the solution:
     asoundconf set-default-card VIA8237
This seems to set VIA8237 as card "0" every time.  I get a lot more programs to have sound.  Apart from the ones mentioned above (forgot to mention Totem) now also Audacity,RealPlayer,Rhytmbox and VLC work with sound.

But I still have no sound from juK, KsCD, Noatun, Mplayer and XMMS and also there are no system sounds and Alsamixer does not work.  And this with every boot.

Don know if I prefer this to the boot lottery, which gave me ALL sounds when lucky.

---

### Post by Krister Hallergard on 2006-06-25
Believe I found a solution to disable the TV Tuner Card: added the line "blacklist saa7134_alsa" to /etc/modprobe.d/blacklist

The TV Tuner Card (Yuan TUN900) doesn't work with Linux anyway, but I like to keep it in the box for when I boot the XP partition

---

