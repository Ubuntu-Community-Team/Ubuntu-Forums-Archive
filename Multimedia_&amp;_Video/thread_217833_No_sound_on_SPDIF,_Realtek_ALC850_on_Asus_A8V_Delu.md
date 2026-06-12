---
title: "No sound on S/PDIF, Realtek ALC850 on Asus A8V Deluxe"
date: 2006-07-17
forum: Multimedia &amp; Video
---

### Post by martinielsen on 2006-07-17
As a newbe in Linux i find it difficult to make the sound work in Dapper Drake. I think that my onboard soundchip (Realtek ALC850) on my Asus A8V Deluxe motherboard is detected and the relevant driver (uses AC'97 driver in Windows) is automatically installed, but i'm not sure. In the sound prefs. the selected device is "VIA 8237", probably related to my chipset. I use the S/PDIF coaxial out because of the poor quality and loud background noise on the analogue channel. And i think that's the reason that i have no sound. I can not find any S/PDIF settings in the sound prefs.

I have checked the thread here:
[http://ubuntuforums.org/showthread.php?t=32213&highlight=S%2FPDIF+ALC850](http://ubuntuforums.org/showthread.php?t=32213&highlight=S%2FPDIF+ALC850)

But can not find the asound.conf file on my system

Anyone got a clue?

Martin

---

### Post by slider on 2006-07-17
You need to use alsamixer to enable the S/PDIF output. I have a different chipset than yours but had the same issue. It was muted by default.

It is installed with the alsa-tools package 

apt-get install alsa-tools

There are a couple graphical front ends for it but I haven't used either. If you search this forum for alsamixer you will get much more info.

---

### Post by martinielsen on 2006-07-17
Thank you! I will look into that alsa-tools tomorrow, i hope it's not too difficult

---

### Post by slider on 2006-07-18
> **martinielsen said:**
> Thank you! I will look into that alsa-tools tomorrow, i hope it's not too difficult

It's easy. Just make sure to read the man page. The interface is  non-intuitive otherwise.

From the man page (man alsamixer)

```
When a mixer control is turned off, M (mute) appears below  the  volume bar.   When it’s turned on, O in green appears instead.  You can toggle the switch via m key.
```

---

### Post by martinielsen on 2006-07-18
I found the alsamixer (it was not difficult - thanks :)) and unmuted different channels plus turned up the volume. I could not find any channel labeled "S/PDIF" but "IEC958", "IEC958 0" and "IEC958 P"  should be the right ones. No matter what i do, there is no effect. I searched this forum and i can see the many others have the same problem (someone say that it is deeper than alsamixer), but i did not find any solution though.

Some guy even given up Ubuntu on this issue :( :
[http://ubuntuforums.org/showthread.php?t=197843&highlight=alsamixer+spdif](http://ubuntuforums.org/showthread.php?t=197843&highlight=alsamixer+spdif)

My hardware:
Asus A8V Deluxe motherboard with:
VIA VT8237 and Realtek ALC850, 8-channel
Using the coaxial S/PDIF out

I took a look at all the files in the /proc/asound/, there's a lot files and folders in that place. That's making making me nervous. Will i ever fix this?

---

### Post by martinielsen on 2006-07-18
Sorry about replying my own post. I just discovered that the config files in the asound folder are empty. There is a lot og folders and files there, but all the files are empty. 0 bytes of data. Very strange! I can see the alsamixer detects my card if i use the F2 it writes something like:

/proc/asound/version:
0 [V8237          ]: VIA8237 - VIA 8237
 VIA 8237 with ALC850 at 0xe800, irq 209
1 [U0x46d0x8d9    ]: USB-Audio - USB Device 0x46d:0x8d9
USB Device 0x46d:0x8d9 at usb-0000:00:10.0-2, full speed

/proc/asound/devices:
17: [0- 1]: digital audio playback
25: [0- 1]: digital audio capture
16: [0- 0]: digital audio playback
24: [0- 0]: digital audio capture
0: [0- 0]: ctl
1:       : sequencer
33:       : timer
56: [1- 0]: digital audio capture
32: [1- 0]: ctl

/proc/asound/oss/devices:
12: [0-12]: digital audio
3: [0- 3]: digital audio
0: [0- 0]: mixer
1:       : sequencer
8:       : sequencer
19: [1- 3]: digital audio
16: [1- 0]: mixer

And so on...

---

### Post by martinielsen on 2006-07-19
Does anyone know a music player that will work with S/PDIF for sure?

---

### Post by LordRaiden on 2006-07-19
/proc/asound does not hold config files. 

try the instructions in the post that you refer to.

Do ```
aplay -l
```

Find line that has digital output (0, 1, 2, or 3)

then do ```
sudo nano /etc/asound.conf
```

type in ```
pcm "hw:0,x"
``` where x is the number corresponding to the digital output in the previous step. Reboot then try your audio.  If it does not work, try /etc/asound instead of /etc/asound.conf.

---

### Post by martinielsen on 2006-07-22
The solution you all came up with seemed so easy "just un-mute...", but now, after days of fumbling with the GUI sound controls i finally got sweet music here!! :-D

I think i better share it here if someone else with the same type of motherboard and chipset runs into problems. Here's what i did:

First of all i had to unplug my USB webcam (Logitech QuickCam Connect) and reinstall Ubuntu in order to get the right sound card hardware detection, there might be an easier way for skilled users, but i'm a newbe so reinstallation was my best choice :) Before when my webcam was connected, two sound devices was detected: VIA 8237 and my webcam microphone (USB sound device). Now with the webcam unplugged, the GUI sound controls (in the sys tray) tells me i still have two sound devices: VIA 8237 (Alsa mixer) and Realtek ALC850 rev 0 (OSS Mixer). As far as i know the Realtek "device" is a software codec emulated sound device, but this device was somehow not detected with the USB webcam plugged. If i knew how to get access to the OSS Mixer controls in Ubuntu i might had been able to find the Realtek device, but i will never know.

With the VIA 8237 (Alsa mixer) and Realtek ALC850 rev 0 (OSS Mixer) detected i right clicked the sound icon in sys tray and then "Preferences". I changed the device to Realtek ALC850 rev 0 (OSS Mixer) and selected the "Digital-1" track. The "Digital-1" was muted, so i un-muted it, but still i got no sound.

Then i right clicked the sound icon again and then selected "Open Volume Control". In "Volume Control: VIA 8237 (Alsa mixer)" go to Edit -> Preferences and mark the first IEC958 track on the list (the Output and Playback tracks are not needed). With the IEC958 selected there will be a new flag named "Options" available. Click "Options" and change the IEC958 track from "Analog In" to "PCM" - that's it, enjoy the music :)

Remember that the Master volume control (and other volume controls) does not work. If you want to adjust volume you have to adjust it from the source. For instance if you are using the Sound Juicer to play music and want to turn the volume down, use the volume slider in Sound Juicer. If you are fumbling with the Digital-1 volume control, the sound will immediately turn off and the IEC958 track will without notice pop back from PCM to Analog In in the "Volume Control: VIA 8237 (Alsa mixer)" -> Options and you will have to change it back to PCM to get the sound on again (if it's still showing the PCM, close the window and open it again, and you will see that Analog In is selected). Don't ask me why this is happening, it took me days to discover that behaviour!

To all you people trying to help me out - thank you!! Without your help i would have given up and turned back to Windows XP a long time ago ;)

Martin

---

### Post by pelayostyle on 2007-07-25
Thank you for this , i had the same issue and it worked for me.

---

### Post by lefthand on 2007-07-31
Thanks martinielsen, this worked for me on my ASUS m2n-e mobo.! It's interesting that it's not enough to just turn the volume up but that it has to be set in volume control 'preferences' as well.

---

