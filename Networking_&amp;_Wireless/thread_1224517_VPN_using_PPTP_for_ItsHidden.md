---
title: "VPN using PPTP for ItsHidden"
date: 2009-07-27
forum: Networking &amp; Wireless
---

### Post by Bender2k14 on 2009-07-27
Can anyone successfully make a VPN connection to [ItsHidden]("http://itshidden.com/"), which uses PPTP?  If so, please share what you did.

---

### Post by Subban on 2009-07-27
I am failing also to make a connection, have installed network-manager-pptp (or similar) but am failing to connect when I try.

---

### Post by zaadjis on 2009-07-27
I get the error message: "LCP terminated by peer (MPPE required but peer negotiation failed)"

Googling the error message gave me [http://pptpclient.sourceforge.net/howto-diagnosis.phtml#mppe_rbpnf](http://pptpclient.sourceforge.net/howto-diagnosis.phtml#mppe_rbpnf) and [https://bugs.launchpad.net/ubuntu/+source/ppp/+bug/88986](https://bugs.launchpad.net/ubuntu/+source/ppp/+bug/88986) (has patches to pppd attached).

---

### Post by zaadjis on 2009-07-27
I got it to work by re-configuring it to "Use Point-to-Point encryption", see screenshot.

---

### Post by Bender2k14 on 2009-07-27
> **zaadjis said:**
> I got it to work by re-configuring it to "Use Point-to-Point encryption"

Did you apply any patches to the network manager (that you mentioned in your previous post)?

---

### Post by zaadjis on 2009-07-27
> **Bender2k14 said:**
> Did you apply any patches to the network manager (that you mentioned in your previous post)?

No, just ticked the "Use Point-to-Point.." option in the advanced configuration window. Patching pppd would be more trouble than it's worth just to try out a free VPN ;)

---

### Post by gameguy15 on 2009-07-28
Yup worked great this is what i did.
sudo apt-get install network-manager-pptp
then I used the point to point like zaadjis said, with the 128 bit encryption, It wont work for me then so I restarted and it worked right away. The service even lets you have at least 2 computers logged in its great!

---

### Post by Bender2k14 on 2009-07-28
Ok, restarting was the step I was missing.  Here is a summary of the steps that worked for me (and does not include restarting your whole computer):

[http://ubuntu-chronicles.blogspot.com/2009/07/jaunty-vpn-itshiddencom.html]("http://ubuntu-chronicles.blogspot.com/2009/07/jaunty-vpn-itshiddencom.html")

---

### Post by trobrock on 2009-07-29
I am trying to get ItsHidden VPN working on Ubuntu 9.04 as a VM inside of OS X, I have done all the steps that everyone said worked for them, but I am still unable to connect to the VPN.  Is there any reason a VM would cause the VPN not to connect?

---

### Post by dawgonit on 2009-07-29
I had to add the following to my /etc/shorewall/interfaces file

> net ppp0 detect

I also added the following to the /etc/shorewall/zones file

> vpn     ipv4

then restart shorewall

> sudo shorewall restart

I hope it helps some of you.

---

### Post by trobrock on 2009-07-29
> **dawgonit said:**
> I had to add the following to my /etc/shorewall/interfaces file



I also added the following to the /etc/shorewall/zones file



then restart shorewall



I hope it helps some of you.

I do not have a /etc/shorewall folder, any other ideas for this to work in a VM?

---

### Post by dawgonit on 2009-07-29
I just posted that because I know many use shorewall and perhaps it might help for the same problem.

I posted the following which worked for someone else. I do not take credit for it I simply came across it. Perhaps it will help you as well.

> I saw someone else had entered the wrong password for the default keyring. They simply opened home folder and view hidden folders. They then deleted the key file from ./gnome2/keyring.

They then tried to connect again and used the same password they used for registering the user vpn account and it worked for them.

---

### Post by trobrock on 2009-07-29
> **dawgonit said:**
> I just posted that because I know many use shorewall and perhaps it might help for the same problem.

I posted the following which worked for someone else. I do not take credit for it I simply came across it. Perhaps it will help you as well.

Still no luck, I may try and set ip up on my Jaunty box at home that is not a VM and see if it works to determine whether im just doing something wrong or if it it because of the VM

---

### Post by dawgonit on 2009-07-29
I've got time so I will set it up using virtual box and see if it gives me problems.

---

### Post by trobrock on 2009-07-29
> **dawgonit said:**
> I've got time so I will set it up using virtual box and see if it gives me problems.

Thanks, let me know how it goes.

---

### Post by dawgonit on 2009-07-29
I tried several OS and all failed. I searched google and found out that the vpn servers we need to connect to will not allow two connections from the same ip #. Since the tunnel goes from guest to host interface it has the same ip #.

I think I have a work around by using 2 network cards and assiginng one to host and one to guest in hopes of show a separate ip. I am out of time but will try this theroy in the next couple of days.

This is why I pay for my vpn I can run it as software via Mac,MS & Linux always connecting even if all 3 at the same time.

---

### Post by trobrock on 2009-07-29
> **dawgonit said:**
> I tried several OS and all failed. I searched google and found out that the vpn servers we need to connect to will not allow two connections from the same ip #. Since the tunnel goes from guest to host interface it has the same ip #.

I think I have a work around by using 2 network cards and assiginng one to host and one to guest in hopes of show a separate ip. I am out of time but will try this theroy in the next couple of days.

This is why I pay for my vpn I can run it as software via Mac,MS & Linux always connecting even if all 3 at the same time.

So it shows up as two computer from the same ip even if I am not connected to the VPN with the host?

---

### Post by dawgonit on 2009-07-29
It appears like that. I spent an hour messing with every configuration I could while watching the log files for clues and that is what appears to me and the errors I recorded why it will not connect via guest. 

Perhaps someone can prove me wrong. I'm going to try via 2 separate interface pci cards through my router, one for guest and one for host. I will post back if or if not it worked unless someone smarter than me here figures how to to it(more than I can count that are smarter than I am here) :))

---

### Post by dawgonit on 2009-07-29
type in firefox url bar > about:configdouble left click to change it from false to true

> network.proxy.socks_remote_dns  trueThis lets remote (not your ISP) DNS hook you up.

A little more privacy.

Restart FF

---

### Post by clandestiny on 2009-08-01
I have intermittent trouble with this at work, and I think I might have figured out why ....

This service uses addresses in the 192.168.0.0, 192.168.1.0, and 192.168.2.0 networks, that I have seen so far.  My office uses the last two of those.  Any collision with anything real inside your own LAN -- seems to me -- could only cause problems.  Sometimes it works from my office, sometimes not.

At home, my network uses addresses off the 10.0.0.0 family, and I haven't had a lick of trouble with this, since I got it configured right and working.  (Historically, I've had enough problems in general with routers and even packet spoofers using 192.168.*.* that I avoid it on principle, preferring something deep in the 10.*.*.* family that's almost impossible to guess and very unlikely to ever collide with.)

For the record, my work box is Windows XP on a Linux LAN, and my home box is Ubuntu Intrepid (using hand-configured pptp-linux package, as I abhor networkmanager) on a Linux LAN.

Also, for the record, speedtest.net clocked me around 2-3mb/.3mb up/down for various sites in USA, Europe and Africa.  I don't see how anyone could ask more from a free service.  :)

---

### Post by dawgonit on 2009-08-01
I just disconnected from a router and connected directly to my dsl modem. No problems using the vpn. I did the same inside as guest and no problems connecting like before.  clandestiny hit it right on. Thanks.

> I have intermittent trouble with this at work, and I think I might have figured out why ....

This service uses addresses in the 192.168.0.0, 192.168.1.0, and 192.168.2.0 networks, that I have seen so far. My office uses the last two of those. Any collision with anything real inside your own LAN -- seems to me -- could only cause problems. Sometimes it works from my office, sometimes not.

At home, my network uses addresses off the 10.0.0.0 family, and I haven't had a lick of trouble with this, since I got it configured right and working. (Historically, I've had enough problems in general with routers and even packet spoofers using 192.168.*.* that I avoid it on principle, preferring something deep in the 10.*.*.* family that's almost impossible to guess and very unlikely to ever collide with.)

For the record, my work box is Windows XP on a Linux LAN, and my home box is Ubuntu Intrepid (using hand-configured pptp-linux package, as I abhor networkmanager) on a Linux LAN.I agree it is great speed for free.

> Also, for the record, speedtest.net clocked me around 2-3mb/.3mb up/down for various sites in USA, Europe and Africa. I don't see how anyone could ask more from a free service.

---

### Post by drainplugofideas on 2009-08-03
It wasn't working for me (just didn't do anything) but after a reboot it's working great. I'm pretty happy about it.

---

### Post by dawgonit on 2009-08-04
Just a warning if you use this it will timeout and allow your real IP # to be shown. I've gone off the idea until they add port forwarding. The paid VPN I use will not allow anything to pass through if it goes down providing that you have your firewall configured correctly and it has only happened once in the past 5 years.

---

### Post by Willli on 2010-01-08
In my syslog, I got this messages
Jan  8 11:49:34 NetworkManager: <info>  Starting VPN service 'org.freedesktop.NetworkManager.pptp'...
Jan  8 11:49:34  NetworkManager: <info>  VPN service 'org.freedesktop.NetworkManager.pptp' started (org.freedesktop.NetworkManager.pptp), PID 4228
Jan  8 11:49:34  NetworkManager: <info>  VPN service 'org.freedesktop.NetworkManager.pptp' just appeared, activating connections
Jan  8 11:49:34  NetworkManager: <info>  VPN plugin state changed: 1
Jan  8 11:49:37  NetworkManager: <info>  VPN plugin state changed: 3
Jan  8 11:49:37  pppd[4267]: Plugin /usr/lib/pppd/2.4.5//nm-pptp-pppd-plugin.so loaded.
Jan  8 11:49:37  NetworkManager: <info>  VPN connection 'ItsHidden' (Connect) reply received.
Jan  8 11:49:37  pppd[4267]: pppd 2.4.5 started by root, uid 0
Jan  8 11:49:37  pppd[4267]: Using interface ppp0
Jan  8 11:49:37  pppd[4267]: Connect: ppp0 <--> /dev/pts/0
Jan  8 11:49:37  NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/ppp0, iface: ppp0)
Jan  8 11:49:37  NetworkManager:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/ppp0, iface: ppp0): no ifupdown configuration found.
Jan  8 11:49:52  wpa_supplicant[1254]: CTRL-EVENT-SCAN-RESULTS 
Jan  8 11:49:57  pptp[4269]: nm-pptp-service-4228 fatal[get_ip_address:pptp.c:430]: gethostbyname 'vpn.itshidden.com': HOST NOT FOUND
Jan  8 11:49:57  pppd[4267]: Modem hangup
Jan  8 11:49:57  pppd[4267]: Connection terminated.
Jan  8 11:49:57  NetworkManager: <info>  VPN plugin failed: 1
Jan  8 11:49:57  NetworkManager:    SCPlugin-Ifupdown: devices removed (path: /sys/devices/virtual/net/ppp0, iface: ppp0)
Jan  8 11:49:57  pppd[4267]: Exit.

