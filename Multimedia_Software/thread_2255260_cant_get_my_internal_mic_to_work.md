---
title: "cant get my internal mic to work"
date: 2014-12-03
forum: Multimedia Software
---

### Post by diegos91 on 2014-12-03
Ubuntu 14.04 (but i tried others distros)
Realtek ALC 272
Its a laptop
Thing ive tried:
changing the hda model
ive tried changing the channel (raising one, and the other one to 0%)
Using another distro
The other mic (the one that plugs in) works ok.
Didint try: installing windows.

---

### Post by ajgreeny on 2014-12-03
Have you looked in **pulseaudio volume control,** which you can get to from the **volume icon -> Sound Settings**, where you should find the gain for the two microphones is shown separately.

You could also run **alsamixer** in terminal and check that the levels of outputs are not set too low.

Move from slider to slider, and raise and lower levels with the cursor keys;
Mute and unmute with the "M" key.
Tab will move you from "playback" to "capture".
Esc will save and exit.

---

### Post by diegos91 on 2014-12-03
Thank you for your answer ajgreeny, I already tried that, and it did not work.

---

### Post by diegos91 on 2014-12-05
bump :c nothing atm
> diegos@diegos-NCL60:~$ lsmod | grep snd
snd_hda_codec_hdmi     48290  1 
snd_hda_codec_realtek    72575  1 
snd_hda_codec_generic    70087  1 snd_hda_codec_realtek
snd_hda_intel          30683  6 
snd_hda_controller     35518  1 snd_hda_intel
snd_hda_codec         144671  5 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_intel,snd_hda_controller
snd_hwdep              13613  1 snd_hda_codec
snd_pcm               113863  6 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_hda_controller
snd_seq_midi           13564  0 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_rawmidi            30865  1 snd_seq_midi
snd_seq                67636  2 snd_seq_midi_event,snd_seq_midi
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              30118  2 snd_pcm,snd_seq
snd                    74235  21 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel,snd_seq_device
soundcore              12680  2 snd,snd_hda_codec


> diegos@diegos-NCL60:~$ aplay -l
**** Lista de PLAYBACK dispositivos hardware ****
tarjeta 0: MID [HDA Intel MID], dispositivo 0: ALC272 Analog [ALC272 Analog]
  Subdispositivos: 0/1
  Subdispositivo #0: subdevice #0
tarjeta 0: MID [HDA Intel MID], dispositivo 3: HDMI 0 [HDMI 0]
  Subdispositivos: 1/1


> [http://www.alsa-project.org/db/?f=a8dc45d8adb001d4c4b31de42de1ef8c32997d15](http://www.alsa-project.org/db/?f=a8dc45d8adb001d4c4b31de42de1ef8c32997d15)
Lets see if anything of this helps

---

### Post by sudodus on 2014-12-09
> **ajgreeny said:**
> Have you looked in **pulseaudio volume control,** which you can get to from the **volume icon -> Sound Settings**, where you should find the gain for the two microphones is shown separately.

You could also run **alsamixer** in terminal and check that the levels of outputs are not set too low.

Move from slider to slider, and raise and lower levels with the cursor keys;
Mute and unmute with the "M" key.
Tab will move you from "playback" to "capture".
Esc will save and exit.

+1

I usually succeed using pulseaudio and pavucontol (the pulsaudio volume control graphical user interface).

It may take a while, sometimes*** hours*** to explore and test all the available settings. I run some soundtrack while exploring the settings in order to get instant response, when things start to work. Try to change things in a systematic way (maybe keep track of what was tested with pencil and paper).

---

### Post by diegos91 on 2014-12-10
> **sudodus said:**
> +1

I usually succeed using pulseaudio and pavucontol (the pulsaudio volume control graphical user interface).

It may take a while, sometimes*** hours*** to explore and test all the available settings. I run some soundtrack while exploring the settings in order to get instant response, when things start to work. Try to change things in a systematic way (maybe keep track of what was tested with pencil and paper).

already tried that again also tried using diff channels but it didnt work

---

### Post by sudodus on 2014-12-10
Do you know that the hardware is good?

- Does it work in a live system (if you try various linux distros and versions live from DVD or USB drives without installing)? You might find a distro/version which has a good driver or good recognition tool for your particular audio hardware. ***Knoppix*** is known for good hardware recognition.

---

### Post by diegos91 on 2014-12-10
Ive tried some live cds, but ill try knoppix. (Downloading
It works everything, even the plug-in mic. except the internal mic

---

### Post by sudodus on 2014-12-11
Well, if no linux is working with the internal mic, it might be broken. The last resort would be to install Windows (and a suitable audio driver?) to test if that mic can work.

---

### Post by diegos91 on 2014-12-11
well ive tried knopix and didnt found anything
also tried some other fixes changing  alsa-base.conf
using gstreamer
the weirdest thing is: that when i call echo in skype, and look at pavucontrol it says internal analog stereo  and the other option is: monitor of internal analog stereo.
The option Im thinking is buying a microphone c: but ty for your answer

---

