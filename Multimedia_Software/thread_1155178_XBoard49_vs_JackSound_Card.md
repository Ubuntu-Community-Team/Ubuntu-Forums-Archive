---
title: "XBoard49 vs Jack/Sound Card"
date: 2009-05-10
forum: Multimedia Software
---

### Post by billstei on 2009-05-10
I have an E-MU Xboard49 USB MIDI keyboard and if this is turned on while booting into Ubuntu Jaunty, Jack shows this as an audio device (which it's not) at hw:1, which would normally be the address of my second sound card (a PCI512), which I have selected in Jack as the sound card that it uses, and when Jack starts it fails (and the second sound card is nowhere to be found elsewhere in Jack).  If I have the XBoard turned off then my second sound card is assigned hw:1 and Jack starts without any problems, and then if I turn on the XBoard it too works normally (in particular with Wine and a MIDI related program running under Wine).  The workaround is "easy", but I suppose this is a problem somewhere in udev?  I have all the Pulseaudio stuff removed except for libpulse which is depended upon by way too many programs (like kate, ktorrent, kmag?  huh?)

---

### Post by markbuntu on 2009-05-10
MIDI is part of the alsa stack so midi devices are treated as audio devices.

It is a problem with the way pci devices are discovered and assigned which is a semi random process. You can fix index numbers and/or assign alias for the devices in /etc/modprobe.d/alsa-base (alsa-base.conf if you are using jaunty) so they are assigned the same hw position consistently over reboots. This is an alsa issue and has nothing to do with pulse.

You can look in here for more about aliases and indexing audio devices

[http://ubuntuforums.org/showthread.php?t=922860](http://ubuntuforums.org/showthread.php?t=922860)

---

### Post by billstei on 2009-05-11
I see in alsa-base.conf the line:

options snd-usb-audio index=-2

I wonder if the keyboard which is showing up in /proc/asound/modules as index 3 (if I turn it on post-boot):

 0 snd_hda_intel
 1 snd_emu10k1
 2 em28xx_alsa
 3 snd_usb_audio

is then taking index 1 (3 - 2 = 1) and hiding snd_emu10k1 (my second sound card) from Jack (if I turn it on pre-boot)?

---

### Post by markbuntu on 2009-05-11
Did you read the link?
You can just do it like this. Add these lines to the end of alsa-base.conf

options snd_hda_intel index=0
options snd_emu10k1 index=1
options snd_usb_audio index=2
options em28xx_alsa index=3

and they will all have the same hw numbers at every boot and jack will not get confused. All those options....index=2 lines already in alsa-base.conf are just some defaults to prevent those devices from grabbing hw0. You can comment them out if you don't have any of those devices or want to change their index numbers. it is better to add the options you want to use at the end of the file so you can easily see what you did in case you need to make further changes.

---

### Post by billstei on 2009-05-12
I put the following at the end of the alsa-base.conf file (Note this is slightly different than post above):

options snd_hda_intel index=0
options snd_emu10k1 index=1
options em28xx_alsa index=2
options snd_usb_audio index=3

And then with the Xboard turned on pre-boot, I get the following from cat /proc/asound/modules:

 0 snd_hda_intel
 1 snd_usb_audio

I have not removed any of the =-2 lines in alsa-base.conf, but I suppose that is the next logical step.  In any event, using options...index= is not a guarantee of a particular index.

P.S. Probably even more puzzling is the complete disappearance of em28xx_alsa at index 2.

---

### Post by markbuntu on 2009-05-12
That is sort of weird. those things should not have disappeared. You can try using aliases, they seem a little more reliable. One of the links in that post I gave you explains how to do that.

---

### Post by billstei on 2009-05-12
I guess the problem with aliases is that I don't think I can use an alias in qjackctl. (?)

---

### Post by markbuntu on 2009-05-13
The alias thing is just for alsa. You would still use hw in jack.

---

