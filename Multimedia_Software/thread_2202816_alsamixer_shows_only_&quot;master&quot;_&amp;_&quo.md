---
title: "alsamixer shows only &quot;master&quot; &amp; &quot;pcm&quot; options; no sound from internal speaker"
date: 2014-01-31
forum: Multimedia Software
---

### Post by adrian19 on 2014-01-31
Hi, there. I am new here and also new as a Ubuntu 12.04 user, :)

Well, I just met some trouble for sound. There is no sound from the internal speaker while my earphone works perfectly. My computer is Sony [COLOR=#666666][FONT=Arial]SVF1431AYCW, [/FONT][/COLOR]with HDMI output. 

When I tried to check with alsamixer, there were only "master" & "pcm" options for the PCH sound card (playback). I set PCH as default, and I believe that the earphone also works via it. 

Some info are as follows:

**aplay --list-devices:**

card 0: MID [HDA Intel MID], device 3: HDMI 0 [HDMI 0]
  : 1/1
   #0: subdevice #0
card 0: MID [HDA Intel MID], device 7: HDMI 1 [HDMI 1]
  : 1/1
   #0: subdevice #0
card 0: MID [HDA Intel MID], device 8: HDMI 2 [HDMI 2]
  : 1/1
   #0: subdevice #0
card 1: PCH [HDA Intel PCH], device 0: HDA Generic [HDA Generic]
  : 1/1
   #0: subdevice #0

root@adrian:/home/adrian# [B]lsmod | grep snd

[/B]
snd_hda_codec_realtek    79962  0 
snd_seq_midi           13324  0 
snd_rawmidi            30417  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61930  2 snd_seq_midi,snd_seq_midi_event
snd_seq_device         14497  3 snd_seq_midi,snd_rawmidi,snd_seq
snd_hda_codec_hdmi     37463  1 
snd_hda_intel          44339  4 
snd_hda_codec         141761  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
snd_pcm               102477  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_timer              29989  2 snd_seq,snd_pcm
snd                    69533  18 snd_hda_codec_realtek,snd_rawmidi,snd_seq,snd_seq_device,snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_timer
soundcore              12680  1 snd
snd_page_alloc         18798  2 snd_hda_intel,snd_pcm


My guess:
The sound cards could be detected by kernel, but there is somethin wrong with the drivers... Don't know whether it has something to do with the HDMI card...

Thanks so much for your help!

---

### Post by Bucky Ball on 2014-01-31
Welcome. Did you hit F6 in alsamixer to check other sound cards/devices? Nothing muted anywhere?

---

### Post by soodvarun78 on 2014-01-31
verify that card driver is correct.
You have 2 sound cards, card 0 for HDMI and card1 of realtek which I think will be connected to internal speaker
you can get info for you card from /proc/asound/card*, and verify driver is correct for card1 .

---

