---
title: "Ubuntu 9.10, Acer Aspire One, Atheros and dhclient not running"
date: 2009-11-10
forum: Networking &amp; Wireless
---

### Post by tenentblueberry on 2009-11-10
Hi all, I've got an Acer Aspire One 751h in order to replace my MSI Wind U100. I installed Karmic Koala as soon as I got it. I wanted to get all new features, like GRUB2, ext4 in my root partition, etc. But I've problems with many items, like:
[LIST]
[*] Poulsbo chipset (solved)
[*] Audio (solved)
[*] Wireless
[*] Suspend
[*] Hibernate
[/LIST]
Etcetera.

First of all, I want to solve the wireless issue. This Acer netbook has an Atheros wireless card (AR5001), but dhclient doesn't find any valid IP addresses. It finds all wireless APs in the neighbourhood, but it cannot connect.

I tried to:
[LIST]
[*]Change from network-manager to wicd and vice-versa. The problem remains the same.
[*]blacklist acer_wmi (as I found somewhere), but there weren't any problems.
[*]blacklist atk_pci.
[*]Tried to change dhclient to dhcpcd and vice-versa, but dhcpcd only guess an "crazy" IP, like 169.254.251.46.
[*]modprobe -rf atk9k ; modprobe -rf ath5k ; modprobe atk9k ; modprobe ath5k, I tried to remove and reload the kernel modules, but there weren't any valid IP addresses.
[*]I've got JoikuSpot in my Symbian 3G smartphone, so I tried to create a new wireless network. Maybe my network has any configuration problems... No success, it couldn't connect to 
[/LIST]

No one had been successful. Any ideas? Ubuntu 9.10 reinstall isn't a bad idea either, nowadays...

And everything was fine with my (old) Wind... Dammit.

Thanks in advance, Ricardo.

---

### Post by Incandescence on 2009-12-16
Hi. I have the same problem, i've found that Flash Memory of every type I have (my iPod with HDD, SD card, flash drives) need to be unplugged before hibernating or suspending or the system will freeze, requiring a manual restart. It's not brilliant but if you unplug the card while it suspends or whatever, you're fine.

My audio works fine.

My wireless has apparently disappeared. I have wired ethernet capability and I can use my 3G mobile Broadband Dongle, as I am now, but I can't connect to my wireless network at home.

When I right click the wireless icon in the panel, the enable/disable wireless networking box isn't present, the left click menu has no wireless network category.

Unfortunately I'm still a Linux newbie so that's all i've got at the moment.

---

