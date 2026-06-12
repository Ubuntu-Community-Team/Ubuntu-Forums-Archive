---
title: "Bluetooth PAN configuration"
date: 2010-03-19
forum: Networking &amp; Wireless
---

### Post by slipdipper on 2010-03-19
Hey guys, I'm trying to set up a PAN between two laptops to use as a transport for layer 3 communication..

my problem is that it just doesnt work. 

On the server (GN) side i have (important items shown):

/etc/default/bluetooth
```

BLUETOOTH_ENABLED=1
PAND_ENABLED=1

```

/etc/bluetooth/network.conf (using all defaults except)
```

DisableSecurity=true

```

My configuration on the server side is:
```

modprobe bnep
bluetoothd -n -d
hciconfig hci0 piscan
hciconfig hci0 lm master,accept
ifconfig pan0 10.0.0.1 netmask 255.255.255.0
pand --listen --role GN --master -n -p

```

Notable errors on the server side are:
(bluetoothd)
```

bluetoothd -n -d
bluetoothd[8238]: Bluetooth daemon
bluetoothd[8238]: Enabling debug information
bluetoothd[8238]: parsing main.conf
bluetoothd[8238]: offmode=NoScan
bluetoothd[8238]: discovto=0
bluetoothd[8238]: pageto=8192
bluetoothd[8238]: name=%h-%d
bluetoothd[8238]: class=0x000100
bluetoothd[8238]: inqmode=0
bluetoothd[8238]: Starting SDP server
bluetoothd[8238]: Loading plugins /usr/lib/bluetooth/plugins
bluetoothd[8238]: /usr/lib/bluetooth/plugins/audio.so
bluetoothd[8238]: Unix socket created: 11
bluetoothd[8238]: Telephony plugin initialized
bluetoothd[8238]: HFP AG features: "Ability to reject a call" "Enhanced call status" "Extended Error Result Codes"
bluetoothd[8238]: /usr/lib/bluetooth/plugins/hal.so
bluetoothd[8238]: /usr/lib/bluetooth/plugins/input.so
bluetoothd[8238]: input.conf: Key file does not have key 'IdleTimeout'
bluetoothd[8238]: /usr/lib/bluetooth/plugins/netlink.so
bluetoothd[8238]: Starting experimental netlink support
bluetoothd[8238]: Failed to find Bluetooth netlink family
bluetoothd[8238]: Can't init plugin /usr/lib/bluetooth/plugins/netlink.so
bluetoothd[8238]: /usr/lib/bluetooth/plugins/network.so
bluetoothd[8238]: /etc/bluetooth/network.conf: Key file does not have key 'Disable'
bluetoothd[8238]: /etc/bluetooth/network.conf: Key file does not have key 'Script'
bluetoothd[8238]: /etc/bluetooth/network.conf: Key file does not have key 'Script'
bluetoothd[8238]: /etc/bluetooth/network.conf: Key file does not have key 'Script'
bluetoothd[8238]: /etc/bluetooth/network.conf: Key file does not have key 'Interface'
bluetoothd[8238]: /etc/bluetooth/network.conf: Key file does not have key 'Interface'
bluetoothd[8238]: /etc/bluetooth/network.conf: Key file does not have key 'Interface'
bluetoothd[8238]: Config options: InterfacePrefix=bnep%d, PANU_Script=(null), GN_Script=(null), NAP_Script=(null), GN_Interface=pan0, NAP_Interface=pan1, Security=false
bluetoothd[8238]: Can't create GN bridge
bluetoothd[8238]: /usr/lib/bluetooth/plugins/serial.so
bluetoothd[8238]: /usr/lib/bluetooth/plugins/service.so
bluetoothd[8238]: HCI dev 0 registered
bluetoothd[8238]: child 8239 forked
bluetoothd[8238]: HCI dev 0 already up
bluetoothd[8238]: headset_server_probe: path /org/bluez/hci0
bluetoothd[8238]: audio.conf: Key file does not have key 'Master'
bluetoothd[8238]: Adding record with handle 0x10000
bluetoothd[8238]: Record pattern UUID 00000003-0000-1000-8000-00805f9
bluetoothd[8238]: Record pattern UUID 00000100-0000-1000-8000-00805f9
bluetoothd[8238]: Record pattern UUID 00001002-0000-1000-8000-00805f9
bluetoothd[8238]: Record pattern UUID 00001108-0000-1000-8000-00805f9
bluetoothd[8238]: Record pattern UUID 00001112-0000-1000-8000-00805f9
bluetoothd[8238]: Record pattern UUID 00001203-0000-1000-8000-00805f9
bluetoothd[8238]: audio.conf: Key file does not have key 'SCORouting'
bluetoothd[8238]: a2dp_server_probe: path /org/bluez/hci0
bluetoothd[8238]: audio.conf: Key file does not have key 'Disable'
bluetoothd[8238]: audio.conf: Key file does not have group 'A2DP'
bluetoothd[8238]: audio.conf: Key file does not have group 'A2DP'
bluetoothd[8238]: audio.conf: Key file does not have group 'A2DP'
bluetoothd[8238]: audio.conf: Key file does not have group 'A2DP'
bluetoothd[8238]: audio.conf: Key file does not have key 'Master'
bluetoothd[8238]: SEP 0xb888ed10 registered: type:0 codec:0 seid:1
bluetoothd[8238]: Adding record with handle 0x10001
bluetoothd[8238]: Record pattern UUID 00000019-0000-1000-8000-00805f9
bluetoothd[8238]: Record pattern UUID 00000100-0000-1000-8000-00805f9
bluetoothd[8238]: Record pattern UUID 00001002-0000-1000-8000-00805f9
bluetoothd[8238]: Record pattern UUID 0000110a-0000-1000-8000-00805f9
bluetoothd[8238]: Record pattern UUID 0000110d-0000-1000-8000-00805f9
bluetoothd[8238]: avrcp_server_probe: path /org/bluez/hci0
bluetoothd[8238]: audio.conf: Key file does not have key 'Master'
bluetoothd[8238]: Adding record with handle 0x10002
bluetoothd[8238]: Record pattern UUID 00000017-0000-1000-8000-00805f9
bluetoothd[8238]: Record pattern UUID 00000100-0000-1000-8000-00805f9
bluetoothd[8238]: Record pattern UUID 00001002-0000-1000-8000-00805f9
bluetoothd[8238]: Record pattern UUID 0000110c-0000-1000-8000-00805f9
bluetoothd[8238]: Record pattern UUID 0000110e-0000-1000-8000-00805f9
bluetoothd[8238]: Adding record with handle 0x10003
bluetoothd[8238]: Record pattern UUID 00000017-0000-1000-8000-00805f9
bluetoothd[8238]: Record pattern UUID 00000100-0000-1000-8000-00805f9
bluetoothd[8238]: Record pattern UUID 00001002-0000-1000-8000-00805f9
bluetoothd[8238]: Record pattern UUID 0000110e-0000-1000-8000-00805f9
bluetoothd[8238]: network_server_probe: path /org/bluez/hci0
bluetoothd[8238]: Adding record with handle 0x10004
bluetoothd[8238]: Record pattern UUID 0000000f-0000-1000-8000-00805f9
bluetoothd[8238]: Record pattern UUID 00000100-0000-1000-8000-00805f9
bluetoothd[8238]: Record pattern UUID 00001002-0000-1000-8000-00805f9
bluetoothd[8238]: Record pattern UUID 00001115-0000-1000-8000-00805f9
bluetoothd[8238]: register_server_record: got record id 0x10004
bluetoothd[8238]: Registered interface org.bluez.NetworkPeer on path /org/bluez/hci0
bluetoothd[8238]: network_server_probe: path /org/bluez/hci0
bluetoothd[8238]: Adding record with handle 0x10005
bluetoothd[8238]: Record pattern UUID 0000000f-0000-1000-8000-00805f9
bluetoothd[8238]: Record pattern UUID 00000100-0000-1000-8000-00805f9
bluetoothd[8238]: Record pattern UUID 00001002-0000-1000-8000-00805f9
bluetoothd[8238]: Record pattern UUID 00001117-0000-1000-8000-00805f9
bluetoothd[8238]: register_server_record: got record id 0x10005
bluetoothd[8238]: Registered interface org.bluez.NetworkHub on path /org/bluez/hci0
bluetoothd[8238]: network_server_probe: path /org/bluez/hci0
bluetoothd[8238]: Adding record with handle 0x10006
bluetoothd[8238]: Record pattern UUID 0000000f-0000-1000-8000-00805f9
bluetoothd[8238]: Record pattern UUID 00000100-0000-1000-8000-00805f9
bluetoothd[8238]: Record pattern UUID 00001002-0000-1000-8000-00805f9
bluetoothd[8238]: Record pattern UUID 00001116-0000-1000-8000-00805f9
bluetoothd[8238]: register_server_record: got record id 0x10006
bluetoothd[8238]: Registered interface org.bluez.NetworkRouter on path /org/bluez/hci0
bluetoothd[8238]: proxy_probe: path /org/bluez/hci0
bluetoothd[8238]: Registered interface org.bluez.SerialProxyManager on path /org/bluez/hci0
bluetoothd[8238]: service_probe: path /org/bluez/hci0
bluetoothd[8238]: Registered interface org.bluez.Service on path /org/bluez/hci0
bluetoothd[8238]: Adapter /org/bluez/hci0 has been enabled
bluetoothd[8238]: Starting security manager 0
bluetoothd[8238]: child 8239 exited
bluetoothd[8238]: Computer is classified as laptop
bluetoothd[8238]: Current device class is 0x0a010c
bluetoothd[8238]: Setting 0x00010c for major/minor device class
bluetoothd[8238]: adapter_get_device(AA:AA:AA:AA:AA:AA)
bluetoothd[8238]: adapter_create_device(AA:AA:AA:AA:AA:AA)
bluetoothd[8238]: Creating device /org/bluez/hci0/dev_AA_AA_AA_AA_AA_AA
bluetoothd[8238]: Removing temporary device AA:AA:AA:AA:AA:AA
bluetoothd[8238]: Removing device /org/bluez/hci0/dev_AA_AA_AA_AA_AA_AA
bluetoothd[8238]: adapter_get_device(AA:AA:AA:AA:AA:AA)
bluetoothd[8238]: adapter_create_device(AA:AA:AA:AA:AA:AA)
bluetoothd[8238]: Creating device /org/bluez/hci0/dev_AA_AA_AA_AA_AA_AA
bluetoothd[8238]: Removing temporary device AA:AA:AA:AA:AA:AA
bluetoothd[8238]: Removing device /org/bluez/hci0/dev_AA_AA_AA_AA_AA_AA
bluetoothd[8238]: adapter_get_device(AA:AA:AA:AA:AA:AA)
bluetoothd[8238]: adapter_create_device(AA:AA:AA:AA:AA:AA)
bluetoothd[8238]: Creating device /org/bluez/hci0/dev_AA_AA_AA_AA_AA_AA
bluetoothd[8238]: Removing temporary device AA:AA:AA:AA:AA:AA
bluetoothd[8238]: Removing device /org/bluez/hci0/dev_AA_AA_AA_AA_AA_AA

```

