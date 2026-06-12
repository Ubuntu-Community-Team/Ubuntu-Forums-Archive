---
title: "Audio playback without Sound"
date: 2009-02-01
forum: Multimedia Software
---

### Post by ohgodnotanother1 on 2009-02-01
Dear (X)Ubuntu users,

I have installed Xubuntu 8.10 and my sound card seems to be detected correctly. The card is reported as C-Media 8738 - see below. It's a Terratec Aureon 5.1 PCI card, but I've been told that the chip matters only.

This is the output of "aplay -l" copied from a terminal.
```

**** List of PLAYBACK Hardware Devices ****
card 0: CMI8738 [C-Media CMI8738], device 0: CMI8738-MC6 [C-Media PCI DAC/ADC]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CMI8738 [C-Media CMI8738], device 1: CMI8738-MC6 [C-Media PCI 2nd DAC]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CMI8738 [C-Media CMI8738], device 2: CMI8738-MC6 [C-Media PCI IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: CMI8738_1 [C-Media CMI8738], device 0: CMI8738-MC6 [C-Media PCI DAC/ADC]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: CMI8738_1 [C-Media CMI8738], device 1: CMI8738-MC6 [C-Media PCI 2nd DAC]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: CMI8738_1 [C-Media CMI8738], device 2: CMI8738-MC6 [C-Media PCI IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

This is the output of lspci|grep audio:
```

02:03.0 Multimedia audio controller: C-Media Electronics Inc CM8738 (rev 10)
02:0b.0 Multimedia audio controller: C-Media Electronics Inc CM8738 (rev 10)

```

I tried to play an MP3 file with audacious and the equalizer visualization bars are moving correctly, however I don't hear a single sound.

I tried VLC for the same purpose and I don't get any sound there either.

I have installed the restricted modules and set the "Device" to "default" and the "Wannabe Master" to "Master,0" in the xfce4-mixer (which is like the gnome audio controller applet). I have also tried and combination without success.

The volume is > 0, I have checked that too.

The audio file is clearly playing in the player, but I don't get any sound at all. Why??

Kind thanks for any help in advance!

---

### Post by Paqman on 2009-02-06
I wouldn't really know where to go with this, except to comment that this sound card works out of the box on 8.10 Gnome. All I had to do was disable my onboard sound and the Aureon worked after the next boot.

---

### Post by ohgodnotanother1 on 2009-02-09
Thanks Paqman!

I disabled the on-board audio chip in the BIOS and next time I booted the system I heard all sounds properly.:D

---

