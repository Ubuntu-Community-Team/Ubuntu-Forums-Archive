---
title: "RT5390 Wireless 802.11n intermittent connection"
date: 2012-10-30
forum: Networking &amp; Wireless
---

### Post by dwb814 on 2012-10-30
Hi,
I just installed Ubuntu 32bit on my wife's compaq presario cq57 laptop. Just about got everything worked out but, the wireless card (RALink RT3090) is having drop off-low signal issues. I did a ```
sudo modprobe -v rt5390 (also for) rt5390sta
``` and got FATAL: Module rt5390sta not found, the same for just 5390.

When I do ```
lspci -nnk
``` Kernel driver in use: rt2800pci Kernel modules: rt2800pc. But the network controller is RT5390 Wireless 802.11n 1T/1R PCIE. I tried blacklisting rt2800 pci, but since Module rt5390sta isn't found it killed my network connection.

I saw a post by "[[COLOR=#DD4814]**Wild Man**[/COLOR]]("http://ubuntuforums.org/member.php?u=508533") [http://ubuntuforums.org/showpost.php?p=11795211&postcount=2.]("http://ubuntuforums.org/showpost.php?p=11795211&postcount=2") 

My questions are, Should I run the "reinstall linux-headers" or isn't it necessary since I'm on 12.04? Should I download this driver and install it and blacklist the rt2800? And finally are the commands the same for 12.04?

I appreciate any help given on this. Thank you

---

### Post by lfehr on 2012-11-01
This is in german but it worked for me:

[http://forum.ubuntuusers.de/topic/ralink-rt-3391/#post-3473742](http://forum.ubuntuusers.de/topic/ralink-rt-3391/#post-3473742)

Hope it helps :)

---

### Post by dwb814 on 2012-11-02
> **lfehr said:**
> This is in german but it worked for me:

[http://forum.ubuntuusers.de/topic/ralink-rt-3391/#post-3473742](http://forum.ubuntuusers.de/topic/ralink-rt-3391/#post-3473742)

Hope it helps :)

Yes sir, it confirmed what I needed to do. Thanks

---

### Post by jsteen123 on 2012-11-24
Why doesn't ubuntu fix this?


I'm not a power-user, just want a distro that works  
I have a laptop (Hp Pavilion) and I can't exchange the card.

Installed OpenSuse, and it works great.
I love Ubuntu,but I found it a little funny, that a distro, who wants people to switch from Windows to Linux ,have this kind of problems.

There are a lot of laptops with this card,people who want to switch already have the hardware.

I still love Ubuntu, but it is frustrating when I tell my friends, about this great distro.
and when they install it, they  don't even have internet on their computer.

I mean for a Linux user this is a small issue, but for those who want to try Linux , well they go back to Windows.

excuse for bad English.

---

