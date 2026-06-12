---
title: "mobile connection issues"
date: 2009-10-10
forum: Networking &amp; Wireless
---

### Post by mythos8709 on 2009-10-10
i am running 9.04 jaunty desktop on my acer 150 zg5 and having problems getting the internal 3G to work

my network manager seems to detect the 3G modem and even find what network the card belongs to (play online) but when i attempt to connect it doesn't seem to do much.

here is the output from lsusb:
```
Bus 001 Device 002: ID 0c45:62c0 Microdia Pavilion Webcam
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 0af0:7211 Option 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```i modified my 10-modem.fdi hal file according to the link below but i am not sure whether i need to recompile something for the .fdi changes to take place
[https://bugzilla.redhat.com/show_bug.cgi?id=479424](https://bugzilla.redhat.com/show_bug.cgi?id=479424)


lshal output
```
  usb_device.bus_number = 2  (0x2)  (int)
  usb_device.can_wake_up = true  (bool)
  usb_device.configuration_value = 1  (0x1)  (int)
  usb_device.device_class = 9  (0x9)  (int)
  usb_device.device_protocol = 0  (0x0)  (int)
  usb_device.device_revision_bcd = 518  (0x206)  (int)
  usb_device.device_subclass = 0  (0x0)  (int)
  usb_device.is_self_powered = true  (bool)
  usb_device.linux.device_number = 1  (0x1)  (int)
  usb_device.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.0/usb2'  (string)
  usb_device.max_power = 0  (0x0)  (int)
  usb_device.num_configurations = 1  (0x1)  (int)
  usb_device.num_interfaces = 1  (0x1)  (int)
  usb_device.num_ports = 2  (0x2)  (int)
  usb_device.product = '1.1 root hub'  (string)
  usb_device.product_id = 1  (0x1)  (int)
  usb_device.serial = '0000:00:1d.0'  (string)
  usb_device.speed = 12.0 (12) (double)
  usb_device.vendor = 'Linux Foundation'  (string)
  usb_device.vendor_id = 7531  (0x1d6b)  (int)
  usb_device.version = 1.1 (1.1) (double)

udi = '/org/freedesktop/Hal/devices/usb_device_1d6b_1_0000_00_1d_0_if0'
  info.linux.driver = 'hub'  (string)
  info.parent = '/org/freedesktop/Hal/devices/usb_device_1d6b_1_0000_00_1d_0'  (string)
  info.product = 'USB Hub Interface'  (string)
  info.subsystem = 'usb'  (string)
  info.udi = '/org/freedesktop/Hal/devices/usb_device_1d6b_1_0000_00_1d_0_if0'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'usb'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.0/usb2/2-0:1.0'  (string)
  usb.bus_number = 2  (0x2)  (int)
  usb.can_wake_up = true  (bool)
  usb.configuration_value = 1  (0x1)  (int)
  usb.device_class = 9  (0x9)  (int)
  usb.device_protocol = 0  (0x0)  (int)
  usb.device_revision_bcd = 518  (0x206)  (int)
  usb.device_subclass = 0  (0x0)  (int)
  usb.interface.class = 9  (0x9)  (int)
  usb.interface.number = 0  (0x0)  (int)
  usb.interface.protocol = 0  (0x0)  (int)
  usb.interface.subclass = 0  (0x0)  (int)
  usb.is_self_powered = true  (bool)
  usb.linux.device_number = 1  (0x1)  (int)
  usb.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.0/usb2/2-0:1.0'  (string)
  usb.max_power = 0  (0x0)  (int)
  usb.num_configurations = 1  (0x1)  (int)
  usb.num_interfaces = 1  (0x1)  (int)
  usb.num_ports = 2  (0x2)  (int)
  usb.product = 'USB Hub Interface'  (string)
  usb.product_id = 1  (0x1)  (int)
  usb.serial = '0000:00:1d.0'  (string)
  usb.speed = 12.0 (12) (double)
  usb.vendor = 'Linux Foundation'  (string)
  usb.vendor_id = 7531  (0x1d6b)  (int)
  usb.version = 1.1 (1.1) (double)

udi = '/org/freedesktop/Hal/devices/pci_8086_27d6'
  info.linux.driver = 'pcieport-driver'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = '82801G (ICH7 Family) PCI Express Port 4'  (string)
  info.subsystem = 'pci'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_8086_27d6'  (string)
  info.vendor = 'Intel Corporation'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'pci'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1c.3'  (string)
  pci.device_class = 6  (0x6)  (int)
  pci.device_protocol = 0  (0x0)  (int)
  pci.device_subclass = 4  (0x4)  (int)
  pci.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1c.3'  (string)
  pci.product = '82801G (ICH7 Family) PCI Express Port 4'  (string)
  pci.product_id = 10198  (0x27d6)  (int)
  pci.subsys_product_id = 0  (0x0)  (int)
  pci.subsys_vendor_id = 0  (0x0)  (int)
  pci.vendor = 'Intel Corporation'  (string)
  pci.vendor_id = 32902  (0x8086)  (int)

udi = '/org/freedesktop/Hal/devices/pci_8086_27d4'
  info.linux.driver = 'pcieport-driver'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = '82801G (ICH7 Family) PCI Express Port 3'  (string)
  info.subsystem = 'pci'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_8086_27d4'  (string)
  info.vendor = 'Intel Corporation'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'pci'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1c.2'  (string)
  pci.device_class = 6  (0x6)  (int)
  pci.device_protocol = 0  (0x0)  (int)
  pci.device_subclass = 4  (0x4)  (int)
  pci.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1c.2'  (string)
  pci.product = '82801G (ICH7 Family) PCI Express Port 3'  (string)
  pci.product_id = 10196  (0x27d4)  (int)
  pci.subsys_product_id = 0  (0x0)  (int)
  pci.subsys_vendor_id = 0  (0x0)  (int)
  pci.vendor = 'Intel Corporation'  (string)
  pci.vendor_id = 32902  (0x8086)  (int)

udi = '/org/freedesktop/Hal/devices/pci_168c_1c'
  info.linux.driver = 'ath5k_pci'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pci_8086_27d4'  (string)
  info.product = 'AR242x 802.11abg Wireless PCI Express Adapter'  (string)
  info.subsystem = 'pci'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_168c_1c'  (string)
  info.vendor = 'Atheros Communications Inc.'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'pci'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1c.2/0000:03:00.0'  (string)
  pci.device_class = 2  (0x2)  (int)
  pci.device_protocol = 0  (0x0)  (int)
  pci.device_subclass = 0  (0x0)  (int)
  pci.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1c.2/0000:03:00.0'  (string)
  pci.product = 'AR242x 802.11abg Wireless PCI Express Adapter'  (string)
  pci.product_id = 28  (0x1c)  (int)
  pci.subsys_product_id = 57352  (0xe008)  (int)
  pci.subsys_vendor = 'Foxconn International, Inc.'  (string)
  pci.subsys_vendor_id = 4187  (0x105b)  (int)
  pci.vendor = 'Atheros Communications Inc.'  (string)
  pci.vendor_id = 5772  (0x168c)  (int)

udi = '/org/freedesktop/Hal/devices/net_00_23_4e_2e_cd_07_0'
  info.capabilities = {'net', 'net.80211control'} (string list)
  info.category = 'net.80211control'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pci_168c_1c'  (string)
  info.product = 'Networking Wireless Control Interface'  (string)
  info.subsystem = 'net'  (string)
  info.udi = '/org/freedesktop/Hal/devices/net_00_23_4e_2e_cd_07_0'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'net'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1c.2/0000:03:00.0/net/wmaster0'  (string)
  net.address = '00:23:4e:2e:cd:07'  (string)
  net.arp_proto_hw_id = 801  (0x321)  (int)
  net.interface = 'wmaster0'  (string)
  net.linux.ifindex = 4  (0x4)  (int)
  net.originating_device = '/org/freedesktop/Hal/devices/pci_168c_1c'  (string)

udi = '/org/freedesktop/Hal/devices/net_00_23_4e_2e_cd_07'
  info.capabilities = {'net', 'net.80211'} (string list)
  info.category = 'net.80211'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pci_168c_1c'  (string)
  info.product = 'WLAN Interface'  (string)
  info.subsystem = 'net'  (string)
  info.udi = '/org/freedesktop/Hal/devices/net_00_23_4e_2e_cd_07'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'net'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1c.2/0000:03:00.0/net/wlan0'  (string)
  net.80211.mac_address = 151635545351  (0x234e2ecd07)  (uint64)
  net.address = '00:23:4e:2e:cd:07'  (string)
  net.arp_proto_hw_id = 1  (0x1)  (int)
  net.interface = 'wlan0'  (string)
  net.linux.ifindex = 5  (0x5)  (int)
  net.originating_device = '/org/freedesktop/Hal/devices/pci_168c_1c'  (string)

udi = '/org/freedesktop/Hal/devices/pci_8086_27d2'
  info.linux.driver = 'pcieport-driver'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = '82801G (ICH7 Family) PCI Express Port 2'  (string)
  info.subsystem = 'pci'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_8086_27d2'  (string)
  info.vendor = 'Intel Corporation'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'pci'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1c.1'  (string)
  pci.device_class = 6  (0x6)  (int)
  pci.device_protocol = 0  (0x0)  (int)
  pci.device_subclass = 4  (0x4)  (int)
  pci.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1c.1'  (string)
  pci.product = '82801G (ICH7 Family) PCI Express Port 2'  (string)
  pci.product_id = 10194  (0x27d2)  (int)
  pci.subsys_product_id = 0  (0x0)  (int)
  pci.subsys_vendor_id = 0  (0x0)  (int)
  pci.vendor = 'Intel Corporation'  (string)
  pci.vendor_id = 32902  (0x8086)  (int)

udi = '/org/freedesktop/Hal/devices/pci_10ec_8136'
  info.linux.driver = 'r8169'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pci_8086_27d2'  (string)
  info.product = 'RTL8101E/RTL8102E PCI Express Fast Ethernet controller'  (string)
  info.subsystem = 'pci'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_10ec_8136'  (string)
  info.vendor = 'Realtek Semiconductor Co., Ltd.'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'pci'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1c.1/0000:02:00.0'  (string)
  pci.device_class = 2  (0x2)  (int)
  pci.device_protocol = 0  (0x0)  (int)
  pci.device_subclass = 0  (0x0)  (int)
  pci.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1c.1/0000:02:00.0'  (string)
  pci.product = 'RTL8101E/RTL8102E PCI Express Fast Ethernet controller'  (string)
  pci.product_id = 33078  (0x8136)  (int)
  pci.subsys_product_id = 347  (0x15b)  (int)
  pci.subsys_vendor = 'Acer Incorporated [ALI]'  (string)
  pci.subsys_vendor_id = 4133  (0x1025)  (int)
  pci.vendor = 'Realtek Semiconductor Co., Ltd.'  (string)
  pci.vendor_id = 4332  (0x10ec)  (int)

udi = '/org/freedesktop/Hal/devices/net_00_23_8b_1f_80_4f'
  info.capabilities = {'net', 'net.80203', 'wake_on_lan'} (string list)
  info.category = 'net.80203'  (string)
  info.interfaces = {'org.freedesktop.Hal.Device.WakeOnLan'} (string list)
  info.parent = '/org/freedesktop/Hal/devices/pci_10ec_8136'  (string)
  info.product = 'Networking Interface'  (string)
  info.subsystem = 'net'  (string)
  info.udi = '/org/freedesktop/Hal/devices/net_00_23_8b_1f_80_4f'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'net'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1c.1/0000:02:00.0/net/eth0'  (string)
  net.80203.mac_address = 152657952847  (0x238b1f804f)  (uint64)
  net.address = '00:23:8b:1f:80:4f'  (string)
  net.arp_proto_hw_id = 1  (0x1)  (int)
  net.interface = 'eth0'  (string)
  net.linux.ifindex = 2  (0x2)  (int)
  net.originating_device = '/org/freedesktop/Hal/devices/pci_10ec_8136'  (string)
  org.freedesktop.Hal.Device.WakeOnLan.method_argnames = {'', '', 'enable'} (string list)
  org.freedesktop.Hal.Device.WakeOnLan.method_execpaths = {'hal-system-wol-supported', 'hal-system-wol-enabled', 'hal-system-wol-enable'} (string list)
  org.freedesktop.Hal.Device.WakeOnLan.method_names = {'GetSupported', 'GetEnabled', 'SetEnabled'} (string list)
  org.freedesktop.Hal.Device.WakeOnLan.method_signatures = {'', '', 'b'} (string list)

udi = '/org/freedesktop/Hal/devices/pci_8086_27d0'
  info.linux.driver = 'pcieport-driver'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = '82801G (ICH7 Family) PCI Express Port 1'  (string)
  info.subsystem = 'pci'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_8086_27d0'  (string)
  info.vendor = 'Intel Corporation'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'pci'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1c.0'  (string)
  pci.device_class = 6  (0x6)  (int)
  pci.device_protocol = 0  (0x0)  (int)
  pci.device_subclass = 4  (0x4)  (int)
  pci.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1c.0'  (string)
  pci.product = '82801G (ICH7 Family) PCI Express Port 1'  (string)
  pci.product_id = 10192  (0x27d0)  (int)
  pci.subsys_product_id = 0  (0x0)  (int)
  pci.subsys_vendor_id = 0  (0x0)  (int)
  pci.vendor = 'Intel Corporation'  (string)
  pci.vendor_id = 32902  (0x8086)  (int)

udi = '/org/freedesktop/Hal/devices/pci_8086_27d8'
  info.linux.driver = 'HDA Intel'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = '82801G (ICH7 Family) High Definition Audio Controller'  (string)
  info.subsystem = 'pci'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_8086_27d8'  (string)
  info.vendor = 'Intel Corporation'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'pci'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1b.0'  (string)
  pci.device_class = 4  (0x4)  (int)
  pci.device_protocol = 0  (0x0)  (int)
  pci.device_subclass = 3  (0x3)  (int)
  pci.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1b.0'  (string)
  pci.product = '82801G (ICH7 Family) High Definition Audio Controller'  (string)
  pci.product_id = 10200  (0x27d8)  (int)
  pci.subsys_product_id = 347  (0x15b)  (int)
  pci.subsys_vendor = 'Acer Incorporated [ALI]'  (string)
  pci.subsys_vendor_id = 4133  (0x1025)  (int)
  pci.vendor = 'Intel Corporation'  (string)
  pci.vendor_id = 32902  (0x8086)  (int)

udi = '/org/freedesktop/Hal/devices/pci_8086_27d8_sound_card_0'
  info.capabilities = {'sound'} (string list)
  info.category = 'sound'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pci_8086_27d8'  (string)
  info.product = 'HDA Intel Sound Card'  (string)
  info.subsystem = 'sound'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_8086_27d8_sound_card_0'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'sound'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1b.0/sound/card0'  (string)
  sound.card = 0  (0x0)  (int)
  sound.card_id = 'HDA Intel'  (string)
  sound.originating_device = '/org/freedesktop/Hal/devices/pci_8086_27d8'  (string)

udi = '/org/freedesktop/Hal/devices/pci_8086_27d8_sound_card_0_alsa_playback_0'
  access_control.file = '/dev/snd/pcmC0D0p'  (string)
  access_control.type = 'sound'  (string)
  alsa.card = 0  (0x0)  (int)
  alsa.card_id = 'HDA Intel'  (string)
  alsa.device = 0  (0x0)  (int)
  alsa.device_file = '/dev/snd/pcmC0D0p'  (string)
  alsa.device_id = 'ALC268 Analog'  (string)
  alsa.originating_device = '/org/freedesktop/Hal/devices/pci_8086_27d8_sound_card_0'  (string)
  alsa.pcm_class = 'generic'  (string)
  alsa.type = 'playback'  (string)
  info.callouts.add = {'hal-acl-tool --add-device'} (string list)
  info.callouts.remove = {'hal-acl-tool --remove-device'} (string list)
  info.capabilities = {'alsa', 'access_control'} (string list)
  info.category = 'alsa'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pci_8086_27d8_sound_card_0'  (string)
  info.product = 'ALC268 Analog ALSA Playback Device'  (string)
  info.subsystem = 'sound'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_8086_27d8_sound_card_0_alsa_playback_0'  (string)
  linux.device_file = '/dev/snd/pcmC0D0p'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'sound'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1b.0/sound/card0/pcmC0D0p'  (string)

udi = '/org/freedesktop/Hal/devices/pci_8086_27d8_sound_card_0_alsa_capture_0'
  access_control.file = '/dev/snd/pcmC0D0c'  (string)
  access_control.type = 'sound'  (string)
  alsa.card = 0  (0x0)  (int)
  alsa.card_id = 'HDA Intel'  (string)
  alsa.device = 0  (0x0)  (int)
  alsa.device_file = '/dev/snd/pcmC0D0c'  (string)
  alsa.device_id = 'ALC268 Analog'  (string)
  alsa.originating_device = '/org/freedesktop/Hal/devices/pci_8086_27d8_sound_card_0'  (string)
  alsa.pcm_class = 'generic'  (string)
  alsa.type = 'capture'  (string)
  info.callouts.add = {'hal-acl-tool --add-device'} (string list)
  info.callouts.remove = {'hal-acl-tool --remove-device'} (string list)
  info.capabilities = {'alsa', 'access_control'} (string list)
  info.category = 'alsa'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pci_8086_27d8_sound_card_0'  (string)
  info.product = 'ALC268 Analog ALSA Capture Device'  (string)
  info.subsystem = 'sound'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_8086_27d8_sound_card_0_alsa_capture_0'  (string)
  linux.device_file = '/dev/snd/pcmC0D0c'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'sound'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1b.0/sound/card0/pcmC0D0c'  (string)

udi = '/org/freedesktop/Hal/devices/pci_8086_27d8_sound_card_0_oss_mixer__1'
  access_control.file = '/dev/mixer'  (string)
  access_control.type = 'sound'  (string)
  info.callouts.add = {'hal-acl-tool --add-device'} (string list)
  info.callouts.remove = {'hal-acl-tool --remove-device'} (string list)
  info.capabilities = {'oss', 'access_control'} (string list)
  info.category = 'oss'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pci_8086_27d8_sound_card_0'  (string)
  info.product = 'ALC268 Analog OSS Control Device'  (string)
  info.subsystem = 'sound'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_8086_27d8_sound_card_0_oss_mixer__1'  (string)
  linux.device_file = '/dev/mixer'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'sound'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1b.0/sound/card0/mixer'  (string)
  oss.card = 0  (0x0)  (int)
  oss.card_id = 'HDA Intel'  (string)
  oss.device_file = '/dev/mixer'  (string)
  oss.device_id = 'ALC268 Analog'  (string)
  oss.originating_device = '/org/freedesktop/Hal/devices/pci_8086_27d8_sound_card_0'  (string)
  oss.type = 'mixer'  (string)

udi = '/org/freedesktop/Hal/devices/pci_8086_27d8_sound_card_0_oss_pcm_0_0'
  access_control.file = '/dev/dsp'  (string)
  access_control.type = 'sound'  (string)
  info.callouts.add = {'hal-acl-tool --add-device'} (string list)
  info.callouts.remove = {'hal-acl-tool --remove-device'} (string list)
  info.capabilities = {'oss', 'access_control'} (string list)
  info.category = 'oss'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pci_8086_27d8_sound_card_0'  (string)
  info.product = 'ALC268 Analog OSS PCM Device'  (string)
  info.subsystem = 'sound'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_8086_27d8_sound_card_0_oss_pcm_0_0'  (string)
  linux.device_file = '/dev/dsp'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'sound'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1b.0/sound/card0/dsp'  (string)
  oss.card = 0  (0x0)  (int)
  oss.card_id = 'HDA Intel'  (string)
  oss.device = 0  (0x0)  (int)
  oss.device_file = '/dev/dsp'  (string)
  oss.device_id = 'ALC268 Analog'  (string)
  oss.originating_device = '/org/freedesktop/Hal/devices/pci_8086_27d8_sound_card_0'  (string)
  oss.type = 'pcm'  (string)

udi = '/org/freedesktop/Hal/devices/pci_8086_27d8_sound_card_0_alsa_control__1'
  access_control.file = '/dev/snd/controlC0'  (string)
  access_control.type = 'sound'  (string)
  alsa.card = 0  (0x0)  (int)
  alsa.card_id = 'HDA Intel'  (string)
  alsa.device_file = '/dev/snd/controlC0'  (string)
  alsa.originating_device = '/org/freedesktop/Hal/devices/pci_8086_27d8_sound_card_0'  (string)
  alsa.type = 'control'  (string)
  info.callouts.add = {'hal-acl-tool --add-device'} (string list)
  info.callouts.remove = {'hal-acl-tool --remove-device'} (string list)
  info.capabilities = {'alsa', 'access_control'} (string list)
  info.category = 'alsa'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pci_8086_27d8_sound_card_0'  (string)
  info.product = 'HDA Intel ALSA Control Device'  (string)
  info.subsystem = 'sound'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_8086_27d8_sound_card_0_alsa_control__1'  (string)
  linux.device_file = '/dev/snd/controlC0'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'sound'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1b.0/sound/card0/controlC0'  (string)

udi = '/org/freedesktop/Hal/devices/pci_8086_27d8_sound_card_0_oss_pcm_0'
  access_control.file = '/dev/audio'  (string)
  access_control.type = 'sound'  (string)
  info.callouts.add = {'hal-acl-tool --add-device'} (string list)
  info.callouts.remove = {'hal-acl-tool --remove-device'} (string list)
  info.capabilities = {'oss', 'access_control'} (string list)
  info.category = 'oss'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pci_8086_27d8_sound_card_0'  (string)
  info.product = 'ALC268 Analog OSS PCM Device'  (string)
  info.subsystem = 'sound'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_8086_27d8_sound_card_0_oss_pcm_0'  (string)
  linux.device_file = '/dev/audio'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'sound'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1b.0/sound/card0/audio'  (string)
  oss.card = 0  (0x0)  (int)
  oss.card_id = 'HDA Intel'  (string)
  oss.device = 0  (0x0)  (int)
  oss.device_file = '/dev/audio'  (string)
  oss.device_id = 'ALC268 Analog'  (string)
  oss.originating_device = '/org/freedesktop/Hal/devices/pci_8086_27d8_sound_card_0'  (string)
  oss.type = 'pcm'  (string)

udi = '/org/freedesktop/Hal/devices/pci_8086_27a6'
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller'  (string)
  info.subsystem = 'pci'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_8086_27a6'  (string)
  info.vendor = 'Intel Corporation'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'pci'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:02.1'  (string)
  pci.device_class = 3  (0x3)  (int)
  pci.device_protocol = 0  (0x0)  (int)
  pci.device_subclass = 128  (0x80)  (int)
  pci.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:02.1'  (string)
  pci.product = 'Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller'  (string)
  pci.product_id = 10150  (0x27a6)  (int)
  pci.subsys_product_id = 347  (0x15b)  (int)
  pci.subsys_vendor = 'Acer Incorporated [ALI]'  (string)
  pci.subsys_vendor_id = 4133  (0x1025)  (int)
  pci.vendor = 'Intel Corporation'  (string)
  pci.vendor_id = 32902  (0x8086)  (int)

udi = '/org/freedesktop/Hal/devices/pci_8086_27ae'
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'Mobile 945GME Express Integrated Graphics Controller'  (string)
  info.subsystem = 'pci'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_8086_27ae'  (string)
  info.vendor = 'Intel Corporation'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'pci'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:02.0'  (string)
  pci.device_class = 3  (0x3)  (int)
  pci.device_protocol = 0  (0x0)  (int)
  pci.device_subclass = 0  (0x0)  (int)
  pci.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:02.0'  (string)
  pci.product = 'Mobile 945GME Express Integrated Graphics Controller'  (string)
  pci.product_id = 10158  (0x27ae)  (int)
  pci.subsys_product_id = 347  (0x15b)  (int)
  pci.subsys_vendor = 'Acer Incorporated [ALI]'  (string)
  pci.subsys_vendor_id = 4133  (0x1025)  (int)
  pci.vendor = 'Intel Corporation'  (string)
  pci.vendor_id = 32902  (0x8086)  (int)

udi = '/org/freedesktop/Hal/devices/pci_8086_27ae_drm_i915_card0'
  access_control.file = '/dev/dri/card0'  (string)
  access_control.type = 'video'  (string)
  drm.dri_library = 'i915'  (string)
  info.callouts.add = {'hal-acl-tool --add-device'} (string list)
  info.callouts.remove = {'hal-acl-tool --remove-device'} (string list)
  info.capabilities = {'drm', 'access_control'} (string list)
  info.category = 'drm'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pci_8086_27ae'  (string)
  info.product = 'Direct Rendering Manager Device'  (string)
  info.subsystem = 'drm'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_8086_27ae_drm_i915_card0'  (string)
  info.vendor = 'Intel Corporation'  (string)
  linux.device_file = '/dev/dri/card0'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'drm'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:02.0/drm/card0'  (string)

udi = '/org/freedesktop/Hal/devices/pci_8086_27ac'
  info.linux.driver = 'agpgart-intel'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'Mobile 945GME Express Memory Controller Hub'  (string)
  info.subsystem = 'pci'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_8086_27ac'  (string)
  info.vendor = 'Intel Corporation'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'pci'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:00.0'  (string)
  pci.device_class = 6  (0x6)  (int)
  pci.device_protocol = 0  (0x0)  (int)
  pci.device_subclass = 0  (0x0)  (int)
  pci.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:00.0'  (string)
  pci.product = 'Mobile 945GME Express Memory Controller Hub'  (string)
  pci.product_id = 10156  (0x27ac)  (int)
  pci.subsys_product_id = 347  (0x15b)  (int)
  pci.subsys_vendor = 'Acer Incorporated [ALI]'  (string)
  pci.subsys_vendor_id = 4133  (0x1025)  (int)
  pci.vendor = 'Intel Corporation'  (string)
  pci.vendor_id = 32902  (0x8086)  (int)

udi = '/org/freedesktop/Hal/devices/fuse'
  access_control.file = '/dev/fuse'  (string)
  access_control.type = 'camera'  (string)
  info.callouts.add = {'hal-acl-tool --add-device'} (string list)
  info.callouts.remove = {'hal-acl-tool --remove-device'} (string list)
  info.capabilities = {'access_control'} (string list)
  info.parent = '/org/freedesktop/Hal/devices/pci_8086_27ac'  (string)
  info.subsystem = 'unknown'  (string)
  info.udi = '/org/freedesktop/Hal/devices/fuse'  (string)


Dumped 111 device(s) from the Global Device List.
------------------------------------------------

```please help! i am stumped!

---

### Post by mythos8709 on 2009-10-10
here is a serial debug of my network manager. it appears that the device cannot locate a network. i know that i am in range of my 3g network however, because if i use my usb 3g modem it works just fine...

```
NetworkManager: <info>  starting...
NetworkManager: <info>  (eth0): new Ethernet device (driver: 'r8169')
NetworkManager: <info>  (eth0): exported as /org/freedesktop/Hal/devices/net_00_23_8b_1f_80_4f
NetworkManager: <info>  (wlan0): driver supports SSID scans (scan_capa 0x01).
NetworkManager: <info>  (wlan0): new 802.11 WiFi device (driver: 'ath5k_pci')
NetworkManager: <info>  (wlan0): exported as /org/freedesktop/Hal/devices/net_00_23_4e_2e_cd_07
NetworkManager: <info>  (ttyHS3): found serial port (udev:GSM  hal:GSM)
NetworkManager: <info>  (ttyHS2): ignoring due to lack of mobile broadband capabilties
NetworkManager: <info>  (ttyHS1): found serial port (udev:GSM  hal:)
NetworkManager: <info>  (ttyHS1): deferring until all ports found
NetworkManager: <info>  (ttyHS0): found serial port (udev:GSM  hal:)
NetworkManager: <info>  (ttyHS0): deferring until all ports found
NetworkManager: <info>  (eth0): device state change: 1 -> 2
NetworkManager: <info>  (eth0): bringing up device.
NetworkManager: <info>  (eth0): preparing device.
NetworkManager: <info>  (eth0): deactivating device (reason: 2).
NetworkManager: <info>  Unmanaged Device found; state CONNECTED forced. (see http://bugs.launchpad.net/bugs/191889)
NetworkManager: <info>  Unmanaged Device found; state CONNECTED forced. (see http://bugs.launchpad.net/bugs/191889)
NetworkManager: <info>  (wlan0): device state change: 1 -> 2
NetworkManager: <info>  (wlan0): bringing up device.
NetworkManager: <info>  (wlan0): preparing device.
NetworkManager: <info>  (wlan0): deactivating device (reason: 2).
NetworkManager: <info>  Re-checking deferred serial ports
NetworkManager: <info>  (ttyHS0): new Modem device (driver: 'hso')
NetworkManager: <info>  (ttyHS0): exported as /org/freedesktop/Hal/devices/usb_device_af0_7211_Serial_Number_if0_serial_unknown_0
NetworkManager: <info>  (wlan0): device state change: 2 -> 3
NetworkManager: <info>  Unmanaged Device found; state CONNECTED forced. (see http://bugs.launchpad.net/bugs/191889)
NetworkManager: <info>  Unmanaged Device found; state CONNECTED forced. (see http://bugs.launchpad.net/bugs/191889)
NetworkManager: <info>  (wlan0): supplicant interface state:  starting -> ready
NetworkManager: <info>  (ttyHS0): device state change: 1 -> 2
NetworkManager: <info>  (ttyHS0): deactivating device (reason: 2).
NetworkManager: nm_system_device_flush_ip4_routes_with_iface: assertion `iface_idx >= 0' failed
NetworkManager: nm_system_device_flush_ip4_addresses_with_iface: assertion `iface_idx >= 0' failed
NetworkManager: <info>  (ttyHS0): device state change: 2 -> 3
NetworkManager: <info>  Activation (wlan0) starting connection 'Auto PlunderPL'
NetworkManager: <info>  (wlan0): device state change: 3 -> 4
NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
NetworkManager: <info>  (wlan0): device state change: 4 -> 5
NetworkManager: <info>  Activation (wlan0/wireless): access point 'Auto PlunderPL' has security, but secrets are required.
NetworkManager: <info>  (wlan0): device state change: 5 -> 6
NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
NetworkManager: <info>  (wlan0): device state change: 6 -> 4
NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
NetworkManager: <info>  (wlan0): device state change: 4 -> 5
NetworkManager: <info>  Activation (wlan0/wireless): connection 'Auto PlunderPL' has security, and secrets exist.  No new secrets needed.
NetworkManager: <info>  Config: added 'ssid' value 'PlunderPL'
NetworkManager: <info>  Config: added 'scan_ssid' value '1'
NetworkManager: <info>  Config: added 'key_mgmt' value 'WPA-PSK'
NetworkManager: <info>  Config: added 'psk' value '<omitted>'
NetworkManager: nm_setting_802_1x_get_pkcs11_engine_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
NetworkManager: nm_setting_802_1x_get_pkcs11_module_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
NetworkManager: <info>  Config: set interface ap_scan to 1
NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> disconnected
NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning
NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> associating
NetworkManager: <info>  (wlan0): supplicant connection state:  associating -> 4-way handshake
NetworkManager: <info>  (wlan0): supplicant connection state:  4-way handshake -> associated
NetworkManager: <info>  (wlan0): supplicant connection state:  associated -> disconnected
NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning
NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> associated
NetworkManager: <info>  (wlan0): supplicant connection state:  associated -> 4-way handshake
NetworkManager: <info>  (wlan0): supplicant connection state:  4-way handshake -> group handshake
NetworkManager: <info>  (wlan0): supplicant connection state:  group handshake -> completed
NetworkManager: <info>  Activation (wlan0/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'PlunderPL'.
NetworkManager: <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) scheduled.
NetworkManager: <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) started...
NetworkManager: <info>  (wlan0): device state change: 5 -> 7
NetworkManager: <info>  Activation (wlan0) Beginning DHCP transaction.
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wmaster0: unknown hardware address type 801
NetworkManager: <info>  dhclient started with pid 3845
NetworkManager: <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) complete.
wmaster0: unknown hardware address type 801
Listening on LPF/wlan0/00:23:4e:2e:cd:07
Sending on   LPF/wlan0/00:23:4e:2e:cd:07
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
NetworkManager: <info>  DHCP: device wlan0 state changed (null) -> preinit
DHCPOFFER of 192.168.8.198 from 192.168.8.1
DHCPREQUEST of 192.168.8.198 on wlan0 to 255.255.255.255 port 67
DHCPACK of 192.168.8.198 from 192.168.8.1
NetworkManager: <info>  DHCP: device wlan0 state changed preinit -> bound
NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP Configure Get) scheduled...
NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP Configure Get) started...
NetworkManager: <info>    address 192.168.8.198
NetworkManager: <info>    prefix 24 (255.255.255.0)
NetworkManager: <info>    gateway 192.168.8.1
NetworkManager: <info>    nameserver '192.168.8.1'
NetworkManager: <info>    domain name 'chello.pl'
NetworkManager: <info>  Activation (wlan0) Stage 5 of 5 (IP Configure Commit) scheduled...
NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP Configure Get) complete.
NetworkManager: <info>  Activation (wlan0) Stage 5 of 5 (IP Configure Commit) started...
bound to 192.168.8.198 -- renewal in 41481 seconds.
NetworkManager: <info>  (wlan0): device state change: 7 -> 8
NetworkManager: <info>  Policy set 'Auto PlunderPL' (wlan0) as default for routing and DNS.
NetworkManager: <info>  Activation (wlan0) successful, device activated.
NetworkManager: <info>  Activation (wlan0) Stage 5 of 5 (IP Configure Commit) complete.
NetworkManager: <info>  Activation (ttyHS0) starting connection 'Play Online'
NetworkManager: <info>  (ttyHS0): device state change: 3 -> 4
NetworkManager: <info>  Activation (ttyHS0) Stage 1 of 5 (Device Prepare) scheduled...
NetworkManager: <info>  Activation (ttyHS0) Stage 1 of 5 (Device Prepare) started...
NetworkManager: <debug> [1255212789.362553] nm_serial_device_open(): (ttyHS0) opening device...
NetworkManager: <info>  Activation (ttyHS0) Stage 1 of 5 (Device Prepare) complete.
NetworkManager: <debug> [1255212789.465100] nm_serial_debug(): Sending: 'ATZ E0 V1 X4 &C1 +FCLASS=0
'
NetworkManager: <debug> [1255212789.600460] nm_serial_debug(): Got: '

OK

'
NetworkManager: <debug> [1255212789.600713] nm_serial_debug(): Sending: 'AT+CPIN?
'
NetworkManager: <debug> [1255212789.728348] nm_serial_debug(): Got: '

+CPIN: READY



OK

'
NetworkManager: <debug> [1255212789.728576] nm_serial_debug(): Sending: 'ATZ E0 V1 X4 &C1 +FCLASS=0
'
NetworkManager: <debug> [1255212789.856321] nm_serial_debug(): Got: '

OK

'
NetworkManager: <info>  (ttyHS0): powering up...
NetworkManager: <debug> [1255212789.856649] nm_serial_debug(): Sending: 'AT+CFUN=1
'
NetworkManager: <debug> [1255212789.984203] nm_serial_debug(): Got: '

OK

'
NetworkManager: <debug> [1255212789.984403] nm_serial_debug(): Sending: 'AT+CGMM
'
NetworkManager: <debug> [1255212790.118940] nm_serial_debug(): Got: '

GTM380



OK

'
NetworkManager: <debug> [1255212790.119306] nm_serial_debug(): Sending: 'AT+CREG?
'
NetworkManager: <debug> [1255212790.240109] nm_serial_debug(): Got: '

+CREG: 0,2



OK

'
NetworkManager: <info>  Searching for a network...
NetworkManager: <debug> [1255212791.001318] nm_serial_debug(): Sending: 'AT+CREG?
'
NetworkManager: <debug> [1255212791.135667] nm_serial_debug(): Got: '

+CREG: 0,2



OK

'
NetworkManager: <info>  Searching for a network...
NetworkManager: <debug> [1255212792.000868] nm_serial_debug(): Sending: 'AT+CREG?
'
NetworkManager: <debug> [1255212792.030191] nm_serial_debug(): Got: '

+CREG: 0,2



OK

'
NetworkManager: <info>  Searching for a network...
NetworkManager: <debug> [1255212793.001647] nm_serial_debug(): Sending: 'AT+CREG?
'
NetworkManager: <debug> [1255212793.054707] nm_serial_debug(): Got: '

+CREG: 0,2



OK

'
NetworkManager: <info>  Searching for a network...
NetworkManager: <debug> [1255212794.001598] nm_serial_debug(): Sending: 'AT+CREG?
'
NetworkManager: <debug> [1255212794.078212] nm_serial_debug(): Got: '

+CREG: 0,2



OK

'
NetworkManager: <info>  Searching for a network...
NetworkManager: <debug> [1255212795.001626] nm_serial_debug(): Sending: 'AT+CREG?
'
NetworkManager: <debug> [1255212795.101683] nm_serial_debug(): Got: '

+CREG: 0,2



OK

'
NetworkManager: <info>  Searching for a network...
NetworkManager: <debug> [1255212796.000444] nm_serial_debug(): Sending: 'AT+CREG?
'
NetworkManager: <debug> [1255212796.125171] nm_serial_debug(): Got: '

+CREG: 0,2



OK

'
NetworkManager: <info>  Searching for a network...
NetworkManager: <debug> [1255212797.001680] nm_serial_debug(): Sending: 'AT+CREG?
'
NetworkManager: <debug> [1255212797.148658] nm_serial_debug(): Got: '

+CREG: 0,2



OK

'
NetworkManager: <info>  Searching for a network...
NetworkManager: <debug> [1255212798.001952] nm_serial_debug(): Sending: 'AT+CREG?
'
NetworkManager: <debug> [1255212798.044212] nm_serial_debug(): Got: '

+CREG: 0,2



OK

'
NetworkManager: <info>  Searching for a network...
NetworkManager: <debug> [1255212799.001611] nm_serial_debug(): Sending: 'AT+CREG?
'
NetworkManager: <debug> [1255212799.067662] nm_serial_debug(): Got: '

+CREG: 0,2



OK

'
NetworkManager: <info>  Searching for a network...
NetworkManager: <debug> [1255212800.002431] nm_serial_debug(): Sending: 'AT+CREG?
'
NetworkManager: <debug> [1255212800.091177] nm_serial_debug(): Got: '

+CREG: 0,2



OK

'
NetworkManager: <info>  Searching for a network...
NetworkManager: <debug> [1255212801.001538] nm_serial_debug(): Sending: 'AT+CREG?
'
NetworkManager: <debug> [1255212801.114691] nm_serial_debug(): Got: '

+CREG: 0,2



OK

'
NetworkManager: <info>  Searching for a network...
NetworkManager: <debug> [1255212802.001090] nm_serial_debug(): Sending: 'AT+CREG?
'
NetworkManager: <debug> [1255212802.137981] nm_serial_debug(): Got: '

+CREG: 0,2



OK

'
NetworkManager: <info>  Searching for a network...
NetworkManager: <debug> [1255212803.001366] nm_serial_debug(): Sending: 'AT+CREG?
'
NetworkManager: <debug> [1255212803.034710] nm_serial_debug(): Got: '

+CREG: 0,2



OK

'
NetworkManager: <info>  Searching for a network...
NetworkManager: <debug> [1255212804.001280] nm_serial_debug(): Sending: 'AT+CREG?
'
NetworkManager: <debug> [1255212804.058688] nm_serial_debug(): Got: '

+CREG: 0,2



OK

'
NetworkManager: <info>  Searching for a network...
NetworkManager: <debug> [1255212805.002086] nm_serial_debug(): Sending: 'AT+CREG?
'
NetworkManager: <debug> [1255212805.082690] nm_serial_debug(): Got: '

+CREG: 0,2



OK

'
NetworkManager: <info>  Searching for a network...
NetworkManager: <debug> [1255212806.002451] nm_serial_debug(): Sending: 'AT+CREG?
'
NetworkManager: <debug> [1255212806.105968] nm_serial_debug(): Got: '

+CREG: 0,2



OK

'
NetworkManager: <info>  Searching for a network...
NetworkManager: <debug> [1255212807.001390] nm_serial_debug(): Sending: 'AT+CREG?
'
NetworkManager: <debug> [1255212807.130692] nm_serial_debug(): Got: '

+CREG: 0,2



OK

'
NetworkManager: <info>  Searching for a network...
NetworkManager: <debug> [1255212808.002019] nm_serial_debug(): Sending: 'AT+CREG?
'
NetworkManager: <debug> [1255212808.154688] nm_serial_debug(): Got: '

+CREG: 0,2



OK

'
NetworkManager: <info>  Searching for a network...
NetworkManager: <debug> [1255212809.001990] nm_serial_debug(): Sending: 'AT+CREG?
'
NetworkManager: <debug> [1255212809.050698] nm_serial_debug(): Got: '

+CREG: 0,2



OK

'
NetworkManager: <info>  Searching for a network...
NetworkManager: <debug> [1255212810.001113] nm_serial_debug(): Sending: 'AT+CREG?
'
NetworkManager: <debug> [1255212810.073992] nm_serial_debug(): Got: '

+CREG: 0,2



OK

'
NetworkManager: <info>  Searching for a network...
NetworkManager: <debug> [1255212811.000823] nm_serial_debug(): Sending: 'AT+CREG?
'
NetworkManager: <debug> [1255212811.098616] nm_serial_debug(): Got: '

+CREG: 0,2



OK

'
NetworkManager: <info>  Searching for a network...
NetworkManager: <debug> [1255212812.002079] nm_serial_debug(): Sending: 'AT+CREG?
'
NetworkManager: <debug> [1255212812.122629] nm_serial_debug(): Got: '

+CREG: 0,2



OK

'
NetworkManager: <info>  Searching for a network...
NetworkManager: <debug> [1255212813.001815] nm_serial_debug(): Sending: 'AT+CREG?
'
NetworkManager: <debug> [1255212813.146893] nm_serial_debug(): Got: '

+CREG: 0,2



OK

'
NetworkManager: <info>  Searching for a network...
NetworkManager: <debug> [1255212814.001156] nm_serial_debug(): Sending: 'AT+CREG?
'
NetworkManager: <debug> [1255212814.041986] nm_serial_debug(): Got: '

+CREG: 0,2



OK

'
NetworkManager: <info>  Searching for a network...
NetworkManager: <debug> [1255212815.001463] nm_serial_debug(): Sending: 'AT+CREG?
'
NetworkManager: <debug> [1255212815.066699] nm_serial_debug(): Got: '

+CREG: 0,2



OK

'
NetworkManager: <info>  Searching for a network...
NetworkManager: <debug> [1255212816.000628] nm_serial_debug(): Sending: 'AT+CREG?
'
NetworkManager: <debug> [1255212816.090765] nm_serial_debug(): Got: '

+CREG: 0,2



OK

'
NetworkManager: <info>  Searching for a network...
NetworkManager: <debug> [1255212817.001835] nm_serial_debug(): Sending: 'AT+CREG?
'
NetworkManager: <debug> [1255212817.114650] nm_serial_debug(): Got: '

+CREG: 0,2



OK

'
NetworkManager: <info>  Searching for a network...
NetworkManager: <debug> [1255212818.002126] nm_serial_debug(): Sending: 'AT+CREG?
'
NetworkManager: <debug> [1255212818.138700] nm_serial_debug(): Got: '

+CREG: 0,2



OK

'
NetworkManager: <info>  Searching for a network...
NetworkManager: <info>  (ttyHS0): device state change: 4 -> 3
NetworkManager: <info>  (ttyHS0): deactivating device (reason: 39).
NetworkManager: <debug> [1255212818.440315] nm_serial_device_close(): Closing device 'ttyHS0'
NetworkManager: <info>  Policy set 'Auto PlunderPL' (wlan0) as default for routing and DNS.
NetworkManager: nm_system_device_flush_ip4_routes_with_iface: assertion `iface_idx >= 0' failed
NetworkManager: nm_system_device_flush_ip4_addresses_with_iface: assertion `iface_idx >= 0' failed
```

---

