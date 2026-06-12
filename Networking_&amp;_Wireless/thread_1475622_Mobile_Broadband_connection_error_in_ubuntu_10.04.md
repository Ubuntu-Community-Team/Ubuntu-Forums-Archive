---
title: "Mobile Broadband connection error in ubuntu 10.04"
date: 2010-05-07
forum: Networking &amp; Wireless
---

### Post by Kbipinkumar on 2010-05-07
Hi
 
 i recently installed ubuntu 10.04 in my laptop. everything is working fine except for my mobile broadband connection. i use a huawei ec1260 USB 3g modem to connect to the net. the OS detects the modem fine and the network manger applet prompts me to set up the connection as well i.e entering the username, password,  number to be dialled etc. however when i actually try to dial the connection the applet icon flashes for a long while and a notification pops up saying connection disconnected. has anyone come across same kind of problem and solutions, if any.

  Earlier i used the same modem in in karmic i was able to connect to net and even now i am able to connect using the modem in windows 7 as well

hope some one has an answer

Bipin

---

### Post by dineshs on 2010-05-07
pl post the output of
```
lsusb
```
```
dmesg | grep -e "modem" -e "tty"
```
You can try any of the following methods if NM is not working.I suggest pppconfig
[http://www.ubuntugeek.com/setting-up-dial-up-connection-in-ubuntu.html](http://www.ubuntugeek.com/setting-up-dial-up-connection-in-ubuntu.html)

---

### Post by Kbipinkumar on 2010-05-14
> **dineshs said:**
> pl post the output of
```
lsusb
``````
dmesg | grep -e "modem" -e "tty"
```You can try any of the following methods if NM is not working.I suggest pppconfig
[http://www.ubuntugeek.com/setting-up-dial-up-connection-in-ubuntu.html](http://www.ubuntugeek.com/setting-up-dial-up-connection-in-ubuntu.html)

Here's the lsusb output as you have asked 

Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 002: ID 045e:00cb Microsoft Corp. Basic Optical Mouse v2.0
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
**Bus 005 Device 003: ID 12d1:140b Huawei Technologies Co., Ltd. **
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 0a5c:2150 Broadcom Corp. 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 090c:7371 Feiya Technology Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 0bda:0158 Realtek Semiconductor Corp. Mass Storage Device
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

---

### Post by dineshs on 2010-05-14
what about ```
dmesg | grep -e "modem" -e "tty"
```

---

### Post by Kbipinkumar on 2010-05-15
> **dineshs said:**
> what about ```
dmesg | grep -e "modem" -e "tty"
```

heres is the output for the command

[    0.000000] console [tty0] enabled

---

### Post by glabu on 2010-05-26
i have the same problem like Kbipinkumar

when plugging in the stick /var/log/syslog shows the following messages:
```
May 26 19:38:51 tony-sony kernel: [ 3769.392990] usb 2-1.1: new full speed USB device using ehci_hcd and address 27
May 26 19:38:51 tony-sony kernel: [ 3769.506764] usb 2-1.1: configuration #1 chosen from 1 choice
May 26 19:38:51 tony-sony kernel: [ 3769.507146] hso 2-1.1:1.0: Not our interface
May 26 19:38:51 tony-sony kernel: [ 3769.589508] usb-storage: probe of 2-1.1:1.0 failed with error -5
May 26 19:38:51 tony-sony kernel: [ 3769.589970] usb 2-1.1: USB disconnect, address 27
May 26 19:38:53 tony-sony kernel: [ 3771.954201] usb 2-1.1: new full speed USB device using ehci_hcd and address 28
May 26 19:38:53 tony-sony NetworkManager: <info>  Found wwan radio killswitch rfkill19 (at /sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.1/rfkill/rfkill19) (driver usb)
May 26 19:38:53 tony-sony kernel: [ 3772.066861] usb 2-1.1: configuration #1 chosen from 1 choice
May 26 19:38:53 tony-sony kernel: [ 3772.067959] hso0: Disabled Privacy Extensions
May 26 19:38:53 tony-sony NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.1/2-1.1:1.0/net/hso0, iface: hso0)
May 26 19:38:53 tony-sony NetworkManager:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.1/2-1.1:1.0/net/hso0, iface: hso0): no ifupdown configuration found.
May 26 19:38:53 tony-sony modem-manager: (ttyHS1) opening serial device...
May 26 19:38:53 tony-sony modem-manager: (ttyHS1): probe requested by plugin 'Option High-Speed'
May 26 19:38:53 tony-sony modem-manager: (Option High-Speed): GSM modem /sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.1 claimed port hso0
May 26 19:38:53 tony-sony modem-manager: Added modem /sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.1
May 26 19:38:53 tony-sony modem-manager: (ttyHS0) opening serial device...
May 26 19:38:53 tony-sony modem-manager: (ttyHS0): probe requested by plugin 'Option High-Speed'
May 26 19:38:53 tony-sony modem-manager: (ttyHS2) opening serial device...
May 26 19:38:53 tony-sony modem-manager: (ttyHS2): probe requested by plugin 'Option High-Speed'
May 26 19:38:56 tony-sony modem-manager: (ttyHS1) closing serial device...
May 26 19:38:56 tony-sony modem-manager: (ttyHS0) closing serial device...
May 26 19:38:56 tony-sony modem-manager: (Option High-Speed): GSM modem /sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.1 claimed port ttyHS1
May 26 19:38:56 tony-sony modem-manager: Exported modem /sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.1 as /org/freedesktop/ModemManager/Modems/16
May 26 19:38:56 tony-sony modem-manager: (Option High-Speed): GSM modem /sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.1 claimed port ttyHS0
May 26 19:38:56 tony-sony NetworkManager: <info>  (hso0): new GSM device (driver: 'hso')
May 26 19:38:56 tony-sony NetworkManager: <info>  (hso0): exported as /org/freedesktop/NetworkManager/Devices/18
May 26 19:38:56 tony-sony NetworkManager: <info>  (hso0): now managed
May 26 19:38:56 tony-sony NetworkManager: <info>  (hso0): device state change: 1 -> 2 (reason 2)
May 26 19:38:56 tony-sony NetworkManager: <info>  (hso0): deactivating device (reason: 2).
May 26 19:38:56 tony-sony NetworkManager: <info>  (hso0): device state change: 2 -> 3 (reason 0)
May 26 19:38:59 tony-sony kernel: [ 3777.346351] usb 2-1.1: USB disconnect, address 28
May 26 19:38:59 tony-sony NetworkManager: <info>  Radio killswitch /sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.1/rfkill/rfkill19 disappeared
May 26 19:38:59 tony-sony modem-manager: Removed modem /sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.1
May 26 19:38:59 tony-sony NetworkManager: <info>  (hso0): now unmanaged
May 26 19:38:59 tony-sony NetworkManager: <info>  (hso0): device state change: 3 -> 1 (reason 36)
May 26 19:38:59 tony-sony NetworkManager: <info>  (hso0): cleaning up...
May 26 19:38:59 tony-sony NetworkManager: <info>  (hso0): taking down device.
May 26 19:38:59 tony-sony NetworkManager: <info>  Unmanaged Device found; state CONNECTED forced. (see http://bugs.launchpad.net/bugs/191889)
May 26 19:38:59 tony-sony NetworkManager: <info>  Unmanaged Device found; state CONNECTED forced. (see http://bugs.launchpad.net/bugs/191889)
May 26 19:38:59 tony-sony NetworkManager:    SCPlugin-Ifupdown: devices removed (path: /sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.1/2-1.1:1.0/net/hso0, iface: hso0)
May 26 19:38:59 tony-sony modem-manager: (ttyHS2) closing serial device...
May 26 19:38:59 tony-sony kernel: [ 3777.777013] usb 2-1.1: new full speed USB device using ehci_hcd and address 29
May 26 19:38:59 tony-sony kernel: [ 3777.887435] usb 2-1.1: device descriptor read/all, error -32
May 26 19:38:59 tony-sony kernel: [ 3777.908118] hub 2-1:1.0: unable to enumerate USB device on port 1
May 26 19:39:02 tony-sony kernel: [ 3780.518279] hub 2-1:1.0: connect-debounce failed, port 1 disabled
May 26 19:39:04 tony-sony kernel: [ 3782.509243] usb 2-1.1: new full speed USB device using ehci_hcd and address 31
May 26 19:39:04 tony-sony NetworkManager: <info>  Found wwan radio killswitch rfkill20 (at /sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.1/rfkill/rfkill20) (driver usb)
May 26 19:39:04 tony-sony kernel: [ 3782.632558] usb 2-1.1: configuration #1 chosen from 1 choice
May 26 19:39:04 tony-sony kernel: [ 3782.633549] hso0: Disabled Privacy Extensions
May 26 19:39:04 tony-sony modem-manager: (ttyHS0) opening serial device...
May 26 19:39:04 tony-sony modem-manager: (ttyHS0): probe requested by plugin 'Option High-Speed'
May 26 19:39:04 tony-sony NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.1/2-1.1:1.0/net/hso0, iface: hso0)
May 26 19:39:04 tony-sony NetworkManager:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.1/2-1.1:1.0/net/hso0, iface: hso0): no ifupdown configuration found.
May 26 19:39:04 tony-sony modem-manager: (Option High-Speed): GSM modem /sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.1 claimed port hso0
May 26 19:39:04 tony-sony modem-manager: Added modem /sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.1
May 26 19:39:04 tony-sony modem-manager: (ttyHS1) opening serial device...
May 26 19:39:04 tony-sony modem-manager: (ttyHS1): probe requested by plugin 'Option High-Speed'
May 26 19:39:04 tony-sony modem-manager: (ttyHS2) opening serial device...
May 26 19:39:04 tony-sony modem-manager: (ttyHS2): probe requested by plugin 'Option High-Speed'
May 26 19:39:06 tony-sony modem-manager: (ttyHS0) closing serial device...
May 26 19:39:06 tony-sony modem-manager: Exported modem /sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.1 as /org/freedesktop/ModemManager/Modems/17
May 26 19:39:06 tony-sony modem-manager: (Option High-Speed): GSM modem /sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.1 claimed port ttyHS0
May 26 19:39:06 tony-sony modem-manager: (ttyHS1) closing serial device...
May 26 19:39:06 tony-sony modem-manager: (Option High-Speed): GSM modem /sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.1 claimed port ttyHS1
May 26 19:39:06 tony-sony NetworkManager: <info>  (hso0): new GSM device (driver: 'hso')
May 26 19:39:06 tony-sony NetworkManager: <info>  (hso0): exported as /org/freedesktop/NetworkManager/Devices/19
May 26 19:39:06 tony-sony NetworkManager: <info>  (hso0): now managed
May 26 19:39:06 tony-sony NetworkManager: <info>  (hso0): device state change: 1 -> 2 (reason 2)
May 26 19:39:06 tony-sony NetworkManager: <info>  (hso0): deactivating device (reason: 2).
May 26 19:39:06 tony-sony NetworkManager: <info>  (hso0): device state change: 2 -> 3 (reason 0)

```
does not seem to be a problem

when trying to get a connection, the same log shows this messages:
```
May 26 19:39:33 tony-sony NetworkManager: <info>  Activation (hso0) starting connection 'T-Mobile Internet 1'
May 26 19:39:33 tony-sony NetworkManager: <info>  (hso0): device state change: 3 -> 4 (reason 0)
May 26 19:39:33 tony-sony NetworkManager: <info>  Activation (hso0) Stage 1 of 5 (Device Prepare) scheduled...
May 26 19:39:33 tony-sony NetworkManager: <info>  Activation (hso0) Stage 1 of 5 (Device Prepare) started...
May 26 19:39:33 tony-sony NetworkManager: <info>  Activation (hso0) Stage 1 of 5 (Device Prepare) complete.
May 26 19:39:33 tony-sony modem-manager: (ttyHS0) opening serial device...
May 26 19:39:33 tony-sony modem-manager: Modem /org/freedesktop/ModemManager/Modems/17: state changed (disabled -> enabling)
May 26 19:39:34 tony-sony modem-manager: Modem /org/freedesktop/ModemManager/Modems/17: state changed (enabling -> enabled)
May 26 19:39:35 tony-sony modem-manager: Registration state changed: 1
May 26 19:39:35 tony-sony modem-manager: Modem /org/freedesktop/ModemManager/Modems/17: state changed (enabled -> registered)
May 26 19:39:39 tony-sony modem-manager: (ttyHS0) closing serial device...
May 26 19:39:39 tony-sony NetworkManager: <info>  Radio killswitch /sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.1/rfkill/rfkill20 disappeared
May 26 19:39:39 tony-sony modem-manager: Modem /org/freedesktop/ModemManager/Modems/17: state changed (registered -> disabled)
May 26 19:39:39 tony-sony modem-manager: Removed modem /sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.1
May 26 19:39:39 tony-sony modem-manager: mm_callback_info_schedule: assertion `info->pending_id == 0' failed
May 26 19:39:39 tony-sony modem-manager: mm_callback_info_schedule: assertion `info->called == FALSE' failed
May 26 19:39:39 tony-sony NetworkManager: <info>  (hso0): now unmanaged
May 26 19:39:39 tony-sony NetworkManager: <info>  (hso0): device state change: 4 -> 1 (reason 36)
May 26 19:39:39 tony-sony NetworkManager: <info>  (hso0): deactivating device (reason: 36).
May 26 19:39:39 tony-sony kernel: [ 3818.051326] usb 2-1.1: USB disconnect, address 31
May 26 19:39:40 tony-sony NetworkManager: <info>  (hso0): cleaning up...
May 26 19:39:40 tony-sony NetworkManager: <info>  (hso0): taking down device.
May 26 19:39:40 tony-sony NetworkManager: <info>  Unmanaged Device found; state CONNECTED forced. (see http://bugs.launchpad.net/bugs/191889)
May 26 19:39:40 tony-sony NetworkManager: <info>  Unmanaged Device found; state CONNECTED forced. (see http://bugs.launchpad.net/bugs/191889)
May 26 19:39:40 tony-sony NetworkManager:    SCPlugin-Ifupdown: devices removed (path: /sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.1/2-1.1:1.0/net/hso0, iface: hso0)
May 26 19:39:42 tony-sony kernel: [ 3820.597031] hub 2-1:1.0: connect-debounce failed, port 1 disabled

```
does somebody know whats going on there and how to fix it? the same usb stick works still great on karmic on my other notebook....

---

### Post by pdc on 2010-05-27
> does somebody know whats going on there and how to fix it?

No

> the same usb stick works still great on karmic on my other notebook.... 

so maybe stick with what works ............

---

### Post by klemes on 2010-05-27
I have the exact same issue with Network Manager in 10.04 using my Nokia N78 3G modem to connect to the Internet.Solved it by using _wvdial_.It works fine now.It's got to do with some bug with the Network Manager.Let's hope it will get fixed soon in some future updated version of it.
Oh and do not forget to unplug your modem from the USB port prior to connecting with wvdial because if you have tried to connect earlier with Network Manager your modem will be in a non-responding state.

---

### Post by ubun2warrior on 2010-05-27
Hi Kbipinkumar

I once used a 3g modem to connect to the net in Ubuntu. I faced a similar problem. Just right click network manager>edit connection> mobile broadband> select your 3g connection> edit> then go to IPV4> there in the method select Automatic(PPP). 
Then save and close.
That should solve the problem.

---

### Post by shebaw on 2010-05-27
I had the exact problem, I was able to use my Huawei modem without any problem in Karmic but it didn't work on Lucid. This is how to solve it, install usb-modswitch from synaptic and it should work after that. You could have looked on the sticky on the known issues of Lucid, anyways, that's how I solved my problem and I'm using my Huawei modem to connect to the net. 
Hope this helps.

---

