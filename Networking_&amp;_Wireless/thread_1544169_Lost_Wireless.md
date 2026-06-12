---
title: "Lost Wireless"
date: 2010-08-02
forum: Networking &amp; Wireless
---

### Post by shaneg-nz on 2010-08-02
Running kubuntu 10.04, all updates applied
Intel Wifi Link 5100

So my laptop froze and had to do a hard reset via the power button,
When i booted back up i had lost my wireless, it was disabled somehow and my drivers were completely wiped from /lib/firmware (iwlwifi-50001/2 ucode) these were shown up at boot, and ifconfig/iwconfig/lshw/networkmanager all showed that i had no wlan0.

So copied the 2 files over from the livecd which im using now.

This fixed the missing files and wlan0 is there, i can also view networks via airodump but via networkmanager there are no visible networks at all, i know i could connect from the command line but that isnt a fix just a band-aid and i dont want my router running wep.

Any other things i could/should copy over?
Any other way to fix this?

---

### Post by winniler on 2010-08-15
I have just had the same problem, I had to forcibly reboot my ACER aspire 5535 laptop and when I was in my kubuntu I couldn't see any wireless network anymore in the scan box.

---