hcidump:
```

hcidump -i hci0 -X
HCI sniffer - Bluetooth packet analyzer ver 1.42
device: hci0 snap_len: 1028 filter: 0xffffffff
> HCI Event: Connect Request (0x04) plen 10
  0000: ee 01 0a 57 60 00 0c 01  0a 01                    ...W`.....
< HCI Command: Accept Connection Request (0x01|0x0009) plen 7
  0000: ee 01 0a 57 60 00 00                              ...W`..
> HCI Event: Command Status (0x0f) plen 4
  0000: 00 01 09 04                                       ....
> HCI Event: Role Change (0x12) plen 8
  0000: 00 ee 01 0a 57 60 00 00                           ....W`..
> HCI Event: Connect Complete (0x03) plen 11
  0000: 00 0b 00 ee 01 0a 57 60  00 01 00                 ......W`...
< HCI Command: Read Remote Supported Features (0x01|0x001b) plen 2
  0000: 0b 00                                             ..
> HCI Event: Command Status (0x0f) plen 4
  0000: 00 01 1b 04                                       ....
< HCI Command: Remote Name Request (0x01|0x0019) plen 10
  0000: ee 01 0a 57 60 00 02 00  00 00                    ...W`.....
> HCI Event: Read Remote Supported Features (0x0b) plen 11
  0000: 00 0b 00 ff ff 8f fe 9b  f9 00 80                 ...........
