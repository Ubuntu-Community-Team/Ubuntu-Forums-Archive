---
title: "Cannot connect to router via cable (or wireless)"
date: 2009-09-24
forum: Networking &amp; Wireless
---

### Post by domee1 on 2009-09-24
Hello all,

I am new in this forum and in ubuntu. I already posted this problem in a German forum but no one was able to help so far.

I bought a new wireless router (model: Hama MiMO Wlan Router, built-in 4-Port-10/300-Mbps-Switch, WPA2) but just can't get a connection. It should, as the manual says, automatically give me an IP address via DHCP, but it doesn't. When I start my computer, the network manager seems to be searching for an IP address, so it seems to recognize some connection although I cannot PING the router (it says "destination unreachable" or something like that). Neither can I connect via wireless because it first has to be activated and for that I will have to gain access to the admin-center. Because they asked in the other forum for it:

interfaces file:

```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp
```resolv.conf file:

```
domain netcologne.de
search netcologne.de
nameserver 81.173.194.76
nameserver 81.173.194.69
```I have a MULTICABLE connection. It is basically everything (TV, telephone, internet) in one cable and I have a special router for that. But I don't think thats the problem, because I cannot even connect to the router alone.

Maybe anyone can help? :)

Thanks a lot,
Dom

PS: The IP of the router is 192.168.2.1. I already tried and deleted all that stuff from the resolv.conf and put "nameserver 192.168.2.1" in there but it didn't work.

---

### Post by chili555 on 2009-09-24
Your *interfaces* file suggests that you will control the wired interface and Network Manager will control the wireless. Once you get set up and use wireless more or less exclusively, that will work fine. However, NM is supposed to shut off wireless if the ethernet cable is plugged in. I'm not sure what it does if the wired interface is not in its control. Let's try this, in a terminal:```
sudo /etc/init.d/NetworkManager stop
sudo ifconfig wlan0 down
sudo dhclient eth0
```Sustitute your wireless interface if it's not wlan0.

However, it might be just as easy to allow NM to control both interfaces. Let's troubleshoot your wired connection first.

Incidentally, this *resolv* file confirms that you were connected at some time:> domain netcologne.de
search netcologne.de
nameserver 81.173.194.76
nameserver 81.173.194.69This can only be provided by the router.

---

### Post by domee1 on 2009-09-24
Hello chili555,

thanks for your reply. the manual of the router says that wireless is deactivated by default. so if will have to connect via cable to access the routers admin center. i will, however, try and do what you suggested. whats in the resolv.conf is provided by the cable modem, not the router.

thanks again,
dom

---

### Post by domee1 on 2009-09-24
well, i just can't seem to get an ip address via dhcp.

dhclient says "DHCPDISCOVER on eth0 255.255.255.255 port 67 interval 6" and several other intervals and in the end "No DHCPOFFERS received. 

dhcp should be activated by default according to the manual.

---

### Post by Bucky Ball on 2009-09-24
Are you sure the router is getting a WAN (internet) connection?

To get into the configuration of the router you should have an IP address for the router (probably found in the manual) which you can type into the address bar of your internet browser (probably Firefox). It should be something along the lines of:

192.168.0.1

... so you could type in the address bar:

[http://192.168.0.1](http://192.168.0.1)

You don't actually need the 'http://' bit.

... or similar. You need to check whether the router is set up as DHCP server and serving you an IP before you go any further with it.

You MUST know the IP of the router or you have no chance of knowing what it is doing or getting in there and configuring it. :)

The sure fire way is to get a cable, plug it into one of the LAN ports on the router, plug the other end into an ethernet port of the machine, forget about internet, just make sure you can put the IP in and communicate with the router from your local machine.

---

### Post by domee1 on 2009-09-24
hey Bucky Ball,

yes, i know the ip and i have tried to connect to the admin center several times with different interface settings (dhcp, static ip...). the problem is, that the router doesn't assign me an ip even though it should :)

>> the sure fire way is to get a cable and plug it into one of the LAN ports on the router and the ethernet port of the machine, forget about internet, and make sure you can put the IP in and communicate with the router.

that is exactly what i am trying to do. i am connected with a cable to a LAN port and i don't even have the modem connected to the router. i have also tried to access the router with my netbook (also jaunty)... same problem. still i don't think the problem is the router.

---

### Post by Bucky Ball on 2009-09-24
System->Admin->Network

'Enable Roaming' = off
ESSID and WEP or WPA security key to match what is in the router
'Configuration' = 'Auto - configuration (DHCP)

That is for dynamic obviously. You need to make sure you have settings right in the router. Is it set up as Access Point (AP)? It seems like router config to me but I could be wrong. Could you open a terminal (Applications->Accesssories) and paste this in:

```
iwconfig
```

Copy and paste the result here please.

---

### Post by issih on 2009-09-24
Two suggestions..
1) make doubley sure the router is turned on...obvious, but you never know.
2) use a static IP to log in and see what is going on.

Hope that helps

---

### Post by Iowan on 2009-09-24
I'll offer [this]("http://ubuntuforums.org/showthread.php?t=1156441") only because it solved my DHCP problem.
 Your mileage will (most likely) vary.

---

### Post by domee1 on 2009-09-25
Update: Okay, I connected my router to two different Windows computers today and the same problem occurred: No IP/access to the router even though DHCP should definitely be activated according to the manual (static IPs don't work either). I will return the router now, I'm not gonna bother with this **** any longer.

Thanks a lot for Your help and suggestions!
Dom

---

