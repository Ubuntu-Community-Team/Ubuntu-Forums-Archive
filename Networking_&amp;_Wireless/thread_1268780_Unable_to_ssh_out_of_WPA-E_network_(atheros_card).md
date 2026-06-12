---
title: "Unable to ssh out of WPA-E network (atheros card)"
date: 2009-09-17
forum: Networking &amp; Wireless
---

### Post by rimunroe on 2009-09-17
Hello, this is my first post on the forums.

I seem to be unable to ssh out from my school's wireless network using my Ubuntu laptop.  One of my friends with similar hardware and the same distribution (9.04) has the same problem, but everyone else seems to be problem free as far as their ability to make ssh connections from the wireless network goes.  The wireless network I am having trouble on uses WPA-Enterprise.  I have no trouble ssh'ing from my home wireless network or from any others which I've tried.  I have not tried any wireless networks using the same encryption as the school's wireless.  I have the same problem no matter which of the four external networks I try to ssh to.  I don't run into the problem when I attempt to ssh to the IP address listed as the "default route" in the network manager.

Running "ssh user@server" when "server" is outside of the school wireless network (SSID "air-cnu") results in no response for a minute or two, and then the output "Connection closed by <Server IP>".  

"ssh -vvvv defender.pcs.cnu.edu" yields the following: 

(note: defender.pcs.cnu.edu is on a completely separate network)
```

rimunroe@antarctica:~$ ssh -vvvv defender.pcs.cnu.edu
OpenSSH_5.1p1 Debian-5ubuntu1, OpenSSL 0.9.8g 19 Oct 2007
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug2: ssh_connect: needpriv 0
debug1: Connecting to defender.pcs.cnu.edu [137.155.2.27] port 22.
debug1: Connection established.
debug1: identity file /home/rimunroe/.ssh/identity type -1
debug1: identity file /home/rimunroe/.ssh/id_rsa type -1
debug1: identity file /home/rimunroe/.ssh/id_dsa type -1
debug1: Remote protocol version 2.0, remote software version OpenSSH_4.7p1 Debian-8ubuntu1.2
debug1: match: OpenSSH_4.7p1 Debian-8ubuntu1.2 pat OpenSSH_4*
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_5.1p1 Debian-5ubuntu1
debug2: fd 3 setting O_NONBLOCK
debug1: SSH2_MSG_KEXINIT sent
Connection closed by 137.155.2.27
rimunroe@antarctica:~$

```"ssh -vvvv 137.155.128.4" yieds the following:

(137.155.128.4 is the address listed as my default route)
```

rimunroe@antarctica:~$ ssh -vvvv 137.155.128.4
OpenSSH_5.1p1 Debian-5ubuntu1, OpenSSL 0.9.8g 19 Oct 2007
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug2: ssh_connect: needpriv 0
debug1: Connecting to 137.155.128.4 [137.155.128.4] port 22.
debug1: Connection established.
debug1: identity file /home/rimunroe/.ssh/identity type -1
debug1: identity file /home/rimunroe/.ssh/id_rsa type -1
debug1: identity file /home/rimunroe/.ssh/id_dsa type -1
debug1: Remote protocol version 2.0, remote software version 3.0.4 SSH Secure Shell
debug1: match: 3.0.4 SSH Secure Shell pat 3.0.*
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_5.1p1 Debian-5ubuntu1
debug2: fd 3 setting O_NONBLOCK
debug1: SSH2_MSG_KEXINIT sent
debug1: SSH2_MSG_KEXINIT received
debug2: kex_parse_kexinit: diffie-hellman-group-exchange-sha256,diffie-hellman-group-exchange-sha1,diffie-hellman-group14-sha1,diffie-hellman-group1-sha1
debug2: kex_parse_kexinit: ssh-rsa,ssh-dss
debug2: kex_parse_kexinit: aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,arcfour128,arcfour256,arcfour,aes192-cbc,aes256-cbc,rijndael-cbc@lysator.liu.se,aes128-ctr,aes192-ctr,aes256-ctr
debug2: kex_parse_kexinit: aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,arcfour128,arcfour256,arcfour,aes192-cbc,aes256-cbc,rijndael-cbc@lysator.liu.se,aes128-ctr,aes192-ctr,aes256-ctr
debug2: kex_parse_kexinit: hmac-md5,hmac-sha1,umac-64@openssh.com,hmac-ripemd160,hmac-ripemd160@openssh.com,hmac-sha1-96,hmac-md5-96
debug2: kex_parse_kexinit: hmac-md5,hmac-sha1,umac-64@openssh.com,hmac-ripemd160,hmac-ripemd160@openssh.com,hmac-sha1-96,hmac-md5-96
debug2: kex_parse_kexinit: none,zlib@openssh.com,zlib
debug2: kex_parse_kexinit: none,zlib@openssh.com,zlib
debug2: kex_parse_kexinit: 
debug2: kex_parse_kexinit: 
debug2: kex_parse_kexinit: first_kex_follows 0 
debug2: kex_parse_kexinit: reserved 0 
debug2: kex_parse_kexinit: diffie-hellman-group1-sha1
debug2: kex_parse_kexinit: ssh-dss
debug2: kex_parse_kexinit: 3des-cbc,aes128-cbc,blowfish-cbc,twofish128-cbc,cast128-cbc,arcfour
debug2: kex_parse_kexinit: 3des-cbc,aes128-cbc,blowfish-cbc,twofish128-cbc,cast128-cbc,arcfour
debug2: kex_parse_kexinit: hmac-md5,hmac-md5-96,hmac-sha1,hmac-sha1-96,hmac-ripemd160
debug2: kex_parse_kexinit: hmac-md5,hmac-md5-96,hmac-sha1,hmac-sha1-96,hmac-ripemd160
debug2: kex_parse_kexinit: none
debug2: kex_parse_kexinit: none
debug2: kex_parse_kexinit: 
debug2: kex_parse_kexinit: 
debug2: kex_parse_kexinit: first_kex_follows 0 
debug2: kex_parse_kexinit: reserved 0 
debug2: mac_setup: found hmac-md5
debug1: kex: server->client aes128-cbc hmac-md5 none
debug2: mac_setup: found hmac-md5
debug1: kex: client->server aes128-cbc hmac-md5 none
debug2: dh_gen_key: priv key bits set: 134/256
debug2: bits set: 525/1024
debug1: sending SSH2_MSG_KEXDH_INIT
debug1: expecting SSH2_MSG_KEXDH_REPLY
debug3: check_host_in_hostfile: filename /home/rimunroe/.ssh/known_hosts
debug3: check_host_in_hostfile: match line 5
debug1: Host '137.155.128.4' is known and matches the DSA host key.
debug1: Found key in /home/rimunroe/.ssh/known_hosts:5
debug2: bits set: 514/1024
debug1: ssh_dss_verify: signature correct
debug2: kex_derive_keys
debug2: set_newkeys: mode 1
debug1: SSH2_MSG_NEWKEYS sent
debug1: expecting SSH2_MSG_NEWKEYS
debug2: set_newkeys: mode 0
debug1: SSH2_MSG_NEWKEYS received
debug1: SSH2_MSG_SERVICE_REQUEST sent
debug2: service_accept: ssh-userauth
debug1: SSH2_MSG_SERVICE_ACCEPT received
debug2: key: /home/rimunroe/.ssh/identity ((nil))
debug2: key: /home/rimunroe/.ssh/id_rsa ((nil))
debug2: key: /home/rimunroe/.ssh/id_dsa ((nil))
debug3: Received SSH2_MSG_IGNORE
debug1: Authentications that can continue: publickey,password
debug3: start over, passed a different list publickey,password
debug3: preferred gssapi-keyex,gssapi-with-mic,gssapi,publickey,keyboard-interactive,password
debug3: authmethod_lookup publickey
debug3: remaining preferred: keyboard-interactive,password
debug3: authmethod_is_enabled publickey
debug1: Next authentication method: publickey
debug1: Trying private key: /home/rimunroe/.ssh/identity
debug3: no such identity: /home/rimunroe/.ssh/identity
debug1: Trying private key: /home/rimunroe/.ssh/id_rsa
debug3: no such identity: /home/rimunroe/.ssh/id_rsa
debug1: Trying private key: /home/rimunroe/.ssh/id_dsa
debug3: no such identity: /home/rimunroe/.ssh/id_dsa
debug2: we did not send a packet, disable method
debug3: authmethod_lookup password
debug3: remaining preferred: ,password
debug3: authmethod_is_enabled password
debug1: Next authentication method: password
rimunroe@137.155.128.4's password: 

```Running PuTTY under WINE gives me the same hang.  I talked to some of the people in ITS and they took a look at the traffic rules and said that ssh shouldn't be being blocked by any rules (which I suppose is obvious given that most other people can ssh wirelessly with no problem).

My laptop is a brand new Lenovo SL500.  I know that one of my friends who does **not** have the problem runs 9.04 and has a broadcom card.

Here are the outputs of various commands I read that I should includ in my post:

$ lspci -nn | grep Atheros
```

02:00.0 Ethernet controller [0200]: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter [168c:001c] (rev 01)

```$ lsub
```

Bus 002 Device 002: ID 17ef:4808 Lenovo 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```$ ifconfig
```

wlan0     Link encap:Ethernet  HWaddr 00:26:5e:e9:60:b9  
          inet addr:137.155.129.100  Bcast:137.155.131.255  Mask:255.255.252.0
          inet6 addr: fe80::226:5eff:fee9:60b9/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4703155 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2050993 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2285802510 (2.2 GB)  TX bytes:482999659 (482.9 MB)

```$ iwconfig
```

wlan0     IEEE 802.11bg  ESSID:"air-cnu"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:0B:86:AD:00:D1   
          Bit Rate=9 Mb/s   Tx-Power=20 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality=84/100  Signal level:-48 dBm  Noise level=-102 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```$ lsmod | grep ath5k
