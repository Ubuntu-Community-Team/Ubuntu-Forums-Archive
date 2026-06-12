---
title: "No audio Toshiba Satellite P100, ubuntu 10.04"
date: 2010-05-09
forum: Multimedia Software
---

### Post by eckorsberg on 2010-05-09
I have a Toshiba Satellite P100-ST9212.  Previously it had Windows XP installed and everything worked.  Yesterday I installed Ubuntu 10.04 and the installation went smoothly (video, wireless, usb, etc) and I did all the suggested updates.  However there is no audio being emitted.  All visual and BIOS indications are that the audio should be enabled and working.  I have version 4.20 of the BIOS

I looked at this forum before submitting this and found general steps to  test for.
The following steps all succeeded 

aplay -l
lspci -v
sudo modprobe snd-hda-intel

The next steps discuss getting fresh ALSA drivers from kernel but this implies that it once worked on a previous Ubuntu install which is not true in my case.  So rather than chasing down this potential wild goose I thought I would post this specific question and see if anyone has seen and better yet knows how to fix this.
This is my first post to this forum and hope I have followed protocol.

---

### Post by eckorsberg on 2010-05-10
I am embarrassed to say how the problem was resolved.  This is my son's laptop and I was not familiar with it, but I just discovered that there is a recessed rotary volume control in front that was turned to off.  The audio was working all the time, I just had the switch off.  Sorry for any distraction this may have caused anyone trying to chase this down :oops:

---

