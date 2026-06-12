---
title: "3G connection 'disappears' when VM guest is started"
date: 2013-06-17
forum: Networking &amp; Wireless
---

### Post by NomadAU on 2013-06-17
Hi,

I've posted on related 3G problems a few times now, without too much success.  However, I have now managed to get my Qualcomm Gobi 2000 working ok under Ubuntu 12.04 LTS (64-bit), however, I still have a problem whenever I try to start a VM guest image.

The following extract from syslog was taken after my 3G was up and running, and just before I started the VM.   The entry 'Jun 18 10:51:06 taroona pppd[2698]: Modem hangup' shows the 3G being dropped, but I'm at a loss to understand why this is happening.  

Perhaps someone has had experience of this and knows how to fix the problem?

```

Jun 18 10:48:08 taroona dbus[958]: [system] Activating service name='com.ubuntu.SystemService' (using servicehelper)
Jun 18 10:48:08 taroona AptDaemon: INFO: Initializing daemon
Jun 18 10:48:08 taroona dbus[958]: [system] Successfully activated service 'com.ubuntu.SystemService'
Jun 18 10:48:08 taroona AptDaemon.PackageKit: INFO: Initializing PackageKit compat layer
Jun 18 10:48:08 taroona dbus[958]: [system] Successfully activated service 'org.freedesktop.PackageKit'
Jun 18 10:48:08 taroona AptDaemon.PackageKit: INFO: Initializing PackageKit transaction
Jun 18 10:48:08 taroona AptDaemon.Worker: INFO: Simulating trans: /org/debian/apt/transaction/ef165b6daa154f64a0e0d36362e01741
Jun 18 10:48:08 taroona AptDaemon.Worker: INFO: Processing transaction /org/debian/apt/transaction/ef165b6daa154f64a0e0d36362e01741
Jun 18 10:48:12 taroona AptDaemon.PackageKit: INFO: Get updates()
Jun 18 10:48:13 taroona AptDaemon.Worker: INFO: Finished transaction /org/debian/apt/transaction/ef165b6daa154f64a0e0d36362e01741

<<<<< This is where I start up the VM guest  >>>>>>>>

Jun 18 10:50:48 taroona /usr/lib/vmware/bin/vmware-hostd[1647]: Accepted password for user xxxxxx from 127.0.0.1
Jun 18 10:50:58 taroona kernel: [  619.579566] userif-2: sent link up event.
Jun 18 10:50:58 taroona kernel: [  825.873839] /dev/vmmon[4155]: PTSC: initialized at 1595999000 Hz using TSC, TSCs are synchronized.
Jun 18 10:50:58 taroona kernel: [  826.143198] /dev/vmmon[4155]: Monitor IPI vector: 0
Jun 18 10:51:06 taroona kernel: [  834.005498] /dev/vmnet: open called by PID 4167 (vmx-vcpu-0)
Jun 18 10:51:06 taroona kernel: [  834.005521] /dev/vmnet: port on hub 8 successfully opened
Jun 18 10:51:06 taroona kernel: [  834.005540] /dev/vmnet: open called by PID 4167 (vmx-vcpu-0)
Jun 18 10:51:06 taroona kernel: [  834.005552] /dev/vmnet: port on hub 8 successfully opened
Jun 18 10:51:06 taroona udevd[465]: seq 2464 queued, 'remove' 'tty'
Jun 18 10:51:06 taroona udevd[465]: passed 238 bytes to netlink monitor 0x7f325b9db2d0
Jun 18 10:51:06 taroona pppd[2698]: Modem hangup
Jun 18 10:51:06 taroona udevd[465]: seq 2465 queued, 'remove' 'usb-serial'
Jun 18 10:51:06 taroona udevd[582]: seq 2464 running
Jun 18 10:51:06 taroona udevd[465]: seq 2466 queued, 'remove' 'tty'
Jun 18 10:51:06 taroona udevd[465]: passed 238 bytes to netlink monitor 0x7f325b9db2d0
Jun 18 10:51:06 taroona udevd[582]: device 0x7f325b9dd050 filled with db file data
Jun 18 10:51:06 taroona udevd[465]: seq 2467 queued, 'remove' 'usb-serial'
Jun 18 10:51:06 taroona udevd[583]: seq 2466 running
Jun 18 10:51:06 taroona pppd[2698]: Connect time 3.6 minutes.
Jun 18 10:51:06 taroona udevd[582]: device 0x7f325b9dc2b0 has devpath '/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.4/2-1.4:1.1'
Jun 18 10:51:06 taroona pppd[2698]: Sent 247493 bytes, received 1140140 bytes.
Jun 18 10:51:06 taroona udevd[583]: device 0x7f325b9db720 filled with db file data
Jun 18 10:51:06 taroona udevd[582]: device 0x7f325b9dca40 has devpath '/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.4'
Jun 18 10:51:06 taroona udevd[582]: device 0x7f325b9eed30 has devpath '/devices/pci0000:00/0000:00:1d.0/usb2/2-1'
Jun 18 10:51:06 taroona udevd[582]: device 0x7f325b9ef570 has devpath '/devices/pci0000:00/0000:00:1d.0/usb2'
Jun 18 10:51:06 taroona udevd[582]: device 0x7f325b9efda0 has devpath '/devices/pci0000:00/0000:00:1d.0'
Jun 18 10:51:06 taroona udevd[583]: device 0x7f325b9dcf20 has devpath '/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.4/2-1.4:1.2'
Jun 18 10:51:06 taroona udevd[582]: device 0x7f325b9f02b0 has devpath '/devices/pci0000:00'
Jun 18 10:51:06 taroona udevd[582]: RUN '%E{hotplugscript} remove %E{PRODUCT}' /etc/udev/rules.d/z010_mchp_tools.rules:21
Jun 18 10:51:06 taroona udevd[583]: device 0x7f325b9dd6b0 has devpath '/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.4'
Jun 18 10:51:06 taroona udevd[582]: no reference left, remove '/dev/serial/by-id/usb-Qualcomm_Incorporated_Qualcomm_Gobi_2000-if01-port0'
Jun 18 10:51:06 taroona udevd[582]: no reference left, remove '/dev/serial/by-path/pci-0000:00:1d.0-usb-0:1.4:1.1-port0'
Jun 18 10:51:06 taroona udevd[583]: device 0x7f325b9eee30 has devpath '/devices/pci0000:00/0000:00:1d.0/usb2/2-1'
Jun 18 10:51:06 taroona udevd[582]: device node '/dev/ttyUSB0' not found
Jun 18 10:51:06 taroona udevd[582]: removing device node '/dev/ttyUSB0'
Jun 18 10:51:06 taroona udevd[583]: device 0x7f325b9ef880 has devpath '/devices/pci0000:00/0000:00:1d.0/usb2'
Jun 18 10:51:06 taroona udevd[583]: device 0x7f325b9f0080 has devpath '/devices/pci0000:00/0000:00:1d.0'
Jun 18 10:51:06 taroona udevd[583]: device 0x7f325b9f05c0 has devpath '/devices/pci0000:00'
Jun 18 10:51:06 taroona udevd[583]: RUN '%E{hotplugscript} remove %E{PRODUCT}' /etc/udev/rules.d/z010_mchp_tools.rules:21
Jun 18 10:51:06 taroona udevd[4176]: starting '/etc/.mplab_ide/mchplinusbdevice remove '
Jun 18 10:51:06 taroona udevd[583]: no reference left, remove '/dev/serial/by-id/usb-Qualcomm_Incorporated_Qualcomm_Gobi_2000-if02-port0'
Jun 18 10:51:06 taroona udevd[465]: seq 2468 queued, 'remove' 'tty'
Jun 18 10:51:06 taroona udevd[4176]: failed to execute '/etc/.mplab_ide/mchplinusbdevice' '/etc/.mplab_ide/mchplinusbdevice remove ': No such file or directory
Jun 18 10:51:06 taroona udevd[583]: no reference left, remove '/dev/serial/by-path/pci-0000:00:1d.0-usb-0:1.4:1.2-port0'
Jun 18 10:51:06 taroona udevd[583]: device node '/dev/ttyUSB1' not found
Jun 18 10:51:06 taroona udevd[583]: removing device node '/dev/ttyUSB1'
Jun 18 10:51:06 taroona udevd[582]: '/etc/.mplab_ide/mchplinusbdevice remove ' [4176] exit with return code 2
Jun 18 10:51:06 taroona udevd[465]: seq 2468 forked new worker [4178]
Jun 18 10:51:06 taroona udevd[582]: passed -1 bytes to netlink monitor 0x7f325ba74c70
Jun 18 10:51:06 taroona udevd[582]: seq 2464 processed with 0
Jun 18 10:51:06 taroona udevd[465]: seq 2469 queued, 'remove' 'usb-serial'
Jun 18 10:51:06 taroona udevd[465]: seq 2464 done with 0
Jun 18 10:51:06 taroona udevd[582]: seq 2465 running
Jun 18 10:51:06 taroona udevd[582]: device 0x7f325b9f02b0 filled with db file data
Jun 18 10:51:06 taroona udevd[4178]: seq 2468 running
Jun 18 10:51:06 taroona udevd[582]: RUN '%E{hotplugscript} remove %E{PRODUCT}' /etc/udev/rules.d/z010_mchp_tools.rules:21
Jun 18 10:51:06 taroona udevd[4178]: device 0x7f325b9f1750 filled with db file data
Jun 18 10:51:06 taroona udevd[4178]: device 0x7f325b9dc470 has devpath '/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.4/2-1.4:1.3'
Jun 18 10:51:06 taroona udevd[465]: passed 199 bytes to netlink monitor 0x7f325b9db2d0
Jun 18 10:51:06 taroona udevd[4180]: starting '/etc/.mplab_ide/mchplinusbdevice remove '
Jun 18 10:51:06 taroona udevd[4178]: device 0x7f325b9dcc00 has devpath '/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.4'
Jun 18 10:51:06 taroona udevd[4180]: failed to execute '/etc/.mplab_ide/mchplinusbdevice' '/etc/.mplab_ide/mchplinusbdevice remove ': No such file or directory
Jun 18 10:51:06 taroona udevd[4178]: device 0x7f325b9dd3f0 has devpath '/devices/pci0000:00/0000:00:1d.0/usb2/2-1'
Jun 18 10:51:06 taroona udevd[4178]: device 0x7f325b9eeeb0 has devpath '/devices/pci0000:00/0000:00:1d.0/usb2'
Jun 18 10:51:06 taroona udevd[4178]: device 0x7f325b9ef6e0 has devpath '/devices/pci0000:00/0000:00:1d.0'
Jun 18 10:51:06 taroona udevd[4178]: device 0x7f325b9efbf0 has devpath '/devices/pci0000:00'
Jun 18 10:51:06 taroona udevd[4178]: RUN '%E{hotplugscript} remove %E{PRODUCT}' /etc/udev/rules.d/z010_mchp_tools.rules:21
Jun 18 10:51:06 taroona udevd[4178]: no reference left, remove '/dev/serial/by-id/usb-Qualcomm_Incorporated_Qualcomm_Gobi_2000-if03-port0'
Jun 18 10:51:06 taroona udevd[4178]: no reference left, remove '/dev/serial/by-path/pci-0000:00:1d.0-usb-0:1.4:1.3-port0'
Jun 18 10:51:06 taroona udevd[4178]: device node '/dev/ttyUSB2' not found
Jun 18 10:51:06 taroona udevd[4178]: removing device node '/dev/ttyUSB2'
Jun 18 10:51:06 taroona modem-manager[979]: <info>  (ttyUSB1) closing serial port...
Jun 18 10:51:06 taroona udevd[582]: '/etc/.mplab_ide/mchplinusbdevice remove ' [4180] exit with return code 2
Jun 18 10:51:06 taroona kernel: [  834.168406] qcserial ttyUSB0: Qualcomm USB modem converter now disconnected from ttyUSB0
Jun 18 10:51:06 taroona kernel: [  834.168428] qcserial 2-1.4:1.1: device disconnected
Jun 18 10:51:06 taroona kernel: [  834.168674] qcserial ttyUSB1: Qualcomm USB modem converter now disconnected from ttyUSB1
Jun 18 10:51:06 taroona kernel: [  834.168691] qcserial 2-1.4:1.2: device disconnected
Jun 18 10:51:06 taroona kernel: [  834.169167] qcserial ttyUSB2: Qualcomm USB modem converter now disconnected from ttyUSB2
Jun 18 10:51:06 taroona kernel: [  834.169194] qcserial 2-1.4:1.3: device disconnected
Jun 18 10:51:06 taroona modem-manager[979]: <info>  (ttyUSB1) serial port closed
Jun 18 10:51:06 taroona udevd[582]: passed -1 bytes to netlink monitor 0x7f325ba74c70
Jun 18 10:51:06 taroona udevd[465]: seq 2465 done with 0
Jun 18 10:51:06 taroona udevd[582]: seq 2465 processed with 0
Jun 18 10:51:06 taroona udevd[4179]: starting '/etc/.mplab_ide/mchplinusbdevice remove '
Jun 18 10:51:06 taroona udevd[4181]: starting '/etc/.mplab_ide/mchplinusbdevice remove '
Jun 18 10:51:06 taroona udevd[4179]: failed to execute '/etc/.mplab_ide/mchplinusbdevice' '/etc/.mplab_ide/mchplinusbdevice remove ': No such file or directory
Jun 18 10:51:06 taroona udevd[4181]: failed to execute '/etc/.mplab_ide/mchplinusbdevice' '/etc/.mplab_ide/mchplinusbdevice remove ': No such file or directory
Jun 18 10:51:06 taroona udevd[583]: '/etc/.mplab_ide/mchplinusbdevice remove ' [4179] exit with return code 2
Jun 18 10:51:06 taroona udevd[4178]: '/etc/.mplab_ide/mchplinusbdevice remove ' [4181] exit with return code 2
Jun 18 10:51:06 taroona udevd[583]: passed -1 bytes to netlink monitor 0x7f325ba74dd0
Jun 18 10:51:06 taroona udevd[583]: seq 2466 processed with 0
Jun 18 10:51:06 taroona udevd[4178]: passed -1 bytes to netlink monitor 0x7f325b9dd810
Jun 18 10:51:06 taroona udevd[465]: seq 2466 done with 0
Jun 18 10:51:06 taroona udevd[4178]: seq 2468 processed with 0
Jun 18 10:51:06 taroona modem-manager[979]: <info>  (tty/ttyUSB1): released by modem /sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.4
Jun 18 10:51:06 taroona udevd[465]: seq 2468 done with 0
Jun 18 10:51:06 taroona udevd[465]: passed 199 bytes to netlink monitor 0x7f325b9db2d0
Jun 18 10:51:06 taroona udevd[465]: passed 199 bytes to netlink monitor 0x7f325b9db2d0
Jun 18 10:51:06 taroona udevd[582]: seq 2467 running
Jun 18 10:51:06 taroona modem-manager[979]: <info>  Modem /org/freedesktop/ModemManager/Modems/0: state changed (connected -> disabled)
Jun 18 10:51:06 taroona udevd[583]: seq 2469 running
Jun 18 10:51:06 taroona udevd[582]: device 0x7f325b9db760 filled with db file data
Jun 18 10:51:06 taroona udevd[583]: device 0x7f325b9f05c0 filled with db file data
Jun 18 10:51:06 taroona udevd[582]: RUN '%E{hotplugscript} remove %E{PRODUCT}' /etc/udev/rules.d/z010_mchp_tools.rules:21
Jun 18 10:51:06 taroona udevd[583]: RUN '%E{hotplugscript} remove %E{PRODUCT}' /etc/udev/rules.d/z010_mchp_tools.rules:21
Jun 18 10:51:06 taroona udevd[4185]: starting '/etc/.mplab_ide/mchplinusbdevice remove '
Jun 18 10:51:06 taroona udevd[4186]: starting '/etc/.mplab_ide/mchplinusbdevice remove '
Jun 18 10:51:06 taroona udevd[4185]: failed to execute '/etc/.mplab_ide/mchplinusbdevice' '/etc/.mplab_ide/mchplinusbdevice remove ': No such file or directory
Jun 18 10:51:06 taroona udevd[4186]: failed to execute '/etc/.mplab_ide/mchplinusbdevice' '/etc/.mplab_ide/mchplinusbdevice remove ': No such file or directory
Jun 18 10:51:06 taroona udevd[582]: '/etc/.mplab_ide/mchplinusbdevice remove ' [4185] exit with return code 2
Jun 18 10:51:06 taroona udevd[583]: '/etc/.mplab_ide/mchplinusbdevice remove ' [4186] exit with return code 2
Jun 18 10:51:06 taroona udevd[582]: passed -1 bytes to netlink monitor 0x7f325ba74c70
Jun 18 10:51:06 taroona udevd[582]: seq 2467 processed with 0
Jun 18 10:51:06 taroona udevd[583]: passed -1 bytes to netlink monitor 0x7f325ba74dd0
Jun 18 10:51:06 taroona udevd[583]: seq 2469 processed with 0
Jun 18 10:51:06 taroona udevd[465]: seq 2467 done with 0
Jun 18 10:51:06 taroona udevd[465]: seq 2469 done with 0
Jun 18 10:51:06 taroona NetworkManager[986]: <info> (ttyUSB1): now unmanaged
Jun 18 10:51:06 taroona NetworkManager[986]: <info> (ttyUSB1): device state change: activated -> unmanaged (reason 'removed') [100 10 36]
Jun 18 10:51:06 taroona pppd[2698]: Connection terminated.
Jun 18 10:51:06 taroona udevd[465]: seq 2470 queued, 'remove' 'queues'
Jun 18 10:51:06 taroona udevd[465]: passed 167 bytes to netlink monitor 0x7f325b9db2d0
Jun 18 10:51:06 taroona udevd[465]: seq 2471 queued, 'remove' 'queues'
Jun 18 10:51:06 taroona udevd[582]: seq 2470 running
Jun 18 10:51:06 taroona udevd[465]: passed 167 bytes to netlink monitor 0x7f325b9db2d0
Jun 18 10:51:06 taroona udevd[582]: device 0x7f325b9db760 filled with db file data
Jun 18 10:51:06 taroona udevd[465]: seq 2472 queued, 'remove' 'net'
Jun 18 10:51:06 taroona udevd[582]: RUN '%E{hotplugscript} remove %E{PRODUCT}' /etc/udev/rules.d/z010_mchp_tools.rules:21
Jun 18 10:51:06 taroona udevd[583]: seq 2471 running
Jun 18 10:51:06 taroona udevd[583]: device 0x7f325b9db720 filled with db file data
Jun 18 10:51:06 taroona udevd[583]: RUN '%E{hotplugscript} remove %E{PRODUCT}' /etc/udev/rules.d/z010_mchp_tools.rules:21
Jun 18 10:51:06 taroona udevd[4188]: starting '/etc/.mplab_ide/mchplinusbdevice remove '
Jun 18 10:51:06 taroona udevd[4188]: failed to execute '/etc/.mplab_ide/mchplinusbdevice' '/etc/.mplab_ide/mchplinusbdevice remove ': No such file or directory
Jun 18 10:51:06 taroona udevd[4189]: starting '/etc/.mplab_ide/mchplinusbdevice remove '
Jun 18 10:51:06 taroona udevd[582]: '/etc/.mplab_ide/mchplinusbdevice remove ' [4188] exit with return code 2
Jun 18 10:51:06 taroona udevd[4189]: failed to execute '/etc/.mplab_ide/mchplinusbdevice' '/etc/.mplab_ide/mchplinusbdevice remove ': No such file or directory
Jun 18 10:51:06 taroona udevd[582]: passed -1 bytes to netlink monitor 0x7f325ba74c70
Jun 18 10:51:06 taroona udevd[465]: seq 2470 done with 0
Jun 18 10:51:06 taroona udevd[582]: seq 2470 processed with 0
Jun 18 10:51:06 taroona udevd[583]: '/etc/.mplab_ide/mchplinusbdevice remove ' [4189] exit with return code 2
Jun 18 10:51:06 taroona udevd[583]: passed -1 bytes to netlink monitor 0x7f325ba74dd0
Jun 18 10:51:06 taroona udevd[583]: seq 2471 processed with 0
Jun 18 10:51:06 taroona udevd[465]: seq 2471 done with 0
Jun 18 10:51:06 taroona udevd[465]: passed 177 bytes to netlink monitor 0x7f325b9db2d0
Jun 18 10:51:06 taroona udevd[582]: seq 2472 running
Jun 18 10:51:06 taroona udevd[582]: device 0x7f325b9db760 filled with db file data
Jun 18 10:51:06 taroona udevd[582]: RUN '%E{hotplugscript} remove %E{PRODUCT}' /etc/udev/rules.d/z010_mchp_tools.rules:21
Jun 18 10:51:06 taroona udevd[4190]: starting '/etc/.mplab_ide/mchplinusbdevice remove '
Jun 18 10:51:06 taroona udevd[4190]: failed to execute '/etc/.mplab_ide/mchplinusbdevice' '/etc/.mplab_ide/mchplinusbdevice remove ': No such file or directory
Jun 18 10:51:06 taroona udevd[582]: '/etc/.mplab_ide/mchplinusbdevice remove ' [4190] exit with return code 2
Jun 18 10:51:06 taroona udevd[582]: passed -1 bytes to netlink monitor 0x7f325ba74c70
Jun 18 10:51:06 taroona udevd[582]: seq 2472 processed with 0
Jun 18 10:51:06 taroona udevd[465]: seq 2472 done with 0
Jun 18 10:51:06 taroona NetworkManager[986]: <info> (ttyUSB1): deactivating device (reason 'removed') [36]
Jun 18 10:51:06 taroona NetworkManager[986]: <warn> could not read ppp stats: No such device
Jun 18 10:51:06 taroona NetworkManager[986]: nm_system_iface_flush_routes: assertion `ifindex > 0' failed
Jun 18 10:51:06 taroona NetworkManager[986]: nm_system_iface_flush_addresses: assertion `ifindex > 0' failed
Jun 18 10:51:06 taroona dnsmasq[2726]: exiting on receipt of SIGTERM
Jun 18 10:51:06 taroona NetworkManager[986]: <info> DNS: starting dnsmasq...
Jun 18 10:51:06 taroona NetworkManager[986]: <info> (ttyUSB1): writing resolv.conf to /sbin/resolvconf
Jun 18 10:51:06 taroona dnsmasq[4218]: started, version 2.59 cache disabled
Jun 18 10:51:06 taroona dnsmasq[4218]: compile time options: IPv6 GNU-getopt DBus i18n DHCP TFTP conntrack IDN
Jun 18 10:51:06 taroona dnsmasq[4218]: warning: no upstream servers configured
Jun 18 10:51:06 taroona NetworkManager[986]: <info> (ttyUSB1): cleaning up...
Jun 18 10:51:06 taroona NetworkManager[986]: <info> (ttyUSB1): taking down device.
Jun 18 10:51:06 taroona NetworkManager[986]: <info> Unmanaged Device found; state CONNECTED forced. (see http://bugs.launchpad.net/bugs/191889)
Jun 18 10:51:06 taroona dbus[958]: [system] Activating service name='org.freedesktop.nm_dispatcher' (using servicehelper)
Jun 18 10:51:06 taroona NetworkManager[986]:    SCPlugin-Ifupdown: devices removed (path: /sys/devices/virtual/net/ppp0, iface: ppp0)
Jun 18 10:51:06 taroona dbus[958]: [system] Successfully activated service 'org.freedesktop.nm_dispatcher'
Jun 18 10:51:08 taroona pppd[2698]: Exit.
Jun 18 10:51:09 taroona udevd[465]: worker [582] exit
Jun 18 10:51:09 taroona udevd[465]: worker [582] cleaned up
Jun 18 10:51:15 taroona kernel: [  843.094450] usb 2-1.4: reset high-speed USB device number 4 using ehci_hcd
Jun 18 10:51:15 taroona kernel: [  843.328364] /dev/vmnet: open called by PID 4184 (vmx-vcpu-3)
Jun 18 10:51:15 taroona kernel: [  843.328377] /dev/vmnet: port on hub 8 successfully opened
Jun 18 10:51:15 taroona kernel: [  843.328389] /dev/vmnet: open called by PID 4184 (vmx-vcpu-3)
Jun 18 10:51:15 taroona kernel: [  843.328395] /dev/vmnet: port on hub 8 successfully opened
Jun 18 10:51:15 taroona kernel: [  843.465896] usb 2-1.4: reset high-speed USB device number 4 using ehci_hcd

```

Edit: I've just done a bit more experimenting and found that not all of my VMWare images exhibit the same problem.  In fact it appears to only be my Ubuntu 12.04 LTS (**32-bit**) image that is causing this issue.

---

### Post by NomadAU on 2013-06-17
Solved!!

Embarrassing as it is, I felt I must close this out and update the forum...who knows, there may be others out there who are as silly as me :-)

The reason the 3G was 'disappearing' when I started a particular VM guest image was that the VM image was connecting to it!!!  Looking under the VM tab, Removable Devices, I found Gobi 2000 listed...and the option to disconnect and reconnect it to the host.  Once I saw this, it all made perfect sense.  Simply setting it back to connected to host resolved the problem.  Doh!!!

---

