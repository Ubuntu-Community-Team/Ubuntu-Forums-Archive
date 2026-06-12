---
title: "M-audio 2496 driver"
date: 2006-11-19
forum: Multimedia &amp; Video
---

### Post by guitarguy on 2006-11-19
I have sound with my onboard nVidia chipset, but I'd really prefer to run my audio (.wav recording & editing) with my M-audio Audiophile 2496 soundcard. I can find [COLOR="Red"].rpm[/COLOR] version of the [COLOR="Red"]driver[/COLOR] but understand that the [COLOR="Red"].deb[/COLOR] would be easier to install. Any ideas? I am running the amd64 version of Ubuntu2.10.
Also , clear instructions would really help me out. I'm getting a bit better at figuring out this system.... but the learning curve is still *steep!*

---

### Post by rikard_grankvist on 2006-11-19
Hello, I have the same card. There are several threads here that can tell you how to get it working. But I can start by saying that audio card setup doesn't work in ubuntu the way it does in Windows (which is what you seem to be coming from). The sound architecture ALSA, automatically detects your cards and probably installs the drivers as well. There's no "driver hunting" necessary, like in windows. You just need to make sure the the audio devices use the right card.

Open a terminal and type: cat /proc/asound/cards

The output should be two cards, 0 and 1. One of those, probably 1 should be the audiophile card.

Use the start menu to go to System->Preferences->Sound. Under Devices, everything should be ALSA. Under sounds, check the "default sound card" at the bottom. If it's the audiophile card, then no problem. Output should be routed to the audiophile card. If not, you need to make audiophile your default card. For some reason, it usually doesn't work to select the card in the Sound dialog (when you open it again, it will have switched back to your other card), so you need to do it the down-and-dirty way. Which is explained in this post:

[http://www.ubuntuforums.org/showpost.php?p=1620232&postcount=10](http://www.ubuntuforums.org/showpost.php?p=1620232&postcount=10)

However, I suggest using gedit rather than nano to edit the file (if you're not used to that program):

sudo gedit /etc/modprobe.d/alsa-base

To my alsa-base file I added:

options snd-ice1712 index=0
options snd-via82xx index=1

snd-ice1712 is the name of the ALSA audiophile 2496 driver. I'm no pro, so I can't guarantee this will solve it, but it did it for me.

---

### Post by guitarguy on 2006-11-21
Thanks for the tips-  Got back to it today and it all works!.... quite well.

Do you make 24 bit recordings with your card? If so what programs do you reccomend? You are correct in surmising that I've done my recording (and music scoring ) in windows. I'm trying to go all open source and switch over to Ubuntu. The music recording doesn't look that tough , but the scoring programs could be more difficult. ( I am a music teacher.)

I'll let you know when I get this thing working.... oh & and then there is MIDI....

Thanks again

---

