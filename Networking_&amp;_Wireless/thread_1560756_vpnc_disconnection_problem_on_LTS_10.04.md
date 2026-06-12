---
title: "vpnc disconnection problem on LTS 10.04"
date: 2010-08-25
forum: Networking &amp; Wireless
---

### Post by cashy on 2010-08-25
Hi,
 
I have 10.04 official, fresh installation. My vpnc "disconnects" after about 16 minutes.
 I tried various setups, tried Makovick-patches, and I reached the  point, where there are no error messages, everything seems to be okay,  but the other side of the vpn is not reachable... :(


 With nm-applet:
Connection successful, got the login banner. Everíthing is okay, speed is right.
Syslog says:
--
Aug 25 14:09:40 cashy-laptop NetworkManager: <info>  Starting VPN service 'org.freedesktop.NetworkManager.vpnc'...
Aug 25 14:09:40 cashy-laptop NetworkManager: <info>  VPN service 'org.freedesktop.NetworkManager.vpnc' started (org.freedesktop.NetworkManager.vpnc), PID 9690
Aug 25 14:09:40 cashy-laptop NetworkManager: <info>  VPN service 'org.freedesktop.NetworkManager.vpnc' just appeared, activating connections
Aug 25 14:09:40 cashy-laptop NetworkManager: <info>  VPN plugin state changed: 1
Aug 25 14:09:40 cashy-laptop NetworkManager: <info>  VPN plugin state changed: 3
Aug 25 14:09:40 cashy-laptop NetworkManager: <info>  VPN connection 'WORK' (Connect) reply received.
Aug 25 14:09:40 cashy-laptop NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/tun0, iface: tun0)
Aug 25 14:09:40 cashy-laptop kernel: [63073.336892] tun0: Disabled Privacy Extensions
Aug 25 14:09:40 cashy-laptop NetworkManager:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/tun0, iface: tun0): no ifupdown configuration found.
Aug 25 14:09:40 cashy-laptop NetworkManager: <info>  VPN connection 'WORK' (IP Config Get) reply received.
Aug 25 14:09:40 cashy-laptop NetworkManager: <info>  VPN Gateway: xxx.xxx.xxx.xxx
Aug 25 14:09:40 cashy-laptop NetworkManager: <info>  Tunnel Device: tun0
Aug 25 14:09:40 cashy-laptop NetworkManager: <info>  Internal IP4 Address: 10.100.101.239
Aug 25 14:09:40 cashy-laptop NetworkManager: <info>  Internal IP4 Prefix: 24
Aug 25 14:09:40 cashy-laptop NetworkManager: <info>  Internal IP4 Point-to-Point Address: 10.100.101.239
Aug 25 14:09:40 cashy-laptop NetworkManager: <info>  Maximum Segment Size (MSS): 0
Aug 25 14:09:40 cashy-laptop NetworkManager: <info>  Static Route: 192.168.110.0/24   Next Hop: 192.168.110.0
Aug 25 14:09:40 cashy-laptop NetworkManager: <info>  Internal IP4 DNS: 84.2.44.1
Aug 25 14:09:40 cashy-laptop NetworkManager: <info>  Internal IP4 DNS: 84.2.46.1
Aug 25 14:09:40 cashy-laptop NetworkManager: <info>  DNS Domain: '(none)'
Aug 25 14:09:40 cashy-laptop NetworkManager: <info>  Login Banner:
---
And not so suddenly, after 16 minutes:
---
Aug 25 14:09:41 cashy-laptop NetworkManager: <info>  VPN connection WORK' (IP Config Get) complete.
Aug 25 14:09:41 cashy-laptop NetworkManager: <info>  Policy set 'Auto HOME' (wlan0) as default for routing and DNS.
Aug 25 14:09:41 cashy-laptop NetworkManager: <info>  VPN plugin state changed: 4
Aug 25 14:09:41 cashy-laptop nm-dispatcher.action: Script '/etc/NetworkManager/dispatcher.d/01ifupdown' exited with error status 1.
---
 With patched vpnc (vpnc-0.5.3r449) nearly the same:
Login, and login banner, counter starts to tick.
Ticks and ticks, but after 16 minutes ping works with 100% packet loss.
 Earlier I tried vpnc-nortel (0.5.3) and the unpatched vpnc (vpnc-0.5.3r449). Brought the same. There was some error messages.
First the "tun0: Disabled Privacy Extensions" informational, and when  the connection begun to hang up, I got two kinds of error messages: "got  late ike packet" and "got packet with wrong cookies". They came about  3-4 times, and then the connection completely stopped.
 Here is the config file, which I tried:
--
IPSec ID WORKDOMAIN
IPSec secret WORKDOMAINPASSWORD
IPSec gateway xxx.xxx.xxx.xxx
Xauth username MYUSERNAME
Xauth password MYUSERPASSWORD
Domain WORKDOMAIN
IKE Authmode psk
Target Networks 192.168.110.0/24
DNSUpdate No
DPD Idle timeout (our side) 0
NAT Traversal Mode cisco-udp
#NAT Traversal Mode force-natt
Enable Single DES
Local Port 10000
---
 Sorry about my "not-so-fluent" English.
