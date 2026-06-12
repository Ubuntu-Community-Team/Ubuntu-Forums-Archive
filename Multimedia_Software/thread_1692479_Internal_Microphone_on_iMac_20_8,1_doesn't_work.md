---
title: "Internal Microphone on iMac 20 8,1 doesn't work"
date: 2011-02-21
forum: Multimedia Software
---

### Post by Jboulden on 2011-02-21
Hello:

I am really struggling to get my the internal microphone on my iMac to function.  I was able to get the sound working by installing ALSA Mixer and appending the /etc/modprobe.d/alsa-base.conf file with [options snd-hda-intel model="imac24"].  Input is not muted. That file is attached.

My gnome-volume-control recognizes an 'Internal Audio Analog Stereo' device, but it picks up no sound.  Here's the chip information: Realtek ALC889A.  Any help would be appreciated.

Does anyone have any advice?

---

### Post by zikalify on 2011-02-25
The alsa fix is to get the audio output to work. To get your mic working you need the AppleUSBVideosupport [http://www.mediafire.com/?81xtkqyttjt](http://www.mediafire.com/?81xtkqyttjt) and put it on your desktop. then go to package manager and search isight this will bring up 1 result "isight firmware something' not sure of exact name. tick then apply then when it asks for the directory of isight firmware type "/home/username/Desktop/the exact driver filename. Shutdown unplug from power thenn reboot. This gets video working but still finding fix for mic input sorry :)

---

### Post by Jboulden on 2011-02-26
Thanks.  Oddly enough, the video was working just fine.  So I have video and sound output, but no sound input.

---

### Post by pnneves on 2012-05-02
In the alsa-base.conf file, in the line
options snd-hda-intel model="imac24"
change the model from "imac24" to "mbp3"

Then force reload of the alsa configuration by doing in a terminal:
sudo alsa force-reload

Afterwards, open alsamixer again. Now you should have an input (mic) channel, select it (arrow keys) and unmute it (m key) - btw, imho you should unmute all channels.
Press Esc to exit and save alsamixer configuration.

This should solve the problem (worked for me! iMac 8,1 ;)).

Note - I didn't have any video problem so did not need to patch/download any video driver.

---

### Post by pnneves on 2012-05-02
just another note: if the alsa force-reload doesn't work, you'll have to reboot, then the new alsa settings will take effect.

---

