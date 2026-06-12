---
title: "DVD playback at super-high speed"
date: 2010-12-05
forum: Mythbuntu
---

### Post by Quadari on 2010-12-05
Hi All,

I'm having a slightly odd issue with playing back a DVD I created.  Mythtv on mythbuntu box plays normal, commercial DVDs without a hitch.  I recently created a DVD of some home movies using iDVD on my mac.  This DVD plays great on my mac, and plays great using either VLC or mplayer on my mythbuntu box.  However, when I try to play the DVD using mythtv it looks fine but everything (audio & video) plays at super-speed.  We all sound like chimpmunks!  It's quite amusing, but would probably be best if I can figure out why that's happening and slow down the high-speed DVD playback.

Here are some details of my system:
Ubuntu version   : 10.04.1 LTS
MythTV Version   : 24158
MythTV Branch    : branches/release-0-23-fixes
Network Protocol : 56
Library API      : 0.23.20100314-1
QT Version       : 4.6.2
DVD Player       : NEC DV-5800A

Let me know if you need other info.

Anyone have any ideas as to what is going on?

Thanks!
Q

---

### Post by thatguruguy on 2010-12-05
Have you tried it in a regular DVD player?

---

### Post by Quadari on 2010-12-06
I had not tried it in a "regular" dvd player (by which, I assume we're talking about one of those stand alone units you plug right into the TV.)

However, I upgraded my mythtv to 0.24 this evening, and that appears to have fixed the issue.  So the upgrade must have fixed whatever playback thing was broken.

---

