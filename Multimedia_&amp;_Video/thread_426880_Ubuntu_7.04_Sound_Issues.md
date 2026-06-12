---
title: "Ubuntu 7.04 Sound Issues"
date: 2007-04-28
forum: Multimedia &amp; Video
---

### Post by awells527 on 2007-04-28
It seems that many people are having sound issues.  My sound is sort of half broken.  I have been following the guide at [http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449), and it hasn't helped me much.

aplay -l returns...

```
**** List of PLAYBACK Hardware Devices ****
card 0: CMI8738MC6 [C-Media PCI CMI8738-MC6], device 0: CMI8738-MC6 [C-Media PCI DAC/ADC]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CMI8738MC6 [C-Media PCI CMI8738-MC6], device 1: CMI8738-MC6 [C-Media PCI 2nd DAC]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CMI8738MC6 [C-Media PCI CMI8738-MC6], device 2: CMI8738-MC6 [C-Media PCI IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

...so I know it finds the card.  Sound **does** work for Listen & Gaim, but nothing else including web content & system sounds.

The bug report about the digital output being enabled by default was not the problem because my card doesn't have that.

As I was typing this, I came across something interesting.  I ran "lspci -v" as a normal user and got "Capabilities: <access denied>" in the output.  Curiously, I then ran "sudo lspci -v", and didn't get the "<access denied>".  Then I ran FF as root to see if it helped, and I heard sound with video!

So at this point, I am at a partial solution, it seems to be a permissions problem.  Any assistance would be appreciated.

---

### Post by a_capp18 on 2007-04-28
You have the same sound card I do.
To get mine to work I went to the file .asoundrc in my home directory and commented out the last line. In fact that was the only non comment line so deleting the file should do the same.
If you have not yet tried this give it a go.

---

### Post by awells527 on 2007-04-29
Actually, I just deleted .asoundrc & asoundrc.asoundconf from my home directory, and it works now.

Thanks for your quick & helpful reply.

---

### Post by jvernon on 2007-05-06
I have the same sound card in my PC.  I'm having the same problem I think.  Rythmbox and Exaile have sound, but MPlayer, VLC, and Flash Player do not.


I tried to delete the file .asoundrc like you had success with.  However that file does not exist in my home directory.

---

