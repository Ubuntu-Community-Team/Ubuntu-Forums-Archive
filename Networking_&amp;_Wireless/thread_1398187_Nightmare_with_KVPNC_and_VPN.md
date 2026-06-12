---
title: "Nightmare with KVPNC and VPN"
date: 2010-02-04
forum: Networking &amp; Wireless
---

### Post by zozza on 2010-02-04
Hello,

I am having a very frustrating time trying to get my VPN to work.  I have read other threads about this but they never seen to get resolved.  

I am using KVPNC (recommended by the VPN owner) on Ubuntu 9.10 using my Universities direct Ethernet connection.   

I have downloaded all the .ovpn scripts to a directory.  I have downloaded KVPNC from the repository (apparently for 9.10 you do not download from the KVPNC website).  

I then use sudo kvpnc and select a server (since there are many based on the .ovpn files).  I click connect and the script works and tells me I have a connection.  See below for an example.  All appears to work.  

But when I actually load any Internet program e.g. Firefox it cannot find a website.  

This happens for all servers which have different locations around the world. 

When I disconnect KVPNC I still have no access.  I have to remove the Ethernet cable before it works again.  

Any ideas - thanks. 

debug: Connect try requested, profile: Stockholm, type: OpenVPN 
debug: openvpn: /usr/sbin/openvpn 
debug: Support for TUN/TAP found (compiled into kernel or kernel module  already loaded). 
debug: Default interface: "eth0". 
debug: IP address of default interface: "my IP address". 
info: Trying to connect to server "stockholm.perfect-privacy.com" with ... 
debug: Setting DNS_UPDATE "Yes". 
debug: Starting Openvpn management handler... 
debug: OpenvpnManagementHandler: Connecting to the OpenVPN manage port  (2222)... 
debug: [openvpn] Tue Feb 2 10:38:28 2010 OpenVPN 2.1_rc19  i486-pc-linux-gnu [SSL] [LZO2] [EPOLL] [PKCS11] built on Oct 13 2009 
debug: [openvpn] 
debug: OpenvpnManagementHandler: Connecting to the OpenVPN manage port  (2222)... host found 
debug: OpenvpnManagementHandler: Connected to the OpenVPN manage port  (2222). 
info: Send username... 
info: Send password... 
debug: [openvpn] Tue Feb 2 10:39:00 2010 WARNING: --ping should normally  be used with --ping-restart or --ping-exit 
debug: OpenvpnManagementHandler: got SUCCESS for user password message 
debug: [openvpn] Tue Feb 2 10:39:00 2010 NOTE: the current  --script-security setting may allow this configuration to call  user-defined scripts 
debug: [openvpn] Tue Feb 2 10:39:00 2010 WARNING: file  '*/root/*.pp-kvpnc/smclient.key' is group or others accessible 
debug: [openvpn] Tue Feb 2 10:39:00 2010 /usr/bin/openssl-vulnkey -q -b  4096 -m 
debug: [openvpn] 
debug: [openvpn] 
debug: [openvpn] WARN: could not open database for 4096 bits. Skipped 
debug: [openvpn] Tue Feb 2 10:39:00 2010 WARNING: file  '*/root/*.pp-kvpnc/smta.key' is group or others accessible 
debug: [openvpn] Tue Feb 2 10:39:00 2010 Control Channel Authentication:  using '*/root/*.pp-kvpnc/smta.key' as a OpenVPN static key file 
debug: [openvpn] Tue Feb 2 10:39:00 2010 LZO compression initialized 
debug: [openvpn] Tue Feb 2 10:39:00 2010 UDPv4 link local: [undef] 
debug: [openvpn] Tue Feb 2 10:39:00 2010 WARNING: this configuration may  cache passwords in memory -- use the auth-nocache option to prevent this 
debug: [openvpn] 
debug: [openvpn] Tue Feb 2 10:39:00 2010 UDPv4 link remote:  95.143.192.159:1149 
debug: [openvpn] 
debug: [openvpn] 
debug: [openvpn] Tue Feb 2 10:39:05 2010 [server] Peer Connection  Initiated with 95.143.192.159:1149 
debug: [openvpn] 
debug: [openvpn] Tue Feb 2 10:39:06 2010 TUN/TAP device tun0 opened 
debug: Tunnel device: tun0 
debug: [openvpn] Tue Feb 2 10:39:06 2010  */root/*.kde/share/apps/kvpnc/openvpn.Stockholm.up tun0 1500 1562  10.0.46.34 10.0.46.33 init 
debug: [openvpn] 
debug: Tunnel interface IP: 10.0.46.34 
debug: [openvpn] Tue Feb 2 10:39:06 2010 /sbin/ifconfig tun0 10.0.46.34  pointopoint 10.0.46.33 mtu 1500 
debug: [openvpn] 
debug: [openvpn] resolvconf: Error: /etc/resolv.conf must be a symlink 
debug: [openvpn] 
debug: [openvpn] Tue Feb 2 10:39:06 2010 Initialization Sequence Completed 
success: Connection established. 
success: Successful connected to server "stockholm.perfect-privacy.com"  at Tue Feb 2 10:39:06 2010, profile "Stockholm". [OpenVPN] 
debug: [openvpn] Using tun0 as tunnel device. 
debug: setFirewallAfterConnectScript:  */root/*.kde/share/apps/kvpnc/firewall_after_connect_script.Stockholm 
debug: "SetFirewallAfterConnectScript" started. 
debug: "SetFirewallAfterConnectScript" finished. 
debug: Use gateway address (stockholm.perfect-privacy.com) for  connection status check. 
debug: "ping_check.sh" started. 
debug: [openvpn] 

I realise there are errors e.g. the /etc/resolv.conf must be a symlink but have tried doing this and still have exactly the same issues. 

Thanks

---

### Post by zozza on 2010-02-06
BUMP!

Anybody?

---

### Post by ulriks on 2011-02-26
Quite late, but look here: 
[http://www.linuxquestions.org/questions/linux-software-2/configure-kvpnc-for-openvpn-408912/]("http://www.linuxquestions.org/questions/linux-software-2/configure-kvpnc-for-openvpn-408912/")

---

