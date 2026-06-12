---
title: "Weird Problem with Wi-Fi Card"
date: 2009-08-14
forum: Networking &amp; Wireless
---

### Post by VelkoMK on 2009-08-14
have an ASUS X50RL with a Atheros AR5007EG Wireless card with a hardware switch for it and for the Bluetooth Device.
When I turn on the hardware switch for the WiFi and Blue tooth, the LED for the WiFi just flashes, and it powers off.
I plugged in an external D-Link USB WiFi Adapter, I plug it in, then I flip the hardware switch for my atheros off and on, and my Atheros Works :S :S :S :S 
Now searching a tutorial to install a MadWiFi Driver (which was a failure) I accidentaly bumped onto 2 commands.
Apparently, if I type:

sudo rmmod asus_laptop
sudo modprobe asus_laptop 

...My Atheros wireless card works, but why like this? What am I doing? Is there a place for me to automize this so I don't enter it everytime I start Ubuntu?

---

### Post by VelkoMK on 2009-08-15
Anyone :S :S :S ?

---

