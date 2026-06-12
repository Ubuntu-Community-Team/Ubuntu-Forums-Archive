---
title: "Ethernet connection HW disables Wifi (HP ProBook with Intel Centrino Advanced-N 6205)"
date: 2013-08-29
forum: Networking &amp; Wireless
---

### Post by Pompey on 2013-08-29
I need some help/hints

I've been trying to get my HP ProBook 6460b to work as an Access Point, which I have successfully achieved. Unfortunately when I connect the Ethernet Cable, then WIFI becomes hardware disabled as though I have pushed the HW button. If I remove the Ethernet Cable then WIFI is active again. It appears to me as though the Ethernet cable is acting as the HW switch. Using the HW Wifi switch just toggles between "airplane mode". This is stopping me from reaching my goal of using the laptop as an occasional Wireless router.

I'm doing everything with the Ubuntu 13.04 desktop 64 bit live CD, but also tried with a 12.04 live CD and had the same results. The laptop has Windows 7 installed and I do not have the same phenomenon under this OS (e.g Wireless is enabled when the ethernet cable is connected). I've done plenty of searching and haven't found a solution, I have also made the odd Bios setting change without success. I have not tried restore default Bios settings like one suggestion that is supposed to work. If this actually does work, as claimed, there must be a setting I can manipulate, but I don't want to do a try it and see approach.

I've tried the various rfkill commands to no effect, but the rfkill list all command does show Wifi being hw blocked as soon as I connect the ethernet cable and not being hw blocked when I remove the ethernet cable.

Anyone out there got any ideas, or has experienced this? Remember, I want to do everything with the live CD, so removing and installing drivers is fine if I don't have to reboot.

---

### Post by Pompey on 2013-08-30
Finally solved this issue!

For those of you who have the same "problem", it is actually just a bios setting that is buried away. One has to disable the "lan/wlan switching" option. I'm now using my laptop  as a WIFI router when required.

Also realised I gave some mis-information in my original mail. I DID have this same problem phenemon in Windows 7.

---

### Post by ingridt on 2013-09-29
This bios setting helped me on my Dell Latitude ubuntu 12.04, that switched to airplane modus after using a docking station. I changed the "Wireless Switch" from "all" to "none". Thanks!

---

