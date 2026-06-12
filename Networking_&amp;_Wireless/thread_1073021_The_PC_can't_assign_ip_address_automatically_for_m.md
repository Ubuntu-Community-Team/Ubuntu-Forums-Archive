---
title: "The PC can't assign ip address automatically for my usb-ethernet connection"
date: 2009-02-17
forum: Networking &amp; Wireless
---

### Post by hzpeterchen on 2009-02-17
Dear all,

When my device (usb gadget,CDC ethernet) connects to the PC, it can't assign ip address automatically for usb0, although it can get MAC address for my usb gadget. Each time I must type:  
    *ifconfig usb0 10.0.0.1 netmask 255.255.255.0 up*
manually to assign ipaddr for usb0. My ubuntu version is 8.04.

the dmesg log likes:

[I][59194.541456] usb 1-1: USB disconnect, address 48
[59194.541729] usb0: unregister 'cdc_ether' usb-0000:00:1a.7-1, CDC Ethernet Device
[59194.821555] usb 1-1: new high speed USB device using ehci_hcd and address 49
[59194.954501] usb 1-1: configuration #1 chosen from 1 choice
[59194.955490] usb0: register 'cdc_ether' at usb-0000:00:1a.7-1, CDC Ethernet Device, 1e:6e:37:bc:8a:47
[59203.719890] usb 1-1: USB disconnect, address 49
[59203.720048] usb0: unregister 'cdc_ether' usb-0000:00:1a.7-1, CDC Ethernet Device
[59203.997019] usb 1-1: new high speed USB device using ehci_hcd and address 50
[59204.145524] usb 1-1: configuration #1 chosen from 2 choices
[59204.160381] usb0: register 'cdc_ether' at usb-0000:00:1a.7-1, CDC Ethernet Device, 3a:41:fc:f0:84:be
[/I]

My /etc/network/interface file:

[I]  1 auto lo
  2 iface lo inet loopback
  3 mapping hotplug
  4 script grep
  5 map usb0
  6 auto usb0
  7 iface usb0 inet static
  8 address 10.0.0.1
  9 netmask 255.255.255.0
 10 ifconfig usb0 10.0.0.1 netmask 255.255.255.0 up
[/I]
or 
  [I]auto lo
  iface lo inet loopback
  ifconfig usb0 10.0.0.1 netmask 255.255.255.0 up
  auto usb0
  iface usb0 inet static
  address 10.0.0.1
  netmask 255.255.255.0[/I]

Does anyone have tips for such problem?
Thank you in advance

---

### Post by hzpeterchen on 2009-02-19
:(

No one knows?
It is very unconvenient for me, I need to first manually assign ip, second tftp my kernel image, after kernel boots, I need to manually assign ip at pc again, otherwise, the NFS filesystem can't be mounted for my device.

Thank you

---

### Post by hzpeterchen on 2009-03-25
I did a workaround at my ubuntu 8.04.

    Edit your /etc/udev/rules.d/85-ifupdown.rules
      Add below line between
      ACTION=="remove", RUN+="/sbin/start-stop-daemon --start --background --pidfile /var/run/network/bogus --startas /sbin/ifdown -- --allow auto $env{INTERFACE}"
      LABEL="net_end"

        KERNEL=="usb0" RUN+="/sbin/ifconfig usb0 10.0.0.1 netmask 255.255.255.0 up"

    NOTE: If your usb CDC ethernet device name is not usb0, please change corresponding one.

---

