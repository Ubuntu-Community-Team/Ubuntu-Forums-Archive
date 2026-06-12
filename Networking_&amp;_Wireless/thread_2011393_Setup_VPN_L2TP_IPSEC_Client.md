---
title: "Setup VPN L2TP IPSEC Client"
date: 2012-06-27
forum: Networking &amp; Wireless
---

### Post by sportsdude81 on 2012-06-27
I am using L2TP Ipsec VPN Applet to connect to a VPN server.  I can't seem to get it to work though.  The "pluto" process keeps timing out, but I am not sure what to look at to fix this.  Here is my log:

```
Jun 27 10:57:37.007 ipsec_setup: Starting Openswan IPsec U2.6.37/K3.2.0-25-generic...
Jun 27 10:57:37.289 ipsec__plutorun: Starting Pluto subsystem...
Jun 27 10:57:37.298 ipsec__plutorun: adjusting ipsec.d to /etc/ipsec.d
Jun 27 10:57:37.306 recvref[30]: Protocol not available
Jun 27 10:57:37.307 xl2tpd[4460]: This binary does not support kernel L2TP.
Jun 27 10:57:37.307 Starting xl2tpd: xl2tpd.
Jun 27 10:57:37.309 xl2tpd[4463]: xl2tpd version xl2tpd-1.3.1 started on maverick PID:4463
Jun 27 10:57:37.309 xl2tpd[4463]: Written by Mark Spencer, Copyright (C) 1998, Adtran, Inc.
Jun 27 10:57:37.309 xl2tpd[4463]: Forked by Scott Balmos and David Stipp, (C) 2001
Jun 27 10:57:37.312 xl2tpd[4463]: Inherited by Jeff McAdams, (C) 2002
Jun 27 10:57:37.312 xl2tpd[4463]: Forked again by Xelerance (www.xelerance.com) (C) 2006
Jun 27 10:57:37.313 xl2tpd[4463]: Listening on IP address 0.0.0.0, port 1701
Jun 27 10:57:37.356 ipsec__plutorun: 002 added connection description "TA_VPN"
Jun 27 10:58:56.967 Last command timed out
Jun 27 10:58:57.002 Stopping xl2tpd: xl2tpd.
Jun 27 10:58:57.004 xl2tpd[4463]: death_handler: Fatal signal 15 received
Jun 27 10:58:57.024 ipsec_setup: Stopping Openswan IPsec...

```

I am running Ubuntu Precise and have xl2tpd version 1.3.1.  Any help would be much appreciated.

Could this be caused because the VPN server is on NAT'd network?

---

### Post by sportsdude81 on 2012-06-28
This sort of a bump, but I realize now that the pluto process is ipsec processes.  So I ran ipsec verify and got:

```
sudo ipsec verify
Checking your system to see if IPsec got installed and started correctly:
Version check and ipsec on-path                             	[OK]
Linux Openswan U2.6.37/K3.2.0-25-generic (netkey)
Checking for IPsec support in kernel                        	[OK]
 SAref kernel support                                       	[N/A]
 NETKEY:  Testing XFRM related proc values                  	[FAILED]

  Please disable /proc/sys/net/ipv4/conf/*/send_redirects
  or NETKEY will cause the sending of bogus ICMP redirects!

	[FAILED]

  Please disable /proc/sys/net/ipv4/conf/*/accept_redirects
  or NETKEY will accept bogus ICMP redirects!

	[OK]
Checking that pluto is running                              	[OK]
 Pluto listening for IKE on udp 500                         	[OK]
 Pluto listening for NAT-T on udp 4500                      	[OK]
Two or more interfaces found, checking IP forwarding        	[FAILED]
Checking for 'ip' command                                   	[OK]
Checking /bin/sh is not /bin/dash                           	[WARNING]
Checking for 'iptables' command                             	[OK]
Opportunistic Encryption Support                            	[DISABLED]
```

Not sure how to fix the failed fields or if they are even relevant

---

### Post by sportsdude81 on 2012-06-28
I am also getting an error 93 in syslog which means according to the source I found:

