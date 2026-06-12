---
title: "Mobile broadband drops connection after 1 minute"
date: 2010-08-17
forum: Networking &amp; Wireless
---

### Post by out_of_time on 2010-08-17
Hi all,

I'm using a Qualcomm U301 mobile broadband USB card with my 64-bit Lucid laptop. The same aircard works fine with my netbook running 32-bit Lucid, but when I connect on this machine the connection nearly always drops after about a minute. I'm connecting using Network Manager, which usually recognizes the card and is able to establish the connection. I've got normal connectivity for about a minute, after which NM reports that it has disconnected. Occasionally, the entire system will lock up when it disconnects as well and I need to hard reboot.

I've come across folks having similar problems with mobile broadband on forums, but haven't yet found a solution that works for me. I've tried the following:

* Disabled wireless in Network Manager
* Deleted the mobile broadband connection in Network Manager and created a new one
* Added the following to /etc/udev/rules.d/50-u301

```

ACTION!="add" GOTO="3G_End"

SUBSYSTEMS=="usb", ATTRS{idProduct}=="6008", ATTRS{idVendor}=="16d8",
RUN+="/sbin/modprobe usbserial vendor=0x16d8 product=0x6008"
LABEL="3G_End"

```

I'm not in an area where I would expect a poor wireless signal -- this has been affecting me all up and down the eastern seaboard of the US which generally has good coverage.

Here's the output of the syslog during the process of plugging the card in, connecting, and then dropping the connection -- there certainly might be something in here that is a clue, but I'm clueless as to what it might be:

