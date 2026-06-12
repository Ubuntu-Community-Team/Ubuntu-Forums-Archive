---
title: "adjusting volume while recording audio playback and microphone"
date: 2010-11-13
forum: Multimedia Software
---

### Post by ben22 on 2010-11-13
Hiya,

In short:
how can I adjust the volume level while recording audio playback and microphone at the same time? I managed to increase the audio playback volume with PulseAudio Volume Control (Input devices -> Monitor of Internal Audio Analog Stereo -> pressing green button "Set as fallback"), but once I click on that green button, no no microphone sound is recorded.

Details:
- using Ubuntu 10.04 LTS
- recording audio with Sound Recorder
- installed PulseAudio Device Choooser and PulseAudio Volume Control
- Input devices -> Internal Audio Analog Stereo --> shows the sound from microphone
- Input devices -> Monitor of Internal Audio Analog Stereo --> shows sound from audioplayback

- Input devices -> Monitor of Internal Audio Analog Stereo -> I press green button "Set as fallback"--> audio playback recorded, but no microphone sound
- Input devices ->  Internal Audio Analog Stereo -> I press green button "Set as fallback"--> microphone sound, but no audio playback.


Question:
- how to adjust volume of audioplayback and microphone recording and record both as a mix together? Thanks!

PS: I checked out this [thread]("http://ubuntuforums.org/showthread.php?t=1379252"), but haven't figured out how to adjust the volumes.

---

### Post by ben22 on 2010-11-13
I tried the following:
- Set it to get to the point where it will record from your sound card.
- Then press Alt-F2 and enter "cvlc alsa://hw:0,0". 
- I hear my own voice via the headphones, but it is not recorded with the audio playback and another gnome-sound-recorder is opened and I get error "No file name specified for writing"

any suggestions?

---

### Post by Leo Damascus on 2010-11-13
Is there any way you could send me an audio file that can show me what's going wrong?  Preferably a downloadable one (or embedded in a YouTube video or some other streamable service) as I am currently occupied with something else and unable to log onto a chat client at the moment.

---

### Post by ben22 on 2010-11-13
hm - it seems it cant open the device

```
leo@ubuntu:~$ cvlc alsa://plughw:0,1
VLC media player 1.0.6 Goldeneye
[0x8630840] dummy interface: using the dummy interface module...
[0x863b458] access_alsa demux error: cannot open device plughw:0,1 for ALSA audio (No such file or directory)
[0x8645758] main access error: no access module matched "alsa"
[0x8637dd0] main input error: open of `alsa://plughw:0,1' failed: no access module matched "alsa"
[0x8637dd0] main input error: Your input can't be opened
[0x8637dd0] main input error: VLC is unable to open the MRL 'alsa://plughw:0,1'. Check the log for details.
^C[0x861e358] signals interface error: Caught Interrupt signal, exiting...

leo@ubuntu:~$ cvlc alsa://plughw:0,0
VLC media player 1.0.6 Goldeneye
[0x990fac0] dummy interface: using the dummy interface module...
[0x99133d0] access_alsa demux error: cannot open device plughw:0,0 for ALSA audio (Device or resource busy)
[0x9923280] main access error: no access module matched "alsa"
[0x9910420] main input error: open of `alsa://plughw:0,0' failed: no access module matched "alsa"
[0x9910420] main input error: Your input can't be opened
[0x9910420] main input error: VLC is unable to open the MRL 'alsa://plughw:0,0'. Check the log for details.
^C[0x985c8d0] signals interface error: Caught Interrupt signal, exiting...

```

---

