---
title: "[SOLVED] Audio via HDMI"
date: 2008-12-06
forum: Mythbuntu
---

### Post by patrick0605 on 2008-12-06
I've done a search for this, tried a few things here and there but I still can't get it to work.

I've got a Foxconn mobo that uses the ATI 3200HD video card w/ built in HDMI.  When I run aplay -l the HDMI shows up as an audio output, but I cannot get it to work.  Is there something in the mythbuntu settings that I need to change for it to work, or is audio over HDMI not supported just yet?

Thanks for your help,

Patrick

---

### Post by jape42 on 2008-12-06
It depends on the video driver you are using.  I had problems with HDMI audio (muting) using the catalyst drivers:

[http://www.gossamer-threads.com/lists/mythtv/users/353433](http://www.gossamer-threads.com/lists/mythtv/users/353433)

The radeonHD driver works great with HDMI audio for me, but I don't have accelerated video with the radeon HD driver.

regards

jp

---

### Post by patrick0605 on 2008-12-06
I followed the "How-Tos" over on MediaBoxblog on audio over HDMI on the 780 chipset mobo, and installing radeonhd audio support.

Now, I have other problems, yay.  The menus in mythbuntu do not display, but if I keep hitting the right arrow key on my keyboard it will pull up the sub-menu (IE: watch recordings, that displays fine), but still no audio, though I'm assuming I have to change the setting in MCC, but I can't see what I'm doing!!  Also, now, playback of my recordings is very slow, and jittery.  

I did manage to test the audio output via the sound-properties, and the tests were successful, I had sound, but now I'm left with a pretty much unusable mythfrontend and jittery video playback.

---

### Post by patrick0605 on 2008-12-07
Ok after a bit of tinkering, a simple log off then back in fixed the menus not showing up, not sure why restarting the computer didn't fix that, but oh well that's resolved.

Still having an issue w/ audio, however.  I messed around with the settings a bit, but still cannot get sound to play in mythbuntu, nor the rest of the system.  I tried watching a video on youtube, and there isn't any sound.

Also still having jittery playback of recordings.  JP, you mentioned that you don't have accelerated video with the radeonhd drivers, is this similar to what you are experiencing?  I'm trying to watch HD recordings, would SD shows still suffer from this problem?

---

### Post by jape42 on 2008-12-07
> **patrick0605 said:**
> Ok after a bit of tinkering, a simple log off then back in fixed the menus not showing up, not sure why restarting the computer didn't fix that, but oh well that's resolved.

Still having an issue w/ audio, however.  I messed around with the settings a bit, but still cannot get sound to play in mythbuntu, nor the rest of the system.  I tried watching a video on youtube, and there isn't any sound.


Right.  If memory serves you will need to configure the HDMI device as the default.  In mythTV I have audio set to ALSA:default, and have alsa sound config files that force the default to be the HDMI sound device ( which is the second device (card 1) for me).  I'll attach the files in case they are useful to you:
```

jape@vcr3:~$ pwd
/home/jape
jape@vcr3:~$ find . | grep asound
./.asoundrc
./.asoundrc.asoundconf
jape@vcr3:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: ALC882 Analog [ALC882 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 1: ALC882 Digital [ALC882 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 0/1
  Subdevice #0: subdevice #0


```
       
> 
Also still having jittery playback of recordings.  JP, you mentioned that you don't have accelerated video with the radeonhd drivers, is this similar to what you are experiencing?  I'm trying to watch HD recordings, would SD shows still suffer from this problem?

My AMD X2 5200 is not able to play video at 1920x1080 (though my mythtv GUI seems OK at this res). Without acceleration your CPU must do the video scaling (and I seem to remember that it wasn't able to take advantage of multiple cores...).  What I've done is set a low res playback mode for recordings in myth ( ie 640x480).  Since I'm mostly watching SD, this is OK for me, though there is a few seconds of blank screen on playback as the resolution changes.  I'm hoping that the radeon HD driver will get acceleration for the HD3200 at some point, but there's no ETA on this since the docs have not yet been released by AMD.

regards,

jp

---

### Post by patrick0605 on 2008-12-08
Thanks for getting me started in the right direction.  

I have, what I believe the onboard soundcard (not the HDMI part) turned off in my BIOS.  So when I run the aplay command I get this:

```
phulton@MythBox:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
phulton@MythBox:~$ 

```

Which is a bit different than what you have.  Should I turn it back on? 

Anyway, when I try to edit the system files you attached, I'm unable to save them.  I'm sure I need to access them from the terminal with a sudo command, but I'm really new to this so I'm not all that familiar with this process.  

Thanks,

Patrick

---

### Post by jape42 on 2008-12-08
> **patrick0605 said:**
> Thanks for getting me started in the right direction.  

I have, what I believe the onboard soundcard (not the HDMI part) turned off in my BIOS.  So when I run the aplay command I get this:

```
phulton@MythBox:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
phulton@MythBox:~$ 

```

Which is a bit different than what you have.  Should I turn it back on? 


I don't think turning your onboard sound card back on would make things work, but if you did, then you may not need to manually edit the files I attached, because I'd guess your setup would be similar to mine.

> 
Anyway, when I try to edit the system files you attached, I'm unable to save them.  I'm sure I need to access them from the terminal with a sudo command, but I'm really new to this so I'm not all that familiar with this process.  

Thanks,

Patrick
Unfortunately I don't know if there are GUI tools that will help you setup your sound devices.  Note that the files I attached go in your home directory, so you shouldn't need sudo access.  In my case my home directory is the same as my mythtv user.

regards,

jp

---

### Post by patrick0605 on 2008-12-09
Well sir, I thank you for all of your help, I have audio!!!

Now, if I could get rid of this jittery playback issue ;)

---

