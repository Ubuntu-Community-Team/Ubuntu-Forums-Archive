---
title: "Lost usbnet asix connection after upgrade to kernel 2.6.32-23-server"
date: 2010-07-02
forum: Networking &amp; Wireless
---

### Post by justforsp on 2010-07-02
After I upgrade my system to kernel 2.6.32-23-server, asix driver doesn't load anymore
dmesg:
[  100.561250] usb 1-6: USB disconnect, address 3
[  102.350030] usb 1-6: new high speed USB device using ehci_hcd and address 4
[  102.517088] usb 1-6: configuration #1 chosen from 1 choice
[  102.528453] asix: disagrees about version of symbol usbnet_set_msglevel
[  102.528462] asix: Unknown symbol usbnet_set_msglevel
[  102.529619] asix: disagrees about version of symbol usbnet_change_mtu
[  102.529625] asix: Unknown symbol usbnet_change_mtu
[  102.530007] asix: disagrees about version of symbol usbnet_unlink_rx_urbs
[  102.530012] asix: Unknown symbol usbnet_unlink_rx_urbs
[  102.530321] asix: disagrees about version of symbol usbnet_get_msglevel
[  102.530327] asix: Unknown symbol usbnet_get_msglevel
[  102.530810] asix: disagrees about version of symbol usbnet_open
[  102.530815] asix: Unknown symbol usbnet_open
[  102.531058] asix: disagrees about version of symbol usbnet_skb_return
[  102.531063] asix: Unknown symbol usbnet_skb_return
[  102.531305] asix: disagrees about version of symbol usbnet_tx_timeout
[  102.531310] asix: Unknown symbol usbnet_tx_timeout
[  102.531875] asix: disagrees about version of symbol usbnet_get_settings
[  102.531880] asix: Unknown symbol usbnet_get_settings
[  102.532344] asix: disagrees about version of symbol usbnet_suspend
[  102.532349] asix: Unknown symbol usbnet_suspend
[  102.532680] asix: disagrees about version of symbol usbnet_start_xmit
[  102.532688] asix: Unknown symbol usbnet_start_xmit
[  102.533122] asix: disagrees about version of symbol usbnet_get_drvinfo
[  102.533128] asix: Unknown symbol usbnet_get_drvinfo
[  102.533557] asix: disagrees about version of symbol usbnet_get_endpoints
[  102.533563] asix: Unknown symbol usbnet_get_endpoints
[  102.534544] asix: disagrees about version of symbol usbnet_nway_reset
[  102.534556] asix: Unknown symbol usbnet_nway_reset
[  102.535001] asix: disagrees about version of symbol usbnet_stop
[  102.535011] asix: Unknown symbol usbnet_stop
[  102.535622] asix: disagrees about version of symbol usbnet_defer_kevent
[  102.535633] asix: Unknown symbol usbnet_defer_kevent
[  102.536893] asix: disagrees about version of symbol usbnet_disconnect
[  102.536903] asix: Unknown symbol usbnet_disconnect
[  102.537319] asix: disagrees about version of symbol usbnet_set_settings
[  102.537329] asix: Unknown symbol usbnet_set_settings
[  102.537743] asix: disagrees about version of symbol usbnet_probe
[  102.537754] asix: Unknown symbol usbnet_probe
[  102.538131] asix: disagrees about version of symbol usbnet_resume
[  102.538139] asix: Unknown symbol usbnet_resume

I checked /lib/modules/2.6.32-23-server
and I found strange that for version 2.6.32-23 i have 2 usbnet modules
./kernel/drivers/net/usb/usbnet.ko
./updates/cw/usbnet.ko

Is there some configuration I'm missing to make my D-Link DUB-E100 card to work with 2.6.32-23?
thanks a lot in advance

---

### Post by justforsp on 2010-07-04
Anyone using usb network card with Lucid?

---

### Post by justforsp on 2010-07-05
Just find out that kernel is not really the problem
problem is caused by upgrade of linux-backports-modules-wireless-lucid-server from 2.6.32.22.23 to 2.6.32.23.24
backports modules are now also include usbnet and this makes asix stop working
is it a bug?

---

### Post by shreyanshjain8 on 2010-07-19
hey man.. even i am facing this problem...
i am a USB-LAN card of ENTER company.. 

after the upgradation to new kernel thats 2.6.32-23 my card also stopped detecting automatically by the ubuntu...

if backport is the problem than unistalling it from synaptic solves the problem...??? i mean to say that after uninstalling my system will detect the device automatically..???

---

