---
title: "my bluetooth headset does not play audio"
date: 2008-04-26
forum: Multimedia Software
---

### Post by forevertheuni on 2008-04-26
[http://ubuntuforums.org/showthread.php?p=4731782](http://ubuntuforums.org/showthread.php?p=4731782)
I followed this setup trying with pulse enabled and with only alsa.
I pair my headset I try to play something with "bluetooth" device (I did pcm.bluetooth and not pcm.auto) and them I have this in daemon.log 

```

Apr 26 17:17:29 merlin audio[7042]: connect(): Connection timed out (110)
Apr 26 17:17:29 merlin audio[7042]: config failed
Apr 26 17:17:29 merlin audio[7042]: Audio API: sending BT_SETCONFIGURATION_RSP
Apr 26 17:17:29 merlin audio[7042]: State changed /org/bluez/audio/device0: HEADSET_STATE_PLAY_IN_PROGRESS -> HEADSET_STATE_CONNECTED

```

After mplayer stops trying to run the audio through the headset I have:

```
 
Apr 26 17:17:31 merlin audio[7042]: Unix client disconnected (fd=9)

```

I tried with sco and snd-bt-sco module loaded and not loaded.

What else may I try?

---

