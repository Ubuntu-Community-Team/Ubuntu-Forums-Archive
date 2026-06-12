---
title: "[SOLVED] cant get my web cam to work"
date: 2008-10-21
forum: Multimedia Software
---

### Post by cowboyup8606 on 2008-10-21
i just re-installed ubuntu and im using amsn for my instant messaging and my logiteck web cam isnt working  heres what i get when i used the command 
sudo lsusb    can anyone help me plz 




Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 006: ID 046d:08ae Logitech, Inc. 
Bus 001 Device 005: ID 045e:0730 Microsoft Corp. 
Bus 001 Device 004: ID 05e3:1205 Genesys Logic, Inc. Afilias Optical Mouse H3003
Bus 001 Device 001: ID 0000:0000

---

### Post by linuxwizard on 2008-10-21
Try using Ekiga see if the cam works/detected. You may have to work with the settings > Open Ekiga > Edit > Preferences > Video > Video Devices > try changing some of the settings. If your webcam works with Ekiga than you will know their is a issue with amsn or you don't have a setting set right. Alot of Logitech webcams will just work out of the box.

To test your webcam you can do this:
There are 6 icons on the left side of the main Ekiga window. Push the 4th button from the top (a grey round webcam). If eveything is ok, you'll see the output of the webcam. If not, you'll see the Ekiga logo bouncing slowly.

---

### Post by cowboyup8606 on 2008-10-21
i got it to work  ty man

---

