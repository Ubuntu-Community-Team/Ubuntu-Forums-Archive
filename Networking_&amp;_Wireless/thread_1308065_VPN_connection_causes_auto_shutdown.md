---
title: "VPN connection causes auto shutdown"
date: 2009-10-31
forum: Networking &amp; Wireless
---

### Post by pgngp on 2009-10-31
I have an unusual problem. When I connect to my company network using the Cisco VPN client (v. 4.8.02) on my Dell Latitude E6400 laptop with Ubuntu 9.04, after some time the computer shuts off automatically. 

For example, I first connected to my company network using the VPN client and then tried to synchronize email messages in Evolution Mail. While Evolution Mail was synchronizing, my laptop shut down abruptly. 

In another instance, I connected to the remote network using the VPN client and then tried some google searches, and then all of a sudden the laptop shut down. 

I extracted the log messages that are logged just before the computer is abruptly shut down:

Oct 30 21:25:45 pgupta-laptop kernel: [ 1828.594323] input: HID 413c:8158 as /devices/pci0000:00/0000:00:1a.0/usb3/3-1/3-1.2/3-1.2:1.0/input/input13
Oct 30 21:25:45 pgupta-laptop kernel: [ 1828.676126] generic-usb 0003:413C:8158.0004: input,hidraw1: USB HID v1.11 Mouse [HID 413c:8158] on usb-0000:00:1a.0-1.2/input0
Oct 30 21:25:45 pgupta-laptop kernel: [ 1829.101779] 0000:00:19.0: eth0: Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
Oct 30 21:25:45 pgupta-laptop kernel: [ 1829.101782] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
Oct 30 21:25:45 pgupta-laptop kernel: [ 1829.101953] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
Oct 30 21:25:54 pgupta-laptop kernel: [ 1838.347019] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
Oct 30 21:29:34 pgupta-laptop kernel: [ 2058.043758] compiz.real[3748]: segfault at 4 ip b74c75bb sp bfce9470 error 4 in libGLcore.so.180.44[b6ab3000+d1a000]
Oct 30 21:29:39 pgupta-laptop bonobo-activation-server (pgupta-7259): could not associate with desktop session: Failed to connect to socket /tmp/dbus-iclURp4XJX: Connection refused
Oct 30 21:29:40 pgupta-laptop exiting on signal 15



Oct 30 21:31:11 pgupta-laptop kernel: [   19.132742] ADDRCONF(NETDEV_UP): eth0: link is not ready
Oct 30 21:31:11 pgupta-laptop kernel: [   19.133367] iwlagn 0000:0c:00.0: firmware: requesting iwlwifi-5000-1.ucode
Oct 30 21:31:11 pgupta-laptop kernel: [   20.056410] Registered led device: iwl-phy0:radio
Oct 30 21:31:11 pgupta-laptop kernel: [   20.056424] Registered led device: iwl-phy0:assoc
Oct 30 21:31:11 pgupta-laptop kernel: [   20.056436] Registered led device: iwl-phy0:RX
Oct 30 21:31:11 pgupta-laptop kernel: [   20.056448] Registered led device: iwl-phy0:TX
Oct 30 21:31:12 pgupta-laptop kernel: [   20.793857] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Oct 30 21:31:12 pgupta-laptop kernel: [   20.884815] 0000:00:19.0: eth0: Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
Oct 30 21:31:12 pgupta-laptop kernel: [   20.884818] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
Oct 30 21:31:12 pgupta-laptop kernel: [   20.885002] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
Oct 30 21:31:14 pgupta-laptop kernel: [   22.362075] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
Oct 30 21:31:40 pgupta-laptop exiting on signal 15



