---
title: "Acer Aspire 6920g Sound Working on 8.10 [solution]"
date: 2009-01-04
forum: Multimedia Software
---

### Post by strid3r on 2009-01-04
After much struggle (i mean like a couple of weeks), I finally got my sound to work on ALSA. This is my First tutorial so take it easy. I'll try to get to all of the points.

First thing you need to do is to get the newest version of the ALSA drivers. Save this to your Desktop:
[HTML]ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.18a.tar.bz2[/HTML]
Extract the file 
```
tar -xvf ~/Desktop/alsa-driver-1.0.18a.tar.bz2
```
(paste is Ctrl+Shift+V)

```
cd alsa-driver-1.0.18a
```


Make sure you have multiverse repositories enabled
```
sudo apt-get install build-essential linux-headers-$(uname -r)
```
```
./configure
make
sudo make install
```

Install this little tool called verb to get your sound working:
[HTML]ftp://ftp.suse.com/pub/people/tiwai/misc/hda-verb-0.3.tar.gz[/HTML]
like before, extract and this time copy the contents of folder to a folder in your home directory like ".verb"
```
mkdir ~/.verb && mv -rf * ~/.verb
cd ~/.verb
sudo ./hda-verb /dev/snd/hwC0D0 0x15 SET_EAPD_BTLENABLE 2
```

Thats it! Now to check if it worked:


Right click on the volume control at the top and select "Open Volume Control"

Device: HDA Intel (ALSA mixer)

Make sure the following settings are Unmuted and at max volume (if you don't see them, click on preferences and highlight the checkbox next to the device):
PCM , Front, Surround
Go to switches and make sure the Headphone is CHECKED
this turns on the bass

Now turn the Master up to about 85%, no more. Trust me it gets LOUD!

Play something, if you here sound CONGRATS! if not, try unmuting everything.

To be able to have this on startup, just go back to your terminal and:
```
cd ~/.verb && gedit
```
Paste the following:
```

#!/bin/bash
sudo /home/strid3r/Desktop/ALSA/hda-verb-0.3/hda-verb /dev/snd/hwC0D0 0x15 SET_EAPD_BTLENABLE 2

```
Save this as sound.sh
Go to System>Preferences>Sessions
Click +Add
Name: Sound On
Command: sudo bash ~/.verb/sound.sh
Click +Add to save it to your startup


*Notes/Tips about this configuration:

For some weird reason, the headphone switch corresponds to the TUBA bass speaker.
"Front" controls the main speakers.
and "Surround" Controls the Headphone/SPDIF jack.
If you want sound output, just mute "Front" and turn up "Surround"
What I did was, I added an extra volume control on my main panel. I made one of them for Front and the other for Surround.
Just right click on the volume control and click on Preferences.

IF IT DOESN'T WORK
1) Unmute EVERYTHING

2) I'm not sure if you need the newest ALSA firmware, but I installed it so, you can if you choose. If it didn't work for you, then try installing firmware.

Firmware is here:
[HTML]ftp://ftp.alsa-project.org/pub/firmware/alsa-firmware-1.0.17.tar.bz2[/HTML]


If you get this to work or it doesn't work, please leave feedback on how you fixed it (hopefully). :)

---

### Post by applefreakpeeps on 2009-05-07
how about the internal mic?

---