EPROTONOSUPPORT 93 / * Protocol not supported * /

WTF?

```
Jun 28 16:15:22 maverick xl2tpd[3577]: Listening on IP address 0.0.0.0, port 1701
Jun 28 16:15:22 maverick L2tpIPsecVpnControlDaemon: Command service xl2tpd start finished with exit code 0
Jun 28 16:15:22 maverick ipsec__plutorun: 002 added connection description "TA_VPN"
Jun 28 16:15:22 maverick L2tpIPsecVpnControlDaemon: Executing command ipsec auto --ready
Jun 28 16:15:22 maverick L2tpIPsecVpnControlDaemon: Command ipsec auto --ready finished with exit code 0
Jun 28 16:15:22 maverick L2tpIPsecVpnControlDaemon: Executing command ipsec auto --up TA_VPN
Jun 28 16:16:40 maverick L2tpIPsecVpnControlDaemon: Closing client connection
Jun 28 16:16:40 maverick L2tpIPsecVpnControlDaemon: Command ipsec auto --up TA_VPN finished with error code 93
Jun 28 16:16:40 maverick L2tpIPsecVpnControlDaemon: Command ipsec auto --up TA_VPN finished with exit code 0
Jun 28 16:16:40 maverick L2tpIPsecVpnControlDaemon: Opening client connection
Jun 28 16:16:40 maverick L2tpIPsecVpnControlDaemon: Executing command service xl2tpd stop
Jun 28 16:16:40 maverick xl2tpd[3577]: death_handler: Fatal signal 15 received

```

---

### Post by sportsdude81 on 2012-06-28
According to auth.log it can see the server but it rejects the server because the server is in a NAT'd network and has a private IP address instead of the public one I am specifying.  Does anyone know how to remedy this in L2TP IPsec VPN Manager 1.0.7?

Any help would be much appreciated.

```
Jun 28 16:52:41 maverick pluto[5023]: "TA_VPN" #1: STATE_MAIN_I3: sent MI3, expecting MR3
Jun 28 16:52:41 maverick pluto[5023]: "TA_VPN" #1: Main mode peer ID is ID_IPV4_ADDR: '10.0.1.2'
Jun 28 16:52:41 maverick pluto[5023]: "TA_VPN" #1: we require peer to have ID '123.123.123.123', but peer declares '10.0.1.2'
Jun 28 16:52:41 maverick pluto[5023]: "TA_VPN" #1: sending encrypted notification INVALID_ID_INFORMATION to 123.123.123.123:4500
Jun 28 16:52:41 maverick pluto[5023]: "TA_VPN" #1: next payload type of ISAKMP Hash Payload has an unknown value: 240
Jun 28 16:52:41 maverick pluto[5023]: "TA_VPN" #1: malformed payload in packet
Jun 28 16:52:41 maverick pluto[5023]: | payload malformed after IV
Jun 28 16:52:41 maverick pluto[5023]: |   c5 50 6c 9c  39 23 31 cc
Jun 28 16:52:41 maverick pluto[5023]: "TA_VPN" #1: sending notification PAYLOAD_MALFORMED to 123.123.123.123:4500
Jun 28 16:54:00 maverick pluto[5023]: shutting down

```

---

### Post by sportsdude81 on 2012-06-29
Bump and more info.  Here is my Server host setup:


Mac OSX server---->NAT-----> Internet <------NAT<-------Host

I have set the "Server Identity" field in L2TP IPsec VPN Manager 1.0.7 and that seemed to fix the issue I stated above about the Mac OSX server being NAT'd.  I am still getting a Malformed packet error.  I am getting closer... here is the new log from the VPN Manager.

