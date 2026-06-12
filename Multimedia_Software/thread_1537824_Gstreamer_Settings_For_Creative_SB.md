---
title: "Gstreamer Settings For Creative SB"
date: 2010-07-24
forum: Multimedia Software
---

### Post by ZBlue on 2010-07-24
Hi , 

I am using ubuntu 10.04 with ALSA for my Creative sound blaster sound card. This is the output of aplay -l 

```
card 0: SB [HDA ATI SB], device 0: ALC1200 Analog [ALC1200 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 1: ALC1200 Digital [ALC1200 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: Live [Dell Sound Blaster Live!], device 0: emu10k1x [EMU10K1X Front]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: Live [Dell Sound Blaster Live!], device 1: emu10k1x [EMU10K1X Rear]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: Live [Dell Sound Blaster Live!], device 2: emu10k1x [EMU10K1X Center/LFE]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```When using gstreamer-properties I have to choose between the front/centre/rear channels and correspondingly get the sound only from the chosen one instead of all channels. Alsamixer also adjusts sound only for the selected channel.

Is there any way I can get the sound routed to all channels ? (front/rear & center).

Other outputs are posted : cat /proc/asound/version

```
Advanced Linux Sound Architecture Driver Version 1.0.21.
```head -n 1 /proc/asound/card*/codec#*

```
==> /proc/asound/card0/codec#0 <==
Codec: Realtek ALC1200

==> /proc/asound/card1/codec#0 <==
Codec: ATI R6xx HDMI

```Thanks ! :)

---

### Post by no2498 on 2010-07-24
? can you right click the volume control click preferences
in on 804 so im not sure if you can on 10.04

---

### Post by ZBlue on 2010-07-24
> **no2498 said:**
> ? can you right click the volume control click preferences
in on 804 so im not sure if you can on 10.04

i have uninstalled pulseaudio so that option is missing as of now. i still hear sound from each set of speakers.. just that i would like to hear all of them together..

---

### Post by ZBlue on 2010-07-25
> **ZBlue said:**
> i have uninstalled pulseaudio so that option is missing as of now. i still hear sound from each set of speakers.. just that i would like to hear all of them together..

Update : If i choose any among front/centre/rear from gstreamer-properties then i can get sound from all three by setting all inputs equal to the one chosen in alsamixer. but the problem is that this does not allow to control the volumes of the channels independently. 

Still need help !

---

### Post by lidex on 2010-07-26
With pulse it's fairly straightforward, not sure about alsa but maybe something in here:
[http://www.google.com/search?q=surround+sound+alsa&sitesearch=ubuntuforums.org](http://www.google.com/search?q=surround+sound+alsa&sitesearch=ubuntuforums.org)

---

### Post by ZBlue on 2010-07-28
I now get sound from all speakers and can control each channel independently using alsamixer during the speaker test : 

```
speaker-test -Dplug:surround51 -c6  -twav
```But applications (e.g. Guayadequye , SMplayer) still send output either to the front OR the rear OR the center depending on what i choose in gstreamer-properties which gives me the following options : 

[ATTACH]164792[/ATTACH]

The speaker test works correctly when "default" is selected. 

Any ideas on how I can get sound from all speakers while using music/movie applications ??

---

### Post by lidex on 2010-07-30
> **ZBlue said:**
> I now get sound from all speakers and can control each channel independently using alsamixer during the speaker test : 

```
speaker-test -Dplug:surround51 -c6  -twav
```But applications (e.g. Guayadequye , SMplayer) still send output either to the front OR the rear OR the center depending on what i choose in gstreamer-properties which gives me the following options : 

[ATTACH]164792[/ATTACH]

The speaker test works correctly when "default" is selected. 

Any ideas on how I can get sound from all speakers while using music/movie applications ??

Hmm. Have you tried changing audio output through preferences of the apps you mention?

---

### Post by ZBlue on 2010-07-30
> **lidex said:**
> Hmm. Have you tried changing audio output through preferences of the apps you mention?

Well in VLC for example I get the same ALSA audio output choices as in gstreamer - fornt , rear or centre. 

One thing which works is setting all inputs to any one of front/rear/centre in alsamixer which outputs audio to all the channels... but then I am not able to control the volumes independently..

---

### Post by lidex on 2010-07-30
> **ZBlue said:**
> Well in VLC for example I get the same ALSA audio output choices as in gstreamer - fornt , rear or centre. 

One thing which works is setting all inputs to any one of front/rear/centre in alsamixer which outputs audio to all the channels... but then I am not able to control the volumes independently..

Pulse audio volume control should be able to do that.
This may help:
[http://ubuntuforums.org/showthread.php?t=1254492](http://ubuntuforums.org/showthread.php?t=1254492)

---

### Post by ZBlue on 2010-07-31
> **lidex said:**
> Pulse audio volume control should be able to do that.
This may help:
[http://ubuntuforums.org/showthread.php?t=1254492](http://ubuntuforums.org/showthread.php?t=1254492)

thanks for your suggestions,, I should have mentioned earlier that I have removed pulseaudio :p I'm looking for a n ALSA solution.

---

### Post by lidex on 2010-07-31
Alsa, eh? Have a look at the attached document. 
References:
[http://www.sabi.co.uk/Notes/linuxSoundALSA.html](http://www.sabi.co.uk/Notes/linuxSoundALSA.html)
[http://alsa.opensrc.org/index.php/Emu10k1](http://alsa.opensrc.org/index.php/Emu10k1)

---

### Post by ZBlue on 2010-08-07
Fixed it , thanks. Used the .asoundrc configuration which copies stereo sound to all channels.

---

