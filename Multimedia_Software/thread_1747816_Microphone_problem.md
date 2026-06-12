---
title: "Microphone problem"
date: 2011-05-03
forum: Multimedia Software
---

### Post by kindmoji on 2011-05-03
hi,
I have a serious problem , my microphone doesn't work on Ubuntu whereas it works on windows XP very well,
so i can't do voice chats on Ubuntu with skype or pidgin or any other programs.
PLEASE HELP ME.

Best regards.

---

### Post by lidex on 2011-05-04
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

When the PCM device is opened via "default" PCM (without pulse-audio
plugin), you'll likely have "Digital Capture Volume" control as well.
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

