---
title: "Sounds suddenly not playing on ubuntu, help."
date: 2007-03-01
forum: Multimedia &amp; Video
---

### Post by Iceni on 2007-03-01
I am a new user. I've gotten most things running up til now, including beryl, ntfs-3g, etc. The usual stuff is all there, and working.

Today my sound disappeared. I was watching a music video, then tried to drag-drop another music video into Totem, and after that the sound was all gone. I was fooling around with totem's sound-settings, trying surround modes etc, but I set back to normal stereo after no improvement in sound quality. 

What I've tried so far:
- Restart
- reinstalling alsa (follwing LordRaiden's guide)
- Disabling & eneabling the external mixer in alsamixer
- Added ""options snd-intel8x0 ac97_quirk=3" to /etc/modprobe.d/alsa-base as suggested in the guide.

Now I'm at a loss for what to try, and I'd really hate to reinstall ubuntu again just for this. Anyone got any suggestions?

Thanks in advance!

EDIT:
It looks like everything is working fine, amarok playing, videos playing. Tried with other speakers, but didn't help. Ubuntu acting like sound is there, did I mute it in some weird way that won't show up in the colume control?

---

### Post by Iceni on 2007-03-01
Nevermind me, I actually did mute something weird. Wonder how I did that. 

Please close or delete thread:)

---

### Post by lajn on 2007-03-01
No, please don't close or delete this thread. I'm not able to get any sound either. I would like to know what you had muted? Everything seems to be working fine for me, the card has been detected, mplayer plays my files and I can watch movies on you tube but there is no sound. :confused:

---

### Post by rajeev1204 on 2007-03-01
Hi

it can happen when playing video using media players like totem and gxine.

It happened to me too wiith gxine .Funny thing is that GXINE seems to reduce master volume control also


Just try to remember what u did before sound suddenly disappeared


regards

rajeev

---

### Post by Iceni on 2007-03-01
> **lajn said:**
> No, please don't close or delete this thread. I'm not able to get any sound either. I would like to know what you had muted? Everything seems to be working fine for me, the card has been detected, mplayer plays my files and I can watch movies on you tube but there is no sound. :confused:

here is what I did:

- I opened the gnome volume control (double-click speaker icon)
- Then edit-preferences
- Checked everything, turned out "IEC 958 Playback AC97-SPSA" was muted.

Hope this helps.

---

