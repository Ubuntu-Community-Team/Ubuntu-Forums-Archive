---
title: "Alsa Mic"
date: 2008-03-01
forum: Multimedia &amp; Video
---

### Post by Tarmael on 2008-03-01
Hey all.

I just got a new mic (One of those cool earpiece and mic single ear headset things.) and I can't get the mic working, so I figured I'd ask you lot.

Alsa version:
1.0.14
alsamixer has everything at full. And I'm getting static from the earpiece when I turn Front Mic on even though there's no front mic connection.

I'm using the onboard sound card, which is
:~$ lspci | grep Audio
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia

I looked at the ALSA wiki and it didn't really help me.

Also, the mic I got has all this propaganda for Skype (as it's a Skype headset) and comes with 60 minutes of free skype time. Anyone want that? I don't care about Skype, I didn't buy it for the Skype, I got it for the cool functionality and the extreme comfort it has.

EDIT: OH!!

I can get it to record using arecord and aplay, but not with the gnome Sound Recorder. And I get voice feedback when I enable Analog Mix but it goes away when I mute Mic Boost.

---

### Post by Tarmael on 2008-03-03
No one? Anyone?

---

### Post by Tarmael on 2008-03-08
Anyone got any suggestions?

---

### Post by Yellow Pasque on 2008-03-08
The only thing I know to suggest with ALSA is to try updating to the latest version. I've posted some scripts that make it easy: [http://ubuntuforums.org/showpost.php?p=4298894&postcount=24](http://ubuntuforums.org/showpost.php?p=4298894&postcount=24)

EDIT: Actually, on second thought, it's probably not ALSA doing it, but just the fact that you're using onboard audio.

---

### Post by Tarmael on 2008-03-08
hah, yeah... I know the advantages of getting a sound card. I would, but I just bought the most expensive thing in my life... An engagement ring. It wasn't too expensive, but I'm not that rich. So you can understand why I'm using onboard sound.

As I stated (As I THINK I stated) I went to the ALSA site, and they said that my onboard sound card IS supported and has information on getting sound working if it wasn't already. Well, that info wasn't useful to me.

I'll check it out anyway. It's good to have the latest versions...

I'll report on the progress when I get home.

Cheers,

Bas.

---

### Post by Tarmael on 2008-03-09
That worked so well.

Thank you!!

Now with ALSA 1.0.16.

Also, when I have money pretty much my first priority is to get a sound card.

---

### Post by Yellow Pasque on 2008-03-09
You're welcome. Engagement ring > sound card.

---

