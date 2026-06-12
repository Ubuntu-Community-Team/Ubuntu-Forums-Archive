---
title: "VPN Connections appear to be using the wrong interface"
date: 2009-10-07
forum: Networking &amp; Wireless
---

### Post by the_dark_light on 2009-10-07
I'm trying to connect a Netbook running 9.04 (Desktop) to my VPN.  VPN is running PopTop to provide PPTP

I've managed to get another laptop running 9.04 to connect, all the options on network manager are the same (So I can't for the life of me remember how I did this).

When I try to connect the netbook I get the connection failed (timed out) message.  As I say the PPTP options in network manager are identical on both machines.

tail /var/log/messages revealed:

eth0: link is not ready

Does this mean that PPP is trying to connect using the wired interface eth0, if this is the case how do I tell it to use the wireless interface?

---

### Post by the_dark_light on 2009-10-08
An update, here is the output from /var/log/messages on the laptop that does connect:

dan@dan-laptop:~$ tail /var/log/messages
Oct  8 22:02:52 dan-laptop kernel: [111744.688519] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Oct  8 22:03:01 dan-laptop kernel: [111753.368018] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
Oct  8 22:03:23 dan-laptop pppd[15767]: Plugin /usr/lib/pppd/2.4.5//nm-pptp-pppd-plugin.so loaded.
Oct  8 22:03:23 dan-laptop pppd[15767]: pppd 2.4.5 started by root, uid 0
Oct  8 22:03:23 dan-laptop pppd[15767]: Using interface ppp0
Oct  8 22:03:23 dan-laptop pppd[15767]: Connect: ppp0 <--> /dev/pts/0
Oct  8 22:03:24 dan-laptop pppd[15767]: CHAP authentication succeeded
Oct  8 22:03:24 dan-laptop pppd[15767]: MPPE 128-bit stateless compression enabled
Oct  8 22:03:24 dan-laptop pppd[15767]: local  IP address 192.168.1.60
Oct  8 22:03:24 dan-laptop pppd[15767]: remote IP address 192.168.1.50

The following is produced on the netbook:

dan@dan-netbook:~$ tail /var/log/messages
Oct  8 23:02:28 dan-netbook kernel: [   22.981918] Bridge firewalling registered
Oct  8 23:02:30 dan-netbook kernel: [   24.703831] [drm] Initialized drm 1.1.0 20060810
Oct  8 23:02:30 dan-netbook kernel: [   24.811447] ppdev: user-space parallel port driver
Oct  8 23:02:34 dan-netbook kernel: [   28.336791] ADDRCONF(NETDEV_UP): eth0: link is not ready
Oct  8 23:02:37 dan-netbook kernel: [   31.628986] hda-intel: IRQ timing workaround is activated for card #0. Suggest a bigger bdl_pos_adj.
Oct  8 23:04:21 dan-netbook pppd[3258]: Plugin /usr/lib/pppd/2.4.5//nm-pptp-pppd-plugin.so loaded.
Oct  8 23:04:22 dan-netbook pppd[3258]: pppd 2.4.5 started by root, uid 0
Oct  8 23:04:22 dan-netbook pppd[3258]: Using interface ppp0
Oct  8 23:04:22 dan-netbook pppd[3258]: Connect: ppp0 <--> /dev/pts/0
Oct  8 23:04:23 dan-netbook pppd[3258]: CHAP authentication succeeded
dan@dan-netbook:~$ 

Can anyone advise what's going on here?

---

