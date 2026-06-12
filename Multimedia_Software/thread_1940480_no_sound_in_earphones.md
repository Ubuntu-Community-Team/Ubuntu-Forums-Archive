---
title: "no sound in earphones"
date: 2012-03-13
forum: Multimedia Software
---

### Post by i_karpas on 2012-03-13
[SIZE=3]I upgraded to Ubuntu 11.10 in a dual boot with 2 HDD, the first has Win 7, the 2nd Ubuntu OS. I only use earphones and they **work with Win 7** but not with 11.10.
I tried the System Settings>Sound>Hardware -- but 
**no **[/SIZE][SIZE=3]**earphones are displayed**. none of the options:
   Off,...,analog stereo output , etc produce any sound, the volume is turned to Max, but running the test (speakers) give no sound.  I tried alsamixer the earphones are greyed out and show oo at the bottom, also tried the Sound Troubleshooting Procedures  that show the Driver, Library, & Utilities correctly
The soundcard is recognized as HDA Intel. What else can I do?
  I'll appreciate ur help:(
[/SIZE]

---

### Post by i_karpas on 2012-03-20
:popcorn:Problem solved by reporting a bug thru Launch Pad
received the forllowing reply

Try the latest alsa kernel module: [https://code.launchpad.net/~ubuntu-]("https://code.launchpad.net/%7Eubuntu-")
audio-dev/+archive/alsa-daily/

sudo apt-add-repository ppa:ubuntu-audio-dev/alsa-daily
sudo apt-get update
sudo apt-get install alsa-hda-dkms
  then reboot

---

