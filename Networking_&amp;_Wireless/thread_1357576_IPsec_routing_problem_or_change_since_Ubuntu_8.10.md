---
title: "IPsec routing problem or change since Ubuntu 8.10"
date: 2009-12-17
forum: Networking &amp; Wireless
---

### Post by bmcchesney on 2009-12-17
Hello,

In recent versions of Ubuntu I am having trouble routing IPsec traffic properly over a configured tunnel. I've tried the same minimal configuration in various versions:

Ubuntu 8.04.3 x86. Worked.
Ubuntu 8.10 x86. Failed.
Ubuntu 9.04 x86. Failed.
Ubuntu 9.10 x86. Failed.

It appears that something has changed between 8.04 and 8.10. I've probably always been doing something incorrectly. If anyone could please advise what I am doing wrong or suggest a fix, it would be greatly appreciated.

Full details follow, but the summary is, I am trying to upgrade an IPsec site-to-site endpoint from 8.04 to 9.10. Whereas before I could ping remote computers from the Ubuntu box itself and from all computers on the local subnet, after the (clean) upgrade I can only ping remote computers from behind the Ubuntu box: I cannot ping from the Ubuntu box. I'm using ipsec-tools and Racoon, but I have also found the same issue with OpenSwan.

It's not a major issue, until there's something running on the box that needs to access a remote address. It also doesn't help for troubleshooting. It just doesn't seem complete to me that the endpoint can't access the remote network.

Anyone encoutered this problem? Any suggestions welcome.


Network overview:

LOCAL Subnet 192.168.88.0/24
   |
192.168.88.1
Ubuntu - Various version I am testing
192.168.11.2
   |
192.168.11.1
Speedtouch ADSL Router
A.A.A.A
   |
(Internet)
   |
Z.Z.Z.Z
Netgear ADSL Router
192.168.1.1
   |
192.168.1.2
Ubuntu 8.04.3 LTS
10.0.9.1
   |
REMOTE Subnet 10.0.9.0/24


Configuration (as applied on each version tested):

[/etc/network/interfaces]
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
        address 192.168.11.2
        netmask 255.255.255.0
        gateway 192.168.11.1
        dns-nameservers 192.168.11.1

auto eth5
iface eth5 inet static
        address 192.168.88.1
        netmask 255.255.255.0

:apt-get update
:apt-get install racoon ipsec-tools tshark

[/etc/racoon/racoon.conf]
path pre_shared_key "/etc/racoon/psk.txt";
path certificate "/etc/racoon/certs";
remote Z.Z.Z.Z {
        exchange_mode main;
        #lifetime time 24 hour;
        my_identifier address;
        #initial_contact on;
        nat_traversal on;
        proposal {
                encryption_algorithm 3des;
                hash_algorithm sha1;
                authentication_method pre_shared_key;
                dh_group 2;
        }
}
sainfo address 192.168.88.0/24 any address 10.0.9.0/24 any {
        encryption_algorithm 3des;
        authentication_algorithm hmac_sha1;
        lifetime time 8 hours;
        compression_algorithm deflate;
        #pfs_group 2;
}

[/etc/racoon/psk.txt]
Z.Z.Z.Z    PRESHAREDKEY

[/etc/ipsec-tools.conf]
flush;
spdflush;
spdadd 192.168.88.0/24 10.0.9.0/24 any -P out ipsec
        esp/tunnel/192.168.11.2-Z.Z.Z.Z/require;
spdadd 10.0.9.0/24 192.168.88.0/24 any -P in ipsec
        esp/tunnel/Z.Z.Z.Z-192.168.11.2/require;

:setkey -f /etc/ipsec-tools.conf
:/etc/init.d/racoon restart
:echo 1 > /proc/sys/net/ipv4/ip_forward


Results on v8.04.3:
:route add -net 10.0.9.0 netmask 255.255.255.0 gw 192.168.88.1
:ping 10.0.9.1
packets returned!
Can also ping from box behind vpn endpoint!

Results on v8.10 onwards:
Without the route added, I can ping from behind vpn server, but not the vpn server itself.
When route added, I **can't** ping from either vpn server or from behind it. I can see that the packets are getting transmitted however on the remote endpoint:
206.150113 A.A.A.A -> 192.168.1.2  ESP ESP (SPI=0x00675a21)
206.150226  192.168.1.2 -> A.A.A.A ESP ESP (SPI=0x0eb87208)
209.590182 A.A.A.A -> 192.168.1.2  ESP ESP (SPI=0x00675a21)
209.590246  192.168.1.2 -> A.A.A.A ESP ESP (SPI=0x0eb87208)

Regards,
Bob McChesney

---

### Post by bmcchesney on 2009-12-22
I've got this resolved, so I'm posting here for the benefit of others who might be having the same problem.

Whereas in Ubuntu 8.04 (and earlier?) the following routing command was sufficient

:route add -net 10.0.9.0 netmask 255.255.255.0 gw 192.168.88.1

the following is now required

:ip route add 10.0.9.0/24 via 192.168.11.2 src 192.168.88.1

Regards,
Bob McChesney

---

### Post by whit on 2010-03-10
The second form is iproute2, which also works fine on 8.04.

---

