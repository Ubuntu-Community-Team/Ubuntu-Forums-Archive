---
title: "modem-manager error crash and restarting continusly"
date: 2013-02-12
forum: Networking &amp; Wireless
---

### Post by redjocker on 2013-02-12
Hello everybody, 

I have a Ubuntu 12.10 64Bits on a Toshiba laptop R700.
My laptop have a built in Ericson 3G card, and with previous versions of ubuntu it worked fine for me, but not now.

The modem-manager crash all times, and two three times in a hour. (see picture attached).

And my sys.log continuously repeat the same messages, and  looks like this:
```

Feb 12 23:48:47 R700 kernel: [ 6062.462146] usb 1-1.5: **new high-speed USB device number [COLOR=Red]39[/COLOR] using ehci_hcd**
Feb 12 23:48:47 R700 kernel: [ 6062.559434] usb 1-1.5: New USB device found, idVendor=0930, idProduct=1311
Feb 12 23:48:47 R700 kernel: [ 6062.559442] usb 1-1.5: New USB device strings: Mfr=1, Product=2, SerialNumber=3
Feb 12 23:48:47 R700 kernel: [ 6062.559446] usb 1-1.5: Product: F3607gw
Feb 12 23:48:47 R700 kernel: [ 6062.559450] usb 1-1.5: Manufacturer: 0    F3607gw
Feb 12 23:48:47 R700 kernel: [ 6062.559453] usb 1-1.5: SerialNumber: 3564000301320640
Feb 12 23:48:47 R700 mtp-probe: checking bus 1, device 39: "/sys/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.5"
Feb 12 23:48:47 R700 kernel: [ 6062.564233] cdc_acm 1-1.5:1.1: ttyACM0: USB ACM device
Feb 12 23:48:47 R700 kernel: [ 6062.580203] cdc_acm 1-1.5:1.3: ttyACM1: USB ACM device
Feb 12 23:48:47 R700 kernel: [ 6062.596175] cdc_wdm 1-1.5:1.5: cdc-wdm0: USB WDM device
Feb 12 23:48:47 R700 kernel: [ 6062.599150] cdc_ether 1-1.5:1.6: wwan0: register 'cdc_ether' at usb-0000:00:1a.0-1.5, Mobile Broadband Network Device, 02:80:37:ec:02:00
Feb 12 23:48:47 R700 kernel: [ 6062.600527] cdc_wdm 1-1.5:1.8: cdc-wdm1: USB WDM device
Feb 12 23:48:47 R700 kernel: [ 6062.601169] cdc_acm 1-1.5:1.9: ttyACM2: USB ACM device
Feb 12 23:48:47 R700 mtp-probe: bus: 1, device: 39 was not an MTP device
Feb 12 23:48:47 R700 modem-manager[14519]: supports_port: assertion `task == NULL' failed
Feb 12 23:48:47 R700 modem-manager[14519]: <info>  (ttyACM0) opening serial port...
Feb 12 23:48:47 R700 NetworkManager[984]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.5/1-1.5:1.6/net/wwan0, iface: wwan0)
Feb 12 23:48:47 R700 NetworkManager[984]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.5/1-1.5:1.6/net/wwan0, iface: wwan0): no ifupdown configuration found.
Feb 12 23:48:47 R700 modem-manager[14519]: supports_port: assertion `task == NULL' failed
Feb 12 23:48:47 R700 modem-manager[14519]: <info>  (ttyACM2) opening serial port...
Feb 12 23:48:47 R700 modem-manager[14519]: <info>  (ttyACM1) opening serial port...
Feb 12 23:48:47 R700 modem-manager[14519]: <info>  (Ericsson MBM): GSM modem /sys/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.5 claimed port wwan0
Feb 12 23:48:50 R700 modem-manager[14519]: <info>  (ttyACM0) closing serial port...
Feb 12 23:48:50 R700 modem-manager[14519]: <info>  (ttyACM0) serial port closed
Feb 12 23:48:50 R700 modem-manager[14519]: <warn>  Couldn't probe for capabilities, probably not a GSM or CDMA modem
Feb 12 23:48:50 R700 modem-manager[14519]: supports_port: assertion `task == NULL' failed
Feb 12 23:48:50 R700 kernel: [ 6065.839804] usb 1-1.5: USB disconnect, device number 39
Feb 12 23:48:50 R700 modem-manager[14519]: <info>  (ttyACM1) closing serial port...
Feb 12 23:48:50 R700 modem-manager[14519]: <info>  (ttyACM1) serial port closed
Feb 12 23:48:50 R700 kernel: [ 6065.844927] cdc_ether 1-1.5:1.6: wwan0: unregister 'cdc_ether' usb-0000:00:1a.0-1.5, Mobile Broadband Network Device
Feb 12 23:48:50 R700 avahi-daemon[1010]: Withdrawing workstation service for wwan0.
Feb 12 23:48:50 R700 modem-manager[14519]: mm_serial_port_close: assertion `priv->open_count > 0' failed
Feb 12 23:48:50 R700 NetworkManager[984]:    SCPlugin-Ifupdown: devices removed (path: /sys/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.5/1-1.5:1.6/net/wwan0, iface: wwan0)
Feb 12 23:48:50 R700 modem-manager[14519]: <info>  (net/wwan0): released by modem /sys/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.5
Feb 12 23:48:50 R700 modem-manager[14519]: <info>  (ttyACM2) closing serial port...
Feb 12 23:48:50 R700 modem-manager[14519]: <info>  (ttyACM2) serial port closed
Feb 12 23:48:50 R700 modem-manager[14519]: <warn>  Couldn't probe for capabilities, probably not a GSM or CDMA modem
Feb 12 23:48:50 R700 modem-manager[14519]: supports_port: assertion `task == NULL' failed
Feb 12 23:48:50 R700 modem-manager[14519]: <error> Failed to organize modem ports: (0) Failed to find primary port.
Feb 12 23:48:50 R700 modem-manager[14519]: marshal_object: assertion `g_variant_is_object_path (path)' failed
Feb 12 23:48:50 R700 modem-manager[14519]: failed to marshal parameter 1 for signal DeviceRemoved
Feb 12 23:48:52 R700 kernel: [ 6067.824759]** usb 1-1.5: new high-speed USB device number [COLOR=Red]40[/COLOR] using ehci_hcd**
Feb 12 23:48:52 R700 kernel: [ 6067.921869] usb 1-1.5: New USB device found, idVendor=0930, idProduct=1311
Feb 12 23:48:52 R700 kernel: [ 6067.921876] usb 1-1.5: New USB device strings: Mfr=1, Product=2, SerialNumber=3
Feb 12 23:48:52 R700 kernel: [ 6067.921881] usb 1-1.5: Product: F3607gw
Feb 12 23:48:52 R700 kernel: [ 6067.921885] usb 1-1.5: Manufacturer: 0    F3607gw
Feb 12 23:48:52 R700 kernel: [ 6067.921888] usb 1-1.5: SerialNumber: 3564000301320640
Feb 12 23:48:52 R700 mtp-probe: checking bus 1, device 40: "/sys/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.5"
Feb 12 23:48:52 R700 kernel: [ 6067.926929] cdc_acm 1-1.5:1.1: ttyACM0: USB ACM device
Feb 12 23:48:52 R700 kernel: [ 6067.940538] cdc_acm 1-1.5:1.3: ttyACM1: USB ACM device
Feb 12 23:48:52 R700 kernel: [ 6067.956554] cdc_wdm 1-1.5:1.5: cdc-wdm0: USB WDM device
Feb 12 23:48:52 R700 kernel: [ 6067.959373] cdc_ether 1-1.5:1.6: wwan0: register 'cdc_ether' at usb-0000:00:1a.0-1.5, Mobile Broadband Network Device, 02:80:37:ec:02:00
Feb 12 23:48:52 R700 kernel: [ 6067.960675] cdc_wdm 1-1.5:1.8: cdc-wdm1: USB WDM device
Feb 12 23:48:52 R700 kernel: [ 6067.961343] cdc_acm 1-1.5:1.9: ttyACM2: USB ACM device
Feb 12 23:48:52 R700 mtp-probe: bus: 1, device: 40 was not an MTP device
Feb 12 23:48:52 R700 NetworkManager[984]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.5/1-1.5:1.6/net/wwan0, iface: wwan0)
Feb 12 23:48:52 R700 NetworkManager[984]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.5/1-1.5:1.6/net/wwan0, iface: wwan0): no ifupdown configuration found.
Feb 12 23:48:52 R700 modem-manager[14519]: supports_port: assertion `task == NULL' failed
Feb 12 23:48:52 R700 modem-manager[14519]: supports_port: assertion `task == NULL' failed
Feb 12 23:48:52 R700 modem-manager[14519]: <info>  (ttyACM1) opening serial port...
Feb 12 23:48:52 R700 modem-manager[14519]: <info>  (ttyACM2) opening serial port...
Feb 12 23:48:52 R700 modem-manager[14519]: <info>  (Ericsson MBM): GSM modem /sys/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.5 claimed port wwan0
Feb 12 23:48:52 R700 modem-manager[14519]: <info>  (ttyACM0) opening serial port...
Feb 12 23:48:56 R700 modem-manager[14519]: <info>  (ttyACM0) closing serial port...
Feb 12 23:48:56 R700 modem-manager[14519]: <info>  (ttyACM0) serial port closed
Feb 12 23:48:56 R700 modem-manager[14519]: <warn>  Couldn't probe for capabilities, probably not a GSM or CDMA modem
Feb 12 23:48:56 R700 modem-manager[14519]: supports_port: assertion `task == NULL' failed
Feb 12 23:48:56 R700 kernel: [ 6071.202337] usb 1-1.5: USB disconnect, device number 40
Feb 12 23:48:56 R700 modem-manager[14519]: <info>  (ttyACM1) closing serial port...
Feb 12 23:48:56 R700 modem-manager[14519]: <info>  (ttyACM1) serial port closed
Feb 12 23:48:56 R700 modem-manager[14519]: <warn>  Couldn't probe for capabilities, probably not a GSM or CDMA modem
Feb 12 23:48:56 R700 kernel: [ 6071.210691] cdc_ether 1-1.5:1.6: wwan0: unregister 'cdc_ether' usb-0000:00:1a.0-1.5, Mobile Broadband Network Device
Feb 12 23:48:56 R700 avahi-daemon[1010]: Withdrawing workstation service for wwan0.
Feb 12 23:48:56 R700 NetworkManager[984]:    SCPlugin-Ifupdown: devices removed (path: /sys/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.5/1-1.5:1.6/net/wwan0, iface: wwan0)
Feb 12 23:48:56 R700 modem-manager[14519]: mm_serial_port_close: assertion `priv->open_count > 0' failed
Feb 12 23:48:56 R700 modem-manager[14519]: <info>  (net/wwan0): released by modem /sys/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.5
Feb 12 23:48:56 R700 modem-manager[14519]: <info>  (ttyACM2) closing serial port...
Feb 12 23:48:56 R700 modem-manager[14519]: <info>  (ttyACM2) serial port closed
Feb 12 23:48:56 R700 modem-manager[14519]: <warn>  Couldn't probe for capabilities, probably not a GSM or CDMA modem
Feb 12 23:48:56 R700 modem-manager[14519]: supports_port: assertion `task == NULL' failed
Feb 12 23:48:56 R700 modem-manager[14519]: <error> Failed to organize modem ports: (0) Failed to find primary port.
Feb 12 23:48:56 R700 modem-manager[14519]: marshal_object: assertion `g_variant_is_object_path (path)' failed
Feb 12 23:48:56 R700 modem-manager[14519]: failed to marshal parameter 1 for signal DeviceRemoved
Feb 12 23:48:58 R700 kernel: [ 6073.187087] usb 1-1.5: new high-speed USB device number 41 using ehci_hcd

```My /var/log/boot.log is:

