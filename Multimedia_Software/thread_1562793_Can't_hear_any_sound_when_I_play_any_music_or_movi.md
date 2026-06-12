---
title: "Can't hear any sound when I play any music or movie file"
date: 2010-08-28
forum: Multimedia Software
---

### Post by m4enigma on 2010-08-28
Hello All,

I am using Ubuntu 10.04 and I can't hear any sound when I play any movie file. I have all the latest codecs installed. I also installed VLC player which plays video but doesn't play audio.

I checked this thread 
[http://ubuntuforums.org/showthread.php?t=1474822](http://ubuntuforums.org/showthread.php?t=1474822)

and I don't have my output sound as mute.

System :

Sony Vaio Laptop E Series VPCEB14EN.

---

### Post by sharathcshekhar on 2010-08-28
1. What is the Video format you are trying to play?
2. Can you play songs? Mp3 format?
3. Do you get sound when Ubuntu Boots up?

---

### Post by m4enigma on 2010-08-28
No, i don't get any sound. Even when I boot Ubuntu, I get no sound and I can't play .mp3 format also. I can see any format video I want to. I tried all video formats, .avi, .mkv, .mpg, everything plays but no sound.

---

### Post by cchhrriiss121212 on 2010-08-28
Try reading through [this]("http://ubuntuforums.org/showthread.php?t=205449") and post back if you get stuck.

---

### Post by m4enigma on 2010-09-09
This also says the same solution. But my sound is not on mute. I even tried alsamixer but there also, the sound is not on mute. It is set to full volume.

Also, please see the output of aplay -l on my machine :

> $ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC269 Analog [ALC269 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Generic [HD-Audio Generic], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

---

### Post by m4enigma on 2010-09-15
What do i do ?

---

### Post by lidex on 2010-09-17
Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Enter your user password when prompted. Choose the upload option and provide a link for the output.

---

### Post by m4enigma on 2010-09-23
When I run the script, I get the following error :

> Newer version detected: 
To view the ChangeLog, please visit [http://www.alsa-project.org/alsa-info.sh.changelog](http://www.alsa-project.org/alsa-info.sh.changelog)
The original file alsa-info.sh will be overwritten!
If you do not like to proceed, press Ctrl-C now..


---

### Post by m4enigma on 2010-09-23
I am however giving the output of some useful commands of which the script mentioned. Please help me!! :(:(. I really need sound on my machine as I am doing an audio based project.

---

### Post by m4enigma on 2010-09-23
Here is the dmesg output.

---

### Post by lkjoel on 2010-09-24
> **m4enigma said:**
> Hello All,

I am using Ubuntu 10.04 and I can't hear any sound when I play any movie file. I have all the latest codecs installed. I also installed VLC player which plays video but doesn't play audio.

I checked this thread 
[http://ubuntuforums.org/showthread.php?t=1474822](http://ubuntuforums.org/showthread.php?t=1474822)

and I don't have my output sound as mute.

System :

Sony Vaio Laptop E Series VPCEB14EN.
Try Fix your sound! in my signature.
Then use Post-Fix your sound! in my signature.

---

### Post by lidex on 2010-09-24
Try running this command in a terminal for 10.04 or later:
```
ubuntu-bug audio
```
Reference the Ubuntu-Bug Audio link in my sig.

---

### Post by m4enigma on 2010-09-26
I installed the pre-release of Ubuntu 10.10. No sound problems now finally :).

---