> HCI Event: Command Status (0x0f) plen 4
  0000: 00 01 19 04                                       ....
> HCI Event: Max Slots Change (0x1b) plen 3
  0000: 0b 00 05                                          ...
> ACL data: handle 11 flags 0x02 dlen 10
    L2CAP(s): Info req: type 2
< ACL data: handle 11 flags 0x02 dlen 16
    L2CAP(s): Info rsp: type 2 result 0
      Extended feature mask 0x0080
> ACL data: handle 11 flags 0x02 dlen 10
    L2CAP(s): Info req: type 3
< ACL data: handle 11 flags 0x02 dlen 20
    L2CAP(s): Info rsp: type 3 result 0
      Unknown (len 8)
> ACL data: handle 11 flags 0x02 dlen 12
    L2CAP(s): Connect req: psm 15 scid 0x0040
< ACL data: handle 11 flags 0x02 dlen 16
    L2CAP(s): Connect rsp: dcid 0x0040 scid 0x0040 result 1 status 0
      Connection pending - No futher information available
< ACL data: handle 11 flags 0x02 dlen 10
    L2CAP(s): Info req: type 2
> ACL data: handle 11 flags 0x02 dlen 16
    L2CAP(s): Info rsp: type 2 result 0
      Extended feature mask 0x0080
