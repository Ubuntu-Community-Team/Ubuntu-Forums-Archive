---
title: "black screen on vpn connection"
date: 2009-01-14
forum: Networking &amp; Wireless
---

### Post by blumm on 2009-01-14
Hi,
Please help, I have been trying to resolve this for weeks now!!!! :confused:

I am using kvpnc to connect to my company vpn. I can successfully connect but after I connect I can't browse internet and remote desktop shows a black screen.

Here is my kvpnc log

debug: Connect try requested, profile: ###COMPANY_NAME###VPN, type: PPTP
debug: Backup file of resolv.conf: /root/.kde/share/apps/kvpnc/resolv.conf.before.kvpnc_###COMPANY_NAME###VPN
debug: resolv.conf backup process started.
debug: pppd: /usr/sbin/pppd
debug: pppd version (major): "2"
debug: pppd version (minor): "4"
debug: pppd version (subminor): "4"
debug: pppd version is >= 2.4.2, good
debug: pppdHasRequireMppeSupport: true
debug: Testing mppe-required
debug: [test pppd raw]: /usr/sbin/pppd: unrecognized option 'mppe' pppd version 2.4.4 Usage: /usr/sbin/pppd [ options ], where options are: Communicate over the named device Set the baud rate to : Set the local and/or remote interface IP addresses. Either one may be omitted. asyncmap Set the desired async map to hex auth Require authentication from peer connect 
Invoke shell command 
to set up the serial line crtscts Use hardware RTS/CTS flow control defaultroute Add default route through interface file Take options from file modem Use modem control lines mru Set MRU value to for negotiation See pppd(8) for more options. 
debug: /usr/sbin/pppd has no MPPE support using "mppe-required".
debug: PppdMppeRequired: false
debug: /usr/sbin/pppd has MPPE support.
debug: Test support of replacedefaultroute pppd: failed
debug: pppd: (/usr/sbin/pppd) has MPPE support: require-mppe
debug: No default interface given, tried default interface, got success, using "eth0".
debug: Old default device: eth0, old default gw: 192.168.0.1
debug: pppd peer script: /etc/ppp/peers/kvpnc.###COMPANY_NAME###VPN 
debug: Enabling debug for pptpd.
debug: Using (NT) domain name "###COMPANY_NAME###".
debug: pppd version (major): "2"
debug: pppd version (minor): "4"
debug: pppd version (subminor): "4"
debug: pppd version is >= 2.4.2, good
debug: pppdHasRequireMppeSupport: true
debug: Testing mppe-required
debug: [test pppd raw]: /usr/sbin/pppd: unrecognized option 'mppe' pppd version 2.4.4 Usage: /usr/sbin/pppd [ options ], where options are: Communicate over the named device Set the baud rate to : Set the local and/or remote interface IP addresses. Either one may be omitted. asyncmap Set the desired async map to hex auth Require authentication from peer connect 
Invoke shell command 
to set up the serial line crtscts Use hardware RTS/CTS flow control defaultroute Add default route through interface file Take options from file modem Use modem control lines mru Set MRU value to for negotiation See pppd(8) for more options. 
debug: /usr/sbin/pppd has no MPPE support using "mppe-required".
debug: PppdMppeRequired: false
debug: /usr/sbin/pppd has MPPE support.
debug: Test support of replacedefaultroute pppd: failed
debug: "PppdBackupDefaultRouteScript" (/root/.kde/share/apps/kvpnc/pppd.###COMPANY_NAME###VPN.backup_default_route.sh) started.
debug: "PppdBackupDefaultRouteScript" (/root/.kde/share/apps/kvpnc/pppd.###COMPANY_NAME###VPN.up) finished.
debug: Authentication method: mschap-v2
debug: chmod of /etc/ppp/pap-secrets (go-rwx) started.
debug: pppd secrets file: /etc/ppp/chap-secrets
debug: Username: ###USER_NAME###
debug: chmod of /etc/ppp/chap-secrets (go-rwx) started.
debug: pppd: /usr/sbin/pppd 
debug: Trying to connect to server "###SERVER###.###COMPANY_NAME###.com" with user "###USER_NAME###"... 
debug: Setting DNS_UPDATE "Yes".
debug: "pppd" started.
debug: [pppd] using channel 28
debug: [pppd] Using interface ppp0
debug: [pppd] Connect: ppp0 /dev/pts/2
debug: [pppd] sent [LCP ConfReq id=0x1 ]
debug: [pppd] rcvd [LCP ConfAck id=0x1 ]
debug: [pppd] rcvd [LCP ConfReq id=0x1 ]
debug: Tunnel IP address: id=0x1 
debug: [pppd] sent [LCP ConfRej id=0x1 ]
debug: [pppd] rcvd [LCP ConfReq id=0x2 ]
debug: Tunnel IP address: id=0x2 
debug: [pppd] sent [LCP ConfNak id=0x2 ]
debug: [pppd] rcvd [LCP ConfReq id=0x3 ]
debug: Tunnel IP address: id=0x3 
debug: [pppd] sent [LCP ConfAck id=0x3 ]
debug: Tunnel IP address: id=0x3 
debug: [pppd] rcvd [CHAP Challenge id=0x0 , name = "H60W3101HA"]
debug: [pppd] sent [CHAP Response id=0x0 , name = "###COMPANY_NAME###\\###USER_NAME###"]
debug: [pppd] rcvd [CHAP Success id=0x0 "S=B0BD46730DBD153C6C8361E206AA7E2912163F3D"]
debug: [pppd] CHAP authentication succeeded
debug: CHAP authentication succeeded. 
debug: [pppd] sent [CCP ConfReq id=0x1 ]
debug: [pppd] rcvd [CCP ConfReq id=0x5 ]
debug: [pppd] sent [CCP ConfNak id=0x5 ]
debug: [pppd] rcvd [IPCP ConfReq id=0x6 ]
debug: [pppd] sent [IPCP TermAck id=0x6]
debug: [pppd] rcvd [CCP ConfNak id=0x1 ]
debug: [pppd] sent [CCP ConfReq id=0x2 ]
debug: [pppd] rcvd [CCP ConfReq id=0x7 ]
debug: [pppd] sent [CCP ConfAck id=0x7 ]
debug: [pppd] rcvd [CCP ConfAck id=0x2 ]
debug: [pppd] MPPE 128-bit stateless compression enabled
debug: MPPE 128-bit stateless compression enabled. 
debug: [pppd] sent [IPCP ConfReq id=0x1 ]
debug: [pppd] rcvd [IPCP ConfRej id=0x1 ]
debug: [pppd] sent [IPCP ConfReq id=0x2 ]
debug: [pppd] rcvd [IPCP ConfNak id=0x2 ]
debug: [pppd] sent [IPCP ConfReq id=0x3 ]
debug: [pppd] rcvd [IPCP ConfAck id=0x3 ]
debug: [pppd] rcvd [IPCP ConfReq id=0x8 ]
debug: [pppd] sent [IPCP ConfAck id=0x8 ]
debug: [pppd] not replacing existing default route via 192.168.0.1
debug: [pppd] Cannot determine ethernet address for proxy ARP
debug: [pppd] local IP address 10.10.0.35
debug: Tunnel IP address: 10.10.0.35 
debug: [pppd] remote IP address 10.10.10.220
success: Successful connected to server "arrow.###COMPANY_NAME###.com" user: "###USER_NAME###" at Wed Jan 14 22:06:23 2009 [PPTP]
success: Connection established.
debug: Tunnel interface IP address: 10.10.0.35
debug: replacing default route: yes
debug: Setting extra route: arrow.###COMPANY_NAME###.com over eth0 gw 192.168.0.1
debug: default route count : 1
debug: "PppdUpScript" (/root/.kde/share/apps/kvpnc/pppd.###COMPANY_NAME###VPN.up) started.
debug: "PppdUpScript" (/root/.kde/share/apps/kvpnc/pppd.###COMPANY_NAME###VPN.up) finished.
debug: Local IP address: 10.10.0.35, remote IP address: , device: , speed: 
debug: setFirewallAfterConnectScript: /root/.kde/share/apps/kvpnc/firewall_after_connect_script.###COMPANY_NAME###VPN 
debug: Insert rule for fixing path MTU discovery problem
debug: "SetFirewallAfterConnectScript" started.
debug: Ping to arrow.###COMPANY_NAME###.com within 4 checks every 1s was ok.
debug: "SetFirewallAfterConnectScript" finished.
debug: Use gateway address (arrow.###COMPANY_NAME###.com) for connection status check.
debug: "ping_check.sh" started.
debug: [pppd] Script /etc/ppp/ip-up started (pid 17610)
debug: [pppd] Script /etc/ppp/ip-up finished (pid 17610), status = 0x0
debug: Ping to arrow.###COMPANY_NAME###.com within 4 checks every 1s was ok.
debug: Ping to arrow.###COMPANY_NAME###.com within 4 checks every 1s was ok.
debug: Ping to arrow.###COMPANY_NAME###.com within 4 checks every 1s was ok.

Also I added some more info below

**[COLOR="Red"] ifconfig[/COLOR]**
eth0      Link encap:Ethernet  HWaddr 00:0f:ea:81:b6:c8  
          inet addr:192.168.0.20  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::20f:eaff:fe81:b6c8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:15290 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10869 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:18112362 (18.1 MB)  TX bytes:1550983 (1.5 MB)
          Interrupt:19 Base address:0xc800

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:20838 errors:0 dropped:0 overruns:0 frame:0
          TX packets:20838 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:3411581 (3.4 MB)  TX bytes:3411581 (3.4 MB)

ppp0      Link encap:Point-to-Point Protocol  
          inet addr:10.10.0.35  P-t-P:10.10.10.220  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1196  Metric:1
          RX packets:290 errors:0 dropped:0 overruns:0 frame:0
          TX packets:308 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3
          RX bytes:26297 (26.2 KB)  TX bytes:21944 (21.9 KB)

[COLOR="Red"]** route -n**[/COLOR]
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
10.10.10.220    0.0.0.0         255.255.255.255 UH    0      0        0 ppp0
66.219.47.7     192.168.0.1     255.255.255.255 UGH   0      0        0 eth0
192.168.0.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
0.0.0.0         0.0.0.0         0.0.0.0         U     0      0        0 ppp0
 [COLOR="Red"]**nslookup ###SERVER_NAME###.###COMPANY_NAME###.com**[/COLOR]
Server:        10.10.0.13
Address:    10.10.0.13#53

Name:    ##SERVER###.###COMPANY_NAME###.com
Address: 10.10.10.35


[COLOR="Red"]** sudo cat /etc/resolv.conf**[/COLOR]
# generated by kvpnc. Do not edit it.
nameserver 10.10.0.13
search hq.###COMPANY_NAME###.com yellow.###COMPANY_NAME###.com

**[COLOR="Red"] ping [www.ibm.com](www.ibm.com)[/COLOR]**
PING [www.ibm.com.cs186.net](www.ibm.com.cs186.net) (129.42.60.216) 56(84) bytes of data.
^C
--- [www.ibm.com.cs186.net](www.ibm.com.cs186.net) ping statistics ---
5 packets transmitted, 0 received, 100% packet loss, time 4004ms



[COLOR="Red"] uname -a[/COLOR]
Linux myserver 2.6.27-7-generic #1 SMP Tue Nov 4 19:33:20 UTC 2008 i686 GNU/Linux

---

### Post by ballin on 2009-02-14
I had this problem and have spent all morning trying to fix it - in my case I could RDP to a local Windows machine, but when connected through VPN I just received a black screen.

In my case this was caused by the MTU value of my ethernet connection.

If you sudo ifconfig you will see a MTU value for [eth0] or whichever.
Mine was set to ~500...when I set this to 1500 it worked.

Other people seem to be the other way around, ie. set to 1500 and they need to set it to 1400 or something - try experimenting.

To set the MTU : sudo ifconfig eth0 mtu 1500


Hope this is useful for some people!

---

### Post by blumm on 2009-02-14
Thanks for your reply. I will try this.

---

