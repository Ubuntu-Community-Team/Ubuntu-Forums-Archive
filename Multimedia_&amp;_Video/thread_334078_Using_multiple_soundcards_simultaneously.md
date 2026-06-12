---
title: "Using multiple soundcards simultaneously"
date: 2007-01-08
forum: Multimedia &amp; Video
---

### Post by reuben on 2007-01-08
I just bought myself a wireless sound device (saitek a-250, it has a USB dongle which acts as a USB-audio device, and broadcasts the stream via bluetooth to the receiver, which essentially is a set of speakers.) 

ALSA recognizes the device, and I can play sound through it. However, what I'd really like to do is set it up so that playing audio (e.g. via amarok) plays on both my primary sound card (physically attached to the compuer) and the wireless audio device. That way, in e.g. party situations, the room that the compuer in plus the remote speakers are playing the same set of music.

An extension to this would be the ability to route different sounds through different cards. That way, the computer can be playing a movie, but an audio stream of music can be sent to the receiver in another room. (This appears to be easier to get going.)

Any clues here?

---

### Post by groggyboy on 2007-03-29
i found this on the amarok FAQ page - instructions on configuring it to use the proper sound card.  one of the setups is for using multiple sound cards at the same time (ie onboard sound + usb audio).  i haven't tested it myself, but it's worth a shot!

[http://amarok.kde.org/wiki/FAQ#How_can_I_change_where_the_audio_is_output_to.3F](http://amarok.kde.org/wiki/FAQ#How_can_I_change_where_the_audio_is_output_to.3F)

---

### Post by Novus on 2008-03-29
I followed this howto (and spent hours of googeling) but it just dosn't work..

Amarok
```
Audio output unavailable; the device is busy.
xine parameters:
```

So I try with XMMS, but similar error there

XMMS
```
Please check that:
Your soundcard is configured properly
You have the correct output plugin selected
No other program is blocking the soundcard
```

I only get these errors when trying to use both soundcards at the same time.. individually they both run fine in both Amarok & XMMS so it can't be the FF issue

someone PLZ help me

---

### Post by jdb2 on 2008-04-05
You might want to try opening a shell and typing " lsof +D /dev/snd " . This will give you a list of process-file pairs where file listed is being held open by the associated process. Try killing off some of the processes listed. It's worked for me in the past

jdb2

---

