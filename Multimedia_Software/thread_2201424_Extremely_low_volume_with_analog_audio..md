---
title: "Extremely low volume with analog audio."
date: 2014-01-24
forum: Multimedia Software
---

### Post by MacOsX74 on 2014-01-24
Hi!

Having an problem i cant solve.
Playing 2 channel audio gives me no audio. If i put volume to max on my reciever i can hear something playing with distorsion.
Audio is working fine playing movies in xbmc but not 2 channel audio.
In spotify or any other player there is almost no sound.
If I connect headphones to any jack i hear sound but with alot of crap in it.

Pulseaudio is removed from system. Need to remove it for XBMC sound to work.
Sound has worked before but i think kernelupdates has caused this issue.

Have updated alsa.
Tried to install Pulseaudio again but that didnt make any difference.
Checked levels in alsamixer but couldnt find anything there either.

Running Ubuntu 13.04 server.
Connected to reciever with Spdif.

I´m no Linux pro so any suggestions would be great.

/Marcus

---

### Post by Bucky Ball on 2014-01-24
*Thread moved to **Multimedia & Video**.*

You might want to try installing Pulseaudio Volume Control and see if that throws any light on things.

'sudo apt-get install pavucontrol' in a terminal.

---

### Post by MacOsX74 on 2014-01-24
> **Bucky Ball said:**
> *Thread moved to **Multimedia & Video**.*

You might want to try installing Pulseaudio Volume Control and see if that throws any light on things.

'sudo apt-get install pavucontrol' in a terminal.

Tried that but nothing.

---

### Post by MacOsX74 on 2014-01-24
I think maybe it has something to do with the different channels.
If I crank the reciever up on max I can hear a little from left back and subwoofer channels.

---

### Post by Bucky Ball on 2014-01-24
Yep, that's probably it. While you have an audio stream going (play some music through any app) open PAVControl and hit the 'Playback' tab. You should see the stream there and be able to choose the device. You might also want to check the 'Configuration' tab and make sure that is set correctly also. 

In alsamixer you could try muting every channel but the ones you want (front l/r by the sounds).

Sometimes takes an incantation, dancing three circles while facing the moon and throwing some salt over your shoulder to get the right combination of settings in PAVControl ... :-k

---

### Post by MacOsX74 on 2014-01-24
I have tried with Pulseaudio and pavucontrol but no sound with that either. Now I dont have Pulse installed because it dosent play well with xbmc.
Is it easier to find the problem with Pulse installed or should I just stick with alsa.

Something I thought about was in alsamixer. I know that Spdif isn´t mutet but should i mute the Nvidia cards audio. Im running the HDA intel card for audio because i dont have any HDMI on my reciever.
I run the HDMI from Nvidia to my projector but just for picture.

---

### Post by MacOsX74 on 2014-01-30
Bump

---

### Post by Yellow Pasque on 2014-01-30
[https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)

---

### Post by MacOsX74 on 2014-01-31
> **Temüjin said:**
> [https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)

okey!
run the script and the output are here:
[http://www.alsa-project.org/db/?f=6c6d24c8d6ac75d34513d54efee741bdd271c26b](http://www.alsa-project.org/db/?f=6c6d24c8d6ac75d34513d54efee741bdd271c26b)

hope it tells you something useful.

---

### Post by MacOsX74 on 2014-01-31
I noticed today when running xbmc that its something wrong with the speaker setup.
I know my hardware is correct but I watched an tv episode and when there was music playing the sound came from the subwoofer and the back channels.
The center channel seems fine. Looks like there some mixups between the channels.
The episode had Digital 5.1 sound.

---

