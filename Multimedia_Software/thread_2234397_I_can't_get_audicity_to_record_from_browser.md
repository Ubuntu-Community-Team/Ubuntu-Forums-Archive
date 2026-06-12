---
title: "I can't get audicity to record from browser"
date: 2014-07-14
forum: Multimedia Software
---

### Post by Frank_Callo on 2014-07-14
Hi all

I just re installed audacity on my laptop.  I'm running ubuntu 12.5.  I have pulse volume control and found a good tutorial which instructs me to set alsa plug in (which I have) in the record tab.  When I go to the record tab (in pulse volume) I get a message saying NO APPLICATIONS RECORDING.  There seems to be nothing for me to set or anything like that.  Any suggestions?

Thanks

---

### Post by Dennis N on 2014-07-14
You will probably find it easier to record streaming audio with audio recorder.

Available through this ppa:

[https://launchpad.net/~osmoma/+archive/audio-recorder](https://launchpad.net/~osmoma/+archive/audio-recorder)

---

### Post by Frank_Callo on 2014-07-14
possibly, but I need to edit.

---

### Post by Dennis N on 2014-07-14
> **Frank_Callo said:**
> possibly, but I need to edit.

Well, you could edit the recording with Audacity.

---

### Post by Dennis N on 2014-07-14
I decided to look into recording streaming audio with Audacity and got it working easily, at least on this computer. I recall trying to record an audio stream with Audacity a few years ago and had problems. No so this time. Attached is an image of Audacity with the settings that worked: 

Host: ALSA
Output device: default
Input device: pulse

Be sure Software Playthrough is OFF in the Transport menu. 
The input volume slider on Audacity doesn't work on this particular Audacity version, so I adjusted the recording (input) volume in Pulse Audio Volume Control > Recording Tab. 

Small window on image is Pulse Audio Vol. Control (PAVC) showing the Recording tab. It should show: "ALSA plugin [audacity]: ALSA Capture from: Monitor of Built-in Audio Analog Stereo". If it shows "Built-In Audio Analog Stereo" or something else click on this to change. Note: the Recording tab is empty unless some audio is being recorded or monitored in Audacity.

The PAVC Configuration tab may show two devices: 1) built-in audio; 2) a high definition audio device - description and options depends on your system. You want the built-in audio set to "Analog Stereo Duplex" and the other device (if present) should be set to "Off".

---

