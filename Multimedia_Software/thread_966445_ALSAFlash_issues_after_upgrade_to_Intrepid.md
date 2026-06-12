---
title: "ALSA/Flash issues after upgrade to Intrepid"
date: 2008-11-01
forum: Multimedia Software
---

### Post by AurolacKid on 2008-11-01
I use an external soundcard (Edirol UA-4FX) and it was working fine back on Hardy but once I upgraded to Intrepid things were thrown off.

Firstly I get no sound from flash anymore. Video is fine but no sound at all. I spent days searching for a solution but none have worked for me so far. I used to have my sound playback set to 'EDIROL UA-4FX USB Audio (ALSA)' back on Hardy but that no longer works. When I click test I get:
"audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Could not open audio device for playback." from any ALSA selections. OSS works fine but I read somewhere that Flash doesn't work so well with OSS (?) and I'm thinking that might be my problem. Thoughts?

Also even with OSS I can't get sound to work in VLC, and in Totem the audio is really messed up. Otherwise it sounds good while listening to music using Exaile or gmusicbrowser..
Another thing I noticed is I can only get sound from one thing at a time. For example if exaile is running (even if it's not playing) I can't get sound from totem or pidgin and vice versa

---

### Post by AurolacKid on 2008-11-05
This is the only time I'll bump this : \

---

### Post by AurolacKid on 2008-11-05
Well I just disabled my onboard sound card in BIOS and removed the other one in my PCI slot and restarted and things are working good now but I'm afraid of restarting :|

---

