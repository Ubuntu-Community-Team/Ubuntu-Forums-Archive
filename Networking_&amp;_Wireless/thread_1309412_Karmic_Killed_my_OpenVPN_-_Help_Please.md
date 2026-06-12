---
title: "Karmic Killed my OpenVPN - Help Please"
date: 2009-11-01
forum: Networking &amp; Wireless
---

### Post by bigben1313 on 2009-11-01
I just changed from Linux Mint 7 to Ubuntu 9.10.  I use Witopia as an OpenVPN connection, and it worked great using network-manager-openvpn on Mint.  I have tried using network-manager-openvpn, gopenvpn, and the openvpn command line.  

I won't cover network-manager-openvpn, since that seems to be a bigger problem and I just want my VPN to work.  When using gopenvpn or the command line, I can connect to the server but it kills my internet connection.  I can surf the web before connection, but after connection firefox times out.

My config file
```

client
dev tun
proto udp
remote vpn.xxxx.xxxxxx.net   1194
resolv-retry infinite
nobind
persist-key
persist-tun
ns-cert-type server
cipher bf-cbc
comp-lzo
verb 3
mute 20
ca /home/ben/Documents/Witopia/ca.crt
key /home/ben/Documents/Witopia/Ben.key
cert /home/ben/Documents/Witopia/Ben.crt
```

My terminal output when using openVPN

```
ben@BeePC:~$ sudo openvpn --config /home/ben/Documents/Witopia/personalVPN-128-US.ovpn
Sun Nov  1 22:03:11 2009 OpenVPN 2.1_rc19 i486-pc-linux-gnu [SSL] [LZO2] [EPOLL] [PKCS11] built on Oct 13 2009
Sun Nov  1 22:03:11 2009 NOTE: OpenVPN 2.1 requires '--script-security 2' or higher to call user-defined scripts or executables
Sun Nov  1 22:03:11 2009 /usr/bin/openssl-vulnkey -q -b 1024 -m <modulus omitted>
Sun Nov  1 22:03:12 2009 LZO compression initialized
Sun Nov  1 22:03:12 2009 Control Channel MTU parms [ L:1542 D:138 EF:38 EB:0 ET:0 EL:0 ]
Sun Nov  1 22:03:22 2009 RESOLVE: NOTE: vpn.us.witopia.net resolves to 16 addresses, choosing one by random
Sun Nov  1 22:03:22 2009 Data Channel MTU parms [ L:1542 D:1450 EF:42 EB:135 ET:0 EL:0 AF:3/1 ]
Sun Nov  1 22:03:22 2009 Local Options hash (VER=V4): '41690919'
Sun Nov  1 22:03:22 2009 Expected Remote Options hash (VER=V4): '530fdded'
Sun Nov  1 22:03:22 2009 Socket Buffers: R=[114688->131072] S=[114688->131072]
Sun Nov  1 22:03:22 2009 UDPv4 link local: [undef]
Sun Nov  1 22:03:22 2009 UDPv4 link remote: 207.7.138.116:1194
Sun Nov  1 22:03:23 2009 TLS: Initial packet from 207.7.138.116:1194, sid=49bdff58 24d77c64
Sun Nov  1 22:03:25 2009 VERIFY OK: depth=1, /C=US/ST=Virginia/L=Reston/O=Full_Mesh_Networks__Inc./OU=FMN_Engineering___Operations/CN=Full_Mesh_Networks_Certificate_Authority/emailAddress=support@fullmesh.net
Sun Nov  1 22:03:25 2009 VERIFY OK: nsCertType=SERVER
Sun Nov  1 22:03:25 2009 VERIFY OK: depth=0, /C=US/ST=Virginia/O=Full_Mesh_Networks__Inc./OU=WiTopia_Engineering___Operations/CN=vpn/emailAddress=support@witopia.net
Sun Nov  1 22:03:32 2009 Data Channel Encrypt: Cipher 'BF-CBC' initialized with 128 bit key
Sun Nov  1 22:03:32 2009 Data Channel Encrypt: Using 160 bit message hash 'SHA1' for HMAC authentication
Sun Nov  1 22:03:32 2009 Data Channel Decrypt: Cipher 'BF-CBC' initialized with 128 bit key
Sun Nov  1 22:03:32 2009 Data Channel Decrypt: Using 160 bit message hash 'SHA1' for HMAC authentication
Sun Nov  1 22:03:32 2009 Control Channel: TLSv1, cipher TLSv1/SSLv3 DHE-RSA-AES256-SHA, 1024 bit RSA
Sun Nov  1 22:03:32 2009 [vpn] Peer Connection Initiated with 207.7.138.116:1194
Sun Nov  1 22:03:33 2009 SENT CONTROL [vpn]: 'PUSH_REQUEST' (status=1)
Sun Nov  1 22:03:33 2009 PUSH: Received control message: 'PUSH_REPLY,redirect-gateway def1,dhcp-option DNS 10.118.0.1,route 10.178.0.1,topology net30,ping 10,ping-restart 60,ifconfig 10.178.6.230 10.178.6.229'
Sun Nov  1 22:03:33 2009 OPTIONS IMPORT: timers and/or timeouts modified
Sun Nov  1 22:03:33 2009 OPTIONS IMPORT: --ifconfig/up options modified
Sun Nov  1 22:03:33 2009 OPTIONS IMPORT: route options modified
Sun Nov  1 22:03:33 2009 OPTIONS IMPORT: --ip-win32 and/or --dhcp-option options modified
Sun Nov  1 22:03:33 2009 ROUTE default_gateway=192.168.1.1
Sun Nov  1 22:03:33 2009 TUN/TAP device tun0 opened
Sun Nov  1 22:03:33 2009 TUN/TAP TX queue length set to 100
Sun Nov  1 22:03:33 2009 /sbin/ifconfig tun0 10.178.6.230 pointopoint 10.178.6.229 mtu 1500
Sun Nov  1 22:03:33 2009 /sbin/route add -net 207.7.138.116 netmask 255.255.255.255 gw 192.168.1.1
Sun Nov  1 22:03:33 2009 /sbin/route add -net 0.0.0.0 netmask 128.0.0.0 gw 10.178.6.229
Sun Nov  1 22:03:33 2009 /sbin/route add -net 128.0.0.0 netmask 128.0.0.0 gw 10.178.6.229
Sun Nov  1 22:03:33 2009 /sbin/route add -net 10.178.0.1 netmask 255.255.255.255 gw 10.178.6.229
Sun Nov  1 22:03:33 2009 Initialization Sequence Completed

```