Oct 30 21:36:34 pgupta-laptop kernel: [   19.128736] ADDRCONF(NETDEV_UP): eth0: link is not ready
Oct 30 21:36:34 pgupta-laptop kernel: [   19.129359] iwlagn 0000:0c:00.0: firmware: requesting iwlwifi-5000-1.ucode
Oct 30 21:36:34 pgupta-laptop kernel: [   19.492701] Registered led device: iwl-phy0:radio
Oct 30 21:36:34 pgupta-laptop kernel: [   19.492715] Registered led device: iwl-phy0:assoc
Oct 30 21:36:34 pgupta-laptop kernel: [   19.492727] Registered led device: iwl-phy0:RX
Oct 30 21:36:34 pgupta-laptop kernel: [   19.492739] Registered led device: iwl-phy0:TX
Oct 30 21:36:34 pgupta-laptop kernel: [   19.501845] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Oct 30 21:36:35 pgupta-laptop kernel: [   20.764817] 0000:00:19.0: eth0: Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
Oct 30 21:36:35 pgupta-laptop kernel: [   20.764820] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
Oct 30 21:36:35 pgupta-laptop kernel: [   20.764992] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
Oct 30 21:36:36 pgupta-laptop kernel: [   21.074570] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
Oct 30 21:37:16 pgupta-laptop kernel: [   61.836811] hda-intel: IRQ timing workaround is activated for card #0. Suggest a bigger bdl_pos_adj.
Oct 30 21:37:35 pgupta-laptop kernel: [   81.000404] Clocksource tsc unstable (delta = -218487538 ns)
Oct 30 21:39:57 pgupta-laptop bonobo-activation-server (pgupta-4084): could not associate with desktop session: Failed to connect to socket /tmp/dbus-gc8afDxUCd: Connection refused
Oct 30 21:39:58 pgupta-laptop exiting on signal 15



Oct 30 22:34:03 pgupta-laptop kernel: [   19.129743] ADDRCONF(NETDEV_UP): eth0: link is not ready
Oct 30 22:34:03 pgupta-laptop kernel: [   19.130384] iwlagn 0000:0c:00.0: firmware: requesting iwlwifi-5000-1.ucode
Oct 30 22:34:04 pgupta-laptop kernel: [   20.091446] Registered led device: iwl-phy0:radio
Oct 30 22:34:04 pgupta-laptop kernel: [   20.091458] Registered led device: iwl-phy0:assoc
Oct 30 22:34:04 pgupta-laptop kernel: [   20.091470] Registered led device: iwl-phy0:RX
Oct 30 22:34:04 pgupta-laptop kernel: [   20.091481] Registered led device: iwl-phy0:TX
Oct 30 22:34:04 pgupta-laptop kernel: [   20.316824] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Oct 30 22:34:05 pgupta-laptop kernel: [   21.946159] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
Oct 30 22:35:03 pgupta-laptop kernel: [   79.500080] Clocksource tsc unstable (delta = -294389037 ns)
Oct 30 22:41:48 pgupta-laptop bonobo-activation-server (pgupta-4453): could not associate with desktop session: Failed to connect to socket /tmp/dbus-XTIp6W73Ty: Connection refused
Oct 30 22:41:50 pgupta-laptop exiting on signal 15



Oct 30 22:49:14 pgupta-laptop kernel: [   19.129741] ADDRCONF(NETDEV_UP): eth0: link is not ready
Oct 30 22:49:14 pgupta-laptop kernel: [   19.130374] iwlagn 0000:0c:00.0: firmware: requesting iwlwifi-5000-1.ucode
Oct 30 22:49:14 pgupta-laptop kernel: [   19.947247] Registered led device: iwl-phy0:radio
Oct 30 22:49:14 pgupta-laptop kernel: [   19.947261] Registered led device: iwl-phy0:assoc
Oct 30 22:49:14 pgupta-laptop kernel: [   19.947273] Registered led device: iwl-phy0:RX
Oct 30 22:49:14 pgupta-laptop kernel: [   19.947284] Registered led device: iwl-phy0:TX
Oct 30 22:49:14 pgupta-laptop kernel: [   19.984777] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Oct 30 22:49:16 pgupta-laptop kernel: [   21.650895] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
Oct 30 22:49:28 pgupta-laptop kernel: [   33.360924] hda-intel: IRQ timing workaround is activated for card #0. Suggest a bigger bdl_pos_adj.
Oct 30 22:50:12 pgupta-laptop kernel: [   77.500037] Clocksource tsc unstable (delta = -151840300 ns)
Oct 30 22:54:30 pgupta-laptop kernel: [  335.108024] CE: hpet increasing min_delta_ns to 15000 nsec
Oct 30 22:58:43 pgupta-laptop kernel: [  588.894402] Cisco Systems VPN Client Version 4.8.02 (0030) kernel module loaded
Oct 30 23:09:07 pgupta-laptop -- MARK --
Oct 30 23:28:44 pgupta-laptop kernel: [ 2389.816269] CE: hpet increasing min_delta_ns to 22500 nsec



