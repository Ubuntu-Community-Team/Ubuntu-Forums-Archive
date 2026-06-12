---
title: "pulse audio and ice1712 trouble with 9.10"
date: 2009-11-28
forum: Multimedia Software
---

### Post by Reeman on 2009-11-28
If anyone can suggest a pulse audio solution to the M-audio 24/96 configuration please fire away. When I try any of the latest distros Ubuntu 9.10, Fedora 12, or even OpenSuse latest gnome/pulse offerings the HW functions do not show up in pulse. Anybody else experiencing these problems with the M-audio 24/96 audiophile card. It was the most reliable and best supported bit of high end hardware at one time! 

The only options available are digital i/os in the mixer settings. However I can use apps that can access alsa directly like audacity but the desktop sound server and all the related apps are borked because pulse is not seeing the adc outs on the card! So the problem lies in the pulse server not in alsa. 

Mint linux 7.10 64 does still work with the pulse server but newer releases that use the current pulse default installs are all borked.

---

### Post by RaumTrug on 2009-11-28
got one of those cards, too, and got the analogue outputs running!

look here: [https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/178442/comments/63](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/178442/comments/63)

you basically create both files and put them where stated in that post! I've had to do a reboot before it worked.

afterwards you can select "analogue output" from the pulse device chooser, and all apps able to use pulse output on the rca jacks again! you might have to "reset" some of the apps somehow, for example I had to turn audio off and on again to make ogg video/sound files playback in firefox, but most apps work for me with this fix, though for some I have to turn off pulse to let them hog the alsa driver directly in order to get "good" sound.

I'm not sure about the digital out surround options that were there before, after this fix they were gone, but I don't use them anyways!

good luck

---