```

ath5k                 107520  0 
mac80211              217592  1 ath5k
led_class              12036  2 lenovo_sl_laptop,ath5k
cfg80211               38288  2 ath5k,mac80211

```$ dmesg
```

[    0.000000] BIOS EBDA/lowmem at: 0009e800/0009e800
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.28-15-generic (buildd@palmer) (gcc version 4.3.3 (Ubuntu 4.3.3-5ubuntu4) ) #49-Ubuntu SMP Tue Aug 18 18:40:08 UTC 2009 (Ubuntu 2.6.28-15.49-generic)
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   NSC Geode by NSC
[    0.000000]   Cyrix CyrixInstead
[    0.000000]   Centaur CentaurHauls
[    0.000000]   Transmeta GenuineTMx86
[    0.000000]   Transmeta TransmetaCPU
[    0.000000]   UMC UMC UMC UMC
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009e800 (usable)
[    0.000000]  BIOS-e820: 000000000009e800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e3000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000007ddb0000 (usable)
[    0.000000]  BIOS-e820: 000000007ddb0000 - 000000007ddbe400 (ACPI data)
[    0.000000]  BIOS-e820: 000000007ddbe400 - 000000007ddf0000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000007ddf0000 - 000000007de00000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffb00000 - 0000000100000000 (reserved)
[    0.000000] DMI 2.5 present.
[    0.000000] last_pfn = 0x7ddb0 max_arch_pfn = 0x100000
[    0.000000] Scanning 2 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000002000 (usable)
[    0.000000]  modified: 0000000000002000 - 0000000000006000 (reserved)
[    0.000000]  modified: 0000000000006000 - 0000000000007000 (usable)
[    0.000000]  modified: 0000000000007000 - 0000000000010000 (reserved)
[    0.000000]  modified: 0000000000010000 - 0000000000091800 (usable)
[    0.000000]  modified: 000000000009e800 - 00000000000a0000 (reserved)
[    0.000000]  modified: 00000000000e3000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 000000007ddb0000 (usable)
[    0.000000]  modified: 000000007ddb0000 - 000000007ddbe400 (ACPI data)
[    0.000000]  modified: 000000007ddbe400 - 000000007ddf0000 (ACPI NVS)
[    0.000000]  modified: 000000007ddf0000 - 000000007de00000 (reserved)
[    0.000000]  modified: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  modified: 00000000ffb00000 - 0000000100000000 (reserved)
[    0.000000] kernel direct mapping tables up to 373fe000 @ 10000-16000
[    0.000000] RAMDISK: 378bb000 - 37fef7c7
[    0.000000] Allocated new RAMDISK: 0087d000 - 00fb17c7
[    0.000000] Move RAMDISK from 00000000378bb000 - 0000000037fef7c6 to 0087d000 - 00fb17c6
[    0.000000] ACPI: RSDP 000F92E0, 0024 (r2 ACPIAM)
[    0.000000] ACPI: XSDT 7DDB0100, 0084 (r1 LENOVO TP-6A         570 MSFT       97)
[    0.000000] ACPI: FACP 7DDB0290, 00F4 (r3 LENOVO TP-6A         570 MSFT       97)
[    0.000000] ACPI: DSDT 7DDB0680, BF09 (r1  LENOV TP-6A         180 INTL 20051117)
[    0.000000] ACPI: FACS 7DDBE400, 0040
[    0.000000] ACPI: APIC 7DDB0390, 005C (r1 LENOVO TP-6A         570 MSFT       97)
[    0.000000] ACPI: MCFG 7DDB0430, 003C (r1 LENOVO TP-6A         570 MSFT       97)
[    0.000000] ACPI: SLIC 7DDB0470, 0176 (r1 LENOVO TP-6A         570 MSFT       97)
[    0.000000] ACPI: ECDT 7DDB0620, 0054 (r1 LENOVO TP-6A         570 MSFT       97)
[    0.000000] ACPI: DBGP 7DDB03F0, 0034 (r1 LENOVO TP-6A         570 MSFT       97)
[    0.000000] ACPI: BOOT 7DDB05F0, 0028 (r1 LENOVO TP-6A         570 MSFT       97)
[    0.000000] ACPI: OEMB 7DDBE440, 0071 (r1 LENOVO TP-6A         570 MSFT       97)
[    0.000000] ACPI: HPET 7DDBC590, 0038 (r1 LENOVO TP-6A         570 MSFT       97)
[    0.000000] ACPI: GSCI 7DDBE4C0, 2024 (r1 LENOVO TP-6A         570 MSFT       97)
[    0.000000] ACPI: ATKG 7DDC06F0, 8024 (r1 LENOVO TP-6A         570 MSFT       97)
[    0.000000] ACPI: SSDT 7DDC9280, 04E6 (r1  PmRef TP-6A         180 INTL 20051117)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 1129MB HIGHMEM available.
[    0.000000] 883MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 373fe000
[    0.000000]   low ram: 00000000 - 373fe000
[    0.000000]   bootmap 00012000 - 00018e80
[    0.000000] (9 early reservations) ==> bootmem [0000000000 - 00373fe000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
[    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
[    0.000000]   #3 [0000100000 - 00008780ac]    TEXT DATA BSS ==> [0000100000 - 00008780ac]
[    0.000000]   #4 [0000879000 - 000087d000]    INIT_PG_TABLE ==> [0000879000 - 000087d000]
[    0.000000]   #5 [000009e800 - 0000100000]    BIOS reserved ==> [000009e800 - 0000100000]
[    0.000000]   #6 [0000010000 - 0000012000]          PGTABLE ==> [0000010000 - 0000012000]
[    0.000000]   #7 [000087d000 - 0000fb17c7]      NEW RAMDISK ==> [000087d000 - 0000fb17c7]
[    0.000000]   #8 [0000012000 - 0000019000]          BOOTMAP ==> [0000012000 - 0000019000]
[    0.000000] found SMP MP-table at [c00ff780] 000ff780
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000000 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x000373fe
[    0.000000]   HighMem  0x000373fe -> 0x0007ddb0
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[4] active PFN ranges
[    0.000000]     0: 0x00000000 -> 0x00000002
[    0.000000]     0: 0x00000006 -> 0x00000007
[    0.000000]     0: 0x00000010 -> 0x00000091
[    0.000000]     0: 0x00000100 -> 0x0007ddb0
[    0.000000] On node 0 totalpages: 515380
[    0.000000] free_area_init_node: node 0, pgdat c06cb500, node_mem_map c1000000
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3940 pages, LIFO batch:0
[    0.000000]   Normal zone: 1736 pages used for memmap
[    0.000000]   Normal zone: 220470 pages, LIFO batch:31
[    0.000000]   HighMem zone: 2260 pages used for memmap
[    0.000000]   HighMem zone: 286942 pages, LIFO batch:31
[    0.000000]   Movable zone: 0 pages used for memmap
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] ACPI: HPET id: 0x8086a301 base: 0xfed00000
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] SMP: Allowing 2 CPUs, 0 hotplug CPUs
[    0.000000] PM: Registered nosave memory: 0000000000002000 - 0000000000006000
[    0.000000] PM: Registered nosave memory: 0000000000007000 - 0000000000010000
[    0.000000] PM: Registered nosave memory: 0000000000091000 - 000000000009f000
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e3000
[    0.000000] PM: Registered nosave memory: 00000000000e3000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 80000000 (gap: 7de00000:81000000)
[    0.000000] PERCPU: Allocating 45056 bytes of per cpu data
[    0.000000] NR_CPUS: 64, nr_cpu_ids: 2, nr_node_ids 1
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 511352
[    0.000000] Kernel command line: root=UUID=34b47da4-5ad7-4bc2-8f4d-e7b4bec8cb41 ro quiet splash 
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Extended CMOS year: 2000
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 1995.011 MHz processor.
[    0.004000] Console: colour VGA+ 80x25
[    0.004000] console [tty0] enabled
[    0.004000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.004000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.004000] allocated 10310080 bytes of page_cgroup
[    0.004000] please try cgroup_disable=memory option if you don't want
[    0.004000] Scanning for low memory corruption every 60 seconds
[    0.004000] Memory: 2018544k/2062016k available (4115k kernel code, 42204k reserved, 2199k data, 532k init, 1156808k highmem)
[    0.004000] virtual kernel memory layout:
[    0.004000]     fixmap  : 0xffc77000 - 0xfffff000   (3616 kB)
[    0.004000]     pkmap   : 0xff400000 - 0xff800000   (4096 kB)
[    0.004000]     vmalloc : 0xf7bfe000 - 0xff3fe000   ( 120 MB)
[    0.004000]     lowmem  : 0xc0000000 - 0xf73fe000   ( 883 MB)
[    0.004000]       .init : 0xc0733000 - 0xc07b8000   ( 532 kB)
[    0.004000]       .data : 0xc0504f5f - 0xc072ae60   (2199 kB)
[    0.004000]       .text : 0xc0100000 - 0xc0504f5f   (4115 kB)
[    0.004000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.004000] SLUB: Genslabs=12, HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
[    0.004000] hpet clockevent registered
[    0.004000] HPET: 4 timers in total, 0 timers will be used for per-cpu timer
[    0.004000] Calibrating delay loop (skipped), value calculated using timer frequency.. 3990.02 BogoMIPS (lpj=7980044)
[    0.004000] Security Framework initialized
[    0.004000] SELinux:  Disabled at boot.
[    0.004000] AppArmor: AppArmor initialized
[    0.004000] Mount-cache hash table entries: 512
[    0.004000] Initializing cgroup subsys ns
[    0.004000] Initializing cgroup subsys cpuacct
[    0.004000] Initializing cgroup subsys memory
[    0.004000] Initializing cgroup subsys freezer
[    0.004000] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.004000] CPU: L2 cache: 2048K
[    0.004000] CPU: Physical Processor ID: 0
[    0.004000] CPU: Processor Core ID: 0
[    0.004000] using mwait in idle threads.
[    0.004000] Checking 'hlt' instruction... OK.
[    0.019731] ACPI: Core revision 20080926
[    0.025064] ACPI: Checking initramfs for custom DSDT
[    0.528457] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.569197] CPU0: Intel(R) Core(TM)2 Duo CPU     T5870  @ 2.00GHz stepping 0d
[    0.572002] Booting processor 1 APIC 0x1 ip 0x6000
[    0.004000] Initializing CPU#1
[    0.004000] Calibrating delay using timer specific routine.. 3990.00 BogoMIPS (lpj=7980012)
[    0.004000] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.004000] CPU: L2 cache: 2048K
[    0.004000] CPU: Physical Processor ID: 0
[    0.004000] CPU: Processor Core ID: 1
[    0.656687] CPU1: Intel(R) Core(TM)2 Duo CPU     T5870  @ 2.00GHz stepping 0d
[    0.656709] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[    0.660043] Brought up 2 CPUs
[    0.660047] Total of 2 processors activated (7980.02 BogoMIPS).
[    0.660108] CPU0 attaching sched-domain:
[    0.660112]  domain 0: span 0-1 level MC
[    0.660117]   groups: 0 1
[    0.660127] CPU1 attaching sched-domain:
[    0.660130]  domain 0: span 0-1 level MC
[    0.660134]   groups: 1 0
[    0.660231] net_namespace: 776 bytes
[    0.660232] Booting paravirtualized kernel on bare hardware
[    0.660496] Time: 14:07:27  Date: 09/16/09
[    0.660496] regulator: core version 0.5
[    0.660496] NET: Registered protocol family 16
[    0.660496] EISA bus registered
[    0.660496] ACPI FADT declares the system doesn't support PCIe ASPM, so disable it
[    0.660496] ACPI: bus type pci registered
[    0.660496] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
[    0.660496] PCI: Not using MMCONFIG.
[    0.660566] PCI: PCI BIOS revision 3.00 entry at 0xf0031, last bus=13
[    0.660570] PCI: Using configuration type 1 for base access
[    0.666549] ACPI: EC: EC description table is found, configuring boot EC
[    0.668026] ACPI: EC: non-query interrupt received, switching to interrupt mode
[    0.694949] ACPI: Interpreter enabled
[    0.694962] ACPI: (supports S0 S1 S3 S4 S5)
[    0.695001] ACPI: Using IOAPIC for interrupt routing
[    0.695199] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
[    0.701896] PCI: MCFG area at e0000000 reserved in ACPI motherboard resources
[    0.701900] PCI: Using MMCONFIG for extended config space
[    0.721083] ACPI: EC: GPE = 0x1b, I/O: command/status = 0x66, data = 0x62
[    0.721087] ACPI: EC: driver started in interrupt mode
[    0.721549] ACPI: No dock devices found.
[    0.721717] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.721850] pci 0000:00:02.0: reg 10 64bit mmio: [0xfd400000-0xfd7fffff]
[    0.721863] pci 0000:00:02.0: reg 18 64bit mmio: [0xd0000000-0xdfffffff]
[    0.721871] pci 0000:00:02.0: reg 20 io port: [0x5c00-0x5c07]
[    0.721923] pci 0000:00:02.1: reg 10 64bit mmio: [0xfd300000-0xfd3fffff]
[    0.722070] pci 0000:00:1a.0: reg 20 io port: [0x5880-0x589f]
[    0.722170] pci 0000:00:1a.1: reg 20 io port: [0x5800-0x581f]
[    0.722269] pci 0000:00:1a.2: reg 20 io port: [0x5480-0x549f]
[    0.722373] pci 0000:00:1a.7: reg 10 32bit mmio: [0xfd8fbc00-0xfd8fbfff]
[    0.722433] pci 0000:00:1a.7: PME# supported from D0 D3hot D3cold
[    0.722440] pci 0000:00:1a.7: PME# disabled
[    0.722509] pci 0000:00:1b.0: reg 10 64bit mmio: [0xfd8f4000-0xfd8f7fff]
[    0.722555] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.722562] pci 0000:00:1b.0: PME# disabled
[    0.722636] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.722643] pci 0000:00:1c.0: PME# disabled
[    0.722721] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
[    0.722728] pci 0000:00:1c.1: PME# disabled
[    0.722806] pci 0000:00:1c.2: PME# supported from D0 D3hot D3cold
[    0.722812] pci 0000:00:1c.2: PME# disabled
[    0.722891] pci 0000:00:1c.3: PME# supported from D0 D3hot D3cold
[    0.722897] pci 0000:00:1c.3: PME# disabled
[    0.722988] pci 0000:00:1d.0: reg 20 io port: [0x5400-0x541f]
[    0.723088] pci 0000:00:1d.1: reg 20 io port: [0x5080-0x509f]
[    0.723188] pci 0000:00:1d.2: reg 20 io port: [0x5000-0x501f]
[    0.723294] pci 0000:00:1d.7: reg 10 32bit mmio: [0xfd8fb800-0xfd8fbbff]
[    0.723353] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.723360] pci 0000:00:1d.7: PME# disabled
[    0.723615] pci 0000:00:1f.2: reg 10 io port: [0x4c00-0x4c07]
[    0.723625] pci 0000:00:1f.2: reg 14 io port: [0x4880-0x4883]
[    0.723635] pci 0000:00:1f.2: reg 18 io port: [0x4800-0x4807]
[    0.723645] pci 0000:00:1f.2: reg 1c io port: [0x4480-0x4483]
[    0.723655] pci 0000:00:1f.2: reg 20 io port: [0x4400-0x441f]
[    0.723665] pci 0000:00:1f.2: reg 24 32bit mmio: [0xfd8fb000-0xfd8fb7ff]
[    0.723689] pci 0000:00:1f.2: PME# supported from D3hot
[    0.723695] pci 0000:00:1f.2: PME# disabled
[    0.723869] pci 0000:02:00.0: reg 10 64bit mmio: [0xfd9f0000-0xfd9fffff]
[    0.723930] pci 0000:02:00.0: supports D1 D2
[    0.723933] pci 0000:02:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.723940] pci 0000:02:00.0: PME# disabled
[    0.724035] pci 0000:00:1c.1: bridge 32bit mmio: [0xfd900000-0xfd9fffff]
[    0.724110] pci 0000:00:1c.2: bridge io port: [0x6000-0xdfff]
[    0.724117] pci 0000:00:1c.2: bridge 32bit mmio: [0xfda00000-0xfe9fffff]
[    0.724128] pci 0000:00:1c.2: bridge 64bit mmio pref: [0xfc700000-0xfcefffff]
[    0.724195] pci 0000:0c:00.0: reg 10 io port: [0xe800-0xe8ff]
[    0.724225] pci 0000:0c:00.0: reg 18 64bit mmio: [0xfcfff000-0xfcffffff]
[    0.724246] pci 0000:0c:00.0: reg 20 64bit mmio: [0xfcfe0000-0xfcfeffff]
[    0.724259] pci 0000:0c:00.0: reg 30 32bit mmio: [0xfeaf0000-0xfeafffff]
[    0.724276] pci 0000:0c:00.0: supports D1 D2
[    0.724279] pci 0000:0c:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.724287] pci 0000:0c:00.0: PME# disabled
[    0.724375] pci 0000:00:1c.3: bridge io port: [0xe000-0xefff]
[    0.724381] pci 0000:00:1c.3: bridge 32bit mmio: [0xfea00000-0xfeafffff]
[    0.724392] pci 0000:00:1c.3: bridge 64bit mmio pref: [0xfcf00000-0xfcffffff]
[    0.724448] pci 0000:0d:00.0: reg 10 32bit mmio: [0xfebff800-0xfebfffff]
[    0.724511] pci 0000:0d:00.0: PME# supported from D0 D3hot D3cold
[    0.724518] pci 0000:0d:00.0: PME# disabled
[    0.724573] pci 0000:0d:00.1: reg 10 32bit mmio: [0xfebff400-0xfebff4ff]
[    0.724636] pci 0000:0d:00.1: supports D1 D2
[    0.724639] pci 0000:0d:00.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.724646] pci 0000:0d:00.1: PME# disabled
[    0.724701] pci 0000:0d:00.2: reg 10 32bit mmio: [0xfebff000-0xfebff0ff]
[    0.724764] pci 0000:0d:00.2: supports D1 D2
[    0.724767] pci 0000:0d:00.2: PME# supported from D0 D1 D2 D3hot D3cold
[    0.724774] pci 0000:0d:00.2: PME# disabled
[    0.724829] pci 0000:0d:00.3: reg 10 32bit mmio: [0xfebfec00-0xfebfecff]
[    0.724892] pci 0000:0d:00.3: supports D1 D2
[    0.724895] pci 0000:0d:00.3: PME# supported from D0 D1 D2 D3hot D3cold
[    0.724902] pci 0000:0d:00.3: PME# disabled
[    0.724957] pci 0000:0d:00.4: reg 10 32bit mmio: [0xfebfe800-0xfebfe8ff]
[    0.725020] pci 0000:0d:00.4: supports D1 D2
[    0.725023] pci 0000:0d:00.4: PME# supported from D0 D1 D2 D3hot D3cold
[    0.725031] pci 0000:0d:00.4: PME# disabled
[    0.725114] pci 0000:00:1e.0: transparent bridge
[    0.725124] pci 0000:00:1e.0: bridge 32bit mmio: [0xfeb00000-0xfebfffff]
[    0.725169] bus 00 -> node 0
[    0.725183] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.725802] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P3._PRT]
[    0.726029] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P4._PRT]
[    0.726275] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P6._PRT]
[    0.726495] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P8._PRT]
[    0.773971] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 *10 11 12)
[    0.774288] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 *5 10 12)
[    0.774598] ACPI: PCI Interrupt Link [LNKC] (IRQs *6)
[    0.774904] ACPI: PCI Interrupt Link [LNKD] (IRQs *3 4 5 7 10 12)
[    0.775216] ACPI: PCI Interrupt Link [LNKE] (IRQs 6) *0, disabled.
[    0.775523] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 *7 10 12)
[    0.775834] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 *4 5 6 7 10 12)
[    0.776154] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 *10 12)
[    0.780928] ACPI Warning (tbutils-0217): Incorrect checksum in table [ATKG] - D8, should be 73 [20080926]
[    0.780979] ACPI: WMI: Mapper loaded
[    0.781048] SCSI subsystem initialized
[    0.781048] libata version 3.00 loaded.
[    0.781048] usbcore: registered new interface driver usbfs
[    0.781048] usbcore: registered new interface driver hub
[    0.781048] usbcore: registered new device driver usb
[    0.781048] PCI: Using ACPI for IRQ routing
[    0.788014] Bluetooth: Core ver 2.13
[    0.788035] NET: Registered protocol family 31
[    0.788035] Bluetooth: HCI device and connection manager initialized
[    0.788035] Bluetooth: HCI socket layer initialized
[    0.788035] NET: Registered protocol family 8
[    0.788035] NET: Registered protocol family 20
[    0.788052] NetLabel: Initializing
[    0.788055] NetLabel:  domain hash size = 128
[    0.788058] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.788077] NetLabel:  unlabeled traffic allowed by default
[    0.788097] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0
[    0.788106] hpet0: 4 comparators, 64-bit 14.318180 MHz counter
[    0.792088] AppArmor: AppArmor Filesystem Enabled
[    0.796012] Switched to high resolution mode on CPU 0
[    0.796753] Switched to high resolution mode on CPU 1
[    0.800016] pnp: PnP ACPI init
[    0.800028] ACPI: bus type pnp registered
[    0.802715] pnp 00:0c: mem resource (0xfd3f8000-0xfd3fafff) overlaps 0000:00:02.1 BAR 0 (0xfd300000-0xfd3fffff), disabling
[    0.805050] pnp: PnP ACPI: found 15 devices
[    0.805054] ACPI: ACPI bus type pnp unregistered
[    0.805060] PnPBIOS: Disabled by ACPI PNP
[    0.805074] system 00:01: iomem range 0xfed10000-0xfed19fff has been reserved
[    0.805089] system 00:08: ioport range 0x4d0-0x4d1 has been reserved
[    0.805094] system 00:08: ioport range 0x800-0x87f has been reserved
[    0.805098] system 00:08: ioport range 0x400-0x41f has been reserved
[    0.805102] system 00:08: ioport range 0x480-0x4bf has been reserved
[    0.805107] system 00:08: iomem range 0xfed1c000-0xfed1ffff has been reserved
[    0.805111] system 00:08: iomem range 0xfed20000-0xfed3ffff has been reserved
[    0.805116] system 00:08: iomem range 0xfed45000-0xfed89fff has been reserved
[    0.805121] system 00:08: iomem range 0xfed90000-0xfed90fff has been reserved
[    0.805125] system 00:08: iomem range 0xfed91000-0xfed91fff has been reserved
[    0.805130] system 00:08: iomem range 0xfed92000-0xfed92fff has been reserved
[    0.805134] system 00:08: iomem range 0xfed93000-0xfed93fff has been reserved
[    0.805139] system 00:08: iomem range 0xffb00000-0xffbfffff has been reserved
[    0.805144] system 00:08: iomem range 0xfff00000-0xffffffff has been reserved
[    0.805154] system 00:0a: iomem range 0xffa00000-0xffbfffff could not be reserved
[    0.805159] system 00:0a: iomem range 0xffe00000-0xffffffff could not be reserved
[    0.805168] system 00:0b: iomem range 0xffc00000-0xffdfffff has been reserved
[    0.805177] system 00:0c: ioport range 0x250-0x253 has been reserved
[    0.805181] system 00:0c: ioport range 0x256-0x25f has been reserved
[    0.805186] system 00:0c: ioport range 0x702-0x703 has been reserved
[    0.805190] system 00:0c: ioport range 0x4c0-0x4cf has been reserved
[    0.805194] system 00:0c: ioport range 0x4d2-0x4df has been reserved
[    0.805198] system 00:0c: ioport range 0x4e0-0x4ef has been reserved
[    0.805202] system 00:0c: ioport range 0x4f0-0x4ff has been reserved
[    0.805207] system 00:0c: iomem range 0xfec00000-0xfec00fff has been reserved
[    0.805211] system 00:0c: iomem range 0xfee00000-0xfee00fff has been reserved
[    0.805215] system 00:0c: iomem range 0xf9efc000-0xf9efefff has been reserved
[    0.805220] system 00:0c: iomem range 0xfd8f8000-0xfd8fafff has been reserved
[    0.805229] system 00:0d: iomem range 0xe0000000-0xefffffff has been reserved
[    0.805239] system 00:0e: iomem range 0x0-0x9ffff could not be reserved
[    0.805243] system 00:0e: iomem range 0xc0000-0xcffff could not be reserved
[    0.805248] system 00:0e: iomem range 0xe0000-0xfffff could not be reserved
[    0.805252] system 00:0e: iomem range 0x100000-0x7ddfffff could not be reserved
[    0.840074] pci 0000:00:1c.0: PCI bridge, secondary bus 0000:01
[    0.840078] pci 0000:00:1c.0:   IO window: disabled
[    0.840085] pci 0000:00:1c.0:   MEM window: disabled
[    0.840092] pci 0000:00:1c.0:   PREFETCH window: disabled
[    0.840101] pci 0000:00:1c.1: PCI bridge, secondary bus 0000:02
[    0.840105] pci 0000:00:1c.1:   IO window: disabled
[    0.840113] pci 0000:00:1c.1:   MEM window: 0xfd900000-0xfd9fffff
[    0.840119] pci 0000:00:1c.1:   PREFETCH window: disabled
[    0.840129] pci 0000:00:1c.2: PCI bridge, secondary bus 0000:03
[    0.840134] pci 0000:00:1c.2:   IO window: 0x6000-0xdfff
[    0.840142] pci 0000:00:1c.2:   MEM window: 0xfda00000-0xfe9fffff
[    0.840149] pci 0000:00:1c.2:   PREFETCH window: 0x000000fc700000-0x000000fcefffff
[    0.840160] pci 0000:00:1c.3: PCI bridge, secondary bus 0000:0c
[    0.840165] pci 0000:00:1c.3:   IO window: 0xe000-0xefff
[    0.840173] pci 0000:00:1c.3:   MEM window: 0xfea00000-0xfeafffff
[    0.840180] pci 0000:00:1c.3:   PREFETCH window: 0x000000fcf00000-0x000000fcffffff
[    0.840190] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:0d
[    0.840194] pci 0000:00:1e.0:   IO window: disabled
[    0.840202] pci 0000:00:1e.0:   MEM window: 0xfeb00000-0xfebfffff
[    0.840208] pci 0000:00:1e.0:   PREFETCH window: disabled
[    0.840230] pci 0000:00:1c.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.840237] pci 0000:00:1c.0: setting latency timer to 64
[    0.840250] pci 0000:00:1c.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.840257] pci 0000:00:1c.1: setting latency timer to 64
[    0.840269] pci 0000:00:1c.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.840276] pci 0000:00:1c.2: setting latency timer to 64
[    0.840288] pci 0000:00:1c.3: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    0.840295] pci 0000:00:1c.3: setting latency timer to 64
[    0.840305] pci 0000:00:1e.0: setting latency timer to 64
[    0.840311] bus: 00 index 0 io port: [0x00-0xffff]
[    0.840315] bus: 00 index 1 mmio: [0x000000-0xffffffff]
[    0.840319] bus: 01 index 0 mmio: [0x0-0x0]
[    0.840322] bus: 01 index 1 mmio: [0x0-0x0]
[    0.840325] bus: 01 index 2 mmio: [0x0-0x0]
[    0.840328] bus: 01 index 3 mmio: [0x0-0x0]
[    0.840331] bus: 02 index 0 mmio: [0x0-0x0]
[    0.840334] bus: 02 index 1 mmio: [0xfd900000-0xfd9fffff]
[    0.840337] bus: 02 index 2 mmio: [0x0-0x0]
[    0.840340] bus: 02 index 3 mmio: [0x0-0x0]
[    0.840343] bus: 03 index 0 io port: [0x6000-0xdfff]
[    0.840347] bus: 03 index 1 mmio: [0xfda00000-0xfe9fffff]
[    0.840350] bus: 03 index 2 mmio: [0xfc700000-0xfcefffff]
[    0.840354] bus: 03 index 3 mmio: [0x0-0x0]
[    0.840357] bus: 0c index 0 io port: [0xe000-0xefff]
[    0.840360] bus: 0c index 1 mmio: [0xfea00000-0xfeafffff]
[    0.840364] bus: 0c index 2 mmio: [0xfcf00000-0xfcffffff]
[    0.840367] bus: 0c index 3 mmio: [0x0-0x0]
[    0.840370] bus: 0d index 0 mmio: [0x0-0x0]
[    0.840374] bus: 0d index 1 mmio: [0xfeb00000-0xfebfffff]
[    0.840377] bus: 0d index 2 mmio: [0x0-0x0]
[    0.840380] bus: 0d index 3 io port: [0x00-0xffff]
[    0.840383] bus: 0d index 4 mmio: [0x000000-0xffffffff]
[    0.840395] NET: Registered protocol family 2
[    0.852079] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.852438] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.852852] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.853071] TCP: Hash tables configured (established 131072 bind 65536)
[    0.853075] TCP reno registered
[    0.860100] NET: Registered protocol family 1
[    0.860269] checking if image is initramfs... it is
[    1.861193] Freeing initrd memory: 7377k freed
[    1.861238] Simple Boot Flag at 0x51 set to 0x1
[    1.861471] cpufreq: No nForce2 chipset.
[    1.861662] audit: initializing netlink socket (disabled)
[    1.861691] type=2000 audit(1253110047.860:1): initialized
[    1.873387] highmem bounce pool size: 64 pages
[    1.873395] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    1.875509] VFS: Disk quotas dquot_6.5.1
[    1.875601] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    1.876559] fuse init (API version 7.10)
[    1.876688] msgmni has been set to 1698
[    1.876939] alg: No test for stdrng (krng)
[    1.876955] io scheduler noop registered
[    1.876958] io scheduler anticipatory registered
[    1.876962] io scheduler deadline registered
[    1.876982] io scheduler cfq registered (default)
[    1.876997] pci 0000:00:02.0: Boot video device
[    1.882752] pcieport-driver 0000:00:1c.0: setting latency timer to 64
[    1.882807] pcieport-driver 0000:00:1c.0: found MSI capability
[    1.882851] pcieport-driver 0000:00:1c.0: irq 2303 for MSI/MSI-X
[    1.882870] pci_express 0000:00:1c.0:pcie00: allocate port service
[    1.882892] pci_express 0000:00:1c.0:pcie03: allocate port service
[    1.882981] pcieport-driver 0000:00:1c.1: setting latency timer to 64
[    1.883035] pcieport-driver 0000:00:1c.1: found MSI capability
[    1.883073] pcieport-driver 0000:00:1c.1: irq 2302 for MSI/MSI-X
[    1.883091] pci_express 0000:00:1c.1:pcie00: allocate port service
[    1.883111] pci_express 0000:00:1c.1:pcie03: allocate port service
[    1.883199] pcieport-driver 0000:00:1c.2: setting latency timer to 64
[    1.883254] pcieport-driver 0000:00:1c.2: found MSI capability
[    1.883292] pcieport-driver 0000:00:1c.2: irq 2301 for MSI/MSI-X
[    1.883311] pci_express 0000:00:1c.2:pcie00: allocate port service
[    1.883330] pci_express 0000:00:1c.2:pcie02: allocate port service
[    1.883349] pci_express 0000:00:1c.2:pcie03: allocate port service
[    1.883441] pcieport-driver 0000:00:1c.3: setting latency timer to 64
[    1.883494] pcieport-driver 0000:00:1c.3: found MSI capability
[    1.883532] pcieport-driver 0000:00:1c.3: irq 2300 for MSI/MSI-X
[    1.883550] pci_express 0000:00:1c.3:pcie00: allocate port service
[    1.883570] pci_express 0000:00:1c.3:pcie03: allocate port service
[    1.883674] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    1.884397] pciehp 0000:00:1c.2:pcie02: HPC vendor_id 8086 device_id 2944 ss_vid 0 ss_did 0
[    1.884454] pciehp 0000:00:1c.2:pcie02: service driver pciehp loaded
[    1.884468] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    1.884775] ACPI: AC Adapter [AC0] (off-line)
[    1.989018] ACPI: Battery Slot [BAT0] (battery present)
[    1.989122] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
[    1.989127] ACPI: Power Button (FF) [PWRF]
[    1.989257] input: Sleep Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input1
[    1.989268] ACPI: Sleep Button (CM) [SLPB]
[    1.989389] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input2
[    1.994477] ACPI: Lid Switch [LID]
[    1.995612] ACPI Warning (tbutils-0217): Incorrect checksum in table [SSDT] - E4, should be 73 [20080926]
[    1.995622] ACPI: SSDT 7DDC87F0, 0286 (r1  PmRef TP-6A         180 INTL 20051117)
[    1.996565] ACPI: SSDT 7DDC8B10, 0765 (r1  PmRef  Cpu0Cst     3001 INTL 20051117)
[    1.998087] Monitor-Mwait will be used to enter C-1 state
[    1.998092] Monitor-Mwait will be used to enter C-2 state
[    1.998097] Monitor-Mwait will be used to enter C-3 state
[    1.998118] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[    1.998155] processor ACPI_CPU:00: registered as cooling_device0
[    1.998161] ACPI: Processor [P001] (supports 8 throttling states)
[    1.998700] ACPI Warning (tbutils-0217): Incorrect checksum in table [SSDT] - 37, should be C7 [20080926]
[    1.998709] ACPI: SSDT 7DDC8720, 00C8 (r1  PmRef TP-6A         180 INTL 20051117)
[    1.999624] ACPI: SSDT 7DDC8A80, 0085 (r1  PmRef  Cpu1Cst     3000 INTL 20051117)
[    2.001306] ACPI: CPU1 (power states: C1[C1] C2[C2] C3[C3])
[    2.001337] processor ACPI_CPU:01: registered as cooling_device1
[    2.001343] ACPI: Processor [P002] (supports 8 throttling states)
[    2.015624] ACPI Warning (nspredef-0858): \_TZ_.THRM._PSL: Return Package type mismatch at index 0 - found Processor, expected Reference [20080926]
[    2.015636] ACPI: Expecting a [Reference] package element, found type C
[    2.015840] thermal LNXTHERM:01: registered as thermal_zone0
[    2.018575] ACPI: Thermal Zone [THRM] (39 C)
[    2.018666] isapnp: Scanning for PnP cards...
[    2.372693] isapnp: No Plug & Play device found
[    2.381347] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    2.383070] brd: module loaded
[    2.383546] loop: module loaded
[    2.383646] Fixed MDIO Bus: probed
[    2.383653] PPP generic driver version 2.4.2
[    2.383738] input: Macintosh mouse button emulation as /devices/virtual/input/input3
[    2.383782] Driver 'sd' needs updating - please use bus_type methods
[    2.383797] Driver 'sr' needs updating - please use bus_type methods
[    2.383861] ahci 0000:00:1f.2: version 3.0
[    2.383875] ahci 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    2.383925] ahci 0000:00:1f.2: irq 2299 for MSI/MSI-X
[    2.384024] ahci 0000:00:1f.2: AHCI 0001.0200 32 slots 4 ports 3 Gbps 0x33 impl SATA mode
[    2.384029] ahci 0000:00:1f.2: flags: 64bit ncq sntf stag pm led clo pio slum part ems 
[    2.384037] ahci 0000:00:1f.2: setting latency timer to 64
[    2.384372] scsi0 : ahci
[    2.384511] scsi1 : ahci
[    2.384599] scsi2 : ahci
[    2.384697] scsi3 : ahci
[    2.384783] scsi4 : ahci
[    2.384869] scsi5 : ahci
[    2.385291] ata1: SATA max UDMA/133 abar m2048@0xfd8fb000 port 0xfd8fb100 irq 2299
[    2.385296] ata2: SATA max UDMA/133 abar m2048@0xfd8fb000 port 0xfd8fb180 irq 2299
[    2.385299] ata3: DUMMY
[    2.385302] ata4: DUMMY
[    2.385306] ata5: SATA max UDMA/133 abar m2048@0xfd8fb000 port 0xfd8fb300 irq 2299
[    2.385310] ata6: SATA max UDMA/133 abar m2048@0xfd8fb000 port 0xfd8fb380 irq 2299
[    2.704022] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    2.706067] ata1.00: ACPI cmd f5/00:00:00:00:00:a0 filtered out
[    2.706141] ata1.00: ACPI cmd ef/10:06:00:00:00:a0 succeeded
[    2.706146] ata1.00: ACPI cmd ef/10:03:00:00:00:a0 filtered out
[    2.748258] ata1.00: ATA-8: WDC WD2500BEVS-08VAT2, 14.01A14, max UDMA/133
[    2.748262] ata1.00: 488397168 sectors, multi 0: LBA48 NCQ (depth 31/32)
[    2.750987] ata1.00: ACPI cmd f5/00:00:00:00:00:a0 filtered out
[    2.751097] ata1.00: ACPI cmd ef/10:06:00:00:00:a0 succeeded
[    2.751102] ata1.00: ACPI cmd ef/10:03:00:00:00:a0 filtered out
[    2.753561] ata1.00: configured for UDMA/133
[    3.088021] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    3.091210] ata2.00: ACPI cmd ef/10:06:00:00:00:a0 succeeded
[    3.092861] ata2.00: ATAPI: HL-DT-STCD-RW/DVD DRIVE GCC-T20N, B.06, max UDMA/33
[    3.097196] ata2.00: ACPI cmd ef/10:06:00:00:00:a0 succeeded
[    3.098876] ata2.00: configured for UDMA/33
[    3.436020] ata5: SATA link down (SStatus 0 SControl 300)
[    3.772019] ata6: SATA link down (SStatus 0 SControl 300)
[    3.788152] scsi 0:0:0:0: Direct-Access     ATA      WDC WD2500BEVS-0 14.0 PQ: 0 ANSI: 5
[    3.788294] sd 0:0:0:0: [sda] 488397168 512-byte hardware sectors: (250 GB/232 GiB)
[    3.788320] sd 0:0:0:0: [sda] Write Protect is off
[    3.788324] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    3.788364] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    3.788454] sd 0:0:0:0: [sda] 488397168 512-byte hardware sectors: (250 GB/232 GiB)
[    3.788478] sd 0:0:0:0: [sda] Write Protect is off
[    3.788482] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    3.788522] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    3.788527]  sda: sda1 sda2 sda3
[    3.843054] sd 0:0:0:0: [sda] Attached SCSI disk
[    3.843117] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    3.847880] scsi 1:0:0:0: CD-ROM            HL-DT-ST RW/DVD GCC-T20N  B.06 PQ: 0 ANSI: 5
[    3.859925] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
[    3.859929] Uniform CD-ROM driver Revision: 3.20
[    3.860067] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    3.860122] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    3.861280] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    3.861307] ehci_hcd 0000:00:1a.7: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    3.861328] ehci_hcd 0000:00:1a.7: setting latency timer to 64
[    3.861333] ehci_hcd 0000:00:1a.7: EHCI Host Controller
[    3.861417] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 1
[    3.865343] ehci_hcd 0000:00:1a.7: debug port 1
[    3.865353] ehci_hcd 0000:00:1a.7: cache line size of 32 is not supported
[    3.865371] ehci_hcd 0000:00:1a.7: irq 18, io mem 0xfd8fbc00
[    3.880014] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00
[    3.880106] usb usb1: configuration #1 chosen from 1 choice
[    3.880147] hub 1-0:1.0: USB hub found
[    3.880161] hub 1-0:1.0: 6 ports detected
[    3.880328] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    3.880345] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    3.880350] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    3.880414] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 2
[    3.884320] ehci_hcd 0000:00:1d.7: debug port 1
[    3.884330] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    3.884347] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xfd8fb800
[    3.896013] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    3.896096] usb usb2: configuration #1 chosen from 1 choice
[    3.896140] hub 2-0:1.0: USB hub found
[    3.896149] hub 2-0:1.0: 6 ports detected
[    3.896297] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    3.896324] uhci_hcd: USB Universal Host Controller Interface driver
[    3.896354] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    3.896363] uhci_hcd 0000:00:1a.0: setting latency timer to 64
[    3.896368] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[    3.896432] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 3
[    3.896471] uhci_hcd 0000:00:1a.0: irq 16, io base 0x00005880
[    3.896580] usb usb3: configuration #1 chosen from 1 choice
[    3.896619] hub 3-0:1.0: USB hub found
[    3.896628] hub 3-0:1.0: 2 ports detected
[    3.896764] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    3.896774] uhci_hcd 0000:00:1a.1: setting latency timer to 64
[    3.896779] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[    3.896845] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 4
[    3.896883] uhci_hcd 0000:00:1a.1: irq 21, io base 0x00005800
[    3.896986] usb usb4: configuration #1 chosen from 1 choice
[    3.897033] hub 4-0:1.0: USB hub found
[    3.897043] hub 4-0:1.0: 2 ports detected
[    3.897166] uhci_hcd 0000:00:1a.2: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    3.897175] uhci_hcd 0000:00:1a.2: setting latency timer to 64
[    3.897180] uhci_hcd 0000:00:1a.2: UHCI Host Controller
[    3.897242] uhci_hcd 0000:00:1a.2: new USB bus registered, assigned bus number 5
[    3.897280] uhci_hcd 0000:00:1a.2: irq 19, io base 0x00005480
[    3.897388] usb usb5: configuration #1 chosen from 1 choice
[    3.897426] hub 5-0:1.0: USB hub found
[    3.897435] hub 5-0:1.0: 2 ports detected
[    3.897558] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    3.897569] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    3.897574] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    3.897639] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 6
[    3.897668] uhci_hcd 0000:00:1d.0: irq 23, io base 0x00005400
[    3.897772] usb usb6: configuration #1 chosen from 1 choice
[    3.897810] hub 6-0:1.0: USB hub found
[    3.897819] hub 6-0:1.0: 2 ports detected
[    3.897947] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    3.897956] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    3.897961] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    3.898029] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 7
[    3.898058] uhci_hcd 0000:00:1d.1: irq 19, io base 0x00005080
[    3.898161] usb usb7: configuration #1 chosen from 1 choice
[    3.898200] hub 7-0:1.0: USB hub found
[    3.898209] hub 7-0:1.0: 2 ports detected
[    3.898334] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    3.898345] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    3.898349] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    3.898412] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 8
[    3.898440] uhci_hcd 0000:00:1d.2: irq 18, io base 0x00005000
[    3.898551] usb usb8: configuration #1 chosen from 1 choice
[    3.898590] hub 8-0:1.0: USB hub found
[    3.898599] hub 8-0:1.0: 2 ports detected
[    3.898828] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
[    3.902522] i8042.c: Detected active multiplexing controller, rev 1.1.
[    3.904697] serio: i8042 KBD port at 0x60,0x64 irq 1
[    3.904705] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[    3.904709] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[    3.904713] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[    3.904717] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[    3.908059] mice: PS/2 mouse device common for all mice
[    3.924104] rtc_cmos 00:03: RTC can wake from S4
[    3.924155] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[    3.924187] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
[    3.924284] device-mapper: uevent: version 1.0.3
[    3.924411] device-mapper: ioctl: 4.14.0-ioctl (2008-04-23) initialised: dm-devel@redhat.com
[    3.924515] device-mapper: multipath: version 1.0.5 loaded
[    3.924519] device-mapper: multipath round-robin: version 1.0.0 loaded
[    3.924632] EISA: Probing bus 0 at eisa.0
[    3.924654] Cannot allocate resource for EISA slot 4
[    3.924657] Cannot allocate resource for EISA slot 5
[    3.924661] Cannot allocate resource for EISA slot 6
[    3.924665] Cannot allocate resource for EISA slot 7
[    3.924668] Cannot allocate resource for EISA slot 8
[    3.924671] EISA: Detected 0 cards.
[    3.924849] cpuidle: using governor ladder
[    3.925037] cpuidle: using governor menu
[    3.925834] TCP cubic registered
[    3.925995] NET: Registered protocol family 10
[    3.926655] lo: Disabled Privacy Extensions
[    3.927191] NET: Registered protocol family 17
[    3.927215] Bluetooth: L2CAP ver 2.11
[    3.927218] Bluetooth: L2CAP socket layer initialized
[    3.927222] Bluetooth: SCO (Voice Link) ver 0.6
[    3.927225] Bluetooth: SCO socket layer initialized
[    3.927268] Bluetooth: RFCOMM socket layer initialized
[    3.927278] Bluetooth: RFCOMM TTY layer initialized
[    3.927281] Bluetooth: RFCOMM ver 1.10
[    3.927321] Marking TSC unstable due to TSC halts in idle
[    3.928431] Using IPI No-Shortcut mode
[    3.928493] registered taskstats version 1
[    3.928612]   Magic number: 9:768:131
[    3.928646] acpi device:06: hash matches
[    3.928649] acpi PNP0C02:03: hash matches
[    3.928702] rtc_cmos 00:03: setting system clock to 2009-09-16 14:07:30 UTC (1253110050)
[    3.928705] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    3.928706] EDD information not available.
[    3.928966] Freeing unused kernel memory: 532k freed
[    3.929132] Write protecting the kernel text: 4116k
[    3.929194] Write protecting the kernel read-only data: 1528k
[    3.962221] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
[    4.209229] usb 2-5: new high speed USB device using ehci_hcd and address 2
[    4.224263] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    4.224287] r8169 0000:0c:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    4.224311] r8169 0000:0c:00.0: setting latency timer to 64
[    4.224482] r8169 0000:0c:00.0: irq 2298 for MSI/MSI-X
[    4.225185] eth0: RTL8168c/8111c at 0xf7c92000, 00:26:18:1b:d7:58, XID 3c4000c0 IRQ 2298
[    4.271188] ohci1394 0000:0d:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    4.323914] ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[16]  MMIO=[febff800-febfffff]  Max Packet=[2048]  IR/IT contexts=[4/4]
[    4.384460] usb 2-5: configuration #1 chosen from 1 choice
[    4.662984] PM: Starting manual resume from disk
[    4.662987] PM: Resume from partition 8:2
[    4.662989] PM: Checking hibernation image.
[    4.663204] PM: Resume from disk failed.
[    4.675063] EXT4-fs: barriers enabled
[    4.694151] kjournald2 starting.  Commit interval 5 seconds
[    4.694190] EXT4-fs: delayed allocation enabled
[    4.694195] EXT4-fs: file extents enabled
[    4.695090] EXT4-fs: mballoc enabled
[    4.695093] EXT4-fs: mounted filesystem with ordered data mode.
[    5.632190] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[001e8c0001e9c016]
[    8.172925] udev: starting version 141
[    8.421091] cfg80211: Calling CRDA to update world regulatory domain
[    8.539633] Linux agpgart interface v0.103
[    8.636956] iTCO_vendor_support: vendor-support=0
[    8.638388] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.05
[    8.638653] iTCO_wdt: failed to reset NO_REBOOT flag, reboot disabled by hardware
[    8.638665] iTCO_wdt: No card detected
[    8.652256] Non-volatile memory driver v1.2
[    8.666186] Linux video capture interface: v2.00
[    8.676625] acpi device:1e: registered as cooling_device2
[    8.676857] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:1b/input/input5
[    8.681123] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[    8.684737] agpgart-intel 0000:00:00.0: Intel Mobile Intel® GM45 Express Chipset
[    8.685364] agpgart-intel 0000:00:00.0: detected 32764K stolen memory
[    8.688874] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xd0000000
[    8.709448] cfg80211: World regulatory domain updated:
[    8.709452]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[    8.709454]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    8.709456]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[    8.709458]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[    8.709460]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    8.709462]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    8.752710] input: PC Speaker as /devices/platform/pcspkr/input/input6
[    8.764607] sdhci: Secure Digital Host Controller Interface driver
[    8.764609] sdhci: Copyright(c) Pierre Ossman
[    8.765149] ricoh-mmc: Ricoh MMC Controller disabling driver
[    8.765152] ricoh-mmc: Copyright(c) Philip Langdale
[    8.765187] ricoh-mmc: Ricoh MMC controller found at 0000:0d:00.2 [1180:0843] (rev 12)
[    8.765206] ricoh-mmc: Controller is now disabled.
[    8.788447] uvcvideo: Found UVC 1.00 device CNF7237&CNF7238 (17ef:4808)
[    8.790034] input: CNF7237&CNF7238 as /devices/pci0000:00/0000:00:1d.7/usb2/2-5/2-5:1.0/input/input7
[    8.790734] usbcore: registered new interface driver uvcvideo
[    8.790778] USB Video Class driver (v0.1.0)
[    8.889467] sdhci-pci 0000:0d:00.1: SDHCI controller found [1180:0822] (rev 22)
[    8.889484] sdhci-pci 0000:0d:00.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    8.890522] sdhci-pci 0000:0d:00.1: Will use DMA mode even though HW doesn't fully claim to support it.
[    8.892656] mmc0: SDHCI controller on PCI [0000:0d:00.1] using DMA
[    8.930116] thinkpad_acpi: Not yet supported ThinkPad detected!
[    8.982500] ath5k_pci 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    8.982513] ath5k_pci 0000:02:00.0: setting latency timer to 64
[    8.982569] ath5k_pci 0000:02:00.0: registered as 'phy0'
[    9.023505] phy0: Selected rate control algorithm 'pid'
[    9.131835] synaptics was reset on resume, see synaptics_resume_reset if you have trouble on resume
[    9.150540] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[    9.150599] HDA Intel 0000:00:1b.0: setting latency timer to 64
[    9.183409] ath5k phy0: Atheros AR2425 chip found (MAC: 0xe2, PHY: 0x70)
[    9.495779] lp: driver loaded but no devices found
[    9.562390] Adding 4883752k swap on /dev/sda2.  Priority:-1 extents:1 across:4883752k
[    9.578623] EXT4 FS on sda1, internal journal on sda1:8
[    9.839365] EXT4-fs: barriers enabled
[    9.861910] kjournald2 starting.  Commit interval 5 seconds
[    9.862344] EXT4 FS on sda3, internal journal on sda3:8
[    9.862348] EXT4-fs: delayed allocation enabled
[    9.862350] EXT4-fs: file extents enabled
[    9.881603] EXT4-fs: mballoc enabled
[    9.881606] EXT4-fs: mounted filesystem with ordered data mode.
[   10.028080] Synaptics Touchpad, model: 1, fw: 7.0, id: 0x1c0b1, caps: 0xd04791/0xb00000
[   10.028088] serio: Synaptics pass-through port at isa0060/serio4/input0
[   10.063601] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio4/input/input8
[   10.138654] type=1505 audit(1253110056.708:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=2084
[   10.180804] type=1505 audit(1253110056.748:3): operation="profile_load" name="/sbin/dhclient-script" name2="default" pid=2088
[   10.180891] type=1505 audit(1253110056.748:4): operation="profile_load" name="/sbin/dhclient3" name2="default" pid=2088
[   10.180927] type=1505 audit(1253110056.748:5): operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" name2="default" pid=2088
[   10.180959] type=1505 audit(1253110056.748:6): operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" name2="default" pid=2088
[   10.296887] type=1505 audit(1253110056.864:7): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=2093
[   10.297064] type=1505 audit(1253110056.868:8): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=2093
[   10.322073] type=1505 audit(1253110056.892:9): operation="profile_load" name="/usr/sbin/tcpdump" name2="default" pid=2097
[   11.332347] synaptics was reset on resume, see synaptics_resume_reset if you have trouble on resume
[   11.358906] input: Lenovo ThinkPad SL Series extra buttons as /devices/virtual/input/input9
[   11.386331] lenovo-sl-laptop: Started backlight brightness control
[   11.391379] Registered led device: lensl::lenovocare
[   11.391465] lenovo-sl-laptop: Loaded Lenovo ThinkPad SL Series driver
[   12.148661] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   12.148664] Bluetooth: BNEP filters: protocol multicast
[   12.182083] Bridge firewalling registered
[   12.501044] Clocksource tsc unstable (delta = -137124059 ns)
[   12.912757] psmouse serio5: ID: 10 00 64<6>ppdev: user-space parallel port driver
[   14.690484] [drm] Initialized drm 1.1.0 20060810
[   14.701013] pci 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   14.701018] pci 0000:00:02.0: setting latency timer to 64
[   14.701572] pci 0000:00:02.0: irq 2297 for MSI/MSI-X
[   14.702637] [drm] Initialized i915 1.6.0 20080730 on minor 0
[   14.703143] [drm:i915_setparam] *ERROR* unknown parameter 4
[   16.624640] IBM TrackPoint firmware: 0x0e, buttons: 3/3
[   16.855992] input: TPPS/2 IBM TrackPoint as /devices/platform/i8042/serio4/serio5/input/input10
[   17.429096] r8169: eth0: link down
[   17.429286] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   17.502323] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   19.449281] wlan0: authenticate with AP 00:0b:86:a9:ec:b0
[   19.450725] wlan0: authenticated
[   19.450728] wlan0: associate with AP 00:0b:86:a9:ec:b0
[   19.455294] wlan0: RX AssocResp from 00:0b:86:a9:ec:b0 (capab=0x421 status=0 aid=1)
[   19.455298] wlan0: associated
[   19.455604] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   19.455712] wlan0: disassociating by local choice (reason=3)
[   30.040048] wlan0: no IPv6 routers present
[   36.230929] ath5k phy0: unsupported jumbo
[   36.307490] wlan0: authenticate with AP 00:0b:86:a9:ec:b1
[   36.313980] wlan0: authenticated
[   36.313986] wlan0: associate with AP 00:0b:86:a9:ec:b1
[   36.360837] wlan0: RX AssocResp from 00:0b:86:a9:ec:b1 (capab=0x431 status=0 aid=5)
[   36.360841] wlan0: associated
[   73.432211] wlan0: authenticate with AP 00:0b:86:a9:ec:b1
[   73.433724] wlan0: authenticated
[   73.433728] wlan0: associate with AP 00:0b:86:a9:ec:b1
[   73.450006] wlan0: RX ReassocResp from 00:0b:86:a9:ec:b1 (capab=0x431 status=0 aid=5)
[   73.450009] wlan0: associated
[  829.090467] ath5k phy0: unsupported jumbo
[  829.388469] wlan0: authenticate with AP 00:0b:86:a9:ec:b1
[  829.436082] wlan0: authenticate with AP 00:0b:86:ab:1f:11
[  829.465187] wlan0: authenticate with AP 00:0b:86:ab:1f:11
[  829.467264] wlan0: authenticated
[  829.467274] wlan0: associate with AP 00:0b:86:ab:1f:11
[  829.471823] wlan0: RX ReassocResp from 00:0b:86:ab:1f:11 (capab=0x431 status=0 aid=1)
[  829.471831] wlan0: associated
[ 1191.313154] wlan0: authenticate with AP 00:0b:86:a9:ec:b1
[ 1191.315301] wlan0: authenticated
[ 1191.315306] wlan0: associate with AP 00:0b:86:a9:ec:b1
[ 1191.319261] wlan0: RX ReassocResp from 00:0b:86:a9:ec:b1 (capab=0x431 status=0 aid=2)
[ 1191.319263] wlan0: associated
[ 2622.954224] wlan0: disassociating by local choice (reason=3)
[ 2623.025493] wlan0: direct probe to AP 00:0b:86:a9:ec:b1 try 1
[ 2623.030852] wlan0 direct probe responded
[ 2623.030864] wlan0: authenticate with AP 00:0b:86:a9:ec:b1
[ 2623.223148] ACPI: BIOS _OSI(Linux) query ignored
[ 2623.223988] ACPI: BIOS _OSI(Linux) query ignored
[ 2624.688981] [drm:gm45_get_vblank_counter] *ERROR* trying to get vblank count for disabled pipe 0
[ 2625.071725] PM: Marking nosave pages: 0000000000002000 - 0000000000006000
[ 2625.071728] PM: Marking nosave pages: 0000000000007000 - 0000000000010000
[ 2625.071731] PM: Marking nosave pages: 0000000000091000 - 0000000000100000
[ 2625.071737] PM: Basic memory bitmaps created
[ 2625.071739] PM: Syncing filesystems ... done.
[ 2625.257239] Freezing user space processes ... (elapsed 0.00 seconds) done.
[ 2625.257828] Freezing remaining freezable tasks ... (elapsed 0.00 seconds) done.
[ 2625.257877] PM: Shrinking memory...  -\|/-\done (62084 pages freed)
[ 2626.734853] PM: Freed 248336 kbytes in 1.47 seconds (168.93 MB/s)
[ 2626.734867] Suspending console(s) (use no_console_suspend to debug)
[ 2626.736356] sd 0:0:0:0: [sda] Synchronizing SCSI cache
[ 2626.736641] pciehp 0000:00:1c.2:pcie02: pciehp_suspend ENTRY
[ 2626.736796] ricoh-mmc: Suspending.
[ 2626.736808] ricoh-mmc: Controller is now re-enabled.
[ 2626.737865] ACPI handle has no context!
[ 2626.737871] sdhci-pci 0000:0d:00.1: PCI INT B disabled
[ 2626.737877] ACPI handle has no context!
[ 2626.772208] r8169 0000:0c:00.0: PME# enabled
[ 2626.772218] r8169 0000:0c:00.0: wake-up capability enabled by ACPI
[ 2626.788415] ath5k_pci 0000:02:00.0: PCI INT A disabled
[ 2626.868458] ehci_hcd 0000:00:1d.7: PCI INT A disabled
[ 2626.868504] uhci_hcd 0000:00:1d.2: PCI INT C disabled
[ 2626.868549] uhci_hcd 0000:00:1d.1: PCI INT B disabled
[ 2626.868594] uhci_hcd 0000:00:1d.0: PCI INT A disabled
[ 2626.868641] pciehp 0000:00:1c.2:pcie02: pciehp_suspend ENTRY
[ 2626.900057] HDA Intel 0000:00:1b.0: PCI INT A disabled
[ 2626.916182] ehci_hcd 0000:00:1a.7: PCI INT C disabled
[ 2626.916245] uhci_hcd 0000:00:1a.2: PCI INT D disabled
[ 2626.916292] uhci_hcd 0000:00:1a.1: PCI INT B disabled
[ 2626.916339] uhci_hcd 0000:00:1a.0: PCI INT A disabled
[ 2626.916626] ACPI: Preparing to enter system sleep state S4
[ 2626.924254] Disabling non-boot CPUs ...
[ 2626.926531] NOHZ: local_softirq_pending 100
[ 2627.024019] CPU 1 is now offline
[ 2627.024022] SMP alternatives: switching to UP code
[ 2627.150056] CPU0 attaching NULL sched-domain.
[ 2627.150059] CPU1 attaching NULL sched-domain.
[ 2627.150284] CPU0 attaching NULL sched-domain.
[ 2627.150407] CPU1 is down
[ 2627.150480] Extended CMOS year: 2000
[ 2627.150551] PM: Creating hibernation image: 
[ 2627.154087] PM: Need to copy 120246 pages
[ 2627.154087] PM: Normal pages needed: 23848 + 1024 + 40, available pages: 202324
[ 2627.154087] Extended CMOS year: 2000
[ 2627.154087] Enabling non-boot CPUs ...
[ 2627.154087] SMP alternatives: switching to SMP code
[ 2627.281398] Booting processor 1 APIC 0x1 ip 0x6000
[ 2627.149917] Initializing CPU#1
[ 2627.149917] Calibrating delay using timer specific routine.. 3990.06 BogoMIPS (lpj=7980122)
[ 2627.149917] CPU: L1 I cache: 32K, L1 D cache: 32K
[ 2627.149917] CPU: L2 cache: 2048K
[ 2627.149917] CPU: Physical Processor ID: 0
[ 2627.149917] CPU: Processor Core ID: 1
[ 2627.372445] CPU1: Intel(R) Core(TM)2 Duo CPU     T5870  @ 2.00GHz stepping 0d
[ 2627.372499] CPU0 attaching NULL sched-domain.
[ 2627.373184] CPU0 attaching sched-domain:
[ 2627.373187]  domain 0: span 0-1 level MC
[ 2627.373189]   groups: 0 1
[ 2627.373193] CPU1 attaching sched-domain:
[ 2627.373195]  domain 0: span 0-1 level MC
[ 2627.373196]   groups: 1 0
[ 2627.376015] Switched to high resolution mode on CPU 1
[ 2627.376025] CPU1 is up
[ 2627.376027] ACPI: Waking up from system sleep state S4
[ 2627.799612] ACPI: EC: non-query interrupt received, switching to interrupt mode
[ 2627.926622] pci 0000:00:02.0: restoring config space at offset 0x1 (was 0x900007, writing 0x900407)
[ 2627.930023] pci 0000:00:02.0: setting latency timer to 64
[ 2627.930049] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[ 2627.930055] uhci_hcd 0000:00:1a.0: setting latency timer to 64
[ 2627.930103] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[ 2627.930109] uhci_hcd 0000:00:1a.1: setting latency timer to 64
[ 2627.930157] uhci_hcd 0000:00:1a.2: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[ 2627.930163] uhci_hcd 0000:00:1a.2: setting latency timer to 64
[ 2627.930211] ehci_hcd 0000:00:1a.7: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[ 2627.930217] ehci_hcd 0000:00:1a.7: setting latency timer to 64
[ 2627.944145] HDA Intel 0000:00:1b.0: restoring config space at offset 0x4 (was 0xf9ef8004, writing 0xfd8f4004)
[ 2627.944156] HDA Intel 0000:00:1b.0: restoring config space at offset 0x1 (was 0x100006, writing 0x100002)
[ 2627.944180] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[ 2627.944188] HDA Intel 0000:00:1b.0: setting latency timer to 64
[ 2627.944288] pcieport-driver 0000:00:1c.0: setting latency timer to 64
[ 2627.944361] pcieport-driver 0000:00:1c.1: setting latency timer to 64
[ 2627.944426] pcieport-driver 0000:00:1c.2: setting latency timer to 64
[ 2627.944431] pciehp 0000:00:1c.2:pcie02: pciehp_resume ENTRY
[ 2627.944494] pcieport-driver 0000:00:1c.3: setting latency timer to 64
[ 2627.944501] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[ 2627.944507] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[ 2627.944555] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[ 2627.944561] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[ 2627.944609] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[ 2627.944615] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[ 2627.944663] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[ 2627.944669] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[ 2627.944759] pci 0000:00:1e.0: setting latency timer to 64
[ 2627.944837] ahci 0000:00:1f.2: restoring config space at offset 0x1 (was 0x2b00403, writing 0x2b00407)
[ 2627.944872] ahci 0000:00:1f.2: setting latency timer to 64
[ 2627.960103] ath5k_pci 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[ 2627.976217] r8169 0000:0c:00.0: wake-up capability disabled by ACPI
[ 2627.976224] r8169 0000:0c:00.0: PME# disabled
[ 2628.044757] ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[16]  MMIO=[febff800-febfffff]  Max Packet=[2048]  IR/IT contexts=[4/4]
[ 2628.064152] sdhci-pci 0000:0d:00.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[ 2628.064156] sdhci-pci 0000:0d:00.1: Will use DMA mode even though HW doesn't fully claim to support it.
[ 2628.065164] ricoh-mmc: Resuming.
[ 2628.065172] ricoh-mmc: Controller is now disabled.
[ 2628.065269] pciehp 0000:00:1c.2:pcie02: pciehp_resume ENTRY
[ 2628.065345] sd 0:0:0:0: [sda] Starting disk
[ 2628.264117] ata6: SATA link down (SStatus 0 SControl 300)
[ 2628.264140] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[ 2628.264163] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[ 2628.264181] ata5: SATA link down (SStatus 0 SControl 300)
[ 2628.265824] ata1.00: ACPI cmd f5/00:00:00:00:00:a0 filtered out
[ 2628.266223] ata1.00: ACPI cmd ef/10:06:00:00:00:a0 succeeded
[ 2628.266225] ata1.00: ACPI cmd ef/10:03:00:00:00:a0 filtered out
[ 2628.266892] ata2.00: ACPI cmd ef/10:06:00:00:00:a0 succeeded
[ 2628.272410] ata2.00: ACPI cmd ef/10:06:00:00:00:a0 succeeded
[ 2628.274105] ata2.00: configured for UDMA/33
[ 2628.292060] ata2: exception Emask 0x10 SAct 0x0 SErr 0x0 action 0x9 t4
[ 2628.292062] ata2: irq_stat 0x40000001
[ 2628.296544] ata2.00: configured for UDMA/33
[ 2628.296548] ata2: EH complete
[ 2628.317468] ata1.00: ACPI cmd f5/00:00:00:00:00:a0 filtered out
[ 2628.317599] ata1.00: ACPI cmd ef/10:06:00:00:00:a0 succeeded
[ 2628.317603] ata1.00: ACPI cmd ef/10:03:00:00:00:a0 filtered out
[ 2628.319391] ata1.00: configured for UDMA/133
[ 2628.332113] ata1: exception Emask 0x10 SAct 0x0 SErr 0x0 action 0x9 t4
[ 2628.332115] ata1: irq_stat 0x00400040, connection status changed
[ 2628.336603] ata1.00: configured for UDMA/133
[ 2628.336606] ata1: EH complete
[ 2628.336666] sd 0:0:0:0: [sda] 488397168 512-byte hardware sectors: (250 GB/232 GiB)
[ 2628.336691] sd 0:0:0:0: [sda] Write Protect is off
[ 2628.336694] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[ 2628.336730] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[ 2628.336769] sd 0:0:0:0: [sda] 488397168 512-byte hardware sectors: (250 GB/232 GiB)
[ 2628.336787] sd 0:0:0:0: [sda] Write Protect is off
[ 2628.336789] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[ 2628.336807] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[ 2628.453863] pci 0000:00:02.0: setting latency timer to 64
[ 2628.455895] PM: Image restored successfully.
[ 2628.495411] Restarting tasks ... done.
[ 2628.510293] PM: Basic memory bitmaps freed
[ 2628.821370] synaptics was reset on resume, see synaptics_resume_reset if you have trouble on resume
[ 2631.496756] r8169: eth0: link down
[ 2631.496920] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 2631.652559] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 2631.678678] wlan0: direct probe to AP 00:0b:86:a9:ec:b0 try 1
[ 2631.706496] wlan0: direct probe to AP 00:0b:86:a9:ec:b0 try 1
[ 2631.905014] wlan0: direct probe to AP 00:0b:86:a9:ec:b0 try 2
[ 2632.105055] wlan0: direct probe to AP 00:0b:86:a9:ec:b0 try 3
[ 2632.304041] wlan0: direct probe to AP 00:0b:86:a9:ec:b0 timed out
[ 2777.690275] Monitor-Mwait will be used to enter C-3 state
[ 2798.035928] wlan0: authenticate with AP 00:1e:e5:62:55:42
[ 2798.037475] wlan0: authenticated
[ 2798.037484] wlan0: associate with AP 00:1e:e5:62:55:42
[ 2798.040168] wlan0: RX AssocResp from 00:1e:e5:62:55:42 (capab=0x411 status=0 aid=1)
[ 2798.040173] wlan0: associated
[ 2798.042120] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 2798.214272] padlock: VIA PadLock not detected.
[ 2803.533204] process `skype' is using obsolete setsockopt SO_BSDCOMPAT
[ 2808.609155] wlan0: no IPv6 routers present
[ 2858.043873] wlan0 direct probe responded
[ 2858.043887] wlan0: authenticate with AP 00:1e:e5:62:55:42
[ 2858.046444] wlan0: authenticated
[ 2858.046453] wlan0: associate with AP 00:1e:e5:62:55:42
[ 2858.048913] wlan0: RX ReassocResp from 00:1e:e5:62:55:42 (capab=0x411 status=0 aid=1)
[ 2858.048920] wlan0: associated
[ 2865.976839] wlan0: deauthenticated
[ 2866.976124] wlan0: direct probe to AP 00:1e:e5:62:55:42 try 1
[ 2866.979295] wlan0 direct probe responded
[ 2866.979303] wlan0: authenticate with AP 00:1e:e5:62:55:42
[ 2866.981743] wlan0: authenticated
[ 2866.981751] wlan0: associate with AP 00:1e:e5:62:55:42
[ 2866.983826] wlan0: RX ReassocResp from 00:1e:e5:62:55:42 (capab=0x411 status=0 aid=1)
[ 2866.983832] wlan0: associated
[ 3263.772319] ath5k phy0: unsupported jumbo
[ 7595.657833] ath5k phy0: unsupported jumbo
[ 8542.498733] ath5k phy0: noise floor calibration timeout (2412MHz)
[10261.378539] ath5k phy0: unsupported jumbo
[11538.121692] ath5k phy0: unsupported jumbo
[12665.706969] ath5k phy0: unsupported jumbo
[13472.343524] ath5k phy0: noise floor calibration timeout (2437MHz)
[13943.337414] ath5k phy0: noise floor calibration timeout (2457MHz)
[15366.925722] ath5k phy0: unsupported jumbo
[15914.512526] ath5k phy0: unsupported jumbo
[15986.627475] ath5k phy0: unsupported jumbo
[16055.901823] ath5k phy0: unsupported jumbo
[16825.339897] ath5k phy0: noise floor calibration timeout (2437MHz)
[17712.384037] ath5k phy0: unsupported jumbo
[17750.978412] ath5k phy0: unsupported jumbo
[17751.986395] ath5k phy0: unsupported jumbo
[17815.342807] ath5k phy0: unsupported jumbo
[17831.605707] ath5k phy0: unsupported jumbo
[17892.055863] ath5k phy0: unsupported jumbo
[17896.544024] ath5k phy0: unsupported jumbo
[17919.320708] ath5k phy0: unsupported jumbo
[17952.954287] ath5k phy0: unsupported jumbo
[17991.656807] ath5k phy0: unsupported jumbo
[18007.269018] ath5k phy0: unsupported jumbo
[18031.580928] ath5k phy0: unsupported jumbo
[18176.990238] ath5k phy0: unsupported jumbo
[18308.249291] ath5k phy0: unsupported jumbo
[18667.939059] ath5k phy0: unsupported jumbo
[18725.221236] ath5k phy0: unsupported jumbo
[19152.187095] ath5k phy0: unsupported jumbo
[19171.358723] ath5k phy0: unsupported jumbo
[19212.961374] ath5k phy0: unsupported jumbo
[19244.034579] ath5k phy0: unsupported jumbo
[19328.733715] ath5k phy0: unsupported jumbo
[19370.531112] ath5k phy0: unsupported jumbo
[19387.641687] ath5k phy0: unsupported jumbo
[19536.862801] ath5k phy0: unsupported jumbo
[19538.535948] ath5k phy0: unsupported jumbo
[19551.135207] ath5k phy0: unsupported jumbo
[19632.622566] ath5k phy0: unsupported jumbo
[19850.684139] ath5k phy0: unsupported jumbo
[19875.931393] ath5k phy0: unsupported jumbo
[19989.453737] ath5k phy0: unsupported jumbo
[20060.408782] ath5k phy0: unsupported jumbo
[20110.431970] ath5k phy0: unsupported jumbo
[20333.691457] ath5k phy0: unsupported jumbo
[20453.051885] ath5k phy0: unsupported jumbo
[20467.680321] ath5k phy0: unsupported jumbo
[20565.386742] ath5k phy0: unsupported jumbo
[20660.856453] ath5k phy0: unsupported jumbo
[20740.687353] ath5k phy0: unsupported jumbo
[21047.453969] ath5k phy0: unsupported jumbo
[21383.925767] ath5k phy0: unsupported jumbo
[21397.470213] ath5k phy0: unsupported jumbo
[21698.995274] ath5k phy0: unsupported jumbo
[22098.230208] ath5k phy0: unsupported jumbo
[22523.054087] ath5k phy0: unsupported jumbo
[22694.489025] ath5k phy0: unsupported jumbo
[23136.364735] ath5k phy0: unsupported jumbo
[23216.042642] ath5k phy0: unsupported jumbo
[23274.513124] ath5k phy0: unsupported jumbo
[23307.649603] ath5k phy0: unsupported jumbo
[23606.053823] ath5k phy0: unsupported jumbo
[23615.738905] ath5k phy0: unsupported jumbo
[23759.637172] ath5k phy0: unsupported jumbo
[24041.354154] ath5k phy0: unsupported jumbo
[24044.697420] ath5k phy0: unsupported jumbo
[24227.035920] ath5k phy0: unsupported jumbo
[24242.128796] ath5k phy0: unsupported jumbo
[31380.677741] ath5k phy0: unsupported jumbo
[42948.177631] ath5k phy0: unsupported jumbo
[44207.619594] ath5k phy0: unsupported jumbo
[44898.153215] ath5k phy0: unsupported jumbo
[47203.177235] ath5k phy0: unsupported jumbo
[47570.281263] ACPI: BIOS _OSI(Linux) query ignored
[47570.282102] ACPI: BIOS _OSI(Linux) query ignored
[47581.575664] ACPI: BIOS _OSI(Linux) query ignored
[47581.576536] ACPI: BIOS _OSI(Linux) query ignored
[48710.094271] UDF-fs: No VRS found
[48710.132169] ISO 9660 Extensions: Microsoft Joliet Level 1
[48710.132655] ISOFS: changing to secondary root
[49928.868256] ath5k phy0: unsupported jumbo
[50884.675132] ath5k phy0: unsupported jumbo
[51124.302376] ath5k phy0: unsupported jumbo
[53040.538813] ath5k phy0: unsupported jumbo
[53297.337473] ath5k phy0: noise floor calibration timeout (2437MHz)
[56517.282010] ath5k phy0: unsupported jumbo
[56797.371824] ath5k phy0: unsupported jumbo
[60257.196551] ath5k phy0: unsupported jumbo
[60694.668867] ath5k phy0: unsupported jumbo
[61552.164387] ath5k phy0: unsupported jumbo
[61747.516419] ath5k phy0: unsupported jumbo
[68518.342389] ath5k phy0: unsupported jumbo
[71768.046651] hda-intel: IRQ timing workaround is activated for card #0. Suggest a bigger bdl_pos_adj.
[72313.685950] ath5k phy0: unsupported jumbo
[75539.414221] [drm:gm45_get_vblank_counter] *ERROR* trying to get vblank count for disabled pipe 0
[75539.709239] PM: Marking nosave pages: 0000000000002000 - 0000000000006000
[75539.709243] PM: Marking nosave pages: 0000000000007000 - 0000000000010000
[75539.709245] PM: Marking nosave pages: 0000000000091000 - 0000000000100000
[75539.709251] PM: Basic memory bitmaps created
[75539.709253] PM: Syncing filesystems ... done.
[75539.717899] Freezing user space processes ... (elapsed 0.01 seconds) done.
[75539.736372] Freezing remaining freezable tasks ... (elapsed 0.00 seconds) done.
[75539.736414] PM: Shrinking memory...  -\|/-\|/-<5>ACPI: BIOS _OSI(Linux) query ignored
[75540.506171] ACPI: BIOS _OSI(Linux) query ignored
[75540.632131] \|/-\|/-\done (238011 pages freed)
[75544.719428] PM: Freed 952044 kbytes in 4.98 seconds (191.17 MB/s)
[75544.719442] Suspending console(s) (use no_console_suspend to debug)
[75544.924105] sd 0:0:0:0: [sda] Synchronizing SCSI cache
[75544.951693] pciehp 0000:00:1c.2:pcie02: pciehp_suspend ENTRY
[75544.951844] ricoh-mmc: Suspending.
[75544.951854] ricoh-mmc: Controller is now re-enabled.
[75544.952930] ACPI handle has no context!
[75544.952937] sdhci-pci 0000:0d:00.1: PCI INT B disabled
[75544.952944] ACPI handle has no context!
[75544.988206] r8169 0000:0c:00.0: PME# enabled
[75544.988216] r8169 0000:0c:00.0: wake-up capability enabled by ACPI
[75545.004413] ath5k_pci 0000:02:00.0: PCI INT A disabled
[75545.084413] ehci_hcd 0000:00:1d.7: PCI INT A disabled
[75545.084459] uhci_hcd 0000:00:1d.2: PCI INT C disabled
[75545.084505] uhci_hcd 0000:00:1d.1: PCI INT B disabled
[75545.084550] uhci_hcd 0000:00:1d.0: PCI INT A disabled
[75545.084596] pciehp 0000:00:1c.2:pcie02: pciehp_suspend ENTRY
[75545.100859] HDA Intel 0000:00:1b.0: PCI INT A disabled
[75545.116178] ehci_hcd 0000:00:1a.7: PCI INT C disabled
[75545.116242] uhci_hcd 0000:00:1a.2: PCI INT D disabled
[75545.116289] uhci_hcd 0000:00:1a.1: PCI INT B disabled
[75545.116336] uhci_hcd 0000:00:1a.0: PCI INT A disabled
[75545.116638] ACPI: Preparing to enter system sleep state S4
[75545.124426] Disabling non-boot CPUs ...
[75545.228017] CPU 1 is now offline
[75545.228020] SMP alternatives: switching to UP code
[75545.357191] CPU0 attaching NULL sched-domain.
[75545.357194] CPU1 attaching NULL sched-domain.
[75545.357226] CPU0 attaching NULL sched-domain.
[75545.357350] CPU1 is down
[75545.357423] Extended CMOS year: 2000
[75545.357493] PM: Creating hibernation image: 
[75545.361214] PM: Need to copy 114755 pages
[75545.361214] PM: Normal pages needed: 30918 + 1024 + 40, available pages: 195256
[75545.361214] Extended CMOS year: 2000
[75545.361214] Enabling non-boot CPUs ...
[75545.361214] SMP alternatives: switching to SMP code
[75545.488933] Booting processor 1 APIC 0x1 ip 0x6000
[75545.356997] Initializing CPU#1
[75545.356997] Calibrating delay using timer specific routine.. 3990.01 BogoMIPS (lpj=7980034)
[75545.356997] CPU: L1 I cache: 32K, L1 D cache: 32K
[75545.356997] CPU: L2 cache: 2048K
[75545.356997] CPU: Physical Processor ID: 0
[75545.356997] CPU: Processor Core ID: 1
[75545.576405] CPU1: Intel(R) Core(TM)2 Duo CPU     T5870  @ 2.00GHz stepping 0d
[75545.576474] CPU0 attaching NULL sched-domain.
[75545.577012] Switched to high resolution mode on CPU 1
[75545.580024] CPU0 attaching sched-domain:
[75545.580026]  domain 0: span 0-1 level MC
[75545.580029]   groups: 0 1
[75545.580033] CPU1 attaching sched-domain:
[75545.580034]  domain 0: span 0-1 level MC
[75545.580036]   groups: 1 0
[75545.580516] CPU1 is up
[75545.580518] ACPI: Waking up from system sleep state S4
[75546.004826] ACPI: EC: non-query interrupt received, switching to interrupt mode
[75546.129674] pci 0000:00:02.0: restoring config space at offset 0x1 (was 0x900007, writing 0x900407)
[75546.133093] pci 0000:00:02.0: setting latency timer to 64
[75546.133120] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[75546.133126] uhci_hcd 0000:00:1a.0: setting latency timer to 64
[75546.133176] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[75546.133182] uhci_hcd 0000:00:1a.1: setting latency timer to 64
[75546.133237] uhci_hcd 0000:00:1a.2: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[75546.133243] uhci_hcd 0000:00:1a.2: setting latency timer to 64
[75546.133291] ehci_hcd 0000:00:1a.7: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[75546.133297] ehci_hcd 0000:00:1a.7: setting latency timer to 64
[75546.148144] HDA Intel 0000:00:1b.0: restoring config space at offset 0x4 (was 0xf9ef8004, writing 0xfd8f4004)
[75546.148155] HDA Intel 0000:00:1b.0: restoring config space at offset 0x1 (was 0x100006, writing 0x100002)
[75546.148179] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[75546.148187] HDA Intel 0000:00:1b.0: setting latency timer to 64
[75546.148287] pcieport-driver 0000:00:1c.0: setting latency timer to 64
[75546.148359] pcieport-driver 0000:00:1c.1: setting latency timer to 64
[75546.148424] pcieport-driver 0000:00:1c.2: setting latency timer to 64
[75546.148428] pciehp 0000:00:1c.2:pcie02: pciehp_resume ENTRY
[75546.148491] pcieport-driver 0000:00:1c.3: setting latency timer to 64
[75546.148499] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[75546.148505] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[75546.148552] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[75546.148558] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[75546.148605] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[75546.148611] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[75546.148659] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[75546.148664] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[75546.148753] pci 0000:00:1e.0: setting latency timer to 64
[75546.148830] ahci 0000:00:1f.2: restoring config space at offset 0x1 (was 0x2b00403, writing 0x2b00407)
[75546.148866] ahci 0000:00:1f.2: setting latency timer to 64
[75546.164111] ath5k_pci 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[75546.180223] r8169 0000:0c:00.0: wake-up capability disabled by ACPI
[75546.180231] r8169 0000:0c:00.0: PME# disabled
[75546.248760] ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[16]  MMIO=[febff800-febfffff]  Max Packet=[2048]  IR/IT contexts=[4/4]
[75546.268153] sdhci-pci 0000:0d:00.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[75546.268158] sdhci-pci 0000:0d:00.1: Will use DMA mode even though HW doesn't fully claim to support it.
[75546.269166] ricoh-mmc: Resuming.
[75546.269175] ricoh-mmc: Controller is now disabled.
[75546.269279] pciehp 0000:00:1c.2:pcie02: pciehp_resume ENTRY
[75546.269354] sd 0:0:0:0: [sda] Starting disk
[75546.468116] ata5: SATA link down (SStatus 0 SControl 300)
[75546.468139] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[75546.468161] ata6: SATA link down (SStatus 0 SControl 300)
[75546.468179] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[75546.469842] ata1.00: ACPI cmd f5/00:00:00:00:00:a0 filtered out
[75546.470241] ata1.00: ACPI cmd ef/10:06:00:00:00:a0 succeeded
[75546.470243] ata1.00: ACPI cmd ef/10:03:00:00:00:a0 filtered out
[75546.470685] ata2.00: ACPI cmd ef/10:06:00:00:00:a0 succeeded
[75546.474407] ata2.00: ACPI cmd ef/10:06:00:00:00:a0 succeeded
[75546.475583] ata2.00: configured for UDMA/33
[75546.492062] ata2: exception Emask 0x10 SAct 0x0 SErr 0x0 action 0x9 t4
[75546.492065] ata2: irq_stat 0x40000001
[75546.494855] ata2.00: configured for UDMA/33
[75546.494858] ata2: EH complete
[75546.518146] ata1.00: ACPI cmd f5/00:00:00:00:00:a0 filtered out
[75546.518260] ata1.00: ACPI cmd ef/10:06:00:00:00:a0 succeeded
[75546.518263] ata1.00: ACPI cmd ef/10:03:00:00:00:a0 filtered out
[75546.520070] ata1.00: configured for UDMA/133
[75546.536112] ata1: exception Emask 0x10 SAct 0x0 SErr 0x0 action 0x9 t4
[75546.536115] ata1: irq_stat 0x00400040, connection status changed
[75546.539783] ata1.00: configured for UDMA/133
[75546.539786] ata1: EH complete
[75546.539833] sd 0:0:0:0: [sda] 488397168 512-byte hardware sectors: (250 GB/232 GiB)
[75546.539848] sd 0:0:0:0: [sda] Write Protect is off
[75546.539849] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[75546.539870] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[75546.539893] sd 0:0:0:0: [sda] 488397168 512-byte hardware sectors: (250 GB/232 GiB)
[75546.539904] sd 0:0:0:0: [sda] Write Protect is off
[75546.539906] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[75546.539925] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[75546.653304] pci 0000:00:02.0: setting latency timer to 64
[75546.655369] PM: Image restored successfully.
[75546.691055] Restarting tasks ... done.
[75546.692493] PM: Basic memory bitmaps freed
[75547.007898] synaptics was reset on resume, see synaptics_resume_reset if you have trouble on resume
[75553.247734] r8169: eth0: link down
[75553.248200] ADDRCONF(NETDEV_UP): eth0: link is not ready
[75553.653194] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[75553.688433] wlan0: direct probe to AP 00:0b:86:a9:ec:b0 try 1
[75553.715919] wlan0: direct probe to AP 00:0b:86:a9:ec:b0 try 1
[75553.912068] wlan0: direct probe to AP 00:0b:86:a9:ec:b0 try 2
[75554.112124] wlan0: direct probe to AP 00:0b:86:a9:ec:b0 try 3
[75554.316039] wlan0: direct probe to AP 00:0b:86:a9:ec:b0 timed out
[75584.578612] wlan0: authenticate with AP 00:0b:86:ad:00:d1
[75584.582131] wlan0: authenticated
[75584.582137] wlan0: associate with AP 00:0b:86:ad:00:d1
[75584.589890] wlan0: RX AssocResp from 00:0b:86:ad:00:d1 (capab=0x431 status=0 aid=3)
[75584.589894] wlan0: associated
[75584.590746] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[75595.520153] wlan0: no IPv6 routers present
[75645.370840] wlan0: authenticate with AP 00:0b:86:ad:00:d1
[75647.255338] wlan0: authenticate with AP 00:0b:86:ad:00:d1
[75647.257676] wlan0: authenticated
[75647.257692] wlan0: associate with AP 00:0b:86:ad:00:d1
[75647.260922] wlan0: RX ReassocResp from 00:0b:86:ad:00:d1 (capab=0x431 status=0 aid=3)
[75647.260929] wlan0: associated
[75704.747699] ath5k phy0: noise floor calibration timeout (2462MHz)
[75705.151100] ath5k phy0: noise floor calibration timeout (2467MHz)
[75706.382665] ath5k phy0: noise floor calibration timeout (2462MHz)
[75706.477983] wlan0 direct probe responded
[75706.477995] wlan0: authenticate with AP 00:0b:86:ad:00:d1
[75706.677047] wlan0: authenticate with AP 00:0b:86:ad:00:d1
[75706.877032] wlan0: authentication with AP 00:0b:86:ad:00:d1 timed out
[75707.169371] wlan0: disassociated
[75709.213516] wlan0: authenticate with AP 00:0b:86:ad:00:d1
[75709.215135] wlan0: authenticated
[75709.215144] wlan0: associate with AP 00:0b:86:ad:00:d1
[75709.218830] wlan0: RX ReassocResp from 00:0b:86:ad:00:d1 (capab=0x431 status=0 aid=3)
[75709.218837] wlan0: associated
[78404.720576] ath5k phy0: noise floor calibration timeout (2462MHz)
[79884.339820] ath5k phy0: noise floor calibration timeout (2462MHz)
[80605.342027] ACPI: BIOS _OSI(Linux) query ignored
[80605.342868] ACPI: BIOS _OSI(Linux) query ignored
[80687.260472] wlan0: authenticate with AP 00:0b:86:ab:13:31
[80687.267502] wlan0: authenticated
[80687.267513] wlan0: associate with AP 00:0b:86:ab:13:31
[80687.273164] wlan0: RX ReassocResp from 00:0b:86:ab:13:31 (capab=0x431 status=0 aid=2)
[80687.273172] wlan0: associated
[80700.601959] wlan0: disassociating by local choice (reason=3)
[80702.498131] wlan0: authenticate with AP 00:0b:86:ab:13:31
[80702.498185] wlan0: authenticate with AP 00:0b:86:ab:13:31
[80702.499714] wlan0: authenticate with AP 00:0b:86:ab:13:31
[80702.514655] wlan0: authenticated
[80702.514667] wlan0: associate with AP 00:0b:86:ab:13:31
[80702.519958] wlan0: RX AssocResp from 00:0b:86:ab:13:31 (capab=0x431 status=0 aid=2)
[80702.519966] wlan0: associated
[80732.521161] wlan0: No ProbeResp from current AP 00:0b:86:ab:13:31 - assume out of range
[80736.449666] wlan0: authenticate with AP 00:0b:86:ab:13:e1
[80736.451249] wlan0: authenticated
[80736.451258] wlan0: associate with AP 00:0b:86:ab:13:e1
[80736.461657] wlan0: RX ReassocResp from 00:0b:86:ab:13:e1 (capab=0x431 status=0 aid=1)
[80736.461665] wlan0: associated
[80783.940256] wlan0: authenticate with AP 00:0b:86:ac:5f:91
[80783.943478] wlan0: authenticated
[80783.943484] wlan0: associate with AP 00:0b:86:ac:5f:91
[80783.953484] wlan0: RX ReassocResp from 00:0b:86:ac:5f:91 (capab=0x431 status=0 aid=4)
[80783.953488] wlan0: associated
[80795.601889] wlan0: disassociating by local choice (reason=3)
[80799.325175] wlan0: authenticate with AP 00:0b:86:a3:0f:61
[80799.326756] wlan0: authenticated
[80799.326765] wlan0: associate with AP 00:0b:86:a3:0f:61
[80799.330276] wlan0: RX AssocResp from 00:0b:86:a3:0f:61 (capab=0x431 status=0 aid=2)
[80799.330284] wlan0: associated
[80842.114799] wlan0: authenticate with AP 00:0b:86:ac:63:11
[80842.118446] wlan0: authenticated
[80842.118457] wlan0: associate with AP 00:0b:86:ac:63:11
[80842.124395] wlan0: RX ReassocResp from 00:0b:86:ac:63:11 (capab=0x431 status=0 aid=2)
[80842.124402] wlan0: associated
[80848.124188] wlan0: No ProbeResp from current AP 00:0b:86:ac:63:11 - assume out of range
[80852.086260] wlan0: authenticate with AP 00:0b:86:a3:29:42
[80852.089908] wlan0: authenticated
[80852.089919] wlan0: associate with AP 00:0b:86:a3:29:42
[80852.097867] wlan0: RX ReassocResp from 00:0b:86:a3:29:42 (capab=0x431 status=0 aid=1)
[80852.097875] wlan0: associated
[80894.120222] wlan0: No ProbeResp from current AP 00:0b:86:a3:29:42 - assume out of range
[80897.945166] wlan0: authenticate with AP 00:0b:86:ac:63:b1
[80897.946845] wlan0: authenticated
[80897.946854] wlan0: associate with AP 00:0b:86:ac:63:b1
[80897.950852] wlan0: RX ReassocResp from 00:0b:86:ac:63:b1 (capab=0x431 status=0 aid=3)
[80897.950860] wlan0: associated
[80960.572136] ath5k phy0: failed to reset the MAC Chip
[80960.572147] ath5k phy0: can't reset hardware (-5)
[80960.572153] phy0: failed to set freq to 2412 MHz for scan
[80962.328427] wlan0: authenticate with AP 00:0b:86:a2:46:41
[80962.330131] wlan0: authenticated
[80962.330142] wlan0: associate with AP 00:0b:86:a2:46:41
[80962.334003] wlan0: RX ReassocResp from 00:0b:86:a2:46:41 (capab=0x431 status=0 aid=1)
[80962.334010] wlan0: associated
[80967.748357] ACPI: BIOS _OSI(Linux) query ignored
[80967.749201] ACPI: BIOS _OSI(Linux) query ignored
[81195.340379] ath5k phy0: noise floor calibration timeout (2462MHz)
[85329.802436] ACPI: BIOS _OSI(Linux) query ignored
[85329.803272] ACPI: BIOS _OSI(Linux) query ignored
[85492.312114] wlan0: No ProbeResp from current AP 00:0b:86:a2:46:41 - assume out of range
[85496.105156] wlan0: authenticate with AP 00:0b:86:ac:63:b1
[85496.106762] wlan0: authenticated
[85496.106768] wlan0: associate with AP 00:0b:86:ac:63:b1
[85496.110372] wlan0: RX ReassocResp from 00:0b:86:ac:63:b1 (capab=0x431 status=0 aid=2)
[85496.110377] wlan0: associated
[85706.248108] wlan0: No ProbeResp from current AP 00:0b:86:ac:63:b1 - assume out of range
[85710.087094] wlan0: authenticate with AP 00:0b:86:a3:29:42
[85710.091956] wlan0: authenticated
[85710.091968] wlan0: associate with AP 00:0b:86:a3:29:42
[85710.096547] wlan0: RX ReassocResp from 00:0b:86:a3:29:42 (capab=0x21 status=17 aid=0)
[85710.096554] wlan0: AP denied association (code=17)
[85710.098586] wlan0: RX ReassocResp from 00:0b:86:a3:29:42 (capab=0x21 status=17 aid=0)
[85710.098593] wlan0: AP denied association (code=17)
[85710.288194] wlan0: associate with AP 00:0b:86:a3:29:42
[85710.300849] wlan0: RX AssocResp from 00:0b:86:a3:29:42 (capab=0x431 status=0 aid=2)
[85710.300857] wlan0: associated
[85784.310587] wlan0: No ProbeResp from current AP 00:0b:86:a3:29:42 - assume out of range
[85795.161899] wlan0: authenticate with AP 00:0b:86:a3:0f:61
[85795.165969] wlan0: authenticated
[85795.165978] wlan0: associate with AP 00:0b:86:a3:0f:61
[85795.172981] wlan0: RX ReassocResp from 00:0b:86:a3:0f:61 (capab=0x431 status=0 aid=1)
[85795.172987] wlan0: associated
[85795.207805] wlan0: authenticate with AP 00:0b:86:a3:0f:61
[85795.209577] wlan0: authenticated
[85795.209588] wlan0: associate with AP 00:0b:86:a3:0f:61
[85795.408180] wlan0: associate with AP 00:0b:86:a3:0f:61
[85795.410227] wlan0: deauthenticated
[85796.408188] wlan0: direct probe to AP 00:0b:86:a3:0f:61 try 1
[85796.450986] wlan0 direct probe responded
[85796.450998] wlan0: authenticate with AP 00:0b:86:a3:0f:61
[85796.465855] wlan0: authenticated
[85796.465866] wlan0: associate with AP 00:0b:86:a3:0f:61
[85796.521639] wlan0: RX ReassocResp from 00:0b:86:a3:0f:61 (capab=0x431 status=0 aid=1)
[85796.521647] wlan0: associated
[85798.742509] ath5k phy0: noise floor calibration timeout (2412MHz)
[85799.835355] wlan0: disassociating by local choice (reason=3)
[85801.793027] wlan0: authenticate with AP 00:0b:86:a3:0f:61
[85801.795391] wlan0: authenticated
[85801.795402] wlan0: associate with AP 00:0b:86:a3:0f:61
[85801.796144] wlan0: authenticate with AP 00:0b:86:a3:0f:61
[85801.809415] wlan0: authenticated
[85801.809428] wlan0: associate with AP 00:0b:86:a3:0f:61
[85801.899538] wlan0: RX AssocResp from 00:0b:86:a3:0f:61 (capab=0x431 status=0 aid=1)
[85801.899546] wlan0: associated
[85863.896160] wlan0: No ProbeResp from current AP 00:0b:86:a3:0f:61 - assume out of range
[85868.240539] wlan0: authenticate with AP 00:0b:86:ab:13:e1
[85868.242203] wlan0: authenticated
[85868.242208] wlan0: associate with AP 00:0b:86:ab:13:e1
[85868.245728] wlan0: RX ReassocResp from 00:0b:86:ab:13:e1 (capab=0x431 status=0 aid=1)
[85868.245733] wlan0: associated
[85878.743004] ath5k phy0: noise floor calibration timeout (2412MHz)
[85882.644504] wlan0: authenticate with AP 00:0b:86:ac:5a:91
[85882.668493] wlan0: authenticated
[85882.668498] wlan0: associate with AP 00:0b:86:ac:5a:91
[85882.675895] wlan0: RX ReassocResp from 00:0b:86:ac:5a:91 (capab=0x431 status=0 aid=2)
[85882.675899] wlan0: associated
[85976.441027] ACPI: BIOS _OSI(Linux) query ignored
[85976.441865] ACPI: BIOS _OSI(Linux) query ignored
[85980.210162] wlan0: direct probe to AP 00:0b:86:ac:5a:91 try 1
[85980.238641] wlan0: authenticate with AP 00:0b:86:ad:00:d1
[85980.270219] wlan0: authenticate with AP 00:0b:86:ad:00:d1
[85980.290558] wlan0: authenticated
[85980.290566] wlan0: associate with AP 00:0b:86:ad:00:d1
[85980.294244] wlan0: RX ReassocResp from 00:0b:86:ad:00:d1 (capab=0x431 status=0 aid=6)
[85980.294251] wlan0: associated
[86042.294763] wlan0 direct probe responded
[86042.294775] wlan0: authenticate with AP 00:0b:86:ad:00:d1
[86042.296897] wlan0: authenticated
[86042.296905] wlan0: associate with AP 00:0b:86:ad:00:d1
[86042.300719] wlan0: RX ReassocResp from 00:0b:86:ad:00:d1 (capab=0x431 status=0 aid=6)
[86042.300726] wlan0: associated
[86397.340294] ath5k phy0: noise floor calibration timeout (2462MHz)
[86402.432158] wlan0: direct probe to AP 00:0b:86:ac:5a:91 try 1
[86402.436582] wlan0: authenticate with AP 00:0b:86:ad:00:d1
[86402.466783] wlan0: authenticate with AP 00:0b:86:ad:00:d1
[86402.469710] wlan0: authenticated
[86402.469721] wlan0: associate with AP 00:0b:86:ad:00:d1
[86402.473112] wlan0: RX ReassocResp from 00:0b:86:ad:00:d1 (capab=0x431 status=0 aid=6)
[86402.473118] wlan0: associated
[86464.480935] wlan0 direct probe responded
[86464.480948] wlan0: authenticate with AP 00:0b:86:ad:00:d1
[86464.483031] wlan0: authenticated
[86464.483038] wlan0: associate with AP 00:0b:86:ad:00:d1
[86464.486581] wlan0: RX ReassocResp from 00:0b:86:ad:00:d1 (capab=0x431 status=0 aid=6)
[86464.486587] wlan0: associated
[86649.341504] ath5k phy0: noise floor calibration timeout (2462MHz)
[86890.340380] ath5k phy0: noise floor calibration timeout (2462MHz)
[86911.340191] ath5k phy0: noise floor calibration timeout (2462MHz)
[87454.567286] ath5k phy0: unsupported jumbo
[89642.268632] wlan0: direct probe to AP 00:0b:86:ac:5a:91 try 1
[89642.270159] wlan0: authenticate with AP 00:0b:86:ad:00:d1
[89642.311937] wlan0: authenticate with AP 00:0b:86:ad:00:d1
[89642.314000] wlan0: authenticated
[89642.314009] wlan0: associate with AP 00:0b:86:ad:00:d1
[89642.318435] wlan0: RX ReassocResp from 00:0b:86:ad:00:d1 (capab=0x431 status=0 aid=6)
[89642.318441] wlan0: associated
[89704.322178] wlan0 direct probe responded
[89704.322191] wlan0: authenticate with AP 00:0b:86:ad:00:d1
[89704.324690] wlan0: authenticated
[89704.324697] wlan0: associate with AP 00:0b:86:ad:00:d1
[89704.329334] wlan0: RX ReassocResp from 00:0b:86:ad:00:d1 (capab=0x431 status=0 aid=6)
[89704.329340] wlan0: associated

