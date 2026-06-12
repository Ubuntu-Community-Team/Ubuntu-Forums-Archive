---
title: "Need help getting SkyStar2 Digital Satellite card working"
date: 2008-10-19
forum: Multimedia Software
---

### Post by psavva on 2008-10-19
Can someone please help me on a card new DVB card i have just bought and can't get it working.

It's a Technisat SkyStar2

Here is some info that may help.

lspci
```

02:03.0 Network controller: Techsan Electronics Co Ltd B2C2 FlexCopII DVB chip / Technisat SkyStar2 DVB card (rev 02)

```

dmesg
```

[10114.169518] flexcop-pci: will use the HW PID filter.
[10114.169530] flexcop-pci: card revision 2
[10114.169542] b2c2_flexcop_pci 0000:02:03.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[10114.185045] b2c2-flexcop: unkown FlexCop Revision: f. Please report the linux-dvb@linuxtv.org.
[10114.187449] DVB: registering new adapter (FlexCop Digital TV device)
[10114.190001] b2c2-flexcop: reading of MAC address failed.
[10114.190005] 
[10114.190255] b2c2-flexcop: i2c master_xfer failed
[10114.190647] b2c2-flexcop: i2c master_xfer failed
[10114.190654] CX24123: cx24123_i2c_readreg: reg=0x0 (error=-121)
[10114.190658] CX24123: wrong demod revision: 87
[10114.191003] b2c2-flexcop: i2c master_xfer failed
[10114.393028] b2c2-flexcop: i2c master_xfer failed
[10114.393453] b2c2-flexcop: i2c master_xfer failed
[10114.393462] mt352_read_register: readreg error (reg=127, ret==-121)
[10114.393879] b2c2-flexcop: i2c master_xfer failed
[10114.393886] nxt200x: nxt200x_readbytes: i2c read error (addr 0x0a, err == -121)
[10114.393893] Unknown/Unsupported NXT chip: 00 00 00 00 00
[10114.394295] b2c2-flexcop: i2c master_xfer failed
[10114.394303] lgdt330x: i2c_read_demod_bytes: addr 0x59 select 0x02 error (ret == -121)
[10114.394743] b2c2-flexcop: i2c master_xfer failed
[10114.395162] b2c2-flexcop: i2c master_xfer failed
[10114.395169] stv0297_readreg: readreg error (reg == 0x80, ret == -121)
[10114.395584] b2c2-flexcop: i2c master_xfer failed
[10114.395590] mt312_read: ret == -121
[10114.395820] b2c2-flexcop: no frontend driver found for this B2C2/FlexCop adapter
[10114.396868] b2c2_flexcop_pci 0000:02:03.0: PCI INT A disabled

```

lshal

```

udi = '/org/freedesktop/Hal/devices/net_00_13_20_21_6a_9f'
  info.capabilities = {'net', 'net.80203', 'wake_on_lan'} (string list)
  info.category = 'net.80203'  (string)
  info.interfaces = {'org.freedesktop.Hal.Device.WakeOnLan'} (string list)
  info.parent = '/org/freedesktop/Hal/devices/pci_8086_1050'  (string)
  info.product = 'Networking Interface'  (string)
  info.subsystem = 'net'  (string)
  info.udi = '/org/freedesktop/Hal/devices/net_00_13_20_21_6a_9f'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'net'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1e.0/0000:02:08.0/net/eth0'  (string)
  net.80203.mac_address = 82143439519  (0x1320216a9f)  (uint64)
  net.address = '00:13:20:21:6a:9f'  (string)
  net.arp_proto_hw_id = 1  (0x1)  (int)
  net.interface = 'eth0'  (string)
  net.linux.ifindex = 2  (0x2)  (int)
  net.originating_device = '/org/freedesktop/Hal/devices/pci_8086_1050'  (string)
  org.freedesktop.Hal.Device.WakeOnLan.method_argnames = {'', '', 'enable'} (string list)
  org.freedesktop.Hal.Device.WakeOnLan.method_execpaths = {'hal-system-wol-supported', 'hal-system-wol-enabled', 'hal-system-wol-enable'} (string list)
  org.freedesktop.Hal.Device.WakeOnLan.method_names = {'GetSupported', 'GetEnabled', 'SetEnabled'} (string list)
  org.freedesktop.Hal.Device.WakeOnLan.method_signatures = {'', '', 'b'} (string list)

udi = '/org/freedesktop/Hal/devices/pci_13d0_2103'
  info.linux.driver = 'b2c2_flexcop_pci'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pci_8086_244e'  (string)
  info.product = 'B2C2 FlexCopII DVB chip / Technisat SkyStar2 DVB card'  (string)
  info.subsystem = 'pci'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_13d0_2103'  (string)
  info.vendor = 'Techsan Electronics Co Ltd'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'pci'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1e.0/0000:02:03.0'  (string)
  pci.device_class = 2  (0x2)  (int)
  pci.device_protocol = 0  (0x0)  (int)
  pci.device_subclass = 128  (0x80)  (int)
  pci.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1e.0/0000:02:03.0'  (string)
  pci.product = 'B2C2 FlexCopII DVB chip / Technisat SkyStar2 DVB card'  (string)
  pci.product_id = 8451  (0x2103)  (int)
  pci.subsys_product_id = 8451  (0x2103)  (int)
  pci.subsys_vendor = 'Techsan Electronics Co Ltd'  (string)
  pci.subsys_vendor_id = 5072  (0x13d0)  (int)
  pci.vendor = 'Techsan Electronics Co Ltd'  (string)
  pci.vendor_id = 5072  (0x13d0)  (int)


```


If you need any other info, Please let me know and i will post it up.

---

### Post by chris_pmf on 2012-01-30
I've the same problem... could you please help me with your solution? Thanks :)

---

