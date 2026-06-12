---
title: "Audio through HDMI on MSI K9N2GM?"
date: 2009-03-14
forum: Multimedia Software
---

### Post by daveisfera on 2009-03-14
I'm trying to get the audio working through the HDMI connection on a MSI K9N2GM motherboard (it has a Realtek ALC888 sound card). I've tried following the instructions at http://www.mythtv.org/wiki/AllensDigitalAudioHowto , http://www.mythtv.org/wiki/Configuring_Digital_Sound#Setting_up_ALSA.27s_.asoundrc.2C_Properly , http://www.alsa-project.org/main/index.php/Matrix:Module-hda-intel (they appear to be out of date), and even http://www.goingson.be/2008/12/ubuntu-and-hdmi-audio-output.html , but none of it has worked.

I also tried installing the driver from Realtek ( http://www.realtek.com.tw/Downloads/downloadsView.aspx?Langid=1&PNid=14&PFid=24&Level=4&Conn=3&DownTypeID=3&GetDown=false ), but that didn't do the trick either.

Does anyone have any suggestions on how I can get this working?

Thanks,
Dave

---

### Post by daveisfera on 2009-03-20
I did a fresh install of Mythbuntu 8.10, updated, and then installed the Realtek High Definition Audio Codecs. The device shows up when I run "aplay -l":

```
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: ALC888 Analog [ALC888 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: ALC888 Digital [ALC888 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 3: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

But when I run "speaker-test -c 2 -Dplughw:0,3", I don't hear anything.


I also tried updating to the 180 Nvidia proprietary drivers in the repo, but it didn't help. Any suggestions?


Just for documentation purposes, I had to add the following packages to get the Realtek install script to work:

```
sudo apt-get install build-essential linux-headers-generic libncurses5-dev xmlto
```

And I had to add the following two lines on line 60 of the install script (between configure and make):

```
touch alsaconf/po/t-ja.gmo
touch alsaconf/po/t-ru.gmo
```

---

### Post by markbuntu on 2009-03-20
HDMI is controlled by the gpu driver, nvidia in your case. Many people are having this problem with the nvidia driver. It seems to depend a lot on which gpu you have, some work but many do not.

---

### Post by daveisfera on 2009-03-20
> **markbuntu said:**
> HDMI is controlled by the gpu driver, nvidia in your case. Many people are having this problem with the nvidia driver. It seems to depend a lot on which gpu you have, some work but many do not.

So does that mean that I should just give up and switch to Windows? I know that it's not the most appealing option, but I just want things to work.

---

### Post by daveisfera on 2009-03-20
I just installed mythbuntu 8.10 and I'm trying to get the audio working through the HDMI connection on a MSI K9N2GM motherboard (it has a Realtek ALC888 sound card). I've tried following the instructions at [http://www.mythtv.org/wiki/AllensDigitalAudioHowto](http://www.mythtv.org/wiki/AllensDigitalAudioHowto), [http://www.mythtv.org/wiki/Configuring_Digital_Sound#Setting_up_ALSA.27s_.asoundrc.2C_Properly](http://www.mythtv.org/wiki/Configuring_Digital_Sound#Setting_up_ALSA.27s_.asoundrc.2C_Properly) , [http://www.alsa-project.org/main/index.php/Matrix:Module-hda-intel](http://www.alsa-project.org/main/index.php/Matrix:Module-hda-intel) (this one appears to be out of date), and even [http://www.goingson.be/2008/12/ubuntu-and-hdmi-audio-output.html](http://www.goingson.be/2008/12/ubuntu-and-hdmi-audio-output.html), but none of it has worked.

I also tried installing the driver from Realtek ([http://www.realtek.com.tw/Downloads/downloadsView.aspx?Langid=1&PNid=14&PFid=24&Level=4&Conn=3&DownTypeID=3&GetDown=false](http://www.realtek.com.tw/Downloads/downloadsView.aspx?Langid=1&PNid=14&PFid=24&Level=4&Conn=3&DownTypeID=3&GetDown=false)), but that didn't do the trick either.

NOTE: Just for documentation purposes, I had to add the following packages to get the Realtek install script to work:

```
sudo apt-get install build-essential linux-headers-generic libncurses5-dev xmlto
```

And I had to add the following two lines on line 60 of the install script (between configure and make):

```
touch alsaconf/po/t-ja.gmo
touch alsaconf/po/t-ru.gmo
```


The device shows up when I run "aplay -l":

```
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: ALC888 Analog [ALC888 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: ALC888 Digital [ALC888 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 3: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

But when I run "speaker-test -c 2 -Dplughw:0,3", I don't hear anything.


I also tried updating to the 180 Nvidia proprietary drivers in the repo, but it didn't fix the problem.

Any suggestions?

Thanks,
Dave

---

### Post by markbuntu on 2009-03-20
Well no, no need to do that yet. There are a bunch of threads here in this forum and elsewhere about the nvidia driver and using it, it is not too complicated. You should do a search. Try the forum search function here first and google next.

---

### Post by daveisfera on 2009-03-20
I have tried basically everything that I've been able to find, but none of it has seemed to work. Any suggestions?

---

### Post by daveisfera on 2009-03-21
I stumbled along [this post with the same motherboard](http://www.goingson.be/2008/12/ubuntu-and-hdmi-audio-output.html) and I was finally able to get sounds work over HDMI, but there's always static when I play anything. Any ideas on how I can fix that?

---

### Post by daveisfera on 2009-03-21
I stumbled along [this post with the same motherboard](http://www.goingson.be/2008/12/ubuntu-and-hdmi-audio-output.html) and I was finally able to get sounds work over HDMI, but there's always static when I play anything. Any ideas on how I can fix that?

---

### Post by daveisfera on 2009-03-30
So it turns out that I just had a data problem that was causing the static, and now the audio plays fine. Also, the audio works out of the box with Jaunty (once I unmute the HDMI device in alsamixer), so that's a huge plus.

---

### Post by daveisfera on 2009-03-30
So it turns out that I just had a data problem that was causing the static, and now the audio plays fine. Also, the audio works out of the box with Jaunty, so that's a huge plus.

---

### Post by orduek on 2009-05-14
So, Upgrading to Jaunty solved your problem?

---

### Post by daveisfera on 2009-05-14
> **orduek said:**
> So, Upgrading to Jaunty solved your problem?

I was able to get audio through the HDMI cable in Intrepid by upgrading to the newest version of ALSA using [this script](http://ubuntuforums.org/showthread.php?p=6589810#post6589810), but Jaunty came with a new enough version of ALSA so that this was not an issue and the HDMI audio worked out of the box.

However, in both instances, the HDMI audio device is muted by default and needs to be unmuted using alsamixer (it's at the end of the list). I muted the device named "IEC958" and unmuted "IEC958 1" and then it worked just fine. I submited a [bug report](https://bugs.launchpad.net/mythbuntu/+bug/354281) about this, but it was rejected as a "configuration issue" which seemed kind of lame to me.

---