I'm using Ubuntu 9.10. I restarted my computer several times and I get the same error. Could you tell me what is the problem?

---

### Post by bin4ryninj4 on 2010-08-26
Having pretty much the same issue as everyone else when trying to connect to itsHidden VPN.  I know for a fact my usrname/psswd is correct because I can log on to the sight.  I have all the plugins for network manager.  

I am using Lucid Lunix on an Acer Aspire with all updates to the date of this posting.  I have deleted my keyrings, and restarted several times.  here is my syslog output after trying to connect:

Aug 26 12:51:18 hiro-H4ckBook NetworkManager: <info>  Starting VPN service 'org.freedesktop.NetworkManager.pptp'...
Aug 26 12:51:18 hiro-H4ckBook NetworkManager: <info>  VPN service 'org.freedesktop.NetworkManager.pptp' started (org.freedesktop.NetworkManager.pptp), PID 19096
Aug 26 12:51:18 hiro-H4ckBook NetworkManager: <info>  VPN service 'org.freedesktop.NetworkManager.pptp' just appeared, activating connections
Aug 26 12:51:18 hiro-H4ckBook NetworkManager: <info>  VPN plugin state changed: 1
Aug 26 12:51:18 hiro-H4ckBook NetworkManager: <info>  VPN plugin state changed: 3
Aug 26 12:51:18 hiro-H4ckBook NetworkManager: <info>  VPN connection 'itsHidden' (Connect) reply received.
Aug 26 12:51:18 hiro-H4ckBook pppd[19109]: Plugin /usr/lib/pppd/2.4.5//nm-pptp-pppd-plugin.so loaded.
Aug 26 12:51:18 hiro-H4ckBook pppd[19109]: pppd 2.4.5 started by root, uid 0
Aug 26 12:51:18 hiro-H4ckBook NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/ppp0, iface: ppp0)
Aug 26 12:51:18 hiro-H4ckBook NetworkManager:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/ppp0, iface: ppp0): no ifupdown configuration found.
Aug 26 12:51:18 hiro-H4ckBook pppd[19109]: Using interface ppp0
Aug 26 12:51:18 hiro-H4ckBook pppd[19109]: Connect: ppp0 <--> /dev/pts/0
Aug 26 12:51:18 hiro-H4ckBook pptp[19113]: nm-pptp-service-19096 log[main:pptp.c:314]: The synchronous pptp option is NOT activated
Aug 26 12:51:39 hiro-H4ckBook pptp[19115]: nm-pptp-service-19096 warn[open_inetsock:pptp_callmgr.c:329]: connect: Connection timed out
Aug 26 12:51:39 hiro-H4ckBook pptp[19115]: nm-pptp-service-19096 fatal[callmgr_main:pptp_callmgr.c:127]: Could not open control connection to 94.75.253.244
Aug 26 12:51:39 hiro-H4ckBook pptp[19113]: nm-pptp-service-19096 fatal[open_callmgr:pptp.c:479]: Call manager exited with error 256
Aug 26 12:51:39 hiro-H4ckBook pppd[19109]: Modem hangup
Aug 26 12:51:39 hiro-H4ckBook pppd[19109]: Connection terminated.
Aug 26 12:51:39 hiro-H4ckBook NetworkManager: <info>  VPN plugin failed: 1
Aug 26 12:51:39 hiro-H4ckBook NetworkManager:    SCPlugin-Ifupdown: devices removed (path: /sys/devices/virtual/net/ppp0, iface: ppp0)
Aug 26 12:51:39 hiro-H4ckBook pppd[19109]: Exit.
Aug 26 12:51:39 hiro-H4ckBook NetworkManager: <info>  VPN plugin failed: 1
Aug 26 12:51:39 hiro-H4ckBook NetworkManager: <info>  VPN plugin failed: 1
Aug 26 12:51:39 hiro-H4ckBook NetworkManager: <info>  VPN plugin state changed: 6
Aug 26 12:51:39 hiro-H4ckBook NetworkManager: <info>  VPN plugin state change reason: 0
Aug 26 12:51:39 hiro-H4ckBook NetworkManager: <WARN>  connection_state_changed(): Could not process the request because no VPN connection was active.
Aug 26 12:51:39 hiro-H4ckBook NetworkManager: <info>  Policy set 'Auto GothamPublic' (wlan0) as default for routing and DNS.
Aug 26 12:51:52 hiro-H4ckBook NetworkManager: <debug> [1282841512.002457] ensure_killed(): waiting for vpn service pid 19096 to exit
Aug 26 12:51:52 hiro-H4ckBook NetworkManager: <debug> [1282841512.002597] ensure_killed(): vpn service pid 19096 cleaned up

