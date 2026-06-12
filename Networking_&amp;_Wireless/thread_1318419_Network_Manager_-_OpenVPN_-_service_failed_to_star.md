---
title: "Network Manager - OpenVPN - service failed to start"
date: 2009-11-07
forum: Networking &amp; Wireless
---

### Post by PartisanEntity on 2009-11-07
So this is quite frustrating:

**Background:**

In Ubuntu 9.04 I had a VPN connection configured in order to use Witopia. It worked.

I upgraded to Ubuntu 9.10 and now it doesn't work.

**Problem:**

In Network Manager, under VPN Connections, when I select my "openvpn" connection I get this error message:

*The vpn connection 'openvpn' failed because the VPN service failed to start.*

**More Info:**

Here is what it says in Sys Log:

(notice what I have highlighted in red)

> Nov  7 21:05:21 ubuntu-laptop NetworkManager: <info>  Starting VPN service 'org.freedesktop.NetworkManager.openvpn'...
Nov  7 21:05:21 ubuntu-laptop NetworkManager: <info>  VPN service 'org.freedesktop.NetworkManager.openvpn' started (org.freedesktop.NetworkManager.openvpn), PID 1974
Nov  7 21:05:22 ubuntu-laptop NetworkManager: <info>  VPN service 'org.freedesktop.NetworkManager.openvpn' just appeared, activating connections
Nov  7 21:05:22 ubuntu-laptop NetworkManager: <info>  VPN plugin state changed: 1
Nov  7 21:05:22 ubuntu-laptop NetworkManager: <info>  VPN plugin state changed: 3
Nov  7 21:05:22 ubuntu-laptop NetworkManager: <info>  VPN connection 'openvpn' (Connect) reply received.
Nov  7 21:05:22 ubuntu-laptop NetworkManager: [COLOR="Red"]<WARN>  nm_vpn_connection_connect_cb(): VPN connection 'openvpn' failed to connect: 'No VPN secrets!'.[/COLOR]
Nov  7 21:05:22 ubuntu-laptop NetworkManager: [COLOR="red"]<WARN>  connection_state_changed(): Could not process the request because no VPN connection was active.[/COLOR]
Nov  7 21:05:22 ubuntu-laptop NetworkManager: <info>  Policy set 'Auto eth0' (eth0) as default for routing and DNS.
Nov  7 21:05:35 ubuntu-laptop NetworkManager: <debug> [1257624335.001600] ensure_killed(): waiting for vpn service pid 1974 to exit
Nov  7 21:05:35 ubuntu-laptop NetworkManager: <debug> [1257624335.001766] ensure_killed(): vpn service pid 1974 cleaned up
Nov  7 21:05:40 ubuntu-laptop NetworkManager: <info>  Starting VPN service 'org.freedesktop.NetworkManager.openvpn'...
Nov  7 21:05:40 ubuntu-laptop NetworkManager: <info>  VPN service 'org.freedesktop.NetworkManager.openvpn' started (org.freedesktop.NetworkManager.openvpn), PID 1978
Nov  7 21:05:40 ubuntu-laptop NetworkManager: <info>  VPN service 'org.freedesktop.NetworkManager.openvpn' just appeared, activating connections
Nov  7 21:05:40 ubuntu-laptop NetworkManager: <info>  VPN plugin state changed: 3
Nov  7 21:05:40 ubuntu-laptop NetworkManager: <info>  VPN connection 'openvpn' (Connect) reply received.
Nov  7 21:05:40 ubuntu-laptop NetworkManager: <WARN>  nm_vpn_connection_connect_cb(): VPN connection 'openvpn' failed to connect: 'No VPN secrets!'.
Nov  7 21:05:40 ubuntu-laptop NetworkManager: <WARN>  connection_state_changed(): Could not process the request because no VPN connection was active.
Nov  7 21:05:40 ubuntu-laptop NetworkManager: <info>  Policy set 'Auto eth0' (eth0) as default for routing and DNS.
Nov  7 21:05:53 ubuntu-laptop NetworkManager: <debug> [1257624353.002543] ensure_killed(): waiting for vpn service pid 1978 to exit
Nov  7 21:05:53 ubuntu-laptop NetworkManager: <debug> [1257624353.002711] ensure_killed(): vpn service pid 1978 cleaned up