```Part of the output of "sudo lshw"
```

  *-network
       description: Wireless interface
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wmaster0
       version: 01
       serial: 00:26:5e:e9:60:b9
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath5k_pci ip=137.155.129.100 latency=0 module=ath5k multicast=yes wireless=IEEE 802.11bg
  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:0c:00.0
       logical name: eth0
       version: 02
       serial: 00:26:18:1b:d7:58
       size: 10MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no module=r8169 multicast=yes port=MII speed=10MB/s
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: d6:98:8c:cf:c4:ce
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

```$ iwlist scan
```

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:0B:86:AD:00:D1
                    ESSID:"air-cnu"
                    Mode:Master
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=76/100  Signal level:-52 dBm  Noise level=-101 dBm
                    Encryption key:on
                    IE: Unknown: 00076169722D636E75
                    IE: Unknown: 010882840B0C12161824
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : 802.1x
                    IE: Unknown: DD0A00037F04010000000000
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:tsf=0000000966787c5e
                    Extra: Last beacon: 4764ms ago
          Cell 02 - Address: 00:0B:86:AD:00:D1
                    ESSID:""
                    Mode:Master
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=65/100  Signal level:-59 dBm  Noise level=-101 dBm
                    Encryption key:on
                    IE: Unknown: 0000
                    IE: Unknown: 010882840B160C121824
                    IE: Unknown: 03010B
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : 802.1x
                    IE: Unknown: DD0A00037F04010000000000
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:tsf=0000000966be9575
                    Extra: Last beacon: 168ms ago

pan0      Interface doesn't support scanning.

```$ lsb_release -d
```

Description:    Ubuntu 9.04

```$ uname -mr
```

2.6.28-15-generic i686

```$ sudo /etc/init.d/networking restart
```

* Reconfiguring network interfaces...                                          Ignoring unknown interface wlan0=wlan0.
                                                                         [ OK ]

```

---

### Post by rimunroe on 2009-09-18
I tried using the proprietary driver in the hardware manager but it did not change anything.

---

