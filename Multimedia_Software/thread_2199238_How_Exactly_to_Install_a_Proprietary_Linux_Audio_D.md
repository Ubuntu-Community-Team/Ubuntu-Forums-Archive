---
title: "How Exactly to Install a Proprietary Linux Audio Driver (tar.bz2)"
date: 2014-01-12
forum: Multimedia Software
---

### Post by bettyhills on 2014-01-12
I've installed Ubuntu 12.04.3 on an old PC with 1GB ram, 160GB HDD.  All is well except no sound.  I downloaded a Linux audio driver package for my Avance '97 Realtek sound system as a tar.bz2 file.  Instructions say for automatic install:  Execute  ./install

I do not know how to execute that command (terminal?), in what directory to type in that command, or in what directory I should place the tar.bz2 file in order for it to be found later by the sound system.  (I already attempted the command while in the download directory -  unsuccessfully.  And I've searched hard for the answer online, but came up dry.)

Can anyone tell me exactly where to place the compressed file before extracting it so that the drivers end up where they should be when done, and the exact way to issue the command correctly?  Thanks in advance.











































downloaded a Linux driver package for my Avance '97 Realtek speakersound system online

---

### Post by Bucky Ball on 2014-01-12
Why do you think you need a driver? Do you have Pulseaudio Volume Control in Apps>Multimedia? If so, have a look in there and see if your card is identified in any of the drop down boxes (in input or output tab). Open a terminal and run this command:

```
sudo lshw -C sound
```

See your card there? Please post the output for it here. ;)

---

### Post by bettyhills on 2014-01-12
Thanks for the reply. 

In my install of PP 12.04.3, there is no Pulseaudio Volume Control in Apps>Multimedia.  Rhythmbox Music Player is the only sound-related app.  I did enter the command in Terminal and received the response:  "Sorry, there is nothing that matches your search."

---

### Post by Bucky Ball on 2014-01-13
*Thread moved to **Multimedia & Video**.*

Should have moved it the first time. ;)

Ok, try typing 'alsamixer' in a terminal and see if that is identifying your card. Hit F6 and that should bring up a list of sound cards. Is yours identified correctly? Can you see anything muted in alsamixer? Use arrow keys to move around and turn slider up or down and 'm' to unmute/mute.

For a more graphical view of things, you can install gnome-alsamixer and/or pavucontrol (Pulseaudio Volume Control). Both will be available in Apps>Sound & Video (or Multimedia?) and both launch to a GUI.

---

### Post by Yellow Pasque on 2014-01-13
The best way to install a proprietary audio driver in Linux is usually not to install it at all..
Please give link to to the driver you're trying.
Also, give info: [https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)

---

### Post by bettyhills on 2014-01-13
The card is a VIA 8233A, chip Realtek ALC650D.  Your instructions worked perfectly.  All sliders moved to the top and the sound is loud and clear set at Play Sound Through "LFE on Separate Mono Output" and Mode "Analog Stereo Output" in System Settings, Sound.  Thank you, BB, for the teaching moment.  I've written it all down to use on the next 5 Ubuntu installs ahead of me.

---

### Post by Bucky Ball on 2014-01-13
Great news! Please mark thread as solved from the instructions in my signature.

It is fairly rare to require the manual installation of an audio driver in Linux (at least for a regular domestic soundcard). Are the next five installs to the same configuration of hardware? If so, at least this bit should work. Good luck with it. ;)

---

