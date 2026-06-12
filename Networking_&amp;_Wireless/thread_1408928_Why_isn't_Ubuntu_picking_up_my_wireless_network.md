---
title: "Why isn't Ubuntu picking up my wireless network?"
date: 2010-02-17
forum: Networking &amp; Wireless
---

### Post by Earl-Grey on 2010-02-17
Hope somebody can help. When I looking in my wireless connections list, my router never pops up. Sometimes I can connect to the internet when I type my information in manually but I think the root of the problem is that it isn't showing up in my list.

Would I need to find a new driver for my wireless card?

Any help would be great.

---

### Post by wojox on 2010-02-17
What's:

```
lspci | grep -i net
```

tell us?

---

### Post by bhuvi07 on 2010-02-17
hi every one..
i just installed kde in  linux..
so the problem nw is that the network manager works fine with gnome n detects ol the wirelless networks..
but KDE does identifies any network..
plzzzz help me toof ind the network manager as well as it can detect networks olse

---

### Post by Earl-Grey on 2010-02-17
> **wojox said:**
> What's:

```
lspci | grep -i net
```tell us?


wow, thanks for the fast reply.

This is what I got;-

```
0c:04.0 Ethernet controller: Atheros Communications Inc. Atheros AR5001X+ Wireless Network Adapter (rev 01)
0c:0b.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)

```

---

### Post by superprash2003 on 2010-02-17
does it not list any wifi network at all? or just yours?

---

### Post by Earl-Grey on 2010-02-17
> **superprash2003 said:**
> does it not list any wifi network at all? or just yours?

It lists three or four but not mine. In XP it shows a larger list and I can connect to my route with ease.

Would it be possible that my router isn't compatible with Ubuntu?

---

### Post by Earl-Grey on 2010-02-20
I have got the Network Manager to work a little bit better now by changing my SSID. Now when I look for my network in the list it is nearly always there. I'm still having trouble connecting to it though and every time I restart I still have to delete my previous settings and put them in again and repeat the cycle quite a few times before I can connect. :confused:

---

### Post by wfarr_09 on 2010-02-20
I Have the same sort of problem only, It Doesn't show any networks. Here's the code from when I Boot my computer.(BTW: It's a PCMCIA Card.)

> 
[56.458314]ETH0:Cannot Find Firmware agere_sta_fw.bin
[56.540050]hermes@00010100:Timeout Waiting For Command 0x0002 completion
[57.060189]ETH0:Cannot Find Firmware agere_sta_fw.bin
[57.060241]orinoco_reset:Error -2 Re-initializing firmware
[57.060243]eth0: Device Has Been Disabled
:confused:

---

### Post by northd_tech on 2010-02-20
> **wfarr_09 said:**
> I Have the same sort of problem only, It Doesn't show any networks. Here's the code from when I Boot my computer.(BTW: It's a PCMCIA Card.)

[56.458314]ETH0:Cannot Find Firmware agere_sta_fw.bin
[56.540050]hermes@00010100:Timeout Waiting For Command 0x0002 completion
[57.060189]ETH0:Cannot Find Firmware agere_sta_fw.bin
[57.060241]orinoco_reset:Error -2 Re-initializing firmware
[57.060243]eth0: Device Has Been Disabled 			 		


It looks like yours is hunting a firmware file "agere_sta_fw.bin" but I'm not sure it is the same Atheros network card.

You should probably run these commands from a terminal and post the results so that we can make sure what kind of hardware you have:

```

lspci 

lsmod

uname -a

sudo lshw -C network

ifconfig

iwconfig
```

I know that the older Broadcom wireless cards needed to "cut" the firmware out of Windows drivers to work under Linux (but a Linux driver has since been released for those).  Your card sounds like a similar situation.

---

### Post by northd_tech on 2010-02-20
From what I was reading on these threads:

[http://ubuntuforums.org/showpost.php?p=8858008&postcount=2](http://ubuntuforums.org/showpost.php?p=8858008&postcount=2)

maybe you guys with this Atheros AR5001X and AR5001X+ (like Earl-Grey's results indicate above) should consider using ndiswrapper and some Windows drivers.

You should be able to download the drivers here for 32-bit:

[http://www.atheros.cz/download.php?atheros=AR5001X&system=1](http://www.atheros.cz/download.php?atheros=AR5001X&system=1)

and here for 64-bit:

[http://www.x-drivers.com/catalog/drivers/wireless_networks/companies/atheros/models/ar5001x/8735.html](http://www.x-drivers.com/catalog/drivers/wireless_networks/companies/atheros/models/ar5001x/8735.html)

[http://www.atheros.cz/](http://www.atheros.cz/)

After you unzip the appropriate file, you just point to those drivers by going into System > Administration > Windows Wireless Drivers (if ndiswrapper is already installed, which it should be under 9.04 or 9.10).

I'm not sure which of the drivers that Atheros needs- you might need to trial & error it a little to find the correct driver.

---

### Post by Earl-Grey on 2010-02-20
Thanks for the advice. If I get it to work I will post my results here :KS

---

### Post by excogitation on 2010-04-18
I filed a bug about the weak reception problem here: [565537]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/565537").
Feel free to contribute.

---

