---
title: "Can't use PCI sound card over integrated"
date: 2008-02-05
forum: Multimedia &amp; Video
---

### Post by SBFC on 2008-02-05
Hello everyone.

I'm having issues with my PCI soundcard versus my mobo integrated sound card. 

I have a Phillips PCI sound card installed, shows up as 'CMI8738MC6 [C-Media PCI CMI8738-MC6], device 0: CMI8738-MC6 [C-Media PCI DAC/ADC]' with 'aplay -li'. My mobo is an Asus M2A-VM HDMI with integrated sound, 'SB [HDA ATI SB], device 1: ALC883 Digital [ALC883 Digital]'.

I know the Phillips card works with Alsa as I've used before in one of my older Xubuntu systems. However, I can't seem to get my system to use it over the integrated card. I know the Phillips card is working as I can test the mic out in the mixer...but I can't get any audio to go through from any apps. It all goes through the integrated sound.

Any help would be greatly appreciated.

---

### Post by Existentialist on 2008-02-06
If you don't use the on board sound you can always try turning it off.  In the advanced section of BIOS there is an on board device configuration section that lets you turn it off.

I'm sure somebody has a better solution that can fix this from within ubuntu but you mine as well try it as there is no reason to leave on board audio on if you aren't using it.

---

### Post by SBFC on 2008-02-06
Thanks for the suggestion...finally works.

---

### Post by cor2y on 2008-02-06
see this post on selecting a default soundcard when you have more than one, WITHOUT having to visit the mobo bios to turn off onboard audio.

[http://ubuntuforums.org/showthread.php?t=650026](http://ubuntuforums.org/showthread.php?t=650026)

---

