---
title: "Microphone not working after Update..."
date: 2011-04-29
forum: Multimedia Software
---

### Post by christhecoolboy on 2011-04-29
My Microphone on my MSI AE2020 is not working after I updated to Ubuntu 11.04, It was working perfectly fine before I updated, how can I fix this?! Thanks for any help, Chris...

---

### Post by lidex on 2011-05-01
On the input tab of 'Sound Preferences' make sure it's not muted and you have the correct selection in the connector drop-down.

---

### Post by christhecoolboy on 2011-05-01
> **lidex said:**
> On the input tab of 'Sound Preferences' make sure it's not muted and you have the correct selection in the connector drop-down.

The only connector I have is "Internal Audio Analogue Stereo" and if I open "Alsamixer" and unmute it, I hear hissing static, My mic worked 100% correctly before I upgraded to 11.04...

---

### Post by lidex on 2011-05-01
That's not the connector, see what I'm referring to below. Also what profile is selected on the hardware tab? Needs to be duplex or output + input format.

---

### Post by christhecoolboy on 2011-05-01
> **lidex said:**
> That's not the connector, see what I'm referring to below. Also what profile is selected on the hardware tab? Needs to be duplex or output + input format.
There isn't a connector at all, but there used to be one... and It's Duplex... would a screenshot help at all?! :)

---

### Post by lidex on 2011-05-01
> **christhecoolboy said:**
> There isn't a connector at all, but there used to be one... and It's Duplex... would a screenshot help at all?! :)

That points to the problem. Need a little more info.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.
[Terminal="Applications->Accessories->Terminal"]

---

### Post by christhecoolboy on 2011-05-01
> **lidex said:**
> That points to the problem. Need a little more info.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.
[Terminal="Applications->Accessories->Terminal"]

Already did it yesterday... Hmmm... Errrrr... Trying to find the place I put it... AHA! Here: [http://paste.ubuntu.com/601047/](http://paste.ubuntu.com/601047/) [Please tell me you can fix it], the sda-hda-intel option on alsa-base.conf is auto, because it is the only one that works with the sound card on my PC... I tried every other, but when I installed 10.10, the Mic worked without any problems, it was the sound, that was fixed with "auto"...

---

### Post by lidex on 2011-05-01
Try gnome-alsamixer.
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

Then use pulseaudio volume control (pavucontrol) to select your mic in 'Input Devices' tab.

Your mixer settings:
```
Simple mixer control 'Mic',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 0 [0%] [-34.50dB] [off]
  Front Right: Playback 0 [0%] [-34.50dB] [off]

Simple mixer control 'Mic Boost',0
  Capabilities: volume penum
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: 0 - 3
  Front Left: 3 [100%] [30.00dB]
  Front Right: 3 [100%] [30.00dB]

Simple mixer control 'Capture',0
  Capabilities: cvolume cswitch penum
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 31
  Front Left: Capture 31 [100%] [30.00dB] [on]
  Front Right: Capture 31 [100%] [30.00dB] [on]

Simple mixer control 'Input Source',0
  Capabilities: cenum
  Items: 'Mic' 'Internal Mic'
  Item0: 'Mic'

Simple mixer control 'Internal Mic',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 0 [0%] [-34.50dB] [off]
  Front Right: Playback 0 [0%] [-34.50dB] [off]

Simple mixer control 'Internal Mic Boost',0
  Capabilities: volume penum
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: 0 - 3
  Front Left: 0 [0%] [0.00dB]
  Front Right: 0 [0%] [0.00dB]
```

> Changing default subdevice configuration

    Some sound devices have multiple capture subdevices (eg. hda-intel), but pulseaudio only seems to detect the parent device, and only listens to subdevice #0. ALSA may not be configured to use your preferred device as subdevice #0 by default.

        Open the pulseaudio record meter (pavumeter --record)
        Talk into your chosen device while you carry out the process and watch the meter.
            Some channels are quite noisy even with no input (especially on integrated chipsets), so we are watching for movements that correspond to our voice. 

        Use alsamixer -c n (where n is your sound card number, probably 0)
            Press F4 to get to the capture console
            Make sure the first capture channel is enabled ("CAPTUR" in red, press space to toggle), and the volume turned up.
            Check the first input source is switched to your chosen plug (Mic, in my case) 
        At this point, you should see the record meter bouncing in response to your voice.
        I found that I had to repeat this procedure each time I wanted to use the Mic, even though the settings "stuck" in the mixer, something in the soundcard wasn't initialized until it was repeated.
        This also works if you use the "Options" tab in the standard mixer app to do the same thing. 



---

### Post by christhecoolboy on 2011-05-01
I'm a little confused, what do I have to do? sorry... :(

---

### Post by lidex on 2011-05-01
Open a terminal and paste in this command:
```
sudo apt-get install gnome-alsamixer
```
Terminal="Applications->Accessories->Terminal"
Press the enter key and it will ask for your password. Type it in even though it will not show (for security) and press enter again.
Now open the run dialog with the Alt+F2 key-combo and enter:
```
gnome-alsamixer
``` and click run.
Use 'Edit -> Sound Card Properties' menu to enable elements. Then on the soundcard tab adjust levels. Make sure "Input Source',0" is set to 'internal mic' and 'internal mic' is unmuted and turned up to about 80% and if not enough, utilize the 'internal mic boost'

Refer back to my previous post. You'll need to get your hands dirty and try to figure some things out or we'll be here till July.

---

### Post by christhecoolboy on 2011-05-01
This might take forever because I am not a techy person with Ubuntu yet... :(

---

### Post by christhecoolboy on 2011-05-02
> **christhecoolboy said:**
> This might take forever because I am not a techy person with Ubuntu yet... :(
Do you think you could teamview to fix? i'm rubbish with this... :confused:

---

