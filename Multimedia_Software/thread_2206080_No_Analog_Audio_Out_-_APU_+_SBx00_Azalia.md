---
title: "No Analog Audio Out - APU + SBx00 Azalia"
date: 2014-02-17
forum: Multimedia Software
---

### Post by TheFu on 2014-02-17
I'm feeling really dumb today. Can't get any local audio out of a media PC.

Ubuntu Server 12.04.4 + LXDE + XBMC Frodo on top. I like a minimal install.

Swapped in a new HDD a few days ago that required GPT, so a fresh install of Ubuntu Server was needed. This is an AMD E-350+Radeon GPU miniPC.  Before the HDD swap, the audio worked perfectly - both HDMI and analog.

There are 2 sound devices seen by the OS.
```
$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Generic [HD-Audio Generic], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: SB [HDA ATI SB], device 0: ALC887-VD Analog [ALC887-VD Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 1: SB [HDA ATI SB], device 1: ALC887-VD Digital [ALC887-VD Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

I want to use Card 1, device 0 for analog. In XBMC, that device is selected by the System-->Settings-->Audio, but nothing comes out. BTW, those settings worked on the old installation too.

Ok - could be XBMC, lets try aplay directly
```
$ aplay /usr/share/xbmc/addons/skin.confluence/sounds/notify.wav
ALSA lib pcm_dmix.c:1018:(snd_pcm_dmix_open) unable to open slave
aplay: main:682: audio open error: No such file or directory
```

Permissions issue?
```
$ sudo aplay /usr/share/xbmc/addons/skin.confluence/sounds/notify.wav
ALSA lib pcm_dmix.c:1018:(snd_pcm_dmix_open) unable to open slave
aplay: main:682: audio open error: No such file or directory
```
Nope.

Specify the device:
```
$ aplay -D hw:1,0 /usr/share/xbmc/addons/skin.confluence/sounds/notify.wav
Playing WAVE '/usr/share/xbmc/addons/skin.confluence/sounds/notify.wav' : Signed 16 bit Little Endian, Rate 32000 Hz, Mono
aplay: set_params:1087: Channels count non available
```

Better, but still no sound output.
If aplay sees the device, then the drivers are loaded ... 
```
$ lsmod |grep snd
snd_hda_codec_realtek    56448  1 
snd_hda_codec_hdmi     41736  1 
snd_hda_intel          53038  0 
snd_hda_codec         194727  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
snd_hwdep              13613  1 snd_hda_codec
snd_pcm               107140  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30416  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                66061  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29989  2 snd_pcm,snd_seq
snd_seq_device         14497  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    73753  11 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_seq_midi,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              12680  1 snd
snd_page_alloc         18798  2 snd_hda_intel,snd_pcm
```
Yep. Lots of driver support.
What about the volume controls? Using **alsamixer** for that.
```

 Card: HDA ATI SB                                     F1:  Help               &#9474;
&#9474; Chip: Realtek ALC887-VD                              F2:  System information &#9474;
&#9474; View: F3:[Playback] F4: Capture  F5: All             F6:  Select sound card  &#9474;
&#9474; Item: Master [dB gain: -3.00]                        Esc: Exit               &#9474;
&#9474;                                                                              &#9474;
&#9474;     &#9484;&#9472;&#9472;&#9488;     &#9484;&#9472;&#9472;&#9488;     &#9484;&#9472;&#9472;&#9488;     &#9484;&#9472;&#9472;&#9488;     &#9484;&#9472;&#9472;&#9488;     &#9484;&#9472;&#9472;&#9488;     &#9484;&#9472;&#9472;&#9488;     &#9484;&#9472;&#9472;&#9488;      &#9474;
&#9474;     &#9474;  &#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;     &#9474;  &#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;      &#9474;
&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;     &#9474;  &#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;      &#9474;
&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;     &#9474;  &#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;      >
&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;     &#9474;  &#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;      >
&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;     &#9474;  &#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;      >
&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;     &#9474;  &#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;      >
&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;     &#9474;  &#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;      >
&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;     &#9474;  &#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;      >
&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;     &#9474;  &#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;      >
&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;     &#9474;  &#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;      &#9474;
&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;     &#9474;  &#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;      &#9474;
&#9474;     &#9500;&#9472;&#9472;&#9508;     &#9500;&#9472;&#9472;&#9508;     &#9492;&#9472;&#9472;&#9496;     &#9500;&#9472;&#9472;&#9508;     &#9500;&#9472;&#9472;&#9508;     &#9492;&#9472;&#9472;&#9496;     &#9500;&#9472;&#9472;&#9508;     &#9500;&#9472;&#9472;&#9508;      &#9474;
&#9474;     &#9474;MM&#9474;     &#9474;OO&#9474;              &#9474;OO&#9474;     &#9474;MM&#9474;              &#9474;OO&#9474;     &#9474;OO&#9474;      &#9474;
&#9474;     &#9492;&#9472;&#9472;&#9496;     &#9492;&#9472;&#9472;&#9496;              &#9492;&#9472;&#9472;&#9496;     &#9492;&#9472;&#9472;&#9496;              &#9492;&#9472;&#9472;&#9496;     &#9492;&#9472;&#9472;&#9496;      &#9474;
&#9474;      88    100<>100 100<>100 100<>100   0<>0     0<>0   100<>100   100       &#9474;
&#9474;  < Master >Headphon   PCM     Front   Front Mi Front Mi Surround  Center  
```
(hope that copy/paste looks correct)

Verified that the analog jack to the stereo was working by connecting an mp3 player to it. Van Halen STILL ROCKS!

$ more /proc/asound/cards 
```
 0 [Generic        ]: HDA-Intel - HD-Audio Generic
                      HD-Audio Generic at 0xfe020000 irq 41
 1 [SB             ]: HDA-Intel - HDA ATI SB
                      HDA ATI SB at 0xfe024000 irq 16
```

I should also mention that ~/.asoundrc does not exist.


So ... I'm stumped.
Any ideas?

---

### Post by TheFu on 2014-02-17
After spending 2+ hrs on this ... installed **gnome-alsamixer** (and half of all
gnome-apps/libs too!!!) to see the master volume "mute" was checked.  That
setting is **NOT seen** in the CLI **alsamixer**.

Working now. It was immediate.

Update:   So ... alsamixer does have an indication of "mute" - See the "MM" under the Master control?  Toggle that with 'm' character.

See - I was feeling dumb for good reason! ;)

---

