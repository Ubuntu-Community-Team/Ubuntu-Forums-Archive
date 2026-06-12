---
title: "No sound with Creative Sound Blaster 5.1"
date: 2009-05-14
forum: Multimedia Software
---

### Post by sugeesh1n1 on 2009-05-14
Hi...I'm facing a big problem with my sound card. My sound card is  Creative sound blaster 5.1 and it produce sound only when I open wav or vob files with vlc player and that too when I select devices as 5.1 or 2front 2 rear and not with stereo. When I open mp3 files fith any player(including vlc) the player opens the file and plays it but i can't hear any sound from any of my speakers. And I'm not getting any system sound like login sound too..

aplay -l command gives me this
sugeesh1n1@DESKTOP1N1:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Live [Dell Sound Blaster Live!], device 0: emu10k1x [EMU10K1X Front]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Live [Dell Sound Blaster Live!], device 1: emu10k1x [EMU10K1X Rear]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Live [Dell Sound Blaster Live!], device 2: emu10k1x [EMU10K1X Center/LFE]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: V8237 [VIA 8237], device 0: VIA 8237 [VIA 8237]
  Subdevices: 4/4
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
card 1: V8237 [VIA 8237], device 1: VIA 8237 [VIA 8237]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

And alsamixer gives this

Card: Dell Sound Blaster Live!                                               &#9474;
&#9474; Chip: SigmaTel STAC9758,59                                                   &#9474;
&#9474; View: [Playback] Capture  All                                                &#9474;
&#9474; Item: Master [dB gain=-28.50, -28.50]

I've disabled my onboard sound card on bios.
I've tried the comprehensive sound troubleshooting sticky post.Then only it started getting sound at least with the VLC player.

Somebody pls help me..............

Pls try to get a solution..

Is it any problem with the alsa mixer settings? or with the alsa driver itself? Shall I need to install Pulseaudio?
Pls gimme a solution.....I'm new to Ubuntu...Pls help me..:icon_frown:

---