< ACL data: handle 11 flags 0x02 dlen 10
    L2CAP(s): Info req: type 3
> HCI Event: Remote Name Req Complete (0x07) plen 255
  0000: 00 ee 01 0a 57 60 00 62  74 2d 30 00 00 00 00 00  ....W`.bt-0.....
  0010: 00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  ................
  0020: 00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  ................
  0030: 00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  ................
  0040: 00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  ................
  0050: 00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  ................
  0060: 00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  ................
  0070: 00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  ................
  0080: 00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  ................
  0090: 00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  ................
  00a0: 00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  ................
  00b0: 00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  ................
  00c0: 00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  ................
  00d0: 00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  ................
  00e0: 00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  ................
  00f0: 00 00 00 00 00 00 00 00  00 00 00 00 00 00 00     ...............
> HCI Event: Number of Completed Packets (0x13) plen 5
  0000: 01 0b 00 04 00                                    .....
> ACL data: handle 11 flags 0x02 dlen 20
    L2CAP(s): Info rsp: type 3 result 0
      Unknown (len 8)
< ACL data: handle 11 flags 0x02 dlen 16
    L2CAP(s): Connect rsp: dcid 0x0040 scid 0x0040 result 0 status 0
      Connection successful
> ACL data: handle 11 flags 0x02 dlen 16
    L2CAP(s): Config req: dcid 0x0040 flags 0x00 clen 4
      MTU 1691
< ACL data: handle 11 flags 0x02 dlen 18
    L2CAP(s): Config rsp: scid 0x0040 flags 0x00 result 0 clen 4
      MTU 1691
< ACL data: handle 11 flags 0x02 dlen 16
    L2CAP(s): Config req: dcid 0x0040 flags 0x00 clen 4
      MTU 1691
> HCI Event: Number of Completed Packets (0x13) plen 5
  0000: 01 0b 00 04 00                                    .....
> ACL data: handle 11 flags 0x02 dlen 18
    L2CAP(s): Config rsp: scid 0x0040 flags 0x00 result 0 clen 4
      MTU 1691
> ACL data: handle 11 flags 0x02 dlen 11
    L2CAP(d): cid 0x0040 len 7 [psm 15]
      BNEP: Control(0x01|0)
        Setup Req(0x01) size 0x02 dst 0x1116(NAP) src 0x1115(PANU)
< ACL data: handle 11 flags 0x02 dlen 12
    L2CAP(s): Disconn req: dcid 0x0040 scid 0x0040
> ACL data: handle 11 flags 0x02 dlen 12
    L2CAP(s): Disconn rsp: dcid 0x0040 scid 0x0040
> HCI Event: Number of Completed Packets (0x13) plen 5
  0000: 01 0b 00 01 00                                    .....
> HCI Event: Disconn Complete (0x05) plen 4
  0000: 00 0b 00 13                                       ....
> HCI Event: Connect Request (0x04) plen 10
  0000: ee 01 0a 57 60 00 0c 01  0a 01                    ...W`.....
