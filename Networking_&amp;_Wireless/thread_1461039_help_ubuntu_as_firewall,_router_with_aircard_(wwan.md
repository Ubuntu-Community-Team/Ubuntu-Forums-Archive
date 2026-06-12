---
title: "help: ubuntu as firewall, router with aircard (wwan)"
date: 2010-04-23
forum: Networking &amp; Wireless
---

### Post by senor_smile on 2010-04-23
I have seen tutorials on setting up a secured firewall/router/gateway using ubuntu server as the platform.  However, I am wondering if anyone has had experience with using an aircard (wireless broadband card via usb) to set up a router.  

Which card do you recommend?  Any precautions?  Any specific code already written to automatically recognize mobile broadband cards and restart the connection if it goes stale?

Thanks in advance!

---

### Post by computer13137 on 2010-04-23
I've never gotten a computer to act as a wireless access point.  I haven't had the time to experiment with it, nor the proper hardware.

Here's the short and sweet.  Your WiFi card has to support "master" or "access point" mode as far as I know.  It might be helpful if you posted your WiFi card's model number instead of just saying something general like you have said.

That said, if your WiFi card supports master mode, all you need to do is setup a broadcast ssid from the network card, bridge it with eth1, (eth1+wlan0 = br0) then route packets from eth0 to br0 for your Internet connection. 

It sounds simple. I do it for eth0 to eth1, but I've never done WiFi.  I just have a Linksys WAP54G plugged in next to my server that takes care of that for me. 

Cheers,
Kirk

---

### Post by senor_smile on 2010-04-24
> **computer13137 said:**
> I've never gotten a computer to act as a wireless access point.  I haven't had the time to experiment with it, nor the proper hardware.

Here's the short and sweet.  Your WiFi card has to support "master" or "access point" mode as far as I know.  It might be helpful if you posted your WiFi card's model number instead of just saying something general like you have said.

That said, if your WiFi card supports master mode, all you need to do is setup a broadcast ssid from the network card, bridge it with eth1, (eth1+wlan0 = br0) then route packets from eth0 to br0 for your Internet connection. 

It sounds simple. I do it for eth0 to eth1, but I've never done WiFi.  I just have a Linksys WAP54G plugged in next to my server that takes care of that for me. 

Cheers,
Kirk

I am not actually trying to figure out how to use an existing wireless card to broadcast out, but to use an aircard from somewhere like verizon or t-mobile on the wan side (it would technically be considered wwan=wireless wide area network).  I have gotten one to work one the command line with a lot of effort, but I am looking for some more automation to make the card automatically connect when inserted, and restart the connection if and when it goes stale.

---

### Post by computer13137 on 2010-04-24
> **senor_smile said:**
> I am not actually trying to figure out how to use an existing wireless card to broadcast out, but to use an aircard from somewhere like verizon or t-mobile on the wan side (it would technically be considered wwan=wireless wide area network).  I have gotten one to work one the command line with a lot of effort, but I am looking for some more automation to make the card automatically connect when inserted, and restart the connection if and when it goes stale.

Oh, so that's what you meant by aircard. I thought it was a WiFi card made by Apple or something. Maybe I'm thinking of the Airport.

Sadly, I don't have any experience with cellular broadband whatsoever, as obvious by my lack of knowledge on the vocabulary involved...  

If the cellular card creates an interface (such as eth1, wlan0, etc, I'm not sure what the prefix would be but if it shows up in ifconfig) then it should be a fairly simple matter to turn your computer into a router so other computers can use this WAN connection.  You may find an adaptation of this tutorial to be helpful: [http://www.yolinux.com/TUTORIALS/LinuxTutorialIptablesNetworkGateway.html](http://www.yolinux.com/TUTORIALS/LinuxTutorialIptablesNetworkGateway.html)

As for automatically connecting to your cellular Internet, I am absolutely useless to you.  I've never used cellular broadband.  But if you need help with the Interface to Interface gateway tutorial above there, I can certainly help you with that.

Cheers,
Kirk

---

### Post by senor_smile on 2010-04-24
> **computer13137 said:**
> Oh, so that's what you meant by aircard. I thought it was a WiFi card made by Apple or something. Maybe I'm thinking of the Airport.

Sadly, I don't have any experience with cellular broadband whatsoever, as obvious by my lack of knowledge on the vocabulary involved...  

If the cellular card creates an interface (such as eth1, wlan0, etc, I'm not sure what the prefix would be but if it shows up in ifconfig) then it should be a fairly simple matter to turn your computer into a router so other computers can use this WAN connection.  You may find an adaptation of this tutorial to be helpful: [http://www.yolinux.com/TUTORIALS/LinuxTutorialIptablesNetworkGateway.html](http://www.yolinux.com/TUTORIALS/LinuxTutorialIptablesNetworkGateway.html)

As for automatically connecting to your cellular Internet, I am absolutely useless to you.  I've never used cellular broadband.  But if you need help with the Interface to Interface gateway tutorial above there, I can certainly help you with that.

Cheers,
Kirk

Ah, thanks for the link.  I will add it to my resources for the project.  I am actually hoping to utilize shorewall for the SPI and port forwarding instead of iptables directly.  There just seems sooo much to learning iptables, and shorewall seems to make it much easier while keeping it powerful.  At least that's what I have picked up on from my reading.  I am still quite in the learning/designing phase for this as I've never worked with low level router type commands to this degree.

---

### Post by computer13137 on 2010-04-24
I'm not familiar with ShoreWall, but my router is only like a twenty line shell script and mostly spaces and comments... :\

```
# Clear old iptables rules.
iptables --flush
iptables --table nat --flush
iptables --delete-chain
iptables --table nat --delete-chain

# Setup the router.
# Internet: eth0
# LAN: eth2
iptables --table nat --append POSTROUTING --out-interface eth0 -j MASQUERADE
iptables --append FORWARD --in-interface eth2 -j ACCEPT

# Enable packet forwarding in the kernel.
echo 1 > /proc/sys/net/ipv4/ip_forward

# Run port forwarding script.
/root/router/ports.sh
```And then to forward a port:
> iptables -t nat -A PREROUTING -i eth0 -p **tcp** --dport **1111** -j DNAT --to **LAN_IP**:**1111**"tcp" can also be udp if you want to forward a udp port. 
Replace 1111 with the port you want to forward.
Replace LAN_IP with a valid local IP.  (10.1.5.3, 192.168.1.23, etc.)

Cheers,
Kirk

---

### Post by senor_smile on 2010-04-24
> **computer13137 said:**
> I'm not familiar with ShoreWall, but my router is only like a twenty line shell script and mostly spaces and comments... :\

```
# Clear old iptables rules.
iptables --flush
iptables --table nat --flush
iptables --delete-chain
iptables --table nat --delete-chain

# Setup the router.
# Internet: eth0
# LAN: eth2
iptables --table nat --append POSTROUTING --out-interface eth0 -j MASQUERADE
iptables --append FORWARD --in-interface eth2 -j ACCEPT

# Enable packet forwarding in the kernel.
echo 1 > /proc/sys/net/ipv4/ip_forward

# Run port forwarding script.
/root/router/ports.sh
```And then to forward a port:
"tcp" can also be udp if you want to forward a udp port. 
Replace 1111 with the port you want to forward.
Replace LAN_IP with a valid local IP.  (10.1.5.3, 192.168.1.23, etc.)

Cheers,
Kirk

That seems simple enough.  Would you post the content of your port forwarding script too?

---

### Post by computer13137 on 2010-04-24
> **senor_smile said:**
> That seems simple enough.  Would you post the content of your port forwarding script too?

I did.  It's just a ton of those lines.  One for every port I want to forward.

I just run that on startup.  I know there's a way to save your iptables rules too, but I find the startup script works just fine. 

Plus, this way, I can run that script while the system is live, and it will clear my port forward rules and apply new ones without any disconnections.  This is helpful as I run an IRC server and other local services I wouldn't want to see disconnected by a "router reboot" like those old Linksys boxes loved to do. 

Cheers,
Kirk

---

### Post by computer13137 on 2010-04-24
I should also note that for a fully functional network, you will want to assign your LAN interface a static IP address, and operate a DHCP server on your Linux box.

If you want a local DNS server, BIND can take care of that for you.

Cheers,
Kirk

---

