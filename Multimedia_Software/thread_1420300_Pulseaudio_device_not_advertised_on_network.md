---
title: "Pulseaudio device not advertised on network"
date: 2010-03-02
forum: Multimedia Software
---

### Post by AcIDx0 on 2010-03-02
Hello all,

I am trying to stream my sound to a remote pulseaudio server on the same subnet.

I am trying to send the audio from an Jauntu laptop to a debian squeeze desktop. 
The sound on Debian works, issuing paplay something.wav plays it out loud.
On startup, I can see messages about AVAHI and Pulseaudio starting. I can ping the computers from one to another. Multicast services like DLNA work on this network. 
pulseaudio --version
pulseaudio 0.9.21 

Yet I cannot see the service advertised on my laptop with padevchooser. 

Side question - how can I redirect the sound without seeing the service? e.g. what should I write in the sink field.

I have googled extensively, and I have no idea what can I do resolve this. 

Please help.

---

### Post by AcIDx0 on 2010-03-03
Bump! Anyone? Some gurus on pulseaudio? I have no clue where to look. I have no error messages, it appears to work, just does not advertise the service, and I can't test the actual audio transmission.

---

### Post by AcIDx0 on 2010-03-03
Correction - laptop is Karmic, not jaunty :)

---

### Post by AcIDx0 on 2010-03-08
OK, solved the problem by reinstalling all the packages. Still don't know what it was.

---

