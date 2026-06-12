---
title: "[SOLVED] ATI Graphics Install HELP HELP HELP"
date: 2007-11-04
forum: Multimedia &amp; Video
---

### Post by JimBuntu on 2007-11-04
I have tried to install an ATI Graphics card and it did not work. Im wondering if its because of Ubuntu not have the correct drivers or if its just something simple like not enough power from power supply. I looked at the card while installed and didnt see the fan moving. The box says 300w recomended and mine is only 200w. Could this be the problem? I installed the card (agp) and hooked it all up. It shows the initial loading screen (grub...) and then shows Ubuntu with a loading bar under it, then it goes to a blue screen saying that x server could not load properly which could be due to it not being set up properly. Then if you click yes to check the output it shows at the bottom "no screen detected". Could it be possible that the card is not working because of lack of power but I'm still seeing the bios and all the other stuff?

please help...

---

### Post by Martje_001 on 2007-11-04
Go to a terminal (once you get the blue screen, press ALT+CTRL+F1) and login. Do "sudo dpkg-reconfigure xserver-xorg" and awnser the questions.

---