Oct 30 23:41:54 pgupta-laptop kernel: [   21.453750] ADDRCONF(NETDEV_UP): eth0: link is not ready
Oct 30 23:41:54 pgupta-laptop kernel: [   21.454389] iwlagn 0000:0c:00.0: firmware: requesting iwlwifi-5000-1.ucode
Oct 30 23:41:54 pgupta-laptop kernel: [   22.055442] Registered led device: iwl-phy0:radio
Oct 30 23:41:54 pgupta-laptop kernel: [   22.055456] Registered led device: iwl-phy0:assoc
Oct 30 23:41:54 pgupta-laptop kernel: [   22.055468] Registered led device: iwl-phy0:RX
Oct 30 23:41:54 pgupta-laptop kernel: [   22.055482] Registered led device: iwl-phy0:TX
Oct 30 23:41:55 pgupta-laptop kernel: [   22.395061] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Oct 30 23:41:56 pgupta-laptop kernel: [   24.022237] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
Oct 30 23:42:07 pgupta-laptop kernel: [   35.283856] hda-intel: IRQ timing workaround is activated for card #0. Suggest a bigger bdl_pos_adj.
Oct 30 23:42:53 pgupta-laptop kernel: [   81.000247] Clocksource tsc unstable (delta = -133228667 ns)
Oct 30 23:46:41 pgupta-laptop kernel: [  308.688682] Cisco Systems VPN Client Version 4.8.02 (0030) kernel module loaded


Oct 31 00:00:43 pgupta-laptop kernel: [   20.132735] ADDRCONF(NETDEV_UP): eth0: link is not ready
Oct 31 00:00:43 pgupta-laptop kernel: [   20.133360] iwlagn 0000:0c:00.0: firmware: requesting iwlwifi-5000-1.ucode
Oct 31 00:00:43 pgupta-laptop kernel: [   20.602571] Registered led device: iwl-phy0:radio
Oct 31 00:00:43 pgupta-laptop kernel: [   20.602584] Registered led device: iwl-phy0:assoc
Oct 31 00:00:43 pgupta-laptop kernel: [   20.602596] Registered led device: iwl-phy0:RX
Oct 31 00:00:43 pgupta-laptop kernel: [   20.602608] Registered led device: iwl-phy0:TX
Oct 31 00:00:43 pgupta-laptop kernel: [   20.906699] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Oct 31 00:00:45 pgupta-laptop kernel: [   22.472304] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
Oct 31 00:01:41 pgupta-laptop kernel: [   79.000244] Clocksource tsc unstable (delta = -267975302 ns)
Oct 31 00:03:27 pgupta-laptop kernel: [  184.645044] CE: hpet increasing min_delta_ns to 15000 nsec
Oct 31 00:11:52 pgupta-laptop kernel: [  689.526671] Cisco Systems VPN Client Version 4.8.02 (0030) kernel module loaded


I would really appreciate any help in this regard. Thank you in advance!

---

### Post by pgngp on 2009-11-03
Solved! 

With the help of [http://www.lamnk.com/blog/vpn/how-to-install-cisco-vpn-client-on-ubuntu-jaunty-jackalope-and-karmic-koala-64-bit/]("http://www.lamnk.com/blog/vpn/how-to-install-cisco-vpn-client-on-ubuntu-jaunty-jackalope-and-karmic-koala-64-bit/"), I was able to solve this issue. Apparently, the problem was the dual cores on my laptop. When I disabled one of the cores, the VPN connection worked fine, without abruptly shutting down my computer.

---