My ifconfig when connected to openVPN

```
eth0      Link encap:Ethernet  HWaddr 00:26:18:77:b0:69  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:1
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:28 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:622 errors:0 dropped:0 overruns:0 frame:0
          TX packets:622 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:55842 (55.8 KB)  TX bytes:55842 (55.8 KB)

ra0       Link encap:Ethernet  HWaddr 00:25:d3:3c:00:ef  
          inet addr:192.168.1.117  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::225:d3ff:fe3c:ef/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:296669 errors:0 dropped:0 overruns:0 frame:0
          TX packets:26861 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:56732749 (56.7 MB)  TX bytes:5184784 (5.1 MB)
          Interrupt:19 

tun0      Link encap:UNSPEC  HWaddr 00-00-00-00-00-00-00-00-00-00-00-00-00-00-00-00  
          inet addr:10.178.6.230  P-t-P:10.178.6.229  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:21 errors:0 dropped:0 overruns:0 frame:0
          TX packets:46 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:1248 (1.2 KB)  TX bytes:22687 (22.6 KB)

```

So, it seems like it is connecting but then I can't use the connection.  I don't know why the change from Mint 7 to Karmic would make this problem.  Any help would be greatly appreciated, since a dead VPN makes this new install much less useful.

---

### Post by maynardp on 2009-11-07
the Network Manager is likely your problem.
It controls your DNS servers in the background and the entries that are suppose to get added by your VPN client are being ignored.

the line in your log output 

```
PUSH: Received control message: 'PUSH_REPLY,redirect-gateway def1,dhcp-option DNS 10.118.0.1,route 10.178.0.1,topology net30,ping 10,ping-restart 60,ifconfig 10.178.6.230 10.178.6.229'
```

shows a DNS server of 10.118.0.1 (it may be different next time so check again)

Check your /etc/resolv.conf file
```
cat /etc/resolv.conf
```
it should contain a "nameserver" entry matching this entry, preferably at the top of the list.

If not, that will likely be the source of your trouble.

I have a solution (albeit a long one) for getting Network-Manager OpenVPN working.

------------------------ 
Ubuntu 9.10 (as of Nov 7, 2009) has a couple bugs that will prevent it from working out of the box with Witopia.

1) see this bug [https://bugs.launchpad.net/ubuntu/+source/network-manager-openvpn/+bug/453807](https://bugs.launchpad.net/ubuntu/+source/network-manager-openvpn/+bug/453807)
[LIST]
[*]it includes a patch for /etc/dbus-1/system.d/nm-openvpn-service.conf
[*]but doesn't include instructions for creating or applying it
[/LIST]

```
cd /etc/dbus-1/system.d
sudo vi openvpn.patch

```
[LIST]
[*]this patch file needs to include tabs for 'patch' to work
[/LIST]            
```
--- nm-openvpn-service.conf.fixed 2009-11-05 16:07:53.764591878 +0200
+++ nm-openvpn-service.conf 2009-11-05 12:24:59.672779358 +0200
@@ -6,6 +6,10 @@
 		<allow own="org.freedesktop.NetworkManager.openvpn"/>
 		<allow send_destination="org.freedesktop.NetworkManager.openvpn"/>
 	</policy>
+	<policy user="at_console">
+		<allow own="org.freedesktop.NetworkManager.openvpn"/>
+		<allow send_destination="org.freedesktop.NetworkManager.openvpn"/>
+	</policy>
 	<policy context="default">
 		<deny own="org.freedesktop.NetworkManager.openvpn"/>
 		<deny send_destination="org.freedesktop.NetworkManager.openvpn"/>
```

```
sudo patch -b nm-openvpn-service.conf <openvpn.patch 

```
[LIST]reboot your computer
[/LIST]

2) the other bug is the fact that Network Manager OpenVPN won't work with a Private key that doesn't have a passphrase.  It use to, but it won't now.
[LIST]
[*]add a passphrase to a COPY of your private key
[/LIST]
```
cd /usr/local/openvpn/conf

```
[LIST]
[*]if you followed the Witopia instructions, otherwise change to the directory where your keys are stored
[/LIST]
```
cp <your_name>.key oldkey.key
mv <your_name>.key <your_name>.key.save
openssl rsa -des3 -in oldkey.key -out <your_name>.key

```
[LIST]
[*]you will be prompted for a passphrase, make it something you will remember
[/LIST]

