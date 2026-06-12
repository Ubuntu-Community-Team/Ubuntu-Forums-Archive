---
title: "issue with vpnc to cisco vpn in 10.04"
date: 2010-05-08
forum: Networking &amp; Wireless
---

### Post by flitclicker on 2010-05-08
Hi. Thanks for any help with this one:

I installed 10.04 and the first thing i needed to do was connect to my company's cisco VPN.

Not really knowing where to start, I had a google, and followed [these]("http://www.ubuntugeek.com/how-to-setup-cisco-vpn-using-vpnc-ubuntu-jaunty-9-04.html") ([http://www.ubuntugeek.com/how-to-setup-cisco-vpn-using-vpnc-ubuntu-jaunty-9-04.html](http://www.ubuntugeek.com/how-to-setup-cisco-vpn-using-vpnc-ubuntu-jaunty-9-04.html))
instructions, using  the .pcf file I'd been using on Windows.

It looked to have worked a treat: starting from the console I could then RDP through the tunnel and work fine.

However it drops the connection after about ten minutes.

I then found out about network-manager-vpnc, so installed that from the synaptic package manager in ubuntu.  Following a reboot I got that to work fine, so now I could connect from the NM icon without having to open a terminal.  Nice, but still drops after a few minutes.  This method at least gives me a message saying "VPN connection failed".

I've had a good search around but cant find anything which helps.  I could work round it, but after the VPN tunnel is removed, the RDP client hangs (if I use it in full screen I cant exit at all) and ubuntu becomes unresponsive for a few minutes. 

From the syslog, it seems tun0 gets removed, but I dont know why.

Any assistance much appreciated, I dont want to go back to Windows!

Thanks.


Log:

> May  8 08:47:02 jon-laptop NetworkManager: <info>  DHCP: device wlan0 state changed (null) -> preinit
May  8 08:47:02 jon-laptop dhclient: Listening on LPF/wlan0/00:19:d2:01:70:c8
May  8 08:47:02 jon-laptop dhclient: Sending on   LPF/wlan0/00:19:d2:01:70:c8
May  8 08:47:02 jon-laptop dhclient: Sending on   Socket/fallback
May  8 08:47:03 jon-laptop dhclient: DHCPREQUEST of 10.0.0.109 on wlan0 to 255.255.255.255 port 67
May  8 08:47:03 jon-laptop dhclient: DHCPACK of 10.0.0.109 from 10.0.0.1
May  8 08:47:03 jon-laptop NetworkManager: <info>  DHCP: device wlan0 state changed preinit -> reboot
May  8 08:47:03 jon-laptop NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP4 Configure Get) scheduled...
May  8 08:47:03 jon-laptop NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP4 Configure Get) started...
May  8 08:47:03 jon-laptop NetworkManager: <info>    address 10.0.0.109
May  8 08:47:03 jon-laptop NetworkManager: <info>    prefix 24 (255.255.255.0)
May  8 08:47:03 jon-laptop NetworkManager: <info>    gateway 10.0.0.1
May  8 08:47:03 jon-laptop NetworkManager: <info>    nameserver 'xxx.xxx.x.xxx'
May  8 08:47:03 jon-laptop NetworkManager: <info>    nameserver 'xxx.xxx.xx.xxx'
May  8 08:47:03 jon-laptop NetworkManager: <info>  Activation (wlan0) Stage 5 of 5 (IP Configure Commit) scheduled...
May  8 08:47:03 jon-laptop NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP4 Configure Get) complete.
May  8 08:47:03 jon-laptop NetworkManager: <info>  Activation (wlan0) Stage 5 of 5 (IP Configure Commit) started...
May  8 08:47:03 jon-laptop avahi-daemon[749]: Joining mDNS multicast group on interface wlan0.IPv4 with address 10.0.0.109.
May  8 08:47:03 jon-laptop avahi-daemon[749]: New relevant interface wlan0.IPv4 for mDNS.
May  8 08:47:03 jon-laptop avahi-daemon[749]: Registering new address record for 10.0.0.109 on wlan0.IPv4.
May  8 08:47:03 jon-laptop dhclient: bound to 10.0.0.109 -- renewal in 41112 seconds.
May  8 08:47:04 jon-laptop NetworkManager: <info>  (wlan0): writing resolv.conf to /sbin/resolvconf
May  8 08:47:04 jon-laptop NetworkManager: <info>  (wlan0): device state change: 7 -> 8 (reason 0)
May  8 08:47:04 jon-laptop NetworkManager: <info>  (wlan0): writing resolv.conf to /sbin/resolvconf
May  8 08:47:04 jon-laptop NetworkManager: <info>  Policy set 'monkey' (wlan0) as default for routing and DNS.
May  8 08:47:04 jon-laptop NetworkManager: <info>  Activation (wlan0) successful, device activated.
May  8 08:47:04 jon-laptop NetworkManager: <info>  Activation (wlan0) Stage 5 of 5 (IP Configure Commit) complete.
May  8 08:47:04 jon-laptop ntpdate[1357]: adjust time server 91.189.94.4 offset -0.357614 sec
May  8 08:47:06 jon-laptop anacron[1393]: Anacron 2.3 started on 2010-05-08
May  8 08:47:06 jon-laptop anacron[1393]: Normal exit (0 jobs run)
May  8 08:47:09 jon-laptop kernel: [   61.388027] wlan0: no IPv6 routers present
May  8 08:47:35 jon-laptop NetworkManager: <info>  Starting VPN service 'org.freedesktop.NetworkManager.vpnc'...
May  8 08:47:35 jon-laptop NetworkManager: <info>  VPN service 'org.freedesktop.NetworkManager.vpnc' started (org.freedesktop.NetworkManager.vpnc), PID 1408
May  8 08:47:35 jon-laptop NetworkManager: <info>  VPN service 'org.freedesktop.NetworkManager.vpnc' just appeared, activating connections
May  8 08:47:35 jon-laptop NetworkManager: <info>  VPN plugin state changed: 3
May  8 08:47:35 jon-laptop NetworkManager: <info>  VPN connection 'SI' (Connect) reply received.
May  8 08:47:35 jon-laptop NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/tun0, iface: tun0)
May  8 08:47:35 jon-laptop NetworkManager:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/tun0, iface: tun0): no ifupdown configuration found.
May  8 08:47:35 jon-laptop kernel: [   87.816554] tun0: Disabled Privacy Extensions
May  8 08:47:36 jon-laptop NetworkManager: <info>  VPN connection 'SI' (IP Config Get) reply received.
May  8 08:47:36 jon-laptop NetworkManager: <info>  VPN Gateway: xxx.xxx.xxx.xxx
May  8 08:47:36 jon-laptop NetworkManager: <info>  Tunnel Device: tun0
May  8 08:47:36 jon-laptop NetworkManager: <info>  Internal IP4 Address: 172.20.1.62
May  8 08:47:36 jon-laptop NetworkManager: <info>  Internal IP4 Prefix: 24
May  8 08:47:36 jon-laptop NetworkManager: <info>  Internal IP4 Point-to-Point Address: 172.20.1.62
May  8 08:47:36 jon-laptop NetworkManager: <info>  Maximum Segment Size (MSS): 0
May  8 08:47:36 jon-laptop NetworkManager: <info>  Static Route: 172.20.1.0/24   Next Hop: 172.20.1.0
May  8 08:47:36 jon-laptop NetworkManager: <info>  Static Route: 172.20.0.0/24   Next Hop: 172.20.0.0
May  8 08:47:36 jon-laptop NetworkManager: <info>  DNS Domain: '(none)'
May  8 08:47:36 jon-laptop NetworkManager: <info>  Login Banner:
May  8 08:47:36 jon-laptop NetworkManager: <info>  -----------------------------------------
May  8 08:47:36 jon-laptop NetworkManager: <info>  Welcome to VPN. Authorised users only#012
May  8 08:47:36 jon-laptop NetworkManager: <info>  -----------------------------------------
May  8 08:47:36 jon-laptop vpnc[1413]: can't open pidfile /var/run/vpnc/pid for writing
May  8 08:47:37 jon-laptop NetworkManager: <info>  (tun0): writing resolv.conf to /sbin/resolvconf
May  8 08:47:37 jon-laptop NetworkManager: <info>  VPN connection 'SI' (IP Config Get) complete.
May  8 08:47:37 jon-laptop NetworkManager: <info>  (wlan0): writing resolv.conf to /sbin/resolvconf
May  8 08:47:37 jon-laptop NetworkManager: <info>  Policy set 'monkey' (wlan0) as default for routing and DNS.
May  8 08:47:37 jon-laptop NetworkManager: <info>  VPN plugin state changed: 4
May  8 08:47:37 jon-laptop ntpdate[1444]: adjust time server 91.189.94.4 offset -0.341756 sec
May  8 08:47:43 jon-laptop AptDaemon: INFO: Initializing daemon
May  8 08:50:29 jon-laptop kernel: [  260.965070] CE: hpet increasing min_delta_ns to 15000 nsec
May  8 08:53:43 jon-laptop AptDaemon: INFO: Quiting due to inactivity
May  8 08:53:43 jon-laptop AptDaemon: INFO: Shutdown was requested
May  8 08:58:00 jon-laptop kernel: [  712.793071] CE: hpet increasing min_delta_ns to 22500 nsec
May  8 09:04:31 jon-laptop NetworkManager:    SCPlugin-Ifupdown: devices removed (path: /sys/devices/virtual/net/tun0, iface: tun0)
May  8 09:04:31 jon-laptop NetworkManager: <info>  VPN plugin failed: 1
May  8 09:04:31 jon-laptop NetworkManager: <info>  VPN plugin state changed: 6
May  8 09:04:31 jon-laptop NetworkManager: <info>  VPN plugin state change reason: 0
May  8 09:04:31 jon-laptop NetworkManager: <WARN>  connection_state_changed(): Could not process the request because no VPN connection was active.
May  8 09:04:31 jon-laptop NetworkManager: <info>  (tun0): writing resolv.conf to /sbin/resolvconf
May  8 09:04:32 jon-laptop NetworkManager: <info>  (wlan0): writing resolv.conf to /sbin/resolvconf
May  8 09:04:32 jon-laptop NetworkManager: <info>  Policy set 'monkey' (wlan0) as default for routing and DNS.
May  8 09:04:45 jon-laptop NetworkManager: <debug> [1273305885.002165] ensure_killed(): waiting for vpn service pid 1408 to exit
May  8 09:04:45 jon-laptop NetworkManager: <debug> [1273305885.002317] ensure_killed(): vpn service pid 1408 cleaned up
May  8 09:14:49 jon-laptop kernel: [ 1721.421070] CE: hpet increasing min_delta_ns to 33750 nsec