```
Jun 29 11:37:53.408 ipsec_setup: Starting Openswan IPsec U2.6.37/K3.2.0-25-generic...
Jun 29 11:37:53.719 ipsec__plutorun: Starting Pluto subsystem...
Jun 29 11:37:53.731 ipsec__plutorun: adjusting ipsec.d to /etc/ipsec.d
Jun 29 11:37:53.737 recvref[30]: Protocol not available
Jun 29 11:37:53.737 xl2tpd[11716]: This binary does not support kernel L2TP.
Jun 29 11:37:53.737 Starting xl2tpd: xl2tpd.
Jun 29 11:37:53.738 xl2tpd[11719]: xl2tpd version xl2tpd-1.3.1 started on maverick PID:11719
Jun 29 11:37:53.738 xl2tpd[11719]: Written by Mark Spencer, Copyright (C) 1998, Adtran, Inc.
Jun 29 11:37:53.739 xl2tpd[11719]: Forked by Scott Balmos and David Stipp, (C) 2001
Jun 29 11:37:53.740 xl2tpd[11719]: Inherited by Jeff McAdams, (C) 2002
Jun 29 11:37:53.740 xl2tpd[11719]: Forked again by Xelerance (www.xelerance.com) (C) 2006
Jun 29 11:37:53.740 xl2tpd[11719]: Listening on IP address 0.0.0.0, port 1701
Jun 29 11:37:53.780 ipsec__plutorun: 002 added connection description "TA_VPN"
Jun 29 11:39:04.569 104 "TA_VPN" #1: STATE_MAIN_I1: initiate
Jun 29 11:39:04.570 003 "TA_VPN" #1: received Vendor ID payload [RFC 3947] method set to=109 
Jun 29 11:39:04.570 003 "TA_VPN" #1: received Vendor ID payload [Dead Peer Detection]
Jun 29 11:39:04.571 106 "TA_VPN" #1: STATE_MAIN_I2: sent MI2, expecting MR2
Jun 29 11:39:04.571 003 "TA_VPN" #1: NAT-Traversal: Result using RFC 3947 (NAT-Traversal): both are NATed
Jun 29 11:39:04.572 108 "TA_VPN" #1: STATE_MAIN_I3: sent MI3, expecting MR3
Jun 29 11:39:04.572 004 "TA_VPN" #1: STATE_MAIN_I4: ISAKMP SA established {auth=OAKLEY_PRESHARED_KEY cipher=oakley_3des_cbc_192 prf=oakley_sha group=modp1024}
Jun 29 11:39:04.573 117 "TA_VPN" #2: STATE_QUICK_I1: initiate
Jun 29 11:39:04.573 003 "TA_VPN" #2: length of ISAKMP Notification Payload is smaller than minimum
Jun 29 11:39:04.574 003 "TA_VPN" #2: malformed payload in packet
Jun 29 11:39:04.574 003 "TA_VPN" #2: length of ISAKMP Notification Payload is smaller than minimum
Jun 29 11:39:04.574 003 "TA_VPN" #2: malformed payload in packet
Jun 29 11:39:04.575 003 "TA_VPN" #2: length of ISAKMP Notification Payload is smaller than minimum
Jun 29 11:39:04.575 003 "TA_VPN" #2: malformed payload in packet
Jun 29 11:39:04.576 003 "TA_VPN" #2: length of ISAKMP Notification Payload is smaller than minimum
Jun 29 11:39:04.576 003 "TA_VPN" #2: malformed payload in packet
Jun 29 11:39:04.576 010 "TA_VPN" #2: STATE_QUICK_I1: retransmission; will wait 20s for response
Jun 29 11:39:04.577 003 "TA_VPN" #2: length of ISAKMP Notification Payload is smaller than minimum
Jun 29 11:39:04.577 003 "TA_VPN" #2: malformed payload in packet
Jun 29 11:39:04.578 003 "TA_VPN" #2: length of ISAKMP Notification Payload is smaller than minimum
Jun 29 11:39:04.578 003 "TA_VPN" #2: malformed payload in packet
Jun 29 11:39:04.579 003 "TA_VPN" #2: length of ISAKMP Notification Payload is smaller than minimum
Jun 29 11:39:04.579 003 "TA_VPN" #2: malformed payload in packet
Jun 29 11:39:04.579 003 "TA_VPN" #2: length of ISAKMP Notification Payload is smaller than minimum
Jun 29 11:39:04.580 003 "TA_VPN" #2: malformed payload in packet
Jun 29 11:39:04.580 003 "TA_VPN" #2: length of ISAKMP Notification Payload is smaller than minimum
Jun 29 11:39:04.581 003 "TA_VPN" #2: malformed payload in packet
Jun 29 11:39:04.581 003 "TA_VPN" #2: length of ISAKMP Notification Payload is smaller than minimum
Jun 29 11:39:04.582 003 "TA_VPN" #2: malformed payload in packet
Jun 29 11:39:04.582 003 "TA_VPN" #2: length of ISAKMP Notification Payload is smaller than minimum
Jun 29 11:39:04.582 003 "TA_VPN" #2: malformed payload in packet
Jun 29 11:39:04.583 010 "TA_VPN" #2: STATE_QUICK_I1: retransmission; will wait 40s for response
Jun 29 11:39:04.583 003 "TA_VPN" #2: length of ISAKMP Notification Payload is smaller than minimum
Jun 29 11:39:04.584 003 "TA_VPN" #2: malformed payload in packet
Jun 29 11:39:04.584 031 "TA_VPN" #2: max number of retransmissions (2) reached STATE_QUICK_I1.  No acceptable response to our first Quick Mode message: perhaps peer likes no proposal
Jun 29 11:39:04.585 000 "TA_VPN" #2: starting keying attempt 2 of at most 3, but releasing whack
Jun 29 11:39:04.586 [ERROR  300]   'IPsec' failed to negotiate or establish security associations
Jun 29 11:39:08.683 xl2tpd[11719]: death_handler: Fatal signal 15 received
Jun 29 11:39:08.684 Stopping xl2tpd: xl2tpd.
Jun 29 11:39:08.696 ipsec_setup: Stopping Openswan IPsec...

```

