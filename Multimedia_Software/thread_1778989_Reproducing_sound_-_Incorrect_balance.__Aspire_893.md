---
title: "Reproducing sound - Incorrect balance.  Aspire 8935g"
date: 2011-06-09
forum: Multimedia Software
---

### Post by Graham C Williams on 2011-06-09
Acer Aspire 8935G. ubuntu 11.04 64bit
The laptop speakers reproduce sound but the balance is to the far Right-hand side of the system. The Headphone output is OK, it is only the laptop speaker reproduction where the balance is incorrect. 
Is there a more comprehensive mixer that will allow me do a 5.1 balance with a 2 channel signal? 
I think the error is associated with the system trying to create a stereo balance on a SS speaker setup - the Alsa Mixer and the Gnome mixer are not upto the task. (It appears as if the speakers are setup for someone to listen with the laptop turned sideways (from the POV of the RH end of the keypad))
Perhaps there are some manual adjustments I can make to alter the balance across the system?

Graham

---

### Post by lidex on 2011-06-09
Post your amixer output please:
```
amixer
```
What profile is selected in 'Sound Preferences'?

---

### Post by Graham C Williams on 2011-06-10
Hi.

monique@monique-Aspire-8935G:~$ amixer
Simple mixer control 'Master',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined penum
  Playback channels: Mono
  Limits: Playback 0 - 64
  Mono: Playback 50 [78%] [-14.00dB] [on]
Simple mixer control 'Headphone',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 64
  Mono:
  Front Left: Playback 62 [97%] [0.00dB] [on]
  Front Right: Playback 62 [97%] [0.00dB] [on]
Simple mixer control 'Speaker',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 64
  Mono:
  Front Left: Playback 62 [97%] [0.00dB] [on]
  Front Right: Playback 62 [97%] [0.00dB] [on]
Simple mixer control 'PCM',0
  Capabilities: pvolume penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 255
  Mono:
  Front Left: Playback 255 [100%] [0.00dB]
  Front Right: Playback 255 [100%] [0.00dB]
Simple mixer control 'Line',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 23 [74%] [0.00dB] [off]
  Front Right: Playback 23 [74%] [0.00dB] [off]
Simple mixer control 'Mic',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 23 [74%] [0.00dB] [off]
  Front Right: Playback 23 [74%] [0.00dB] [off]
Simple mixer control 'Mic Boost',0
  Capabilities: volume penum
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: 0 - 3
  Front Left: 0 [0%] [0.00dB]
  Front Right: 0 [0%] [0.00dB]
Simple mixer control 'IEC958',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'IEC958 Default PCM',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'Beep',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 23 [74%] [0.00dB] [off]
  Front Right: Playback 23 [74%] [0.00dB] [off]
Simple mixer control 'Capture',0
  Capabilities: cvolume cswitch penum
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 46
  Front Left: Capture 28 [61%] [12.00dB] [on]
  Front Right: Capture 28 [61%] [12.00dB] [on]
Simple mixer control 'Capture',1
  Capabilities: cvolume cswitch penum
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 46
  Front Left: Capture 0 [0%] [-16.00dB] [on]
  Front Right: Capture 0 [0%] [-16.00dB] [on]
Simple mixer control 'Capture',2
  Capabilities: cvolume cswitch penum
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 46
  Front Left: Capture 0 [0%] [-16.00dB] [on]
  Front Right: Capture 0 [0%] [-16.00dB] [on]
Simple mixer control 'Input Source',0
  Capabilities: cenum
  Items: 'Mic' 'Line'
  Item0: 'Mic'
Simple mixer control 'Input Source',1
  Capabilities: cenum
  Items: 'Mic' 'Line'
  Item0: 'Mic'
Simple mixer control 'Input Source',2
  Capabilities: cenum
  Items: 'Mic' 'Line'
  Item0: 'Mic'

Graham. (monique is my daughter)

---

### Post by lidex on 2011-06-12
Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.
[Terminal="Applications->Accessories->Terminal"]

---

### Post by Graham C Williams on 2011-06-12
-Aspire-8935G:~$ wget [http://www.alsa-project.org/alsa-info.sh](http://www.alsa-project.org/alsa-info.sh) -O alsa-info.sh && bash alsa-info.sh
--2011-06-12 18:15:35--  [http://www.alsa-project.org/alsa-info.sh](http://www.alsa-project.org/alsa-info.sh)
Resolving [www.alsa-project.org](www.alsa-project.org)... 77.48.224.243
Connecting to [www.alsa-project.org|77.48.224.243|:80](www.alsa-project.org|77.48.224.243|:80)... connected.
HTTP request sent, awaiting response... 302 Found
Location: [http://git.alsa-project.org/?p=alsa-driver.git;a=blob_plain;f=utils/alsa-info.sh](http://git.alsa-project.org/?p=alsa-driver.git;a=blob_plain;f=utils/alsa-info.sh) [following]
--2011-06-12 18:15:39--  [http://git.alsa-project.org/?p=alsa-driver.git;a=blob_plain;f=utils/alsa-info.sh](http://git.alsa-project.org/?p=alsa-driver.git;a=blob_plain;f=utils/alsa-info.sh)
Resolving git.alsa-project.org... 77.48.224.243
Reusing existing connection to [www.alsa-project.org:80](www.alsa-project.org:80).
HTTP request sent, awaiting response... 200 OK
Length: unspecified [text/plain]
Saving to: `alsa-info.sh'

    [  <=>                                  ] 27,247       118K/s   in 0.2s    

2011-06-12 18:15:40 (118 KB/s) - `alsa-info.sh' saved [27247]

ALSA Information Script v 0.4.60
--------------------------------

This script visits the following commands/files to collect diagnostic
information about your ALSA installation and sound related hardware.

  dmesg
  lspci
  lsmod
  aplay
  amixer
  alsactl
  /proc/asound/
  /sys/class/sound/
  ~/.asoundrc (etc.)

See 'alsa-info.sh --help' for command line options.

Automatically upload ALSA information to [www.alsa-project.org?](www.alsa-project.org?) [y/N] : y
Uploading information to [www.alsa-project.org](www.alsa-project.org) ...  Done!

Your ALSA information is located at [http://www.alsa-project.org/db/?f=649cbb34367dd54988dcdcee6804dd582e71b2f2](http://www.alsa-project.org/db/?f=649cbb34367dd54988dcdcee6804dd582e71b2f2)

Please inform the person helping you.

---

### Post by Graham C Williams on 2011-06-13
Ref: What profile is selected in 'Sound Preferences'?

There are a number of preferences. What one are you after?
Hardware: Internal Audio 1 Output/1 Input. Analogue Stereo Duplex
(There is an alternative: RV710/730 1 output Digital Stereo (HDMI) Output)

Input: Internal Audio Analogue Stereo

Output: Internal Audio Analogue Stereo (Alternative: RV710/730 Digital Stereo (HDMI)). Connector: Analogue Speakers.

Sorry, I missed this question earlier.
Graham

---

### Post by lidex on 2011-06-13
Just for giggles try this:
```
echo "options snd-hda-intel model=acer-aspire-8930g" | sudo tee -a /etc/modprobe.d/alsa-base.conf
``` **Reboot**

---

### Post by Graham C Williams on 2011-06-14
Well Sir. I think I can see what you have done but the main point is..It Works. Ha Ha. Big Thanks for your help.

Graham

---

### Post by lidex on 2011-06-15
> **Graham C Williams said:**
> Well Sir. I think I can see what you have done but the main point is..It Works. Ha Ha. Big Thanks for your help.

Graham

You're welcome. Please mark the thread solved using 'Thread Tools' up top.

---

