---
title: "SMC 2802W Wireless working..."
date: 2006-06-12
forum: Networking &amp; Wireless
---

### Post by Pirámide on 2006-06-12
Dear friends:

I've installed wireless network with a SMC 2802W wireless card. As you know, this wireless card is problematic, because SMC changed the prism54 hardware. This problems are related in a [previous message of remmelt]("http://www.ubuntuforums.org/showthread.php?t=27916&highlight=smc+2802W"), but it's about 5.04, and contains a configuration error.

I explain here all the process:

[LIST=1]
[*]First of all, you must check that your card is v2 (v1 works fine with prism54 driver)
[*]If it's v2, Ubuntu detects it, but can't activate or connect to ESSID
[*]Now, connect to SMC web, and [get the XP drivers]("http://www.smc.com/index.cfm?event=downloads.doSearchCriteria&localeCode=EN_NLD&knowsPartNumber=false&productCategory=5&userPartNumber=&modelNumber=541&partNumber=2991&downloadType=1&os=8")
[*]Unpack the XP driver
[*]Open **Synaptic**, and install ndiswrapper-utils package
[*]Open a console
[*]sudo modprobe -r prism54 (uninstalls prism54 module from kernel)
[*]sudo ndiswrapper -i /path_to_the_driver/2802W.inf (installs 2802w driver)
[*]ndiswrapper -l (check the driver installation)
[*]sudo ndiswrapper -m (attach ndiswrapper module to kernel)
[*]modprobe ndiswrapper (without any message: it's ok)
[*]Open **System, Administration, Network**... you must see wlan0 card. You can configurate it, and use the wireless network.... but this is only temporal. If reboot, prism54 driver is active again, and you lose, so...
[*]In console, sudo gedit /etc/modprobe.d/blacklist
[*]At the end of file, add the line "blacklist prism54". Save the file, and reboot Ubuntu.
[*]All must be fine now...
[/LIST]
Note that, when Ubuntu starts, if can't detect the access point predefined, the process is delayed some time...

I need help to configure Wep and WPA for this card...

---

### Post by Culito on 2006-06-15
Too Bad the 2602W is a whole different animal.  It has an oddball AMD chipset that I gave up on.

---

