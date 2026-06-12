---
title: "How to record internal audio with Audacity in any Ubuntu-derivative"
date: 2013-02-12
forum: Multimedia Software
---

### Post by opiumpoetry on 2013-02-12
[COLOR=#000000][FONT=arial][SIZE=1]1.Install pulseaudio and pavucontrol (PulseAudio Volume Control) in terminal (sudo apt-get install [/SIZE][/FONT][/COLOR][COLOR=#000000][FONT=arial]pulseaudio[/FONT][/COLOR][COLOR=#000000][FONT=arial][SIZE=1] [/SIZE]pavucontrol)[SIZE=1] or using Synaptic or whichever software center you have installed.
2.Open PulseAudio Volume Control. It should be in the applications menu under Sound and Video.
3.Open Audacity and start recording (hit the button with the red dot in the upper left panel). Start playing any audio file.
4.Hit the "Recording" tab in the PulseAudio Volume Control window.
5.At the bottom, where it says "Show," make sure "Applications" is selected.
6.At the top, where it says "ALSA plug-in [audacity] : ALSA Capture *from*," choose "Monitor of Internal Audio Analog Stereo".

This appears to be persistent so that you will only have to do it once, but you will have to repeat these steps to record in another application (such as Sound Recorder or mhWaveEdit).[/SIZE][/FONT][/COLOR]

---

