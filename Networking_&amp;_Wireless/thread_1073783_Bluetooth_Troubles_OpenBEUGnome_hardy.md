---
title: "Bluetooth Troubles OpenBEU/Gnome hardy"
date: 2009-02-18
forum: Networking &amp; Wireless
---

### Post by docPhunk on 2009-02-18
ok ive been fighting to get my phone to transfer files to my comp via bluetooth. im using the blueZ stack in OpenGEU (ubuntu with e17 and gnome) 

blutooth dongle is detected, i am able to see my phone with hcitools scan, and can even send files to my phone using the bluetooth-applet but on after running 'pand <my phone address>', when i try to connect with 'hidd --connect' i get the error "Can't get device information: Success". If i delete the foler /var/lib/bluetooth/<my bluetooth address> and runnn hidd --connect i am prompted for the passcode. when i enter the code i get the same error. now the really weird thing is when i try to connect to my computer from my phone it says its paired and my computer locks up COMPLETLEY and i have to hard reboot...ive never had a linux system hopelessly lock up b4...is there a problem with BlueZ, is it a problem with enlightenment? i dunno, any help would be much appreciated.

---

