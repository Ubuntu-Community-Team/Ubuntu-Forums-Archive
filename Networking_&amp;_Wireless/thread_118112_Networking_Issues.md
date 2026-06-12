---
title: "Networking Issues"
date: 2006-01-16
forum: Networking &amp; Wireless
---

### Post by haddad on 2006-01-16
Hello

I have been asked to fix an ubuntu installation which has a problem of dissappearing from the network.

The box has a single network card:

IP 192.168.27.10
MASK 255.255.255.0
GATEWAY 192.168.27.1

I can ping 192.168.27.1 from the machine but all traffic destined for outside the LAN is unsuccesful

When I did a traceroute for a machine outside the LAN the packets were sent to 192.168.27.10 instead of the default gateway 192.168.27.1.

Below are some lines from dmesg which I suspect say something about the problem but I dont understand what they mean

```

ACPI: PCI interrupt 0000:01:0a.0[A] -> GSI 11 (level, low) -> IRQ 11
NET: Registered protocol family 10
Disabled Privacy Extensions on device c02f0500(lo)
IPv6 over IPv4 tunneling driver
ACPI: Power Button (FF) [PWRF]
ACPI: Sleep Button (CM) [SBTN]
ibm_acpi: ec object not found
apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
apm: overridden by ACPI.
eth0: no IPv6 routers present
ip_tables: (C) 2000-2002 Netfilter core team
ip_conntrack version 2.1 (2558 buckets, 20464 max) - 336 bytes per conntrack
Inbound IN=eth0 OUT= MAC=00:04:76:22:a0:09:00:09:0f:0c:2b:e7:08:00 SRC=221.203.145.54 DST=192.168.27.10 LEN=501 TOS=0x00 PREC=0x00 TTL=41 ID=0 DF PROTO=UDP SPT=32847 DPT=1026 LEN=481
Outbound IN= OUT=eth0 SRC=192.168.27.10 DST=192.168.27.255 LEN=96 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=137 DPT=137 LEN=76
Outbound IN= OUT=eth0 SRC=192.168.27.10 DST=192.168.27.255 LEN=96 TOS=0x00 PREC=0x00 TTL=64 ID=1 DF PROTO=UDP SPT=137 DPT=137 LEN=76
Outbound IN= OUT=eth0 SRC=192.168.27.10 DST=192.168.27.255 LEN=96 TOS=0x00 PREC=0x00 TTL=64 ID=2 DF PROTO=UDP SPT=137 DPT=137 LEN=76
Outbound IN= OUT=eth0 SRC=192.168.27.10 DST=192.168.27.255 LEN=96 TOS=0x00 PREC=0x00 TTL=64 ID=3 DF PROTO=UDP SPT=137 DPT=137 LEN=76
Outbound IN= OUT=eth0 SRC=192.168.27.10 DST=192.168.27.255 LEN=96 TOS=0x00 PREC=0x00 TTL=64 ID=4 DF PROTO=UDP SPT=137 DPT=137 LEN=76
Outbound IN= OUT=eth0 SRC=192.168.27.10 DST=192.168.27.255 LEN=259 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=138 DPT=138 LEN=239

```

Help please?

---