< HCI Command: Accept Connection Request (0x01|0x0009) plen 7
  0000: ee 01 0a 57 60 00 00                              ...W`..
> HCI Event: Command Status (0x0f) plen 4
  0000: 00 01 09 04                                       ....
> HCI Event: Role Change (0x12) plen 8
  0000: 00 ee 01 0a 57 60 00 00                           ....W`..
> HCI Event: Connect Complete (0x03) plen 11
  0000: 00 0b 00 ee 01 0a 57 60  00 01 00                 ......W`...
< HCI Command: Read Remote Supported Features (0x01|0x001b) plen 2
  0000: 0b 00                                             ..
> HCI Event: Command Status (0x0f) plen 4
  0000: 00 01 1b 04                                       ....
< HCI Command: Remote Name Request (0x01|0x0019) plen 10
  0000: ee 01 0a 57 60 00 02 00  00 00                    ...W`.....
> HCI Event: Read Remote Supported Features (0x0b) plen 11
  0000: 00 0b 00 ff ff 8f fe 9b  f9 00 80                 ...........
> HCI Event: Command Status (0x0f) plen 4
  0000: 00 01 19 04                                       ....
> HCI Event: Max Slots Change (0x1b) plen 3
  0000: 0b 00 05                                          ...
> ACL data: handle 11 flags 0x02 dlen 10
    L2CAP(s): Info req: type 2
< ACL data: handle 11 flags 0x02 dlen 16
    L2CAP(s): Info rsp: type 2 result 0
      Extended feature mask 0x0080
> ACL data: handle 11 flags 0x02 dlen 10
    L2CAP(s): Info req: type 3
< ACL data: handle 11 flags 0x02 dlen 20
    L2CAP(s): Info rsp: type 3 result 0
      Unknown (len 8)
> ACL data: handle 11 flags 0x02 dlen 12
    L2CAP(s): Connect req: psm 15 scid 0x0040
< ACL data: handle 11 flags 0x02 dlen 16
    L2CAP(s): Connect rsp: dcid 0x0040 scid 0x0040 result 1 status 0
      Connection pending - No futher information available
< ACL data: handle 11 flags 0x02 dlen 10
    L2CAP(s): Info req: type 2
> ACL data: handle 11 flags 0x02 dlen 16
    L2CAP(s): Info rsp: type 2 result 0
      Extended feature mask 0x0080
< ACL data: handle 11 flags 0x02 dlen 10
    L2CAP(s): Info req: type 3
> HCI Event: Remote Name Req Complete (0x07) plen 255
  0000: 00 ee 01 0a 57 60 00 62  74 2d 30 00 00 00 00 00  ....W`.bt-0.....
  0010: 00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  ................
  0020: 00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  ................
  0030: 00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  ................
  0040: 00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  ................
  0050: 00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  ................
  0060: 00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  ................
  0070: 00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  ................
  0080: 00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  ................
  0090: 00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  ................
  00a0: 00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  ................
  00b0: 00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  ................
  00c0: 00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  ................
  00d0: 00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  ................
  00e0: 00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  ................
  00f0: 00 00 00 00 00 00 00 00  00 00 00 00 00 00 00     ...............
> HCI Event: Number of Completed Packets (0x13) plen 5
  0000: 01 0b 00 04 00                                    .....
> ACL data: handle 11 flags 0x02 dlen 20
    L2CAP(s): Info rsp: type 3 result 0
      Unknown (len 8)
< ACL data: handle 11 flags 0x02 dlen 16
    L2CAP(s): Connect rsp: dcid 0x0040 scid 0x0040 result 0 status 0
      Connection successful
> ACL data: handle 11 flags 0x02 dlen 16
    L2CAP(s): Config req: dcid 0x0040 flags 0x00 clen 4
      MTU 1691
< ACL data: handle 11 flags 0x02 dlen 18
    L2CAP(s): Config rsp: scid 0x0040 flags 0x00 result 0 clen 4
      MTU 1691
< ACL data: handle 11 flags 0x02 dlen 16
    L2CAP(s): Config req: dcid 0x0040 flags 0x00 clen 4
      MTU 1691
> HCI Event: Number of Completed Packets (0x13) plen 5
  0000: 01 0b 00 04 00                                    .....
> ACL data: handle 11 flags 0x02 dlen 18
    L2CAP(s): Config rsp: scid 0x0040 flags 0x00 result 0 clen 4
      MTU 1691
> ACL data: handle 11 flags 0x02 dlen 11
    L2CAP(d): cid 0x0040 len 7 [psm 15]
      BNEP: Control(0x01|0)
        Setup Req(0x01) size 0x02 dst 0x1116(NAP) src 0x1115(PANU)
< ACL data: handle 11 flags 0x02 dlen 12
    L2CAP(s): Disconn req: dcid 0x0040 scid 0x0040
> ACL data: handle 11 flags 0x02 dlen 12
    L2CAP(s): Disconn rsp: dcid 0x0040 scid 0x0040
> HCI Event: Number of Completed Packets (0x13) plen 5
  0000: 01 0b 00 01 00                                    .....
> HCI Event: Disconn Complete (0x05) plen 4
  0000: 00 0b 00 13                                       ....
> HCI Event: Connect Request (0x04) plen 10
  0000: ee 01 0a 57 60 00 0c 01  0a 01                    ...W`.....
