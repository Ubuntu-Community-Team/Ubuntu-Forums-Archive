---
title: "no sound"
date: 2007-05-17
forum: Multimedia &amp; Video
---

### Post by dignus on 2007-05-17
Goodmorning gentlemen,

I have my laptop installed with Ubuntu. All looks fine, but.. my speakers dont' give me any sound when playing an mp3 or any other damn thing.

Here's some relevant output:

dignus@hamster:~/Desktop$ lspci | grep Aud
00:14.2 Audio device: ATI Technologies Inc SB450 HDA Audio (rev 01)

dignus@hamster:~/Desktop$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: ALC861VD Analog [ALC861VD Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

All channels are unmuted according to alsamixer & volume control. I've tried a couple of apps to play files with: mplayer, xmms, rhytymbox.. all no luck. I'm not seeing any errors. Any suggestions?

---

### Post by dignus on 2007-05-21
Other users with the same problem, you can find the solution on this page: [https://wiki.ubuntu.com/LaptopTestingTeam/Lenovo3000C200_89224MG](https://wiki.ubuntu.com/LaptopTestingTeam/Lenovo3000C200_89224MG)

Note: reboot after this procedure!

---

### Post by mississippifawn on 2007-06-12
I was having the same problem.  I used the wiki to no avail.  I followed it step-by-step and rebooted, all with no luck.  Any other suggestions?

---

