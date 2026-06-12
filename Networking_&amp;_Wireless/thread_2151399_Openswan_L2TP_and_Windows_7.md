---
title: "Openswan L2TP and Windows 7"
date: 2013-06-04
forum: Networking &amp; Wireless
---

### Post by j_zuilkowski on 2013-06-04
God this is insane to set up for some reason.  I think building custom kernels in 1996 were easier than this...

So anyway, I've tried every tutorial on this I could find, and I cannot get this to work.  Here is the tutorial I am working off of for the purposes of this post:  [https://help.ubuntu.com/community/L2TPServer](https://help.ubuntu.com/community/L2TPServer)

I have followed this more or less exactly, except for updating openswan to the version in launchpad.  I just cannot make sense of this.  Here is my config (all passwords and keys the exact same string for the moment):

/etc/ipsec.conf:
```
config setup    nat_traversal=yes
    virtual_private=%v4:10.0.0.0/8,%v4:192.168.0.0/16,%v4:172.16.0.0/12,%v4:!10.152.2.0/24
    #contains the networks that are allowed as subnet= for the remote client. In other words, the address ranges that may live behind a NAT router through which a client connects.
    oe=off
    protostack=netkey
 
conn L2TP-PSK-NAT
    rightsubnet=vhost:%priv
    also=L2TP-PSK-noNAT
 
conn L2TP-PSK-noNAT
    authby=secret
    pfs=no
    auto=add
    keyingtries=3
    rekey=no
    # Apple iOS doesn't send delete notify so we need dead peer detection
    # to detect vanishing clients
    dpddelay=30
    dpdtimeout=120
    dpdaction=clear
    # Set ikelifetime and keylife to same defaults windows has
    ikelifetime=8h
    keylife=1h
    type=transport
    # Replace IP address with your local IP (private, behind NAT IP is okay as well)
    left=200.200.200.145
    # For updated Windows 2000/XP clients,
    # to support old clients as well, use leftprotoport=17/%any
    leftprotoport=17/1701
    right=%any
    rightprotoport=17/%any
    #force all to be nat'ed. because of iOS
    forceencaps=yes
```

/etc/ipsec.secrets
```
200.200.200.145   %any:  PSK "password"
```

/etc/xl2tpd/xl2tpd.conf
```
[global]ipsec saref = no
port = 1701                                                     ; * Bind to port 1701
auth file = /etc/xl2tpd/l2tp-secrets    ; * Where our challenge secrets are
 
[lns default]
ip range = 10.9.242.2-10.9.242.6
local ip = 10.9.242.1
require chap = yes
refuse pap = yes
require authentication = yes
ppp debug = yes
pppoptfile = /etc/ppp/options.xl2tpd
length bit = yes
exclusive = no                                          ; * Only permit one tunnel per host
assign ip = yes
name = VPN-Server  
```

/etc/xl2tpd/l2tp-secrets
```
# Secrets for authenticating l2tp tunnels# us    them    secret
# *             marko blah2
# zeus          marko   blah
# *     *       interop
* * password
```

/etc/ppp/options.xl2tpd
```
refuse-mschap-v2refuse-mschap
ms-dns 8.8.8.8
ms-dns 8.8.4.4
asyncmap 0
auth
crtscts
idle 1800
mtu 1200
mru 1200
lock
hide-password
local
debug
name l2tpd
proxyarp
lcp-echo-interval 30
lcp-echo-failure 4
```

/etc/ppp/chap-secrets
```
# Secrets for authentication using CHAP
# client        server  secret                  IP addresses
user1 l2tpd password *
user2 * password *
```


/etc/init.d/ipsec.vpn
```
case "$1" in  start)
echo "Starting my Ipsec VPN"
iptables  -t nat   -A POSTROUTING -o eth0 -s 10.9.242.0/24 -j MASQUERADE
echo 1 > /proc/sys/net/ipv4/ip_forward
for each in /proc/sys/net/ipv4/conf/*
do
    echo 0 > $each/accept_redirects
    echo 0 > $each/send_redirects
done
/etc/init.d/ipsec start
/etc/init.d/xl2tpd start
;;
stop)
echo "Stopping my Ipsec VPN"
iptables --table nat --flush
echo 0 > /proc/sys/net/ipv4/ip_forward
/etc/init.d/ipsec stop
/etc/init.d/xl2tpd stop
;;
restart)
echo "Restarting my Ipsec VPN"
iptables  -t nat   -A POSTROUTING -o eth0 -s 10.9.242.0/24 -j MASQUERADE
echo 1 > /proc/sys/net/ipv4/ip_forward
for each in /proc/sys/net/ipv4/conf/*
do
    echo 0 > $each/accept_redirects
    echo 0 > $each/send_redirects
done
/etc/init.d/ipsec restart
/etc/init.d/xl2tpd restart
 
;;
  *)
 echo "Usage: /etc/init.d/ipsec.vpn  {start|stop|restart}"
 exit 1
  ;;
esac
```


