---
title: "Can't configure new router"
date: 2010-08-27
forum: Networking &amp; Wireless
---

### Post by jordon on 2010-08-27
I just got a new wireless router (Asus WL-520GC). I can connect to the Internet, but I can't access 192.168.1.1 to configure the router (this is the correct address, according to the manual). It doesn't respond to a ping either.

```
$ ping -c4 192.168.1.1
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.

--- 192.168.1.1 ping statistics ---
4 packets transmitted, 0 received, 100% packet loss, time 3022ms
```

---

### Post by Iowan on 2010-08-27
What address does your machine get? Also, does the router have a wired port you might try?

---

### Post by jordon on 2010-08-27
> **Iowan said:**
> What address does your machine get?

I still don't know how to figure that out. I've done some Googling and apparently ifconfig will tell you, but I can't pick out anything that makes sense.

```
$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:19:b9:77:27:f8  
          inet6 addr: fec0::b:219:b9ff:fe77:27f8/64 Scope:Site
          inet6 addr: 2002:42fd:876a:b:219:b9ff:fe77:27f8/64 Scope:Global
          inet6 addr: fe80::219:b9ff:fe77:27f8/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:319460 errors:0 dropped:0 overruns:0 frame:0
          TX packets:344128 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:127417123 (127.4 MB)  TX bytes:391616312 (391.6 MB)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1328 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1328 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:118120 (118.1 KB)  TX bytes:118120 (118.1 KB)

wlan0     Link encap:Ethernet  HWaddr 00:1b:77:5f:f3:93  
          inet addr:66.253.132.165  Bcast:66.253.135.255  Mask:255.255.252.0
          inet6 addr: fe80::21b:77ff:fe5f:f393/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:72910 errors:0 dropped:0 overruns:0 frame:0
          TX packets:69853 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:26574994 (26.5 MB)  TX bytes:73710352 (73.7 MB)
```

> **Iowan said:**
> Also, does the router have a wired port you might try?

It does, but I don't want to use it if I don't have to.

---

### Post by Iowan on 2010-08-27
Wow, I'm not familiar with IPv6, so I'm not sure how to interpret that...> **jordon said:**
> It does, but I don't want to use it if I don't have to.Reason I ask - some routers seem a bit more lenient on a LAN connection than an external... But, I'd think the router would respond to a ping - even if it wouldn't accept an HTTP connection...

---

### Post by BkkBonanza on 2010-08-27
You're using the wifi right? So wlan0 is your wifi interface.
It reports an IP of 66.253.132.165.
That isn't a private LAN address so presumably it's not getting that from your router.
Well, it doesn't look right anyway. It looks like a public IP.
Are you sure you're acquiring a wifi connection with the right device, your router?

Typically on a LAN you would be using an address range like 192.168.* or 10.0.*

---

### Post by jordon on 2010-08-28
I'm definitely using the Wi-Fi. I only have one network cable, and it's plugged into the router.

I hadn't rebooted my computer since I first tried to set up the router, so I thought I would try that.

After a reboot, I had the opposite problem. I was *only* able to access 192.168.1.1 and *not* the web in general:

```
$ ifconfig 
eth0      Link encap:Ethernet  HWaddr 00:19:b9:77:27:f8  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:160 errors:0 dropped:0 overruns:0 frame:0
          TX packets:160 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:12160 (12.1 KB)  TX bytes:12160 (12.1 KB)

wlan0     Link encap:Ethernet  HWaddr 00:1b:77:5f:f3:93  
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21b:77ff:fe5f:f393/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:840 errors:0 dropped:0 overruns:0 frame:0
          TX packets:319 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:100529 (100.5 KB)  TX bytes:33308 (33.3 KB)

$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     2      0        0 wlan0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlan0
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 wlan0
```

I rebooted again, and the situation was the same as it was the first time. I could access everything but 192.168.1.1. The output of ifconfig was the same as in my previous post.

I rebooted yet again, and I could only access 192.168.1.1; I got the same results as above.

Weird...

---

