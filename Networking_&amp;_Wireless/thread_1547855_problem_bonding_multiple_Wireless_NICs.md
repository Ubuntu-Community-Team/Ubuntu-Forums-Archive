---
title: "problem bonding multiple Wireless NICs"
date: 2010-08-07
forum: Networking &amp; Wireless
---

### Post by yankeeone on 2010-08-07
Hi everyone,
I'm a new ubuntu user, but I've had experience with other linux distros (rpm,deb).
I built an HTPC for my home but I can't get the ethernet cable from the router to the HTPC.
Giving the fact that I have a network hard disk with a lot of stuff inside I decided to create an high availability wireless connection (the HTPC has 2 wireless cards).
the two cards are: 
1 Atheros AR5007G  54Mbps  (TP-Link)  ath5k module
1 TI ACX111 card   54Mbps  (D-Link)   ndiswrapper module
Both card works ok only if the router DHCP client is disabled, but it is not a problem because i do not need DHCP, I like static addresses.
The goals of this setup are to increase the available bandwith (Secondary) and to increase the reliability of the network (Primary).
My wireless networks are set up as: 192.168.1.55 ath
                                    192.168.1.60 acx
                                    192.168.1.1  gateway
                                    
I followed some tutorials on the net and it looks like that i have to load the bonding kernel module in mode 0 and monitor 100ms:
modprobe bonding mode=0 miimon=100

After that i have to set the bond0 virtual device up with the network address and mac of the first slave:
ifconfig bond0 192.168.1.55 netmask 255.255.255.0 broadcast 192.168.1.255 hw ether [wlan0 MAC]

Running ifconfig -a shows the new network device available bond0 that is using the wlan0 mac and ip address.
Now it's time to enslave the NICs to the bond0:
ifenslave bond0 wlan0
ifenslave bond0 wlan1

Now the two NICs appear to be bonded to the main virtual device but while the wlan0 usually connect to the wireless network, the second NIC (wlan1) refuses to connect.
I'm using the gnome network manager to set up the wireless connections.
Also the connection is not working, nor internet nor pinging the gateway.

had I missed something???
My suspect is that both NICs are trying to connect to the router with the same MAC and IP so the connection of the scond wlan is refused, but it is only a theory....

another question:
when we bond two or more NICs we see that all slaves share the same MAC with the bond0 virtual device, but what do see the router?
will It (the router) continue to see multiple MACs or will it see only a MAC repeated in multiple connections???

Thank you for your support!

---

### Post by Mark Larry on 2012-02-16
Hello to all,

 'm trying to do the same and bond two wireless NIC and I'm facing the same problem.

I have already bonded the two wired ethernet interfaces achieving 2 Gb/s of bandwidth with the aggregation of eth1 and eth2 wired interfaces.

Now I was I trying to do the bond of the 2 wireless devices(2 atheros) and I'm facing the same problem that is described here [http://ubuntuforums.org/showthread.php?p=11688437](http://ubuntuforums.org/showthread.php?p=11688437)

 Can someone please help me
 All advises, comments, etc... will be very much appreciated.

 Best Regards
 Mark

---

### Post by Mark Larry on 2012-02-16
Hi again, 

As anyone ever been able to bind 2 wireless NIC, may be in the same way that wired NIC's or other way.

Open to new solutions..

Regards
Mark

---

