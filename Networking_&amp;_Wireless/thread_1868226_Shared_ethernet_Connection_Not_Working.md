---
title: "Shared ethernet Connection Not Working"
date: 2011-10-24
forum: Networking &amp; Wireless
---

### Post by lvalen18 on 2011-10-24
SO Ever since the early builds of Ubuntu 11.10 all the way up to the Final Release I've had the issue..

What I do is connect a Desktop to a Router and share the Desktop Wireless Connection via the Ethernet (shared to Other Computers).. What starts happening is Ubuntu Keeps Connecting/Disconnecting the connection..

"Ethernet Connection Established" "Ethernet Connection Disconnected"

On 11.04 I didn't have this issue but ever since the bump to 11.10 it keeps happening.
___

Ubuntu 11.10 Unity(eww)
AMD 32bit

Wireless-- Broadcom
Ethernet -- Realtek (onboard) and AMDtek (PCI)

---

### Post by praseodym on 2011-10-24
Hi,

please show:

```
lspci -nnk | grep -iA2 net
lsmod
```

---

### Post by fransfrans on 2011-10-25
same here:
lspci -nnk | grep -iA2 net
00:19.0 Ethernet controller [0200]: Intel Corporation 82567LM-3 Gigabit Network Connection [8086:10de] (rev 02)
	Subsystem: Hewlett-Packard Company Device [103c:3035]
	Kernel driver in use: e1000e
--
07:09.0 Ethernet controller [0200]: Intel Corporation 82541PI Gigabit Ethernet Controller [8086:107c] (rev 05)
	Subsystem: Intel Corporation PRO/1000 GT Desktop Adapter [8086:1376]
	Kernel driver in use: e1000
schreuder@KVIS61:~$ lsmod
Module                  Size  Used by
ipt_MASQUERADE         12759  1 
xt_state               12578  1 
ipt_REJECT             12576  2 
xt_tcpudp              12603  4 
iptable_filter         12810  1 
nf_nat_h323            17002  0 
nf_conntrack_h323      62913  1 nf_nat_h323
nf_nat_pptp            12629  0 
nf_conntrack_pptp      13830  1 nf_nat_pptp
nf_conntrack_proto_gre    13656  1 nf_conntrack_pptp
nf_nat_proto_gre       12767  1 nf_nat_pptp
nf_nat_tftp            12489  0 
nf_conntrack_tftp      12953  1 nf_nat_tftp
nf_nat_sip             17086  0 
nf_conntrack_sip       29730  1 nf_nat_sip
nf_nat_irc             12643  0 
nf_conntrack_irc       13383  1 nf_nat_irc
nf_nat_ftp             12704  0 
nf_conntrack_ftp       13452  1 nf_nat_ftp
iptable_nat            13229  1 
nf_nat                 25890  9 ipt_MASQUERADE,nf_nat_h323,nf_nat_pptp,nf_nat_proto_gre,nf_nat_tftp,nf_nat_sip,nf_nat_irc,nf_nat_ftp,iptable_nat
nf_conntrack_ipv4      19716  4 iptable_nat,nf_nat
nf_conntrack           82342  18 ipt_MASQUERADE,xt_state,nf_nat_h323,nf_conntrack_h323,nf_nat_pptp,nf_conntrack_pptp,nf_conntrack_proto_gre,nf_nat_tftp,nf_conntrack_tftp,nf_nat_sip,nf_conntrack_sip,nf_nat_irc,nf_conntrack_irc,nf_nat_ftp,nf_conntrack_ftp,iptable_nat,nf_nat,nf_conntrack_ipv4
nf_defrag_ipv4         12729  1 nf_conntrack_ipv4
ip_tables              27473  2 iptable_filter,iptable_nat
x_tables               29846  7 ipt_MASQUERADE,xt_state,ipt_REJECT,xt_tcpudp,iptable_filter,iptable_nat,ip_tables
bnep                   18436  2 
rfcomm                 47946  0 
bluetooth             166112  10 bnep,rfcomm
binfmt_misc            17540  1 
vesafb                 13809  1 
nvidia              11713772  42 
snd_hda_codec_analog    93522  1 
tpm_infineon           17536  0 
snd_hda_intel          33390  2 
snd_hda_codec         104802  2 snd_hda_codec_analog,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
snd_pcm                96755  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30547  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
ppdev                  17113  0 
hp_wmi                 18092  0 
tpm_tis                18546  0 
sparse_keymap          13890  1 hp_wmi
snd_timer              29991  2 snd_pcm,snd_seq
parport_pc             36962  1 
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    68266  13 snd_hda_codec_analog,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse                73882  0 
wmi                    19256  1 hp_wmi
pl2303                 17993  0 
serio_raw              13166  0 
usbserial              47107  1 pl2303
soundcore              12680  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
mei                    41480  0 
lp                     17799  0 
parport                46562  3 ppdev,parport_pc,lp
floppy                 70365  0 
e1000                 108573  0 
e1000e                160535  0

---

### Post by praseodym on 2011-10-25
Internet connection sharing only works with WEP encryption. Which of those 2 cards do you use? Please show:

```
ifconfig -a
cat /etc/udev/rules.d/70-persistent-net.rules
route -n
dmesg | grep e1000
```
The driver e1000e maybe needs an update:

