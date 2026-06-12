---
title: "Guide: Openswan, XL2TP and PPP on Ubuntu Maverick for iPhone VPN Connection"
date: 2010-12-14
forum: Networking &amp; Wireless
---

### Post by ndoggac on 2010-12-14
*** Working Again As of Latest Edit ***

This setup will allow you to login to your own Ubuntu VPN server using your Iphone's default IOS VPN settings.

Install the necessary packages.
sudo apt-get install openswan ppp xl2tpd


Using the following setup:

192.168.1.22 Ubuntu Server IP Address 
192.168.1.1  Gateway Internal IP

On your router, forward ports 500/udp and 4500/udp to the server at 192.168.1.22.  This procedure can be found elsewhere and is not covered here.

===================
Here&#8217;s my /etc/ipsec.conf file. 
(no changes necessary from text below)
===================
```

version 2.0

config setup
  nat_traversal=yes
  virtual_private=%v4:10.0.0.0/8,%v4:192.168.1.0/16,%v4:172.16.0.0/12
  oe=off
  protostack=netkey

include /etc/ipsec.d/l2tp-psk.conf

```
==================
Here&#8217;s my /etc/ipsec.d/l2tp-psk.conf file. 
(change left & leftnexthop values)
Important NOTE: dpd entries allow you to connect multiple times without having to restart IPSEC...Thanks to user "FTT" for this
==================
```

conn L2TP-PSK-NAT
  rightsubnet=vhost:%priv
  also=L2TP-PSK-noNAT

conn L2TP-PSK-noNAT
  authby=secret
  pfs=no
  auto=add
  keyingtries=3
  rekey=no
  type=transport
  left=192.168.1.22
  leftnexthop=192.168.1.1
  leftprotoport=17/1701
  right=%any
  rightprotoport=17/%any 
  dpddelay=15
  dpdtimeout=30
  dpdaction=clear
  #Uncomment the line below for OSX on MAC?  untested!
  #rightprotoport=17/0 

```
==================
Here's my /etc/xl2tpd/xl2tpd.conf file. 
(change ip range & local ip) 
Important NOTES: "local ip" value must be outside "ip range" 
                 Both "local ip" and "ip range" MUST be outside the DHCP range on your local router or DHCP server.
==================
```

[global]
ipsec saref = yes
[lns default]
ip range = 192.168.1.231-192.168.1.239
local ip = 192.168.1.230
refuse chap = yes
refuse pap = yes
require authentication = yes
ppp debug = yes
pppoptfile = /etc/ppp/options.xl2tpd
length bit = yes

```
==================
Here&#8217;s my /etc/ppp/options.xl2tpd file. 
(change ms-dns value)
==================
```

require-mschap-v2
ms-dns 192.168.1.1
asyncmap 0
auth
crtscts
lock
hide-password
modem
debug
name l2tpd
proxyarp
lcp-echo-interval 30
lcp-echo-failure 4

```
==================
Here&#8217;s my /etc/ppp/chap-secrets file. 
(change username & password values)
Example uses (username=test and password=testpass)
Important NOTE: The 233 IP Address must be in the "ip range" from the /etc/xl2tpd/xl2tpd.conf setting.  Repeat for additional users using different IP addresses within the range.
==================
```

test l2tpd testpass 192.168.1.233
l2tpd test testpass 192.168.1.233

```
==================
Here&#8217;s my /etc/ipsec.secrets file. (change IP address & Secret values) 
==================
```

192.168.1.22   %any:  PSK "TestSecret"

```
================

Run these three commands to restart everything

sudo /etc/init.d/pppd-dns restart
sudo /etc/init.d/xl2tpd restart
sudo /etc/init.d/ipsec restart

==================

Run the following command, you should get the text below.

sudo ipsec verify

==================

Checking your system to see if IPsec got installed and started correctly:
Version check and ipsec on-path [OK]
Linux Openswan U2.4.9/K2.6.24-23-generic (netkey)
Checking for IPsec support in kernel [OK]
NETKEY detected, testing for disabled ICMP send_redirects [OK]
NETKEY detected, testing for disabled ICMP accept_redirects [OK]
Checking for RSA private key (/etc/ipsec.secrets) [DISABLED]
ipsec showhostkey: no default key in "/etc/ipsec.secrets"
Checking that pluto is running [OK]
Two or more interfaces found, checking IP forwarding [OK]
Checking NAT and MASQUERADEing [OK]
Checking for 'ip' command [OK]
Checking for 'iptables' command [OK]
Opportunistic Encryption Support [DISABLED]


If the two netkey / ICMP lines fail, don't worry...it should still work.  Not sure why this happens for some and not others.  I tried changing the ipv4 ICMP settings and got no change in the verify results.  Not quite sure what the problem is here yet??

=========

Last but not least, place the following line into your /etc/rc.local file 
(This allows forwarding of packets so you can access WAN addresses, not just LAN addresses and persistent across reboots.)

echo 1 > /proc/sys/net/ipv4/ip_forward

=========

Running the following command enables it currently, no need to reboot

sudo echo 1 > /proc/sys/net/ipv4/ip_forward

===============================================================

Now for the Iphone Setup

Settings -> General -> Network -> VPN -> Add VPN Configuration

L2TP
Description: WhateverYouWantToCallIt
Server: WANipAddress (could be a DynamicDNS URL)
Account: test
RSA SecurID=OFF
Password: testpass
Secret: TestSecret
Send All Traffic=On

Save it, then turn your VPN on, it should connect and you will see a VPN icon in the upper status bar (left side on 3gs, right side on 4).  Now all your traffic will be protected in WiFi hotspots, 3G, etc.

Hope this helps. Let me know if there are any typos or mistakes.  
Anyone care to test this with an Android phone and post the setting differences if any?

---

### Post by mök on 2011-01-19
Thanks for sharing.

You do not make use of the -source package, therefore you do not need it.

The ipsec.conf file is indentation sensitive. You might want to repost the file with correct indentation.

The virtual_private line makes it impossible to connect if the client has a 192.168.x.y address somewhere in a  nat-ed network. You should only exclude the immediate subnet where your server lives.

The ipsec.conf file will give you a warning that KLIPS cannot be found on each startup. include protostack=netkey to avoid the warning.

You reference an example file /etc/ipsec.d/examples/no_oe.conf that does not exist.

---

### Post by dsuchter on 2011-01-23
I'm having a problem getting this to work for my iPhone 4 and my Ubuntu Maverick netbook endpoint. I'm real close to working, but on my iPhone I get an error:
```
VPN Connection
A connection could not be established to the PPP server. Try reconnecting. If the problem continues, verify your settings and contact your Administrator
```

Any idea what might cause this?

I also noticed an extremely minor error in your post - you transposed the "d" and "p" in "xl2tpd" (<= this is correct, but if you expand the acronym for what you wrote you'd get, 'x Layer 2 Tunneling Daemon Protocol'). That's not a huge problem, of course, but for someone like me who tried to follow *precisely* by using cut-and-paste, it threw me off for a second.

Thanks for the great post so far-

---

### Post by dsuchter on 2011-01-27
bump

---

### Post by ndoggac on 2011-01-27
thanks to mok and dsuchter for their corrections.

Fixes made:
removed source package from installation line per Mok
changed 192.168.0.0 to 192.168.1.0  per Mok
added protostack=netkey to ipsec.conf per Mok
removed no_oe.conf reference (leftover from testing) per Mok
fixed the transposed "d" and "p" in xl2tpd per dsuchter

I can't get the text to indent in the post.  Any help on doing that would be appreciated.

---

### Post by dsuchter on 2011-01-27
> **ndoggac said:**
> thanks to mok and dsuchter for their corrections.

I can't get the text to indent in the post.  Any help on doing that would be appreciated.

Wrap it in CODE tags (the hash-symbol button on the post-editing widget will get you these tags, or you can manually type them in using square brackets).

```

no indent
  two spaces
    four spaces
  two spaces

```

---

### Post by ndoggac on 2011-01-27
Thanks for that dsuchter.  I think maybe the package got updated on me, some of my conf files have additional settings in them, and I can't get it to work right now either.  Will have to tackle it this weekend.  Sorry I can't be more help.

---

### Post by dsuchter on 2011-01-27
I've found plenty of other people posting about trying to get this to work, but this thread is about the only one with Maverick 10.10 + iPhone, specifically, and I think that' s important. This may be a bug in Ubuntu (or something upstream), so I'm really curious if you ever had this working via Maverick <=> iOS, and if so precisely which builds and versions of each (I'm on Maverick 32-bit netbook edition and using iOS 4.2.1 as my client iPhone4 hardware).

Here's the possibly related bug: [https://bugs.launchpad.net/ubuntu/+source/network-manager-pptp/+bug/663184](https://bugs.launchpad.net/ubuntu/+source/network-manager-pptp/+bug/663184)

---

### Post by ndoggac on 2011-01-29
I definitely had this working before as the VPN icon in the upper left of the Iphone screen appeared, and I verified my external IP address was that of my local home LAN while connecting both via 3G and from public WIFI spots.  I'm running IOS 4.0.1 on an Iphone 3GS and Maverick 64-bit Ubuntu on a dedicated "always on" server.  I hadn't updated the server in quite a while, and the other day pulled about 100 updates or so.  After that it stopped working, and I noticed that added text was in some of my configuration files...so I'm not exactly sure what happened.

---

### Post by ndoggac on 2011-01-29
Noticed in my original post....Openswan version is different from what it is now.  May have caused the problem.  Still working on this.

originally
Linux Openswan U2.4.9/K2.6.24-23-generic

now it is
Linux Openswan U2.6.23/K2.6.32-28-server


I also noticed one line in the verify screen is different

then
Checking for RSA private key (/etc/ipsec.secrets) [DISABLED]

now
Checking for RSA private key (/etc/ipsec.secrets) [OK]

---

### Post by dsuchter on 2011-01-30
So you're saying the VPN worked when **ipsec verify** showed that RSA private key is disabled? I wonder how one would configure things to disable RSA private keys... I've looked through various manpages, but all I can find is an "authby" option for ipsecd, which you've already got enabled in your configs below. I also have it disabled (really "authby=secret", which I assume disables RSA key authentication), but I'm getting ```
checking for RSA private key (/etc/ipsec.secrets) [OK]
```

---

### Post by ndoggac on 2011-02-01
Below is my auth.log entry for when I'm trying to connect via my Iphone over 3G.  I've replaced ServerName, iphone address, and Comcast IP for security.  I removed the times, all the logs shown were produced within 3 seconds.  I also shortened down some of the Vendor ID stuff with a ... for security.

Right now on the iPhone I'm getting the following error message.

```

The L2TP-VPN server did not respond.  Try reconnecting.  If the problem continues, verify your settings and contact your Administrator.

```


Excerpt from my auth.log on Ubuntu.  Is there another log file I should be showing?

