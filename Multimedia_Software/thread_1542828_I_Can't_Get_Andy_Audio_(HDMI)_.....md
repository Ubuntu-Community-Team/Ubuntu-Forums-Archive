---
title: "I Can't Get Andy Audio (HDMI) ...."
date: 2010-07-31
forum: Multimedia Software
---

### Post by Xonnie316 on 2010-07-31
Hey guys,

I'm very new to Linux and most especially Ubuntu. I've recently installed Ubuntu and I've been experiencing no audio on my Asus ION mini PC... I use an HDMI cable to connect to my Samsung LCD TV.

I've went to System -> Preferences -> Sound

I've changed it to every sound device:

Analog Stereo Input
Digital Stereo (HDMI) Output
Digital Stereo (HDMI) Output + Analog Stereo Input
Digital Stereo Duplex (IEC958)
Digital Stereo (IEC958) Output + Analog Stereo Input
Analog Stereo Output
Analog Stereo Duplex

And it still won't come out with any audio.

I went to the main audio  turned it to mute and turned it back on. Still won't work...

Any other suggestions of what I can do...

I'm also experiencing Screen Resolution issue with my nVidia ION  : [http://ubuntuforums.org/showthread.php?t=1542825](http://ubuntuforums.org/showthread.php?t=1542825)

Would somebody give me some help please,

I would greatly appreciate your help, because this is really turning me off on staying on Ubuntu as my OS, because I just keep getting one issue after another.

Cheers,

Shaun

---

### Post by lidex on 2010-08-01
Right-click the alsa-info script link in my sig and "save as" to your user folder. Then run this command in a terminal:
```
sudo bash utils_alsa-info.sh
```
Enter your user password when prompted. Choose the upload option and provide a link for the output.

---

