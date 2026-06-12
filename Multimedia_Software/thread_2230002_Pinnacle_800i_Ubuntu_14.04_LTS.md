---
title: "Pinnacle 800i Ubuntu 14.04 LTS"
date: 2014-06-16
forum: Multimedia Software
---

### Post by GuppyGuy on 2014-06-16
Hello, recently I have begun helping an older gentleman set up a Media PC to record digital television.  I purchased two Pinnacle 800i PCI tuner cards, as the PCI-E cards don't usually support analog, and there are a couple analog channels he would still like to receive.  The specs are: AMD A10-6800K, 8GB 1600Mhz RAM, 1TB 7200RPM HDD, and 120GB SSD with a fresh install Ubuntu 14.04 LTS.  My research indicated that I needed to make sure I had both XC5000 firmware, and the latest driver for a CX23880 device.  This link [http://www.linuxtv.org/wiki/index.php/Xceive_XC5000/XC4000#Firmware_Information](http://www.linuxtv.org/wiki/index.php/Xceive_XC5000/XC4000#Firmware_Information) seems to show native firmware support in [COLOR=#000000][FONT=sans-serif]kernels 2.6.24+, thus including Ubuntu 14.04.  So then, I tried following the info for the driver on this page [/FONT][/COLOR][http://www.linuxtv.org/wiki/index.php/Pinnacle_PCTV_HD_Card_(800i)#Drivers](http://www.linuxtv.org/wiki/index.php/Pinnacle_PCTV_HD_Card_(800i)#Drivers), but when running make it warns of the driver being outdated, and provides a link to [http://git.linuxtv.org/media_build.git](http://git.linuxtv.org/media_build.git).  This however I found was most likely not the best driver to install as it was for testing with older kernels only, so I found [http://git.linuxtv.org/media_tree.git](http://git.linuxtv.org/media_tree.git) and followed the directions in the 'about' tab.  However I did not see a make/make install command mentioned and was confused.  I followed the directions anyway, but no devices appear under Tvheadend's browser config.  Strangely, I can receive a signal from a VCR through the coaxial input through the program TvTime.  Any help in getting this card working with Tvheadend would be greatly appreciated.

Thanks,
- GuppyGuy

---

### Post by xc3RnbFO8P on 2014-06-17
Maybe you should ask here:
[https://tvheadend.org/projects/tvheadend/boards/4]("https://tvheadend.org/projects/tvheadend/boards/4")

---