Client external nat address - 220.220.220.97
Client real address - 10.10.10.161
Server external address - 200.200.200.145
Server internal address - 10.9.242.1
 
After starting and attempting a connection, /var/log/auth.log:
```
Jun  4 10:38:26 ubuntuvpn ipsec__plutorun: Starting Pluto subsystem...Jun  4 10:38:26 ubuntuvpn pluto[1828]: Starting Pluto (Openswan Version 2.6.38; Vendor ID OEvy\134kgzWq\134s) pid:1828
Jun  4 10:38:26 ubuntuvpn pluto[1828]: LEAK_DETECTIVE support [disabled]
Jun  4 10:38:26 ubuntuvpn pluto[1828]: OCF support for IKE [disabled]
Jun  4 10:38:26 ubuntuvpn pluto[1828]: SAref support [disabled]: Protocol not available
Jun  4 10:38:26 ubuntuvpn pluto[1828]: SAbind support [disabled]: Protocol not available
Jun  4 10:38:26 ubuntuvpn pluto[1828]: NSS support [disabled]
Jun  4 10:38:26 ubuntuvpn pluto[1828]: HAVE_STATSD notification support not compiled in
Jun  4 10:38:26 ubuntuvpn pluto[1828]: Setting NAT-Traversal port-4500 floating to on
Jun  4 10:38:26 ubuntuvpn pluto[1828]:    port floating activation criteria nat_t=1/port_float=1
Jun  4 10:38:26 ubuntuvpn pluto[1828]:    NAT-Traversal support  [enabled]
Jun  4 10:38:26 ubuntuvpn pluto[1828]: using /dev/urandom as source of random entropy
Jun  4 10:38:26 ubuntuvpn pluto[1828]: ike_alg_register_enc(): Activating OAKLEY_AES_CBC: Ok (ret=0)
Jun  4 10:38:26 ubuntuvpn pluto[1828]: ike_alg_register_hash(): Activating OAKLEY_SHA2_512: Ok (ret=0)
Jun  4 10:38:26 ubuntuvpn pluto[1828]: ike_alg_register_hash(): Activating OAKLEY_SHA2_256: Ok (ret=0)
Jun  4 10:38:26 ubuntuvpn pluto[1828]: starting up 1 cryptographic helpers
Jun  4 10:38:26 ubuntuvpn pluto[1828]: started helper pid=1831 (fd:6)
Jun  4 10:38:26 ubuntuvpn pluto[1828]: Using Linux 2.6 IPsec interface code on 3.2.0-26-generic-pae (experimental code)
Jun  4 10:38:26 ubuntuvpn pluto[1831]: using /dev/urandom as source of random entropy
Jun  4 10:38:26 ubuntuvpn pluto[1828]: ike_alg_register_enc(): Activating aes_ccm_8: Ok (ret=0)
Jun  4 10:38:26 ubuntuvpn pluto[1828]: ike_alg_add(): ERROR: algo_type '0', algo_id '0', Algorithm type already exists
Jun  4 10:38:26 ubuntuvpn pluto[1828]: ike_alg_register_enc(): Activating aes_ccm_12: FAILED (ret=-17)
Jun  4 10:38:26 ubuntuvpn pluto[1828]: ike_alg_add(): ERROR: algo_type '0', algo_id '0', Algorithm type already exists
Jun  4 10:38:26 ubuntuvpn pluto[1828]: ike_alg_register_enc(): Activating aes_ccm_16: FAILED (ret=-17)
Jun  4 10:38:26 ubuntuvpn pluto[1828]: ike_alg_add(): ERROR: algo_type '0', algo_id '0', Algorithm type already exists
Jun  4 10:38:26 ubuntuvpn pluto[1828]: ike_alg_register_enc(): Activating aes_gcm_8: FAILED (ret=-17)
Jun  4 10:38:26 ubuntuvpn pluto[1828]: ike_alg_add(): ERROR: algo_type '0', algo_id '0', Algorithm type already exists
Jun  4 10:38:26 ubuntuvpn pluto[1828]: ike_alg_register_enc(): Activating aes_gcm_12: FAILED (ret=-17)
Jun  4 10:38:26 ubuntuvpn pluto[1828]: ike_alg_add(): ERROR: algo_type '0', algo_id '0', Algorithm type already exists
Jun  4 10:38:26 ubuntuvpn pluto[1828]: ike_alg_register_enc(): Activating aes_gcm_16: FAILED (ret=-17)
Jun  4 10:38:26 ubuntuvpn pluto[1828]: added connection description "L2TP-PSK-NAT"
Jun  4 10:38:26 ubuntuvpn pluto[1828]: added connection description "L2TP-PSK-noNAT"
Jun  4 10:38:26 ubuntuvpn pluto[1828]: listening for IKE messages
Jun  4 10:38:26 ubuntuvpn pluto[1828]: adding interface eth0/eth0 200.200.200.145:500
Jun  4 10:38:26 ubuntuvpn pluto[1828]: adding interface eth0/eth0 200.200.200.145:4500
Jun  4 10:38:26 ubuntuvpn pluto[1828]: adding interface lo/lo 127.0.0.1:500
Jun  4 10:38:26 ubuntuvpn pluto[1828]: adding interface lo/lo 127.0.0.1:4500
Jun  4 10:38:26 ubuntuvpn pluto[1828]: adding interface lo/lo ::1:500
Jun  4 10:38:26 ubuntuvpn pluto[1828]: loading secrets from "/etc/ipsec.secrets"
Jun  4 10:38:38 ubuntuvpn pluto[1828]: packet from 220.220.220.97:500: ignoring Vendor ID payload [MS NT5 ISAKMPOAKLEY 00000008]
Jun  4 10:38:38 ubuntuvpn pluto[1828]: packet from 220.220.220.97:500: received Vendor ID payload [RFC 3947] method set to=115 
Jun  4 10:38:38 ubuntuvpn pluto[1828]: packet from 220.220.220.97:500: received Vendor ID payload [draft-ietf-ipsec-nat-t-ike-02_n] meth=106, but already using method 115
Jun  4 10:38:38 ubuntuvpn pluto[1828]: packet from 220.220.220.97:500: ignoring Vendor ID payload [FRAGMENTATION]
Jun  4 10:38:38 ubuntuvpn pluto[1828]: packet from 220.220.220.97:500: ignoring Vendor ID payload [MS-Negotiation Discovery Capable]
Jun  4 10:38:38 ubuntuvpn pluto[1828]: packet from 220.220.220.97:500: ignoring Vendor ID payload [Vid-Initial-Contact]
Jun  4 10:38:38 ubuntuvpn pluto[1828]: packet from 220.220.220.97:500: ignoring Vendor ID payload [IKE CGA version 1]
Jun  4 10:38:38 ubuntuvpn pluto[1828]: "L2TP-PSK-NAT"[1] 220.220.220.97 #1: responding to Main Mode from unknown peer 220.220.220.97
Jun  4 10:38:38 ubuntuvpn pluto[1828]: "L2TP-PSK-NAT"[1] 220.220.220.97 #1: OAKLEY_GROUP 20 not supported.  Attribute OAKLEY_GROUP_DESCRIPTION
Jun  4 10:38:38 ubuntuvpn pluto[1828]: "L2TP-PSK-NAT"[1] 220.220.220.97 #1: OAKLEY_GROUP 19 not supported.  Attribute OAKLEY_GROUP_DESCRIPTION
Jun  4 10:38:38 ubuntuvpn pluto[1828]: "L2TP-PSK-NAT"[1] 220.220.220.97 #1: transition from state STATE_MAIN_R0 to state STATE_MAIN_R1
Jun  4 10:38:38 ubuntuvpn pluto[1828]: "L2TP-PSK-NAT"[1] 220.220.220.97 #1: STATE_MAIN_R1: sent MR1, expecting MI2
Jun  4 10:38:38 ubuntuvpn pluto[1828]: "L2TP-PSK-NAT"[1] 220.220.220.97 #1: NAT-Traversal: Result using draft-ietf-ipsec-nat-t-ike (MacOS X): both are NATed
Jun  4 10:38:38 ubuntuvpn pluto[1828]: "L2TP-PSK-NAT"[1] 220.220.220.97 #1: transition from state STATE_MAIN_R1 to state STATE_MAIN_R2
Jun  4 10:38:38 ubuntuvpn pluto[1828]: "L2TP-PSK-NAT"[1] 220.220.220.97 #1: STATE_MAIN_R2: sent MR2, expecting MI3
Jun  4 10:38:38 ubuntuvpn pluto[1828]: "L2TP-PSK-NAT"[1] 220.220.220.97 #1: Main mode peer ID is ID_IPV4_ADDR: '10.10.10.161'
Jun  4 10:38:38 ubuntuvpn pluto[1828]: "L2TP-PSK-NAT"[1] 220.220.220.97 #1: switched from "L2TP-PSK-NAT" to "L2TP-PSK-NAT"
Jun  4 10:38:38 ubuntuvpn pluto[1828]: "L2TP-PSK-NAT"[2] 220.220.220.97 #1: deleting connection "L2TP-PSK-NAT" instance with peer 220.220.220.97 {isakmp=#0/ipsec=#0}
Jun  4 10:38:38 ubuntuvpn pluto[1828]: "L2TP-PSK-NAT"[2] 220.220.220.97 #1: transition from state STATE_MAIN_R2 to state STATE_MAIN_R3
Jun  4 10:38:38 ubuntuvpn pluto[1828]: "L2TP-PSK-NAT"[2] 220.220.220.97 #1: new NAT mapping for #1, was 220.220.220.97:500, now 220.220.220.97:4500
Jun  4 10:38:38 ubuntuvpn pluto[1828]: "L2TP-PSK-NAT"[2] 220.220.220.97 #1: STATE_MAIN_R3: sent MR3, ISAKMP SA established {auth=OAKLEY_PRESHARED_KEY cipher=aes_256 prf=oakley_sha group=modp2048}
Jun  4 10:38:38 ubuntuvpn pluto[1828]: "L2TP-PSK-NAT"[2] 220.220.220.97 #1: Dead Peer Detection (RFC 3706): not enabled because peer did not advertise it
Jun  4 10:38:38 ubuntuvpn pluto[1828]: "L2TP-PSK-NAT"[2] 220.220.220.97 #1: the peer proposed: 200.200.200.145/32:17/1701 -> 10.10.10.161/32:17/0
Jun  4 10:38:38 ubuntuvpn pluto[1828]: "L2TP-PSK-NAT"[2] 220.220.220.97 #1: NAT-Traversal: received 2 NAT-OA. using first, ignoring others
Jun  4 10:38:38 ubuntuvpn pluto[1828]: "L2TP-PSK-NAT"[2] 220.220.220.97 #2: responding to Quick Mode proposal {msgid:01000000}
Jun  4 10:38:38 ubuntuvpn pluto[1828]: "L2TP-PSK-NAT"[2] 220.220.220.97 #2:     us: 200.200.200.145<200.200.200.145>:17/1701
Jun  4 10:38:38 ubuntuvpn pluto[1828]: "L2TP-PSK-NAT"[2] 220.220.220.97 #2:   them: 220.220.220.97[10.10.10.161]:17/1701===10.10.10.161/32
Jun  4 10:38:38 ubuntuvpn pluto[1828]: "L2TP-PSK-NAT"[2] 220.220.220.97 #2: transition from state STATE_QUICK_R0 to state STATE_QUICK_R1
Jun  4 10:38:38 ubuntuvpn pluto[1828]: "L2TP-PSK-NAT"[2] 220.220.220.97 #2: STATE_QUICK_R1: sent QR1, inbound IPsec SA installed, expecting QI2
Jun  4 10:38:38 ubuntuvpn pluto[1828]: "L2TP-PSK-NAT"[2] 220.220.220.97 #2: Dead Peer Detection (RFC 3706): not enabled because peer did not advertise it
Jun  4 10:38:38 ubuntuvpn pluto[1828]: "L2TP-PSK-NAT"[2] 220.220.220.97 #2: transition from state STATE_QUICK_R1 to state STATE_QUICK_R2
Jun  4 10:38:38 ubuntuvpn pluto[1828]: "L2TP-PSK-NAT"[2] 220.220.220.97 #2: STATE_QUICK_R2: IPsec SA established transport mode {ESP/NAT=>0x4df83af2 <0xed657056 xfrm=AES_128-HMAC_SHA1 NATOA=10.10.10.161 NATD=220.220.220.97:4500 DPD=none}
Jun  4 10:38:38 ubuntuvpn pluto[1828]: "L2TP-PSK-NAT"[2] 220.220.220.97 #1: the peer proposed: 200.200.200.145/32:17/1701 -> 10.10.10.161/32:17/1701
Jun  4 10:38:38 ubuntuvpn pluto[1828]: "L2TP-PSK-NAT"[2] 220.220.220.97 #1: NAT-Traversal: received 2 NAT-OA. using first, ignoring others
Jun  4 10:38:38 ubuntuvpn pluto[1828]: "L2TP-PSK-NAT"[2] 220.220.220.97 #3: responding to Quick Mode proposal {msgid:02000000}
Jun  4 10:38:38 ubuntuvpn pluto[1828]: "L2TP-PSK-NAT"[2] 220.220.220.97 #3:     us: 200.200.200.145<200.200.200.145>:17/1701
Jun  4 10:38:38 ubuntuvpn pluto[1828]: "L2TP-PSK-NAT"[2] 220.220.220.97 #3:   them: 220.220.220.97[10.10.10.161]:17/1701===10.10.10.161/32
Jun  4 10:38:38 ubuntuvpn pluto[1828]: "L2TP-PSK-NAT"[2] 220.220.220.97 #3: keeping refhim=4294901761 during rekey
Jun  4 10:38:38 ubuntuvpn pluto[1828]: "L2TP-PSK-NAT"[2] 220.220.220.97 #3: transition from state STATE_QUICK_R0 to state STATE_QUICK_R1
Jun  4 10:38:38 ubuntuvpn pluto[1828]: "L2TP-PSK-NAT"[2] 220.220.220.97 #3: STATE_QUICK_R1: sent QR1, inbound IPsec SA installed, expecting QI2
Jun  4 10:38:38 ubuntuvpn pluto[1828]: "L2TP-PSK-NAT"[2] 220.220.220.97 #3: Dead Peer Detection (RFC 3706): not enabled because peer did not advertise it
Jun  4 10:38:38 ubuntuvpn pluto[1828]: "L2TP-PSK-NAT"[2] 220.220.220.97 #3: transition from state STATE_QUICK_R1 to state STATE_QUICK_R2
Jun  4 10:38:38 ubuntuvpn pluto[1828]: "L2TP-PSK-NAT"[2] 220.220.220.97 #3: STATE_QUICK_R2: IPsec SA established transport mode {ESP/NAT=>0x4c6b122e <0xd56aa467 xfrm=AES_128-HMAC_SHA1 NATOA=10.10.10.161 NATD=220.220.220.97:4500 DPD=none}
Jun  4 10:38:38 ubuntuvpn pluto[1828]: "L2TP-PSK-NAT"[2] 220.220.220.97 #1: received Delete SA(0x4df83af2) payload: deleting IPSEC State #2
Jun  4 10:38:38 ubuntuvpn pluto[1828]: "L2TP-PSK-NAT"[2] 220.220.220.97 #1: received and ignored informational message
Jun  4 10:38:41 ubuntuvpn pluto[1828]: "L2TP-PSK-NAT"[2] 220.220.220.97 #1: the peer proposed: 200.200.200.145/32:17/1701 -> 10.10.10.161/32:17/1701
Jun  4 10:38:41 ubuntuvpn pluto[1828]: "L2TP-PSK-NAT"[2] 220.220.220.97 #1: NAT-Traversal: received 2 NAT-OA. using first, ignoring others
Jun  4 10:38:41 ubuntuvpn pluto[1828]: "L2TP-PSK-NAT"[2] 220.220.220.97 #4: responding to Quick Mode proposal {msgid:03000000}
Jun  4 10:38:41 ubuntuvpn pluto[1828]: "L2TP-PSK-NAT"[2] 220.220.220.97 #4:     us: 200.200.200.145<200.200.200.145>:17/1701
Jun  4 10:38:41 ubuntuvpn pluto[1828]: "L2TP-PSK-NAT"[2] 220.220.220.97 #4:   them: 220.220.220.97[10.10.10.161]:17/1701===10.10.10.161/32
Jun  4 10:38:41 ubuntuvpn pluto[1828]: "L2TP-PSK-NAT"[2] 220.220.220.97 #4: keeping refhim=4294901761 during rekey
Jun  4 10:38:41 ubuntuvpn pluto[1828]: "L2TP-PSK-NAT"[2] 220.220.220.97 #4: transition from state STATE_QUICK_R0 to state STATE_QUICK_R1
Jun  4 10:38:41 ubuntuvpn pluto[1828]: "L2TP-PSK-NAT"[2] 220.220.220.97 #4: STATE_QUICK_R1: sent QR1, inbound IPsec SA installed, expecting QI2
Jun  4 10:38:41 ubuntuvpn pluto[1828]: "L2TP-PSK-NAT"[2] 220.220.220.97 #4: Dead Peer Detection (RFC 3706): not enabled because peer did not advertise it
Jun  4 10:38:41 ubuntuvpn pluto[1828]: "L2TP-PSK-NAT"[2] 220.220.220.97 #4: transition from state STATE_QUICK_R1 to state STATE_QUICK_R2
Jun  4 10:38:41 ubuntuvpn pluto[1828]: "L2TP-PSK-NAT"[2] 220.220.220.97 #4: STATE_QUICK_R2: IPsec SA established transport mode {ESP/NAT=>0x4d942577 <0x212e8af6 xfrm=AES_128-HMAC_SHA1 NATOA=10.10.10.161 NATD=220.220.220.97:4500 DPD=none}
Jun  4 10:38:41 ubuntuvpn pluto[1828]: "L2TP-PSK-NAT"[2] 220.220.220.97 #1: received Delete SA(0x4c6b122e) payload: deleting IPSEC State #3
Jun  4 10:38:41 ubuntuvpn pluto[1828]: "L2TP-PSK-NAT"[2] 220.220.220.97 #1: received and ignored informational message
Jun  4 10:38:45 ubuntuvpn pluto[1828]: "L2TP-PSK-NAT"[2] 220.220.220.97 #1: the peer proposed: 200.200.200.145/32:17/1701 -> 10.10.10.161/32:17/1701
Jun  4 10:38:45 ubuntuvpn pluto[1828]: "L2TP-PSK-NAT"[2] 220.220.220.97 #1: NAT-Traversal: received 2 NAT-OA. using first, ignoring others
Jun  4 10:38:45 ubuntuvpn pluto[1828]: "L2TP-PSK-NAT"[2] 220.220.220.97 #5: responding to Quick Mode proposal {msgid:04000000}
Jun  4 10:38:45 ubuntuvpn pluto[1828]: "L2TP-PSK-NAT"[2] 220.220.220.97 #5:     us: 200.200.200.145<200.200.200.145>:17/1701
Jun  4 10:38:45 ubuntuvpn pluto[1828]: "L2TP-PSK-NAT"[2] 220.220.220.97 #5:   them: 220.220.220.97[10.10.10.161]:17/1701===10.10.10.161/32
Jun  4 10:38:45 ubuntuvpn pluto[1828]: "L2TP-PSK-NAT"[2] 220.220.220.97 #5: keeping refhim=4294901761 during rekey
Jun  4 10:38:45 ubuntuvpn pluto[1828]: "L2TP-PSK-NAT"[2] 220.220.220.97 #5: transition from state STATE_QUICK_R0 to state STATE_QUICK_R1
Jun  4 10:38:45 ubuntuvpn pluto[1828]: "L2TP-PSK-NAT"[2] 220.220.220.97 #5: STATE_QUICK_R1: sent QR1, inbound IPsec SA installed, expecting QI2
Jun  4 10:38:45 ubuntuvpn pluto[1828]: "L2TP-PSK-NAT"[2] 220.220.220.97 #5: Dead Peer Detection (RFC 3706): not enabled because peer did not advertise it
Jun  4 10:38:45 ubuntuvpn pluto[1828]: "L2TP-PSK-NAT"[2] 220.220.220.97 #5: transition from state STATE_QUICK_R1 to state STATE_QUICK_R2
Jun  4 10:38:45 ubuntuvpn pluto[1828]: "L2TP-PSK-NAT"[2] 220.220.220.97 #5: STATE_QUICK_R2: IPsec SA established transport mode {ESP/NAT=>0xfaee9a12 <0x135b3fd8 xfrm=AES_128-HMAC_SHA1 NATOA=10.10.10.161 NATD=220.220.220.97:4500 DPD=none}
Jun  4 10:38:45 ubuntuvpn pluto[1828]: "L2TP-PSK-NAT"[2] 220.220.220.97 #1: received Delete SA(0x4d942577) payload: deleting IPSEC State #4
Jun  4 10:38:45 ubuntuvpn pluto[1828]: "L2TP-PSK-NAT"[2] 220.220.220.97 #1: received and ignored informational message
Jun  4 10:38:53 ubuntuvpn pluto[1828]: "L2TP-PSK-NAT"[2] 220.220.220.97 #1: the peer proposed: 200.200.200.145/32:17/1701 -> 10.10.10.161/32:17/1701
Jun  4 10:38:53 ubuntuvpn pluto[1828]: "L2TP-PSK-NAT"[2] 220.220.220.97 #1: NAT-Traversal: received 2 NAT-OA. using first, ignoring others
Jun  4 10:38:53 ubuntuvpn pluto[1828]: "L2TP-PSK-NAT"[2] 220.220.220.97 #6: responding to Quick Mode proposal {msgid:05000000}
Jun  4 10:38:53 ubuntuvpn pluto[1828]: "L2TP-PSK-NAT"[2] 220.220.220.97 #6:     us: 200.200.200.145<200.200.200.145>:17/1701
Jun  4 10:38:53 ubuntuvpn pluto[1828]: "L2TP-PSK-NAT"[2] 220.220.220.97 #6:   them: 220.220.220.97[10.10.10.161]:17/1701===10.10.10.161/32
Jun  4 10:38:53 ubuntuvpn pluto[1828]: "L2TP-PSK-NAT"[2] 220.220.220.97 #6: keeping refhim=4294901761 during rekey
Jun  4 10:38:53 ubuntuvpn pluto[1828]: "L2TP-PSK-NAT"[2] 220.220.220.97 #6: transition from state STATE_QUICK_R0 to state STATE_QUICK_R1
Jun  4 10:38:53 ubuntuvpn pluto[1828]: "L2TP-PSK-NAT"[2] 220.220.220.97 #6: STATE_QUICK_R1: sent QR1, inbound IPsec SA installed, expecting QI2
Jun  4 10:38:53 ubuntuvpn pluto[1828]: "L2TP-PSK-NAT"[2] 220.220.220.97 #6: Dead Peer Detection (RFC 3706): not enabled because peer did not advertise it
Jun  4 10:38:53 ubuntuvpn pluto[1828]: "L2TP-PSK-NAT"[2] 220.220.220.97 #6: transition from state STATE_QUICK_R1 to state STATE_QUICK_R2
Jun  4 10:38:53 ubuntuvpn pluto[1828]: "L2TP-PSK-NAT"[2] 220.220.220.97 #6: STATE_QUICK_R2: IPsec SA established transport mode {ESP/NAT=>0x739ad68f <0xea7e39fc xfrm=AES_128-HMAC_SHA1 NATOA=10.10.10.161 NATD=220.220.220.97:4500 DPD=none}
Jun  4 10:38:53 ubuntuvpn pluto[1828]: "L2TP-PSK-NAT"[2] 220.220.220.97 #1: received Delete SA(0xfaee9a12) payload: deleting IPSEC State #5
Jun  4 10:38:53 ubuntuvpn pluto[1828]: "L2TP-PSK-NAT"[2] 220.220.220.97 #1: received and ignored informational message
Jun  4 10:39:03 ubuntuvpn pluto[1828]: "L2TP-PSK-NAT"[2] 220.220.220.97 #1: the peer proposed: 200.200.200.145/32:17/1701 -> 10.10.10.161/32:17/1701
Jun  4 10:39:03 ubuntuvpn pluto[1828]: "L2TP-PSK-NAT"[2] 220.220.220.97 #1: NAT-Traversal: received 2 NAT-OA. using first, ignoring others
Jun  4 10:39:03 ubuntuvpn pluto[1828]: "L2TP-PSK-NAT"[2] 220.220.220.97 #7: responding to Quick Mode proposal {msgid:06000000}
Jun  4 10:39:03 ubuntuvpn pluto[1828]: "L2TP-PSK-NAT"[2] 220.220.220.97 #7:     us: 200.200.200.145<200.200.200.145>:17/1701
Jun  4 10:39:03 ubuntuvpn pluto[1828]: "L2TP-PSK-NAT"[2] 220.220.220.97 #7:   them: 220.220.220.97[10.10.10.161]:17/1701===10.10.10.161/32
Jun  4 10:39:03 ubuntuvpn pluto[1828]: "L2TP-PSK-NAT"[2] 220.220.220.97 #7: keeping refhim=4294901761 during rekey
Jun  4 10:39:03 ubuntuvpn pluto[1828]: "L2TP-PSK-NAT"[2] 220.220.220.97 #7: transition from state STATE_QUICK_R0 to state STATE_QUICK_R1
Jun  4 10:39:03 ubuntuvpn pluto[1828]: "L2TP-PSK-NAT"[2] 220.220.220.97 #7: STATE_QUICK_R1: sent QR1, inbound IPsec SA installed, expecting QI2
Jun  4 10:39:03 ubuntuvpn pluto[1828]: "L2TP-PSK-NAT"[2] 220.220.220.97 #7: Dead Peer Detection (RFC 3706): not enabled because peer did not advertise it
Jun  4 10:39:03 ubuntuvpn pluto[1828]: "L2TP-PSK-NAT"[2] 220.220.220.97 #7: transition from state STATE_QUICK_R1 to state STATE_QUICK_R2
Jun  4 10:39:03 ubuntuvpn pluto[1828]: "L2TP-PSK-NAT"[2] 220.220.220.97 #7: STATE_QUICK_R2: IPsec SA established transport mode {ESP/NAT=>0xc3ef0b1a <0x5d07ed5d xfrm=AES_128-HMAC_SHA1 NATOA=10.10.10.161 NATD=220.220.220.97:4500 DPD=none}
Jun  4 10:39:03 ubuntuvpn pluto[1828]: "L2TP-PSK-NAT"[2] 220.220.220.97 #1: received Delete SA(0x739ad68f) payload: deleting IPSEC State #6
Jun  4 10:39:03 ubuntuvpn pluto[1828]: "L2TP-PSK-NAT"[2] 220.220.220.97 #1: received and ignored informational message
Jun  4 10:39:13 ubuntuvpn pluto[1828]: "L2TP-PSK-NAT"[2] 220.220.220.97 #1: received Delete SA(0xc3ef0b1a) payload: deleting IPSEC State #7
Jun  4 10:39:13 ubuntuvpn pluto[1828]: "L2TP-PSK-NAT"[2] 220.220.220.97 #1: ERROR: netlink XFRM_MSG_DELPOLICY response for flow eroute_connection delete included errno 2: No such file or directory
Jun  4 10:39:13 ubuntuvpn pluto[1828]: "L2TP-PSK-NAT"[2] 220.220.220.97 #1: received and ignored informational message
Jun  4 10:39:13 ubuntuvpn pluto[1828]: "L2TP-PSK-NAT"[2] 220.220.220.97 #1: received Delete SA payload: deleting ISAKMP State #1
Jun  4 10:39:13 ubuntuvpn pluto[1828]: "L2TP-PSK-NAT"[2] 220.220.220.97: deleting connection "L2TP-PSK-NAT" instance with peer 220.220.220.97 {isakmp=#0/ipsec=#0}
Jun  4 10:39:13 ubuntuvpn pluto[1828]: packet from 220.220.220.97:4500: received and ignored informational message
```

