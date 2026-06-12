---
title: "unable to pair bluetooth device to laptop"
date: 2011-03-13
forum: Networking &amp; Wireless
---

### Post by meghsinghnokha on 2011-03-13
hello i am unable to pair mobile to laptop . i have installed bluetooth , bluez , bluez-utils . bluetooth applet is in notification area , when i try to set up new device it can search my mobile but when i trying to pair then it can't do . simply it show only PIN number and mobile don't receive any message for PIN ,i am tired to pair it when i write < dmesg >  in terminal then i found some lines about bluetooth which i copy and paste here as it:-  [   20.602554] Skipping EDID probe due to cached edid
[   20.607278] type=1400 audit(1300009550.231:10): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient3" pid=1095 comm="apparmor_parser"
[   20.608027] type=1400 audit(1300009550.231:11): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=1095 comm="apparmor_parser"
[   20.851333] usb 3-1.3: new full speed USB device using uhci_hcd and address 5
[   21.008372] Bluetooth: Core ver 2.15
[   21.008419] NET: Registered protocol family 31
[   21.008420] Bluetooth: HCI device and connection manager initialized
[   21.008422] Bluetooth: HCI socket layer initialized
[   21.011283] Bluetooth: Generic Bluetooth USB driver ver 0.6
[   21.012021] usbcore: registered new interface driver btusb
[   21.060355] Console: switching to colour frame buffer device 170x48
[   21.063055] fb0: inteldrmfb frame buffer device
[   21.063056] drm: registered panic notifier
[   21.063066] Slow work thread pool: Starting up
[   21.063186] Slow work thread pool: Ready
[   21.079706] acpi device:3b: registered as cooling_device2
[   21.080677] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A03:00/LNXVIDEO:01/input/input10
[   21.080797] ACPI: Video Device [VID1] (multi-head: yes  rom: no  post: no)
[   21.080821] [Firmware Bug]: Duplicate ACPI video bus devices for the same VGA controller, please try module parameter "video.allow_duplicates=1"if the current driver doesn't work.
[   21.080927] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[   21.080975] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[   21.081045]   alloc irq_desc for 47 on node -1
[   21.081048]   alloc kstat_irqs on node -1
[   21.081062] HDA Intel 0000:00:1b.0: irq 47 for MSI/MSI-X
[   21.081095] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   21.102026] Bluetooth: L2CAP ver 2.14
[   21.102029] Bluetooth: L2CAP socket layer initialized
[   21.108072] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   21.108076] Bluetooth: BNEP filters: protocol multicast
[   21.112064] Bluetooth: SCO (Voice Link) ver 0.6
[   21.112067] Bluetooth: SCO socket layer initialized
[   21.142597] Skipping EDID probe due to cached edid
[   21.210555] input: HDA Intel Mic at Ext Right Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input11
[   21.210717] input: HDA Intel HP Out at Ext Right Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input12
[   21.230376] Bluetooth: RFCOMM TTY layer initialized
[   21.230383] Bluetooth: RFCOMM socket layer initialized
[   21.230385] Bluetooth: RFCOMM ver 1.11
[   21.353140] dahdi: Telephony Interface Registered on major 196
[   21.353143] dahdi: Version: 2.2.1
[   21.357195] dahdi_dummy: Trying to load High Resolution Timer
[   21.357198] dahdi_dummy: Initialized High Resolution Timer
[   21.357200] dahdi_dummy: Starting High Resolution Timer
[   21.357205] dahdi_dummy: High Resolution Timer started, good to go
[   21.359483] dahdi_transcode: Loaded.
i am new for linux ubuntu i didn't understand about it . i read in a forum about dmesg then i copy paste it . please help me and solve my problem . before few days when i installed ubuntu 10.10  on my laptop then it connected easily but after few days it not work i deleted my paired mobile from it , i uninstall blue tooth through  ubuntu software center after it i install again but i couldn't paired .when i command in terminal sudo hidd --connect 00:21:FE:F5:14:21 then it say Can't get device information: Host is down as it :-
meghsinghnokha@meghsinghnokha-Inspiron-1440:~$ hcitool scan
Scanning ...
	00:21:FE:F5:14:21	Nokia 3120 classic
	00:1B:EE:19:D5:19	Nokia N72
meghsinghnokha@meghsinghnokha-Inspiron-1440:~$ sudo hidd --connect 00:21:FE:F5:14:21
Can't get device information: Host is down
meghsinghnokha@meghsinghnokha-Inspiron-1440:~$

meghsinghnokha@meghsinghnokha-Inspiron-1440:~$ sudo /etc/init.d/bluez-utils restart
sudo: /etc/init.d/bluez-utils: command not found
meghsinghnokha@meghsinghnokha-Inspiron-1440:~$ hcitool dev
Devices:
	hci0	0C:60:76:90:8B:F9

meghsinghnokha@meghsinghnokha-Inspiron-1440:~$ sudo hidd --help
hidd - Bluetooth HID daemon version 4.69

---