---

### Post by mikafri on 2012-10-10
Any updates on this thread? I'm in same situation with sportsdude81, just can't find out how to fix theNATted Mac OSx Server issue. Getting similar log.

All replies are welcome :)

---

### Post by sportsdude81 on 2012-10-10
> **mikafri said:**
> Any updates on this thread? I'm in same situation with sportsdude81, just can't find out how to fix theNATted Mac OSx Server issue. Getting similar log.

All replies are welcome :)

Never found a solution. Have to switch to windows to do any VPN stuff  ](*,).  Hopefully someone gots the answers

---

### Post by mikafri on 2012-10-10
> **sportsdude81 said:**
> Never found a solution. Have to switch to windows to do any VPN stuff  ](*,).  Hopefully someone gots the answers

Thanks for the answer, I've been banging my head to the wall for few days now.. Gotta give up soon if no one have the answer, and change to windows as well.

---

### Post by cmsdloma on 2012-12-11
Hi all,

I've managed to set up a Ubuntu Server at home (behind NAT), and I've got the following types of VPN all working: OpenVPN, PPTP, L2TP over IPSEC.  I can connect to all of them okay from my laptop away from home (roadwarrior setup).  I can even connect to L2TP over IPSEC fine from my iPhone and iPad.

I've been trying to set up a VPN client from a Ubuntu Desktop (Precise x32) but I'm also struggling with OpenSwan.  My Ubuntu Desktop is in a bridged VM on my roadwarrior laptop, so the journey is something like:

Ubuntu VM -> NAT (192.168.1.x) -> {Internet} -> NAT {192.168.42.y} -> UbuntuSrv

The same path works from a Windows VM, so this would seem to just be a configuration issue with my OpenSwan client, maybe I'm being stupid.  Here's my /etc/ipsec.conf:

```

# /etc/ipsec.conf - Openswan IPsec configuration file

# This file:  /usr/share/doc/openswan/ipsec.conf-sample
#
# Manual:     ipsec.conf.5

version    2.0    # conforms to second version of ipsec.conf specification

# basic configuration
    dumpdir=/var/run/pluto/
    interfaces=%defaultroute
    nat_traversal=yes
    virtual_private=%v4:10.0.0.0/8,%v4:192.168.0.0/16,%v4:172.16.0.0/12,%v4:25.0.0.0/8,%v6:fd00::/8,%v6:fe80::/10
    oe=off
    protostack=auto

# Add connections here

conn L2TP-PSK-NAT
    rightsubnet=vhost:%priv
    #rightsubnet=vhost:%no,%priv    # Bit confused here, but tried both
    also=L2TP-PSK-noNAT

conn L2TP-PSK-noNAT
    authby=secret
    pfs=no
    auto=add
    keyingtries=3
    rekey=no
    ikelifetime=8h
    keylife=1h
    type=transport
    left=%any
    leftid=@ubuntu
    #leftsubnet=192.168.1.0/24     # Tried this, didn't make a difference
    leftnexthop=%defaultroute
    leftprotoport=17/%any
    right=86.151.218.43
    rightid=@oberth.dyndns.org
    rightprotoport=17/1701

```

I tried to make 'left' the local, and 'right' the remote, but may have gotten slightly confused :confused:

My /etc/ipsec.secrets just includes /var/lib/openswan/ipsec.secrets.inc, which contains:

```

:       PSK     "mypsk"

```

System config:

```

uname -r
3.2.0-34-generic

ipsec -- version
Linux Openswan U2.6.37/K3.2.0-34-generic (netkey)
See `ipsec --copyright' for copyright information.

ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0c:29:92:c0:26  
          inet addr:192.168.1.72  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20c:29ff:fe92:c026/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:39841 errors:0 dropped:0 overruns:0 frame:0
          TX packets:23339 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:39020329 (39.0 MB)  TX bytes:2385719 (2.3 MB)
          Interrupt:19 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:804 errors:0 dropped:0 overruns:0 frame:0
          TX packets:804 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:81027 (81.0 KB)  TX bytes:81027 (81.0 KB)

```

(I've turned on IP forwarding, etc.)

Here is my auth.log:

```