Anybody can help?

---

### Post by cashy on 2010-08-25
Additionally:
 I got this in syslog next time, when vpn hung:
---
Aug 25 14:26:38 cashy-laptop NetworkManager:    SCPlugin-Ifupdown: devices removed (path: /sys/devices/virtual/net/tun0, iface: tun0)
Aug 25 14:26:38 cashy-laptop NetworkManager: <info>  VPN plugin failed: 1
Aug 25 14:26:38 cashy-laptop NetworkManager: <info>  VPN plugin state changed: 6
Aug 25 14:26:38 cashy-laptop NetworkManager: <info>  VPN plugin state change reason: 0
Aug 25 14:26:38 cashy-laptop NetworkManager: <WARN>  connection_state_changed(): Could not process the request because no VPN connection was active.
Aug 25 14:26:39 cashy-laptop NetworkManager: <info>  Policy set 'Auto HOME' (wlan0) as default for routing and DNS.
Aug 25 14:26:39 cashy-laptop nm-dispatcher.action: Script '/etc/NetworkManager/dispatcher.d/01ifupdown' exited with error status 1.
Aug 25 14:26:52 cashy-laptop NetworkManager: <debug>  [1282739212.001864] ensure_killed(): waiting for vpn service pid 9690 to  exit
Aug 25 14:26:52 cashy-laptop NetworkManager: <debug> [1282739212.001961] ensure_killed(): vpn service pid 9690 cleaned up

---

### Post by cashy on 2010-08-25
I tried the official cisco vpn client. Dead end. It freezes my system, even if I enable one of the cpu-s. So no way.

I installed cisco vpn client on my winbox, in vmware. I don't want to use it. But I must. :(

---

### Post by cashy on 2010-08-28
Bump.

Anybody? Please help me!

---

### Post by cashy on 2010-08-31
Bump.

---

### Post by Haphazard on 2010-09-01
Hi,

I had / have a similar problem -and when looking at your log postings I found them very similar to what I was experiencing.

My admin (whom I contacted) told me that there are problems with Ubuntu and VPNC connections which he suggested are solved by setting the MTU for the VPN connection (this has something to do with packet size, which should be less than 1300 in order to work).

the trick was to type into a console:
```
sudo ifconfig tun0 mtu 1250
```

This did not work when the connection was not up (you get an error message)
 but works fine when the VPN connection is up.

Then the connection stayed up in my case. BUT I still have problems:
a) do I have to do that every time I connect?
b) why do some links not work when connected (internal addresses work but not external addresses)

Hope this helps you in some way.

btw. I use Ubuntu 10.04 LTS with all updates and use not a script to set up the connection but type into the GUI the information needed.

Good luck. And please post back if you are successful and whether you can do normal "usage".

CU
Haphazard

---

### Post by cashy on 2010-09-24
Sorry for the late answering.

I tried vpnc from behind three different routers. I tried MTU setting (thanks a lot!) on 1250, 1300 (the windows cisco vpn client setting!), and lower values (for e.: 960). It's all the same. After 16 minutes connection hangs up.

I use vmware and winxp inside of it, because of this problem :(

Regards,
   cashy

---

### Post by mikemcginn on 2011-06-21
I have had the very same problem since I started using vpnc. The vpnc man page refers to [http://www.unix-ag.uni-kl.de/~massar/vpnc/](http://www.unix-ag.uni-kl.de/~massar/vpnc/), which indicates that cpnc has not been updated since November of 2009. Tellingly the disconnection problem is listed among the known bugs. I am fortunate in that I have had my data center open the firewall to my ficed IP at work, and I only need to use vpnc for short bursts when something goes wrong while I am not at work.

---

### Post by mikemcginn on 2011-06-23
I have a colleague with the same problem under FreeBSD. The problem seems to be endemic with version 0.5.3 of vpnc, which does not seem to have been touched by a developer in quite a while. By comparing logs, we have determined that both of us, thousand of miles apart get disconnected after exactly one hour.
4369:Jun 21 19:11:26 adrastea ntpd[10645]: Listening on interface #9 tun0, 10.38.9.58#123 Enabled
4431:Jun 21 20:09:56 adrastea NetworkManager:    SCPlugin-Ifupdown: devices removed (path: /sys/devices/virtual/net/tun0, iface: tun0)
4432:Jun 21 20:10:37 adrastea NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/tun0, iface: tun0)
4433:Jun 21 20:10:37 adrastea NetworkManager:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/tun0, iface: tun0): no ifupdown configuration found.
4435:Jun 21 20:11:26 adrastea ntpd[10645]: Listening on interface #10 tun0, 10.38.9.55#123 Enabled
4436:Jun 21 20:11:26 adrastea ntpd[10645]: Deleting interface #9 tun0, 10.38.9.58#123, interface stats: received=0, sent=0, dropped=0, active_time=3600 secs

I conferred with the guy who runs the Cisco PIX at out colo. This coincides with the rekeying interval (3600 seconds) in the PIX firewall.

My colleagues logs showed the same 3600 second disconnect. 

Does anyone know if vpnc is being actively maintained at this point??

---

