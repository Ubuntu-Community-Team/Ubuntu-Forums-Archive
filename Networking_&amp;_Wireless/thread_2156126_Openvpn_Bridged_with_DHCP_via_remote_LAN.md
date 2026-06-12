---
title: "Openvpn Bridged with DHCP via remote LAN"
date: 2013-06-20
forum: Networking &amp; Wireless
---

### Post by sefs on 2013-06-20
Hi,

I want to establish an Openvpn server in bridged mode on a remote LAN.  I want VPN clients to get their DHCP leases from the DHCP server on the remote LAN instead of from the Openvpn Server itself.

Has anyone here actually done this and got it to work?  If so help me out.

Thanks.

---

### Post by ahallubuntu on 2013-06-20
~

---

### Post by sefs on 2013-06-20
> **ahallubuntu said:**
> Why can't you let the OpenVPN server run its own DHCP server in the same subnet?  That's what I do.  Say the subnet is the typical 192.168.1.1/24.  Maybe I'll have 10 or so road warriors who connect via VPN.  I reserve 16 IP addresses for them.  I let the main DHCP server assign IPs in the range 192.168.1.100 to 192.168.1.199.  I let the OpenVPN server assign them in the range of 192.168.1.200 - 192.168.1.219.  No conflicts, and all clients can see each other (if that's the goal).

Hey there thanks for the reply.  I know this is an alternative method, but...one of the specific goals is to have the remote LAN serve and manage the dhcp leases to the tap interface of the  openvpn clients.

---

### Post by ahallubuntu on 2013-06-20
~

---

### Post by sefs on 2013-06-20
> **ahallubuntu said:**
> I understand that it is preferable to manage your network in one place (your main network router/DHCP server), but I wasn't able to work it out either in an easy way when I set up one of my OpenVPN setups.  Perhaps it is possible, but how many hours do you wish to spend trying to figure it out?

Is there any other reason you need to do it this way besides wanting to manage the network in entirely one place?

Sighs. You are correct about the hours part.  All the "solutions" I have seen on openvpn.net forums either don't work or go unanswered.  

Yes I have a reason which is this.  I am using dnsmasq on the remote LAN in such a way that I can refer to LAN clients by there FQDNs.  If I can get an openvpn client to accept DHCP from the remote LAN, then it too would be able to reference machines on the remote LAN by there FQDNs and it itself will have a registered FQDN in dnsmasq on the remote LAN that can be referred too by remote LAN clients.

---

### Post by ahallubuntu on 2013-06-20
~

---

### Post by sefs on 2013-06-21
> **ahallubuntu said:**
> I understand.  Let us know if you figure it out and how you did it!

Preamble:

SERVER
```

#=====================================
# Server Settings
#=====================================
local 192.168.1.3
dev tap0
proto udp
;proto tcp
port 1195
mode server
tls-server
tls-remote "openvpn.klingon.lan"
persist-key
persist-tun
tun-mtu 1500
tun-mtu-extra 32
mssfix 1450
max-clients 10
push "explicit-exit-notify 3"

#=====================================
# Network & DHCP Settings
#=====================================
server-bridge
push "route-gateway 192.168.1.1"
push "redirect-gateway def1 bypass-dhcp"
client-config-dir /etc/openvpn/ccd-bridged
client-to-client

#=====================================
# Certificates & Encryption Settings
#=====================================
ca /etc/openvpn/klingon-rootca-subscriptions.crt
cert /etc/openvpn/klingon-openvpn.crt
key /etc/openvpn/klingon-openvpn.key
dh /etc/openvpn/klingon-openvpn-dh.key
tls-auth /etc/openvpn/klingon-openvpn-ta.key 0
cipher AES-128-CBC
comp-lzo

#=====================================
# Management, Logs & Security Settings
#=====================================
management localhost 5003 /etc/openvpn/passwd.key
log /etc/openvpn/log/log-klingonOpenvpnBridged0.log
status /etc/openvpn/log/status-klingonOpenvpnBridged0.log
keepalive 10 120
verb 3
mute 20
script-security 2
;user nobody
;group nogroup
;client-connect /etc/openvpn/scripts/client-connect.sh
;client-disconnect /etc/openvpn/scripts/client-disconnect.sh

```

