---
title: "Default Output Settings for ALSA only apply to aply?"
date: 2010-04-05
forum: Multimedia Software
---

### Post by illafam on 2010-04-05
Software/Hardware:
Ubuntu 9.10 64 bit
Creative Digital SX USB Sound Card

Problem:
I have a Creative Digital SX Sound Card.  When ever I play sound its very distorted and crackly.  (This happens on OS X Intel machines as well.)  After some digging around I created an .asound file in my home folder.  It has the following contents:


pcm.!default {
        type hw
        card 1
        device 0
        rate 48000
}

ctl.!default {
        type hw
        card 1
        device 0
        rate 48000
}

Once I added the line rate 48000 I was able to hear my audio as per normal with aplay.

illa@illa-desktop:~$ aplay -D default test.wav 
Playing WAVE 'test.wav' : Signed 16 bit Little Endian, Rate 44100 Hz, Stereo
Warning: rate is not accurate (requested = 44100Hz, got = 48000Hz)
         please, try the plug plugin (-Dplug:default)

OR

illa@illa-desktop:~$ aplay -Dplug:default test.wav 
Playing WAVE 'test.wav' : Signed 16 bit Little Endian, Rate 44100 Hz, Stereo


So this works fine through aplay.  My problem is how do I get other applications to use these settings.  My understanding is that whatever I set as my default in the .asound file should be for all applications.  

 Aplay respects this as I no longer need to specify a device name and it will use the correct settings.  So for instance if I run 

 illa@illa-desktop:~$ aplay test.wav 
Playing WAVE 'test.wav' : Signed 16 bit Little Endian, Rate 44100 Hz, Stereo
Warning: rate is not accurate (requested = 44100Hz, got = 48000Hz)
         please, try the plug plugin (-Dplug:default)

The audio playback is fine, and I did not need to specify a device I defined in my .asound file

I just need the rest of the applications to obey this.

---

### Post by illafam on 2010-05-11
after messing around with this further I noticed that in VLC/Preferences I can set a default output device.. I changed this from default to ALSA.. now VLC works fine.. not all my applications seem to have configuration options like this(rhythm box/firefox etc.)

I also un-installed pulse server.. once I did that all sounds played correctly.. but my volume control applet was gone and I can not control the volume of my ps3 from the digital in component... reinstalled pulse audio server.. now the sound is distorted again unless I use vlc or aplay..

I dont really understand how pulse works.. but it seems to me as long as the sound doesn't go through pulse its fine

---

### Post by Yellow Pasque on 2010-05-11
When you are using aplay or VLC with ALSA output, you are bypassing pulseaudio and sending sound to ALSA's software mixer (dmix), which resamples to 48kHz before sending the audio to your card.

When you use other programs, they use pulseaudio output by default, which doesn't resample 44.1kHz audio in its default configuration, so 44.1kHz audio is sent to your card. Creative cards resample to 48kHz in hardware, and apparently, your card's hardware mixer is either defective or picking up motherboard noise.

The best way around this would be to make pulse resample to 48kHz, so open up the configuration file for editing:
```
gksu gedit /etc/pulse/daemon.conf
```
Change this line:
```
; default-sample-rate = 44100
```
to:
```
default-sample-rate = 48000
```
Save. Quit. Close all apps using audio and reboot or just restart pulse:
```
sudo pulseaudio --kill && sudo pulseaudio --start
```

If that works and you want all apps to use pulse, change your asouond.conf like so: [http://ubuntuforums.org/showthread.php?t=1455816](http://ubuntuforums.org/showthread.php?t=1455816)

---

