---
title: "skype doesn't recognise SoundMAX ?"
date: 2008-12-17
forum: Multimedia Software
---

### Post by hofald on 2008-12-17
Hello!
I am completely new to Ubuntu (or Linux for that sake) and I just managed to install Skype. Hurray! :-)
However, I don't get any sound in or out of Skype, even though I can record and playback my voice with the Sound Recorder.
I am using Ubuntu 8.10 on an IBM T43 with a SoundMAX sound card.
I already tried moving using "esddsp skype" as I found on the Skype homepage, but that didn't work (couldn't find libesddsp.so.0). So I tried moving the this file in the /usr/lib/ directory as described in this thread ([http://ubuntuforums.org/showthread.php?p=4682046](http://ubuntuforums.org/showthread.php?p=4682046)).
Now if I say "esddsp skype" Skype starts up but I get error messages like:

ALSA lib pcm.c:2196: (snd_pcm_open_noupdate) Unknown PCM cards.pcm.hdmi
ALSA lib pcm.c:2196: (snd_pcm_open_noupdate) Unknown PCM cards.pcm.hdmi
ALSA lib pcm_bluetooth.c:1619: (bluetooth_init) BT_GETCAPABILITIES failed : Input/output error(5)

And still no sound in Skype ...

Would appreciate any help!

---

