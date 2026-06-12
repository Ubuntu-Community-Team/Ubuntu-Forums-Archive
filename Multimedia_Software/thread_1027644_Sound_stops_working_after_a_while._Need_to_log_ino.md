---
title: "Sound stops working after a while. Need to log in/out to restore it."
date: 2009-01-01
forum: Multimedia Software
---

### Post by davidhoenig on 2009-01-01
I thought this was a problem with 8.10 since sound worked fine in 8.04 with the same hardware, so I posted this:

[http://ubuntuforums.org/showthread.php?p=6471758#post6471758](http://ubuntuforums.org/showthread.php?p=6471758#post6471758)

But since I reinstalled 8.04 and still have the problem, I am posting here. 

**The problem**: after a few hours sound stops working, sort of. I will get no sound from Flash apps in FF3, Amarok, or Rythmbox. 

**Symptoms**: FF and Rythmbox do/say nothing. Amarok will complain "Audio output unavailable; the device is busy. xine parameters:". vlc and mplayer will continue to play mp3s just fine.

**What I try**: Restarting pulseaudio via: $ pulseaudio -k; pulseaudio -D; has no effect. 

**Work-around**: If I log out, then log back in, sound is fully restored.

So logging out/in must be restarting some process that is wedged and messing up the audio driver. But just restarting pulseaudio is not enough. Any other ideas?

---

### Post by rdeman on 2009-09-10
I have the same problem, however:
on Windows in comnbination with a headset VOIP IUSB device from Trust
it's the specific Flash Player + Trust Headset combo
seperatly they work fine
(ie Flash player output on internal speakers = OK, headset in combo with eg. iTunes audio: works fine too)
together they fail.
After 1 2 minutes audio stops.
This happens with eg youtube as well as with live video (netstream objects)

---

