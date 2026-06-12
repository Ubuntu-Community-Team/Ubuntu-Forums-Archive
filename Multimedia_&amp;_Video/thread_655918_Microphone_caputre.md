---
title: "Microphone caputre"
date: 2008-01-01
forum: Multimedia &amp; Video
---

### Post by forevertheuni on 2008-01-01
Hello all. I'm trying to capture from my microphone so that I can use teamspeak and eve-online voice.
I tried to capture sound with rec, audacity , krec and gnome-sound-recorder.

when I try to capture with ALSA: default in audacity it doesn't capture. with ALSA: hw:0,0 everything is ok.
when I try to capture with rec -t alsa default out.wav it does not capture, with rec -t alsa dsnoop:0 out.wav if does capture but a really bad sound with breaks.

krec and gnomesound-manager doesn't capture a thing. 
in alsamix(gnome mixer and kde mixer) I have capture set to microphone mic boost at max

In eve-online(wine application) it uses dsnoop:0 for the input but I can't hear any sound from the echo test.
The two things that I want is
1.getting default to also record
2. getting dnsoop:0 to record with good sound and no breaks.
Thank you for any help in advance

After editing:
ekiga wengophone does not capture. In ekiga I can't even control volumes(it used to work I don't know when it stopped to work)

---

### Post by forevertheuni on 2008-01-03
it seems "digital" needs to be up to capture something..instead of "capture".

---

