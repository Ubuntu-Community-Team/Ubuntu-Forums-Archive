---
title: "Bluetooth - Send and Receive problem"
date: 2009-03-30
forum: Networking &amp; Wireless
---

### Post by remcoj1 on 2009-03-30
Hello,

I am curenty trying to connect 2 linux pc's with eachother by using 2 Bluetooth dongels
A MSI dongle and an Epox dongle.

I use RFCOMM to try to connect the two devices.
A connection is made when I use the Epox dongle as client and the MSI dongle as server. However if I reverse those roles (MSI client, Epox server) I get the error message: "Can't connect RFCOMM socket: Operation now in progress"

I am using Kernel version: 2.6.18

Terminal:
Epox = Listen   --   MSI = connect:
    Epox side:
    ```

    user@eadevenv:~$ rfcomm listen 0   
    Waiting for connection on channel 1
    Connection from 00:11:22:33:44:55 to /dev/rfcomm0
    Press CTRL-C for hangup
    
```
    MSI side:
    ```

    user@eadevenv:~$rfcomm connect 0 AA:BB:CC:DD:EE:FF 1
    Connected /dev/rfcomm0 to AA:BB:CC:DD:EE:FF on channel 1
    Connection from 00:11:22:33:44:55 to /dev/rfcomm0
    Press CTRL-C for hangup
    
```

Epox = Connect   --   MSI = Listen:
    Epox side:
    ```

    user@eadevenv:~$rfcomm connect 0 00:11:22:33:44:55 1 
    Can't connect RFCOMM socket: Operation now in progress
    
```
    MSI side:
    ```

    user@eadevenv:~$ rfcomm listen 0   
    Waiting for connection on channel 1
    
```

I tried to debug the problem by using hcidump. De following results where given:

Epox = Client   --  MSI = Server       ERROR
```

HCI sniffer - Bluetooth packet analyzer ver 1.32
device: hci0 snap_len: 1028 filter: 0xffffffff
< HCI Command: Create Connection (0x01|0x0005) plen 13
> HCI Event: Command Status (0x0f) plen 4
> HCI Event: Connect Complete (0x03) plen 11
< ACL data: handle 43 flags 0x02 dlen 12
    L2CAP(s): Connect req: psm 3 scid 0x0040
< HCI Command: Read Remote Supported Features (0x01|0x001b) plen 2
> HCI Event: Number of Completed Packets (0x13) plen 5
> HCI Event: Max Slots Change (0x1b) plen 3
> HCI Event: Command Status (0x0f) plen 4
> HCI Event: Command Status (0x0f) plen 4
< HCI Command: Write Link Policy Settings (0x02|0x000d) plen 4
> HCI Event: Read Remote Supported Features (0x0b) plen 11
> HCI Event: Command Complete (0x0e) plen 6
< HCI Command: Disconnect (0x01|0x0006) plen 3
> HCI Event: Command Status (0x0f) plen 4
> HCI Event: Disconn Complete (0x05) plen 4

```

