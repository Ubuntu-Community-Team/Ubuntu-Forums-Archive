---
title: "Dual Audio Input/Output"
date: 2010-02-28
forum: Multimedia Software
---

### Post by hhacckerr on 2010-02-28
I am attempting to connect a bluetooth headset to a Telex Intercom System. I can connect my bluetooth headset to Ubuntu and use the microphone and the speaker perfectly. There are no problems with the Line-In or the Line-Out.

Is there any way to connect the BT-Microphone to the Line-Out while connecting the Line-In to the BT-Speaker?

---

### Post by hhacckerr on 2010-08-13
In case anyone was interested, you can create two loopback devices in PulseAudio feeding BT-Mic to LineOut and LineIn to BT-Out.

See:
[http://pulseaudio.org/wiki/Modules#module-loopback]("http://pulseaudio.org/wiki/Modules#module-loopback")
[http://ubuntuforums.org/showthread.php?t=1324135]("http://ubuntuforums.org/showthread.php?t=1324135")

---

