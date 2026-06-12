---
title: "Conexant sound card help please"
date: 2009-12-18
forum: Multimedia Software
---

### Post by reiki on 2009-12-18
Ok I read the comprehensive sound troubleshooting thread and I'm still having difficulty.
I have a Dell Zino HD. I'm getting sound from the front headphone jack but I can't seems to get the rear analog jack activated. (Works fine in Win7 so I know the jack is not defective)

```

**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: CONEXANT Analog [CONEXANT Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 1: Conexant Digital [Conexant Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

My understanding is that you can EITHER have sound from the HDMI or from the analog jack. I've tried muting and unmuting various combinations in alsamixer. Just not sure what I'm doing wrong. I don't see a conexant driver in the alsa database.

Anyone got time to lead me through this to see if I can get it working? It's really the only thing that didnn't work out-of-the-box with a fresh Karmic install.

thanks

---

### Post by MonkeyPlus on 2009-12-28
I am in the exact same situation as you are. Seeing as I bought this particular computer because it would sit unobtrusively under the TV, having the speakers plugged into the front is not an option.

If I come across a solution during my fiddling I will post it here for you.

I wouldn't otherwise dissuade anyone from buying a Zino btw, other than this annoyance its a nice quiet little computer.

edit: I've a suspicion that the root of this problem could be the HDMI output; I suspect the computer might be trying to play the sound through there rather than the analogue socket.

---

