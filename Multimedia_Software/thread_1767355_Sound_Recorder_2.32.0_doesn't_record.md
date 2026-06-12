---
title: "Sound Recorder 2.32.0 doesn't record"
date: 2011-05-25
forum: Multimedia Software
---

### Post by FernandoTertiary on 2011-05-25
Hola,

It appears am having problems with Sound Recorder 2.32.0. It is not recording. Has anybody ascertained anything about the matter?

Gracias.

---

### Post by lidex on 2011-05-25
What are you trying to record from - internal mic, external mic, line? Post your amixer output please:
```
amixer
```

---

### Post by SoFl W on 2011-05-25
You are going to have to provide a little more info.  I had an old voice recording on a cassette tape I wanted to convert to MP3 or wav.  I hooked up an old "boom box" headset connector to the line in on my sound card.
 I remember having problems, but I don't recall the exact problem.  Maybe I could see the level meters moving but didn't get anything when I played it back.  I believe I had to adjust the File-> Open Volume Control-> Hardware and change the "Profile" selections around.  If I recall correctly Duplex mode was what worked.

---

### Post by FernandoTertiary on 2011-05-27
amixer output is:

```
Simple mixer control 'Master',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined penum
  Playback channels: Mono
  Limits: Playback 0 - 31
  Mono: Playback 25 [81%] [-9.00dB] [on]
Simple mixer control 'Headphone',0
  Capabilities: pswitch penum
  Playback channels: Front Left - Front Right
  Mono:
  Front Left: Playback [on]
  Front Right: Playback [on]
Simple mixer control 'PCM',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 31 [100%] [0.00dB] [on]
  Front Right: Playback 31 [100%] [0.00dB] [on]
Simple mixer control 'Front Mic',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 0 [0%] [-34.50dB] [off]
  Front Right: Playback 0 [0%] [-34.50dB] [off]
Simple mixer control 'Front Mic Boost',0
  Capabilities: volume penum
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: 0 - 3
  Front Left: 3 [100%] [30.00dB]
  Front Right: 3 [100%] [30.00dB]
Simple mixer control 'Line',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 0 [0%] [-34.50dB] [off]
  Front Right: Playback 0 [0%] [-34.50dB] [off]
Simple mixer control 'IEC958',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'IEC958 Default PCM',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'Capture',0
  Capabilities: cvolume cswitch penum
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 31
  Front Left: Capture 29 [94%] [27.00dB] [on]
  Front Right: Capture 29 [94%] [27.00dB] [on]
Simple mixer control 'Capture',1
  Capabilities: cvolume cswitch penum
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 31
  Front Left: Capture 0 [0%] [-16.50dB] [on]
  Front Right: Capture 0 [0%] [-16.50dB] [on]
Simple mixer control 'Input Source',0
  Capabilities: cenum
  Items: 'Rear Mic' 'Front Mic' 'Line'
  Item0: 'Front Mic'
Simple mixer control 'Input Source',1
  Capabilities: cenum
  Items: 'Rear Mic' 'Front Mic' 'Line'
  Item0: 'Rear Mic'
Simple mixer control 'Rear Mic',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 0 [0%] [-34.50dB] [off]
  Front Right: Playback 0 [0%] [-34.50dB] [off]
Simple mixer control 'Rear Mic Boost',0
  Capabilities: volume penum
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: 0 - 3
  Front Left: 0 [0%] [0.00dB]
  Front Right: 0 [0%] [0.00dB]

```

& Gracias por tu tiempo amiga.

---

### Post by lidex on 2011-05-27
What, again, source are you trying to record from?

First, for mic problem, check this.
**Gnome-alsamixer**
Using Alt+F2 run dialog
```
 gnome-alsamixer 
```
**Use 'Edit -> Sound Card Properties' menu to enable elements.**
Soundcard tab to select / adjust levels.
To install:
```
sudo apt-get install gnome-alsamixer
```

Then go to 'Sound Preferences' to select the correct device and mic ('Connector' option) and unmute your mic in 'Input' tab.
Make sure you have selected a profile with 'duplex' or 'analog input' for the correct sound device on the 'Hardware' tab.
Use Pulse Audio Volume Control (pavucontrol) to unlock stereo sliders for the mic in 'Input Devices' tab. Drag the right slider down to zero. 

From alsa documentation:
> Capture Problems
~~~~~~~~~~~~~~~~
The capture problems are often because of missing setups of mixers.
Thus, before submitting a bug report, make sure that you set up the
mixer correctly.  For example, both "Capture Volume" and "Capture
Switch" have to be set properly in addition to the right "Capture
Source" or "Input Source" selection.  Some devices have "Mic Boost"
volume or switch.

When the PCM device is opened via "default" PCM (without pulse-audio plugin), you'll likely have "Digital Capture Volume" control as well.
This is provided for the extra gain/attenuation of the signal in
software, especially for the inputs without the hardware volume
control such as digital microphones.  Unless really needed, this
should be set to exactly 50%, corresponding to 0dB -- neither extra
gain nor attenuation.  When you use "hw" PCM, i.e., a raw access PCM,
this control will have no influence, though.

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

From ubuntu wiki:
> Changing default subdevice configuration

Some sound devices have multiple capture subdevices (eg. hda-intel), 
but pulseaudio only seems to detect the parent device, and only listens to subdevice #0. 
ALSA may not be configured to use your preferred device as subdevice #0 by default.

Open the pulseaudio record meter (pavumeter --record)
Talk into your chosen device while you carry out the process and watch the meter.
Some channels are quite noisy even with no input (especially on integrated chipsets), 
so we are watching for movements that correspond to our voice. 

Use alsamixer -c n (where n is your sound card number, probably 0)
Press F4 to get to the capture console
Make sure the first capture channel is enabled ("CAPTUR" in red, press space to toggle), 
and the volume turned up.
Check the first input source is switched to your chosen plug (Mic, in my case) 
At this point, you should see the record meter bouncing in response to your voice.
I found that I had to repeat this procedure each time I wanted to use the Mic, 
even though the settings "stuck" in the mixer, something in the soundcard wasn't initialized 
until it was repeated. This also works if you use the "Options" tab in the standard mixer app to do the same thing.

---

### Post by FernandoTertiary on 2011-05-28
Gracias, 
That resolved the problems with the Microphone.

Muchos Gracias.

---

