---
title: "Internet connection sharing?"
date: 2005-12-15
forum: Networking &amp; Wireless
---

### Post by DavidGX on 2005-12-15
Hey guys. Currently until I can buy a router I'm hooking my modem to my pc via usb, then from my pc to my xbox 360 (yes I know it's microsoft.. I don't care for windows either that's why I switched to linux. But I do love the console.) using ethernet cable. Basically, this right here...

(Internet)[COLOR="Red"]=======[/COLOR][Modem][COLOR="yellow"]====[/color][PC][COLOR="blue"]====[/color][Xbox 360]

[COLOR="Red"]Cat5[/color]
[COLOR="blue"]Ethernet[/color]
[COLOR="yellow"]USB[/color]


It worked fine under windows xp using internet connection sharing, but I can't figure out how to get this same setup working under ubuntu. I've searched the forum and google for solutions but haven't found anything that's worked. Any ideas?

---

### Post by alamba on 2005-12-15
I have'nt tried this yet but I think either of these steps should do it:
1. Install firestarter and click on internet sharing
2. In /etc/network -> vi options
3. Change ip_forward=no....to...yes

You should be all set.

Akshay

---

### Post by DavidGX on 2005-12-15
[QUOTE=alamba]I have'nt tried this yet but I think either of these steps should do it:
1. Install firestarter and click on internet sharing
2. In /etc/network -> vi options
3. Change ip_forward=no....to...yes

You should be all set.

Akshay[/QUOTE]

Did that but I keep getting "the device eth0 is not ready" from firestarter. :(

---

### Post by FLeiXiuS on 2005-12-15
After enabling internet forwarding you will have to restart the network service.

$ sudo /etc/init.d/networking restart

Another thing, you need either to set your Xbox's IP address in the same network as what you set eth0.  

To take a step back from configurations, you will need to use a CROSSOVER cable rather then a straight-through when connecting an xbox directly to the PC's NIC.

---

### Post by DavidGX on 2005-12-15
[QUOTE=FLeiXiuS]After enabling internet forwarding you will have to restart the network service.

$ sudo /etc/init.d/networking restart

Another thing, you need either to set your Xbox's IP address in the same network as what you set eth0.  

To take a step back from configurations, you will need to use a CROSSOVER cable rather then a straight-through when connecting an xbox directly to the PC's NIC.[/QUOTE]

Well it worked in windows so I don't know why it wouldn't work here, so I must have the right cable.

Getting closer I think. I have the IP set as 192.168.0.1 in linux and in the 360. The subnet mask is set to 255.255.255.0 in linux & the 360. The gateway isn't set in linux and is set to 0.0.0.0 in the 360.. and it (360) tells me that's what it should NOT be set to :confused: 

Can I just make something up for that or do I need something specific there? And should DHCP be enabled just in firestarter or in firestarter and in the network settings for eth0?

---

### Post by afhp on 2005-12-15
[QUOTE=DavidGX]Well it worked in windows so I don't know why it wouldn't work here, so I must have the right cable.

Getting closer I think. **I have the IP set as 192.168.0.1 in linux and in the 360**. The subnet mask is set to 255.255.255.0 in linux & the 360. The gateway isn't set in linux and is set to 0.0.0.0 in the 360.. and it (360) tells me that's what it should NOT be set to :confused: 

Can I just make something up for that or do I need something specific there? And should DHCP be enabled just in firestarter or in firestarter and in the network settings for eth0?[/QUOTE]

You can't have two machines with the same IP address. 
Make it 192.168.0.1 on the PC, and 192.168.0.2 on the Xbox, for instance. Subnet is OK. Gateway should be set to your PC's address on the Xbox.

Whether you need DHCP (client) on the modem side is up to your ISP. It shouldn't be needed on the ethernet side since you're defining a static address. It's not needed on the Xbox for the same reason.

>  I keep getting "the device eth0 is not ready" from firestarter

Not sure about the way it's supposed to appear here... What is the "apparent" network interface that represents the modem ? If it's indeed eth0, maybe the modem isn't properly recognized. If eth0 is indeed your network card it might not be up. 

What's the output of the ifconfig command ?

---

