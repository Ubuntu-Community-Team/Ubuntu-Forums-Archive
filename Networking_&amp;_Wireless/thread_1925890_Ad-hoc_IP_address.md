---
title: "Ad-hoc IP address"
date: 2012-02-15
forum: Networking &amp; Wireless
---

### Post by MrQuincle on 2012-02-15
Dear forum members,

I do have a robot (Surveyor) which sets up an access point, designing to itself a static IP address. I do not know which IP address that is, but I assume it is 169.254.0.10. However, if I ping it I don't get any response (which I should).

I scan the network:
```
Cell 16 - Address: 02:28:18:81:1E:7C
Channel:11
Frequency:2.462 GHz (Channel 11)
Quality=67/70  Signal level=-43 dBm  
Encryption key:off
ESSID:"SRV2"
Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
          36 Mb/s; 48 Mb/s; 54 Mb/s
Mode:Ad-Hoc
Extra:tsf=000000000076c394
Extra: Last beacon: 268ms ago
IE: Unknown: 000453525632
IE: Unknown: 010482848B96
IE: Unknown: 03010B
IE: Unknown: 06020100
IE: Unknown: 2A0100
IE: Unknown: 32080C1218243048606C

```

I see that there is the Surveyor, SSID srv2, and MAC address 02:28:18:81:1E:7C

```

export ESSID=SRV2
sudo ifconfig wlan0 down
sudo iwconfig wlan0 key off
sudo iwconfig wlan0 essid "$ESSID" mode Ad-Hoc channel 11
sudo ifconfig wlan0 169.254.0.1

```
I assign myself a static ip address in the same net. And I subsequently ping the thing:

ping 169.254.0.10

Regretfully I see this does not work out so well:
```

sudo tcpdump -ennqti wlan0
tcpdump: verbose output suppressed, use -v or -vv for full protocol decode
listening on wlan0, link-type EN10MB (Ethernet), capture size 65535 bytes
1c:4b6:5a:98:1d > 00:20:4a:c0:bb:59, IPv4, length 98: 169.254.0.1 > 169.254.0.10: ICMP echo request, id 4837, seq 1, length 64
1c:4b6:5a:98:1d > 00:20:4a:c0:bb:59, IPv4, length 98: 169.254.0.1 > 169.254.0.10: ICMP echo request, id 4837, seq 2, length 64
1c:4b6:5a:98:1d > 00:20:4a:c0:bb:59, ARP, length 42: Request who-has 169.254.0.10 tell 169.254.0.1, length 28
1c:4b6:5a:98:1d > 00:20:4a:c0:bb:59, ARP, length 42: Request who-has 169.254.0.10 tell 169.254.0.1, length 28
1c:4b6:5a:98:1d > 00:20:4a:c0:bb:59, ARP, length 42: Request who-has 169.254.0.10 tell 169.254.0.1, length 28

```

The only thing that rarely(!!!) happens is this:
```

00:20:4a:c0:bb:59 > ff:ff:ff:ff:ff:ff, ARP, length 42: Request who-has 169.254.0.10 tell 169.254.0.10, length 28

```
Apparently the thing sends something out, but asks for it's own IP address. What is happening here?! Can it be the case that it does have a totally different IP address and still sending this ARP packet out? It does not seem to come with a DHCP request by the way, so that's not the thing. Any pointers will be appreciated!

---

### Post by SeijiSensei on 2012-02-15
Maybe it has a firewall that blocks pings?

---

### Post by MrQuincle on 2012-02-16
> **SeijiSensei said:**
> Maybe it has a firewall that blocks pings?

I do (also) arpings, and no, it doesn't have a firewall.

---

### Post by Perkins on 2012-02-21
You might try using nmap to scan the thing and see if there are any open ports anywhere.  If not then try scanning the entire network and see if maybe it answers up on a different address.  Otherwise is there a link to the robot's documentation?  There might be a secret handshake.

---

