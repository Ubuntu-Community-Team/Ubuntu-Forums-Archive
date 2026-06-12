---
title: "ZTE MF636 not seen by Network Manager on 10.04"
date: 2011-01-20
forum: Networking &amp; Wireless
---

### Post by Darius_ on 2011-01-20
Hi,
I am trying to use a ZTE MF636 (Telstra Australia) USB dongle.

It is detected by the kernel and works in wvdial, however nm doesn't see it so I can't configure it that way.

udevadm info --export-db shows..

P: /devices/pci0000:00/0000:00:1d.7/usb1/1-7/1-7:1.3/ttyUSB2
E: UDEV_LOG=3
E: DEVPATH=/devices/pci0000:00/0000:00:1d.7/usb1/1-7/1-7:1.3/ttyUSB2
E: DRIVER=option1
E: SUBSYSTEM=usb-serial

P: /devices/pci0000:00/0000:00:1d.7/usb1/1-7/1-7:1.3/ttyUSB2/tty/ttyUSB2
N: ttyUSB2
S: char/188:2
S: serial/by-path/pci-0000:00:1d.7-usb-0:7:1.3-port0
S: serial/by-id/usb-ZTE_Incorporated_ZTE_WCDMA_Technologies_MSM_P673C3TBPD010000-if03-port0
E: UDEV_LOG=3
E: DEVPATH=/devices/pci0000:00/0000:00:1d.7/usb1/1-7/1-7:1.3/ttyUSB2/tty/ttyUSB2
E: MAJOR=188
E: MINOR=2
E: DEVNAME=/dev/ttyUSB2
E: SUBSYSTEM=tty
E: ID_PORT=0
E: ID_PATH=pci-0000:00:1d.7-usb-0:7:1.3
E: ID_VENDOR=ZTE_Incorporated
E: ID_VENDOR_ENC=ZTE\x2cIncorporated
E: ID_VENDOR_ID=19d2
E: ID_MODEL=ZTE_WCDMA_Technologies_MSM
E: ID_MODEL_ENC=ZTE\x20WCDMA\x20Technologies\x20MSM
E: ID_MODEL_ID=0031
E: ID_REVISION=0000
E: ID_SERIAL=ZTE_Incorporated_ZTE_WCDMA_Technologies_MSM_P673C3TBPD010000
E: ID_SERIAL_SHORT=P673C3TBPD010000
E: ID_TYPE=generic
E: ID_BUS=usb
E: ID_USB_INTERFACES=:ffffff:080650:
E: ID_USB_INTERFACE_NUM=03
E: ID_USB_DRIVER=option
E: ID_IFACE=03
E: ID_VENDOR_FROM_DATABASE=ONDA Communication S.p.A.
E: ID_MODEL_FROM_DATABASE=ZTE MF110/MF636
E: ID_MM_ZTE_PORT_TYPE_MODEM=1E: DEVLINKS=/dev/char/188:2 /dev/serial/by-path/pci-0000:00:1d.7-usb-0:7:1.3-port0 /dev/serial/by-i
d/usb-ZTE_Incorporated_ZTE_WCDMA_Technologies_MSM_P673C3TBPD010000-if03-port0

lshal shows..

udi = '/org/freedesktop/Hal/devices/usb_device_19d2_31_P673C3TBPD010000_if3_serial_usb_0'
  info.capabilities = {'serial'} (string list)
  info.category = 'serial'  (string)
  info.parent = '/org/freedesktop/Hal/devices/usb_device_19d2_31_P673C3TBPD010000_if3'  (string)
  info.product = 'ZTE MF636'  (string)
  info.subsystem = 'tty'  (string)
  info.udi = '/org/freedesktop/Hal/devices/usb_device_19d2_31_P673C3TBPD010000_if3_serial_usb_0'  (string)
  linux.device_file = '/dev/ttyUSB2'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'tty'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.7/usb1/1-7/1-7:1.3/ttyUSB2/tty/ttyUSB2'  (string)
  serial.device = '/dev/ttyUSB2'  (string)
  serial.originating_device = '/org/freedesktop/Hal/devices/usb_device_19d2_31_P673C3TBPD010000_if3'  (string)
  serial.port = 0  (0x0)  (int)
  serial.type = 'usb'  (string)

I note that (unlike a different USB 3g modem I have) there is no 'modem' in the capability list.

What is the right way to correct this? Is udev not putting the right hint on for hal or is it that a hal rule is missing? (or something else :)

Thanks!

---

### Post by GeorgeVita on 2011-03-14
Hi **Darius_**,
if you did not solve your problem, try a firmware update for your ZTE MF636. This solved a 3 years old [bug#408555]("https://bugs.launchpad.net/bugs/408555") and I can use the 'normal' way to connect (network-manager & modem-manager).

Best source for the firmware update is your 3G data provider as some 'customization' may included. 
**ZTE firmware:** [http://www.zte.com.cn](http://www.zte.com.cn) from top menu choose **Support > Handset Services >** choose **country** and read carefully the description/model/instructions before updating!

Regards,
George

---

