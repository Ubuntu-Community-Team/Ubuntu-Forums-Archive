---
title: "Weird minor wireless issue on Macbook 5,2"
date: 2011-04-15
forum: Networking &amp; Wireless
---

### Post by BlackLagoon187 on 2011-04-15
Hey guys, I recently installed Ubuntu 10.10 32-bit on my Macbook 5,2 and it is working great.
I followed the guide set in ubuntu under the Mac section for my Macbook model but there is a weird thing I found. Whenever I unplug my Macbook from the AC power source and attempt to browse the internet on battery power I am unable to do so but when I reconnect the power source whatever page I was trying to connect to connects.
My wireless card is BCM4322 802.11a/b/g/n Wireless LAN Controller

I have read this post [http://ubuntuforums.org/showpost.php?p=5024425&postcount=1](http://ubuntuforums.org/showpost.php?p=5024425&postcount=1)
Where it has extra steps regarding the network adapter for those that dual boot with windows but the problem still persists. I am triple booting with Mac OSX, Windows, and Linux but there is no special mention on it so I am not sure if I need to do something extra on the Mac side.

I am not sure if I am using the correct keywords when I search in the forums and google but I am unable to find a solution. If it already is covered I would appreciate if you would link me to it :)

Thanks in advance!

Regards,

Timothy

A new Ubuntu user

---

### Post by BlackLagoon187 on 2011-04-24
I found a soloution, I was using maxcpus=1 for my boot settings in grub which was recommended by the guides here and left acpi on now I changed the setting to acpi=off instead of maxcpus=1 and now I can browse the internet regardless of whether or not it is connected to the ac power source.

Hope this helps someone.

---

