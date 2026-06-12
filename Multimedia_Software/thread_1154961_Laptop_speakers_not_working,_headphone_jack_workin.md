---
title: "Laptop speakers not working, headphone jack working"
date: 2009-05-10
forum: Multimedia Software
---

### Post by manolid on 2009-05-10
I've recently installed 9.04 on my Acer 3050. While the headphone jack is working, the laptop speakers are not.

According to [THIS]("https://help.ubuntu.com/community/SoundTroubleshooting") troubleshooting guide, my soundcard is recognized by Ubuntu but the module is not installed. As per the guide, I use the following command to install the module:

sudo aptitude install linux-ubuntu-modules-`uname -r` linux-generic

After running the above command, the following message is displayed in the terminal window... "Couldn't find any package whose name or description matched "linux-ubuntu-modules-2.6.28-11-generic". 

Using the guide stickied to the top of this forum, I'm only able to get to step 4, where I enter the following command: 

sudo modprobe snd-

After running the above command, "FATAL: Module snd_ not found" is displayed.

I'm new to Ubuntu and really have no idea on how to go about solving this problem. Any help with fixing this problem will be appreciated.

---

### Post by Sealbhach on 2009-05-10
Hi, I've seen this recommended in other threads. Give it a try, you can always indo it afterwards if it doesn't work in 9.04.

```
sudo gedit /etc/modprobe.d/alsa-base
```add these two lines at the end of the file:

```
alias snd-card-0 snd-hda-intel
options snd-hda-intel index=0 probe_mask=3 position_fix=3
```

reboot.

[http://www.backports.ubuntuforums.org/showthread.php?t=459938](http://www.backports.ubuntuforums.org/showthread.php?t=459938)

.

---

### Post by manolid on 2009-05-10
Editing the alsa-base file did not help. However the thread that you linked to mentioned turning off mute for the surround setting, which I did via Gnom Alsa Mixer. My sound is now working.

Thanks for your help

---

### Post by Sealbhach on 2009-05-10
That's good, glad you got it sorted.

.

---

