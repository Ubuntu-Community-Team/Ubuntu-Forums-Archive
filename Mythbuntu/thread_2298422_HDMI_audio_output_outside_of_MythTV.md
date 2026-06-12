---
title: "HDMI audio output outside of MythTV"
date: 2015-10-10
forum: Mythbuntu
---

### Post by jonathan.k3 on 2015-10-10
I have two frontends running Mythbuntu 14.04. One is a Lenovo laptop and the other is a ZBox and both are connected to TVs via HDMI. After setting it up, the frontends work as expected, connecting to the backend and playing back recordings (video and audio are good). 

My problem is this. Let's say I exit mythtv and want to use the desktop os to go online and stream from youtube. No sound comes from the TV, only from the speakers in the laptop and no sound from the ZBox miniPC. I've tried searching online and found this:
[https://help.ubuntu.com/community/SoundTroubleshootingProcedure#Other_Useful_Information_to_Quote](https://help.ubuntu.com/community/SoundTroubleshootingProcedure#Other_Useful_Information_to_Quote)

Step 16 halfway works. I can successfully test the HDMI device and sound is outputted from the TV for both the laptop and ZBox but trying to create a conf file as described doesn't work. Sometimes on reboot, mythtv's audio output is broken after creating the conf file. Not sure if I'm doing it wrong or if the info in the guide is outdated. Saw something about adding the user to the audio group, tried it and didn't work for either machine. 

How do I tell the OS to output sound through HDMI for Mythbuntu 14.04? Can I make it default like how it is in MythTV?

---

### Post by blm-ubunet on 2015-10-10
Just let pulseaudio handle system wide audio.
MythTV will stop the pulseaudio server if you use the alsa audio device (in mythtv) & restarts pa server on exit.
With this arrangement when MythTV is running there is no audio sharing/system wide sound.

Install run "pavucontrol".
The "tabs" are setup for most common use first so go the last tab & select your preferred config & then output device.

---

### Post by jonathan.k3 on 2015-10-12
Worked perfectly. Tried rebooting afterwards and the devices output sound to HDMI by default as desired. Thanks for the info.

---