```

fsck de util-linux 2.20.1 
/dev/sda1: clean, 413343/15122432 files, 23733245/60486912 blocks 
modem-manager[961]: <info>  ModemManager (version 0.6.0.0) starting... 
  
modem-manager[961]: <info>  Loaded plugin 'Samsung' 
  
modem-manager[961]: <info>  Loaded plugin 'Option High-Speed' 
  
modem-manager[961]: <info>  Loaded plugin 'SimTech' 
  
modem-manager[961]: <info>  Loaded plugin 'Nokia' 
  
modem-manager[961]: <info>  Loaded plugin 'Linktop' 
  
modem-manager[961]: <info>  Loaded plugin 'Gobi' 
  
modem-manager[961]: <info>  Loaded plugin 'AnyData' 
  
modem-manager[961]: <info>  Loaded plugin 'X22X' 
  
modem-manager[961]: <info>  Loaded plugin 'Novatel' 
  
modem-manager[961]: <info>  Loaded plugin 'Longcheer' 
  
modem-manager[961]: <info>  Loaded plugin 'Wavecom' 
  
modem-manager[961]: <info>  Loaded plugin 'Huawei' 
  
modem-manager[961]: <info>  Loaded plugin 'ZTE' 
  
modem-manager[961]: <info>  Loaded plugin 'MotoC' 
  
modem-manager[961]: <info>  Loaded plugin 'Option' 
  
modem-manager[961]: <info>  Loaded plugin 'Ericsson MBM' 
  
modem-manager[961]: <info>  Loaded plugin 'Sierra' 
  
modem-manager[961]: <info>  Loaded plugin 'Cinterion' 
  
modem-manager[961]: <info>  Loaded plugin 'Iridium' 
  
modem-manager[961]: <info>  Loaded plugin 'Generic' 
  
modem-manager[961]: <info>  Successfully loaded 20 plugins 
  
Skipping profile in /etc/apparmor.d/disable: usr.bin.firefox 
Skipping profile in /etc/apparmor.d/disable: usr.sbin.rsyslogd 
 * Starting AppArmor profiles       [170G  [164G[ OK ] 
speech-dispatcher disabled; edit /etc/default/speech-dispatcher


```Hope you can help me to find a solution ;)
Thank you.