```

ServerName pluto[13800]: packet from <iphone address>:10322: received Vendor ID payload [RFC 3947] method set to=109
ServerName pluto[13800]: packet from <iphone address>:10322: received Vendor ID payload [draft-ietf-ipsec-nat-t-ike] method set to=110
ServerName pluto[13800]: packet from <iphone address>:10322: ignoring unknown Vendor ID payload [8f8d...1de8]
ServerName pluto[13800]: packet from <iphone address>:10322: ignoring unknown Vendor ID payload [439b...f582]
ServerName pluto[13800]: packet from <iphone address>:10322: ignoring unknown Vendor ID payload [4d1e...7285]
ServerName pluto[13800]: packet from <iphone address>:10322: ignoring unknown Vendor ID payload [80d0...e3ee]
ServerName pluto[13800]: packet from <iphone address>:10322: ignoring unknown Vendor ID payload [9909...fa6b]
ServerName pluto[13800]: packet from <iphone address>:10322: received Vendor ID payload [draft-ietf-ipsec-nat-t-ike-03] meth=108, but already using method 110
ServerName pluto[13800]: packet from <iphone address>:10322: received Vendor ID payload [draft-ietf-ipsec-nat-t-ike-02] meth=107, but already using method 110
ServerName pluto[13800]: packet from <iphone address>:10322: received Vendor ID payload [draft-ietf-ipsec-nat-t-ike-02_n] meth=106, but already using method 110
ServerName pluto[13800]: packet from <iphone address>:10322: received Vendor ID payload [Dead Peer Detection]
ServerName pluto[13800]: "L2TP-PSK-NAT"[5] <iphone address> #5: responding to Main Mode from unknown peer <iphone address>
ServerName pluto[13800]: "L2TP-PSK-NAT"[5] <iphone address> #5: transition from state STATE_MAIN_R0 to state STATE_MAIN_R1
ServerName pluto[13800]: "L2TP-PSK-NAT"[5] <iphone address> #5: STATE_MAIN_R1: sent MR1, expecting MI2
ServerName pluto[13800]: "L2TP-PSK-NAT"[5] <iphone address> #5: NAT-Traversal: Result using draft-ietf-ipsec-nat-t-ike (MacOS X): both are NATed
ServerName pluto[13800]: "L2TP-PSK-NAT"[5] <iphone address> #5: transition from state STATE_MAIN_R1 to state STATE_MAIN_R2
ServerName pluto[13800]: "L2TP-PSK-NAT"[5] <iphone address> #5: STATE_MAIN_R2: sent MR2, expecting MI3
ServerName pluto[13800]: "L2TP-PSK-NAT"[5] <iphone address> #5: ignoring informational payload, type IPSEC_INITIAL_CONTACT msgid=00000000
ServerName pluto[13800]: "L2TP-PSK-NAT"[5] <iphone address> #5: Main mode peer ID is ID_IPV4_ADDR: '10.58.131.131'
ServerName pluto[13800]: "L2TP-PSK-NAT"[5] <iphone address> #5: switched from "L2TP-PSK-NAT" to "L2TP-PSK-NAT"
ServerName pluto[13800]: "L2TP-PSK-NAT"[6] <iphone address> #5: deleting connection "L2TP-PSK-NAT" instance with peer <iphone address> {isakmp=#0/ipsec=#0}
ServerName pluto[13800]: "L2TP-PSK-NAT"[6] <iphone address> #5: transition from state STATE_MAIN_R2 to state STATE_MAIN_R3
ServerName pluto[13800]: "L2TP-PSK-NAT"[6] <iphone address> #5: new NAT mapping for #5, was <iphone address>:10322, now <iphone address>:10351
ServerName pluto[13800]: "L2TP-PSK-NAT"[6] <iphone address> #5: STATE_MAIN_R3: sent MR3, ISAKMP SA established {auth=OAKLEY_PRESHARED_KEY cipher=aes_256 prf=oakley_sha group=modp1024}
ServerName pluto[13800]: "L2TP-PSK-NAT"[6] <iphone address> #5: the peer proposed: <Comcast IP>/32:17/1701 -> 10.58.131.131/32:17/0
ServerName pluto[13800]: "L2TP-PSK-NAT"[6] <iphone address> #6: responding to Quick Mode proposal {msgid:49563687}
ServerName pluto[13800]: "L2TP-PSK-NAT"[6] <iphone address> #6:     us: 192.168.1.22<192.168.1.22>[+S=C]:17/1701---192.168.2.1
ServerName pluto[13800]: "L2TP-PSK-NAT"[6] <iphone address> #6:   them: <iphone address>[10.58.131.131,+S=C]:17/0===10.58.131.131/32
ServerName pluto[13800]: "L2TP-PSK-NAT"[6] <iphone address> #6: transition from state STATE_QUICK_R0 to state STATE_QUICK_R1
ServerName pluto[13800]: "L2TP-PSK-NAT"[6] <iphone address> #6: STATE_QUICK_R1: sent QR1, inbound IPsec SA installed, expecting QI2
ServerName pluto[13800]: "L2TP-PSK-NAT"[6] <iphone address> #6: transition from state STATE_QUICK_R1 to state STATE_QUICK_R2
ServerName pluto[13800]: "L2TP-PSK-NAT"[6] <iphone address> #6: STATE_QUICK_R2: IPsec SA established transport mode {ESP=>0x0c22b033 <0x1368f6f8 xfrm=AES_256-HMAC_SHA1 NATOA=none NATD=<iphone address>:10351 DPD=none}

```


Excerpt from syslog on Ubuntu
```

ServerName xl2tpd[13579]: Connection 16 closed to <iphone address>, port 52522 (Timeout)
ServerName xl2tpd[13579]: control_finish: Peer requested tunnel 1 twice, ignoring second one.
ServerName xl2tpd[13579]: control_finish: Peer requested tunnel 1 twice, ignoring second one.
ServerName xl2tpd[13579]: Maximum retries exceeded for tunnel 22051.  Closing.
ServerName xl2tpd[13579]: Unable to deliver closing message for tunnel 44470. Destroying anyway.
ServerName xl2tpd[13579]: control_finish: Peer requested tunnel 1 twice, ignoring second one.
ServerName xl2tpd[13579]: Connection 1 closed to <iphone address>, port 50431 (Timeout)
ServerName xl2tpd[13579]: control_finish: Peer requested tunnel 1 twice, ignoring second one.
ServerName xl2tpd[13579]: Unable to deliver closing message for tunnel 22051. Destroying anyway.
ServerName xl2tpd[13579]: control_finish: Peer requested tunnel 1 twice, ignoring second one.
ServerName xl2tpd[13579]: Maximum retries exceeded for tunnel 45560.  Closing.

```

Seems like maybe xl2tpd is the culprit, although I'm not sure why?

---

### Post by dsuchter on 2011-02-01
I'm at work and my system is unreachable at the moment, but your logs look exactly like mine. The interesting thing, in my noob opinion, is that the LT2P tunnel looks like it opens properly and then nothing else happens.

---

### Post by ndoggac on 2011-02-01
Ok, so from reading around there appears to be a bug with openswan 2.6.x that breaks xl2tp.  The only fix I've seen is to roll back to 2.4.x in order to fix the problem, which worked for me originally.  

Anyone know how to roll back a single package and its dependencies?

---

### Post by dsuchter on 2011-02-01
> **ndoggac said:**
> Ok, so from reading around there appears to be a bug with openswan 2.6.x that breaks xl2tp.  The only fix I've seen is to roll back to 2.4.x in order to fix the problem, which worked for me originally.  

I've been discussing this with a few engineers who have done OpenSwan deployments before and I mentioned reading the same thing, only now I can't find any of the sites that said there are problems with 2.6.x + xl2tp. Do you have any links handy? Knowing why it breaks and seeing other people's information might help lead us to a solution here.

---

