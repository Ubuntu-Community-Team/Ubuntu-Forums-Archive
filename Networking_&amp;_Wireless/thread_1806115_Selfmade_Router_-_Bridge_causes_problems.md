---
title: "Selfmade Router - Bridge causes problems?"
date: 2011-07-17
forum: Networking &amp; Wireless
---

### Post by SeaKing on 2011-07-17
I've set up an own Ubuntu Router using an embedded system board and an wireless card.
First the network setup:
--Internet->-Router1 delivered by the provider (has DHCP and DNS services running)->-networkrange 192.168.1.x ->-Selfmade Ubuntu Router  (has also DHCP and DNS services running)->- networkrange 192.168.10.x

for this project I usesd the documentation [Router ]("https://help.ubuntu.com/community/Router")on the Ubuntu help webside.

The hardware:
base: embedded board with 2 LAN interfaces by VIA
wireless lan card: TP-LINK TL-WN861N with  Atheros 9220 chipset and ath9k driver running under hostapd

Now the Problems are:
I lose connetion to the internet with the computers behind the Ubuntu router frequently (every 10 minutes). But after a second they get it back. Another problem is that i cannot ping the ubuntu router from the computers behind, but pinging the router from the network(192.168.1.x) before it's poassible. 
The ping also have an other problem, if I ping google.com for example I get 13 responses with a time of about 30ms then I get exact 4 responses with a ping >150ms and after this 4 high once I get 13 normal and then again exact 4 responses with a very high ping and so on til the connection aborts.

Is the bridge the problem? If I just use wired connections, without any wireless service and bridge it works quite well.

---

### Post by jmoorse on 2011-07-17
It sounds like wireless is the issue, however it may be something like channel contention.  What channel do you have set?  What segment is wifi used on?  192.168.1.0/24 or 192.168.10.0/24?

I had a similar set of problems a few years back: there was a tree branch blowing back and forth in front of a enterprise wireless bridge causing horrible variable latency...very odd :)

---

### Post by SeaKing on 2011-07-17
I set it to channel 6. The segment, well, what do you mean, the firewallscript is adoped from the tutorial:

# External (Internet-facing) interface 
EXTIF="eth0"  
# External IP address (automatically detected) 
EXTIP=$(/sbin/ip addr show dev "$EXTIF" | perl -lne 'if(/inet (\S+)/){print$1;last}');   
# Internal interface 
INTIF="br0"  
# Internal IP address (in CIDR notation) 
INTIP="192.168.0.1/32"  
# Internal network address (in CIDR notation) 
INTNET="192.168.0.0/24"

---

### Post by jmoorse on 2011-07-17
Try channel 1 or 11 just to test.

I am asking if it is like this:

Internet <> Router1 <wireless> Selfmade router <wired>

Or like this

Internet <> Router1 <wired> Selfmade router <wireless>

---

### Post by SeaKing on 2011-07-17
OK yes is it like this:

Internet <> Router1 <wired> Selfmade router <wireless/wired>

After changing the channel to 1 nothing changed, connection abrot and from the 192.168.178.10.x network the router 192.168.10.1 is not reachable (no ping possible).

Is there anywhere a config-file for the bridge, except interfaces to configure it, like I said if wired and wireless are seperated (two seperate networks) quiet well.

---

### Post by jmoorse on 2011-07-17
Ok, I'm with you there.  Initial findings lead me to believe bridging could be the culprit.  Do both wired/wireless machines behind the selfmade router have the same connectivity issues?  Eg the odd ping times?

---

### Post by SeaKing on 2011-07-17
> **jmoorse said:**
>  Do both wired/wireless machines behind the selfmade router have the same connectivity issues?  Eg the odd ping times? 

Exactly.

Here is my interfaces content:

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
        address         192.168.1.100
        netmask         255.255.255.0
        gateway         192.168.178.1


auto eth1
iface eth1 inet manual

auto wlan0
iface wlan0 inet manual

auto br0
iface br0 inet static
    address 192.168.10.1
    network 192.168.10.0
    netmask 255.255.255.0
    broadcast 192.168.10.255
    bridge-ports eth1 wlan0
___________________
eth0 has a fixed address but it doesn't matter if fixed or dynamic/dhcp

---

### Post by jmoorse on 2011-07-17
I suspect an issue with the wireless card + bridge-utils.  Can you check the kernel / syslogs for any entries during times of interruptions that may be related?  Eg: 'too much work in interrupt'

If you really want to find out you wan remove the wlan from the br and test the wired computers for unusual ping latency.  Wash-rinse-repeat with just wlan0 in the br.

---

### Post by SeaKing on 2011-07-17
In syslog, the only thing I found which can cause latency problems is:

Jul 17 17:11:33 alix-router hostapd: wlan0: STA <mac client> WPA: group key handshake completed (RSN)
Jul 17 17:12:54 alix-router dhcpd: DHCPREQUEST for 192.168.10.11 from <mac client> (nightmare) via bro0
Jul 17 17:12:54 alix-router dhcpd: DHCPACK on 192.168.10.11 to <mac client> (nightmare) via br0
Jul 17 17:12:54 alix-router dhcpd: send_packet: Operation not permitted
Jul 17 17:12:54 alix-router dhcpd: DHCPREQUEST for 192.168.10.11 from <mac client> (nightmare) via bro0
Jul 17 17:12:54 alix-router dhcpd: DHCPACK on 192.168.10.11 to <mac client> (nightmare) via br0
Jul 17 17:12:54 alix-router dhcpd: send_packet: Operation not permitted

but dhcp3-server does not report any failure

---

### Post by jmoorse on 2011-07-17
DHCP should not have anything to do with this.

Can you run a SSID scan from the server just so I can see what other channels / signals are around?

sudo iwlist wlan0 scan

---

### Post by SeaKing on 2011-07-17
I find 3 Signals at channel 1, 8 & 9.

---

### Post by jmoorse on 2011-07-17
> **SeaKing said:**
> I find 3 Signals at channel 1, 8 & 9.

Fun.  8 will overlap with 6 and 9 will overlap with 11.  I wish WAP makers would fix their firmware...

Ok, but in any event you said they work fine when br0 is not used.  Perhaps you can ask the bridge-util team on [https://lists.linux-foundation.org/mailman/listinfo/bridge](https://lists.linux-foundation.org/mailman/listinfo/bridge) ?

---

### Post by SeaKing on 2011-07-17
> **jmoorse said:**
> ... they work fine when br0 is not used. 

Well work fine does not really fit^^ It works, I have the ping problems as well just the connections is stable.

---

### Post by jmoorse on 2011-07-17
Oh ok, just to be clear: the variable latency is noticed on BOTH wired and wireless when they are not bridged?  Or just the wifi?

---

### Post by SeaKing on 2011-07-17
Both, the only effects the bridge has are that clients loses connection and I can not ping the router.

---

### Post by jmoorse on 2011-07-17
So this looks like some obscure software/driver issue, I can't help much there but perhaps one of the Gurus around here can.

Why don't you replace the Ubuntu 'router' with an off the shelf piece of hardware?  Unless this is a hobby, I can't think of a reason why.  TCO for the ubuntu router will be much higher.  In fact, you could use a wireless router as a bridge / switch and remove the double NAT situation you have here.  Just a suggestion.

---

### Post by SeaKing on 2011-07-17
> **jmoorse said:**
>   Unless this is a hobby
Yes more or less it is, but is has also another reason, I want to use PXE Boot and Installation but this is not possible with the Router I have now.


Another question, I found this [tuorial/HOWTO]("http://www.linuxfoundation.org/collaborate/workgroups/networking/bridge") [FONT=Verdana] but the only things I've done for the bridge is: install [/FONT][FONT=Verdana]bridge-utils and add the entry in interfaces, was ist enough?
[/FONT]

---

### Post by jmoorse on 2011-07-17
Ok, in that case rock on!

You should not need to do any explicit bridge config due to what you have in /etc/network/interfaces.  Something to the effect of:

auto br0
iface br0 inet static
    [snip]
    bridge-ports eth# wlan0

We can check though, never hurts :)

Can you run:

brctl show

STP should not matter unless you have a dual homed client (also wired + wireless) connecting to this network.  We can try turning it off as a last resort, I doubt it has anything to do with the problem.

---

### Post by SeaKing on 2011-07-17
# brctl show
bridge name     ____bridge id               ___________STP______enabled     interfaces
br0___________             8000.000db9208ded___no_______eth1
                                                                         __________________________________________wlan0


standart output (except __ ;) )

---

### Post by jmoorse on 2011-07-17
Ok, STP is off.  We can try turning it on.  Doubt that is an issue but we can try, virtualbox has STP on for me on my virbr0 interface so what the heck?

sudo brctl stp br0 on

This may bounce your clients for a bit until STP runs its loop detection.

---

### Post by SeaKing on 2011-07-17
Yes it pushed the ping  unter 100ms. I also found out, that it isn't only impossible to ping the router from a client, but also the other way around. If I ping a client form the server:
From 192.168.10.1 icmp_seq=1 Destination Port Unreachable
From 192.168.10.1 icmp_seq=1 Destination Port Unreachable
From 192.168.10.1 icmp_seq=1 Destination Port Unreachable
From 192.168.10.1 icmp_seq=1 Destination Port Unreachable
.
.
.

/And connections breaks aber 10 min/

/E. I found something interesting in syslog, the client reconnected after these mysterious 10 minutes automatically to the router (and the same dhcp3 error the wohle time between the entries)

---

### Post by jmoorse on 2011-07-17
That is very odd.  Do you know if the clients lose their DHCP addressing when this occurs?  Can you try statically setting them and seeing if they go dark for 10m?

---