[http://thesorcerer.wordpress.com/2011/07/01/guide-intel-82573l-gigabit-ethernet-with-ubuntu-11-04-and-fix-pxe-e05/](http://thesorcerer.wordpress.com/2011/07/01/guide-intel-82573l-gigabit-ethernet-with-ubuntu-11-04-and-fix-pxe-e05/)

---

### Post by fransfrans on 2011-10-26
no, I am using a wired connection, wep encryption is not an issue

---

### Post by fransfrans on 2011-10-26
I have built and installed the latest e1000 driver and it doesn't make any difference

---

### Post by fransfrans on 2011-10-26
(using eth1 for the shared connection, eth0 is working normally) when I exchange the two (DHCP on eth1 and eth0 shared to others), eth0 starts having the same funny behaviour.

ifconfig -a
eth0      Link encap:Ethernet  HWaddr 18:a9:05:eb:5b:a5  
          inet addr:129.125.27.121  Bcast:129.125.255.255  Mask:255.255.0.0
          inet6 addr: fe80::1aa9:5ff:feeb:5ba5/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:362787 errors:0 dropped:2 overruns:0 frame:0
          TX packets:126862 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:377865821 (377.8 MB)  TX bytes:9893494 (9.8 MB)
          Interrupt:19 Memory:f3100000-f3120000 

eth1      Link encap:Ethernet  HWaddr 00:1b:21:c0:94:99  
          inet addr:10.42.43.1  Bcast:10.42.43.255  Mask:255.255.255.0
          inet6 addr: fe80::21b:21ff:fec0:9499/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9659 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:354 (354.0 B)  TX bytes:1985735 (1.9 MB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:437 errors:0 dropped:0 overruns:0 frame:0
          TX packets:437 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:35162 (35.1 KB)  TX bytes:35162 (35.1 KB)

---

### Post by fransfrans on 2011-10-26
cat /etc/udev/rules.d/70-persistent-net.rules
# This file was automatically generated by the /lib/udev/write_net_rules
# program, run by the persistent-net-generator.rules rules file.
#
# You can modify it, as long as you keep each rule on a single
# line, and change only the value of the NAME= key.

# PCI device 0x8086:0x10de (e1000e)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="18:a9:05:eb:5b:a5", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x8086:0x107c (e1000)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:1b:21:c0:94:99", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth1"

---

### Post by fransfrans on 2011-10-26
route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         129.125.15.251  0.0.0.0         UG    0      0        0 eth0
10.42.43.0      0.0.0.0         255.255.255.0   U     0      0        0 eth1
129.125.0.0     0.0.0.0         255.255.0.0     U     1      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0

---

### Post by fransfrans on 2011-10-26
dmesg | grep e1000
[    2.055971] e1000e: Intel(R) PRO/1000 Network Driver - 1.3.10-k2
[    2.055976] e1000e: Copyright(c) 1999 - 2011 Intel Corporation.
[    2.056067] e1000e 0000:00:19.0: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    2.056078] e1000e 0000:00:19.0: setting latency timer to 64
[    2.056188] e1000e 0000:00:19.0: irq 47 for MSI/MSI-X
[    2.075314] e1000: Intel(R) PRO/1000 Network Driver - version 7.3.21-k8-NAPI
[    2.075317] e1000: Copyright (c) 1999-2006 Intel Corporation.
[    2.075352] e1000 0000:07:09.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[    2.242250] e1000e 0000:00:19.0: eth0: (PCI Express:2.5GT/s:Width x1) 18:a9:05:eb:5b:a5
[    2.242254] e1000e 0000:00:19.0: eth0: Intel(R) PRO/1000 Network Connection
[    2.242288] e1000e 0000:00:19.0: eth0: MAC: 8, PHY: 8, PBA No: FFFFFF-0FF
[    2.510391] e1000 0000:07:09.0: eth1: (PCI:33MHz:32-bit) 00:1b:21:c0:94:99
[    2.510395] e1000 0000:07:09.0: eth1: Intel(R) PRO/1000 Network Connection
[   19.068170] e1000e 0000:00:19.0: irq 47 for MSI/MSI-X
[   19.124074] e1000e 0000:00:19.0: irq 47 for MSI/MSI-X
[   20.680882] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: None
[   20.680887] e1000e 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 4762.773660] e1000: eth1 NIC Link is Up 1000 Mbps Full Duplex, Flow Control: RX/TX
[ 5959.548131] e1000: eth1 NIC Link is Down
[ 5961.668133] e1000e: eth0 NIC Link is Down
[ 5969.084419] e1000: eth1 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX
[ 5973.860871] e1000e: eth0 NIC Link is Up 1000 Mbps Full Duplex, Flow Control: Rx/Tx
[ 6102.212126] e1000: eth1 NIC Link is Down
[ 6104.044146] e1000e: eth0 NIC Link is Down
[ 6108.141662] e1000: eth1 NIC Link is Up 1000 Mbps Full Duplex, Flow Control: RX/TX
[ 6112.388874] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: None
[ 6112.388880] e1000e 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[ 6337.134164] e1000 0000:07:09.0: PCI INT A disabled
[ 6522.025661] e1000 0000:07:09.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[ 6522.348021] e1000: 0000:07:09.0: e1000_probe: (PCI:33MHz:32-bit) 00:1b:21:c0:94:99
[ 6522.602741] e1000: eth1: e1000_probe: Intel(R) PRO/1000 Network Connection
[ 6525.994185] e1000: eth1: e1000_watchdog_task: NIC Link is Up 1000 Mbps Full Duplex, Flow Control: RX/TX

---

### Post by praseodym on 2011-10-26
wrong post from me

---

### Post by Ollytheninja on 2011-12-14
How far did you get with this fransfrans? I just discovered this issue today.

---

### Post by Ollytheninja on 2011-12-14
Found a solution, set ipv6 to ignore and reboot

---

