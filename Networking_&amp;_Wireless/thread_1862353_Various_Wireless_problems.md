---
title: "Various Wireless problems"
date: 2011-10-16
forum: Networking &amp; Wireless
---

### Post by capicoso on 2011-10-16
Hi.
I bought a LinkSys WRT120N router so i can have internet in my desktop pc and in my laptop. 
I connect from my modem to the router, then from the router to my desktop pc. Everything works. I couldn't and still can't access to the router's page 192.168.1.1 from ubuntu 11.04. On windows i can. In my Ubuntu connection the gateway is 200.63.148.159, but in my windows is 192.168.1.1. Maybe thats why i can access it from windows. This is going to be a long post, i had/have many problems, im new to ubuntu, and even newer to wireless networking. Btw my ubuntu desktop pc is wired connection.
 So from windows i setted up the router:
```

Automatic configuration - DHCP

Local IP address 192.168.1.1
Subnet mask 255.255.255.0
DHCP server enabled
Static IP Address 192.168.1.100
IP address range 192.168.1.100 to 149
Static DNS 0.0.0.0
```Now for the wireless setup
```

Network mode-N Only (i tested all of the modes already, auto, g, etc)
SSID Casita
Channel Width 20Mhz
Wide Channel Auto
Standar Channel 9 -2452GHz
SSID Broadcast Enabled

``````

Security Mode WEP
Encryption 40/64bit (10HEX digits)
Key1 abb95e73d3
Transmit key 1

```Well, thats my router configuration.

Now on the notebook, i ran commands to see what is my wireless card but it didnt give me too much information, so i went to windows and checked it and it's a mini 802.11n wireless adapter.
So i downloaded ndiswrapper? and installed the driver n73 on linux. Until now i couldn't activate the wireless network, tried to unblock it via terminal, but then i figured out i had to push a laptop button(d'oh) So now i can see my "Casita" network! When i had a WPA key i couldn't connect, and i didnt know how to configure the password so i can type it and login, well nevermind that, i'll configure WPA when i can actually connect.
So with WEP encryption i put my password, and i'm on! At least it says so... i'm connected. But not really. Says i'm connected but i'm not. I suppose it has to be something about the ips dns, etc. Because i have the same problem in windows. I connect but i'm not really connected. Btw this is the wireless network information on my laptop:

```
General
Interface: 802.11 WiFi(wlan0)
Hardware ID?(I'm traslating everything) 00:1D:92:17:BB:0E
Controller: rt73usb
Speed: 18Mb/s
Security: WEP

IPv4
Ip address: 192.168.1.101
Adress of difussion?: 192.168.1.255
Subnet Mask 255.255.255.0
Gateway? 192.168.1.1
DNS 1 192.168.1.1

IPv6
Ignored

```I've been searching and trying things for +15hrs, i don't know what else to do, followed a tutorial here in ubuntu, iwconfig commands, ifconfig, etc. 

Please help. If need more info or a better explanation tell me. Thanks

PS: the OS in the laptop is Lubuntu 11.04

---