### Post by SeaKing on 2011-07-17
I know that the ip stays the same even after reconnection, tomorrow I try to give a client a static address to see if the problem appears then, too.

---

### Post by SeaKing on 2011-07-18
I gave a client a static IP the result: connaction lasts in the first test over 30 minutes (so let's say stable), I still can't ping the router and syslog give me the following log:

Jul 18 08:47:58 alix-router hostapd: wlan0: STA <MAC CLIENT> IEEE 802.11: authenticated
Jul 18 08:47:58 alix-router hostapd: wlan0: STA <MAC CLIENT> IEEE 802.11: associated (aid 1)
Jul 18 08:48:02 alix-router hostapd: wlan0: STA <MAC CLIENT> IEEE 802.11: deauthenticated due to local deauth request
Jul 18 08:48:03 alix-router hostapd: wlan0: STA <MAC CLIENT> IEEE 802.11: authenticated
Jul 18 08:48:03 alix-router hostapd: wlan0: STA <MAC CLIENT> IEEE 802.11: associated (aid 1)
Jul 18 08:48:03 alix-router hostapd: wlan0: STA <MAC CLIENT> RADIUS: starting accounting session 4E23D331-00000003
Jul 18 08:48:03 alix-router hostapd: wlan0: STA <MAC CLIENT> WPA: pairwise key handshake completed (RSN)
Jul 18 08:48:03 alix-router dhcpd: uid lease 192.168.10.11 for client <MAC CLIENT> is duplicate on 192.168.10/24
Jul 18 08:48:03 alix-router dhcpd: DHCPREQUEST for 192.168.10.5 from 74:f0:6d:00:a9:4f via br0
Jul 18 08:48:03 alix-router dhcpd: DHCPACK on 192.168.10.5 to <MAC CLIENT> via br0
[this block is repeated frequently in syslog]

---

### Post by jmoorse on 2011-07-18
Well that is a step in the right direction at least!

I wonder if the ping issues are related to iptables.

Can you post the output of:

```

sudo iptables -L -v

```

Can you also attach dhcpd.conf, or take a look at it?  The UID/duplicate error can sometimes be due to reservations outside the DHCP pool.

---

### Post by psusi on 2011-07-18
> **jmoorse said:**
> Fun.  8 will overlap with 6 and 9 will overlap with 11.  I wish WAP makers would fix their firmware...


What do you mean fix their firmware?  Channel 8 overlaps with channels 7 and 9.  Channel 9 overlaps with 8 and 10.  The worst that should cause though, is lower throughput.

---

### Post by jmoorse on 2011-07-18
> **psusi said:**
> What do you mean fix their firmware?  Channel 8 overlaps with channels 7 and 9.  Channel 9 overlaps with 8 and 10.  The worst that should cause though, is lower throughput.

Some vendors assign default channels outside 1,6,11 which means the trample on other connections.  This can cause packet-loss and in some extreme examples a 'flapping' connection between client and WAP, or even the inability to connect.

See attachment for full overlap diagram

---

### Post by SeaKing on 2011-07-18
I'd better post a picture of the output, see attachment.

192.168.178.x =192.168.1.x => Network 1
192.168.1.x = 192.168.10.1 => Network 2

sorry that I used other ip's before, but some may have problems with 192.168.**178**.x

---

### Post by jmoorse on 2011-07-18
> **SeaKing said:**
> I'd better post a picture of the output, see attachment.

192.168.178.x =192.168.1.x => Network 1
192.168.1.x = 192.168.10.1 => Network 2

sorry that I used other ip's before, but some may have problems with 192.168.**178**.x

I was going back through your interface config, is this accurate:
> 
auto eth0
iface eth0 inet static
address 192.168.1.100
netmask 255.255.255.0
gateway 192.168.178.1

Or did you alter any of the IPs while posting?

---

### Post by SeaKing on 2011-07-18
# Used by ifup(8) and ifdown(8). See the interfaces(5) manpage or
# /usr/share/doc/ifupdown/examples for more information.

# The loopback network interface
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
        address         192.168.178.100
        netmask         255.255.255.0
        gateway         192.168.178.1

auto eth1
iface eth1 inet manual

auto wlan0
iface wlan0 inet manual

auto br0
iface br0 inet static
    address 192.168.1.1
    network 192.168.1.0
    netmask 255.255.255.0
    broadcast 192.168.1.255
    bridge-ports eth1 wlan0

post-up /usr/sbin/my_iptables_rules.sh

up /etc/init.d/dhcp3-server restart
up /ect/init.d/bind9 restart


the one and only interfaces file

---

### Post by jmoorse on 2011-07-18
Ok, that makes sense.  Any idea why your entries in iptables are for 192.168.0.0/24?  I would expect them to be for 192.168.1.0/24 given your config.

---

### Post by SeaKing on 2011-07-19
:mrgreen: thats it! IT WORKS! I get no error reports anymore, a stable connetion and I can ping the router, I even get Infos about the lease time 

Thanks!

---

