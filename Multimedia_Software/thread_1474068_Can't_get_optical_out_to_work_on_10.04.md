---
title: "Can't get optical out to work on 10.04"
date: 2010-05-05
forum: Multimedia Software
---

### Post by Viper187 on 2010-05-05
My sound card is an HT Omega Striker, and it worked fine with 9.04. I did a fresh install of 10.04 and I can't get optical/SPDIF/IEC958/whatever to work. I only use the optical out (mostly with Rythmbox, if that matters). I know I had to enable IEC958(?) on 9.04 to get it working, but that didn't work this time around. The sound card is found fine, so this is really pissing me off.

card 0: CMI8762 [C-Media CMI8762], device 0: CMI8738-MC8 [C-Media PCI DAC/ADC]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CMI8762 [C-Media CMI8762], device 1: CMI8738-MC8 [C-Media PCI 2nd DAC]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CMI8762 [C-Media CMI8762], device 2: CMI8738-MC8 [C-Media PCI IEC958]
  Subdevices: 0/1
  Subdevice #0: subdevice #0

---

### Post by xzero1 on 2010-05-05
Did you enable spdif output in alsamixer? In a terminal type 'alsamixer', use the arrow keys to select S/PDIF output, enable/disable with the 'm' key. Don't depend on sound preferences to work correctly.

---

### Post by Viper187 on 2010-05-05
Thanks. That did it. Sucks you can't rely on the GUI.

---