Dec 11 22:38:49 ubuntu ipsec__plutorun: Starting Pluto subsystem...
Dec 11 22:38:49 ubuntu pluto[8525]: Starting Pluto (Openswan Version 2.6.37; Vendor ID OEu\134d\134jy\134\134ap) pid:8525
Dec 11 22:38:49 ubuntu pluto[8525]: LEAK_DETECTIVE support [disabled]
Dec 11 22:38:49 ubuntu pluto[8525]: OCF support for IKE [disabled]
Dec 11 22:38:49 ubuntu pluto[8525]: SAref support [disabled]: Protocol not available
Dec 11 22:38:49 ubuntu pluto[8525]: SAbind support [disabled]: Protocol not available
Dec 11 22:38:49 ubuntu pluto[8525]: NSS support [disabled]
Dec 11 22:38:49 ubuntu pluto[8525]: HAVE_STATSD notification support not compiled in
Dec 11 22:38:49 ubuntu pluto[8525]: Setting NAT-Traversal port-4500 floating to on
Dec 11 22:38:49 ubuntu pluto[8525]:    port floating activation criteria nat_t=1/port_float=1
Dec 11 22:38:49 ubuntu pluto[8525]:    NAT-Traversal support  [enabled]
Dec 11 22:38:49 ubuntu pluto[8525]: using /dev/urandom as source of random entropy
Dec 11 22:38:49 ubuntu pluto[8525]: ike_alg_register_enc(): Activating OAKLEY_AES_CBC: Ok (ret=0)
Dec 11 22:38:49 ubuntu pluto[8525]: starting up 3 cryptographic helpers
Dec 11 22:38:49 ubuntu pluto[8525]: started helper pid=8528 (fd:6)
Dec 11 22:38:49 ubuntu pluto[8525]: started helper pid=8529 (fd:7)
Dec 11 22:38:49 ubuntu pluto[8525]: started helper pid=8530 (fd:8)
Dec 11 22:38:49 ubuntu pluto[8525]: Kernel interface auto-pick
Dec 11 22:38:49 ubuntu pluto[8525]: Using Linux 2.6 IPsec interface code on 3.2.0-34-generic (experimental code)
Dec 11 22:38:49 ubuntu pluto[8529]: using /dev/urandom as source of random entropy
Dec 11 22:38:49 ubuntu pluto[8528]: using /dev/urandom as source of random entropy
Dec 11 22:38:49 ubuntu pluto[8530]: using /dev/urandom as source of random entropy
Dec 11 22:38:49 ubuntu pluto[8525]: ike_alg_register_enc(): Activating aes_ccm_8: Ok (ret=0)
Dec 11 22:38:49 ubuntu pluto[8525]: ike_alg_add(): ERROR: Algorithm already exists
Dec 11 22:38:49 ubuntu pluto[8525]: ike_alg_register_enc(): Activating aes_ccm_12: FAILED (ret=-17)
Dec 11 22:38:49 ubuntu pluto[8525]: ike_alg_add(): ERROR: Algorithm already exists
Dec 11 22:38:49 ubuntu pluto[8525]: ike_alg_register_enc(): Activating aes_ccm_16: FAILED (ret=-17)
Dec 11 22:38:49 ubuntu pluto[8525]: ike_alg_add(): ERROR: Algorithm already exists
Dec 11 22:38:49 ubuntu pluto[8525]: ike_alg_register_enc(): Activating aes_gcm_8: FAILED (ret=-17)
Dec 11 22:38:49 ubuntu pluto[8525]: ike_alg_add(): ERROR: Algorithm already exists
Dec 11 22:38:49 ubuntu pluto[8525]: ike_alg_register_enc(): Activating aes_gcm_12: FAILED (ret=-17)
Dec 11 22:38:49 ubuntu pluto[8525]: ike_alg_add(): ERROR: Algorithm already exists
Dec 11 22:38:49 ubuntu pluto[8525]: ike_alg_register_enc(): Activating aes_gcm_16: FAILED (ret=-17)
Dec 11 22:38:49 ubuntu pluto[8525]: Changed path to directory '/etc/ipsec.d/cacerts'
Dec 11 22:38:49 ubuntu pluto[8525]: Changed path to directory '/etc/ipsec.d/aacerts'
Dec 11 22:38:49 ubuntu pluto[8525]: Changed path to directory '/etc/ipsec.d/ocspcerts'
Dec 11 22:38:49 ubuntu pluto[8525]: Changing to directory '/etc/ipsec.d/crls'
Dec 11 22:38:49 ubuntu pluto[8525]:   Warning: empty directory
Dec 11 22:38:49 ubuntu pluto[8525]: added connection description "L2TP-PSK-NAT"
Dec 11 22:38:49 ubuntu pluto[8525]: added connection description "L2TP-PSK-noNAT"
Dec 11 22:38:49 ubuntu pluto[8525]: listening for IKE messages
Dec 11 22:38:49 ubuntu pluto[8525]: adding interface eth0/eth0 192.168.1.72:500
Dec 11 22:38:49 ubuntu pluto[8525]: adding interface eth0/eth0 192.168.1.72:4500
Dec 11 22:38:49 ubuntu pluto[8525]: adding interface lo/lo 127.0.0.1:500
Dec 11 22:38:49 ubuntu pluto[8525]: adding interface lo/lo 127.0.0.1:4500
Dec 11 22:38:49 ubuntu pluto[8525]: adding interface lo/lo ::1:500
Dec 11 22:38:49 ubuntu pluto[8525]: loading secrets from "/etc/ipsec.secrets"
Dec 11 22:38:49 ubuntu pluto[8525]: loading secrets from "/var/lib/openswan/ipsec.secrets.inc"
Dec 11 22:38:52 ubuntu pluto[8525]: "L2TP-PSK-NAT": deleting connection
Dec 11 22:38:52 ubuntu pluto[8525]: added connection description "L2TP-PSK-NAT"
Dec 11 22:38:56 ubuntu pluto[8525]: "L2TP-PSK-NAT": **We cannot identify ourselves with either end of this connection**.

