---
title: "My newly Ubuntu'ed desktop gets turfed off the wifi by my XP laptop!"
date: 2009-02-06
forum: Networking &amp; Wireless
---

### Post by Scubdup on 2009-02-06
I'm playing with Ubuntu like a child with a new toy and I was very impressed it had not probs with the wifi and connected to the internet very easily.

Then the missus wants to use my newly freed up laptop for surfing and it would appear the laptop (running XP) turfs my machine off the wifi.

The connection is still there but no pages load.

Any explainations?

The laptop has internal wifi card. The ubuntu desktop is using a USB wifi dongle. The router is a Huawei Echolife 520.

I have been through the router settings and cannot see anything immediately obvious as wrong.

Thanks for any help.

---

### Post by ozbuntu01 on 2009-02-06
Hi scubdup ,

Im a newbie to ubuntu also :D

............................................................................

What brand/models are your Wireless Adapters ?

What version of Ubuntu are you using ?

What are the security settings on your network ?

Are you using Automatic DHCP or manual configurations ?

Is your USB dongle Wireless Adapter Mac Address added into your router ?

When your Ubuntu machine only, is connected to the internet with your USB Adapter , does your router read the device as "attatched" ? (You should have a option to view all the Wireless Adapters Devices that are connected to your router somewhere in your router settings)
..........................................................................

Please also type the outputs of the following terminal commands:

```
 ifconfig 
```

&

```
 iwconfig 
```
...........................................................................

This info should help us a bit more :)

---

### Post by da mono on 2009-02-06
are the devices using the same ip ?? or probably named the same ???  have u tried surfing when your xp machine is surfing a mean start up your xp machine and the your ubuntu machine ???

---

### Post by Scubdup on 2009-02-07
Thanks a lot for helping, guys.

> **ozbuntu01 said:**
> What brand/models are your Wireless Adapters?The XP laptop is an old HP n6125x with "built in Wi-Fi, natch. The controller is from Broadcom and supports the 802.11 b and g standards" - that is all I can find for the moment.

The Ubuntu desktop is using a Netgear WG111 54 Mbps Wireless USB 2.0 Adapter.
> **ozbuntu01 said:**
> What version of Ubuntu are you using ?
Ubuntu 8.10 (Intrepid Ibex)
> **ozbuntu01 said:**
> What are the security settings on your network?Unsure what info you want/need here. Sorry - new to networking as well, I'm afraid. The network is broadcast SSID, with WEP. Let me know what additional info would be useful.
> **ozbuntu01 said:**
> Are you using Automatic DHCP or manual configurations?As far as I'm aware I'm using the default router settings.

The DHCP table is now (while the laptop is off) showing two different Host Names, IP Addresses, and MAC Addresses. The host names look like the names I gave each computer when I first set them up (but I could wrong about the lappy - need to check).

> **ozbuntu01 said:**
> Is your USB dongle Wireless Adapter Mac Address added into your router?Not sure. How do I check? Under Wireless Lan settings it says "Wireless MAC Address Filter disabled"

> **ozbuntu01 said:**
> When your Ubuntu machine only, is connected to the internet with your USB Adapter , does your router read the device as "attatched" ? (You should have a option to view all the Wireless Adapters Devices that are connected to your router somewhere in your router settings)Sorry. Can't find this anywhere.

> **ozbuntu01 said:**
> Please also type the outputs of the following terminal commands:

```
 ifconfig 
```
eth0      Link encap:Ethernet  HWaddr 00:12:3f:9c:4d:a9  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:1b:2f:cd:7b:c0  
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21b:2fff:fecd:7bc0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:15631 errors:0 dropped:0 overruns:0 frame:0
          TX packets:15794 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:7199169 (7.1 MB)  TX bytes:2016060 (2.0 MB)

wmaster0  Link encap:UNSPEC  HWaddr 00-1B-2F-CD-7B-C0-62-63-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
> **ozbuntu01 said:**
> &