### Post by psavva on 2010-08-28
Firstly, lets make sure you've got everything plugged in right.

From the output you provided, it does actually look like you're connected to another Wifi network.

Step 1) 
Ensure you Disable you Wifi Connection.
Right click on the Network Icon, and uncheck "Enable Wireless"

Step 2) 
You should have a network cable connected between your Computer and Your Router.

Make sure it's connected, and check that you have an ip address which is supplied by your router.  You can see this by Right Clicking on the Network Icon, and choosing Connection Information.

Enter the IP Address as is given to you in the "Default Route" into your web browser.  Your router should come up.

Once this is done, open your manual, and configure WIFI, with security. I suggest WPA2. Ensure you set a SSID (Network Name) that you recognise. Used in step 4

Step  3)
Enable your wireless connection. See Step 2 how you disabled it :)

Step 4) Ensure you are connecting to the right network. You will be identify the SSID in the "Available Networks" List if you left click on the Network Icon in Ubuntu.

Good Luck!

P.S. Also check your internet connectivity via your modem. Ensure the cables are attached as per your router manual.

---

### Post by jordon on 2010-08-28
I did some Googling (I know, a little Googling is a dangerous thing) and entered the command "sudo ifconfig wlan0 192.168.1.1 netmask 255.255.255.0". I thought this was the solution to my problem, but it apparently caused the router to block all traffic except that to 192.168.1.1. So then I was able to configure my router with a custom SSID and encryption (needless to say, I just breezed through the quick setup since I don't know what I'm doing). Then I rebooted my computer, and I could again connect to everything except 192.168.1.1. In other words, the problem wasn't really solved. I want to be able to connect to both at the same time.

> **psavva said:**
> From the output you provided, it does actually look like you're connected to another Wifi network.

So I'm pretty sure I'm connected to the right network. It's the one with the name I made up, and to connect to it I had to enter the password that I came up with.

> **psavva said:**
> You should have a network cable connected between your Computer and Your Router.

Do I just need to do that to set this up? Otherwise it defeats the purpose of having Wi-Fi.

> **psavva said:**
> Also check your internet connectivity via your modem. Ensure the cables are attached as per your router manual.

I don't have a modem. I just connect to the Internet through the wall. Could this be part of the problem? My router is plugged in to the Ethernet jack, and then with my computer I connect wirelessly to the router.

The manual has two illustrations of connections. One is router->computer, the other is Ethernet jack->modem->router->computer. Neither of them is Ethernet jack->router, with the computer not physically attached, but that's the setup that actually makes sense to me. (I guess the actual modem is somewhere else, so it's really like the second one, but I'm not sure.)

---

### Post by BkkBonanza on 2010-08-28
Be sure you have correct connections on your router.
There will be two sides: WAN and LAN. Often you will have 4 LAN ports but there can be just one sometimes.
The "wall/internet" jack needs to connect to the WAN port.
Using wifi is equivalent to connecting your computer to the LAN side.

Some routers have an ADSL port and no WAN port. In that case you cannot use it with an ethernet "wall" connection as the WAN side is direct ADSL.

If by chance the "wall" connects to the LAN side you will have issues and it may somehow cause your ISP to incorrectly assign an IP directly across your LAN/wifi.

The router WAN side talks to your ISP and gets a public IP (which kind of looks like the IP that apparently your wlan0 shows, but shouldn't).

The LAN/wifi side is handled by the router and it should generate IPs in the private IP space - typically 192.168.*

If you have misconfigured some settings in the router it may be getting confused and not setting IP values correctly such that you will have problems with addressing.

---

### Post by jmore9 on 2010-08-28
What kind of internet connection do you have ?  Who is your ISP ?

---

### Post by jordon on 2010-08-29
> **BkkBonaza said:**
> The "wall/internet" jack needs to connect to the WAN port.
Using wifi is equivalent to connecting your computer to the LAN side.

Thanks! I had a cable going from the jack to a LAN port. I switched it to the WAN port, and... problem solved.

Well, I won't make that mistake again, and I learned a thing or two on the way.

---

