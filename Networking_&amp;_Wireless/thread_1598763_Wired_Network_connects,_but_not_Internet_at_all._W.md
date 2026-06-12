---
title: "Wired Network connects, but not Internet at all. WiFi works. Wired works in Windows."
date: 2010-10-16
forum: Networking &amp; Wireless
---

### Post by GotWookiee on 2010-10-16
Due to lots of interference I recently switched my network connection from WiFi to cable. Currently my computer is connected to a gigabit D-Link router, which is then connected to a Netgear Powerline network adapter. The other Powerline network adapter is in my roommates bedroom, where it connects to his Linksys router. The linksys router connects to the cable modem.

Under Windows, this setup works fine. Under Linux, I can connect to the D-Link router just fine, via cable or wifi, but cannot reach anything beyond that.

After much searching I tried disabling ipv6. This did not help. I also tried changing my DNS servers to OpenDNS. I've also changed my MTU to 1200 from 1500 but this has not helped. I am unable to ping anything (even the ip address for google so it's not strictly a domain issue).

Also, in Windows I can ping my roommates Linksys router (and reach its configuration page) at 192.168.1.1, but I cannot do the same with the D-Link router (192.168.0.1).
Under Linux, it's exactly the opposite; I can reach the D-Link router but not the Linksys.

---

### Post by btindie on 2010-10-16
What sort of configuration are you using for your network? - static or DHCP? If you're using a static config then you'll also have to give your box the gateway address, this tells it who it must send packets to to reach other networks. To test this type ```
ip route show
``` if it's setup correctly then the last entry should look something like > **default** via 192.168.1.254 dev wlan0  proto static the IP address in your case may be different if it's there, the key part is that it's the **default** route. If it's not there then you need to assign a default gateway to your configuration. Can you ping the gateway?

---

### Post by GotWookiee on 2010-10-17
Thanks for replying. I'm using a static address.

Here is the output of ip route show when I am connected to the Linksys router via WiFi (working connection):
```
192.168.1.0/24 dev wlan0  proto kernel  scope link  src 192.168.1.102  metric 2 
169.254.0.0/16 dev wlan0  scope link  metric 1000 
default via 192.168.1.1 dev wlan0  proto static
```

Here is the output of ip route show when I am connected to my local router via my wired connection:
```
192.168.0.0/24 dev eth0  proto kernel  scope link  src 192.168.0.194  metric 1 
169.254.0.0/16 dev eth0  scope link  metric 1000 
default via 192.168.0.1 dev eth0  proto static
```

How do I give my box the gateway address? Is that the IP of my D-Link router or the Linksys router?

---

### Post by btindie on 2010-10-17
Let me see if I've got this right, when you connect via Ethernet your setup is as follows

[Linux Box] -> [D-Link Router] -> [Poweline Adapter] -> [Linksys Router] => {Internet}
  |           -------192.168.1.0/24 ----------------- + --------                                               192.168.0.0/24 ---|

What is the output of ```
ipconfig /all
``` under windows with an ethernet connection? If you're using static addressing are you using the same under both Linux and Windows?

I don't think the above will work as D-Link/Linksys routers aren't proper routers in the sense that a Cisco is. They have a built in SWITCH that will route between the LAN _ports_ and the WAN _port_, they don't route between LAN ports so with your current subnets it won't work. I suspect that under Windows you are using a 192.168.0.x address that your D-Link *router* is simply switching the packets and passing them to the Linksys Router.

Is DHCP enabled on the Linksys *router*? Then just reconfigure your box to use DHCP instead and it should work. In this case your D-Link *router* is acting as a switch to connect the two networks. You can manually assign an IP address to that (192.168.0.2 ?) so you can access it from the Linksys network, just make sure you disable DHCP on your D-Link to prevent any conflicts.

You could of course give your Linux box an IP address on both subnets (192.168.0.10 & 192.168.1.10) so you can access the web interfaces on both of the "*routers".*

To route between networks your router needs to IP addresses, one on each subnet. For example when an ADSL router connects to the internet it gets an IP address via DHCP from your ISP. This address is assigned to the WAN interface. You then also have the LAN interface which has your local IP address, this is assigned to the switch ports in your typical "home router" and NOT to an individual port as is more commonly done with enterprise class routers.

From the output you've provided I can see that both interfaces are correctly configured for the network they are on (wlan0 / eth0). In both cases they have a *default gateway *configured so if the rest of the network was configured correctly then it should work.
For the WLAN, your default gateway is 192.168.1.1. And for your LAN it's 192.168.0.1.
I suspect the problem is there's no route between the two networks. With the hardware you have there's nothing you can do other than to join the two networks.

I think if you were to do the following on your linux box, then you should be able to ping the Linksys
```
sudo ip addr flush dev eth0
sudo ip addr add 192.168.1.50/24 dev eth0
```If you then do ```
ping 192.168.1.1
``` do you get a response??

If the above is true then the following will get it working for you:

[LIST]
[*]Make sure DHCP is disabled on the D-Link so it doesn't cause problems with the Linksys
[*]Give eth0 on your Linux box an IP address in the 192.168.1.x subnet
[*]Use 192.168.1.1 as your gateway
[*]The DNS settings will be the same as for your WLAN connection
[/LIST]

---

### Post by GotWookiee on 2010-10-30
The above suggestions ended up working. Here is what I did:

[LIST=1]
[*]In Windows, I saved the output of "ipconfig /all" to a text file that I could access from Linux.
[*]I rebooted into Linux.
[*]In Linux, opened the Network Manager and edited the settings for my wired connection.
[*]On the IPv$ tab, I set the method to manual and created an IP address. I populated the different fields with my settings from Windows (the ipconfig /all txt file from earlier). I entered the IP address of the Linksys router as the Gateway and DNS IP's.
[*]I hit apply, closed the Network Manager and disconnected from the wired connection, then re-connected. Working like a charm now.
[/LIST]

Thanks.

---