```

And here's my syslog:

```

Dec 11 22:38:48 ubuntu kernel: [ 8712.000693] NET: Unregistered protocol family 15
Dec 11 22:38:48 ubuntu ipsec_setup: ...Openswan IPsec stopped
Dec 11 22:38:48 ubuntu ipsec_setup: Starting Openswan IPsec 2.6.37...
Dec 11 22:38:48 ubuntu ipsec_setup: Using KLIPS/legacy stack
Dec 11 22:38:49 ubuntu kernel: [ 8712.317860] padlock_sha: VIA PadLock Hash Engine not detected.
Dec 11 22:38:49 ubuntu ipsec_setup: No KLIPS support found while requested, desperately falling back to netkey
Dec 11 22:38:49 ubuntu ipsec_setup: NETKEY support found. Use protostack=netkey in /etc/ipsec.conf to avoid attempts to use KLIPS. Attempting to continue with NETKEY
Dec 11 22:38:49 ubuntu kernel: [ 8712.548053] NET: Registered protocol family 15
Dec 11 22:38:49 ubuntu ipsec_setup: Using NETKEY(XFRM) stack
Dec 11 22:38:49 ubuntu kernel: [ 8712.729217] Initializing XFRM netlink socket
Dec 11 22:38:49 ubuntu kernel: [ 8712.779124] padlock_sha: VIA PadLock Hash Engine not detected.
Dec 11 22:38:49 ubuntu ipsec_setup: ...Openswan IPsec started
Dec 11 22:38:49 ubuntu pluto: adjusting ipsec.d to /etc/ipsec.d
Dec 11 22:38:49 ubuntu ipsec__plutorun: adjusting ipsec.d to /etc/ipsec.d
Dec 11 22:38:49 ubuntu ipsec__plutorun: 002 added connection description "L2TP-PSK-NAT"
Dec 11 22:38:49 ubuntu ipsec__plutorun: 002 added connection description "L2TP-PSK-noNAT"

```

And finally the ipsec verify output:

```

Checking your system to see if IPsec got installed and started correctly:
Version check and ipsec on-path                                 [OK]
Linux Openswan U2.6.37/K3.2.0-34-generic (netkey)
Checking for IPsec support in kernel                            [OK]
 SAref kernel support                                           [N/A]
 NETKEY:  Testing XFRM related proc values                      [FAILED]

  Please disable /proc/sys/net/ipv4/conf/*/send_redirects
  or NETKEY will cause the sending of bogus ICMP redirects!

    [FAILED]

  Please disable /proc/sys/net/ipv4/conf/*/accept_redirects
  or NETKEY will accept bogus ICMP redirects!

    [OK]
Checking that pluto is running                                  [OK]
 Pluto listening for IKE on udp 500                             [OK]
 Pluto listening for NAT-T on udp 4500                          [OK]
Checking for 'ip' command                                       [OK]
Checking /bin/sh is not /bin/dash                               [WARNING]
Checking for 'iptables' command                                 [OK]
Opportunistic Encryption Support                                [DISABLED]

```

I'm stuck on the error: We cannot identify ourselves with either end of this connection.  I can't seem to get past that.  I've tried putting the local IP address (192.168.1.72), but if I do that I get a different error:

```

root@ubuntu:/var/log# /etc/init.d/ipsec restart
ipsec_setup: Stopping Openswan IPsec...
ipsec_setup: Starting Openswan IPsec 2.6.37...
ipsec_setup: No KLIPS support found while requested, desperately falling back to netkey
ipsec_setup: NETKEY support found. Use protostack=netkey in /etc/ipsec.conf to avoid attempts to use KLIPS. Attempting to continue with NETKEY
root@ubuntu:/var/log# ipsec auto --add L2TP-PSK-NAT
023 address family inconsistency in this connection=2 host=2/nexthop=0
037 attempt to load incomplete connection

```

I'm totally puzzled!  If anyone has any clue what I'm doing wrong, please help!  I'd be so grateful, thanks!

Cheers,
Dave

---