you now have your original key with no passphrase <your_name>.key.save
and your new key with a passphrase <your_name>.key

So now you can import PersonalVPN.conf (or some other ".conf") file into Network Manager OpenVPN


[LIST]
[*]click on the Network icon in the info tray
   they've changed it again, it now looks like 2 cables plugged together
[*]select "VPN Connections >" then "Configure VPN..."
   the "Network Connections" dialog box will open with the VPN tab selected
[*]click the "Import" button
   the "Select file to import" dialog box will open
[*]navigate to the /usr/local/openvpn/conf directory (or where ever you stored your keys and conf files) and select one of the ".conf" files
[*]once selected, click "Open"
   the "Editing <name>.conf" dialog box will open
[*]The top field is the Name that will show up in Network Manager OpenVPN
   it doesn't seem to like names with spaces
   if this field has a long name with spaces, remove the spaces, or rename it
[*]If not already selected, select the VPN tab
[*]enter the passphrase you added to your key file in the "Private Key Password:" field
[*]decide whether you want this VPN connection to be established every time you connect to the internet
   if yes, "Connect Automatically" should be checked
   if no, then leave it unchecked
[*]decide whether this VPN should be available to ALL users of the computer
   if yes, "Available to all users" should be checked
      (you will be prompted for your login password if you check this)
   if no, the default, leave it unchecked
[*]Click the Apply button
   you will be returned to the "Network Connections" dialog
[/LIST]
You can now test your VPN

[LIST]
[*]click on the Network icon in the info tray
[*]select "VPN Connections >" then the name of your VPN connection
	default is PersonalVPN
	a little padlock will flash on the Network icon in the info tray
	once the connection is complete, the padlock will remain solid
[/LIST]

You can test your connection by checking your network interfaces 
```
ifconfig -a

```

[LIST]
[*]you should see a tun0 interface listed and it should be UP
[/LIST]

check your IP address at [http://whatismyipaddress.com/](http://whatismyipaddress.com/)

---

### Post by japglish on 2009-11-07
Can't thank you enough for this - it was really bugging me.  Did exactly what you suggested (except substituting vi for gedit - am too noob to be bothered to work out how vi functions!!).

Worked perfectly!!!  A million thanks.

---

### Post by hcgoh on 2009-11-09
Thank you for the workaround solution.... it works for me to...):P

---

### Post by bigben1313 on 2009-11-23
maynardp, thanks for the detailed answer.  It looks like it has helped some other people, but unfortunately I am still having problems.

I am using OpenVPN straight from the terminal so that I can eliminate network-manager-openvpn from the problem.  I have no problems connecting to my VPN, but once it is connected I can't reach any websites.  If I try to ping [www.google.com](www.google.com) I get an "unknown host" error.  I am not an experienced networking person, but that error leads me to believe that the DNS server is not resolving the address.  To fix this, I appended the OpenDNS addresses to my resolv.cof.  When my VPN is connected, it outputs the two OpenDNS addresses that were appended but not the DNS that OpenVPN should be adding to the list.

I can ping the VPN server, and the connection works on my XP machine.  If resolv.conf contains the OpenDNS servers, how could "ping www.google.com" return an "unknown host" error?

I am very confused here.  Any help would be greatly appreciated.

---

### Post by Baboontu on 2009-11-24
Hi
when I tried to apply the patch I got :
Hunk #1 FAILED at 6.
1 out of 1 hunk FAILED -- saving rejects to file nm-openvpn-service.conf.rej
What's wrong?
Thanks

---

### Post by sirajperson on 2010-04-21
I am having the same trouble. I tried with both the network manager and just using the command line. I can connect to the VPN server, but that as far as my connection goes. My VPN clients cannot reach the WAN interface of the VPN server. Checking /etc/resolv.conf shows that the name servers are still the same from the LAN subnet that the VPN client is connecting from. After I edit the resolve.conf file manually I able to resolve a WAN IP, but cannot connect to it. I have been troubled with this for a while, and have been having a hard time figuring this one out.

---