I did read a post stating that connecting with a IP like other IP's on my network might be causing a problem.  I am also aware that my companies firewall might be blocking the attempt.  I haven't tried using our LAN just yet nor have I tried from any other network.  Any help with this would be great.  Thankx!

---

### Post by KIAaze on 2010-11-08
I'm also unable to connect.
Ubuntu 10.10.
Other VPNs I configured work.

(I also wanted to try cyberghostvpn, but I can't even find the name of the gateway for it... Running the windows installer with Wine failed.)

---

### Post by GlennW on 2010-11-09
I'm having trouble with my vpn connection via itshidden. I have been pouring over various posts and trying everything I can see to do all to no avail.

Here is the syslog from my last connection attempt:

[INDENT]Nov  9 11:43:00 glenn-desktop NetworkManager[1043]: <info> Starting VPN service 'org.freedesktop.NetworkManager.pptp'...
Nov  9 11:43:00 glenn-desktop NetworkManager[1043]: <info> VPN service 'org.freedesktop.NetworkManager.pptp' started (org.freedesktop.NetworkManager.pptp), PID 1932
Nov  9 11:43:00 glenn-desktop NetworkManager[1043]: <info> VPN service 'org.freedesktop.NetworkManager.pptp' appeared, activating connections
Nov  9 11:43:00 glenn-desktop NetworkManager[1043]: <info> VPN plugin state changed: 1
Nov  9 11:43:06 glenn-desktop NetworkManager[1043]: <info> VPN plugin state changed: 3
Nov  9 11:43:06 glenn-desktop NetworkManager[1043]: <info> VPN connection 'ItsHidden' (Connect) reply received.
Nov  9 11:43:06 glenn-desktop pppd[1934]: Plugin /usr/lib/pppd/2.4.5//nm-pptp-pppd-plugin.so loaded.
Nov  9 11:43:06 glenn-desktop pppd[1934]: pppd 2.4.5 started by root, uid 0
Nov  9 11:43:06 glenn-desktop pppd[1934]: Using interface ppp0
Nov  9 11:43:06 glenn-desktop pppd[1934]: Connect: ppp0 <--> /dev/pts/0
Nov  9 11:43:06 glenn-desktop modem-manager: (net/ppp0): could not get port's parent device
Nov  9 11:43:06 glenn-desktop NetworkManager[1043]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/ppp0, iface: ppp0)
Nov  9 11:43:06 glenn-desktop NetworkManager[1043]:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/ppp0, iface: ppp0): no ifupdown configuration found.
Nov  9 11:43:06 glenn-desktop pptp[1938]: nm-pptp-service-1932 log[main:pptp.c:314]: The synchronous pptp option is NOT activated
Nov  9 11:43:06 glenn-desktop pptp[1940]: nm-pptp-service-1932 warn[open_inetsock:pptp_callmgr.c:329]: connect: Connection refused
Nov  9 11:43:06 glenn-desktop pptp[1940]: nm-pptp-service-1932 fatal[callmgr_main:pptp_callmgr.c:127]: Could not open control connection to 94.75.253.244
Nov  9 11:43:06 glenn-desktop pptp[1938]: nm-pptp-service-1932 fatal[open_callmgr:pptp.c:487]: Call manager exited with error 256
Nov  9 11:43:06 glenn-desktop pppd[1934]: Modem hangup
Nov  9 11:43:06 glenn-desktop pppd[1934]: Connection terminated.
Nov  9 11:43:06 glenn-desktop NetworkManager[1043]: <warn> VPN plugin failed: 1
Nov  9 11:43:06 glenn-desktop avahi-daemon[1036]: Withdrawing workstation service for ppp0.
Nov  9 11:43:06 glenn-desktop NetworkManager[1043]:    SCPlugin-Ifupdown: devices removed (path: /sys/devices/virtual/net/ppp0, iface: ppp0)
Nov  9 11:43:06 glenn-desktop pppd[1934]: Exit.
Nov  9 11:43:06 glenn-desktop NetworkManager[1043]: <warn> VPN plugin failed: 1
Nov  9 11:43:06 glenn-desktop NetworkManager[1043]: <warn> VPN plugin failed: 1
Nov  9 11:43:06 glenn-desktop NetworkManager[1043]: <info> VPN plugin state changed: 6
Nov  9 11:43:06 glenn-desktop NetworkManager[1043]: <info> VPN plugin state change reason: 0
Nov  9 11:43:06 glenn-desktop NetworkManager[1043]: <warn> error disconnecting VPN: Could not process the request because no VPN connection was active.
Nov  9 11:43:06 glenn-desktop NetworkManager[1043]: <info> Policy set 'Auto eth0' (eth0) as default for IPv4 routing and DNS.[/INDENT]