MSI = Client   --  Epox = Server       OK 
```

HCI sniffer - Bluetooth packet analyzer ver 1.32
device: hci0 snap_len: 1028 filter: 0xffffffff
< HCI Command: Create Connection (0x01|0x0005) plen 13
> HCI Event: Command Status (0x0f) plen 4
> HCI Event: Connect Complete (0x03) plen 11
< ACL data: handle 1 flags 0x02 dlen 12
    L2CAP(s): Connect req: psm 3 scid 0x0040
< HCI Command: Read Remote Supported Features (0x01|0x001b) plen 2
> HCI Event: Max Slots Change (0x1b) plen 3
> ACL data: handle 1 flags 0x02 dlen 16
    L2CAP(s): Connect rsp: dcid 0x0040 scid 0x0040 result 0 status 0
      Connection successful
< ACL data: handle 1 flags 0x02 dlen 16
    L2CAP(s): Config req: dcid 0x0040 flags 0x00 clen 4
      MTU 1013
> HCI Event: Command Status (0x0f) plen 4
< HCI Command: Write Link Policy Settings (0x02|0x000d) plen 4
> ACL data: handle 1 flags 0x02 dlen 14
    L2CAP(s): Config rsp: scid 0x0040 flags 0x00 result 0 clen 0
      Success
> ACL data: handle 1 flags 0x02 dlen 16
    L2CAP(s): Config req: dcid 0x0040 flags 0x00 clen 4
      MTU 1013
< ACL data: handle 1 flags 0x02 dlen 14
    L2CAP(s): Config rsp: scid 0x0040 flags 0x00 result 0 clen 0
      Success
< ACL data: handle 1 flags 0x02 dlen 8
    L2CAP(d): cid 0x0040 len 4 [psm 3]
      RFCOMM(s): SABM: cr 1 dlci 0 pf 1 ilen 0 fcs 0x1c
> ACL data: handle 1 flags 0x02 dlen 8
    L2CAP(d): cid 0x0040 len 4 [psm 3]
      RFCOMM(s): UA: cr 1 dlci 0 pf 1 ilen 0 fcs 0xd7
< ACL data: handle 1 flags 0x02 dlen 18
    L2CAP(d): cid 0x0040 len 14 [psm 3]
      RFCOMM(s): PN CMD: cr 1 dlci 0 pf 0 ilen 10 fcs 0x70 mcc_len 8
      dlci 2 frame_type 0 credit_flow 15 pri 7 ack_timer 0
      frame_size 1008 max_retrans 0 credits 7
> ACL data: handle 1 flags 0x02 dlen 18
    L2CAP(d): cid 0x0040 len 14 [psm 3]
      RFCOMM(s): PN RSP: cr 0 dlci 0 pf 0 ilen 10 fcs 0xaa mcc_len 8
      dlci 2 frame_type 0 credit_flow 14 pri 7 ack_timer 0
      frame_size 1008 max_retrans 0 credits 7
< ACL data: handle 1 flags 0x02 dlen 8
    L2CAP(d): cid 0x0040 len 4 [psm 3]
      RFCOMM(s): SABM: cr 1 dlci 2 pf 1 ilen 0 fcs 0x59
> ACL data: handle 1 flags 0x02 dlen 8
    L2CAP(d): cid 0x0040 len 4 [psm 3]
      RFCOMM(s): UA: cr 1 dlci 2 pf 1 ilen 0 fcs 0x92
< ACL data: handle 1 flags 0x02 dlen 12
    L2CAP(d): cid 0x0040 len 8 [psm 3]
      RFCOMM(s): MSC CMD: cr 1 dlci 0 pf 0 ilen 4 fcs 0x70 mcc_len 2
      dlci 2 fc 0 rtc 1 rtr 1 ic 0 dv 1 b1 1 b2 1 b3 0 len 0
> ACL data: handle 1 flags 0x02 dlen 12
    L2CAP(d): cid 0x0040 len 8 [psm 3]
      RFCOMM(s): MSC CMD: cr 0 dlci 0 pf 0 ilen 4 fcs 0xaa mcc_len 2
      dlci 2 fc 0 rtc 1 rtr 1 ic 0 dv 1 b1 1 b2 1 b3 0 len 0
< ACL data: handle 1 flags 0x02 dlen 12
    L2CAP(d): cid 0x0040 len 8 [psm 3]
      RFCOMM(s): MSC RSP: cr 1 dlci 0 pf 0 ilen 4 fcs 0x70 mcc_len 2
      dlci 2 fc 0 rtc 1 rtr 1 ic 0 dv 1 b1 1 b2 1 b3 0 len 0
> ACL data: handle 1 flags 0x02 dlen 12
    L2CAP(d): cid 0x0040 len 8 [psm 3]
      RFCOMM(s): MSC RSP: cr 0 dlci 0 pf 0 ilen 4 fcs 0xaa mcc_len 2
      dlci 2 fc 0 rtc 1 rtr 1 ic 0 dv 1 b1 1 b2 1 b3 0 len 0
> HCI Event: Number of Completed Packets (0x13) plen 6
< ACL data: handle 1 flags 0x02 dlen 9
    L2CAP(d): cid 0x0040 len 5 [psm 3]
      RFCOMM(d): UIH: cr 1 dlci 2 pf 1 ilen 0 fcs 0x86 credits 33
> HCI Event: Connection Packet Type Changed (0x1d) plen 5
> ACL data: handle 1 flags 0x02 dlen 9
    L2CAP(d): cid 0x0040 len 5 [psm 3]
      RFCOMM(d): UIH: cr 0 dlci 2 pf 1 ilen 0 fcs 0x5c credits 33
> HCI Event: Read Remote Supported Features (0x0b) plen 11
> HCI Event: Number of Completed Packets (0x13) plen 6
< ACL data: handle 1 flags 0x02 dlen 14
    L2CAP(d): cid 0x0040 len 10 [psm 3]
      RFCOMM(d): UIH: cr 1 dlci 2 pf 0 ilen 6 fcs 0x9a
> ACL data: handle 1 flags 0x02 dlen 8
    L2CAP(d): cid 0x0040 len 4 [psm 3]
      RFCOMM(s): DISC: cr 0 dlci 2 pf 1 ilen 0 fcs 0xd9
> HCI Event: Command Complete (0x0e) plen 6
> HCI Event: Number of Completed Packets (0x13) plen 6
< ACL data: handle 1 flags 0x02 dlen 8
    L2CAP(d): cid 0x0040 len 4 [psm 3]
      RFCOMM(s): DISC: cr 1 dlci 2 pf 1 ilen 0 fcs 0xb8
> ACL data: handle 1 flags 0x02 dlen 8
    L2CAP(d): cid 0x0040 len 4 [psm 3]
      RFCOMM(s): UA: cr 1 dlci 2 pf 1 ilen 0 fcs 0x92
> HCI Event: Number of Completed Packets (0x13) plen 6
< ACL data: handle 1 flags 0x02 dlen 8
    L2CAP(d): cid 0x0040 len 4 [psm 3]
      RFCOMM(s): UA: cr 0 dlci 2 pf 1 ilen 0 fcs 0xf3
> HCI Event: Number of Completed Packets (0x13) plen 6
< ACL data: handle 1 flags 0x02 dlen 8
    L2CAP(d): cid 0x0040 len 4 [psm 3]
      RFCOMM(s): DISC: cr 1 dlci 0 pf 1 ilen 0 fcs 0xfd
> ACL data: handle 1 flags 0x02 dlen 8
    L2CAP(d): cid 0x0040 len 4 [psm 3]
      RFCOMM(s): DM: cr 1 dlci 2 pf 1 ilen 0 fcs 0x73
> HCI Event: Number of Completed Packets (0x13) plen 6
< ACL data: handle 1 flags 0x02 dlen 12
    L2CAP(s): Disconn req: dcid 0x0040 scid 0x0040
> HCI Event: Number of Completed Packets (0x13) plen 6
> ACL data: handle 1 flags 0x02 dlen 8
    L2CAP(d): cid 0x0040 len 4 [psm 3]
      RFCOMM(s): UA: cr 1 dlci 0 pf 1 ilen 0 fcs 0xd7
> HCI Event: Number of Completed Packets (0x13) plen 6
> HCI Event: Number of Completed Packets (0x13) plen 6
> ACL data: handle 1 flags 0x02 dlen 12
    L2CAP(s): Disconn rsp: dcid 0x0040 scid 0x0040
> HCI Event: Number of Completed Packets (0x13) plen 6
> HCI Event: Number of Completed Packets (0x13) plen 6
> HCI Event: Number of Completed Packets (0x13) plen 6
> HCI Event: Number of Completed Packets (0x13) plen 6
> HCI Event: Number of Completed Packets (0x13) plen 6
< HCI Command: Disconnect (0x01|0x0006) plen 3
> HCI Event: Command Status (0x0f) plen 4
> HCI Event: Disconn Complete (0x05) plen 4

```