**What I have tried so far:**

Reading through the forum, and searching Google, it seems many people are having this problem. It also doesn't appear to be a new problem.

I tried to remove openvpn and network-manage-openvpn packages and to add them again and to create new connection profiles.

Unfortunately without success.

Any ideas?

---

### Post by adxgrave on 2009-11-08
I have the same problem. Not that it's not working at all but I need to try several time. Sometime the connection drop randomly. The same setup, works  perfectly fine in jaunty. Advice please.

---

### Post by ty1033 on 2009-11-09
Dear all,

After I searched a lot of posts over the Internet, only one can answered the problem about "No VPN secrets" on Ubuntu 9.10

Actually, don't check "Available to all users." on Network Manager. Enable MPPE. Leave the rest as default.

[COLOR=Red]Problem : VPN connection 'openvpn' failed to connect: 'No VPN secrets!'.[/COLOR]

Reference : [https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/284212/comments/69](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/284212/comments/69)

Enjoy Ubuntu 9.10 !!! It is great ! Now I am an Ubuntu-er

---

### Post by iluvgimp on 2009-11-10
Having exact same problems, also with the sporadic timing and disconnects. I have not ever enabled the "All accounts" option and I'm unsure what MPPE is. Someone care to define?

---

### Post by PartisanEntity on 2009-11-11
> **iluvgimp said:**
> Having exact same problems, also with the sporadic timing and disconnects. I have not ever enabled the "All accounts" option and I'm unsure what MPPE is. Someone care to define?

MPPE - Microsoft Point to Point Encryption

I *think* it applies only to PPTP based VPN connections.

In my case I am using SSL.

---

### Post by slcpunk on 2009-11-17
I am having the same issues.  If I am persistent, and keep trying it will connect.  

I see the "no secrets" entry in syslog, as well as the 

 Script '/etc/NetworkManager/dispatcher.d/01ifupdown' exited with error status 1.

error in syslog.  This is mentioned in some older bugs...but nothing that current.

Just for reference: An alternative is to use gopenvpn - I like its setup much better, you just use regular openvpn config files instead of n-m-openvpn's gui.  However, contrary to the gopenvpn documentation, I get prompted for the admin password to connect, and I couldn't figure that out either....that's why I tried to go back to network manager. ( and also just to have one less icon in the notification area )

---

### Post by Sven6210 on 2009-11-21
I am using WiTopia on my EeePC 900a with Ubuntu 9.10. Since I deactivated the option 'Available to all users' as recommended it works very well for me.

What I needed to do to get WiTopia to work:
1. installing OpenVPN with Synaptics (should already be installed)
2. installing 'network-manager-openvpn' with Synapics
3. copying the necessary profile and key files from the Mac or Windows version to any directory in Ubuntu
4. Import the .ovpn files with the network managers (Network Connections) make sure that 'Connect automatically' and 'Available to all users' are not checked (are NOT activated)

That did it for me, I can use WiTopia with Ubuntu 9.10 and it is very reliable

---

### Post by kjurkic on 2009-11-30
Also not getting anywhere with this problem

Have all cert & key files, proven working on Windows & Mac clients

Network manager DOES NOT CONNECT. Cannot find anywhere to set "Share with other users"

gopenvpn only succeeds in giving libgtk error when using *.deb. 
The repos return "not found" when using apt-get update or synaptic..haven't tried source compile yet, but my experience with various *buntus is that if the deb doesn't work, neither will compiling from source; just another dependency clusterfk



....so none of the suggestions here has been successful.:roll:

---

### Post by addeboy on 2009-12-01
It seems there isn't a fix to get it working under Network Manager. I use it now from console with a .conf file:
```
sudo openvpn config.conf
```

---

### Post by Sven6210 on 2009-12-01
I am sorry to hear that you have trouble using OpenVPN with the Gnome Network Manager.

I will describe you how I use it.

**Importing a VPN connection**