---

### Post by antek88 on 2013-05-13
Hello,


I have similar problem on Toshiba r930
Ubuntu 12.10 64bit, updated to 13.04 and error still occur.


My syslog:
```
May 13 21:32:12 piotr-PORTEGE-R930 kernel: [  720.104607] usbhid 2-1.6:1.0: can't add hid device: -71
May 13 21:32:12 piotr-PORTEGE-R930 kernel: [  720.104634] usbhid: probe of 2-1.6:1.0 failed with error -71
May 13 21:32:12 piotr-PORTEGE-R930 kernel: [  720.104977] usb 2-1.6: USB disconnect, device number 42
May 13 21:32:14 piotr-PORTEGE-R930 kernel: [  722.015378] usb 2-1.6: new high-speed USB device number 43 using ehci-pci
May 13 21:32:14 piotr-PORTEGE-R930 kernel: [  722.111332] usb 2-1.6: New USB device found, idVendor=0930, idProduct=1319
May 13 21:32:14 piotr-PORTEGE-R930 kernel: [  722.111339] usb 2-1.6: New USB device strings: Mfr=1, Product=2, SerialNumber=3
May 13 21:32:14 piotr-PORTEGE-R930 kernel: [  722.111343] usb 2-1.6: Product: H5321 gw
May 13 21:32:14 piotr-PORTEGE-R930 kernel: [  722.111347] usb 2-1.6: Manufacturer: TOSHIBA 
May 13 21:32:14 piotr-PORTEGE-R930 kernel: [  722.111350] usb 2-1.6: SerialNumber: xxx
May 13 21:32:14 piotr-PORTEGE-R930 kernel: [  722.143025] cdc_acm 2-1.6:1.1: ttyACM0: USB ACM device
May 13 21:32:14 piotr-PORTEGE-R930 kernel: [  722.146885] cdc_acm 2-1.6:1.3: ttyACM1: USB ACM device
May 13 21:32:14 piotr-PORTEGE-R930 kernel: [  722.155347] cdc_wdm 2-1.6:1.5: cdc-wdm1: USB WDM device
May 13 21:32:14 piotr-PORTEGE-R930 kernel: [  722.182502] cdc_mbim 2-1.6:1.6: cdc-wdm2: USB WDM device
May 13 21:32:14 piotr-PORTEGE-R930 kernel: [  722.182833] cdc_mbim 2-1.6:1.6 wwan0: register 'cdc_mbim' at usb-0000:00:1d.0-1.6, CDC MBIM, 96:cc:b1:e3:51:e1
May 13 21:32:14 piotr-PORTEGE-R930 kernel: [  722.183728] cdc_wdm 2-1.6:1.8: cdc-wdm3: USB WDM device
May 13 21:32:14 piotr-PORTEGE-R930 kernel: [  722.184056] cdc_acm 2-1.6:1.9: ttyACM2: USB ACM device
May 13 21:32:14 piotr-PORTEGE-R930 mtp-probe: checking bus 2, device 43: "/sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.6"
May 13 21:32:14 piotr-PORTEGE-R930 mtp-probe: bus: 2, device: 43 was not an MTP device
May 13 21:32:14 piotr-PORTEGE-R930 NetworkManager[1073]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.6/2-1.6:1.6/net/wwan0, iface: wwan0)
May 13 21:32:14 piotr-PORTEGE-R930 NetworkManager[1073]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.6/2-1.6:1.6/net/wwan0, iface: wwan0): no ifupdown configuration found.
May 13 21:32:14 piotr-PORTEGE-R930 modem-manager[1032]: <info>  (ttyACM0) opening serial port...
May 13 21:32:14 piotr-PORTEGE-R930 modem-manager[1032]: <info>  (ttyACM2) opening serial port...
May 13 21:32:14 piotr-PORTEGE-R930 modem-manager[1032]: <info>  (ttyACM1) opening serial port...
May 13 21:32:19 piotr-PORTEGE-R930 modem-manager[1032]: <info>  (ttyACM0) closing serial port...
May 13 21:32:19 piotr-PORTEGE-R930 modem-manager[1032]: <info>  (ttyACM0) serial port closed
May 13 21:32:19 piotr-PORTEGE-R930 modem-manager[1032]: <info>  (Generic): GSM modem /sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.6 claimed port ttyACM0
May 13 21:32:19 piotr-PORTEGE-R930 modem-manager[1032]: <info>  (ttyACM2) closing serial port...
May 13 21:32:19 piotr-PORTEGE-R930 modem-manager[1032]: <info>  (ttyACM2) serial port closed
May 13 21:32:19 piotr-PORTEGE-R930 modem-manager[1032]: <info>  (ttyACM1) closing serial port...
May 13 21:32:19 piotr-PORTEGE-R930 modem-manager[1032]: <info>  (ttyACM1) serial port closed
May 13 21:32:19 piotr-PORTEGE-R930 modem-manager[1032]: <info>  (Generic): GSM modem /sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.6 claimed port ttyACM2
May 13 21:32:19 piotr-PORTEGE-R930 modem-manager[1032]: <info>  (Generic): GSM modem /sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.6 claimed port ttyACM1
May 13 21:32:19 piotr-PORTEGE-R930 modem-manager[1032]: <info>  (ttyACM0) opening serial port...
May 13 21:32:19 piotr-PORTEGE-R930 NetworkManager[1073]: <warn> (ttyACM0): failed to look up interface index
May 13 21:32:19 piotr-PORTEGE-R930 NetworkManager[1073]: <info> WWAN now disabled by management service
May 13 21:32:19 piotr-PORTEGE-R930 NetworkManager[1073]: <info> (ttyACM0): new GSM/UMTS device (driver: 'cdc_acm' ifindex: 0)
May 13 21:32:19 piotr-PORTEGE-R930 NetworkManager[1073]: <info> (ttyACM0): exported as /org/freedesktop/NetworkManager/Devices/15
May 13 21:32:19 piotr-PORTEGE-R930 NetworkManager[1073]: <info> (ttyACM0): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
May 13 21:32:19 piotr-PORTEGE-R930 NetworkManager[1073]: <info> (ttyACM0): deactivating device (reason 'managed') [2]
May 13 21:32:19 piotr-PORTEGE-R930 NetworkManager[1073]: <info> (ttyACM0): device state change: unavailable -> disconnected (reason 'none') [20 30 0]
May 13 21:32:20 piotr-PORTEGE-R930 modem-manager[1032]: <info>  (ttyACM0) closing serial port...
May 13 21:32:20 piotr-PORTEGE-R930 modem-manager[1032]: <info>  (ttyACM0) serial port closed
```


Hope you can help me and redjocker to find a working solution!
Thank you.

---