---

### Post by flitclicker on 2010-05-10
P.S. I have set dpd-idle to 0 via command line and also via the dpd-idle timeout (0) option in the conf file - but neither makes a difference.
 
I am starting to think that the problem is not VPNC itself, but something network manager is doing periodically which inadvertently tears down the VPN (tun0).

---

### Post by flitclicker on 2010-05-11
Just checked (hadnt thought to till now) and the problem occurs regardless of whether I'm on wireless or cable ethernet.

Any suggestions much appreciated.

---

### Post by flitclicker on 2010-05-12
Tried tun vs tap connection - same thing.
Tried NAT traversal option - no change.
 
Pulling my hair out here! is anyone able to give me any pointers?

---

### Post by iponeverything on 2010-05-12
maybe:

[http://www.lamnk.com/blog/vpn/how-to-install-cisco-vpn-client-on-ubuntu-jaunty-jackalope-and-karmic-koala-64-bit/](http://www.lamnk.com/blog/vpn/how-to-install-cisco-vpn-client-on-ubuntu-jaunty-jackalope-and-karmic-koala-64-bit/)

from here:
[http://art.ubuntuforums.org/showthread.php?p=8237373](http://art.ubuntuforums.org/showthread.php?p=8237373)

---

### Post by flitclicker on 2010-05-12
Thanks for the tip, I hadn't seen that one.

However I'm not getting compile problems or crashes; it runs perfectly apart from it just drops the connection after 17 minutes.

I am using a dual core so did switch off one CPU, but that didnt solve the problem. So I dont think I have the same problem.

Cheers, though, for helping.

---

### Post by spotrick on 2010-05-14
I don't have an answer, but I can offer a "me too". :/

I've had this issue since 8.10 and I feel like I've tried everything, including alternatives to vpnc.

I'm not convinced it's a timeout issue, because I have DPD set to 0, but also I find that sometimes, if I wait long enough, I get some action from the remote host, before it "dies" again. (I'm basically running ssh to a server inside a firewall.)

Have you tried waiting on a connection to see if it eventually starts working again?

But pretty much I've been forced to do my support work through Vista, which hurts.

---

### Post by flitclicker on 2010-05-14
Glad I'm not the only one!

Interesting question about leaving it to see whether anything returns.  I know it doesnt work if I start the VPN via network-manager-vpnc, because the little padlock icon disappears from the network connection and doesnt return. But I might try again from the command line (which appears to hang rather then terminating).

Will let you know.  Does your connection fail at random intervals? Mine always dies at about 17 minutes.

---

### Post by flitclicker on 2010-05-19
Mine never regains any sort of connection.  

Stumped.

---

### Post by will81 on 2010-05-23
I have a similar issue, or perhaps the same one.

Connecting from the command line with my own .conf file is fine.

Connecting using NetworkManager works as long as the box I do NOT tick the box allowing the connecting to be shared with other users.  I have had some issues with things seeming to die after a period of time but I was doing other things and I don't know whether this is related to the OP's 17-minute problem.

Connecting using NetworkManager fails if I HAVE ticked the box allowing the connection to be shared with other users.  Syslog shows something like (I'm not on the same machine so can't copy and paste):

> NetworkManager: <info> Starting VPN service 'org.free[...]
NetworkManager: <info> VPN service 'org.free[...]' started, PID nnnn
NetworkManager: <info> VPN service 'org.free[...]' just appeared, activating connections
NetworkManager: <info> VPN plugin state changed: 1
NetworkManager: <info> VPN plugin state changed: 3
NetworkManager: <info> VPN connection 'connection-name' (Connect) reply received.
NetworkManager: <info> VPN plugin failed: 1
NetworkManager: <info> VPN plugin state changed: 6
NetworkManager: <info> VPN plugin state change reason: 0
NetworkManager: <WARN> connection_state_changed(): Could not process the request because no VPN connection was active.
NetworkManager: <info> (eth1): writing resolve.conf to /sbin/resolvconf

I thought this was the DBus permissions error (Google: vpnc dbus) but I've applied the patch and restarted to no avail.  Not sure where to go from here.

I could just use little shell scripts attached to launchers but the NetworkManager icon is so much neater.  I'm introducing Ubuntu at work and it's very much a hearts and minds campaign!

---

### Post by thauta on 2010-06-01
Another poor soul here trying to get this vpnc working for more than a few minutes. My platform is a 64-bit 10.04 with dual-core enabled.

A rumour I heard was that the problem is related to re-keying between the server and the client. Meaning that the client would be missing some functionality to switch keys during the session (based on timeouts or amount of bytes transferred etc?).

I'll try to dig deeper into this...

---

### Post by LaMooNa on 2010-10-17
I just installed vpnc components from Synaptic Package manager, then you need to restart your computer. then configure your cisco vpn connection and it should work.
it works fine with me

---

### Post by flitclicker on 2010-10-22
Well, I had been using hamachi instead, but as I've just been told to remove it from the server :-\" I'll give VPNC another go and let you know.  Maybe there's been an update..

---

### Post by flitclicker on 2010-10-22
...and it's exactly the same - about 20 mins in, the VPN fails.

---

### Post by tram4 on 2010-10-29
I had a similar issue.  Try disabling "dead peer detection".  I had to do this for one of my connections and also change the encryption to "weak" for it to remain stable.

---

### Post by gnicko on 2010-11-02
Sorry...don't have any solutions or fixes, but I do have what seems to be similar.

I'm using vpnc/network-manager set up on Xubuntu but I've seen the same behavior with Fedora, Debian, etc.

I can only make a connection every other time I try. The first attempt fails, the second works fine (but sometimes drops after a few minutes), the third fails, the forth seems to work fine...and so on...

I've checked with the sys admins. at work and they assure me that the issue isn't caused by anything on their end (I take it with a grain of salt) 

If this sounds familiar to anyone I'd sure like to hear about it and if you have a fix, I'd really appreciate it.

Thanks!

---