```

Aug 17 09:46:52 localhost kernel: [  706.448922] usb 3-4: new high speed USB device using xhci_hcd and address 0
Aug 17 09:46:52 localhost kernel: [  706.479557] xhci_hcd 0000:45:00.0: WARN: short transfer on control ep
Aug 17 09:46:52 localhost kernel: [  706.479929] xhci_hcd 0000:45:00.0: WARN: short transfer on control ep
Aug 17 09:46:52 localhost kernel: [  706.480173] usb 3-4: configuration #1 chosen from 1 choice
Aug 17 09:46:52 localhost kernel: [  706.480182] usb 3-4: ep 0x81 - rounding interval to 2048 microframes
Aug 17 09:46:52 localhost kernel: [  706.480720] hub 3-4:1.0: USB hub found
Aug 17 09:46:52 localhost kernel: [  706.480929] xhci_hcd 0000:45:00.0: WARN: short transfer on control ep
Aug 17 09:46:52 localhost kernel: [  706.481062] hub 3-4:1.0: 4 ports detected
Aug 17 09:46:54 localhost kernel: [  708.448513] hub 3-4:1.0: unable to enumerate USB device on port 2
Aug 17 09:46:55 localhost kernel: [  709.389089] usb 3-4.2: new full speed USB device using xhci_hcd and address 0
Aug 17 09:46:55 localhost kernel: [  709.410812] xhci_hcd 0000:45:00.0: WARN: Stalled endpoint
Aug 17 09:46:55 localhost kernel: [  709.411438] xhci_hcd 0000:45:00.0: WARN: Stalled endpoint
Aug 17 09:46:55 localhost kernel: [  709.412063] xhci_hcd 0000:45:00.0: WARN: Stalled endpoint
Aug 17 09:46:55 localhost kernel: [  709.414934] xhci_hcd 0000:45:00.0: WARN: short transfer on control ep
Aug 17 09:46:55 localhost kernel: [  709.415687] xhci_hcd 0000:45:00.0: WARN: short transfer on control ep
Aug 17 09:46:55 localhost kernel: [  709.416435] xhci_hcd 0000:45:00.0: WARN: short transfer on control ep
Aug 17 09:46:55 localhost kernel: [  709.416814] usb 3-4.2: configuration #1 chosen from 1 choice
Aug 17 09:46:55 localhost kernel: [  709.419183] xhci_hcd 0000:45:00.0: WARN: short transfer on control ep
Aug 17 09:46:55 localhost kernel: [  709.419492] option 3-4.2:1.0: GSM modem (1-port) converter detected
Aug 17 09:46:55 localhost kernel: [  709.419566] usb 3-4.2: GSM modem (1-port) converter now attached to ttyUSB0
Aug 17 09:46:55 localhost kernel: [  709.420057] xhci_hcd 0000:45:00.0: WARN: short transfer on control ep
Aug 17 09:46:55 localhost kernel: [  709.420348] option 3-4.2:1.1: GSM modem (1-port) converter detected
Aug 17 09:46:55 localhost kernel: [  709.420407] usb 3-4.2: GSM modem (1-port) converter now attached to ttyUSB1
Aug 17 09:46:55 localhost kernel: [  709.421183] xhci_hcd 0000:45:00.0: WARN: short transfer on control ep
Aug 17 09:46:55 localhost kernel: [  709.421479] option 3-4.2:1.2: GSM modem (1-port) converter detected
Aug 17 09:46:55 localhost kernel: [  709.421530] usb 3-4.2: GSM modem (1-port) converter now attached to ttyUSB2
Aug 17 09:46:55 localhost kernel: [  709.422059] xhci_hcd 0000:45:00.0: WARN: short transfer on control ep
Aug 17 09:46:55 localhost kernel: [  709.422353] option 3-4.2:1.3: GSM modem (1-port) converter detected
Aug 17 09:46:55 localhost kernel: [  709.422401] usb 3-4.2: GSM modem (1-port) converter now attached to ttyUSB3
Aug 17 09:46:55 localhost kernel: [  709.443902] scsi16 : SCSI emulation for USB Mass Storage devices
Aug 17 09:46:55 localhost kernel: [  709.454447] usb-storage: device found at 3
Aug 17 09:46:55 localhost kernel: [  709.454449] usb-storage: waiting for device to settle before scanning
Aug 17 09:46:55 localhost modem-manager: (ttyUSB0) opening serial device...
Aug 17 09:46:55 localhost modem-manager: (ttyUSB0): probe requested by plugin 'Generic'
Aug 17 09:46:55 localhost modem-manager: (ttyUSB1) opening serial device...
Aug 17 09:46:55 localhost modem-manager: (ttyUSB1): probe requested by plugin 'Generic'
Aug 17 09:46:55 localhost modem-manager: (ttyUSB3) opening serial device...
Aug 17 09:46:55 localhost modem-manager: (ttyUSB3): probe requested by plugin 'Generic'
Aug 17 09:46:55 localhost modem-manager: (ttyUSB2) opening serial device...
Aug 17 09:46:55 localhost modem-manager: (ttyUSB2): probe requested by plugin 'Generic'
Aug 17 09:46:59 localhost modem-manager: (ttyUSB1) closing serial device...
Aug 17 09:46:59 localhost modem-manager: (Generic): CDMA modem /sys/devices/pci0000:00/0000:00:1c.7/0000:45:00.0/usb3/3-4/3-4.2 claimed port ttyUSB1
Aug 17 09:46:59 localhost modem-manager: Added modem /sys/devices/pci0000:00/0000:00:1c.7/0000:45:00.0/usb3/3-4/3-4.2
Aug 17 09:46:59 localhost modem-manager: Exported modem /sys/devices/pci0000:00/0000:00:1c.7/0000:45:00.0/usb3/3-4/3-4.2 as /org/freedesktop/ModemManager/Modems/9
Aug 17 09:46:59 localhost NetworkManager: <info>  (ttyUSB1): new CDMA device (driver: 'option1')
Aug 17 09:46:59 localhost NetworkManager: <info>  (ttyUSB1): exported as /org/freedesktop/NetworkManager/Devices/11
Aug 17 09:46:59 localhost NetworkManager: <info>  (ttyUSB1): now managed
Aug 17 09:46:59 localhost NetworkManager: <info>  (ttyUSB1): device state change: 1 -> 2 (reason 2)
Aug 17 09:46:59 localhost NetworkManager: <info>  (ttyUSB1): deactivating device (reason: 2).
Aug 17 09:46:59 localhost NetworkManager: <info>  (ttyUSB1): device state change: 2 -> 3 (reason 0)
Aug 17 09:47:00 localhost kernel: [  714.456555] usb-storage: device scan complete
Aug 17 09:47:00 localhost kernel: [  714.468536] scsi 16:0:0:0: CD-ROM            CMOTECH  Mass Storage     2.31 PQ: 0 ANSI: 6
Aug 17 09:47:00 localhost kernel: [  714.469523] xhci_hcd 0000:45:00.0: WARN: Stalled endpoint
Aug 17 09:47:00 localhost kernel: [  714.472490] xhci_hcd 0000:45:00.0: WARN: Stalled endpoint
Aug 17 09:47:00 localhost kernel: [  714.475489] xhci_hcd 0000:45:00.0: WARN: Stalled endpoint
Aug 17 09:47:00 localhost kernel: [  714.478458] xhci_hcd 0000:45:00.0: WARN: Stalled endpoint
Aug 17 09:47:00 localhost kernel: [  714.483535] sr1: scsi3-mmc drive: 103x/340x dvd-ram cd/rw xa/form2 caddy
Aug 17 09:47:00 localhost kernel: [  714.483661] sr 16:0:0:0: Attached scsi CD-ROM sr1
Aug 17 09:47:00 localhost kernel: [  714.483749] sr 16:0:0:0: Attached scsi generic sg2 type 5
Aug 17 09:47:01 localhost kernel: [  714.498462] xhci_hcd 0000:45:00.0: WARN: Stalled endpoint
Aug 17 09:47:01 localhost kernel: [  714.501435] xhci_hcd 0000:45:00.0: WARN: Stalled endpoint
Aug 17 09:47:01 localhost kernel: [  714.505506] xhci_hcd 0000:45:00.0: WARN: Stalled endpoint
Aug 17 09:47:01 localhost kernel: [  714.508506] xhci_hcd 0000:45:00.0: WARN: Stalled endpoint
Aug 17 09:47:01 localhost kernel: [  714.510469] sr1: CDROM (ioctl) error, command: Xpwrite, Read disk info 51 00 00 00 00 00 00 00 02 00
Aug 17 09:47:01 localhost kernel: [  714.510479] sr: Sense Key : Hardware Error [current] 
Aug 17 09:47:01 localhost kernel: [  714.510483] sr: Add. Sense: No additional sense information
Aug 17 09:47:01 localhost kernel: [  714.516433] xhci_hcd 0000:45:00.0: WARN: Stalled endpoint
Aug 17 09:47:01 localhost NetworkManager: <info>  Activation (ttyUSB1) starting connection 'Sprint connection'
Aug 17 09:47:01 localhost NetworkManager: <info>  (ttyUSB1): device state change: 3 -> 4 (reason 0)
Aug 17 09:47:01 localhost NetworkManager: <info>  Activation (ttyUSB1) Stage 1 of 5 (Device Prepare) scheduled...
Aug 17 09:47:01 localhost NetworkManager: <info>  Activation (ttyUSB1) Stage 1 of 5 (Device Prepare) started...
Aug 17 09:47:01 localhost NetworkManager: <info>  Activation (ttyUSB1) Stage 1 of 5 (Device Prepare) complete.
Aug 17 09:47:01 localhost modem-manager: (ttyUSB1) opening serial device...
Aug 17 09:47:01 localhost modem-manager: Modem /org/freedesktop/ModemManager/Modems/9: state changed (disabled -> enabling)
Aug 17 09:47:01 localhost modem-manager: Got failure code 100: Unknown error
Aug 17 09:47:01 localhost modem-manager: Your CDMA modem does not support +CMEE command
Aug 17 09:47:01 localhost modem-manager: Modem /org/freedesktop/ModemManager/Modems/9: state changed (enabling -> enabled)
Aug 17 09:47:01 localhost modem-manager: Modem /org/freedesktop/ModemManager/Modems/9: state changed (enabled -> registered)
Aug 17 09:47:01 localhost modem-manager: Modem /org/freedesktop/ModemManager/Modems/9: state changed (registered -> connecting)
Aug 17 09:47:07 localhost modem-manager: (ttyUSB0) closing serial device...
Aug 17 09:47:10 localhost modem-manager: (ttyUSB3) closing serial device...
Aug 17 09:47:11 localhost modem-manager: (ttyUSB2) closing serial device...
Aug 17 09:47:16 localhost modem-manager: Modem /org/freedesktop/ModemManager/Modems/9: state changed (connecting -> connected)
Aug 17 09:47:16 localhost NetworkManager: <info>  Activation (ttyUSB1) Stage 2 of 5 (Device Configure) scheduled...
Aug 17 09:47:16 localhost NetworkManager: <info>  Activation (ttyUSB1) Stage 2 of 5 (Device Configure) starting...
Aug 17 09:47:16 localhost NetworkManager: <info>  (ttyUSB1): device state change: 4 -> 5 (reason 0)
Aug 17 09:47:16 localhost NetworkManager: <info>  Activation (ttyUSB1) Stage 2 of 5 (Device Configure) successful.
Aug 17 09:47:16 localhost NetworkManager: <info>  Activation (ttyUSB1) Stage 3 of 5 (IP Configure Start) scheduled.
Aug 17 09:47:16 localhost NetworkManager: <info>  Activation (ttyUSB1) Stage 2 of 5 (Device Configure) complete.
Aug 17 09:47:16 localhost NetworkManager: <info>  Activation (ttyUSB1) Stage 3 of 5 (IP Configure Start) started...
Aug 17 09:47:16 localhost NetworkManager: <info>  (ttyUSB1): device state change: 5 -> 7 (reason 0)
Aug 17 09:47:16 localhost NetworkManager: <info>  Starting pppd connection
Aug 17 09:47:16 localhost NetworkManager: <debug> [1282052836.285430] nm_ppp_manager_start(): Command line: /usr/sbin/pppd nodetach lock nodefaultroute ttyUSB1 noipdefault noauth usepeerdns lcp-echo-failure 0 lcp-echo-interval 0 ipparam /org/freedesktop/NetworkManager/PPP/3 plugin /usr/lib/pppd/2.4.4/nm-pppd-plugin.so
Aug 17 09:47:16 localhost NetworkManager: <debug> [1282052836.300198] nm_ppp_manager_start(): ppp started with pid 4943
Aug 17 09:47:16 localhost NetworkManager: <info>  Activation (ttyUSB1) Stage 4 of 5 (IP6 Configure Get) scheduled...
Aug 17 09:47:16 localhost NetworkManager: <info>  Activation (ttyUSB1) Stage 3 of 5 (IP Configure Start) complete.
Aug 17 09:47:16 localhost NetworkManager: <info>  Activation (ttyUSB1) Stage 4 of 5 (IP6 Configure Get) started...
Aug 17 09:47:16 localhost NetworkManager: <info>  Activation (ttyUSB1) Stage 4 of 5 (IP6 Configure Get) complete.
Aug 17 09:47:16 localhost pppd[4943]: Plugin /usr/lib/pppd/2.4.4/nm-pppd-plugin.so loaded.
Aug 17 09:47:16 localhost pppd[4943]: pppd 2.4.5 started by root, uid 0
Aug 17 09:47:16 localhost NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/ppp0, iface: ppp0)
Aug 17 09:47:16 localhost NetworkManager:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/ppp0, iface: ppp0): no ifupdown configuration found.
Aug 17 09:47:16 localhost pppd[4943]: Using interface ppp0
Aug 17 09:47:16 localhost pppd[4943]: Connect: ppp0 <--> /dev/ttyUSB1
Aug 17 09:47:16 localhost pppd[4943]: Cannot determine ethernet address for proxy ARP
Aug 17 09:47:16 localhost pppd[4943]: local  IP address 174.152.14.0
Aug 17 09:47:16 localhost pppd[4943]: remote IP address 68.28.113.69
Aug 17 09:47:16 localhost pppd[4943]: primary   DNS address 68.28.114.91
Aug 17 09:47:16 localhost pppd[4943]: secondary DNS address 68.28.122.93
Aug 17 09:47:16 localhost NetworkManager: <info>  PPP manager(IP Config Get) reply received.
Aug 17 09:47:16 localhost NetworkManager: <info>  Activation (ttyUSB1) Stage 4 of 5 (IP4 Configure Get) scheduled...
Aug 17 09:47:16 localhost NetworkManager: <info>  Activation (ttyUSB1) Stage 4 of 5 (IP4 Configure Get) started...
Aug 17 09:47:16 localhost NetworkManager: <info>  Activation (ttyUSB1) Stage 5 of 5 (IP Configure Commit) scheduled...
Aug 17 09:47:16 localhost NetworkManager: <info>  Activation (ttyUSB1) Stage 4 of 5 (IP4 Configure Get) complete.
Aug 17 09:47:16 localhost NetworkManager: <info>  Activation (ttyUSB1) Stage 5 of 5 (IP Configure Commit) started...
Aug 17 09:47:17 localhost NetworkManager: <info>  (ttyUSB1): device state change: 7 -> 8 (reason 0)
Aug 17 09:47:17 localhost NetworkManager: <info>  Policy set 'Sprint connection' (ppp0) as default for routing and DNS.
Aug 17 09:47:17 localhost NetworkManager: <info>  Activation (ttyUSB1) successful, device activated.
Aug 17 09:47:17 localhost NetworkManager: <info>  Activation (ttyUSB1) Stage 5 of 5 (IP Configure Commit) complete.
Aug 17 09:47:18 localhost ntpd[3915]: ntpd exiting on signal 15
Aug 17 09:47:19 localhost ntpdate[5069]: adjust time server 91.189.94.4 offset -0.062125 sec
Aug 17 09:47:19 localhost ntpd[5125]: ntpd 4.2.4p8@1.1612-o Fri Apr  9 03:13:54 UTC 2010 (1)
Aug 17 09:47:19 localhost ntpd[5126]: precision = 1.000 usec
Aug 17 09:47:19 localhost ntpd[5126]: ntp_io: estimated max descriptors: 1024, initial socket boundary: 16
Aug 17 09:47:19 localhost ntpd[5126]: Listening on interface #0 wildcard, 0.0.0.0#123 Disabled
Aug 17 09:47:19 localhost ntpd[5126]: Listening on interface #1 wildcard, ::#123 Disabled
Aug 17 09:47:19 localhost ntpd[5126]: Listening on interface #2 lo, ::1#123 Enabled
Aug 17 09:47:19 localhost ntpd[5126]: Listening on interface #3 lo, 127.0.0.1#123 Enabled
Aug 17 09:47:19 localhost ntpd[5126]: Listening on interface #4 ppp0, 174.152.14.0#123 Enabled
Aug 17 09:47:19 localhost ntpd[5126]: kernel time sync status 2040
Aug 17 09:47:19 localhost ntpd[5126]: frequency initialized 17.147 PPM from /var/lib/ntp/ntp.drift
Aug 17 09:48:01 localhost pppd[4943]: Modem hangup
Aug 17 09:48:01 localhost pppd[4943]: Connect time 0.8 minutes.
Aug 17 09:48:01 localhost pppd[4943]: Sent 6312 bytes, received 22108 bytes.
Aug 17 09:48:01 localhost modem-manager: (ttyUSB1) closing serial device...
Aug 17 09:48:01 localhost modem-manager: Modem /org/freedesktop/ModemManager/Modems/9: state changed (connected -> disabled)
Aug 17 09:48:01 localhost modem-manager: Removed modem /sys/devices/pci0000:00/0000:00:1c.7/0000:45:00.0/usb3/3-4/3-4.2
Aug 17 09:48:01 localhost NetworkManager: <info>  (ttyUSB1): now unmanaged
Aug 17 09:48:01 localhost NetworkManager: <info>  (ttyUSB1): device state change: 8 -> 1 (reason 36)
Aug 17 09:48:01 localhost NetworkManager: <info>  (ttyUSB1): deactivating device (reason: 36).
Aug 17 09:48:01 localhost kernel: [  775.042363] xhci_hcd 0000:45:00.0: WARN Event TRB for slot 2 ep 16 with no TDs queued?
Aug 17 09:48:01 localhost kernel: [  775.042476] option: option_instat_callback: error -108
Aug 17 09:48:01 localhost kernel: [  775.043604] option1 ttyUSB0: GSM modem (1-port) converter now disconnected from ttyUSB0
Aug 17 09:48:01 localhost kernel: [  775.043625] option 3-4.2:1.0: device disconnected
Aug 17 09:48:01 localhost kernel: [  775.044477] option: option_instat_callback: error -108
Aug 17 09:48:01 localhost kernel: [  775.045359] option1 ttyUSB1: GSM modem (1-port) converter now disconnected from ttyUSB1
Aug 17 09:48:01 localhost kernel: [  775.045372] option 3-4.2:1.1: device disconnected
Aug 17 09:48:01 localhost kernel: [  775.045442] option1 ttyUSB2: GSM modem (1-port) converter now disconnected from ttyUSB2
Aug 17 09:48:01 localhost kernel: [  775.045459] option 3-4.2:1.2: device disconnected
Aug 17 09:48:01 localhost kernel: [  775.045525] option1 ttyUSB3: GSM modem (1-port) converter now disconnected from ttyUSB3
Aug 17 09:48:01 localhost kernel: [  775.045547] option 3-4.2:1.3: device disconnected
Aug 17 09:48:01 localhost kernel: [  775.045750] xhci_hcd 0000:45:00.0: WARN Event TRB for slot 2 ep 16 with no TDs queued?
Aug 17 09:48:01 localhost kernel: [  775.047390] sr 16:0:0:0: Device offlined - not ready after error recovery
Aug 17 09:48:01 localhost kernel: [  775.047480] sr 16:0:0:0: rejecting I/O to offline device
Aug 17 09:48:01 localhost kernel: [  775.047712] usb 3-4.2: USB disconnect, address 3
Aug 17 09:48:01 localhost usb_id[5128]: unable to access '/devices/pci0000:00/0000:00:1c.7/0000:45:00.0/usb3/3-4/3-4.2/3-4.2:1.4/host16/target16:0:0/16:0:0:0/block/sr1'
Aug 17 09:48:01 localhost NetworkManager: <info>  (ttyUSB1): cleaning up...
Aug 17 09:48:01 localhost NetworkManager: <info>  (ttyUSB1): taking down device.
Aug 17 09:48:01 localhost pppd[4943]: Connection terminated.
Aug 17 09:48:01 localhost NetworkManager: <info>  Unmanaged Device found; state CONNECTED forced. (see http://bugs.launchpad.net/bugs/191889)
Aug 17 09:48:01 localhost NetworkManager:    SCPlugin-Ifupdown: devices removed (path: /sys/devices/virtual/net/ppp0, iface: ppp0)
Aug 17 09:48:01 localhost nm-dispatcher.action: Error in get_property: Method "Get" with signature "ss" on interface "org.freedesktop.DBus.Properties" doesn't exist#012
Aug 17 09:48:01 localhost kernel: [  775.152410] usb 3-4.2: new full speed USB device using xhci_hcd and address 0
Aug 17 09:48:01 localhost kernel: [  775.174124] xhci_hcd 0000:45:00.0: WARN: Stalled endpoint
Aug 17 09:48:01 localhost kernel: [  775.174748] xhci_hcd 0000:45:00.0: WARN: Stalled endpoint
Aug 17 09:48:01 localhost kernel: [  775.175373] xhci_hcd 0000:45:00.0: WARN: Stalled endpoint
Aug 17 09:48:01 localhost kernel: [  775.178247] xhci_hcd 0000:45:00.0: WARN: short transfer on control ep
Aug 17 09:48:01 localhost kernel: [  775.178999] xhci_hcd 0000:45:00.0: WARN: short transfer on control ep
Aug 17 09:48:01 localhost kernel: [  775.179747] xhci_hcd 0000:45:00.0: WARN: short transfer on control ep
Aug 17 09:48:01 localhost kernel: [  775.180122] usb 3-4.2: configuration #1 chosen from 1 choice
Aug 17 09:48:01 localhost kernel: [  775.182494] xhci_hcd 0000:45:00.0: WARN: short transfer on control ep
Aug 17 09:48:01 localhost kernel: [  775.182812] option 3-4.2:1.0: GSM modem (1-port) converter detected
Aug 17 09:48:01 localhost kernel: [  775.182900] usb 3-4.2: GSM modem (1-port) converter now attached to ttyUSB0
Aug 17 09:48:01 localhost kernel: [  775.183370] xhci_hcd 0000:45:00.0: WARN: short transfer on control ep
Aug 17 09:48:01 localhost kernel: [  775.183676] option 3-4.2:1.1: GSM modem (1-port) converter detected
Aug 17 09:48:01 localhost kernel: [  775.183741] usb 3-4.2: GSM modem (1-port) converter now attached to ttyUSB2
Aug 17 09:48:01 localhost kernel: [  775.184245] xhci_hcd 0000:45:00.0: WARN: short transfer on control ep
Aug 17 09:48:01 localhost kernel: [  775.184540] option 3-4.2:1.2: GSM modem (1-port) converter detected
Aug 17 09:48:01 localhost kernel: [  775.184600] usb 3-4.2: GSM modem (1-port) converter now attached to ttyUSB3
Aug 17 09:48:01 localhost kernel: [  775.185121] xhci_hcd 0000:45:00.0: WARN: short transfer on control ep
Aug 17 09:48:01 localhost kernel: [  775.185417] option 3-4.2:1.3: GSM modem (1-port) converter detected
Aug 17 09:48:01 localhost kernel: [  775.185471] usb 3-4.2: GSM modem (1-port) converter now attached to ttyUSB4
Aug 17 09:48:01 localhost pppd[4943]: Exit.
Aug 17 09:48:01 localhost kernel: [  775.212734] scsi17 : SCSI emulation for USB Mass Storage devices
Aug 17 09:48:01 localhost kernel: [  775.222779] usb-storage: device found at 3
Aug 17 09:48:01 localhost kernel: [  775.222782] usb-storage: waiting for device to settle before scanning
Aug 17 09:48:01 localhost modem-manager: (ttyUSB4) opening serial device...
Aug 17 09:48:01 localhost modem-manager: (ttyUSB4): probe requested by plugin 'Generic'
Aug 17 09:48:01 localhost modem-manager: (ttyUSB3) opening serial device...
Aug 17 09:48:01 localhost modem-manager: (ttyUSB3): probe requested by plugin 'Generic'
Aug 17 09:48:01 localhost modem-manager: (ttyUSB0) opening serial device...
Aug 17 09:48:01 localhost modem-manager: (ttyUSB0): probe requested by plugin 'Generic'
Aug 17 09:48:01 localhost modem-manager: (ttyUSB2) opening serial device...
Aug 17 09:48:01 localhost modem-manager: (ttyUSB2): probe requested by plugin 'Generic'
Aug 17 09:48:03 localhost NetworkManager: <debug> [1282052883.999846] ensure_killed(): waiting for ppp pid 4943 to exit
Aug 17 09:48:04 localhost NetworkManager: <debug> [1282052883.999941] ensure_killed(): ppp pid 4943 cleaned up
Aug 17 09:48:05 localhost modem-manager: (ttyUSB2) closing serial device...
Aug 17 09:48:05 localhost modem-manager: (Generic): CDMA modem /sys/devices/pci0000:00/0000:00:1c.7/0000:45:00.0/usb3/3-4/3-4.2 claimed port ttyUSB2
Aug 17 09:48:05 localhost modem-manager: Added modem /sys/devices/pci0000:00/0000:00:1c.7/0000:45:00.0/usb3/3-4/3-4.2
Aug 17 09:48:05 localhost modem-manager: Exported modem /sys/devices/pci0000:00/0000:00:1c.7/0000:45:00.0/usb3/3-4/3-4.2 as /org/freedesktop/ModemManager/Modems/10
Aug 17 09:48:05 localhost NetworkManager: <info>  (ttyUSB2): new CDMA device (driver: 'option1')
Aug 17 09:48:05 localhost NetworkManager: <info>  (ttyUSB2): exported as /org/freedesktop/NetworkManager/Devices/12
Aug 17 09:48:05 localhost NetworkManager: <info>  (ttyUSB2): now managed
Aug 17 09:48:05 localhost NetworkManager: <info>  (ttyUSB2): device state change: 1 -> 2 (reason 2)
Aug 17 09:48:05 localhost NetworkManager: <info>  (ttyUSB2): deactivating device (reason: 2).
Aug 17 09:48:05 localhost NetworkManager: <info>  (ttyUSB2): device state change: 2 -> 3 (reason 0)
Aug 17 09:48:06 localhost kernel: [  780.232972] usb-storage: device scan complete
Aug 17 09:48:06 localhost kernel: [  780.242280] scsi 17:0:0:0: CD-ROM            CMOTECH  Mass Storage     2.31 PQ: 0 ANSI: 6
Aug 17 09:48:06 localhost kernel: [  780.243216] xhci_hcd 0000:45:00.0: WARN: Stalled endpoint
Aug 17 09:48:06 localhost kernel: [  780.246238] xhci_hcd 0000:45:00.0: WARN: Stalled endpoint
Aug 17 09:48:06 localhost kernel: [  780.249274] xhci_hcd 0000:45:00.0: WARN: Stalled endpoint
Aug 17 09:48:06 localhost kernel: [  780.252247] xhci_hcd 0000:45:00.0: WARN: Stalled endpoint
Aug 17 09:48:06 localhost kernel: [  780.268290] sr1: scsi3-mmc drive: 96x/153x writer dvd-ram xa/form2 
Aug 17 09:48:06 localhost kernel: [  780.268421] sr 17:0:0:0: Attached scsi CD-ROM sr1
Aug 17 09:48:06 localhost kernel: [  780.268497] sr 17:0:0:0: Attached scsi generic sg2 type 5
Aug 17 09:48:06 localhost kernel: [  780.303238] xhci_hcd 0000:45:00.0: WARN: Stalled endpoint
Aug 17 09:48:06 localhost kernel: [  780.306213] xhci_hcd 0000:45:00.0: WARN: Stalled endpoint
Aug 17 09:48:06 localhost kernel: [  780.309213] xhci_hcd 0000:45:00.0: WARN: Stalled endpoint
Aug 17 09:48:06 localhost kernel: [  780.312175] xhci_hcd 0000:45:00.0: WARN: Stalled endpoint
Aug 17 09:48:06 localhost kernel: [  780.314254] sr1: CDROM (ioctl) error, command: Xpwrite, Read disk info 51 00 00 00 00 00 00 00 02 00
Aug 17 09:48:06 localhost kernel: [  780.314265] sr: Sense Key : Hardware Error [current] 
Aug 17 09:48:06 localhost kernel: [  780.314269] sr: Add. Sense: No additional sense information
Aug 17 09:48:06 localhost kernel: [  780.320219] xhci_hcd 0000:45:00.0: WARN: Stalled endpoint

```

Any suggestions would be greatly appreciated -- thanks!

---

### Post by alexfish on 2010-08-17
Hi

not sure if keeping the system updated will eventually cure the problem , as you say it works with 32bit

 until someone comes up with a fix for 64bit version
can only suggest looking here , see what you think

[**Installing  newer version of network-manager in Lucid, from daily trunk builds ppa.**]("http://ubuntuforums.org/showthread.php?t=1549395")

could also suggest searching Launchpad bugs

regards

alexfish

---