Also after starting and attempting a connection, /var/log/syslog:
```
Jun  4 10:38:26 ubuntuvpn kernel: [ 2818.085360] NET: Registered protocol family 15Jun  4 10:38:26 ubuntuvpn ipsec_setup: Starting Openswan IPsec U2.6.38/K3.2.0-26-generic-pae...
Jun  4 10:38:26 ubuntuvpn ipsec_setup: Using NETKEY(XFRM) stack
Jun  4 10:38:26 ubuntuvpn kernel: [ 2818.124262] Initializing XFRM netlink socket
Jun  4 10:38:26 ubuntuvpn kernel: [ 2818.128691] padlock_sha: VIA PadLock Hash Engine not detected.
Jun  4 10:38:26 ubuntuvpn kernel: [ 2818.130801] Intel AES-NI instructions are not detected.
Jun  4 10:38:26 ubuntuvpn kernel: [ 2818.134794] Intel AES-NI instructions are not detected.
Jun  4 10:38:26 ubuntuvpn ipsec_setup: ...Openswan IPsec started
Jun  4 10:38:26 ubuntuvpn xl2tpd[1826]: IPsec SAref does not work with L2TP kernel mode yet, enabling forceuserspace=yes
Jun  4 10:38:26 ubuntuvpn xl2tpd[1826]: setsockopt recvref[30]: Protocol not available
Jun  4 10:38:26 ubuntuvpn xl2tpd[1826]: This binary does not support kernel L2TP.
Jun  4 10:38:26 ubuntuvpn xl2tpd[1829]: xl2tpd version xl2tpd-1.3.1 started on ubuntuvpn PID:1829
Jun  4 10:38:26 ubuntuvpn xl2tpd[1829]: Written by Mark Spencer, Copyright (C) 1998, Adtran, Inc.
Jun  4 10:38:26 ubuntuvpn xl2tpd[1829]: Forked by Scott Balmos and David Stipp, (C) 2001
Jun  4 10:38:26 ubuntuvpn xl2tpd[1829]: Inherited by Jeff McAdams, (C) 2002
Jun  4 10:38:26 ubuntuvpn xl2tpd[1829]: Forked again by Xelerance (www.xelerance.com) (C) 2006
Jun  4 10:38:26 ubuntuvpn xl2tpd[1829]: Listening on IP address 0.0.0.0, port 1701
Jun  4 10:38:26 ubuntuvpn ipsec__plutorun: adjusting ipsec.d to /etc/ipsec.d
Jun  4 10:38:26 ubuntuvpn pluto: adjusting ipsec.d to /etc/ipsec.d
Jun  4 10:38:26 ubuntuvpn ipsec__plutorun: 002 added connection description "L2TP-PSK-NAT"
Jun  4 10:38:26 ubuntuvpn ipsec__plutorun: 002 added connection description "L2TP-PSK-noNAT"
```