```
 iwconfig 
```lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"TalkTalkc2c6k"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:1B:9E:97:47:A8   
          Bit Rate=54 Mb/s   Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality=72/100  Signal level:-35 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

---

### Post by ozbuntu01 on 2009-02-07
@ scubdup ,

Interesting.

I cannot really think of anything else at the moment. Even by looking at your info.

Your network card/computer ip address for your Ubuntu machine is: inet addr:192.168.1.2

Your windows machine should have a similar network card/computer ip address as your ubuntu (But NOT the same) (eg. Windows 192.168.1.3  Ubuntu 192.168.1.2 etc...)

Your route gateway address should most likely be 192.168.1.1

............................................................................

Are you sure it is the "Windows" machine kicking your ubunutu internet ??? (Connect Ubuntu only machine and leave it & see if it disconnects)

Are you sure you have entered the WEP key into Ubuntu ? (To be sure right click Ubuntu Network Manager , "edit Connection" and edit your wireless connection , Check that the WEP password is stored under "Security" tab.

As far as I know the Netgear USB Adapters can be a bit of a pain to get working.

Have you tried updating Ubuntu ?

---

### Post by Scubdup on 2009-02-07
> **ozbuntu01 said:**
> @ scubdup ,

Interesting.

I cannot really think of anything else at the moment. Even by looking at your info.Thanks Oz. In a way that's reassuring because I was worried I was being inept with a trivial problem.

> **ozbuntu01 said:**
> Your network card/computer ip address for your Ubuntu machine is: inet addr:192.168.1.2

Your windows machine should have the same network card/computer ip address as your ubuntu , if not very similar (eg. 192.168.1.3 etc...)You are right. That's what it comes up with in the router's DHCP admin page. (Although I am sure [and yet can't repeat] I have seen the DHCP page show two addresses for the XP machine)

> **ozbuntu01 said:**
> Your route gateway address should most likely be 192.168.1.1Again correct. This is the address I type in to access the router settings.

> **ozbuntu01 said:**
> Are you sure it is the "Windows" machine kicking your ubunutu internet ??? (Connect Ubuntu only machine and leave it & see if it disconnects)Yeah. The only way for me to play happily on the Ubuntu machine is to keep the XP laptop off. Then it has no problems.

> **ozbuntu01 said:**
> Are you sure you have entered the WEP key into Ubuntu ? (To be sure right click Ubuntu Network Manager , "edit Connection" and edit your wireless connection , Check that the WEP password is stored under "Security" tab.

As far as I know the Netgear USB Adapters can be a bit of a pain to get working.

Have you tried updating Ubuntu ?Pretty sure the WEP's enetered - it's connecting after all. Ubuntu's up to date too, according to Update Manager.

All in all, it's a bit of a conundrum.

---

### Post by ugm6hr on 2009-02-07
What IP is the XP laptop assigned?

Did you set a static IP for the XP laptop?

If you connect the XP laptop first, and *then* turn on the Ubuntu desktop, do they both stay connected?

I wonder whether your router has a predefined IP for your XP laptop (or even Ubuntu desktop) based on MAC address, so the XP laptop connects with the same IP as Ubuntu; hence one kicks the other off.

---

### Post by Scubdup on 2009-02-08
Hi Ugm6hr, thanks for showing an interest too.

> **ugm6hr said:**
> What IP is the XP laptop assigned?In the DHCP settings (screenshot attached) the computers have been assigned the following:-

Host Name 	 IP Address 	 MAC Address
sam-desktop 	192.168.1.2 	00-1B-2F-CD-7B-C0
sam-c91e6dc3503 	192.168.1.3 	00-90-4B-F6-34-58 

(Not by me, it must have been automatic. Having said that, I'm puzzled why the old laptop's been assigned 3 while the more recently configured Ubuntu machine has been assigned 2...)

[QUOTE=ugm6hr;6695432]Did you set a static IP for the XP laptop?/quote]
I hadn't but I have now, with possibly interesting results.

I manually assigned the XP laptop the 192.168.1.3 IP.

Now it shows the same sort of symptoms as the ubuntu machine used to exhibit.

It says it is connected to the wifi but cannot access any webpages.

The Ubuntu machine, meanwhile, is absolutely fine and is no longer losing connection.

EDIT: Spoke too soon. Ubuntu machine kicked out (or possibly squeezed out, maybe there's a veeeeeery slow connection there) after about 30 mins.

---

### Post by ugm6hr on 2009-02-08
I'm afraid this situation is a bit beyond my networking knowledge.

Perhaps this is a problem with the router?  Although managing 2 connections should not be difficult.

Or maybe this is a DNS resolution issue?  If both computers are now "connected" to the router, but only 1 can access the web.

Try going here with the XP computer: [http://208.67.219.101/](http://208.67.219.101/)

---

### Post by ozbuntu01 on 2009-02-08
This situation is far beyond my networking knowledge also.

But I have a few more suggestions in mind, which are:

1) Have you read the original Router Documentations/Manuals ??? (There might be some valuable information in there.)

2) Have you tried google'ing your Router Brand/Model for "How to manage 2 internet connections" ???

3) If all else fails, maybe consider purchasing a new Router as it would save alot of hassles if you cannot find a solution.

........................................................................................


(Correcting a mistake in one of my previous posts.) Your windows machine should have a similar network card/computer ip address as your Ubuntu machine (But **_NOT_** the same) (eg. Ubuntu 192.168.1.2  Windows 192.168.1.3 etc...)

Try setting DHCP Manually for both machines. Ensuring the network card/computer ip addresses are NOT the same as each other.

---

### Post by da mono on 2009-02-08
> **Scubdup said:**
> Hi Ugm6hr, thanks for showing an interest too.

In the DHCP settings (screenshot attached) the computers have been assigned the following:-

Host Name      IP Address      MAC Address
sam-desktop     192.168.1.2     00-1B-2F-CD-7B-C0
sam-c91e6dc3503     192.168.1.3     00-90-4B-F6-34-58 

(Not by me, it must have been automatic. Having said that, I'm puzzled why the old laptop's been assigned 3 while the more recently configured Ubuntu machine has been assigned 2...)

[quote=ugm6hr;6695432]Did you set a static IP for the XP laptop?/quote]
I hadn't but I have now, with possibly interesting results.

I manually assigned the XP laptop the 192.168.1.3 IP.

Now it shows the same sort of symptoms as the ubuntu machine used to exhibit.

It says it is connected to the wifi but cannot access any webpages.

The Ubuntu machine, meanwhile, is absolutely fine and is no longer losing connection.

EDIT: Spoke too soon. Ubuntu machine kicked out (or possibly squeezed out, maybe there's a veeeeeery slow connection there) after about 30 mins.

ok in your router reduce you dhcp ip pool to 10
then change tour starting dhcp pool to 192.168.1.100
and finally change your lease time to 1 day after that reboot the router

i hope it helps

---

### Post by Scubdup on 2009-02-11
I'm going to give this a try tonight, da mono. Thanks for the suggestion. I'll let you know how I get on.

I've switched the laptop off, and I'm still having connection problems, although they are less frequent.

I still get disconnected at random points, and then I have to restart the machine before I can connect again.

Before restarting, if I try to connect sometimes network manager waits indefinitely for a network address from the router or asks for my password. If I put the password in, it still doesn't connect.

If da mono's solution doesn't work, then I think I'm going to download and install Ubuntu 8.04 and see if it's a bit more predictable.

---

### Post by Scubdup on 2009-02-18
A (very unscientific) update.

The problem seemed to improve in the last two days, but then a new wireless dongle made by Edimax (£12 from Amazon.co.uk) arrived, I switched to that and so far the problem has not manifested itself again.

I opted for the Edimax after a fair bit of research into Ubuntu friendly USB wifi dongles. Edimax seem keen to cater for the Linux community.

I will use the Edimax for a while and then revert to the Netgear to try and confirm the problem lies with the Netgear dongle.

---

