---
title: "Audio in Firefox but not in music players"
date: 2017-12-02
forum: Multimedia Software
---

### Post by mfox on 2017-12-02
I don't recall the circumstances when I first noticed this, but my audio is highly irregular. It is totally reliable in Firefox 57 when playing youtube, but play the same in Chromium and I have no audio. Also, I have no reliable audio in rhythmbox, and to test whether rhythmbox is the culprit I have tried playing the same songs in VLC, Audacious, Clementine and MPlayer, none of which give audio. I have tried fiddling with the settings in sound preferences, pulseaudio sound and alsaplayer. I can occasionally get audio for music with some combination of killing pulseaudio, changing back and forth the sound source in sound preferences and playing then stopping a youtube video in Firefox. I have tried recording a sequence of these actions to find a working pattern, but no sequence of these steps results in returning my audio all the time. When I do have sound in rhythmbox, if I leave it running it keeps playing, but even stopping a song and immediately changing to another one kills the audio. My audio output from inxi is as follows:
> Audio:     Card-1 Advanced Micro Devices [AMD/ATI] Tonga HDMI Audio [Radeon R9 285/380]
           driver: snd_hda_intel bus-ID: 01:00.1
           Card-2 Intel Sunrise Point-H HD Audio
           driver: snd_hda_intel bus-ID: 00:1f.3
           Sound: Advanced Linux Sound Architecture v: k4.10.0-40-generic

If also discovered that if I plug in a usb sound card and then speakers into it, audio is 100% reliable from all of the apps I mentioned above. My suspicion is that there is some negative interaction between alsa and pulseaudio, but removing pulseaudio altogether isn't an option, as it removes the Ubuntu desktop. Ideas?

---

### Post by Yellow Pasque on 2017-12-02
Try resetting the user's pulse configuration so a fresh one gets generated:
```
rm -r ~/.config/pulse; pulseaudio -k
```
If that doesn't help, give more info: [https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)

---

### Post by mfox on 2017-12-08
Thanks, Temujin. I did try the reset before, both with the command line and by deleting the files by hand. Sometimes this worked, but most of the time it didn't. This is what has been so frustrating about my sound problem - some things work but nothing consistently. Which probably means a problem under the hood that isn't transparent. I will read over the Alsainfo Wiki file to see if there is something there I can try and if anyone has other ideas, please fire away!

---

### Post by Yellow Pasque on 2017-12-08
> **mfox said:**
> I will read over the Alsainfo Wiki file to see if there is something there I can try

There's nothing to try regarding alsa info. You take 30 seconds and run the two commands, give the link to your info, and then maybe I or someone else will have a suggestion for you to try.

---

### Post by Yellow Pasque on 2017-12-08
Come to think of it, I do have a suggestion, and that is to disable your GPU's HDMI audio device if you're not using it.

```
echo "options snd-hda-intel enable=0,1" | sudo tee -a /etc/modprobe.d/disablehdmiaudio.conf
```

If that works correctly, (aplay shows only your motherboard's audio), then try resetting pulseaudio again to make it "forget" about the HDMI device.

---

### Post by mfox on 2017-12-11
Unfortunately, Temujin, implementing the code you suggested above didn't bring back sound to rhythmbox, even after resetting my pulse config. So I carried out your other suggestion to provide more information. The output is [here]("http://www.alsa-project.org/db/?f=335c6e5d4441ed224a8a6e39073b6502dcb98370").

---

### Post by Yellow Pasque on 2017-12-11
I don't see anything alarming/unusual in the info, though I don't claim to be an expert. I don't know what I'd do next. Maybe try to get a pulseaudio log of what happens when the sound plays in Rhythmbox and then goes out. [https://wiki.ubuntu.com/PulseAudio/Log](https://wiki.ubuntu.com/PulseAudio/Log)

You can delete the file you created. For some reason, it didn't disable the HDMI audio anyway:
```
sudo rm /etc/modprobe.d/disablehdmiaudio.conf
```

---

### Post by anontrust on 2017-12-19
if you use firejail could be a related issue

---

