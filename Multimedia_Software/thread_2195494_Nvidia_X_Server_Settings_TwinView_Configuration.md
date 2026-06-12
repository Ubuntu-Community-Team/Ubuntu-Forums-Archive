---
title: "Nvidia X Server Settings TwinView Configuration"
date: 2013-12-24
forum: Multimedia Software
---

### Post by giulio53napoli on 2013-12-24
Hi there ! 
I have a PC with Ubuntu 12.04 LTS with a Samsung monitor, connected via HDMI to a SONY TV. The graphic card is NVIDIA GeForce 7100. 
Until yesterday everything worked: I configured monitors in TwinView via NVIDIA Server Settings, and I could see the images on the Sony at maximum 1920x1080 resolution. 

But now, after an upgrade, if I run  NVIDIA X Server Settings and go under X Server Display Configuration, under Configuration no longer  TwinView appears . 
Another thing I noticed is that if I change something in the X Server Display Configuration screen and then I press Apply, the dialog closes and the change does not apply. 
Any idea what is wrong ?
TIA

---

### Post by florent-blanvillain on 2014-01-29
The same here for the second part: After the last upgrade, if I change the screen resolution and click apply, the dialog closes and nothing more happens.

Ubuntu 12.04 LTS with and Iiyama PL2475HD.

---

### Post by jp734 on 2014-01-31
Have you guys tried uninstalling then reinstalling the driver.

---

### Post by tabea2 on 2014-02-01
Hey there,
I am experiencing the same problem and am really frustrated. Could somebody maybe give me walkthrough on how to uninstall the nvidia drivers?? :confused:
It is really annoying to not be able to use my second screen, as I am working on my thesis and am a bit under time pressure :(

**Edit:**
Google helped me already with my questions on how to uninstall the nvidia driver, and also on how to install it again
[http://askubuntu.com/questions/206283/how-can-i-uninstall-a-nvidia-driver-completely](http://askubuntu.com/questions/206283/how-can-i-uninstall-a-nvidia-driver-completely)
[http://askubuntu.com/questions/111818/how-to-install-a-nvidia-driver-for-11-10](http://askubuntu.com/questions/111818/how-to-install-a-nvidia-driver-for-11-10)

However, the TwinView still **does not work**! :(

---

### Post by mocha on 2014-02-04
Probably you just need to delete your ~/.nvidia-settings file and then re-run the GUI tool.

---

