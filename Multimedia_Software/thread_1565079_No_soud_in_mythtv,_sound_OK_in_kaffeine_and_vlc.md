---
title: "No soud in mythtv, sound OK in kaffeine and vlc"
date: 2010-08-31
forum: Multimedia Software
---

### Post by HD4me2 on 2010-08-31
Have spend a lot of time searching many threads but not seen a solution
Have installed mythtv to kbuntu (32 bit) and configured the backend with HDHomerun and receive video but no sound The ] key brings op the volume bar but sits at 0 and will not adjust.

However caffeine and he HDhomerun conf GUI viewer play the video and sound perfectly.

Strangely, in setting up the backend I never saw an entry for alsa or mixer, it appears somethimg is missing there for HDHomerun, although those are present when I added an entry for a Hauppauge 950Q  USB tuner. Can not get this source to work as yet so have not seen the sound problem there.

The speaker test 
speaker-test -c 2
also works as do the login/logout sounds and the test in system settings/multimedia.

alsa -l reports
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC889A Analog [ALC889A Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC889A Digital [ALC889A Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

Mythtv was installed using apt-get mythtv

---

### Post by HD4me2 on 2010-09-05
After considerable experimentation with the TV setup/General I now have sound.  Had to set Audio out to /dev/dsp and the sound worked, Alsa default fails. Also has to change the mixer parameters since the F9/10/11 keys did not work. Set the mixer device too software and the Mixer controls to Master.  This for a mainboard with Realtek sound chip on board.  1080p video on the Samsung P2370 monitor or the Viewsonic VX2235 1680x1050, ATI 4670 display adapter.

---

