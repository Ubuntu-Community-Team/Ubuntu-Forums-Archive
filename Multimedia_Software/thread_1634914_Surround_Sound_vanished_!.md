---
title: "Surround Sound vanished !"
date: 2010-12-01
forum: Multimedia Software
---

### Post by mhtkhan on 2010-12-01
I've done a fresh install of Ubuntu 10.10 a couple of days ago. My sound card is Creative Sound Blaster Live and I have 4.1 speakers. On the first day I had to choose " 5.1 output + Analog Stereo Input " (from System->Preferences->Sound->Hardware menu) to hear sounds from all channels. On the second day the sound became distorted so I had to choose "4.0 channels". Today I'm still on "4.0 Channels" but don't have any surround sound, sound is coming out from the Rear channels only. I've tried other combinations and even toggled the Connector settings, but no use. Other combinations (like "4.1 Output") result in distorted output. Would you be kind enough to help me out ?

My ALSA info:

[http://www.alsa-project.org/db/?f=79dfb460ad35b0102cf9b4d5dfb2e480fe64a662](http://www.alsa-project.org/db/?f=79dfb460ad35b0102cf9b4d5dfb2e480fe64a662)

=> Additional info: My sound card has two output jacks, one for the front speakers and one for the rear.

---

### Post by lidex on 2010-12-02
> **mhtkhan said:**
> I've done a fresh install of Ubuntu 10.10 a couple of days ago. My sound card is Creative Sound Blaster Live and I have 4.1 speakers. On the first day I had to choose " 5.1 output + Analog Stereo Input " (from System->Preferences->Sound->Hardware menu) to hear sounds from all channels. On the second day the sound became distorted so I had to choose "4.0 channels". Today I'm still on "4.0 Channels" but don't have any surround sound, sound is coming out from the Rear channels only. I've tried other combinations and even toggled the Connector settings, but no use. Other combinations (like "4.1 Output") result in distorted output. Would you be kind enough to help me out ?

My ALSA info:

[http://www.alsa-project.org/db/?f=79dfb460ad35b0102cf9b4d5dfb2e480fe64a662](http://www.alsa-project.org/db/?f=79dfb460ad35b0102cf9b4d5dfb2e480fe64a662)

=> Additional info: My sound card has two output jacks, one for the front speakers and one for the rear.

Choose the correct profile then try gnome-alsamixer to set sound levels appropriately . Too high levels will distort. Also make sure unused inputs are muted.
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
emu10k1@alsaProject:
[http://www.alsa-project.org/main/index.php/Matrix:Module-emu10k1](http://www.alsa-project.org/main/index.php/Matrix:Module-emu10k1)

---

