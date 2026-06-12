---
title: "Ethernet bridge in Virtualbox with Ubuntu 11.04 guest on Win7 host"
date: 2011-07-24
forum: Networking &amp; Wireless
---

### Post by mortalapeman on 2011-07-24
Goal: Use a TAP interface with my openVPN server and network it with my ether-net interface using an ether-net bridge.  

Situation: I am attempting to setup a openVPN server on a Ubuntu 11.04 virtual machine on my Windows 7 host for my home network (the Win7 firewall is disabled for now just in case). The virtual machine is bridged to my network card so it's like having a it attached with a real cable. I have been able to setup and connect to the VPN server using a TUN interface successfully. The next thing I'd like to do use a TAP interface with my openVPN server and network it with my ether-net interface using an ether-net bridge.  My router has assigned my virtual machine a static IP of 192.168.1.65. Here is the script I was using from the openVPN how to site [here:]("http://openvpn.net/index.php/open-source/documentation/miscellaneous/76-ethernet-bridging.html")

```

#!/bin/bash

#################################
# Set up Ethernet bridge on Linux
# Requires: bridge-utils
#################################

# Define Bridge Interface
br="br0"

# Define list of TAP interfaces to be bridged,
# for example tap="tap0 tap1 tap2".
tap="tap0"

# Define physical ethernet interface to be bridged
# with TAP interface(s) above.
eth="eth0"
eth_ip="192.168.1.65"
eth_netmask="255.255.255.0"
eth_broadcast="192.168.1.255"

for t in $tap; do
    openvpn --mktun --dev $t
done

brctl addbr $br
brctl stp $br off    
brctl addif $br $eth
ifconfig $eth 0.0.0.0 promisc up

for t in $tap; do
    brctl addif $br $t
done

for t in $tap; do
    ifconfig $t 0.0.0.0 promisc up
done

ifconfig $br $eth_ip netmask $eth_netmask broadcast $eth_broadcast

```I used the code below to turn on IP forwarding.
```
sysctl -w net.ipv4.ip_forward=1
```The output of iptables -L is:
```

Chain INPUT (policy ACCEPT)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             anywhere            
ACCEPT     all  --  anywhere             anywhere            

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             anywhere            

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination 

```The problem is after running the script (the gnome networking applet is still connected to Auto eth0) I am not longer able to reach the internet through Firefox. I am pretty sure it is because eth0 no longer has a IP assigned to it but my expirence and google ninja skillz have left me with no idea how to proceed from here or what I can add to the script to get it to work.

Any help would be appreciated :)

---

### Post by mortalapeman on 2012-12-14
In case anyone else comes back to this post, I believe I solved my problem by switching to a "tun" interface instead of tap. Here is a paste bin of the script I used to setup things up.

[http://pastebin.com/LnWCeZr6](http://pastebin.com/LnWCeZr6)

It includes the server.conf text as well as the bash script I ended up writing to automate reconfiguration.

---

### Post by Bucky Ball on 2012-12-14
[I][B]Thread closed

Reason:[/B][/I] Old thread put to bed. Please note, 11.04 is no longer supported as of October this year.

---

