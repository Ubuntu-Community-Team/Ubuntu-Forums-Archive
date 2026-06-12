---
title: "3G connection (VZ BroadbandAccess) won't reconnect?"
date: 2009-04-24
forum: Networking &amp; Wireless
---

### Post by CorporateGoth on 2009-04-24
I have a Verizon BroadbandAccess connection, it uses a sierra wireless card.

When I boot up, it can find it and connect to the network fine (well, 'fine', there is still a bug where Network Manager doesn't let me adjust the lcp-echo-interval and lcp-echo-failure variables, and to connect to BroadbandAccess without getting disconnected, both need to be set to 65535).

However, after I disconnect, I cannot reconnect.  In the log file I *AM* getting an IP address and DNS servers, so the connection to verizon is getting established, but the whole process is just not 'completing', I'm not getting a default route, etc.  The message in the log file is 'Terminating on signal 15', which would indicate NetworkManager decided to kill it.

If I reboot again it will work, but it's a little tedious to reboot all the time to get a network connection back.  WTF is going on?

---

### Post by CorporateGoth on 2009-04-24
As an adendum, restarting networking OR NetworkManager does not help.  So far I literally have to re-boot, no 'soft restart' options I've seen so far helped.  But after reboot, it connects fine.

---

### Post by CorporateGoth on 2009-04-24
Here is the (sanitized) output of daemon.log, and messages:

I've highlighted the most suspicious message.

**daemon.log:**
Apr 24 17:48:58 jekyll NetworkManager: <info>  Activation (ttyUSB0) starting connection 'Verizon BroadbandAccess' 
Apr 24 17:48:58 jekyll NetworkManager: <info>  (ttyUSB0): device state change: 3 -> 4 
Apr 24 17:48:58 jekyll NetworkManager: <info>  Activation (ttyUSB0) Stage 1 of 5 (Device Prepare) scheduled... 
Apr 24 17:48:58 jekyll NetworkManager: <info>  Activation (ttyUSB0) Stage 1 of 5 (Device Prepare) started... 
Apr 24 17:48:58 jekyll NetworkManager: <debug> [1240609738.871224] nm_serial_device_open(): (ttyUSB0) opening device... 
Apr 24 17:48:58 jekyll NetworkManager: <info>  Activation (ttyUSB0) Stage 1 of 5 (Device Prepare) complete. 
Apr 24 17:48:59 jekyll NetworkManager: <info>  (ttyUSB0): powering up... 
Apr 24 17:49:03 jekyll NetworkManager: <info>  Connected, Woo! 
Apr 24 17:49:03 jekyll NetworkManager: <info>  Activation (ttyUSB0) Stage 2 of 5 (Device Configure) scheduled... 
Apr 24 17:49:03 jekyll NetworkManager: <info>  Activation (ttyUSB0) Stage 2 of 5 (Device Configure) starting... 
Apr 24 17:49:03 jekyll NetworkManager: <info>  (ttyUSB0): device state change: 4 -> 5 
Apr 24 17:49:03 jekyll NetworkManager: <info>  Starting pppd connection 
Apr 24 17:49:03 jekyll NetworkManager: <debug> [1240609743.982463] nm_ppp_manager_start(): Command line: /usr/sbin/pppd nodetach lock nodefaultroute user [email]----------@vzw3g.com[/email] ttyUSB0 noipdefault noauth refuse-eap refuse-mschap refuse-mschap-v2 crtscts usepeerdns lcp-echo-failure 65535 lcp-echo-interval 65535 ipparam /org/freedesktop/NetworkManager/PPP/4 plugin /usr/lib/pppd/2.4.4/nm-pppd-plugin.so 
Apr 24 17:49:04 jekyll NetworkManager: <debug> [1240609744.007973] nm_ppp_manager_start(): ppp started with pid 15342 
Apr 24 17:49:04 jekyll NetworkManager: <info>  Activation (ttyUSB0) Stage 2 of 5 (Device Configure) complete. 
**Apr 24 17:49:19 jekyll NetworkManager: <WARN>  pppd_timed_out(): Looks like pppd didn't initialize our dbus module **
pr 24 17:49:19 jekyll NetworkManager: <info>  (ttyUSB0): device state change: 5 -> 9 
Apr 24 17:49:19 jekyll NetworkManager: <debug> [1240609759.002210] nm_serial_device_close(): Closing device 'ttyUSB0' 
Apr 24 17:49:19 jekyll NetworkManager: <info>  Marking connection 'Verizon BroadbandAccess' invalid. 
Apr 24 17:49:19 jekyll NetworkManager: <info>  Activation (ttyUSB0) failed. 
Apr 24 17:49:19 jekyll NetworkManager: <info>  (ttyUSB0): device state change: 9 -> 3 
Apr 24 17:49:19 jekyll NetworkManager: <info>  (ttyUSB0): deactivating device (reason: 0). 
Apr 24 17:49:19 jekyll NetworkManager: nm_system_device_flush_ip4_routes_with_iface: assertion `iface_idx >= 0' failed
Apr 24 17:49:19 jekyll NetworkManager: nm_system_device_flush_ip4_addresses_with_iface: assertion `iface_idx >= 0' failed
Apr 24 17:49:20 jekyll NetworkManager: <debug> [1240609761.000994] ensure_killed(): waiting for ppp pid 15342 to exit 
Apr 24 17:49:20 jekyll NetworkManager: <debug> [1240609761.001124] ensure_killed(): ppp pid 15342 cleaned up 


**messages:**
Apr 24 17:49:04 jekyll pppd[15342]: Plugin /usr/lib/pppd/2.4.4/nm-pppd-plugin.so loaded.
Apr 24 17:49:04 jekyll pppd[15342]: pppd 2.4.5 started by root, uid 0
Apr 24 17:49:04 jekyll pppd[15342]: Using interface ppp0
Apr 24 17:49:04 jekyll pppd[15342]: Connect: ppp0 <--> /dev/ttyUSB0
Apr 24 17:49:04 jekyll pppd[15342]: local  IP address XXX.XXX.XXX.XXX
Apr 24 17:49:04 jekyll pppd[15342]: remote IP address XXX.XXX.XXX.XXX
Apr 24 17:49:04 jekyll pppd[15342]: primary   DNS address XXX.XXX.XXX.XXX
Apr 24 17:49:04 jekyll pppd[15342]: secondary DNS address XXX.XXX.XXX.XXX
Apr 24 17:49:19 jekyll pppd[15342]: Terminating on signal 15
Apr 24 17:49:19 jekyll pppd[15342]: Connect time 0.3 minutes.
Apr 24 17:49:19 jekyll pppd[15342]: Sent 0 bytes, received 0 bytes.
Apr 24 17:49:19 jekyll pppd[15342]: Connection terminated.
Apr 24 17:49:20 jekyll pppd[15342]: Exit.


If I manually invoke pppd call ppp0 (where the peer entry for ppp0 looks like):
/dev/ttyUSB0
115200
user "---------@vzw3g.com"
usepeerdns
defaultroute
noauth
show-password
crtscts
lock
persist
lcp-echo-failure 65535
lcp-echo-interval 65535


Then everything works fine - and given the fact that it looks like the pppd part of things, at least up to and including IP acquisition and such looks to be working using NetworkManager, I think this is a NetworkManager problem mainly.

Anyone have ANY insight on what might be causing this?  To repeat earlier, the FIRST time I make a connection to the 3G network after boot, it DOES succeed.  It's just subsequent ones fail.

---