Other information:

hciconfig-a
```

MSI
hci0:   Type: USB
        BD Address: 00:11:22:33:44:55 ACL MTU: 1021:8 SCO MTU: 48:10
        UP RUNNING PSCAN
        RX bytes:517 acl:14 sco:0 events:37 errors:0
        TX bytes:549 acl:14 sco:0 commands:18 errors:0
        Features: 0xff 0xfe 0x8d 0x3e 0x88 0x19 0x00 0x00
        Packet type: DM1 DM3 DM5 DH1 DH3 DH5 HV1 HV2 HV3
        Link policy: RSWITCH HOLD SNIFF PARK
        Link mode: SLAVE ACCEPT
        Name: 'name-0'
        Class: 0x3e0100
        Service Classes: Networking, Rendering, Capturing, Object Transfer, Audio
        Device Class: Computer, Uncategorized
        HCI Ver: 2.0 (0x3) HCI Rev: 0x2c6 LMP Ver: 2.0 (0x3) LMP Subver: 0x2c6
        Manufacturer: Integrated System Solution Corp. (57)

EPOX
hci0:   Type: USB
        BD Address: AA:BB:CC:DD:EE:FF ACL MTU: 192:8 SCO MTU: 64:8
        UP RUNNING
        RX bytes:110 acl:0 sco:0 events:13 errors:0
        TX bytes:294 acl:0 sco:0 commands:12 errors:0
        Features: 0xff 0xff 0x8b 0xf8 0x18 0x18 0x00 0x80
        Packet type: DM1 DM3 DM5 DH1 DH3 DH5 HV1 HV2 HV3
        Link policy: RSWITCH HOLD SNIFF PARK
        Link mode: SLAVE ACCEPT
        Name: 'name-0'
        Class: 0x3e0100
        Service Classes: Networking, Rendering, Capturing, Object Transfer, Audio
        Device Class: Computer, Uncategorized
        HCI Ver: 1.1 (0x1) HCI Rev: 0x639 LMP Ver: 1.1 (0x1) LMP Subver: 0x639
        Manufacturer: Cambridge Silicon Radio (10)

```