CLIENT
```

#=====================================
# Client Settings
#=====================================
remote xxx.xxx.xxx.xxx 995
dev tap
proto udp
;proto tcp
client
ns-cert-type server
persist-key
persist-tun
tun-mtu 1500
tun-mtu-extra 32
mssfix 1450
resolv-retry infinite
nobind
;float

#=====================================
# Certificates & Encryption Settings
#=====================================
ca /etc/openvpn/conf/klingonOpenvpn-ca.crt
cert /etc/openvpn/conf/klingonOpenvpn-client1.crt
key /etc/openvpn/conf/klingonOpenvpn-client1.key
tls-auth /etc/openvpn/conf/klingonOpenvpn-ta.key 1
cipher AES-128-CBC
comp-lzo

#=====================================
# Management, Logs & Security Settings
#=====================================
keepalive 10 60
verb 3
mute 20
script-security 2 system
up /etc/openvpn/update-resolv-conf
down /etc/openvpn/update-resolv-conf
;user nobody
;group nogroup

```


Here is where I am at. When launching openvpn to connect the script runs to completion with the following errors.
```

...
...
...
Fri Jun 21 11:09:14 2013 TUN/TAP device tap0 opened
Fri Jun 21 11:09:14 2013 TUN/TAP TX queue length set to 100
Fri Jun 21 11:09:14 2013 /etc/openvpn/update-resolv-conf tap0 1500 1590   init
Fri Jun 21 11:09:14 2013 /sbin/route add -net xxx.xxx.xxx.xxx netmask 255.255.255.255 gw 172.25.26.254
Fri Jun 21 11:09:14 2013 /sbin/route add -net 0.0.0.0 netmask 128.0.0.0 gw 172.25.25.1
SIOCADDRT: No such process
Fri Jun 21 11:09:14 2013 ERROR: Linux route add command failed: external program exited with error status: 7
Fri Jun 21 11:09:14 2013 /sbin/route add -net 128.0.0.0 netmask 128.0.0.0 gw 172.25.25.1
SIOCADDRT: No such process
Fri Jun 21 11:09:14 2013 ERROR: Linux route add command failed: external program exited with error status: 7
Fri Jun 21 11:09:14 2013 Initialization Sequence Completed

```

At this point the openvpn client is connected to the server, but since in the server.conf only "server-bridge" was used, it does not automatically bring up tap0 configured in Linux.  In MS Windows on the other hand, the talk of the town is this is suppose to work transparently, but I have not tested it as yet.  UPDATE: MS Windows works out of the box.

If I issue: 
```

sudo dhclient -v tap0

```

Then tap0 is configured via the remote LAN's dhcp server.  I can then go about as usual.  When done I would have to issue ```

dhclient -r tap0

```

and then close down the openvpn connection.

I have been trying to automate it by in the client.conf changing

```

...
...
...
up /etc/openvpn/update-resolv-conf
down /etc/openvpn/update-resolv-conf
...
...
...

```

to

```

...
...
...
up "dhclient -v tap0
down "dhclient -r tap0"
...
...
...

```
NB: for above you must add the system mode to --script-security eg. --script-security 2 system.  I am not sure why since "system" is suppose to be deprecated.

The above gives me the error
```

...
...
...
Fri Jun 21 20:19:54 2013 TUN/TAP device tap0 opened
Fri Jun 21 20:19:54 2013 TUN/TAP TX queue length set to 100
Fri Jun 21 20:19:54 2013 dhclient -v tap0 tap0 1500 1590   init
Internet Systems Consortium DHCP Client 4.1-ESV-R4
Copyright 2004-2011 Internet Systems Consortium.
All rights reserved.
For info, please visit https://www.isc.org/software/dhcp/

Cannot find device "init"
Cannot find device "up"
Cannot find device "up"
Cannot find device "1590"
Cannot find device "1500"
Failed to get interface index: No such device
Fri Jun 21 20:19:54 2013 WARNING: Failed running command (--up/--down): external program exited with error status: 1
Fri Jun 21 20:19:54 2013 Exiting

```

So i tried putting these commands in /etc/openvpn/update-resolv-conf, and they successfully run BUT no dhcp server offers any lease and dhclient just times out trying to get a lease so tap0 is never configured for the remote LAN.

So it looks like openvpn has to complete it's initialization sequence first before you can run dhclient on tap0.

I am still looking for a way to automate the autoconfig for tap0 at this point.

---

### Post by sefs on 2013-06-22
Update...

dhcp.sh
------------
```

#!/bin/bash
# 

[ -x /sbin/dhclient ] || exit 0

case $script_type in

up)
        dhclient -v "${dev}"
        ;;
