---
title: "sound using OSSTEST only"
date: 2011-10-11
forum: Multimedia Software
---

### Post by yndesai on 2011-10-11
I have realtek sound card which was not producing any sound using out of box installation of ubuntu.

I tried the OSS open sound system. It installed with some warning. However now what is happening that when I do osstest the sound is played which I can hear however I am not able to play the music yet.

Is there a way to link the existing installation of VLC player to OSS.

thanks

yndesai

---

### Post by yndesai on 2011-10-11
I checked the oss wiki at [http://www.4front-tech.com/wiki/index.php/Configuring_Applications_for_OSSv4#vlc]("http://www.4front-tech.com/wiki/index.php/Configuring_Applications_for_OSSv4#vlc") tried few things and could start the sound.

my osstest result showed
that the /dev/oss/hdaudio/pcm0 was producing sound.

Hence in the 
vlc > tools > preference > audio  
I selected "UNIX OSS audio output" and 
Device I have written "/dev/oss/hdaudio/pcm0"

---

### Post by yndesai on 2011-10-16
I need to use the 
```
ossmix vmix0-outvol 30.0
``` in terminal to increase volume. Also the volume is lesser than the realtek driver when used on windows.

---