< HCI Command: Accept Connection Request (0x01|0x0009) plen 7
  0000: ee 01 0a 57 60 00 00                              ...W`..
> HCI Event: Command Status (0x0f) plen 4
  0000: 00 01 09 04                                       ....
> HCI Event: Role Change (0x12) plen 8
  0000: 00 ee 01 0a 57 60 00 00                           ....W`..
> HCI Event: Connect Complete (0x03) plen 11
  0000: 00 0b 00 ee 01 0a 57 60  00 01 00                 ......W`...
< HCI Command: Read Remote Supported Features (0x01|0x001b) plen 2
  0000: 0b 00                                             ..
> HCI Event: Command Status (0x0f) plen 4
  0000: 00 01 1b 04                                       ....
< HCI Command: Remote Name Request (0x01|0x0019) plen 10
  0000: ee 01 0a 57 60 00 02 00  00 00                    ...W`.....
> HCI Event: Read Remote Supported Features (0x0b) plen 11
  0000: 00 0b 00 ff ff 8f fe 9b  f9 00 80                 ...........
> HCI Event: Command Status (0x0f) plen 4
  0000: 00 01 19 04                                       ....
> HCI Event: Max Slots Change (0x1b) plen 3
  0000: 0b 00 05                                          ...
> ACL data: handle 11 flags 0x02 dlen 10
    L2CAP(s): Info req: type 2
< ACL data: handle 11 flags 0x02 dlen 16
    L2CAP(s): Info rsp: type 2 result 0
      Extended feature mask 0x0080
> ACL data: handle 11 flags 0x02 dlen 10
    L2CAP(s): Info req: type 3
< ACL data: handle 11 flags 0x02 dlen 20
    L2CAP(s): Info rsp: type 3 result 0
      Unknown (len 8)
> ACL data: handle 11 flags 0x02 dlen 12
    L2CAP(s): Connect req: psm 15 scid 0x0040
< ACL data: handle 11 flags 0x02 dlen 16
    L2CAP(s): Connect rsp: dcid 0x0040 scid 0x0040 result 1 status 0
      Connection pending - No futher information available
< ACL data: handle 11 flags 0x02 dlen 10
    L2CAP(s): Info req: type 2
> ACL data: handle 11 flags 0x02 dlen 16
    L2CAP(s): Info rsp: type 2 result 0
      Extended feature mask 0x0080
< ACL data: handle 11 flags 0x02 dlen 10
    L2CAP(s): Info req: type 3
