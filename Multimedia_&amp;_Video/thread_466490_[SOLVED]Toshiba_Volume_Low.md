---
title: "[SOLVED]:Toshiba Volume Low"
date: 2007-06-06
forum: Multimedia &amp; Video
---

### Post by prince_niceguy on 2007-06-06
I broke my head over this the whole day... just thought would post it here for reference.

I have toshiba portege M500 with Intel HDA with following sound devices

###############################################
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: AD198x Analog [AD198x Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 6: Si3054 Modem [Si3054 Modem]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
###############################################

Today the sound become very low... I was barely able to hear anything... I tried out putting snd_hda_intel model=stack3 in the /etc/modprobe.d/alsa-base to no avail...

Then I logged into windows and increased the sound level to maximum... It was almost near mute in windows. Then I logged back into ubuntu and it worked and it was giving the same loud sound now...

Hope this helps some one... :)

---

### Post by wolfen69 on 2007-06-06
what does the volume level in windows have to do with linux? 2 different things.
to the noobs: any hardware settings in windows has absolutely no effect on your linux install.

---

### Post by prince_niceguy on 2007-08-30
Well what you say is true... but in this case Alsa seem not to set some hardware volume correctly on Toshiba... might be a bug. But there is a work around by going into windows and increasing the volume there as windows seem to have the correct driver installed which knows which hardware switch to use...

---

### Post by indieboy445 on 2007-08-31
I've had the same issue (Toshiba laptop as well). My work around is to make sure that the hardware volume dial is turned down when I boot up Ubuntu. Alsa must be doing some sort of hardware check which has gone buggy.

---

### Post by jasbur on 2007-10-13
I can't beleive it. That actually worked! My levels were already at 100% in Vista so I just lowered them to 0% then back up to 100%. Bow everything is working great in my Gutsy install. Thanks.

---

