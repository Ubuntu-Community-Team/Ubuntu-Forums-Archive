---
title: "How to have both wired and wireless connection at the same time?"
date: 2009-03-11
forum: Networking &amp; Wireless
---

### Post by gardara on 2009-03-11
Is it possible to have two seperate connections at the same time?
I have my laptop and my fileserver connected to a switch, I want to use it for local file transferring over nfs but want to use a wifi connection for the internet.

When I connect my ethernet cable in, the wireless network seems to get disabled.... It is connected, but seems not to be active.

This must be possible somehow, but the question is how?

---

### Post by theozzlives on 2009-03-11
I'm not sure you can, I don't think NM will let you do it.

---

### Post by Helgiks on 2009-03-11
You could make iptables (or something else) block all traffic except from your file-server through that specific interface, that might solve your problem if you don't find anything else.

---

### Post by netztier on 2009-03-12
> **theozzlives said:**
> I'm not sure you can, I don't think NM will let you do it.

Yes it does, and no it doesn't, and yet it does :-)

NM versions from NM 0.7 and onwards allow for multiple connections being active at the same time.

The problem comes with this: DHCP servers nearly always assign a default gateway to be used with that connection. 

Now what should NM do when both the WiFi card and the wired NIC learn IP address, subnet mask and default gateway? Which default route should get the preference, i.e., which one should make it into the routing table? 

What the NM people have come up with is this: based on the speed of a connection, the give preference to the default route of the fastest connection. This normally results in the following order: wired - wireless - mobile broadband-(modem)

If that is not what suits your needs, you can for example make sure that your LAN's DHCP server does not advertise a default gateway - and on your local NM, the default gateway learnt via DHCP-on-WiFi will get preference.

Alternatively, you could give your wired NIC a static configuration, but *whithout* default gateway; so you'll get a routing table entry for the wired subnet, but the WiFi-learnt default route stays in the table.

All of this discussion is moot, by the way, if WiFi and wired network are the same subnet and have addresses from the same address range of the DHCP server in question (as it would be the case with the common broadband home router). Then the answer to the OP's question should be: why bother? Why split local traffic from internet-traffic when everything will cross the same broadband router box, anyway?

regards

Marc

---

### Post by gardara on 2009-03-12
Thanks for the reply netztier... I will have a look at your tips when I get home....
But to reply your question...
```
Then the answer to the OP's question should be: why bother? Why split local traffic from internet-traffic when everything will cross the same broadband router box, anyway?
```

I am using a gigabit switch that's just connected to my server and my laptop.... The a wifi connection doesn't touch the switch....

This brings me a thought... Couldn't I just assign a different IP range to the switch?

---

### Post by netztier on 2009-03-12
> **gardara said:**
> 
This brings me a thought... Couldn't I just assign a different IP range to the switch?

Exactly: give the wired LAN an IP range of it's own, and make sure it's a different one than your WiFi uses, and make sure that you don't have a default gateway on that LAN itself - and you have a good start.

So I would create a Profile for a wired network in NetworkManager (right-klick, then "Edit Connections", select the "Wired" tab and "add" a profile) with a static IP address or "DHCP (Addresses only)" if you have a DHCP server running on that LAN, but don'w want to learn the default gateway from it.

Be sure to check the ouptput of netstat -nr after setting this up, so you can see where your default route (destination 0.0.0.0) is pointing to:

```
user@host:~$ **netstat -nr**
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
172.20.125.0    0.0.0.0         255.255.255.0   U         0 0          0 wlan0
169.254.0.0     0.0.0.0         255.255.0.0     U         0 0          0 wlan0
[COLOR="Red"]0.0.0.0         172.20.125.1    0.0.0.0         UG        0 0          0 wlan0
[/COLOR]
```

By creating a new "wired" profile, you can still easily switch to a standard DHCP-enabled setting when you're in another environment.

regards

Marc

---