HCI-daemon
```

#
# HCI daemon configuration file.
#

# HCId options
options {
        # Automatically initialize new devices
        autoinit yes;

        # Security Manager mode
        #   none - Security manager disabled

	#   auto - Use local PIN for incoming connections
        #   user - Always ask user for a PIN
        #
        security none;

        # Pairing mode
        #   none  - Pairing disabled
        #   multi - Allow pairing with already paired devices
        #   once  - Pair once and deny successive attempts
        pairing multi;

        # Default PIN code for incoming connections
        passkey "1234";
}

# Default settings for HCI devices
device {
        # Local device name
        #   %d - device id
        #   %h - host name
        name "%h-%d";

        # Local device class
        
	class 0x3e0100;

        # Default packet type
        #pkt_type DH1,DM1,HV1;

        # Inquiry and Page scan
        iscan enable; pscan enable;

        # Default link mode
        #   none   - no specific policy
        #   accept - always accept incoming connections
        #   master - become master on incoming connections,
        #            deny role switch on outgoing connections
        lm accept;

        # Default link policy
        #   none    - no specific policy
        #   rswitch - allow role switch
        #   hold    - allow hold mode
        #   sniff   - allow sniff mode
        #   park    - allow park mode
        lp rswitch,hold,sniff,park;
}
        class 0x3e0100;

        # Default packet type
        #pkt_type DH1,DM1,HV1;

        # Inquiry and Page scan
        iscan enable; pscan enable;

        # Default link mode
        #   none   - no specific policy
        #   accept - always accept incoming connections
        #   master - become master on incoming connections,
        #            deny role switch on outgoing connections
        lm accept;

        # Default link policy
        #   none    - no specific policy
        #   rswitch - allow role switch
        #   hold    - allow hold mode
        #   sniff   - allow sniff mode
        #   park    - allow park mode
        lp rswitch,hold,sniff,park;
}

```

RFCOMM.config
```

rfcomm0 {
        # Automatically bind the device at startup
        bind no;

        # Bluetooth address of the device
        device AA:BB:CC:DD:EE:FF;

        # RFCOMM channel for the connection
        channel 1;

        # Description of the connection
#       comment "Example Bluetooth device";
}

```

---

### Post by remcoj1 on 2009-04-01
Problem is solved.

I don't know why but everything works when I use ubuntu 8.04 instead of 8.10

---

