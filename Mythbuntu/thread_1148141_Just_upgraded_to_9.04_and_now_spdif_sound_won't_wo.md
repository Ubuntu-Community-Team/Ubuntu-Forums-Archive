---
title: "Just upgraded to 9.04 and now spdif sound won't work (mythtv only)"
date: 2009-05-04
forum: Mythbuntu
---

### Post by Lido on 2009-05-04
I'm using 9.04 with mythtv. I upgraded from 8.10 which was working with digital sound, and now the sound is only this crackling noise. I've tried a few different settings in the setup, but the best I can get is a crackling sound out of the speakers. Video files play fine with sound using Mythvideo ("Internal" player is selected in setup for video files), but live tv and recordings have the crackling sound only. I've got both spdif and hdmi plugged into my receiver. When I test the sound using the sound control panel, I get the tone fine and when the desktop loads I get the welcome sound. It's apparently just Mythtv's live tv and recorded shows that can't play sound.

Settings:

Alsa: Default
passthrough: Default
enable ac3 and dts passthrough: checked
upmix passive
other two options not checked.

I tried max channels both 5.1 and stereo, but that doesn't change anything.

---

### Post by phroman on 2009-05-04
Hi Lido, I had a similar problem, here were my fixes.  I added the following line of code to the end of this file:  /etc/modprobe.d/alsa-base.conf:

```
options snd-hda-intel model=6stack-dig
```


The digital output for the SPIDf is probably muted in the driver.  The SPDIF is called iec958, and you just have to un-mute it.  This link helped me fix that.

[http://alsa.opensrc.org/index.php/DigitalOut]("http://alsa.opensrc.org/index.php/DigitalOut") 

But beware, when I run alsamixer, I could un-mute the ice958 check box but was never able to select it to show PCM OUT.  It didn't matter for me though.  There are a couple of posts I would read through if you want to learn more.

[http://ubuntuforums.org/showthread.php?t=1100747]("http://ubuntuforums.org/showthread.php?t=1100747")

[http://ubuntuforums.org/showthread.php?t=1140776]("http://ubuntuforums.org/showthread.php?t=1140776")

I would try the above 2 things first, however you may have to change the settings in mythtv to this:

Alsa: ALSA:SPDIF   OR  ALSA:iec958 

Post back with anymore questions, good luck.

---

### Post by Lido on 2009-05-04
Thanks. Actually I had sound in everything except live tv and recordings in Myth. The way I finally fixed it was to disable AC3 passthrough, but keep DTS passthrough enabled. Hopefully that will work on every recording from now on but it worked on two or three that I tried so I think this problem is solved.

---