[LIST=1]
[*]click with the right mouse button on the symbol of the network manager and choose 'Edit Connections...'
[*]Go to the tab 'VPN' by clicking on it
[*]Press the button 'Import'
[*]Choose the folder where you have the *.ovpn files you use in Windows or with Mac and press 'Open'
[*]In the following window choose the right missing 'User Certificate', 'CA Certificate' and 'Private Key'. The 'User Certificate' is a *.crt file, the 'CA Certificate' is a *.crt file (in my case 'ca.crt') and the 'Private Key' is a *.key file. These files must be provided to you by the VPN service provider
[*]In this window also make sure that you deactivate 'Connect automatically' in the top section and 'Available to all users' in the bottom section
[*]When you have finished with these settings press 'Apply'
[*]Then you can also close the 'Network Connections' window
[/LIST]
**Opening a VPN connection**

[LIST=1]
[*]Now click with the left mouse button on the symbol of the network manager
[*]Go to 'VPN Connections'
[*]Choose the new connection you just created
[*]You can see that everything worked if you have a small lock in the network manager symbol, it should work well. If you get an error message that OpenVPN could not start just repeat the steps 1-3. I seldom get an error message, normally it works well. And if I get an error message it works at the second attempt
[/LIST]
**Closing a VPN connection**

[LIST=1]
[*]Click with the left mouse button on the symbol of the network manager
[*]Go to 'VPN Connections'
[*]Choose 'Disconnect VPN...'
[/LIST]
 I hope this helps you

---

### Post by PartisanEntity on 2009-12-02
I too have not been able to solve this issue yet, and frankly for the past days I have been too busy to actually look into the matter seriously.

However I assume that those of us who are having this problem are all upgraders and not fresh installers, correct?

---

### Post by etdube on 2009-12-03
> **PartisanEntity said:**
> However I assume that those of us who are having this problem are all upgraders and not fresh installers, correct?

I have a fresh install of Karmic (x86-64) and I experience the same problem:

Dec  3 09:11:50 edube-laptop NetworkManager: <info>  VPN connection 'workvpn' (Connect) reply received.
Dec  3 09:11:50 edube-laptop NetworkManager: <WARN>  nm_vpn_connection_connect_cb(): VPN connection 'workvpn' failed to connect: 'No VPN secrets!'.
Dec  3 09:11:50 edube-laptop NetworkManager: <WARN>  connection_state_changed(): Could not process the request because no VPN connection was active.

After a few tries it is usually able to connect, but sometimes the VPN connection is dropped unexpectedly after a while.

---

### Post by Sven6210 on 2009-12-06
Try to stop all communication when starting OpenVPN. I have some correlation between loading data (websites or file downloads) and trying to establish a VPN connection at the same time. When no data is down- or uploaded then I can easily open OpenVPN.

---

### Post by Sven6210 on 2009-12-25
Dear all, since yeterday I can not open VPN connection with the 'NetworkManager Applet' any more. I suppose the reason is that I installed some new packages. It has been working well before but does not work any more. And I did some small changes to my system due to the new UMTS Stick I got for Christmas.

I will investigate further and let you know if I can identify the reason.

If you have any news it would be great of you could share it with us here.

---

### Post by PartisanEntity on 2009-12-25
Some members have reported that installing the package: *network-manager-pptp* will solve the problem.

If it works for you, please post back and let us know.

---