### Post by dsuchter on 2011-02-02
I just tried to figure out how to downgrade to the older 2.4.9 package using apt-get and ended up deciding to install the latest 2.6.32 from [http://www.openswan.org/code/](http://www.openswan.org/code/) from source. I had to look in the README and install a few compilation tools using apt-get (not a huge surprise). Overall it wasn't too bad getting it to compile and install.

Now I'm on 2.6.32 and I'm getting totally different errors (yey?!?). I'm getting a ton of this in syslog:

```
Feb  1 22:03:07 server pppd[27393]: rcvd [IPCP ConfReq id=0xf7 <addrs 0.0.0.0 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
Feb  1 22:03:07 server pppd[27393]: sent [IPCP ConfRej id=0xf7 <addrs 0.0.0.0 0.0.0.0>]
Feb  1 22:03:07 server pppd[27393]: rcvd [IPCP ConfReq id=0xf8 <addrs 0.0.0.0 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
Feb  1 22:03:07 server pppd[27393]: sent [IPCP ConfRej id=0xf8 <addrs 0.0.0.0 0.0.0.0>]
Feb  1 22:03:07 server pppd[27393]: rcvd [IPCP ConfReq id=0xf9 <addrs 0.0.0.0 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
Feb  1 22:03:07 server pppd[27393]: sent [IPCP ConfRej id=0xf9 <addrs 0.0.0.0 0.0.0.0>]
Feb  1 22:03:08 server pppd[27393]: rcvd [IPCP ConfReq id=0xfa <addrs 0.0.0.0 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
Feb  1 22:03:08 server pppd[27393]: sent [IPCP ConfRej id=0xfa <addrs 0.0.0.0 0.0.0.0>]
Feb  1 22:03:08 server pppd[27393]: rcvd [IPCP ConfReq id=0xfb <addrs 0.0.0.0 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
Feb  1 22:03:08 server pppd[27393]: sent [IPCP ConfRej id=0xfb <addrs 0.0.0.0 0.0.0.0>]
Feb  1 22:03:08 server pppd[27393]: rcvd [IPCP ConfReq id=0xfc <addrs 0.0.0.0 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]

```

and the connection ends with:
```


Feb  1 22:03:09 server pppd[27393]: rcvd [IPCP ConfReq id=0xff <addrs 0.0.0.0 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
Feb  1 22:03:09 server pppd[27393]: sent [IPCP ConfRej id=0xff <addrs 0.0.0.0 0.0.0.0>]
Feb  1 22:03:09 server pppd[27393]: rcvd [LCP TermReq id=0x3 "No network protocols running"]
Feb  1 22:03:09 server pppd[27393]: LCP terminated by peer (No network protocols running)
Feb  1 22:03:09 server pppd[27393]: sent [LCP TermAck id=0x3]
Feb  1 22:03:09 server xl2tpd[27369]: result_code_avp: result code out of range (768 0 14).  Ignoring.
Feb  1 22:03:09 server xl2tpd[27369]: control_finish: Peer tried to disconnect without specifying result code.
Feb  1 22:03:09 server xl2tpd[27369]: network_thread: bad packet
Feb  1 22:03:09 server xl2tpd[27369]: result_code_avp: result code out of range (256 0 14).  Ignoring.
Feb  1 22:03:09 server xl2tpd[27369]: control_finish: Peer tried to disconnect without specifying result code.
Feb  1 22:03:09 server xl2tpd[27369]: network_thread: bad packet
Feb  1 22:03:12 server pppd[27393]: Connection terminated.
Feb  1 22:03:12 server pppd[27393]: Connect time 0.9 minutes.
Feb  1 22:03:12 server pppd[27393]: Sent 3767 bytes, received 6820 bytes.
Feb  1 22:03:12 server avahi-daemon[848]: Withdrawing workstation service for ppp0.
Feb  1 22:03:12 server NetworkManager[873]:    SCPlugin-Ifupdown: devices removed (path: /sys/devices/virtual/net/ppp0, iface: ppp0)
Feb  1 22:03:12 server pppd[27393]: Modem hangup
Feb  1 22:03:12 server pppd[27393]: Exit.
Feb  1 22:03:12 server xl2tpd[27369]: child_handler : pppd exited for call 1199 with code 16
Feb  1 22:03:12 server xl2tpd[27369]: call_close: Call 49031 to [redacted IP] disconnected
Feb  1 22:03:17 server xl2tpd[27369]: Maximum retries exceeded for tunnel 47965.  Closing.
Feb  1 22:03:18 server xl2tpd[27369]: build_fdset: closing down tunnel 47965
Feb  1 22:03:18 server xl2tpd[27369]: Terminating pppd: sending TERM signal to pid 27393
Feb  1 22:03:18 server xl2tpd[27369]: pppd 27393 successfully terminated
Feb  1 22:03:18 server xl2tpd[27369]: Connection 5 closed to [redacted IP], port 56410 (Timeout)
Feb  1 22:03:23 server xl2tpd[27369]: Unable to deliver closing message for tunnel 47965. Destroying anyway.

```

My /var/log/auth.log looks like it has the same errors as before:
```

Feb  1 22:08:48 server pluto[27187]: "L2TP-PSK-NAT"[2] [redacted IP] #4: STATE_QUICK_R2: IPsec SA established transport mode {ESP=>0x06aaca70 <0x789a2459 xfrm=AES_256-HMAC_SHA1 NATOA=none NATD=[redacted IP]:54505 DPD=none}

```

Finally, I think my ipsec verify looks a bit different than before (obviously I restarted everything I could think of):
```

Checking your system to see if IPsec got installed and started correctly:
Version check and ipsec on-path                             	[OK]
Linux Openswan U2.6.26/K2.6.35-24-generic (netkey)
Checking for IPsec support in kernel                        	[OK]
 SAref kernel support                                       	[N/A]
 NETKEY:  Testing for disabled ICMP send_redirects          	[OK]
NETKEY detected, testing for disabled ICMP accept_redirects 	[OK]
Checking that pluto is running                              	[OK]
 Pluto listening for IKE on udp 500                         	[OK]
 Pluto listening for NAT-T on udp 4500                      	[OK]
Two or more interfaces found, checking IP forwarding        	[OK]
Checking NAT and MASQUERADEing                              	[N/A]
Checking for 'ip' command                                   	[OK]
Checking /bin/sh is not /bin/dash                           	[WARNING]
Checking for 'iptables' command                             	[OK]
Opportunistic Encryption Support                            	[DISABLED]

```

---

### Post by raininglemons on 2011-02-02
Bit of googling lead me here. Getting the exact same error as dsuchter.

Tried install from both source and apt-get, seems a problem between ipsec and ppp, using conf that def works (using it on a 9.10 server).

dsuchter are you running 10.10?

---

### Post by dsuchter on 2011-02-02
> **raininglemons said:**
> Bit of googling lead me here. Getting the exact same error as dsuchter.

Tried install from both source and apt-get, seems a problem between ipsec and ppp, using conf that def works (using it on a 9.10 server).

dsuchter are you running 10.10?
Yup, fresh install of Ubuntu 10.10 on an Acer Aspire One AOA110 netbook (Maverick Netbook Edition) specifically so I could make a VPN endpoint in my network:
```

root@servername:~# uname -a; cat /proc/version /etc/lsb-release 
Linux servername 2.6.35-24-generic #42-Ubuntu SMP Thu Dec 2 01:41:57 UTC 2010 i686 GNU/Linux
Linux version 2.6.35-24-generic (buildd@vernadsky) (gcc version 4.4.5 (Ubuntu/Linaro 4.4.4-14ubuntu5) ) #42-Ubuntu SMP Thu Dec 2 01:41:57 UTC 2010
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.10
DISTRIB_CODENAME=maverick
DISTRIB_DESCRIPTION="Ubuntu 10.10"

```

---

### Post by Enigma^ on 2011-02-02
I have the same problem I can't connect from windows7 or my iPhone to my vpn server.
I'm running ubuntu 10.10 server edition, xl2tpd-1.2.6 and Openswan IPsec U2.6.26/K2.6.35-25-generic-pae

Here's my syslog: 
```
Feb  2 21:28:29 ubuntu xl2tpd[4133]: control_finish: Peer requested tunnel 7 twice, ignoring second one.
Feb  2 21:28:29 ubuntu xl2tpd[4133]: Connection established to 192.168.1.33, 1701.  Local: 28153, Remote: 7 (ref=0/0).  LNS session is 'default'
Feb  2 21:28:29 ubuntu xl2tpd[4133]: result_code_avp: result code not appropriate for Incoming-Call-Request.  Ignoring.
Feb  2 21:28:29 ubuntu xl2tpd[4133]: start_pppd: I'm running:
Feb  2 21:28:29 ubuntu xl2tpd[4133]: "/usr/sbin/pppd"
Feb  2 21:28:29 ubuntu xl2tpd[4133]: "passive"
Feb  2 21:28:29 ubuntu xl2tpd[4133]: "nodetach"
Feb  2 21:28:29 ubuntu xl2tpd[4133]: "172.21.118.1:0.0.0.0"
Feb  2 21:28:29 ubuntu xl2tpd[4133]: "refuse-pap"
Feb  2 21:28:29 ubuntu xl2tpd[4133]: "refuse-chap"
Feb  2 21:28:29 ubuntu xl2tpd[4133]: "auth"
Feb  2 21:28:29 ubuntu xl2tpd[4133]: "debug"
Feb  2 21:28:29 ubuntu xl2tpd[4133]: "file"
Feb  2 21:28:29 ubuntu xl2tpd[4133]: "/etc/ppp/options.xl2tpd"
Feb  2 21:28:29 ubuntu xl2tpd[4133]: "/dev/pts/2"
Feb  2 21:28:29 ubuntu xl2tpd[4133]: Call established with 192.168.1.33, Local: 41942, Remote: 1, Serial: 0
Feb  2 21:28:29 ubuntu pppd[4186]: pppd 2.4.5 started by root, uid 0
Feb  2 21:28:29 ubuntu pppd[4186]: using channel 1
Feb  2 21:28:29 ubuntu pppd[4186]: Using interface ppp0
Feb  2 21:28:29 ubuntu pppd[4186]: Connect: ppp0 <--> /dev/pts/2
Feb  2 21:28:29 ubuntu pppd[4186]: sent [LCP ConfReq id=0x1 <mru 1410> <asyncmap 0x0> <auth chap MS-v2> <magic 0x9c7658c5> <pcomp> <accomp>]
Feb  2 21:28:29 ubuntu pppd[4186]: rcvd [LCP ConfAck id=0x1 <mru 1410> <asyncmap 0x0> <auth chap MS-v2> <magic 0x9c7658c5> <pcomp> <accomp>]
Feb  2 21:28:31 ubuntu pppd[4186]: rcvd [LCP ConfReq id=0x1 <mru 1400> <magic 0x41131244> <pcomp> <accomp> <callback CBCP>]
Feb  2 21:28:31 ubuntu pppd[4186]: sent [LCP ConfRej id=0x1 <callback CBCP>]
Feb  2 21:28:31 ubuntu pppd[4186]: rcvd [LCP ConfReq id=0x2 <mru 1400> <magic 0x41131244> <pcomp> <accomp>]
Feb  2 21:28:31 ubuntu pppd[4186]: sent [LCP ConfAck id=0x2 <mru 1400> <magic 0x41131244> <pcomp> <accomp>]
Feb  2 21:28:31 ubuntu pppd[4186]: sent [LCP EchoReq id=0x0 magic=0x9c7658c5]
Feb  2 21:28:31 ubuntu pppd[4186]: sent [CHAP Challenge id=0xe6 <f7e73e9e1439687ba596ddd349636b4f>, name = "l2tpd"]
Feb  2 21:28:31 ubuntu pppd[4186]: rcvd [LCP Ident id=0x3 magic=0x41131244 "MSRASV5.20"]
Feb  2 21:28:31 ubuntu pppd[4186]: rcvd [LCP Ident id=0x4 magic=0x41131244 "MSRAS-0-ENIGMA-PC"]
Feb  2 21:28:31 ubuntu pppd[4186]: rcvd [LCP Ident id=0x5 magic=0x41131244 "\002\37777777632`!\37777777753LbH\37777777617\37777777653p/\37777777740\37777777656\37777777752\37777777752"]
Feb  2 21:28:31 ubuntu pppd[4186]: rcvd [LCP EchoRep id=0x0 magic=0x41131244]
Feb  2 21:28:31 ubuntu pppd[4186]: rcvd [CHAP Response id=0xe6 <e1bfb23120e8f7cc7b8de48786c9553f0000000000000000dd8eb9435cbfeb303e67b1a6694df5cd29e143b38492438700>, name = "test"]
Feb  2 21:28:31 ubuntu pppd[4186]: sent [CHAP Success id=0xe6 "S=29FC71A95497195E4EF55FB62E8276A3AF8F5488 M=Access granted"]
Feb  2 21:28:31 ubuntu kernel: [16161.945876] PPP BSD Compression module registered
Feb  2 21:28:31 ubuntu pppd[4186]: sent [CCP ConfReq id=0x1 <deflate 15> <deflate(old#) 15> <bsd v1 15>]
Feb  2 21:28:31 ubuntu pppd[4186]: sent [IPCP ConfReq id=0x1 <compress VJ 0f 01> <addr 172.21.118.1>]
Feb  2 21:28:31 ubuntu pppd[4186]: rcvd [IPV6CP ConfReq id=0x6 <addr fe80::483c:272c:c66a:ebe1>]
Feb  2 21:28:31 ubuntu pppd[4186]: Unsupported protocol 'IPv6 Control Protovol' (0x8057) received
Feb  2 21:28:31 ubuntu pppd[4186]: sent [LCP ProtRej id=0x2 80 57 01 06 00 0e 01 0a 48 3c 27 2c c6 6a eb e1]
Feb  2 21:28:31 ubuntu pppd[4186]: rcvd [CCP ConfReq id=0x7 <mppe +H -M -S -L -D -C>]
Feb  2 21:28:31 ubuntu pppd[4186]: sent [CCP ConfRej id=0x7 <mppe +H -M -S -L -D -C>]
Feb  2 21:28:31 ubuntu pppd[4186]: rcvd [IPCP ConfReq id=0x8 <addr 0.0.0.0> <ms-dns1 0.0.0.0> <ms-wins 0.0.0.0> <ms-dns2 0.0.0.0> <ms-wins 0.0.0.0>]
Feb  2 21:28:31 ubuntu pppd[4186]: sent [IPCP ConfRej id=0x8 <addr 0.0.0.0> <ms-wins 0.0.0.0> <ms-wins 0.0.0.0>]
Feb  2 21:28:31 ubuntu kernel: [16161.950006] PPP Deflate Compression module registered
Feb  2 21:28:31 ubuntu pppd[4186]: rcvd [CCP ConfRej id=0x1 <deflate 15> <deflate(old#) 15> <bsd v1 15>]
Feb  2 21:28:31 ubuntu pppd[4186]: sent [CCP ConfReq id=0x2]
Feb  2 21:28:31 ubuntu pppd[4186]: rcvd [IPCP ConfRej id=0x1 <compress VJ 0f 01>]
Feb  2 21:28:31 ubuntu pppd[4186]: sent [IPCP ConfReq id=0x2 <addr 172.21.118.1>]
Feb  2 21:28:31 ubuntu pppd[4186]: rcvd [CCP TermReq id=0x9"A\023\022D\000<\37777777715t\000\000\002\37777777734"]
Feb  2 21:28:31 ubuntu pppd[4186]: sent [CCP TermAck id=0x9]
Feb  2 21:28:31 ubuntu pppd[4186]: rcvd [IPCP ConfReq id=0xa <addr 0.0.0.0>]
Feb  2 21:28:31 ubuntu pppd[4186]: sent [IPCP ConfRej id=0xa <addr 0.0.0.0>]
Feb  2 21:28:31 ubuntu pppd[4186]: rcvd [IPCP ConfAck id=0x2 <addr 172.21.118.1>]
Feb  2 21:28:31 ubuntu pppd[4186]: rcvd [IPCP TermReq id=0xb "A\023\022D\000<\37777777715t\000\000\002\37777777742"]
Feb  2 21:28:31 ubuntu pppd[4186]: sent [IPCP TermAck id=0xb]
Feb  2 21:28:31 ubuntu pppd[4186]: rcvd [LCP TermReq id=0xc "A\023\022D\000<\37777777715t\000\000\000\000"]
Feb  2 21:28:31 ubuntu pppd[4186]: LCP terminated by peer (A^S^RD^@<M-Mt^@^@^@^@)
Feb  2 21:28:31 ubuntu pppd[4186]: sent [LCP TermAck id=0xc]
Feb  2 21:28:31 ubuntu xl2tpd[4133]: control_finish: Connection closed to 192.168.1.33, serial 0 ()
Feb  2 21:28:31 ubuntu xl2tpd[4133]: Terminating pppd: sending TERM signal to pid 4186
Feb  2 21:28:31 ubuntu pppd[4186]: Terminating on signal 15
Feb  2 21:28:31 ubuntu pppd[4186]: Modem hangup
Feb  2 21:28:31 ubuntu pppd[4186]: Connection terminated.
Feb  2 21:28:31 ubuntu pppd[4186]: Connect time 0.1 minutes.
Feb  2 21:28:31 ubuntu pppd[4186]: Sent 95 bytes, received 135 bytes.
Feb  2 21:28:31 ubuntu pppd[4186]: Exit.
Feb  2 21:28:31 ubuntu xl2tpd[4133]: pppd 4186 successfully terminated
Feb  2 21:28:31 ubuntu xl2tpd[4133]: control_finish: Connection closed to 192.1
```

---

### Post by dsuchter on 2011-02-03
It occurs to me to mention I'm on a Actiontec MI424WR-GEN2 hardware version "F" router supplied by Verizon for my FiOS connection. It is running firmware 20.10.7.5. Supposedly the default is to support VPN passthrough, but I don't know if inbound VPN connections would require anything above and beyond the UDP500/4500 forwards I've setup.

---

### Post by dsuchter on 2011-02-03
Thanks to some help from the Openswan developers I got this working now (it still has other problems, but this one is clearly solved).

There were a few settings that needed correcting compared to what's represented in this thread. The most important one, and the only one I'm sure enough to post about yet, is the IP address specification in /etc/ppp/chap-secrets.

Note how the original config has a "*" (star) in the fourth column for "IP Address." I was originally under the impression this column represented an ACL to prevent certain remote networks from connecting to your endpoint, however, I now understand it to be the IP address the PPP daemon is going to serve to the connecting client. I kept things simple and put a single static IP that's available on my local NAT'ed LAN in there for both lines (my file only has two lines). After restarting things worked.

*Note of course I made a few other changes, like I disabled SAref, but I'm not sure if those mattered.

I now have a different problem that after one connection from my iPhone the IPSEC daemon needs a restart before I can connect again, but that's a topic I've seen elsewhere on the Internet so I'll research it separately from this thread.

---

### Post by ndoggac on 2011-02-24
I'm still having problems since the update, any further help dsuchter?

Maybe a post of your config files matching those files listed in my first post and any additional?

Did you ever get the daemon reboot issue solved?

Thanks in advance.

---

### Post by Myx0.x3 on 2011-03-29
i get:

```
Checking your system to see if IPsec got installed and started correctly:
Version check and ipsec on-path                                 [OK]
Linux Openswan U2.6.26/K2.6.35-28-generic-pae (netkey)
Checking for IPsec support in kernel                            [OK]
NETKEY detected, testing for disabled ICMP send_redirects       [FAILED]

  Please disable /proc/sys/net/ipv4/conf/*/send_redirects
  or NETKEY will cause the sending of bogus ICMP redirects!

NETKEY detected, testing for disabled ICMP accept_redirects     [FAILED]

  Please disable /proc/sys/net/ipv4/conf/*/accept_redirects
  or NETKEY will accept bogus ICMP redirects!

Checking for RSA private key (/etc/ipsec.secrets)               [OK]
Checking that pluto is running                                  [OK]
Pluto listening for IKE on udp 500                              [OK]
Pluto listening for NAT-T on udp 4500                           [OK]
Two or more interfaces found, checking IP forwarding            [OK]
Checking NAT and MASQUERADEing                                  [N/A]
Checking for 'ip' command                                       [OK]
Checking for 'iptables' command                                 [OK]
Opportunistic Encryption Support                                [DISABLED]

```


And it does looks like it does not work yet :/

---

### Post by dsuchter on 2011-03-29
So for the record no, I never got my daemon reboot issue solved. Unfortunately I also don't currently have that host configured the same way as before (a fresh no OS is on it), so I can't easily reproduce my config files. If I ever figure out how I got things going again I'll post back, but at the rate things are going my guess is Ubuntu and/or some of the other packages relevant here will have updated to the point where my help is obsolete. Sorry about that!

---

### Post by ftt on 2011-04-24
So I think I've got this working now for everyone trying to do this, you need to do what dsuchter said and explicitly specify an ip address for the user connecting in /etc/ppp/chaps-secrets, I only have 1 line in my file:

```
test l2tpd testpass 192.168.1.250
```This will allow you to connect (and gives the iPhone the .250 ip address). Now you're left with the problem that you can only connect once. In syslog it looked like the iPhone isn't disconnecting correctly, potentially tying up that .250 ip address so that you can't reconnect. Enabling dead peer detection allows you to reconnect. I added the following to /etc/ipsec.conf under the L2TP-PSK-noNAT connection:
```
dpddelay=30  
dpdtimeout=120  
dpdaction=clear
```I just tested and could reconnect successfully, I'll use it more tomorrow and if there are any problems I'll post them here.

---

### Post by wlraider70 on 2011-05-11
following the guide got me to

```

server@hyrule:/etc$ sudo ipsec verify
Checking your system to see if IPsec got installed and started correctly:
Version check and ipsec on-path                                 [OK]
Linux Openswan U2.6.23/K2.6.32-28-server (netkey)
Checking for IPsec support in kernel                            [OK]
NETKEY detected, testing for disabled ICMP send_redirects       [OK]
NETKEY detected, testing for disabled ICMP accept_redirects     [OK]
Checking for RSA private key (/etc/ipsec.secrets)               [OK]
Checking that pluto is running                                  [OK]
Pluto listening for IKE on udp 500                              [OK]
Pluto listening for NAT-T on udp 4500                           [OK]
Checking for 'ip' command                                       [OK]
Checking for 'iptables' command                                 [OK]
Opportunistic Encryption Support                                [DISABLED]

```

my phone says server did not respond...

The only place i have a question is the * vs setip earlier in the thread. I have set an ip.
However, im not sure if that matter.

not sure what kind of errors I should look for in the log.


edit--
my MacBook got the error "The server did not respond..."

---

### Post by ndoggac on 2011-06-07
Ok, got this working again.  Here are the details that need to be worked out.

In the /etc/xl2tpd/xl2tpd.conf file, you define an "ip range".  In this case 231 to 239.  The "local ip" value in the same file MUST be outside this range.  In this case, 230.

A value in the "ip range" must be used in the /etc/ppp/chap-secrets file.  In this case, I used 233.  You can add additional users until you fill up the range you specified.  You can always expand the range to accommodate more users.  Originally I had a * in this file instead of an IP address, I believe this was deprecated in the latest version.

I have edited the first post to reflect these changes.

I'm also running this on upgraded server edition to Natty 11.04.

Hopefully this clears up the last of the problems.  Post back to let me know if I missed anything.

I was also wondering how to check that this is truly encrypting the data as we believe.  I would like some sort of external double check that the settings ensure proper encryption.  Anyone have any ideas?  Anyone have any experience with FireSheep they could try to put these settings under the gun?

Also, thanks again to all those users that helped me get this far.  You know who you are ;-)

---

### Post by this on 2011-06-11
I'm still having the server didn't respond problem on both my iPhone and MacBook after confirming my config files are the same as those in the original post.

```
$ uname -a; cat /proc/version /etc/lsb-release 
Linux grabber 2.6.38-8-generic #42-Ubuntu SMP Mon Apr 11 03:31:50 UTC 2011 i686 i686 i386 GNU/Linux
Linux version 2.6.38-8-generic (buildd@vernadsky) (gcc version 4.5.2 (Ubuntu/Linaro 4.5.2-8ubuntu3) ) #42-Ubuntu SMP Mon Apr 11 03:31:50 UTC 2011
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.04
DISTRIB_CODENAME=natty
DISTRIB_DESCRIPTION="Ubuntu 11.04"
```

```
$ dpkg -l openswan ipsec-tools ppp
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                      Version                   Description
+++-=========================-=========================-==================================================================
ii  ipsec-tools               1:0.7.3-12ubuntu1         IPsec tools for Linux
ii  openswan                  1:2.6.28+dfsg-5           Internet Key Exchange daemon
ii  ppp                       2.4.5-5ubuntu1            Point-to-Point Protocol (PPP) - daemon
```

Can anyone suggest anything else which may help me get this working again?

---

### Post by ndoggac on 2011-06-16
```

| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                                          Version                                       Description
+++-=============================================-=============================================-==========================================================================================================
ii  openswan                                      1:2.6.28+dfsg-5                               Internet Key Exchange daemon
ii  ppp                                           2.4.5-5ubuntu1                                Point-to-Point Protocol (PPP) - daemon
ii  xl2tpd                                        1.2.7+dfsg-1                                  a layer 2 tunneling protocol implementation


```

```

Linux MediaServer 2.6.38-8-server #42-Ubuntu SMP Mon Apr 11 03:49:04 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux
Linux version 2.6.38-8-server (buildd@allspice) (gcc version 4.5.2 (Ubuntu/Linaro 4.5.2-8ubuntu3) ) #42-Ubuntu SMP Mon Apr 11 03:49:04 UTC 2011
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.04
DISTRIB_CODENAME=natty
DISTRIB_DESCRIPTION="Ubuntu 11.04"


```

Not sure what's wrong with your setup?  You have the same setup as I do, although you didn't include xl2tp in your listing?  I also don't have ipsec-tools installed.  

Are you sure you have ports successfully forwarded in your router?  dynamic dns works or ip address is publicly accessible?

All I can recommend is double checking all the config files, but I'm sure that's not the help you're looking for.

Did this not work for anyone else running Natty?

---

### Post by wingcomm on 2011-06-20
Looks like some of the issues listed here are fixed in the latest releases of Openswan and xl2tpd.

[http://lists.openswan.org/pipermail/users/2011-April/020411.html](http://lists.openswan.org/pipermail/users/2011-April/020411.html)

---

### Post by michel176 on 2011-07-13
followed your guide exactly and I keep getting this error:

```

Jul 13 16:51:24 ubuntu-server pluto[11098]: ERROR: asynchronous network error report on br0 (sport=4500) for message to 192.168.1.1 port 4500, complainant 192.168.1.1: Connection refused [errno 111, origin ICMP type 3 code 3 (not authenticated)]

```

the ports are set-up in the router and ipsec verify does not give errors

---

### Post by atca on 2011-08-07
This may also be of help [Openswan, xl2tp and PPP in detail]("http://confoundedtech.blogspot.com/2011/08/android-nexus-one-ipsec-psk-vpn-with.html")

---

### Post by osborni on 2011-08-17
Hello - got this setup and working properly... (HUGE THANKS!!!!) but.....

ipsec isn't starting on a reboot.

Verified by rebooting, then running:

> sudo ipsec verify

and finding an incomplete log as well as failing to connect a client.

Then running:

> sudo /etc/init.d/ipsec restart

and getting a complete ipsec verify log and being able to connect with a client.

Any suggestions as to what to do to get ipsec to start on reboot?

---

### Post by atca on 2011-09-03
> **osborni said:**
> Hello - got this setup and working properly... (HUGE THANKS!!!!) but.....

ipsec isn't starting on a reboot.

Verified by rebooting, then running:



and finding an incomplete log as well as failing to connect a client.

Then running:



and getting a complete ipsec verify log and being able to connect with a client.

Any suggestions as to what to do to get ipsec to start on reboot?

See section 12 of this guide...
[http://confoundedtech.blogspot.com/2011/08/android-nexus-one-ipsec-psk-vpn-with.html]("http://confoundedtech.blogspot.com/2011/08/android-nexus-one-ipsec-psk-vpn-with.html")

sudo vi /etc/rc.local

Add: 

/etc/init.d/ipsec start

---

### Post by osborni on 2011-09-03
Yes, thanks, basically what I ended up doing.  Of course, found it a day or two after my post. :)

Next issue is that it doesn't seam to always pick up the connection.  Seams to work better after a fresh reboot, but not too sure about that.  It's behind a dd-wrt router and it will work about 50/50....

---

### Post by atca on 2011-09-04
> **osborni said:**
> Yes, thanks, basically what I ended up doing.  Of course, found it a day or two after my post. :)

Next issue is that it doesn't seam to always pick up the connection.  Seams to work better after a fresh reboot, but not too sure about that.  It's behind a dd-wrt router and it will work about 50/50....

that may be DPD dead peer detection with the iOS.

---

### Post by osborni on 2011-09-04
Hmmm.  I have a DD-wrt router up as well.  Works, but not as robust or as fast on browsing the web as the ubuntu box ( when it works )....  played with MTU on the router, but that didn't make it 100%, just 98% working on web pages.

this was the code that the DD-WRT wiki asks to put into the router:
> #!/bin/sh
echo "nopcomp" >> /tmp/pptpd/options.pptpd
echo "noaccomp" >> /tmp/pptpd/options.pptpd
kill `ps | grep pptp | cut -d ' ' -f 1`
pptpd -c /tmp/pptpd/pptpd.conf -o /tmp/pptpd/options.pptpd

I suspect that it's DPD as well, but I'm not knowledgeable enough to know what to do with it in linux.

Ideas?  Or in there another workaround for iOS clients?

Change the timeouts in the l2tp-psk.conf file?

---

### Post by atca on 2011-09-04
> **osborni said:**
> Hmmm.  I have a DD-wrt router up as well.  Works, but not as robust or as fast on browsing the web as the ubuntu box ( when it works )....  played with MTU on the router, but that didn't make it 100%, just 98% working on web pages.

this was the code that the DD-WRT wiki asks to put into the router:


I suspect that it's DPD as well, but I'm not knowledgeable enough to know what to do with it in linux.

Ideas?  Or in there another workaround for iOS clients?

Change the timeouts in the l2tp-psk.conf file?

See here for my DPD settings:

[http://confoundedtech.blogspot.com/2011/09/configure-iphone-ios-to-use-ipsec-vpn.html](http://confoundedtech.blogspot.com/2011/09/configure-iphone-ios-to-use-ipsec-vpn.html)

DD-WRT I use too, and should that just be forwarding the packets. The browsing will also be constrained by your VPN's upload speed which is bound to be slower than the download.

EDIT: Misread not sure why the DDWRT box is slower than the Ubuntu VPN - maybe the difference in the VPN suites is the cause. I only use DD-WRT for router to router IPSec.

---

### Post by osborni on 2011-09-04
Ok, i'll play with the dpd settings.  They where already in there.

What units are they in?  Seconds?  Minutes?

---

### Post by atca on 2011-09-06
5 seconds I believe

---

### Post by osborni on 2011-09-06
Thanks,

I used your linked recommended DPD settings:
> dpddelay=40
dpdtimeout=130
dpdaction=clear

and it's more robust now.

...
I think that the dd-wrt router on pptp has a much slower processor than the ubuntu box (not really sure, perhaps just less robust code given the limited memory requirements on the DD-wrt router).  Even though I played with the MTU settings, there seams to be more latency and some in game commands and web pages don't load as well as when I connect to the Ubuntu machine via this thread's VPN.  The ubuntu machine's performance on VPN is essentially transparent to how my wifi works when I'm at home on my own network.

---

### Post by abiusx on 2012-01-10
Hi,
I intend to setup VPN server for proxy purposes, not for the usual stuff.

I did all the configuration, but set my IP range to 192.168.0.100-200 

On 10.04 Server LTS 64, IPSec connects successfully but xl2tpd doesn't seem to take over.
What can be causing the problem?
Kind Regards

---

### Post by Jhongy on 2012-01-29
The instructions worked fine for me on a natty Linode Ubuntu server. I made some slight changes to the steps in order to route through to the Internet properly:

[http://www.jfwhome.com/2012/01/29/ipsecl2tp-vpn-on-linode-ubuntu-server-for-iphoneandroid/](http://www.jfwhome.com/2012/01/29/ipsecl2tp-vpn-on-linode-ubuntu-server-for-iphoneandroid/)

---

### Post by logman on 2012-02-20
Hi,

This don't seem to work on me when  i try connect on internet to my lan pc, i did open ports on my router.

Router: DIR-855
Some lan info:
router 192.168.0.1
ubuntu-serv: 192.168.0.2

Some error logs if that helps.

```
Feb 20 22:51:13 purkki pluto[1933]: packet from 188.238.63.190:500: received Vendor ID payload [RFC 3947] method set to=109
Feb 20 22:51:13 purkki pluto[1933]: packet from 188.238.63.190:500: received Vendor ID payload [draft-ietf-ipsec-nat-t-ike-02] meth=107, but already using method 109
Feb 20 22:51:13 purkki pluto[1933]: packet from 188.238.63.190:500: received Vendor ID payload [draft-ietf-ipsec-nat-t-ike-02_n] meth=106, but already using method 109
Feb 20 22:51:13 purkki pluto[1933]: packet from 188.238.63.190:500: received Vendor ID payload [draft-ietf-ipsec-nat-t-ike-00]
Feb 20 22:51:13 purkki pluto[1933]: packet from 188.238.63.190:500: ignoring Vendor ID payload [FRAGMENTATION 80000000]
Feb 20 22:51:13 purkki pluto[1933]: packet from 188.238.63.190:500: received Vendor ID payload [Dead Peer Detection]
Feb 20 22:51:13 purkki pluto[1933]: "L2TP-PSK-NAT"[2] 188.238.63.190 #3: responding to Main Mode from unknown peer 188.238.63.190
Feb 20 22:51:13 purkki pluto[1933]: "L2TP-PSK-NAT"[2] 188.238.63.190 #3: transition from state STATE_MAIN_R0 to state STATE_MAIN_R1
Feb 20 22:51:13 purkki pluto[1933]: "L2TP-PSK-NAT"[2] 188.238.63.190 #3: STATE_MAIN_R1: sent MR1, expecting MI2
Feb 20 22:51:13 purkki pluto[1933]: "L2TP-PSK-NAT"[2] 188.238.63.190 #3: NAT-Traversal: Result using RFC 3947 (NAT-Traversal): both are NATed
Feb 20 22:51:13 purkki pluto[1933]: "L2TP-PSK-NAT"[2] 188.238.63.190 #3: transition from state STATE_MAIN_R1 to state STATE_MAIN_R2
Feb 20 22:51:13 purkki pluto[1933]: "L2TP-PSK-NAT"[2] 188.238.63.190 #3: STATE_MAIN_R2: sent MR2, expecting MI3
Feb 20 22:51:13 purkki pluto[1933]: "L2TP-PSK-NAT"[2] 188.238.63.190 #3: Main mode peer ID is ID_IPV4_ADDR: '10.45.63.190'
Feb 20 22:51:13 purkki pluto[1933]: "L2TP-PSK-NAT"[2] 188.238.63.190 #3: switched from "L2TP-PSK-NAT" to "L2TP-PSK-NAT"
Feb 20 22:51:13 purkki pluto[1933]: "L2TP-PSK-NAT"[3] 188.238.63.190 #3: deleting connection "L2TP-PSK-NAT" instance with peer 188.238.63.190 {isakmp=#0/ipsec=#0}
Feb 20 22:51:13 purkki pluto[1933]: "L2TP-PSK-NAT"[3] 188.238.63.190 #3: transition from state STATE_MAIN_R2 to state STATE_MAIN_R3
Feb 20 22:51:13 purkki pluto[1933]: "L2TP-PSK-NAT"[3] 188.238.63.190 #3: new NAT mapping for #3, was 188.238.63.190:500, now 188.238.63.190:4500
Feb 20 22:51:13 purkki pluto[1933]: "L2TP-PSK-NAT"[3] 188.238.63.190 #3: STATE_MAIN_R3: sent MR3, ISAKMP SA established {auth=OAKLEY_PRESHARED_KEY cipher=aes_256 prf=oakley_sha group=modp1024}
Feb 20 22:51:13 purkki pluto[1933]: "L2TP-PSK-NAT"[3] 188.238.63.190 #3: Dead Peer Detection (RFC 3706): enabled
Feb 20 22:51:13 purkki pluto[1933]: "L2TP-PSK-NAT"[3] 188.238.63.190 #3: ignoring informational payload, type IPSEC_INITIAL_CONTACT msgid=00000000
Feb 20 22:51:13 purkki pluto[1933]: "L2TP-PSK-NAT"[3] 188.238.63.190 #3: received and ignored informational message
Feb 20 22:51:14 purkki pluto[1933]: "L2TP-PSK-NAT"[3] 188.238.63.190 #3: byte 7 of ISAKMP NAT-OA Payload must be zero, but is not
Feb 20 22:51:14 purkki pluto[1933]: "L2TP-PSK-NAT"[3] 188.238.63.190 #3: malformed payload in packet
Feb 20 22:51:14 purkki pluto[1933]: | payload malformed after IV
Feb 20 22:51:14 purkki pluto[1933]: |   ca 78 72 74  46 78 28 79  7b 31 20 0e  32 ca dd 08
Feb 20 22:51:14 purkki pluto[1933]: "L2TP-PSK-NAT"[3] 188.238.63.190 #3: sending notification PAYLOAD_MALFORMED to 188.238.63.190:4500
Feb 20 22:51:17 purkki pluto[1933]: "L2TP-PSK-NAT"[3] 188.238.63.190 #3: byte 7 of ISAKMP NAT-OA Payload must be zero, but is not
Feb 20 22:51:17 purkki pluto[1933]: "L2TP-PSK-NAT"[3] 188.238.63.190 #3: malformed payload in packet
Feb 20 22:51:17 purkki pluto[1933]: | payload malformed after IV
Feb 20 22:51:17 purkki pluto[1933]: |   ca 78 72 74  46 78 28 79  7b 31 20 0e  32 ca dd 08
Feb 20 22:51:17 purkki pluto[1933]: "L2TP-PSK-NAT"[3] 188.238.63.190 #3: sending notification PAYLOAD_MALFORMED to 188.238.63.190:4500
Feb 20 22:51:20 purkki pluto[1933]: "L2TP-PSK-NAT"[3] 188.238.63.190 #3: byte 7 of ISAKMP NAT-OA Payload must be zero, but is not
Feb 20 22:51:20 purkki pluto[1933]: "L2TP-PSK-NAT"[3] 188.238.63.190 #3: malformed payload in packet
Feb 20 22:51:20 purkki pluto[1933]: | payload malformed after IV
Feb 20 22:51:20 purkki pluto[1933]: |   ca 78 72 74  46 78 28 79  7b 31 20 0e  32 ca dd 08
Feb 20 22:51:20 purkki pluto[1933]: "L2TP-PSK-NAT"[3] 188.238.63.190 #3: sending notification PAYLOAD_MALFORMED to 188.238.63.190:4500
Feb 20 22:51:23 purkki pluto[1933]: "L2TP-PSK-NAT"[3] 188.238.63.190 #3: byte 7 of ISAKMP NAT-OA Payload must be zero, but is not
Feb 20 22:51:23 purkki pluto[1933]: "L2TP-PSK-NAT"[3] 188.238.63.190 #3: malformed payload in packet
Feb 20 22:51:23 purkki pluto[1933]: | payload malformed after IV
Feb 20 22:51:23 purkki pluto[1933]: |   ca 78 72 74  46 78 28 79  7b 31 20 0e  32 ca dd 08
Feb 20 22:51:23 purkki pluto[1933]: "L2TP-PSK-NAT"[3] 188.238.63.190 #3: sending notification PAYLOAD_MALFORMED to 188.238.63.190:4500
Feb 20 22:51:26 purkki pluto[1933]: "L2TP-PSK-NAT"[3] 188.238.63.190 #3: byte 7 of ISAKMP NAT-OA Payload must be zero, but is not
Feb 20 22:51:26 purkki pluto[1933]: "L2TP-PSK-NAT"[3] 188.238.63.190 #3: malformed payload in packet
Feb 20 22:51:26 purkki pluto[1933]: | payload malformed after IV
Feb 20 22:51:26 purkki pluto[1933]: |   ca 78 72 74  46 78 28 79  7b 31 20 0e  32 ca dd 08
Feb 20 22:51:26 purkki pluto[1933]: "L2TP-PSK-NAT"[3] 188.238.63.190 #3: sending notification PAYLOAD_MALFORMED to 188.238.63.190:4500
Feb 20 22:51:29 purkki pluto[1933]: "L2TP-PSK-NAT"[3] 188.238.63.190 #3: byte 7 of ISAKMP NAT-OA Payload must be zero, but is not
Feb 20 22:51:29 purkki pluto[1933]: "L2TP-PSK-NAT"[3] 188.238.63.190 #3: malformed payload in packet
Feb 20 22:51:29 purkki pluto[1933]: | payload malformed after IV
Feb 20 22:51:29 purkki pluto[1933]: |   ca 78 72 74  46 78 28 79  7b 31 20 0e  32 ca dd 08
Feb 20 22:51:29 purkki pluto[1933]: "L2TP-PSK-NAT"[3] 188.238.63.190 #3: sending notification PAYLOAD_MALFORMED to 188.238.63.190:4500
Feb 20 22:51:32 purkki pluto[1933]: "L2TP-PSK-NAT"[3] 188.238.63.190 #3: byte 7 of ISAKMP NAT-OA Payload must be zero, but is not
Feb 20 22:51:32 purkki pluto[1933]: "L2TP-PSK-NAT"[3] 188.238.63.190 #3: malformed payload in packet
Feb 20 22:51:32 purkki pluto[1933]: | payload malformed after IV
Feb 20 22:51:32 purkki pluto[1933]: |   ca 78 72 74  46 78 28 79  7b 31 20 0e  32 ca dd 08
Feb 20 22:51:32 purkki pluto[1933]: "L2TP-PSK-NAT"[3] 188.238.63.190 #3: sending notification PAYLOAD_MALFORMED to 188.238.63.190:4500
Feb 20 22:51:35 purkki pluto[1933]: "L2TP-PSK-NAT"[3] 188.238.63.190 #3: byte 7 of ISAKMP NAT-OA Payload must be zero, but is not
Feb 20 22:51:35 purkki pluto[1933]: "L2TP-PSK-NAT"[3] 188.238.63.190 #3: malformed payload in packet
Feb 20 22:51:35 purkki pluto[1933]: | payload malformed after IV
Feb 20 22:51:35 purkki pluto[1933]: |   ca 78 72 74  46 78 28 79  7b 31 20 0e  32 ca dd 08
Feb 20 22:51:35 purkki pluto[1933]: "L2TP-PSK-NAT"[3] 188.238.63.190 #3: sending notification PAYLOAD_MALFORMED to 188.238.63.190:4500
Feb 20 22:51:38 purkki pluto[1933]: "L2TP-PSK-NAT"[3] 188.238.63.190 #3: byte 7 of ISAKMP NAT-OA Payload must be zero, but is not
Feb 20 22:51:38 purkki pluto[1933]: "L2TP-PSK-NAT"[3] 188.238.63.190 #3: malformed payload in packet
Feb 20 22:51:38 purkki pluto[1933]: | payload malformed after IV
Feb 20 22:51:38 purkki pluto[1933]: |   ca 78 72 74  46 78 28 79  7b 31 20 0e  32 ca dd 08
Feb 20 22:51:38 purkki pluto[1933]: "L2TP-PSK-NAT"[3] 188.238.63.190 #3: sending notification PAYLOAD_MALFORMED to 188.238.63.190:4500
Feb 20 22:51:41 purkki pluto[1933]: "L2TP-PSK-NAT"[3] 188.238.63.190 #3: byte 7 of ISAKMP NAT-OA Payload must be zero, but is not
Feb 20 22:51:41 purkki pluto[1933]: "L2TP-PSK-NAT"[3] 188.238.63.190 #3: malformed payload in packet
Feb 20 22:51:41 purkki pluto[1933]: | payload malformed after IV
Feb 20 22:51:41 purkki pluto[1933]: |   ca 78 72 74  46 78 28 79  7b 31 20 0e  32 ca dd 08
Feb 20 22:51:41 purkki pluto[1933]: "L2TP-PSK-NAT"[3] 188.238.63.190 #3: sending notification PAYLOAD_MALFORMED to 188.238.63.190:4500
Feb 20 22:52:13 purkki pluto[1933]: ERROR: asynchronous network error report on eth0 (sport=4500) for message to 188.238.63.190 port 4500, complainant 188.238.63.190: Connection refused [errno 111, origin ICMP type 3 code 3 (not authenticated)]



```When i do try connect from my lan pc - to 192.168.0.2 (ubuntu-serv) this does work..

Does my router do that ?

---

### Post by Weird87 on 2012-02-26
Hi all,

I've set up everything as explained in the guide, but somehow my iPhone keeps giving a timeout error. The log files are included below.

Can anyone help me?

auth.log:
 ```

Feb 26 16:56:51 server pluto[4200]: Using Linux 2.6 IPsec interface code on 3.0.0-16-server (experimental code)
Feb 26 16:56:51 server pluto[4202]: using /dev/urandom as source of random entropy
Feb 26 16:56:51 server pluto[4200]: ike_alg_register_enc(): Activating aes_ccm_8: Ok (ret=0)
Feb 26 16:56:51 server pluto[4200]: ike_alg_add(): ERROR: Algorithm already exists
Feb 26 16:56:51 server pluto[4200]: ike_alg_register_enc(): Activating aes_ccm_12: FAILED (ret=-17)
Feb 26 16:56:51 server pluto[4200]: ike_alg_add(): ERROR: Algorithm already exists
Feb 26 16:56:51 server pluto[4200]: ike_alg_register_enc(): Activating aes_ccm_16: FAILED (ret=-17)
Feb 26 16:56:51 server pluto[4200]: ike_alg_add(): ERROR: Algorithm already exists
Feb 26 16:56:51 server pluto[4200]: ike_alg_register_enc(): Activating aes_gcm_8: FAILED (ret=-17)
Feb 26 16:56:51 server pluto[4200]: ike_alg_add(): ERROR: Algorithm already exists
Feb 26 16:56:51 server pluto[4200]: ike_alg_register_enc(): Activating aes_gcm_12: FAILED (ret=-17)
Feb 26 16:56:51 server pluto[4200]: ike_alg_add(): ERROR: Algorithm already exists
Feb 26 16:56:51 server pluto[4200]: ike_alg_register_enc(): Activating aes_gcm_16: FAILED (ret=-17)
Feb 26 16:56:51 server pluto[4200]: Changed path to directory '/etc/ipsec.d/cacerts'
Feb 26 16:56:51 server pluto[4200]: Changed path to directory '/etc/ipsec.d/aacerts'
Feb 26 16:56:51 server pluto[4200]: Changed path to directory '/etc/ipsec.d/ocspcerts'
Feb 26 16:56:51 server pluto[4200]: Changing to directory '/etc/ipsec.d/crls'
Feb 26 16:56:51 server pluto[4200]:   Warning: empty directory
Feb 26 16:56:51 server pluto[4200]: added connection description "L2TP-PSK-NAT"
Feb 26 16:56:51 server pluto[4200]: "L2TP-PSK-NAT": deleting connection
Feb 26 16:56:51 server pluto[4200]: added connection description "L2TP-PSK-NAT"
Feb 26 16:56:51 server pluto[4200]: added connection description "L2TP-PSK-noNAT"
Feb 26 16:56:51 server pluto[4200]: listening for IKE messages
Feb 26 16:56:51 server pluto[4200]: NAT-Traversal: Trying new style NAT-T
Feb 26 16:56:51 server pluto[4200]: NAT-Traversal: ESPINUDP(1) setup failed for new style NAT-T family IPv4 (errno=19)
Feb 26 16:56:51 server pluto[4200]: NAT-Traversal: Trying old style NAT-T
Feb 26 16:56:51 server pluto[4200]: adding interface eth0/eth0 192.168.1.7:500
Feb 26 16:56:51 server pluto[4200]: adding interface eth0/eth0 192.168.1.7:4500
Feb 26 16:56:51 server pluto[4200]: adding interface lo/lo 127.0.0.1:500
Feb 26 16:56:51 server pluto[4200]: adding interface lo/lo 127.0.0.1:4500
Feb 26 16:56:51 server pluto[4200]: adding interface lo/lo ::1:500
Feb 26 16:56:51 server pluto[4200]: adding interface eth0/eth0 2002:546b:b578:0:217:31ff:fe65:8706:500
Feb 26 16:56:51 server pluto[4200]: loading secrets from "/etc/ipsec.secrets"
Feb 26 16:56:55 server sudo:     joep : TTY=pts/0 ; PWD=/etc ; USER=root ; COMMAND=/usr/sbin/xl2tpd -D
Feb 26 16:57:01 server pluto[4200]: packet from <<iPhone 3g ip>>:317: received Vendor ID payload [RFC 3947] method set to=109
Feb 26 16:57:01 server pluto[4200]: packet from <<iPhone 3g ip>>:317: received Vendor ID payload [draft-ietf-ipsec-nat-t-ike] method set to=110
Feb 26 16:57:01 server pluto[4200]: packet from <<iPhone 3g ip>>:317: ignoring unknown Vendor ID payload [8f8d83826d246b6fc7a8a6a428c11de8]
Feb 26 16:57:01 server pluto[4200]: packet from <<iPhone 3g ip>>:317: ignoring unknown Vendor ID payload [439b59f8ba676c4c7737ae22eab8f582]
Feb 26 16:57:01 server pluto[4200]: packet from <<iPhone 3g ip>>:317: ignoring unknown Vendor ID payload [4d1e0e136deafa34c4f3ea9f02ec7285]
Feb 26 16:57:01 server pluto[4200]: packet from <<iPhone 3g ip>>:317: ignoring unknown Vendor ID payload [80d0bb3def54565ee84645d4c85ce3ee]
Feb 26 16:57:01 server pluto[4200]: packet from <<iPhone 3g ip>>:317: ignoring unknown Vendor ID payload [9909b64eed937c6573de52ace952fa6b]
Feb 26 16:57:01 server pluto[4200]: packet from <<iPhone 3g ip>>:317: received Vendor ID payload [draft-ietf-ipsec-nat-t-ike-03] meth=108, but already using method 110
Feb 26 16:57:01 server pluto[4200]: packet from <<iPhone 3g ip>>:317: received Vendor ID payload [draft-ietf-ipsec-nat-t-ike-02] meth=107, but already using method 110
Feb 26 16:57:01 server pluto[4200]: packet from <<iPhone 3g ip>>:317: received Vendor ID payload [draft-ietf-ipsec-nat-t-ike-02_n] meth=106, but already using method 110
Feb 26 16:57:01 server pluto[4200]: packet from <<iPhone 3g ip>>:317: received Vendor ID payload [Dead Peer Detection]
Feb 26 16:57:01 server pluto[4200]: "L2TP-PSK-NAT"[1] <<iPhone 3g ip>> #1: responding to Main Mode from unknown peer <<iPhone 3g ip>>
Feb 26 16:57:01 server pluto[4200]: "L2TP-PSK-NAT"[1] <<iPhone 3g ip>> #1: transition from state STATE_MAIN_R0 to state STATE_MAIN_R1
Feb 26 16:57:01 server pluto[4200]: "L2TP-PSK-NAT"[1] <<iPhone 3g ip>> #1: STATE_MAIN_R1: sent MR1, expecting MI2
Feb 26 16:57:01 server pluto[4200]: "L2TP-PSK-NAT"[1] <<iPhone 3g ip>> #1: NAT-Traversal: Result using draft-ietf-ipsec-nat-t-ike (MacOS X): both are NATed
Feb 26 16:57:01 server pluto[4200]: "L2TP-PSK-NAT"[1] <<iPhone 3g ip>> #1: transition from state STATE_MAIN_R1 to state STATE_MAIN_R2
Feb 26 16:57:01 server pluto[4200]: "L2TP-PSK-NAT"[1] <<iPhone 3g ip>> #1: STATE_MAIN_R2: sent MR2, expecting MI3
Feb 26 16:57:02 server pluto[4200]: "L2TP-PSK-NAT"[1] <<iPhone 3g ip>> #1: ignoring informational payload, type IPSEC_INITIAL_CONTACT msgid=00000000
Feb 26 16:57:02 server pluto[4200]: "L2TP-PSK-NAT"[1] <<iPhone 3g ip>> #1: Main mode peer ID is ID_IPV4_ADDR: '10.103.29.96'
Feb 26 16:57:02 server pluto[4200]: "L2TP-PSK-NAT"[1] <<iPhone 3g ip>> #1: switched from "L2TP-PSK-NAT" to "L2TP-PSK-NAT"
Feb 26 16:57:02 server pluto[4200]: "L2TP-PSK-NAT"[2] <<iPhone 3g ip>> #1: deleting connection "L2TP-PSK-NAT" instance with peer <<iPhone 3g ip>> {isakmp=#0/ipsec=#0}
Feb 26 16:57:02 server pluto[4200]: "L2TP-PSK-NAT"[2] <<iPhone 3g ip>> #1: transition from state STATE_MAIN_R2 to state STATE_MAIN_R3
Feb 26 16:57:02 server pluto[4200]: "L2TP-PSK-NAT"[2] <<iPhone 3g ip>> #1: new NAT mapping for #1, was <<iPhone 3g ip>>:317, now 62.133.64.13:19060
Feb 26 16:57:02 server pluto[4200]: "L2TP-PSK-NAT"[2] 62.133.64.13 #1: STATE_MAIN_R3: sent MR3, ISAKMP SA established {auth=OAKLEY_PRESHARED_KEY cipher=aes_256 prf=oakley_sha group=modp1024}
Feb 26 16:57:02 server pluto[4200]: "L2TP-PSK-NAT"[2] 62.133.64.13 #1: Dead Peer Detection (RFC 3706): enabled
Feb 26 16:57:03 server pluto[4200]: "L2TP-PSK-NAT"[2] 62.133.64.13 #1: the peer proposed: 84.107.181.120/32:17/1701 -> 10.103.29.96/32:17/1701
Feb 26 16:57:03 server pluto[4200]: "L2TP-PSK-NAT"[2] 62.133.64.13 #2: responding to Quick Mode proposal {msgid:ea4025d0}
Feb 26 16:57:03 server pluto[4200]: "L2TP-PSK-NAT"[2] 62.133.64.13 #2:     us: 192.168.1.7<192.168.1.7>[+S=C]:17/1701---192.168.1.1
Feb 26 16:57:03 server pluto[4200]: "L2TP-PSK-NAT"[2] 62.133.64.13 #2:   them: 62.133.64.13[10.103.29.96,+S=C]:17/1701===10.103.29.96/32
Feb 26 16:57:03 server pluto[4200]: "L2TP-PSK-NAT"[2] 62.133.64.13 #2: transition from state STATE_QUICK_R0 to state STATE_QUICK_R1
Feb 26 16:57:03 server pluto[4200]: "L2TP-PSK-NAT"[2] 62.133.64.13 #2: STATE_QUICK_R1: sent QR1, inbound IPsec SA installed, expecting QI2
Feb 26 16:57:03 server pluto[4200]: "L2TP-PSK-NAT"[2] 62.133.64.13 #2: netlink_raw_eroute: WARNING: that_client port 50979 and that_host port 19060 don't match. Using that_client port.
Feb 26 16:57:03 server pluto[4200]: "L2TP-PSK-NAT"[2] 62.133.64.13 #2: Dead Peer Detection (RFC 3706): enabled
Feb 26 16:57:03 server pluto[4200]: "L2TP-PSK-NAT"[2] 62.133.64.13 #2: transition from state STATE_QUICK_R1 to state STATE_QUICK_R2
Feb 26 16:57:03 server pluto[4200]: "L2TP-PSK-NAT"[2] 62.133.64.13 #2: STATE_QUICK_R2: IPsec SA established transport mode {ESP=>0x09c33038 <0x420d86a3 xfrm=AES_256-HMAC_SHA1 NATOA=none NATD=62.133.64.13:19060 DPD=enabled}

```
  

xl2tp log:
```
xl2tpd[4242]: Enabling IPsec SAref processing for L2TP transport mode SAs
xl2tpd[4242]: IPsec SAref does not work with L2TP kernel mode yet, enabling forceuserspace=yes
xl2tpd[4242]: setsockopt recvref[22]: Protocol not available
xl2tpd[4242]: This binary does not support kernel L2TP.
xl2tpd[4242]: xl2tpd version xl2tpd-1.2.8 started on server PID:4242
xl2tpd[4242]: Written by Mark Spencer, Copyright (C) 1998, Adtran, Inc.
xl2tpd[4242]: Forked by Scott Balmos and David Stipp, (C) 2001
xl2tpd[4242]: Inherited by Jeff McAdams, (C) 2002
xl2tpd[4242]: Forked again by Xelerance (www.xelerance.com) (C) 2006
xl2tpd[4242]: Listening on IP address 0.0.0.0, port 1701
xl2tpd[4242]: control_finish: Peer requested tunnel 56 twice, ignoring second one.
xl2tpd[4242]: Connection established to 62.133.64.13, 50979.  Local: 19159, Remote: 56 (ref=0/0).  LNS session is 'default'
xl2tpd[4242]: start_pppd: I'm running:
xl2tpd[4242]: "/usr/sbin/pppd"
xl2tpd[4242]: "passive"
xl2tpd[4242]: "nodetach"
xl2tpd[4242]: "192.168.0.1:192.168.0.2"
xl2tpd[4242]: "refuse-pap"
xl2tpd[4242]: "refuse-chap"
xl2tpd[4242]: "auth"
xl2tpd[4242]: "debug"
xl2tpd[4242]: "file"
xl2tpd[4242]: "/etc/ppp/options.xl2tpd"
xl2tpd[4242]: "ipparam"
xl2tpd[4242]: "62.133.64.13"
xl2tpd[4242]: "/dev/pts/1"
xl2tpd[4242]: Call established with 62.133.64.13, Local: 9906, Remote: 11802, Serial: 1
/usr/sbin/pppd: The remote system is required to authenticate itself
/usr/sbin/pppd: but I couldn't find any suitable secret (password) for it to use to do so.
xl2tpd[4242]: child_handler : pppd exited for call 11802 with code 1
xl2tpd[4242]: call_close: Call 9906 to 62.133.64.13 disconnected
xl2tpd[4242]: write_packet: tty is not open yet.
xl2tpd[4242]: result_code_avp: result code endianness fix for buggy Apple client. network=768, le=3
xl2tpd[4242]: control_finish: Connection closed to 62.133.64.13, serial 1 ()
xl2tpd[4242]: Terminating pppd: sending TERM signal to pid 4250
xl2tpd[4242]: result_code_avp: result code endianness fix for buggy Apple client. network=256, le=1
xl2tpd[4242]: control_finish: Connection closed to <<iPhone ip>>, port 50979 (), Local: 19159, Remote: 56
xl2tpd[4242]: Can not find tunnel 19159 (refhim=0)
xl2tpd[4242]: network_thread: unable to find call or tunnel to handle packet.  call = 9906, tunnel = 19159 Dumping.
xl2tpd[4242]: Can not find tunnel 19159 (refhim=0)
xl2tpd[4242]: network_thread: unable to find call or tunnel to handle packet.  call = 9906, tunnel = 19159 Dumping.
xl2tpd[4242]: Can not find tunnel 19159 (refhim=0)

```

---

### Post by Jshanna on 2012-03-16
Great guide thanks for writing and updating it!

I have my VPN server running, and accepting connections. But I'd like to enable split tunneling (Totally aware of the security risks.) Any help with that? Right now if a user un-checks the use default gateway on remote network the VPN still accepts the connection, but they're unable to reach anything on the private network.

My network situation is a little strange as I'm on a university network and have a static IP that's internet facing, and a static IP that's internal network facing that I'm NATing into a network that the internal VPN side is on.

---

### Post by daqron on 2012-03-30
It works! Holy cow! I don't know why it is so hard to setup VPN on Ubuntu, but I REALLY appreciate this tutorial for VPN beginners like me. I can now VPN to my home network from the road, and browse the web from coffee shops more securely. Wonderful. I now have this running on Ubuntu 10.04 (server) and it works with MacOS Lion (client).

[B]Some questions and maybe hints for silly people (like me) who may need help with things that are obvious to others ...
[/B]
[LIST=1]
[*]This line doesn't seem to work from the command line, even with sudo.
```
echo 1 > /proc/sys/net/ipv4/ip_forward
```
I had to do:
```
sudo passwd root
[enter root password, then set root password ... don't ask me why]
su
echo 1 > /proc/sys/net/ipv4/ip_forward
```
[*]I could not make this work with the server behind three routers. My previous setup had a DSL router, then a Cisco router that held my entire house's subnet, then another Cisco router with my home office subnet. Although I configured all routers in the chain for appropriate port forwarding it did not work. I removed the middle-man router, so it goes internet->dsl router->Cisco home router. Good enough I guess. Is this a real limitation of the VPN solution or something I did wrong? Guessing the latter.

 
[*]Tutorial says to forward UDP ports 500 and 4500. I suspect 1701 may also be required?


[*]After running ipsec verify there were two failures as follows:
```

NETKEY detected, testing for disabled ICMP send_redirects       [FAILED]

  Please disable /proc/sys/net/ipv4/conf/*/send_redirects
  or NETKEY will cause the sending of bogus ICMP redirects!

NETKEY detected, testing for disabled ICMP accept_redirects     [FAILED]

  Please disable /proc/sys/net/ipv4/conf/*/accept_redirects
  or NETKEY will accept bogus ICMP redirects!
```
Found a fix for this:
```

sudo sysctl -a | grep 'ipv4.conf.*redirect'

```
Copy all the results, then paste all at the bottom of /etc/sysctl.conf, then set all the values to 0 instead of 1.
[/LIST]

Anyway THANKS again for this fantastic thread!

---

### Post by ndoggac on 2012-04-17
I haven't updated to the latest release of Ubuntu yet, so I'm not sure if this get's broken or not.  Jshanna & Daqron, are you two running the latest release?  Glad to hear it's still working for some though.

----------------

Weird87

saw this line...which looks a little suspect

Listening on IP address 0.0.0.0, port 1701

I would go back through and double check all settings and conf files, and re-read my notes about IP address ranges, etc.

----------------

Daqron...dang - three routers!!  I don't think it's a limitation in the VPN, as corporate solutions typically have multiple sub-nets to work through.  The top most router (closest to ISP) forwarded ports to the second router's WAN address, which then forwarded to the 3rd router's WAN address, which then forwarded to the server's IP?  Sorry, I'm not supporting that any further :p

Mine runs fine without port 1701.

----------------

Jshanna, if you're not NAT'ing your internet facing IP into your local LAN, then I think you're at a dead end.  I'm assuming two physical ports here. If separate physical ports, then a separate router would be needed to NAT the external IP into same LAN.  Maybe run a separate virtual machine of Ubuntu server to keep setup simple.  The VM only handles the VPN from the external facing route.  Good way to sandbox the two from each other as well.

If the internet facing IP forwards all traffic to your local LAN IP then this setup should still work.  Can't give better answers without being more familiar with the setup.  Sorry.

----------------

---

### Post by ndoggac on 2012-04-17
logman, i'm thinking you might be getting frame corruption on data NAT'd through the router?  any chance you're running jumbo frames on your router?  Try turning off jumbo frame support and seeing if you can connect.

not sure what else might cause that problem without knowing router brand, model and firmware.  Is your router compatible with third party firmwares (DDWRT or Tomato)?  Might want to give those a try.

or this?
[http://www.ithowto.ro/2011/04/ipsec-openswan-probable-authentication-failure-psk-shared-keys/](http://www.ithowto.ro/2011/04/ipsec-openswan-probable-authentication-failure-psk-shared-keys/)

---

### Post by cmvogt5 on 2012-06-22
Thanks for the info. I can confirm this still works on 12.04 as of today and can connect with a Droid 2 Global running Android 2.3.4.

Much appreciated!

---

### Post by h3nk3 on 2012-07-08
Hi there !!!

I can confirm that it also work for me in ubuntu 12.04 x64

Just ONE thing.....it must be started manually through the command Sudo /etc/init.d/ipsec restart. I have tried many ways of getting the command launched during bootup but no success. The rc.local script file doesnt work for me. I&#7743; using gnome 3

Anyone that has the same problem???

---

### Post by h3nk3 on 2012-07-20
Hi folks. As I Said in erlier post i had this running in ubuntu 12.04 x64 with gnome 3. But suddently ipsec had problems with startup on boot even though the command /etc/init.d ipsec restart was typed in my /etc/rc.local. After googling a while i found out one WORKING solution. I had to put a delay to ipsec restart command. 
I putted this row into /etc/rc.local file :

bash -c "sleep 5; /etc/init.d/ipsec restart"

Now my l2tp/ipsec tunnel starts again on every Re/boot :-) :-) :-)

---

### Post by hellz99 on 2012-07-26
I've tried this on two servers and no matter what I get to the same point and timeout. Servers are a 10.04 server and a 12.04 server running openswan 2.6.38, I've disabled my ufw and cleared out all rules in iptables, although this still may be an iptables problem. 

```
happy pluto[15326]: packet from 1.2.3.4:500: received Vendor ID payload [RFC 3947] method set to=109
happy pluto[15326]: packet from 1.2.3.4:500: received Vendor ID payload [draft-ietf-ipsec-nat-t-ike-02] meth=107, but already using method 109
happy pluto[15326]: packet from 1.2.3.4:500: received Vendor ID payload [draft-ietf-ipsec-nat-t-ike-02_n] meth=106, but already using method 109
happy pluto[15326]: packet from 1.2.3.4:500: received Vendor ID payload [draft-ietf-ipsec-nat-t-ike-00]
happy pluto[15326]: packet from 1.2.3.4:500: ignoring Vendor ID payload [FRAGMENTATION 80000000]
happy pluto[15326]: packet from 1.2.3.4:500: received Vendor ID payload [Dead Peer Detection]
happy pluto[15326]: "L2TP-PSK-NAT"[2] 1.2.3.4 #3: responding to Main Mode from unknown peer 1.2.3.4
happy pluto[15326]: "L2TP-PSK-NAT"[2] 1.2.3.4 #3: transition from state STATE_MAIN_R0 to state STATE_MAIN_R1
happy pluto[15326]: "L2TP-PSK-NAT"[2] 1.2.3.4 #3: STATE_MAIN_R1: sent MR1, expecting MI2
happy pluto[15326]: "L2TP-PSK-NAT"[2] 1.2.3.4 #3: NAT-Traversal: Result using RFC 3947 (NAT-Traversal): peer is NATed
happy pluto[15326]: "L2TP-PSK-NAT"[2] 1.2.3.4 #3: transition from state STATE_MAIN_R1 to state STATE_MAIN_R2
happy pluto[15326]: "L2TP-PSK-NAT"[2] 1.2.3.4 #3: STATE_MAIN_R2: sent MR2, expecting MI3
happy pluto[15326]: "L2TP-PSK-NAT"[2] 1.2.3.4 #3: Main mode peer ID is ID_IPV4_ADDR: '192.168.0.128'
happy pluto[15326]: "L2TP-PSK-NAT"[2] 1.2.3.4 #3: transition from state STATE_MAIN_R2 to state STATE_MAIN_R3
happy pluto[15326]: "L2TP-PSK-NAT"[2] 1.2.3.4 #3: new NAT mapping for #3, was 1.2.3.4:500, now 1.2.3.4:4500
happy pluto[15326]: "L2TP-PSK-NAT"[2] 1.2.3.4 #3: STATE_MAIN_R3: sent MR3, ISAKMP SA established {auth=OAKLEY_PRESHARED_KEY cipher=aes_256 prf=oak                               ley_sha group=modp1024}
happy pluto[15326]: "L2TP-PSK-NAT"[2] 1.2.3.4 #3: ignoring informational payload, type IPSEC_INITIAL_CONTACT msgid=00000000
happy pluto[15326]: "L2TP-PSK-NAT"[2] 1.2.3.4 #3: received and ignored informational message
happy pluto[15326]: "L2TP-PSK-NAT"[2] 1.2.3.4 #3: the peer proposed: XXX.XXX.131.54/32:17/1701 -> 192.168.0.128/32:17/0
happy pluto[15326]: "L2TP-PSK-NAT"[2] 1.2.3.4 #4: responding to Quick Mode proposal {msgid:3a02acf5}
happy pluto[15326]: "L2TP-PSK-NAT"[2] 1.2.3.4 #4:     us: XXX.XXX.131.54<XXX.XXX.131.54>[+S=C]:17/1701
happy pluto[15326]: "L2TP-PSK-NAT"[2] 1.2.3.4 #4:   them: 1.2.3.4[192.168.0.128,+S=C]:17/0===192.168.0.128/32
happy pluto[15326]: "L2TP-PSK-NAT"[2] 1.2.3.4 #4: keeping refhim=4294901761 during rekey
happy pluto[15326]: "L2TP-PSK-NAT"[2] 1.2.3.4 #4: transition from state STATE_QUICK_R0 to state STATE_QUICK_R1
happy pluto[15326]: "L2TP-PSK-NAT"[2] 1.2.3.4 #4: STATE_QUICK_R1: sent QR1, inbound IPsec SA installed, expecting QI2
happy pluto[15326]: "L2TP-PSK-NAT"[2] 1.2.3.4 #4: transition from state STATE_QUICK_R1 to state STATE_QUICK_R2
happy pluto[15326]: "L2TP-PSK-NAT"[2] 1.2.3.4 #4: STATE_QUICK_R2: IPsec SA established transport mode {ESP=>0x0a36ebd1 <0x945700aa xfrm=AES_256-HM                               AC_SHA1 NATOA=none NATD=1.2.3.4:4500 DPD=none}
```

This is from my auth.log and it stops there everytime and then the client times out. Tried android 4.1, 2.3 and a windows client. I have a feeling I'm missing something obvious and any insight on where to look would be great help.

---

### Post by hellz99 on 2012-07-26
I also got my logging in the xl2tpd. Looks like it keeps trying over and over for some reason:

```
xl2tpd[15694]: IPsec SAref does not work with L2TP kernel mode yet, enabling forceuserspace=yes
xl2tpd[15694]: setsockopt recvref[22]: Protocol not available
xl2tpd[15694]: This binary does not support kernel L2TP.
xl2tpd[15694]: xl2tpd version xl2tpd-1.2.5 started on anger PID:15694
xl2tpd[15694]: Written by Mark Spencer, Copyright (C) 1998, Adtran, Inc.
xl2tpd[15694]: Forked by Scott Balmos and David Stipp, (C) 2001
xl2tpd[15694]: Inherited by Jeff McAdams, (C) 2002
xl2tpd[15694]: Forked again by Xelerance (www.xelerance.com) (C) 2006
xl2tpd[15694]: Listening on IP address 0.0.0.0, port 1701
xl2tpd[15694]: get_call: allocating new tunnel for host XXX.XXX.30.50, port 36421.
xl2tpd[15694]: handle_avps: handling avp's for tunnel 61924, call 0
xl2tpd[15694]: message_type_avp: message type 1 (Start-Control-Connection-Request)
xl2tpd[15694]: protocol_version_avp: peer is using version 1, revision 0.
xl2tpd[15694]: hostname_avp: peer reports hostname 'anonymous'
xl2tpd[15694]: framing_caps_avp: supported peer frames: async sync
xl2tpd[15694]: assigned_tunnel_avp: using peer's tunnel 10712
xl2tpd[15694]: receive_window_size_avp: peer wants RWS of 1.  Will use flow control.
xl2tpd[15694]: challenge_avp: challenge avp found
xl2tpd[15694]: get_call: allocating new tunnel for host XXX.XXX.30.50, port 36421.
xl2tpd[15694]: handle_avps: handling avp's for tunnel 10553, call 0
xl2tpd[15694]: message_type_avp: message type 1 (Start-Control-Connection-Request)
xl2tpd[15694]: protocol_version_avp: peer is using version 1, revision 0.
xl2tpd[15694]: hostname_avp: peer reports hostname 'anonymous'
xl2tpd[15694]: framing_caps_avp: supported peer frames: async sync
xl2tpd[15694]: assigned_tunnel_avp: using peer's tunnel 10712
xl2tpd[15694]: receive_window_size_avp: peer wants RWS of 1.  Will use flow control.
xl2tpd[15694]: challenge_avp: challenge avp found
xl2tpd[15694]: control_finish: Peer requested tunnel 10712 twice, ignoring second one.
xl2tpd[15694]: build_fdset: closing down tunnel 10553
xl2tpd[15694]: get_call: allocating new tunnel for host XXX.XXX.30.50, port 36421.
xl2tpd[15694]: handle_avps: handling avp's for tunnel 37720, call 19256
xl2tpd[15694]: message_type_avp: message type 1 (Start-Control-Connection-Request)
xl2tpd[15694]: protocol_version_avp: peer is using version 1, revision 0.
xl2tpd[15694]: hostname_avp: peer reports hostname 'anonymous'
xl2tpd[15694]: framing_caps_avp: supported peer frames: async sync
xl2tpd[15694]: assigned_tunnel_avp: using peer's tunnel 10712
xl2tpd[15694]: receive_window_size_avp: peer wants RWS of 1.  Will use flow control.
xl2tpd[15694]: challenge_avp: challenge avp found
xl2tpd[15694]: control_finish: Peer requested tunnel 10712 twice, ignoring second one.
xl2tpd[15694]: build_fdset: closing down tunnel 37720
xl2tpd[15694]: get_call: allocating new tunnel for host XXX.XXX.30.50, port 36421.
xl2tpd[15694]: handle_avps: handling avp's for tunnel 32441, call 7051
xl2tpd[15694]: message_type_avp: message type 1 (Start-Control-Connection-Request)
xl2tpd[15694]: protocol_version_avp: peer is using version 1, revision 0.
xl2tpd[15694]: hostname_avp: peer reports hostname 'anonymous'
xl2tpd[15694]: framing_caps_avp: supported peer frames: async sync
xl2tpd[15694]: assigned_tunnel_avp: using peer's tunnel 10712
xl2tpd[15694]: receive_window_size_avp: peer wants RWS of 1.  Will use flow control.
xl2tpd[15694]: challenge_avp: challenge avp found
xl2tpd[15694]: control_finish: Peer requested tunnel 10712 twice, ignoring second one.
xl2tpd[15694]: build_fdset: closing down tunnel 32441
xl2tpd[15694]: Maximum retries exceeded for tunnel 61924.  Closing.
```

---

### Post by linuxexplore on 2012-11-29
I have a tutorial on xl2tpd, I hope it will be useful for others.
**[L2TP VPN using xl2tpd]("http://linuxexplore.com/how-tos/l2tp-vpn-using-xl2tpd/")**

[http://linuxexplore.com/how-tos/l2tp-vpn-using-xl2tpd/](http://linuxexplore.com/how-tos/l2tp-vpn-using-xl2tpd/)

Cheers,
Linux Explore | Exploring Linux

---

### Post by ThomasLWT on 2013-01-02
Good day all, 

Seems i'm running into the same issues most people are having here. 
can't get L2TP up and running. 

I've tried many different version of these configs and am stumped at the moment. 

Would someone mind looking over my configs. I've listed all versions, configs, and auth.log

Just wondering if it's me a or another bug.

thanks 

```
lsb_release -a
No LSB modules are available.
Distributor ID:Ubuntu
Description:Ubuntu 12.04.1 LTS
Release:12.04
Codename:precise

ipsec --version
Linux Openswan U2.6.37/K3.2.0-35-generic (netkey)
See `ipsec --copyright' for copyright information.

xl2tpd --version
xl2tpd version: xl2tpd-1.3.1
 
/etc/ipsec.conf file. 

# /etc/ipsec.conf - Openswan IPsec configuration file

# This file: /usr/share/doc/openswan/ipsec.conf-sample
#
# Manual: ipsec.conf.5
version 2.0

config setup
        nat_traversal=yes
        virtual_private=%v4:10.0.0.0/8,%v4:192.168.1.0/16,%v4:172.16.0.0/12
        oe=off
        protostack=netkey
        interfaces="%defaultroute"

conn l2tp-psk-NAT
        rightsubnet=vhost:%priv
        also=L2TP-PSK-noNAT

conn l2tp-psk-noNAT
        authby=secret
        pfs=no
        auto=add
        keyingtries=3
        rekey=no
        type=transport
        left=76.218.xx.xxx (outside IP address)
        leftnexthop=192.168.70.1 (inside router/firewall Untangle)
        leftprotoport=17/1701
        right=%any
        rightprotoport=17/%any
        dpddelay=15
        dpdtimeout=30
        dpdaction=clear
        #Uncomment the line below for OSX on MAC? untested!
        #rightprotoport=17/0


 /etc/xl2tpd/xl2tpd.conf 
;
; Sample l2tpd configuration file
;
; This example file should give you some idea of how the options for l2tpd
; should work. The best place to look for a list of all options is in
; the source code itself, until I have the time to write better documentation :
; Specifically, the file "file.c" contains a list of commands at the end.
;
; You most definitely don't have to spell out everything as it is done here
;
; [global] ; Globa$
; you cannot leave out listen-addr, causes possible wrong src ip on return pack$
listen-addr = 76.218.xx.xxx (Outside IP address)
ipsec saref = yes
; ipsec saref = yes ; For SAref + MAST only
; debug tunnel = yes

[lns default]
ip range = 192.168.70.250-192.168.70.254
local ip = 192.168.70.170 (L2PT server IP)
assign ip = yes
name = l2tpd
refuse chap = yes
refuse pap = yes
require authentication = yes
ppp debug = yes
pppoptfile = /etc/ppp/options.xl2tpd
length bit = yes


/etc/ppp/options.xl2tpd


ipcp-accept-local
ipcp-accept-remote
noccp
idle 1800
mtu 1200
mru 1200
nodefaultroute
connect-delay 5000
require-mschap-v2
ms-dns 192.168.70.1
asyncmap 0
auth
crtscts
lock
hide-password
modem
debug
name l2tpd
proxyarp
lcp-echo-interval 30
lcp-echo-failure 4


/etc/ppp/chap-secrets


# Secrets for authentication using CHAP
# client server secret IP addresses
username l2tpd "password" 192.168.70.251
l2tpd username "password" 192.168.70.252


/etc/ipsec.secrets

# This file holds shared secrets or RSA private keys for inter-Pluto
# authentication. See ipsec_pluto(8) manpage, and HTML documentation.

# RSA private key for this host, authenticating it to any other host
# which knows the public part. Suitable public keys, for ipsec.conf, DNS,
# or configuration of other implementations, can be extracted conveniently
# with "ipsec showhostkey".

# this file is managed with debconf and will contain the automatically created $
include /var/lib/openswan/ipsec.secrets.inc

192.168.70.170 %any: PSK "XXXXXXXXXXXXXXXXXXXXXXXXXXXXXX6"


ipsec verify

root@L2TP:~# ipsec verify
Checking your system to see if IPsec got installed and started correctly:
Version check and ipsec on-path [OK]
Linux Openswan U2.6.37/K3.2.0-35-generic (netkey)
Checking for IPsec support in kernel [OK]
 SAref kernel support [N/A]
 NETKEY: Testing XFRM related proc values [OK]
 [OK]
 [OK]
Checking that pluto is running [OK]
 Pluto listening for IKE on udp 500 [OK]
 Pluto listening for NAT-T on udp 4500 [OK]
Checking for 'ip' command [OK]
Checking /bin/sh is not /bin/dash [WARNING]
Checking for 'iptables' command [OK]
Opportunistic Encryption Support [DISABLED]
root@L2TP:~# 


/etc/rc.local
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser run level
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

for vpn in /proc/sys/net/ipv4/conf/*; do echo 0 > $vpn/accept_redirects; echo 0$
iptables --table nat --append POSTROUTING --jump MASQUERADE

echo 1 > /proc/sys/net/ipv4/ip_forward
iptables -t nat -A POSTROUTING -s 192.168.1.0/24 -o eth0 -j MASQUERADE


exit 0


tail -f /var/log/auth.log

Jan 2 17:30:29 L2TP pluto[1492]: packet from 166.137.179.34:61424: received Vendor ID payload [RFC 3947] method set to=109 
Jan 2 17:30:29 L2TP pluto[1492]: packet from 166.137.179.34:61424: received Vendor ID payload [draft-ietf-ipsec-nat-t-ike] method set to=110 
Jan 2 17:30:29 L2TP pluto[1492]: packet from 166.137.179.34:61424: ignoring unknown Vendor ID payload [8f8d83826d246b6fc7a8a6a428c11de8]
Jan 2 17:30:29 L2TP pluto[1492]: packet from 166.137.179.34:61424: ignoring unknown Vendor ID payload [439b59f8ba676c4c7737ae22eab8f582]
Jan 2 17:30:29 L2TP pluto[1492]: packet from 166.137.179.34:61424: ignoring unknown Vendor ID payload [4d1e0e136deafa34c4f3ea9f02ec7285]
Jan 2 17:30:29 L2TP pluto[1492]: packet from 166.137.179.34:61424: ignoring unknown Vendor ID payload [80d0bb3def54565ee84645d4c85ce3ee]
Jan 2 17:30:29 L2TP pluto[1492]: packet from 166.137.179.34:61424: ignoring unknown Vendor ID payload [9909b64eed937c6573de52ace952fa6b]
Jan 2 17:30:29 L2TP pluto[1492]: packet from 166.137.179.34:61424: received Vendor ID payload [draft-ietf-ipsec-nat-t-ike-03] meth=108, but already using method 110
Jan 2 17:30:29 L2TP pluto[1492]: packet from 166.137.179.34:61424: received Vendor ID payload [draft-ietf-ipsec-nat-t-ike-02] meth=107, but already using method 110
Jan 2 17:30:29 L2TP pluto[1492]: packet from 166.137.179.34:61424: received Vendor ID payload [draft-ietf-ipsec-nat-t-ike-02_n] meth=106, but already using method 110
Jan 2 17:30:29 L2TP pluto[1492]: packet from 166.137.179.34:61424: ignoring Vendor ID payload [FRAGMENTATION 80000000]
Jan 2 17:30:29 L2TP pluto[1492]: packet from 166.137.179.34:61424: received Vendor ID payload [Dead Peer Detection]
Jan 2 17:30:29 L2TP pluto[1492]: packet from 166.137.179.34:61424: initial Main Mode message received on 192.168.70.170:500 but no connection has been authorized with policy=PSK

```

---

### Post by dercommodore on 2013-03-01
Hey thanks for the great posts here.

I tried to bring my system to live according to this guide.
Unfortunately (I think) I ran into the same problem as you guys - starting the xl2tpd

[http://ubuntuforums.org/showthread.php?t=2121413]("http://ubuntuforums.org/showthread.php?t=2121413")

Can someone look over my logs and confirm this? Or is there another error hidden down there ... 
Is there anything new on this topic?

I would really love to use VPN.

---

