---
title: "Acer Asprie 5516 - Wired not recognized"
date: 2009-08-31
forum: Networking &amp; Wireless
---

### Post by StrangersInTheDark on 2009-08-31
Hello world,

My piece of sh*t Dell is no longer with us... But like a bad wife I'm glad it is gone haha... Anyways I just picked up a new Acer Aspire 5516 and just like a new married couple it runs fine...

Currently pleased with it. Only One problem, I currently run a dual boot with vista and ubuntu. Ubuntu recognizes the wireless drivers etc and I can pick up signals and all the normal stuff. However, Ubuntu doesn't seem to have installed the drivers for the network card inside. So I cannot connect to the internet or anything.

Does anyone know a place where I can pick up generic drivers for this? I get no lights no connection nothing, it's as if the network card does not exist.

Any information would be appreciated. Thank you in Advanced.

Before anyone asks "If your network card doesn't work how did you post this message?" The answer to this question is... I booted into Vista :-( and came to the Ubuntu forums.

Now you tell me..."That aint right" I agree, so pleaseee help me get the network card drivers haha...

Take Care everyone,
StrangersInTheDark

---

### Post by uylug on 2009-08-31
Have you tried this?

```
sudo lshw -C network
```

---

### Post by StrangersInTheDark on 2009-08-31
> **uylug said:**
> Have you tried this?

```
sudo lshw -C network
```


yeah one moment. Let me log into Ubuntu and get that information. I will come back and post it ASAP.

---

### Post by uylug on 2009-08-31
Also, try these commands:

```
ifconfig
```

```
cat /etc/network/interfaces
```

```
sudo dhclient eth0
```

---

### Post by StrangersInTheDark on 2009-08-31
> **uylug said:**
> Also, try these commands:

```
ifconfig
``````
cat /etc/network/interfaces
``````
sudo dhclient eth0
```


Sh*t haha now I have to log in and out again to the Operating SYstems...

alright alright... here is the information for the first thing you asked for

-network               
       description: Wireless interface
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wmaster0
       version: 01
       serial: 00:25:56:32:3c:87
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath5k_pci latency=0 module=ath5k multicast=yes wireless=IEEE 802.11bg
  *-network UNCLAIMED
       description: Ethernet controller
       product: Attansic Technology Corp.
       vendor: Attansic Technology Corp.
       physical id: 0
       bus info: pci@0000:05:00.0
       version: c0
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list
       configuration: latency=0
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 92:e1:58:7d:30:88
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

---

### Post by StrangersInTheDark on 2009-08-31
[SIZE=3][SIZE=2]Hi here is all the stuff you asked for. I hope it helps, please let me know if you have any idea what the problem may be. I appreciate it.

[/SIZE]**ifconfig**[/SIZE]


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:480 (480.0 B)  TX bytes:480 (480.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:25:56:32:3c:87  
          inet6 addr: fe80::225:56ff:fe32:3c87/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wmaster0  Link encap:UNSPEC  HWaddr 00-25-56-32-3C-87-63-38-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)



[SIZE=3]**cat /etc/network/interfaces**[/SIZE]

auto lo
iface lo inet loopback


[SIZE=3]**sudo dhclient eth0**[/SIZE]

Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wmaster0: unknown hardware address type 801
SIOCSIFADDR: No such device
eth0: ERROR while getting interface flags: No such device
eth0: ERROR while getting interface flags: No such device
wmaster0: unknown hardware address type 801
Bind socket to interface: No such device

---

### Post by uylug on 2009-09-02
Your network card has not been claimed and you have no eth interface.

See if you can force it:

add this to the /etc/network/interfaces file

```
iface eth0 inet static
address your_ip_address
netmask 255.255.255.0
gateway your_gateway_address

```

```
sudo /etc/init.d/networking restart
```

```
sudo ifconfig eth0 up
```

---

### Post by didibanner on 2009-09-03
> **StrangersInTheDark said:**
> Hello world,

My piece of sh*t Dell is no longer with us... But like a bad wife I'm glad it is gone haha... Anyways I just picked up a new Acer Aspire 5516 and just like a new married couple it runs fine...

Currently pleased with it. Only One problem, I currently run a dual boot with vista and ubuntu. Ubuntu recognizes the wireless drivers etc and I can pick up signals and all the normal stuff. However, Ubuntu doesn't seem to have installed the drivers for the network card inside. So I cannot connect to the internet or anything.

Does anyone know a place where I can pick up generic drivers for this? I get no lights no connection nothing, it's as if the network card does not exist.

Any information would be appreciated. Thank you in Advanced.

Before anyone asks "If your network card doesn't work how did you post this message?" The answer to this question is... I booted into Vista :-( and came to the Ubuntu forums.

Now you tell me..."That aint right" I agree, so pleaseee help me get the network card drivers haha...

Take Care everyone,
StrangersInTheDark

Hi StrangersInTheDark,
I have the same PC and although the wireless works, it works REALLY SLOWLY. You wouldn't happen to have a way around this would you?

Thanks

---

### Post by StrangersInTheDark on 2009-09-04
> **didibanner said:**
> Hi StrangersInTheDark,
I have the same PC and although the wireless works, it works REALLY SLOWLY. You wouldn't happen to have a way around this would you?

Thanks




Hello didibanner,

It is hard for me to determine if my wireless is slow because I was 'borrowing' it from somebody in the neighborhood. But during those experiences, it did run rather slow.

Have you tried getting close to your wireless router and see if it improves any if all? Or check your router is password protected or not. If its not password protected everyone can hop on and eat away your fast connection.

There is a setting in ubuntu I think its called Detect Hardware Drivers if you point your finger up on the menu's it should appear under one of them (sorry, I had to keep switching from ubuntu to vista so im not on ubuntu right now because I still get no internet). But if you see the Detect Hardware Drivers or something similar it will let you select to use a different driver for your wireless card. That might help, and if not you can deactivate it and it will go back to what you had before.

The internal wireless chip by default might be a cheap one that they assigned to our pc. But she runs like a champ in every way I like... Great for programming.

If wireless is that important to you. You might want to check out ebay for a Netgear Wireless USB. I just checked them out for you, and they had some for 13 dollars with free shipping... That might be just what you need. I had one of those from Netgear and it got the job done, great strength for signals.

Sorry for my rant. By the way does your network card work?

- StrangersInTheDark

---

### Post by ctx126 on 2009-09-04
> **uylug said:**
> Your network card has not been claimed and you have no eth interface.

See if you can force it:

add this to the /etc/network/interfaces file

```
iface eth0 inet static
address your_ip_address
netmask 255.255.255.0
gateway your_gateway_address

```

```
sudo /etc/init.d/networking restart
```

```
sudo ifconfig eth0 up
```
Hi,

Did you ever get the original problem regarding your LAN card fixed? I have the same laptop, and although the wireless works, I cant for the life of me get the LAN card working. Does anyone out there know how to fix this problem?

Thank you in advance,

C

---

### Post by StrangersInTheDark on 2009-09-04
Hi C,

No, i'm sorry I did not get that to work. On the last command it threw an error. The driver we need for our network card is a Atheros AR8132 I have not been able to find anything on it.

This has taken me some time to figure out. So I'm thinking I might be better off buying a cheap USB Ethernet Adapter from ebay or newegg.

That should solve my problem.

Other then that, I really do enjoy this laptop and for the price I got it for. Let me know if you find any answers or  have any suggestions.

Take Care,
StrangersInTheDark

---

### Post by didibanner on 2009-09-04
Thanks for the tips, StrangersInTheDark. I tried them but the wifi is still pretty slow :(

---

### Post by ctx126 on 2009-09-05
Hi StrangersInTheDark,

Thank you for your prompt reply. I actually managed to get my LAN NIC working...here is the link for how I did it...

[http://ubuntuforums.org/showthread.php?t=1197614&highlight=acer+5516](http://ubuntuforums.org/showthread.php?t=1197614&highlight=acer+5516)

- C

ps I couldn't get it to work initially, but I reinstalled 9.04 this morning, and then following the steps in the link exactly, I got my LAN to work.

---

### Post by StrangersInTheDark on 2009-09-05
> **ctx126 said:**
> Hi StrangersInTheDark,

Thank you for your prompt reply. I actually managed to get my LAN NIC working...here is the link for how I did it...

[http://ubuntuforums.org/showthread.php?t=1197614&highlight=acer+5516](http://ubuntuforums.org/showthread.php?t=1197614&highlight=acer+5516)

- C

ps I couldn't get it to work initially, but I reinstalled 9.04 this morning, and then following the steps in the link exactly, I got my LAN to work.

Hey C,
Thanks for the heads up. I have a question though. How were you able to install it? I downloaded the tar.gz but got kind of lost on it all. What were the commands you used to install it. I tried following the examples, but it wasn't working out for me.

Any input would be helpful. Anything to get me going so I can get back to developing.

Thanks again,
StrangersInTheDark

---

### Post by ctx126 on 2009-09-06
Hi StrangersInTheDark,

Sure. 

After I reloaded Ubuntu 9.04, I went to the atheros site, and downloaded the following file - AR81Family-linux-v1.0.0.10.tar.gz.

After I got this file, I did the following....

tar -xzvf AR81Family-linux-v1.0.0.10.tar.gz
cd src
make
sudo make install
sudo insmod atl1e.ko
...and the card worked! One word of caution however, after you do you first update, the NIC card will stop working - it did for me. I had to rerun the steps above to make it work again. 

Hope this helps, Let me know if you have any questions.

-chuck

---

### Post by bobwdn on 2009-09-06
This is my two cents on this issue.

I have the same issue with an Acer 5516 laptop. (It currently is running Windoze Vi$ta.) As a test, I tried the Ubuntu live CD. It does not recognise the wired network.

I use Clonezilla for a barebones backup of all machines in our house. Clonezilla experiences the same issue (not recognising the wired network.)

So, my point is that it is not just an Ubuntu issue. It must be the Linux driver software that is the issue.

So, I hope the Linux driver community is working on a new driver.

---

### Post by StrangersInTheDark on 2009-09-06
> **ctx126 said:**
> Hi StrangersInTheDark,

Sure. 

After I reloaded Ubuntu 9.04, I went to the atheros site, and downloaded the following file - AR81Family-linux-v1.0.0.10.tar.gz.

After I got this file, I did the following....

tar -xzvf AR81Family-linux-v1.0.0.10.tar.gz
cd src
make
sudo make install
sudo insmod atl1e.ko
...and the card worked! One word of caution however, after you do you first update, the NIC card will stop working - it did for me. I had to rerun the steps above to make it work again. 

Hope this helps, Let me know if you have any questions.

-chuck

WOOOOOOOOOOO HAHAH Yeah man!!! Thats what i'm talking about!!.... Finally got that b*tch working haha..

thanks for the tips man I appreciate it. The problem for me was I downloaded the tar.gz file onto the desktop so when I ran the commands it wouldn't work. So I moved the file into my 'username' folder, typed in the commands and that baby went to work haha...

Thanks again!! Now I can get back to my programming and Fantasize about Keira Knightley hahah..

[IMG]http://3.bp.blogspot.com/_DLMbxIoKN3c/SNWf2rqdh0I/AAAAAAAAKA8/ZGzo8cgSnq0/s400/keira-knightley-23.jpg[/IMG]

[SIZE=3]**"Keep that 'do while' looping looping."**[/SIZE]

 Peace,
 - **StrangersInTheDark** :cool:

---

