---
title: "uninstalled network manager"
date: 2010-12-08
forum: Networking &amp; Wireless
---

### Post by jr0535 on 2010-12-08
in a stupid effort to try to make my computer connect to the internet i deleted the network manager, thinking that i would be able to reinstall it without internet. so now im trying to figure out how to reinstall it..the internet used run fine before on network manager but one day i couldn't get it to work so i did as i said above.. im on ubuntu 10.04 LTS and use wireless internet when it used to work..
im a little new to ubuntu

thank you in advance

---

### Post by grahammechanical on 2010-12-08
Go to System>Administration>Synaptic Package Manager and search for network-manager-gnome (if you are using Gnome, if not, kde) and select to install. That should do it.

Did you really uninstall network manager or simply remove it from the panel? If it was just removed from the panel then go to System>Preferences>Startup Applications and look for network manger there and select it.

Regards.

---

### Post by jr0535 on 2010-12-10
i tried to install it from synaptic already but it start to try to download it so if fails...

i did find it in startup apps but it was already selected on and i cant find it on the panel when i go to "add to panel"

---

### Post by messelink on 2010-12-10
Go to Synaptic and mark the package you want to install (network-manager-gnome). Then go to File->Generate package download script and save the file on a USB stick.

Take the USB stick to a computer that does have internet and execute the script.

Take the USB stick back to your broken computer and open Synaptic again. Go to File->Add downloaded packages and select the USB stick and the package should be installed.

It is a bit strange that the package is not in your cache though, did you empty your package cache on purpose?

---

### Post by jr0535 on 2010-12-10
solved..thank you very much i got reinstalled and working.

---

