---
title: "ati hd 4300 install and totem"
date: 2010-05-09
forum: Multimedia Software
---

### Post by enchesss on 2010-05-09
short:

spent ages getting ati hd4300 installed on lucid lynx

then totem movie player set contrast to zero making video very dark.

now everything is working


to install ati hd4300 on asus p5gz-mx motherboard (known intel agp issues)


1. set to boot using internal video in bios (you can leave card in but make sure (dvi or vga) cable is not plugged in to card).

2. install lucid using live cd and reboot to internal vga

3. DO NOT INSTALL FGLRX DRiVERS as you will be prompted to!!!!

4. update and install video codecs (just try to play a video file using movie player and it will promt you for the codecs to be installed)

5. (*optional also just check that 3d desktop works now too)

6. run:

```
sudo gedit /etc/modprobe.d/blacklist.conf
```

add the following lines to bottom of blacklist.conf

```

blacklist agpgart
blacklist intel_agp

```

7. restart

8. at bios press delete and switch to pci chipset for graphics card, press f10 and reboot. try to remove vga plug carefully from mother board now and place dvi into card.


9. cross yor fingers and hope it all works.


Note: The video may now not look very good and this is because totem sets the contrast to zero for some reason but it is easy to fix. just go to edit>preferences>display and click on reset to defaults.


Good luck and many thanks to the developers for open source ati drivers.

It is fantastic to see that open source drivers are so much better than the proprietary drivers.

---

