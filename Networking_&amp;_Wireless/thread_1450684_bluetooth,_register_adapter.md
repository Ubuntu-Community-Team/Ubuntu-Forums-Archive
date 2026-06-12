---
title: "bluetooth, register adapter"
date: 2010-04-09
forum: Networking &amp; Wireless
---

### Post by txepkine on 2010-04-09
&#65279;First of all,  I'm sorry for my english. This is my first post at the forum, I wish it is ok.
 
It's very strange for me what happens with my usb adapter. I tell you:
 
- I use a usb-bluetooth-adapter (sitecom) that I think my kernel detects and use the appropiat module;
 
[I]root@capgros-eee:/dev# lsusb
 
Bus 002 Device 003: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)
 
root@capgros-eee:/dev# lsmod | grep bt
 btusb                  11856  2 

- The adapter is functional as it's configurable by hciconfig and I can use it to scan
 bluetooth devices
 
root@capgros-eee:/dev# hcitool dev
 Devices:
 hci0    00:10:60:AA:0E:98
 
root@capgros-eee:/dev# hcitool scan
 Scanning ...
 F4:0B:93:A5:58:EE    BlackBerry 8520
 00:0E:6D:3E:CD:88    Eva
 
-All problems arise when pairing. bluetooth-agent says there is no adapter
 
root@capgros-eee:/dev# bluetooth-agent 1234
 Can't register agent
 Method "RegisterAgent" with signature "os" on interface "org.bluez.Adapter" doesn't exist
 
-If I use bluez-gnome or gnome-bluetooth o blueman, all them fail, all them say there is no adapter. This is very similar to the syslog messages
 
Apr  2 13:45:35 capgros-eee kernel: [ 8865.832082] usb 2-2: new full speed USB device using uhci_hcd and address 5
 Apr  2 13:45:36 capgros-eee kernel: [ 8866.004384] usb 2-2: configuration #1 chosen from 1 choice
 Apr  2 13:45:36 capgros-eee bluetoothd[3955]: Bluetooth daemon 4.51
 Apr  2 13:45:36 capgros-eee bluetoothd[3956]: Starting SDP server
 Apr  2 13:45:36 capgros-eee bluetoothd[3956]: Can't load plugin /usr/lib/bluetooth/plugins/netlink.so: /usr/lib/bluetooth/plugins/netlink.so: undefined symbol: debug
 Apr  2 13:45:36 capgros-eee bluetoothd[3956]: bridge pan0 created
 Apr  2 13:45:36 capgros-eee bluetoothd[3956]: HCI dev 0 registered
 Apr  2 13:45:36 capgros-eee bluetoothd[3956]: HCI dev 0 up
 Apr  2 13:45:36 capgros-eee bluetoothd[3956]: Starting security manager 0
 Apr  2 13:45:36 capgros-eee bluetoothd[3956]: Parsing /etc/bluetooth/serial.conf failed: No such file or directory
 Apr  2 13:45:36 capgros-eee bluetoothd[3956]: Adapter /org/bluez/3955/hci0 has been enabled
 Apr  2 13:45:41 capgros-eee bluetoothd[3956]: Unable to register adapter: hci0 already exist
 
- This is the output of bluetoothd running in foreground and with the debug option
 root@capgros-eee:/dev# bluetoothd -nd
 bluetoothd[3987]: Bluetooth daemon 4.51
 bluetoothd[3987]: Enabling debug information
 bluetoothd[3987]: parsing main.conf
 bluetoothd[3987]: discovto=0
 bluetoothd[3987]: pairto=0
 bluetoothd[3987]: pageto=8192
 bluetoothd[3987]: name=%h-%d
 bluetoothd[3987]: class=0x000100
 bluetoothd[3987]: discov_interval=0
 bluetoothd[3987]: Key file does not have key 'DeviceID'
 bluetoothd[3987]: Starting SDP server
 bluetoothd[3987]: Loading builtin plugins
 bluetoothd[3987]: Loading audio plugin
 bluetoothd[3987]: Loading input plugin
 bluetoothd[3987]: Loading serial plugin
 bluetoothd[3987]: Loading network plugin
 bluetoothd[3987]: Loading service plugin
 bluetoothd[3987]: Loading hciops plugin
 bluetoothd[3987]: Loading hal plugin
 bluetoothd[3987]: Loading storage plugin
 bluetoothd[3987]: Loading plugins /usr/lib/bluetooth/plugins
 bluetoothd[3987]: Can't load plugin /usr/lib/bluetooth/plugins/netlink.so: /usr/lib/bluetooth/plugins/netlink.so: undefined symbol: debug
 bluetoothd[3987]: register_interface: path /org/bluez/3987/any
 bluetoothd[3987]: Registered interface org.bluez.Service on path /org/bluez/3987/any
 bluetoothd[3987]: /etc/bluetooth/network.conf: Key file does not have key 'Disable'
 bluetoothd[3987]: /etc/bluetooth/network.conf: Key file does not have key 'DisableSecurity'
 bluetoothd[3987]: /etc/bluetooth/network.conf: Key file does not have key 'Interface'
 bluetoothd[3987]: /etc/bluetooth/network.conf: Key file does not have key 'Interface'
 bluetoothd[3987]: /etc/bluetooth/network.conf: Key file does not have key 'Interface'
 bluetoothd[3987]: Config options: InterfacePrefix=bnep%d, PANU_Script=(null), GN_Script=(null), NAP_Script=(null), GN_Interface=pan0, NAP_Interface=pan1, Security=true
 bluetoothd[3987]: bridge pan0 created
 bluetoothd[3987]: input.conf: Key file does not have key 'IdleTimeout'
 bluetoothd[3987]: Unix socket created: 9
 bluetoothd[3987]: audio.conf: Key file does not have key 'AutoConnect'
 bluetoothd[3987]: audio.conf: Key file does not have key 'MaxConnected'
 bluetoothd[3987]: Telephony plugin initialized
 bluetoothd[3987]: HFP AG features: "Ability to reject a call" "Enhanced call status" "Extended Error Result Codes" 
bluetoothd[3987]: Entering main loop
 bluetoothd[3987]: RFKILL event idx 1 type 1 op 0 soft 0 hard 0
 bluetoothd[3987]: RFKILL event idx 2 type 1 op 0 soft 0 hard 0
 

-The same exit when I plug the adapter
 
root@capgros-eee:/dev# bluetoothd -nd
 bluetoothd[3987]: Changing service classes to 0x4a0000
 bluetoothd[3987]: Unable to register adapter: hci0 already exist
 bluetoothd[3987]: Changing service classes to 0x5a0000
 [/I]


[I][I]
I have used linux for a lot of years, but I'm only a biologist, I am not a computer expert and  I could not find a solution.  Please, can somebody explain what it's happening. Thanks a lot![/I][/I]

---