> HCI Event: Remote Name Req Complete (0x07) plen 255
  0000: 00 ee 01 0a 57 60 00 62  74 2d 30 00 00 00 00 00  ....W`.bt-0.....
  0010: 00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  ................
  0020: 00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  ................
  0030: 00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  ................
  0040: 00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  ................
  0050: 00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  ................
  0060: 00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  ................
  0070: 00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  ................
  0080: 00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  ................
  0090: 00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  ................
  00a0: 00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  ................
  00b0: 00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  ................
  00c0: 00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  ................
  00d0: 00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  ................
  00e0: 00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  ................
  00f0: 00 00 00 00 00 00 00 00  00 00 00 00 00 00 00     ...............
> ACL data: handle 11 flags 0x02 dlen 20
    L2CAP(s): Info rsp: type 3 result 0
      Unknown (len 8)
< ACL data: handle 11 flags 0x02 dlen 16
    L2CAP(s): Connect rsp: dcid 0x0040 scid 0x0040 result 0 status 0
      Connection successful
> HCI Event: Number of Completed Packets (0x13) plen 5
  0000: 01 0b 00 04 00                                    .....
> ACL data: handle 11 flags 0x02 dlen 16
    L2CAP(s): Config req: dcid 0x0040 flags 0x00 clen 4
      MTU 1691
< ACL data: handle 11 flags 0x02 dlen 18
    L2CAP(s): Config rsp: scid 0x0040 flags 0x00 result 0 clen 4
      MTU 1691
< ACL data: handle 11 flags 0x02 dlen 16
    L2CAP(s): Config req: dcid 0x0040 flags 0x00 clen 4
      MTU 1691
> HCI Event: Number of Completed Packets (0x13) plen 5
  0000: 01 0b 00 04 00                                    .....
> ACL data: handle 11 flags 0x02 dlen 18
    L2CAP(s): Config rsp: scid 0x0040 flags 0x00 result 0 clen 4
      MTU 1691
> ACL data: handle 11 flags 0x02 dlen 11
    L2CAP(d): cid 0x0040 len 7 [psm 15]
      BNEP: Control(0x01|0)
        Setup Req(0x01) size 0x02 dst 0x1116(NAP) src 0x1115(PANU)
< ACL data: handle 11 flags 0x02 dlen 12
    L2CAP(s): Disconn req: dcid 0x0040 scid 0x0040
> ACL data: handle 11 flags 0x02 dlen 12
    L2CAP(s): Disconn rsp: dcid 0x0040 scid 0x0040
> HCI Event: Number of Completed Packets (0x13) plen 5
  0000: 01 0b 00 01 00                                    .....
> HCI Event: Disconn Complete (0x05) plen 4
  0000: 00 0b 00 13  

```

client side config:

```

modprobe bnep
bluetooth -n -d
pand --connect BB:BB:BB:BB:BB:BB -n -p

```

on the client side the major error is:
```

pand[16925]: Connecting to BB:BB:BB:BB:BB:BB
pand[16925]: Connect to BB:BB:BB:BB:BB:BB failed. Success(0)

```

and bnep0 never comes up

also im running bluez 4.12

any help would be appreciated..

---

### Post by slipdipper on 2010-03-19
Ok so i got it working but i think im missing something conceptually about the whole process.

i think it has to do with pand vs bluetoothd.. as i ponder how this all is supposed to work, heres my solution. 

Keep in mind this might not be the way its *supposed* to work. I think the way its supposed to work is by using strictly bluetoothd and simple-agent (comes with bluez). I think pand is supposed to be deprecated. 

Heres my setup:

MASTER Config:
---------------------------------
/etc/bluetooth/main.conf
```

DisablePlugins=network,input

```
(prolly dont need to disable input)

create connect script (this is to start a dhcpd server etc..)
master.sh:
```

#!/bin/sh
ifconfig bnep0 10.0.0.1 netmask 255.255.255.0
dhcpd3 -cf /tmp/dhcp.conf

```

then just 
```

chmod +x master.sh

```

Start bluetoothd (with debugging, but not needed)
```

bluetoothd -n -d

```

start pand (in foreground, but not needed):
```
 
pand -s -r GN -M -b -P -u master.sh

```

slave side configuration
------------------------------------
create client.sh 
```

#!/bin/sh
ifconfig bnep0 up
sleep 2
dhclient bnep0

```

for good measure
```

chmod +x client.sh

```

start pand (in foreground, but not needed):
AA:AA:AA:AA:AA:AA = bd_addr of master
```

pand -c AA:AA:AA:AA:AA:AA -n -p -u client.sh

```


To confirm
```

ping 10.0.0.1

```

Keep in mind this doesnt pair (auth/encrypt) so this means anyone can connect to your master without a pin or anything like that.. very insecure.. 

ima try to make it all work with simple-agent next..

---