Is there anything obvious I am missing?  I have been working on this for over a week now and I'm not making any headway.  I should add that I was able to connect from my iPad last night from home.

Thank you
-Jon

---

### Post by j_zuilkowski on 2013-06-04
I should have also stated that I am running Ubuntu 12.04.2 LTS Server

---

### Post by prodigy_ on 2013-06-04
Do you specifically need L2TP? Because OpenVPN is much easier to configure.

---

### Post by j_zuilkowski on 2013-06-04
Unfortunately yes, I specifically need l2tp.  I have to support what's built in to windows and mac

---

### Post by j_zuilkowski on 2013-06-04
If I am reading this correctly, IPSEC is properly negotiating and establishing a connection - "IPsec SA established transport mode"

But it will disconnect/reconnect several times, then fail.

---

### Post by xtdv on 2013-07-04
> **j_zuilkowski said:**
> If I am reading this correctly, IPSEC is properly negotiating and establishing a connection - "IPsec SA established transport mode"

But it will disconnect/reconnect several times, then fail.

I have the same issue with you. Following this post [http://support.microsoft.com/kb/310109](http://support.microsoft.com/kb/310109) will make Windows successfuly connect to VPN server but it's also disabe the IPSec encryption.

I'm still looking for a better solutions...

---

### Post by halfgaar on 2013-07-17
I have a similar problem (also on 12.04, kernel 3.2.0-49-generic). I tried with a Windows 8 client.

The real error seems to be:

```

ERROR: netlink XFRM_MSG_DELPOLICY response for flow eroute_connection delete included errno 2: No such file or directory

```

I cannot figure out what this is. [One source]("http://tuohuang.info/solve-openswan-l2tp-netlink-XFRM_MSG_DELPOLICY-error/") states a newer version of Openswan fixed it, but my version is much newer than the version specified. I also read stuff about kernel bugs.

Is there anybody who knows what this is? Should we file a bug report?

---

### Post by halfgaar on 2013-07-17
Actually, I solved mine. If you look at [this howto]("http://blog.riobard.com/2010/04/30/l2tp-over-ipsec-ubuntu/"), you'll see the options are a little bit different.

xl2tpd.conf has:

```

refuse chap = yes
refuse pap = yes

```

and /etc/ppp/options.xl2tpd has:

```

require-mschap-v2
refuse-mschap # I added that one

```

What I do wonder about, though, is security. PPTP uses mschap-v2 as well, and that has been royally cracked. IPsec should provide the security, but I don't know how chap-v2 factors into this.

---