Can anyone make sense of this?

Thanks...

---

### Post by GlennW on 2010-12-03
bump......

---

### Post by Henns Wörst on 2010-12-17
I've got exactly the same sh*t with maverick:

> Dec 17 12:16:30 netbook vpnagent[1560]: Function: tableCallbackHandler File: RouteMgr.cpp Line: 1692 Invoked Function: recv Return Code: 11 (0x0000000B) Description: unknown 
Dec 17 12:17:00 netbook vpnagent[1560]: Function: tableCallbackHandler File: RouteMgr.cpp Line: 1692 Invoked Function: recv Return Code: 11 (0x0000000B) Description: unknown 
Dec 17 12:17:01 netbook CRON[6587]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Dec 17 12:18:08 netbook vpnagent[1560]: Function: tableCallbackHandler File: RouteMgr.cpp Line: 1692 Invoked Function: recv Return Code: 11 (0x0000000B) Description: unknown 
Dec 17 12:18:38 netbook vpnagent[1560]: Function: tableCallbackHandler File: RouteMgr.cpp Line: 1692 Invoked Function: recv Return Code: 11 (0x0000000B) Description: unknown 
Dec 17 12:19:45 netbook vpnagent[1560]: Function: tableCallbackHandler File: RouteMgr.cpp Line: 1692 Invoked Function: recv Return Code: 11 (0x0000000B) Description: unknown 
Dec 17 12:20:15 netbook vpnagent[1560]: Function: tableCallbackHandler File: RouteMgr.cpp Line: 1692 Invoked Function: recv Return Code: 11 (0x0000000B) Description: unknown 
Dec 17 12:21:23 netbook vpnagent[1560]: Function: tableCallbackHandler File: RouteMgr.cpp Line: 1692 Invoked Function: recv Return Code: 11 (0x0000000B) Description: unknown 
Dec 17 12:21:53 netbook vpnagent[1560]: Function: tableCallbackHandler File: RouteMgr.cpp Line: 1692 Invoked Function: recv Return Code: 11 (0x0000000B) Description: unknown 
Dec 17 12:23:00 netbook vpnagent[1560]: Function: tableCallbackHandler File: RouteMgr.cpp Line: 1692 Invoked Function: recv Return Code: 11 (0x0000000B) Description: unknown 
Dec 17 12:23:12 netbook NetworkManager[984]: <info> Starting VPN service 'org.freedesktop.NetworkManager.pptp'...
Dec 17 12:23:12 netbook NetworkManager[984]: <info> VPN service 'org.freedesktop.NetworkManager.pptp' started (org.freedesktop.NetworkManager.pptp), PID 6697
Dec 17 12:23:12 netbook NetworkManager[984]: <info> VPN service 'org.freedesktop.NetworkManager.pptp' appeared, activating connections
Dec 17 12:23:12 netbook NetworkManager[984]: <info> VPN plugin state changed: 1
Dec 17 12:23:12 netbook NetworkManager[984]: <info> VPN plugin state changed: 3
Dec 17 12:23:12 netbook NetworkManager[984]: <info> VPN connection 'HideIpVpn' (Connect) reply received.
Dec 17 12:23:12 netbook pppd[6698]: Plugin /usr/lib/pppd/2.4.5//nm-pptp-pppd-plugin.so loaded.
Dec 17 12:23:12 netbook pppd[6698]: pppd 2.4.5 started by root, uid 0
Dec 17 12:23:12 netbook NetworkManager[984]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/ppp0, iface: ppp0)
Dec 17 12:23:12 netbook NetworkManager[984]:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/ppp0, iface: ppp0): no ifupdown configuration found.
Dec 17 12:23:12 netbook modem-manager: (net/ppp0): could not get port's parent device
Dec 17 12:23:12 netbook pppd[6698]: Using interface ppp0
Dec 17 12:23:12 netbook pppd[6698]: Connect: ppp0 <--> /dev/pts/2
Dec 17 12:23:12 netbook pptp[6702]: nm-pptp-service-6697 log[main:pptp.c:314]: The synchronous pptp option is NOT activated
Dec 17 12:23:12 netbook vpnagent[1560]: Function: tableCallbackHandler File: RouteMgr.cpp Line: 1692 Invoked Function: recv Return Code: 11 (0x0000000B) Description: unknown 
Dec 17 12:23:13 netbook pptp[6709]: nm-pptp-service-6697 log[ctrlp_rep:pptp_ctrl.c:251]: Sent control packet type is 1 'Start-Control-Connection-Request'
Dec 17 12:23:13 netbook pptp[6709]: nm-pptp-service-6697 log[ctrlp_disp:pptp_ctrl.c:739]: Received Start Control Connection Reply
Dec 17 12:23:13 netbook pptp[6709]: nm-pptp-service-6697 log[ctrlp_disp:pptp_ctrl.c:773]: Client connection established.
Dec 17 12:23:14 netbook pptp[6709]: nm-pptp-service-6697 log[ctrlp_rep:pptp_ctrl.c:251]: Sent control packet type is 7 'Outgoing-Call-Request'
Dec 17 12:23:14 netbook pptp[6709]: nm-pptp-service-6697 log[ctrlp_disp:pptp_ctrl.c:858]: Received Outgoing Call Reply.
Dec 17 12:23:14 netbook pptp[6709]: nm-pptp-service-6697 log[ctrlp_disp:pptp_ctrl.c:897]: Outgoing call established (call ID 0, peer's call ID 7808).
Dec 17 12:23:14 netbook kernel: [ 9895.484890] Inbound IN=wlan0 OUT= MAC=0c:60:76:1f:c7:8f:00:24:d1:72:51:13:08:00 SRC=173.208.68.58 DST=192.168.0.12 LEN=61 TOS=0x00 PREC=0x00 TTL=54 ID=61356 DF PROTO=47 
Dec 17 12:23:14 netbook kernel: [ 9895.624675] Inbound IN=wlan0 OUT= MAC=0c:60:76:1f:c7:8f:00:24:d1:72:51:13:08:00 SRC=173.208.68.58 DST=192.168.0.12 LEN=60 TOS=0x00 PREC=0x00 TTL=54 ID=61357 DF PROTO=47 
Dec 17 12:23:16 netbook kernel: [ 9898.282657] Inbound IN=wlan0 OUT= MAC=0c:60:76:1f:c7:8f:00:24:d1:72:51:13:08:00 SRC=173.208.68.58 DST=192.168.0.12 LEN=60 TOS=0x00 PREC=0x00 TTL=54 ID=61358 DF PROTO=47 
Dec 17 12:23:17 netbook kernel: [ 9898.525422] Inbound IN=wlan0 OUT= MAC=0c:60:76:1f:c7:8f:00:24:d1:72:51:13:08:00 SRC=173.208.68.58 DST=192.168.0.12 LEN=61 TOS=0x00 PREC=0x00 TTL=54 ID=61359 DF PROTO=47 
Dec 17 12:23:20 netbook kernel: [ 9901.294075] Inbound IN=wlan0 OUT= MAC=0c:60:76:1f:c7:8f:00:24:d1:72:51:13:08:00 SRC=173.208.68.58 DST=192.168.0.12 LEN=60 TOS=0x00 PREC=0x00 TTL=54 ID=61360 DF PROTO=47 
Dec 17 12:23:20 netbook kernel: [ 9901.503061] Inbound IN=wlan0 OUT= MAC=0c:60:76:1f:c7:8f:00:24:d1:72:51:13:08:00 SRC=173.208.68.58 DST=192.168.0.12 LEN=61 TOS=0x00 PREC=0x00 TTL=54 ID=61361 DF PROTO=47 
Dec 17 12:23:22 netbook kernel: [ 9904.285543] Inbound IN=wlan0 OUT= MAC=0c:60:76:1f:c7:8f:00:24:d1:72:51:13:08:00 SRC=173.208.68.58 DST=192.168.0.12 LEN=60 TOS=0x00 PREC=0x00 TTL=54 ID=61362 DF PROTO=47 
Dec 17 12:23:23 netbook kernel: [ 9904.482866] Inbound IN=wlan0 OUT= MAC=0c:60:76:1f:c7:8f:00:24:d1:72:51:13:08:00 SRC=173.208.68.58 DST=192.168.0.12 LEN=61 TOS=0x00 PREC=0x00 TTL=54 ID=61363 DF PROTO=47 
Dec 17 12:23:25 netbook kernel: [ 9907.277823] Inbound IN=wlan0 OUT= MAC=0c:60:76:1f:c7:8f:00:24:d1:72:51:13:08:00 SRC=173.208.68.58 DST=192.168.0.12 LEN=60 TOS=0x00 PREC=0x00 TTL=54 ID=61364 DF PROTO=47 
Dec 17 12:23:26 netbook kernel: [ 9907.482632] Inbound IN=wlan0 OUT= MAC=0c:60:76:1f:c7:8f:00:24:d1:72:51:13:08:00 SRC=173.208.68.58 DST=192.168.0.12 LEN=61 TOS=0x00 PREC=0x00 TTL=54 ID=61365 DF PROTO=47 
Dec 17 12:23:28 netbook kernel: [ 9910.290235] Inbound IN=wlan0 OUT= MAC=0c:60:76:1f:c7:8f:00:24:d1:72:51:13:08:00 SRC=173.208.68.58 DST=192.168.0.12 LEN=60 TOS=0x00 PREC=0x00 TTL=54 ID=61366 DF PROTO=47 
Dec 17 12:23:29 netbook kernel: [ 9910.489436] Inbound IN=wlan0 OUT= MAC=0c:60:76:1f:c7:8f:00:24:d1:72:51:13:08:00 SRC=173.208.68.58 DST=192.168.0.12 LEN=61 TOS=0x00 PREC=0x00 TTL=54 ID=61367 DF PROTO=47 
Dec 17 12:23:30 netbook vpnagent[1560]: Function: tableCallbackHandler File: RouteMgr.cpp Line: 1692 Invoked Function: recv Return Code: 11 (0x0000000B) Description: unknown 
Dec 17 12:23:32 netbook kernel: [ 9913.302561] Inbound IN=wlan0 OUT= MAC=0c:60:76:1f:c7:8f:00:24:d1:72:51:13:08:00 SRC=173.208.68.58 DST=192.168.0.12 LEN=60 TOS=0x00 PREC=0x00 TTL=54 ID=61368 DF PROTO=47 
Dec 17 12:23:32 netbook kernel: [ 9913.493720] Inbound IN=wlan0 OUT= MAC=0c:60:76:1f:c7:8f:00:24:d1:72:51:13:08:00 SRC=173.208.68.58 DST=192.168.0.12 LEN=61 TOS=0x00 PREC=0x00 TTL=54 ID=61369 DF PROTO=47 
Dec 17 12:23:34 netbook kernel: [ 9916.286662] Inbound IN=wlan0 OUT= MAC=0c:60:76:1f:c7:8f:00:24:d1:72:51:13:08:00 SRC=173.208.68.58 DST=192.168.0.12 LEN=60 TOS=0x00 PREC=0x00 TTL=54 ID=61370 DF PROTO=47 
Dec 17 12:23:35 netbook kernel: [ 9916.486576] Inbound IN=wlan0 OUT= MAC=0c:60:76:1f:c7:8f:00:24:d1:72:51:13:08:00 SRC=173.208.68.58 DST=192.168.0.12 LEN=61 TOS=0x00 PREC=0x00 TTL=54 ID=61371 DF PROTO=47 
Dec 17 12:23:37 netbook kernel: [ 9919.286904] Inbound IN=wlan0 OUT= MAC=0c:60:76:1f:c7:8f:00:24:d1:72:51:13:08:00 SRC=173.208.68.58 DST=192.168.0.12 LEN=60 TOS=0x00 PREC=0x00 TTL=54 ID=61372 DF PROTO=47 
Dec 17 12:23:38 netbook kernel: [ 9919.486890] Inbound IN=wlan0 OUT= MAC=0c:60:76:1f:c7:8f:00:24:d1:72:51:13:08:00 SRC=173.208.68.58 DST=192.168.0.12 LEN=61 TOS=0x00 PREC=0x00 TTL=54 ID=61373 DF PROTO=47 
Dec 17 12:23:40 netbook kernel: [ 9922.291218] Inbound IN=wlan0 OUT= MAC=0c:60:76:1f:c7:8f:00:24:d1:72:51:13:08:00 SRC=173.208.68.58 DST=192.168.0.12 LEN=60 TOS=0x00 PREC=0x00 TTL=54 ID=61374 DF PROTO=47 
Dec 17 12:23:41 netbook kernel: [ 9922.487165] Inbound IN=wlan0 OUT= MAC=0c:60:76:1f:c7:8f:00:24:d1:72:51:13:08:00 SRC=173.208.68.58 DST=192.168.0.12 LEN=61 TOS=0x00 PREC=0x00 TTL=54 ID=61375 DF PROTO=47 
Dec 17 12:23:43 netbook pppd[6698]: LCP: timeout sending Config-Requests
Dec 17 12:23:43 netbook pppd[6698]: Connection terminated.
Dec 17 12:23:43 netbook NetworkManager[984]: <warn> VPN plugin failed: 1
Dec 17 12:23:43 netbook avahi-daemon[990]: Withdrawing workstation service for ppp0.
Dec 17 12:23:43 netbook NetworkManager[984]:    SCPlugin-Ifupdown: devices removed (path: /sys/devices/virtual/net/ppp0, iface: ppp0)
Dec 17 12:23:43 netbook pppd[6698]: Modem hangup
Dec 17 12:23:43 netbook pptp[6702]: nm-pptp-service-6697 warn[decaps_hdlc:pptp_gre.c:204]: short read (-1): Input/output error
Dec 17 12:23:43 netbook pptp[6702]: nm-pptp-service-6697 warn[decaps_hdlc:pptp_gre.c:216]: pppd may have shutdown, see pppd log
Dec 17 12:23:43 netbook pptp[6709]: nm-pptp-service-6697 log[callmgr_main:pptp_callmgr.c:234]: Closing connection (unhandled)
Dec 17 12:23:43 netbook pptp[6709]: nm-pptp-service-6697 log[ctrlp_rep:pptp_ctrl.c:251]: Sent control packet type is 12 'Call-Clear-Request'
Dec 17 12:23:43 netbook pptp[6709]: nm-pptp-service-6697 log[call_callback:pptp_callmgr.c:79]: Closing connection (call state)
Dec 17 12:23:43 netbook racoon: INFO: 127.0.0.1[500] used as isakmp port (fd=7)
Dec 17 12:23:43 netbook racoon: INFO: 127.0.0.1[500] used for NAT-T
Dec 17 12:23:43 netbook racoon: INFO: 192.168.0.12[500] used as isakmp port (fd=8)
Dec 17 12:23:43 netbook racoon: INFO: 192.168.0.12[500] used for NAT-T
Dec 17 12:23:43 netbook racoon: INFO: ::1[500] used as isakmp port (fd=9)
Dec 17 12:23:43 netbook racoon: INFO: fe80::e60:76ff:fe1f:c78f%wlan0[500] used as isakmp port (fd=11)
Dec 17 12:23:43 netbook pppd[6698]: Exit.
Dec 17 12:23:43 netbook NetworkManager[984]: <warn> VPN plugin failed: 1
Dec 17 12:23:43 netbook NetworkManager[984]: <warn> VPN plugin failed: 1
Dec 17 12:23:43 netbook NetworkManager[984]: <info> VPN plugin state changed: 6
Dec 17 12:23:43 netbook NetworkManager[984]: <info> VPN plugin state change reason: 0
Dec 17 12:23:43 netbook NetworkManager[984]: <warn> error disconnecting VPN: Could not process the request because no VPN connection was active.
Dec 17 12:23:43 netbook NetworkManager[984]: <info> Policy set 'UPC020762' (wlan0) as default for IPv4 routing and DNS.

---

### Post by Mastermind1980 on 2011-02-27
I'm sorry for bumping a terribly old thread, but I'm having some issues with setting this up in Maverick.

The screenshots that I find everywhere do not comply with what I see on my screen, I have attached an attachment so you can see what I see.

The UltraVPN.crt certificate is there just because it was the only CRT I could find and it wouldn't let me leave it on none, so I just used that one.

Thank you for any help you can give me.

---

