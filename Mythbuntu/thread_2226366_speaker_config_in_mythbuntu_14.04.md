---
title: "speaker config in mythbuntu 14.04"
date: 2014-05-26
forum: Mythbuntu
---

### Post by ubn2usr on 2014-05-26
Hi 
I have a onyko tx nx-807 amp running a 8.1 speaker configuration. Setting up the audio in mythbuntu 14.04 I've found that myth is sending the audio to all the wrong channels.
I've no idea how to fix this. I would prefare to send the audio to the amp and let the amp decode the audio channels and well do what the amp should do.
Audio to the amp is thru optical cable
Audio config in mythbuntu

Alsa:hdmi: card=nvidia,Dev=1 audio will work with a few other drivers but the issue is the same with all of them either in 7.1 or 5.1
How the Speaker are configured
Front Left Ok
Front Right Ok
Center No audio goes to Surround right
Surround Left No audio goes to Right Left
Surround right No audio goes to rear right
Right Left No audio goes to Center 
Rear right No Sub No Surround right

---

### Post by blm-ubunet on 2014-05-27
Optical Toslink (IEC958) can only support stereo PCM bitstream or AC3 (640kbps)/DTS(1M5bps) encoded bitstreams.

So options:
- pass thru' 
- output stereo PCM
- encode to AC3
- decode (HDA etc)-> re-encode AC3
- get HDA (HDMI) capable link to output HDA incl. discrete 8 ch

MythTV supports all these; it has an internal AC3 encoder (could be limited to 5.1).

---

