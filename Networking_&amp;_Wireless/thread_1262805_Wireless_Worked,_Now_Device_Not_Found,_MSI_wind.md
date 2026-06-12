---
title: "Wireless Worked, Now Device Not Found, MSI wind"
date: 2009-09-10
forum: Networking &amp; Wireless
---

### Post by WarholsGhost on 2009-09-10
Hello,

I have an MSI wind with an internal wireless card. It's running the newest version and xubuntu and up until this morning wireless worked fine. Now this morning the device is not showing up in ifconfig and nm-applet says "device not ready"

The internal card is an "Atheros AR242x 802.11agb Express Adapter"

does anyone have any ideas where i can start trouble shooting?

---

### Post by WarholsGhost on 2009-09-10
some more info:

when looking in iwconfig, the device is found but it's not connected to anything.

dmesg is giving me lots of errors of this type

```
atkbd.c : unknown key released (translated set 2, code 0xf6 on isa0060/serio0
```

---

### Post by hellmet on 2009-09-10
Exactly same problem today. Same Ath device. Worked in the morning. Not anymore in the evening. I can't even see 'Enable Wireless' or any available wireless signals nearby anymore. The connection still exists in the network-manager, though. 
I'm having to type this from Windows.

---

### Post by WarholsGhost on 2009-09-10
i was able to get wireless working by attaching a usb wireless card, but not the internal card.

anyone with any insight, please post.

---

### Post by JordanKeith on 2009-09-10
Similar problem here. I just installed the newest stable version of UbuntuStudio. Wireless worked fine, I was able to connect to the internet using the wlan0 device. I hopped on the default package manager and started a download of OpenOffice; after about five minutes the computer locked up, forcing me to do a hard reboot. After restarting, everything works fine but now the wlan0 device isn't even detected.. =S

---

### Post by WarholsGhost on 2009-09-10
are you both using MSI wind?

---

### Post by JordanKeith on 2009-09-10
I'm not sure what that is, so I doubt it. I've got an Atheros wireless card, if that's any help. I just installed UbuntuStudio this morning after enjoying LinuxMint Gloria but wanting more as far as audio production goes..

---

### Post by WarholsGhost on 2009-09-10
it's the laptop i'm working with that has that chipset, just wondering how concentrated the problem is.

---

### Post by JordanKeith on 2009-09-10
I'm not sure on what my chipset is =\ Sorry, I'm not very hardware savvy.  If it gives you any information, I'm using a Toshiba Sattelite Pro, with an Intel Pentium processor. That's about as much information as I know, hardware-wise.

---

### Post by hellmet on 2009-09-10
I'm on a Thinkpad R500.
My wireless was working all right. But yesterday, I activated the Proprietary h/w drivers but wireless still worked. Today morning I shut down my PC and started it in the evening. Now, no wireless, not even an option to de-activate the wireless proprietary drivers. The "Hardware Drivers" windows is empty!! I was better off using free ath5k drivers.

---

### Post by JordanKeith on 2009-09-10
I've found my problem.. The ISO didn't download entirely, which is why it kept crashing. I have to have an OS for class though, so I'm switching back to LinuxMint this afternoon. I suppose the software running on UbuntuStudio should work on LinuxMint as well.

---

