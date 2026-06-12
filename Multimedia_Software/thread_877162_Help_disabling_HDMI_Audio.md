---
title: "Help disabling HDMI Audio"
date: 2008-08-01
forum: Multimedia Software
---

### Post by kramthegram on 2008-08-01
I have an ATI card with an HDMI port, I also have two delta1010 cards for audio capture and playback. I have an asoundrc card making them one virtual device. The problem is that the HDMI seems to randomly either be assigned to HW:0 or HW:2. Since I use an asoundrc file to bridge my cards that means that if the HDMI switched when I reboot I have to go back in and change the card number from 0,1 to 1,2 and back every time. This is getting really annoying, I would like to either set the ATI HDMI to one of the two permanently or disable the audio altogether, and suggestions?

---

### Post by Standy on 2008-10-04
Same here... little different problem, but i'd like to disable the HDMI sound card... since i've read it's useless anyways... 

actually.. it's gotten so anoying that i've had to install windows.. just to keep it going....

'sukk'...

halp!

---

### Post by markbuntu on 2008-10-04
This is how I got my HDMI sound to be consistently listed as last. Edit /etc/modprode.d/alsa-base and put this at the end. 

options snd_hda_intel index=3

The problem is that pci devices are not assigned the same irqs and so, device numbers on every boot. You should really set up your 1010 cards as index=0 and index=1 anyway. There are directions for fixing all that here:

[http://ubuntuforums.org/showthread.php?t=922860](http://ubuntuforums.org/showthread.php?t=922860)

You can ignore all the PA stuff since you are probably using jack exclusively.

---

