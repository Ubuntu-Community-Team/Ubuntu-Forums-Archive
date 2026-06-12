---
title: "Stream audio to shairport - sync &quot;airplay&quot; server"
date: 2017-08-18
forum: Multimedia Software
---

### Post by Bobuscho on 2017-08-18
Hey, 

There are plenty of threads and guides on how to turn and ubuntu machine into an airplay server, but i could find almost nothing on how to stream music TO a shairport/airplay server.

I've set up a homeserver/nas to store my media and handle my backups. This nas serves as an airplay reciever, too. I've managed to set up openmediavault (debian jessie) with shairport-sync.

What works so far: 

Airplay streaming from Windows 10 via "Airfoil" works perfectly.

What does not work:

Audio streaming from Ubuntu/Ubuntu Mate 17.04 to the shairport/airplay server. 

I've managed to install the pulseaudio-raop and the zeroconf module, avahi is running and the shairport/airplay server is recognised by Ubuntu. I can even select it as an output device in the audio settings.

However, there is no sound output. Speakertest does not work, Youtube videos won't even play as there is no sound output (it is not muted, i triple checked it). 

Do you guys have any idea on how to get airplay working?

---