down)
        dhclient -r "${dev}"
        ;;
esac

```

CLIENT (Updated)
```

#=====================================
# Client Settings
#=====================================
remote xxx.xxx.xxx.xxx 995
dev tap
proto udp
;proto tcp
client
ns-cert-type server
persist-key
persist-tun
tun-mtu 1500
tun-mtu-extra 32
mssfix 1450
resolv-retry infinite
nobind
;float

#=====================================
# Certificates & Encryption Settings
#=====================================
ca /etc/openvpn/conf/klingonOpenvpn-ca.crt
cert /etc/openvpn/conf/klingonOpenvpn-client1.crt
key /etc/openvpn/conf/klingonOpenvpn-client1.key
tls-auth /etc/openvpn/conf/klingonOpenvpn-ta.key 1
cipher AES-128-CBC
comp-lzo

#=====================================
# Management, Logs & Security Settings
#=====================================
keepalive 10 60
verb 3
mute 20
script-security 2 system
route-delay 30
;up /etc/openvpn/dhcp.sh
down-pre
down /etc/openvpn/dhcp.sh
;up /etc/openvpn/update-resolv-conf
;down /etc/openvpn/update-resolv-conf
;user nobody
;group nogroup

```

I still have to run dhclient -v tap0 manually, but I have introduced "route-delay 30".  This pauses openvpn execution for 30 seconds.  Enough time to open a terminal window and run the "dhclient -v tap0" command for tap0 to be configured via dhcp of remote LAN.  after 30 seconds openvpn initialization continues with adding routes.  No more errors here as tap0 is up and configured.  Added down-pre so that the down script can be ran BEFORE the tap0 is closed. This is basically a "dhclient -r tap0" to release tap0 ip back to the pool gracefully. Initially the down script was running after the tap0 was destroyed and causing errors.  This way it looks like it is more graceful, and IMORTANTLY this way "/etc/resolv.conf" is set back to what it previously was.

Still have to figure out a way to integrate "dhclient -v tap0" into the init sequence so it is all automatic.

---

### Post by sefs on 2013-06-22
dhcp.sh (updated)
-----------------
```

#!/bin/bash
# 

[ -x /sbin/dhclient ] || exit 0

case $script_type in

up)
        # echo "Your misson should you choose to accept it, is to open a new terminal and issue:"
	# echo "dhclient -v ${dev}"
	# echo "You have 30 seconds...GO!"
        dhclient -v "${dev}" &
        ;;
down)
	echo "Releasing ${dev} DHCP lease."
        dhclient -r "${dev}"
        ;;
esac

```

I've added a "&" to the up script of " dhclient -v "${dev}" ".  What I think that does is to fork it into the background away from the openvpn initilization.  So it now runs and gets a valid lease from the up command in the client config.

CLIENT (updated)
-----------------
```

#=====================================
# Client Settings
#=====================================
remote xxx.xxx.xxx.xxx 995
dev tap
proto udp
;proto tcp
client
ns-cert-type server
persist-key
persist-tun
tun-mtu 1500
tun-mtu-extra 32
mssfix 1450
resolv-retry infinite
nobind
;float

#=====================================
# Certificates & Encryption Settings
#=====================================
ca /etc/openvpn/conf/klingonOpenvpn-ca.crt
cert /etc/openvpn/conf/klingonOpenvpn-client1.crt
key /etc/openvpn/conf/klingonOpenvpn-client1.key
tls-auth /etc/openvpn/conf/klingonOpenvpn-ta.key 1
cipher AES-128-CBC
comp-lzo

#=====================================
# Management, Logs & Security Settings
#=====================================
keepalive 10 60
verb 3
mute 20
script-security 2
route-delay 10
up /etc/openvpn/dhcp.sh
down-pre
down /etc/openvpn/dhcp.sh
;up /etc/openvpn/update-resolv-conf
;down /etc/openvpn/update-resolv-conf
;user nobody
;group nogroup

```

I reduced the route-delay to 10 seconds since getting the dhcp is now "automated" into the up script.  It probably would still be safe to make it longer than 10 though, given how slow or fast a lease can be had.  15 seconds might be better.

One other thing I have discovered is that openvpn tap seems to take a different mac address each time it connects, so it will not reuse an old IP it had previously which would be ideal.  So your dhcp server could be peppered with leases for however long the client lease time is set too.  Is there a way to override this via the dhclient command?

That's it I think.

---