### Post by PartisanEntity on 2009-12-25
I posted about this issue on my blog, and some users have provided solutions in the comments section, I updated the post to include those solutions, hope they help others, [here's the link]("http://www.cognitivecombine.com/2009/11/ubuntu-9-10-network-manager-openvpn-vpn-service-failed-to-start/").

---

### Post by Sven6210 on 2009-12-26
Sorry, my last post was a wrong alarm. Actually it was my fault that OpenVPN did not work any more on my EeePC 900a with 9.10 (KK). I changed the name of the directory where the certificates and key are saved an therefore the 'Network-Manager Applet' did not find the necessary files any more.

Unfortunately the error message was just 'unable to open OpenVPN' and therefore it took me some time to find out about the missing certificates. I updated the links to the certificates and key files and everything works again without installing 'network-manager pptp' or changing the '[FONT=Verdana]/etc/network/interfaces' file.

Maybe you first check the settings in 'Network-Manager Applet' as the error message might be due to wrong configuration of OpenVPN. For more details please see my earlier post under this threat.
[/FONT]

---

### Post by chrisxtj on 2010-01-06
Just the same problem, and so far none of the solutions mentioned above works for me.

---

### Post by keith.burgoyne on 2010-01-12
I am also having the same issue. None of the above solutions seem to help.

---

### Post by karmakowski on 2010-01-17
UPDATE: ok, setting bogus credentials solved it for me
[QUOTE=Tom]To those who have problems with private keys without password :
 You can create  new private key WITH password by running :
 openssl rsa -in OLD_PRIVATE_KEY.key  -des3 -out  NEW_PRIVATE_KEY.key
 You will ba asked for password ,  so  enter  something and remember( or write it down) .
 Don't forget  to do:  chmod og-rwx NEW_PRIVATE_KEY.key or you will get warnings from openvpn  .
 In Openvpn config provide  NEW_PRIVATE_KEY.key and password you entered .
[/QUOTE]
[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/284212/comments/74](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/284212/comments/74)





Has this issue been resolved? I have the same problem with openvpn and network-manager. 

Connecting to openvpn server from command line works fine:
```
$ sudo openvpn VPN.conf
Sun Jan 17 12:05:28 2010 OpenVPN 2.1_rc19 i486-pc-linux-gnu [SSL] [LZO2] [EPOLL] [PKCS11] built on Oct 13 2009
Sun Jan 17 12:05:28 2010 IMPORTANT: OpenVPN's default port number is now 1194, based on an official port number assignment by IANA.  OpenVPN 2.0-beta16 and earlier used 5000 as the default port.
Sun Jan 17 12:05:28 2010 WARNING: No server certificate verification method has been enabled.  See [http://openvpn.net/howto.html#mitm](http://openvpn.net/howto.html#mitm) for more info.
Sun Jan 17 12:05:28 2010 NOTE: OpenVPN 2.1 requires '--script-security 2' or higher to call user-defined scripts or executables
Sun Jan 17 12:05:28 2010 /usr/bin/openssl-vulnkey -q -b 2048 -m <modulus omitted>
Sun Jan 17 12:05:28 2010 LZO compression initialized
Sun Jan 17 12:05:28 2010 UDPv4 link local (bound): [undef]:1194
Sun Jan 17 12:05:28 2010 UDPv4 link remote: *.*.*.*:1194
Sun Jan 17 12:05:29 2010 [server] Peer Connection Initiated with *.*.*.*:1194
Sun Jan 17 12:05:30 2010 TUN/TAP device tun0 opened
Sun Jan 17 12:05:30 2010 /sbin/ifconfig tun0 10.8.0.34 pointopoint 10.8.0.33 mtu 1500
Sun Jan 17 12:05:30 2010 WARNING: potential route subnet conflict between local LAN [[10.8.0.0/255.255.255.0]("http://10.8.0.0/255.255.255.0")] and remote VPN [[10.8.0.0/255.255.255.0]("http://10.8.0.0/255.255.255.0")]
Sun Jan 17 12:05:30 2010 WARNING: potential route subnet conflict between local LAN [[10.8.0.0/255.255.255.0]("http://10.8.0.0/255.255.255.0")] and remote VPN [[10.8.0.1/255.255.255.255]("http://10.8.0.1/255.255.255.255")]
Sun Jan 17 12:05:30 2010 Initialization Sequence Completed

```Connecting to PtPP VPNs from network-manager works:
```

$ tail -f /var/log/daemon.log
[...]
Jan 17 12:20:40 UbuntuBox NetworkManager: <info>  Starting VPN service 'org.freedesktop.NetworkManager.pptp'...
Jan 17 12:20:40 UbuntuBox NetworkManager: <info>  VPN service 'org.freedesktop.NetworkManager.pptp' started (org.freedesktop.NetworkManager.pptp), PID 2142
Jan 17 12:20:40 UbuntuBox NetworkManager: <info>  VPN service 'org.freedesktop.NetworkManager.pptp' just appeared, activating connections
Jan 17 12:20:40 UbuntuBox NetworkManager: <info>  VPN plugin state changed: 1
Jan 17 12:20:40 UbuntuBox NetworkManager: <info>  VPN plugin state changed: 3
Jan 17 12:20:40 UbuntuBox NetworkManager: <info>  VPN connection 'ItsHidden' (Connect) reply received.
Jan 17 12:20:40 UbuntuBox pptp[2147]: nm-pptp-service-2142 log[main:pptp.c:314]: The synchronous pptp option is NOT activated
Jan 17 12:20:40 UbuntuBox NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/ppp0, iface: ppp0)
Jan 17 12:20:40 UbuntuBox NetworkManager:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/ppp0, iface: ppp0): no ifupdown configuration found.
Jan 17 12:20:40 UbuntuBox pptp[2157]: nm-pptp-service-2142 log[ctrlp_rep:pptp_ctrl.c:251]: Sent control packet type is 1 'Start-Control-Connection-Request'
Jan 17 12:20:40 UbuntuBox pptp[2157]: nm-pptp-service-2142 log[ctrlp_disp:pptp_ctrl.c:739]: Received Start Control Connection Reply
Jan 17 12:20:40 UbuntuBox pptp[2157]: nm-pptp-service-2142 log[ctrlp_disp:pptp_ctrl.c:773]: Client connection established.
Jan 17 12:20:41 UbuntuBox pptp[2157]: nm-pptp-service-2142 log[ctrlp_rep:pptp_ctrl.c:251]: Sent control packet type is 7 'Outgoing-Call-Request'
Jan 17 12:20:41 UbuntuBox pptp[2157]: nm-pptp-service-2142 log[ctrlp_disp:pptp_ctrl.c:858]: Received Outgoing Call Reply.
Jan 17 12:20:41 UbuntuBox pptp[2157]: nm-pptp-service-2142 log[ctrlp_disp:pptp_ctrl.c:897]: Outgoing call established (call ID 0, peer's call ID 61824).
Jan 17 12:20:44 UbuntuBox pptp[2147]: nm-pptp-service-2142 log[decaps_gre:pptp_gre.c:414]: buffering packet 6 (expecting 5, lost or reordered)
Jan 17 12:20:44 UbuntuBox modprobe: FATAL: Error inserting padlock_sha (/lib/modules/2.6.31-17-generic/kernel/drivers/crypto/padlock-sha.ko): No such device
Jan 17 12:20:44 UbuntuBox pptp[2147]: nm-pptp-service-2142 log[decaps_gre:pptp_gre.c:414]: buffering packet 10 (expecting 9, lost or reordered)
Jan 17 12:20:45 UbuntuBox NetworkManager: <info>  VPN connection 'ItsHidden' (IP Config Get) reply received.
Jan 17 12:20:45 UbuntuBox NetworkManager: <info>  VPN Gateway: 0.0.0.0
Jan 17 12:20:45 UbuntuBox NetworkManager: <info>  Tunnel Device: ppp0
Jan 17 12:20:45 UbuntuBox NetworkManager: <info>  Internal IP4 Address: 192.168.0.62
Jan 17 12:20:45 UbuntuBox NetworkManager: <info>  Internal IP4 Prefix: 32
Jan 17 12:20:45 UbuntuBox NetworkManager: <info>  Internal IP4 Point-to-Point Address: 192.168.2.1
Jan 17 12:20:45 UbuntuBox NetworkManager: <info>  Maximum Segment Size (MSS): 0
Jan 17 12:20:45 UbuntuBox NetworkManager: <info>  Internal IP4 DNS: 94.75.220.1
Jan 17 12:20:45 UbuntuBox NetworkManager: <info>  Internal IP4 DNS: 94.75.220.3
Jan 17 12:20:45 UbuntuBox NetworkManager: <info>  DNS Domain: '(none)'
Jan 17 12:20:45 UbuntuBox NetworkManager: <info>  Login Banner:
Jan 17 12:20:45 UbuntuBox NetworkManager: <info>  -----------------------------------------
Jan 17 12:20:45 UbuntuBox NetworkManager: <info>  (null)
Jan 17 12:20:45 UbuntuBox NetworkManager: <info>  -----------------------------------------
Jan 17 12:20:46 UbuntuBox NetworkManager: <info>  VPN connection 'ItsHidden' (IP Config Get) complete.
Jan 17 12:20:46 UbuntuBox NetworkManager: <info>  Policy set 'ItsHidden' (ppp0) as default for routing and DNS.
Jan 17 12:20:46 UbuntuBox NetworkManager: <info>  VPN plugin state changed: 4
Jan 17 12:20:46 UbuntuBox nm-dispatcher.action: Script '/etc/NetworkManager/dispatcher.d/01ifupdown' exited with error status 1.

```Connecting to the same openvpn server (I only imported the VPN.conf) fails with 'No VPN secrets!' error and some totally useless notification:
```

$ tail -f /var/log/daemon.log
[...]
Jan 17 12:08:19 ubuntubox NetworkManager: <info>  Starting VPN service 'org.freedesktop.NetworkManager.openvpn'...
Jan 17 12:08:19 ubuntubox NetworkManager: <info>  VPN service 'org.freedesktop.NetworkManager.openvpn' started (org.freedesktop.NetworkManager.openvpn), PID 5236
Jan 17 12:08:19 ubuntubox NetworkManager: <info>  VPN service 'org.freedesktop.NetworkManager.openvpn' just appeared, activating connections
Jan 17 12:08:19 ubuntubox NetworkManager: <info>  VPN plugin state changed: 1
Jan 17 12:08:19 ubuntubox NetworkManager: <info>  VPN plugin state changed: 3
Jan 17 12:08:19 ubuntubox NetworkManager: <info>  VPN connection 'vpn-connection-1' (Connect) reply received.
Jan 17 12:08:19 ubuntubox NetworkManager: <WARN>  nm_vpn_connection_connect_cb(): VPN connection 'vpn-connection-1' failed to connect: 'No VPN secrets!'.
Jan 17 12:08:19 ubuntubox NetworkManager: <WARN>  connection_state_changed(): Could not process the request because no VPN connection was active.
Jan 17 12:08:19 ubuntubox NetworkManager: <info>  Policy set 'Auto local-wifi' (eth1) as default for routing and DNS.
Jan 17 12:08:32 ubuntubox NetworkManager: <debug> [1263726512.001193] ensure_killed(): waiting for vpn service pid 5236 to exit
Jan 17 12:08:32 ubuntubox NetworkManager: <debug> [1263726512.001390] ensure_killed(): vpn service pid 5236 cleaned up

```Really annoying TBH since I do have a correct VPN.conf which network-manager just needs to execute.

---

### Post by OlympusRunner on 2010-01-18
Hi Guys,

I am running on Ubuntu 9.10.

I got Witopia SSL working with my wireless connection.

Once you have your wireless connection set up correctly, I installed "VPN Connection Manager (OpenVPN)" from the Ubuntu Software Center. I copied my old config files from my Windows backup onto my Ubuntu desktop. (I suffered from a Vista Black Screen of Death)

Copied  "C:\Program Files\WiTopia.Net\config" to my desktop.

I then left clicked on the "Network Manager Applet" -> VPN Connections -> Configure VPN...

Then I imported "001 us - Wash DC Metro Main.ovpn"

I unchecked "Connect Automatically" and "Available to all users", although this might not matter. _I then **reset** my laptop_. My wifi connects automatically and I left clicked on the "Network Manager Applet" and clicked on "VPN Connections" and there it was. I clicked on the "001 us - Wash DC Metro Main" and it worked. I see the lock image on the menubar where the "Network Manager Applet" has an icon.

I went to checkout my ip address on [www.ip-adress.com]("http://www.ip-adress.com"). A different ip address located in D.C. popped up. My Witopia personalVPN SSL is working on Ubuntu!


... I have one question... Where should I copy my config files to on Ubuntu?
I have them on my desktop and that doesn't seem right.

The Witopia wiki [http://wiki.witopia.net/wiki/Installing_personalVPN-SSL_on_Linux](http://wiki.witopia.net/wiki/Installing_personalVPN-SSL_on_Linux) states I should use  /usr/local/openvpn/conf/ 

Any other opinions on where I should store my config files? Oh and Witopia has like 15 ovpn files for various geographic locations and a couple are for 256 SSL or TCP 443 connections. I think I might have to import all 15 files... 

Any help on the proper directory to store the config files would be appreciated.

Thanks,

OR

---

### Post by etdube on 2010-01-25
I recently upgraded to kernel 2.6.32-02063204-generic ([http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.32.4/]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v2.6.32.4/")) to solve another unrelated problem with VirtualBox, and since then the "No VPN secrets" error seems to have vanished. The VPN now connects every time on 1st try.

Can somebody else confirm that this also fixes the problem for them? Note: please don't try to upgrade your kernel from unofficial .deb packages unless you really know what you are doing. Something else could break, and I won't take the blame!

---

### Post by JlyGrnMigt on 2010-01-26
I'm trying to get the witopia ssl up and running on ubuntu netbook remix 9.10.

I've followed all the steps here and have imported a few of the location files.  The first time I tried to connect I got the vpn secrets error, and every subsequent try has led to...nothing.  It doesn't connect, but it doesn't give me an error.

I had to change the screen config to even see the part about sharing with all users, but it was not checked by default.

---

### Post by OlympusRunner on 2010-01-26
I noticed when I had VirtualBox running I could not enable my Witopia VPN. 
I always had to start the VPN connection before starting anything else.

Upon logging in to Ubuntu, wait for your wifi to connect, and then connect to the VPN.
If it didn't work wait 5 minutes and try it again and then check on one of those websites that shows you your ip address.

---

### Post by mehmet.ali.anil on 2010-02-07
I just realized that (at least that is the case in my system) , when you import an .ovpn config file network-manager sometimes fails to import some of the configurations, in my case, it imported the authentication method as TLS, and though every other thing was correct, I also gave the error mentioned. When I changed the authentication method to Password with Certificates (TLS), and I gave my username and password on the remote server account, my vpn started to work properly.

Also, In my system, when I browsed for my .key file (private key) though in the dialogbox it was indicated that I was searching for "PEM Certificates *.pem *.crt *.key *.cer" , my .key files seemed to be missing, though it was there, and it is not hidden. That could be another problem.

---

### Post by c.zach on 2010-03-15
I had the same problem - Karmic Koala, network manager and OpenVPN.

What solved the problem:

Even as I does NOT have connection requiring user name and my private key is NOT password protected I changed type of connection to Password/Certificate and filled username and password with random values. I also filled random password for my private key. 

This did it for me, hopefully it will help some of you.

PS: The problem might be connected somehow to network-manager using a keyring, so if you need username/passwords it might be worth a while to try removing these passwords from keyring or enabling/disabling keyring. I have keyring on and it works for me.

---

### Post by dedieko on 2010-04-09
> **c.zach said:**
> I had the same problem - Karmic Koala, network manager and OpenVPN.

What solved the problem:

Even as I does NOT have connection requiring user name and my private key is NOT password protected I changed type of connection to Password/Certificate and filled username and password with random values. I also filled random password for my private key. 

This did it for me, hopefully it will help some of you.

PS: The problem might be connected somehow to network-manager using a keyring, so if you need username/passwords it might be worth a while to try removing these passwords from keyring or enabling/disabling keyring. I have keyring on and it works for me.

+1 Confirm, solved the problem,THANK YOU!!

---

### Post by JlyGrnMigt on 2010-05-17
> **c.zach said:**
> I had the same problem - Karmic Koala, network manager and OpenVPN.

What solved the problem:

Even as I does NOT have connection requiring user name and my private key is NOT password protected I changed type of connection to Password/Certificate and filled username and password with random values. I also filled random password for my private key. 

This did it for me, hopefully it will help some of you.


How weird.  It works for me too.

---

### Post by SaM98 on 2010-05-17
I have the same problem

---

### Post by emecas on 2010-07-06
> **ty1033 said:**
> Dear all,

After I searched a lot of posts over the Internet, only one can answered the problem about "No VPN secrets" on Ubuntu 9.10

Actually, don't check "Available to all users." on Network Manager. Enable MPPE. Leave the rest as default.

[COLOR=Red]Problem : VPN connection 'openvpn' failed to connect: 'No VPN secrets!'.[/COLOR]

Reference : [https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/284212/comments/69](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/284212/comments/69)

Enjoy Ubuntu 9.10 !!! It is great ! Now I am an Ubuntu-er

Thanks!!!

This combination works for me.... i have tried many others and the connection has failed. Ubuntu 10.04 Lucid


EmeCas

---

