---
title: "No sound in Fiesty"
date: 2007-05-02
forum: Multimedia &amp; Video
---

### Post by gmtyrant on 2007-05-02
I am aware that there are boatloads of these threads floating around, maybe someone can get an answer stickied?

The problem: No sound whatsoever since around the time I upgraded to Fiesty. Never had a problem before.

Tried 'Alsa' and the KDE mixer, everything is unmuted and turned up. Tested the sound in Windows, everything is fine, so I know the card is fine.

I'm a noobist, so if anybody has an answer/something I should check, give it to me in simple steps. :)


EDIT: Re-installing libxine-extracodecs seems to have fixed it, though I don't see why. I'm starting to get the hang of this linux maintenance thing. ;)

---

### Post by anirban.sam on 2007-05-05
Type alsamixer and press enter in a console to launch alsamixer. Disable all ICE devices in alsamixer and unmute all muted. Save settings by typing "sudo alsactl store".

---

### Post by andreigbs on 2007-05-05
how do you reinstall codecs and how do you know which ones you need?  I'm also trying to get my SB450 card to work on my Toshiba Satellite.  It worked fine before.

---

### Post by John Azelvandre on 2007-05-05
Re-installing libxine-extracodec worked for me as well.

Actually, it wasn't installed at all on my machine.  So I installed, rebooted, and sound is working.

---

### Post by orangep on 2007-05-05
Where did you find libxine-extracodec?
Dselect doesn't list any such thing.

---

### Post by gmtyrant on 2007-05-05
You can find the extra codec pack with adept or symantic.

Will try alsamixer again next time I have access to that machine, thanks guys.

---

