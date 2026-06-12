---
title: "How to set up VPN over PPPoE?"
date: 2011-07-21
forum: Networking &amp; Wireless
---

### Post by 98174 on 2011-07-21
I first connect to the internet by using pppoeconf to set up my PPPoE connection - it gets bound to ppp0.

Then, I attempt to run a VPN over that.  Since the network manager appears to be completely broken for me in 11.04 when configuring VPNs, I configured a manual VPN connection in /etc/ppp/peers.

Here's the output from the connection:

```

admin@DELL ~ $  > sudo pon cites nodetach
pppd options in effect:
debug           # (from /etc/ppp/peers/cites)
nodetach                # (from command line)
linkname cites          # (from /etc/ppp/peers/cites)
dump            # (from /etc/ppp/peers/cites)
noauth          # (from /etc/ppp/options.pptp)
refuse-pap              # (from /etc/ppp/options.pptp)
refuse-chap             # (from /etc/ppp/options.pptp)
refuse-mschap           # (from /etc/ppp/options.pptp)
refuse-eap              # (from /etc/ppp/options.pptp)
name <removed>               # (from /etc/ppp/peers/cites)
remotename cites                # (from /etc/ppp/peers/cites)
                # (from /etc/ppp/options.pptp)
pty pptp vpn3.near.uiuc.edu --nolaunchpppd              # (from /etc/ppp/peers/cites)
crtscts         # (from /etc/ppp/options)
                # (from /etc/ppp/options)
asyncmap 0              # (from /etc/ppp/options)
lcp-echo-failure 4              # (from /etc/ppp/options)
lcp-echo-interval 30            # (from /etc/ppp/options)
hide-password           # (from /etc/ppp/options)
ipparam cites           # (from /etc/ppp/peers/cites)
usepeerdns              # (from /etc/ppp/peers/cites)
nobsdcomp               # (from /etc/ppp/options.pptp)
nodeflate               # (from /etc/ppp/options.pptp)
nomppe-40               # (from /etc/ppp/peers/cites)
                # (from /etc/ppp/peers/cites)
noipx           # (from /etc/ppp/options)
using channel 15
Using interface ppp1
Connect: ppp1 <--> /dev/pts/3
sent [LCP ConfReq id=0x1 <asyncmap 0x0> <magic 0xafb4e529> <pcomp> <accomp>]
rcvd [LCP ConfReq id=0x1 <mru 1500> <asyncmap 0xa0000> <auth chap MS-v2> <magic 0xd970075> <pcomp> <accomp>]
sent [LCP ConfAck id=0x1 <mru 1500> <asyncmap 0xa0000> <auth chap MS-v2> <magic 0xd970075> <pcomp> <accomp>]
rcvd [LCP ConfAck id=0x1 <asyncmap 0x0> <magic 0xafb4e529> <pcomp> <accomp>]
sent [LCP EchoReq id=0x0 magic=0xafb4e529]
rcvd [CHAP Challenge id=0x2 <d69f1388653c88e559655f65e69687f7>, name = "192.17.144.2"]
sent [CHAP Response id=0x2 <6d42b5581a1e6522287c7ef3d9d1a1e70000000000000000899dd5d1164289111a1a8e56c7d33291efdf4582d02e294100>, name = "<removed>"]
rcvd [LCP EchoRep id=0x0 magic=0xd970075 af b4]
rcvd [CHAP Success id=0x2 "S=48130E8807ED7CB18FC104AAA9F5DED87BF93242"]
CHAP authentication succeeded
sent [CCP ConfReq id=0x1 <mppe +H -M +S -L -D -C>]
rcvd [IPCP ConfReq id=0x51 <addr 192.17.144.2> <compress VJ 07 00>]
sent [IPCP TermAck id=0x51]
rcvd [CCP ConfReq id=0x8e <mppe +H -M +S -L -D -C>]
sent [CCP ConfAck id=0x8e <mppe +H -M +S -L -D -C>]
rcvd [CCP ConfAck id=0x1 <mppe +H -M +S -L -D -C>]
MPPE 128-bit stateless compression enabled
sent [IPCP ConfReq id=0x1 <compress VJ 0f 01> <addr 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
rcvd [IPCP ConfRej id=0x1 <ms-dns2 0.0.0.0>]
sent [IPCP ConfReq id=0x2 <compress VJ 0f 01> <addr 0.0.0.0> <ms-dns1 0.0.0.0>]
rcvd [IPCP ConfNak id=0x2 <compress VJ 07 00> <addr 192.17.145.3> <ms-dns1 130.126.2.131>]
sent [IPCP ConfReq id=0x3 <compress VJ 07 00> <addr 192.17.145.3> <ms-dns1 130.126.2.131>]
rcvd [IPCP ConfAck id=0x3 <compress VJ 07 00> <addr 192.17.145.3> <ms-dns1 130.126.2.131>]
rcvd [IPCP ConfReq id=0x51 <addr 192.17.144.2> <compress VJ 07 00>]
sent [IPCP ConfAck id=0x51 <addr 192.17.144.2> <compress VJ 07 00>]
local  IP address 192.17.145.3
remote IP address 192.17.144.2
primary   DNS address 130.126.2.131
Script /etc/ppp/ip-up started (pid 9407)
Script /etc/ppp/ip-up finished (pid 9407), status = 0x0
^CTerminating on signal 2
Connect time 0.7 minutes.
Sent 0 bytes, received 0 bytes.
Script /etc/ppp/ip-down started (pid 9530)
MPPE disabled
sent [LCP TermReq id=0x2 "MPPE disabled"]
sent [LCP TermReq id=0x3 "MPPE disabled"]
Script /etc/ppp/ip-down finished (pid 9530), status = 0x0
rcvd [LCP TermAck id=0x2]
Connection terminated.
Waiting for 1 child processes...
  script pptp vpn3.near.uiuc.edu --nolaunchpppd , pid 9382
Child process pptp vpn3.near.uiuc.edu --nolaunchpppd  (pid 9382) terminated with signal 2

```

So clearly, my username/pw have been successful, the VPN has registered me.  So why does it still not work?

I go to open up a page in Chrome - It gives me am "unable to resolve DNS address." message.
I try to curl trying both interface ppp0 and ppp1 (the VPN connection) - It hangs forever.

Also, this may or may not be relevant: If I disable 'usepeerdns,' chrome works, but it appears that I'm still using my ppp0 connection, as evident from checking my IP address via an online website.  Also, disabling this makes curl using my PPPoE interface work instead of hang.

---

### Post by 98174 on 2011-07-22
Bump

---

