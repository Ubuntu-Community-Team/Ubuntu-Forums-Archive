---
title: "Intrepid x64 doesn't like my USB (Asus N-11) modem"
date: 2008-12-13
forum: Networking &amp; Wireless
---

### Post by Reiger on 2008-12-13
I've tried native Linux Drivers (it's actually a Ralink 2870 device, or at least that's the driver shipped from Asus' support website) but no dice: it will not add any pysical/logical interface-name in the ifconfig/iwconfig lists.

Next step I've tried was Ndiswrapper + XP drivers. At least now I can 'see' my wireless modem/router through iwlist scan. And WICD finds the device and list networks around me. 

Problems occur however whenever I try to connect to this WPA-PSK network: both manual connection ([http://ubuntuforums.org/showthread.php?t=571188](http://ubuntuforums.org/showthread.php?t=571188)) and connection via network-config or wicd manager fail at the Authentication/DHCP stage.

---

### Post by Reiger on 2008-12-14
Huh? This is really odd: against all better judgenent (tried before nothing suspicious) I've tried the command:
```

lsusb

```

Yet again to see if the device was listed in combination with 
```

sudo ndiswrapper -l

```

Of course it was. But then I unplugged it, and tried again to see if the system would notice...

Well it wouldn't: either command would just 'lock itself up'. Mind you, not the system: that ran Ok (except for Wireless, then), it's just that this particular command would refuse to respond with *any* output even though I can simply run other programs...

However, my suspicions were immediately aroused when I felt how hot the USB thing ran. Granted: it was plugged into the USB hub of my monitor, but (a) where the device itself was located the monitor was actually quite cool; (b) no other USB device on my PC runs _that_ hot (by the feel of it ~40 - 50 C). Only explanation was that some cable was blocking (my USB keyboard is plugged in into the second USB port there) the airflow to the device air-intake/exhaust.

At any rate, tried the same commands with a fresh reboot and after exchanging positions of another USB device and my USB modem ... guess what? It works.

I'll try yet another reboot to see if results are consistent and this isn't some one/off chance, but not before I've made some much-desired/needed downloads. :p

---

