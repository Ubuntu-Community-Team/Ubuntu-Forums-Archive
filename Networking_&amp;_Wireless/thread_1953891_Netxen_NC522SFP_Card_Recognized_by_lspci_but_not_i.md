---
title: "Netxen NC522SFP Card Recognized by lspci but not ifconfig (11.04)"
date: 2012-04-07
forum: Networking &amp; Wireless
---

### Post by mrcozturk on 2012-04-07
Hi all,

I have a Netxen 10Gbps network interface I am trying to get up and running in Ubuntu 11.04 (though I have tried 11.10 and end up with the same problem). The device is listed in lspci, but not in ifconfig:

```

lspci -v
03:00.0 Ethernet controller: NetXen Incorporated NX3031 Multifunction 1/10-Gigabit Server Adapter (rev 42)
    Subsystem: Hewlett-Packard Company NC522SFP Dual Port 10GbE Server Adapter
    Physical Slot: 4
    Flags: fast devsel, IRQ 16
    Memory at f8200000 (64-bit, non-prefetchable) [size=2M]
    Memory at f6000000 (64-bit, non-prefetchable) [size=32M]
    Expansion ROM at f8400000 [disabled] [size=64K]
    Capabilities: <access denied>
    Kernel modules: netxen_nic

03:00.1 Ethernet controller: NetXen Incorporated NX3031 Multifunction 1/10-Gigabit Server Adapter (rev 42)
    Subsystem: Hewlett-Packard Company NC522SFP Dual Port 10GbE Server Adapter
    Physical Slot: 4
    Flags: fast devsel, IRQ 16
    Memory at f8000000 (64-bit, non-prefetchable) [size=2M]
    Memory at f4000000 (64-bit, non-prefetchable) [size=32M]
    Capabilities: <access denied>
    Kernel modules: netxen_nic

```As you can see, the card looks like it's recognized and the netxen_nic module looks loaded. However, I do not see the device listed when running ifconfig -a:
```

ifconfig -a
bond0     Link encap:Ethernet  HWaddr f4:ce:46:a9:37:8c  
          inet addr:10.1.1.18  Bcast:10.1.1.255  Mask:255.255.255.0
          inet6 addr: fe80::f6ce:46ff:fea9:378c/64 Scope:Link
          UP BROADCAST RUNNING MASTER MULTICAST  MTU:1500  Metric:1
          RX packets:492188 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2391408 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:41849566 (41.8 MB)  TX bytes:3620317765 (3.6 GB)

eth0      Link encap:Ethernet  HWaddr f4:ce:46:a9:37:8c  
          UP BROADCAST RUNNING SLAVE MULTICAST  MTU:1500  Metric:1
          RX packets:123071 errors:0 dropped:0 overruns:0 frame:0
          TX packets:596971 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:10466881 (10.4 MB)  TX bytes:903746738 (903.7 MB)
          Memory:fa580000-fa600000 

eth1      Link encap:Ethernet  HWaddr f4:ce:46:a9:37:8c  
          UP BROADCAST RUNNING SLAVE MULTICAST  MTU:1500  Metric:1
          RX packets:123052 errors:0 dropped:0 overruns:0 frame:0
          TX packets:601436 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:10464728 (10.4 MB)  TX bytes:910505430 (910.5 MB)
          Memory:fa500000-fa580000 

eth2      Link encap:Ethernet  HWaddr 08:2e:5f:25:dd:6d  
          inet addr:192.168.1.56  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::a2e:5fff:fe25:dd6d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:33704 errors:0 dropped:0 overruns:0 frame:0
          TX packets:23370 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:41651175 (41.6 MB)  TX bytes:2789114 (2.7 MB)
          Interrupt:20 Memory:fa700000-fa720000 

eth3      Link encap:Ethernet  HWaddr f4:ce:46:a9:37:8c  
          UP BROADCAST RUNNING SLAVE MULTICAST  MTU:1500  Metric:1
          RX packets:122719 errors:0 dropped:0 overruns:0 frame:0
          TX packets:596014 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:10433029 (10.4 MB)  TX bytes:902296786 (902.2 MB)
          Memory:fa480000-fa500000 

eth4      Link encap:Ethernet  HWaddr f4:ce:46:a9:37:8c  
          UP BROADCAST RUNNING SLAVE MULTICAST  MTU:1500  Metric:1
          RX packets:123346 errors:0 dropped:0 overruns:0 frame:0
          TX packets:596987 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:10484928 (10.4 MB)  TX bytes:903768811 (903.7 MB)
          Memory:fa400000-fa480000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:20 errors:0 dropped:0 overruns:0 frame:0
          TX packets:20 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1200 (1.2 KB)  TX bytes:1200 (1.2 KB)

```I have another card on the machine with 4 network interfaces that I use for bond0 (which works great), along with eth2, which is connected to a router. It seems to me that based on the output from lspci I should be seeing two more interfaces here.

Looking into dmesg it looks like the driver is having some problems with the card for some reason:
```

dmesg | grep netxen
[    1.928121] netxen_nic 0000:03:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.928134] netxen_nic 0000:03:00.0: setting latency timer to 64
[    1.928558] netxen_nic 0000:03:00.0: 2MB memory map
[  202.224025] netxen_nic 0000:03:00.0: Error getting board config info.
[  202.224457] netxen_nic 0000:03:00.0: PCI INT A disabled
[  202.224473] netxen_nic: probe of 0000:03:00.0 failed with error -5
[  202.224493] netxen_nic 0000:03:00.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[  202.224510] netxen_nic 0000:03:00.1: setting latency timer to 64
[  202.225407] netxen_nic 0000:03:00.1: 2MB memory map
[  402.409875] netxen_nic 0000:03:00.1: Error getting board config info.
[  402.410304] netxen_nic 0000:03:00.1: PCI INT A disabled
[  402.410315] netxen_nic: probe of 0000:03:00.1 failed with error -5

```I cannot find any information on what these messages from dmesg mean. Does anyone have any insight as to where the problem may lie, and where I can go from here? 

I am stuck.

---

### Post by praseodym on 2012-04-07
Hi,

please show:

```
lspci -nnk | grep -iA2 Next
cat /etc/udev/rules.d/70-persistent-net.rules
dmesg | grep next
cat /etc/network/interfaces
lsmod
```

---

### Post by mrcozturk on 2012-04-07
Hi praseodym, 

Thanks for the response. The info you wanted is below:

lspci -nnk | grep -iA2 Next does not return anything.

dmesg | grep next does not return anything.

```

cat /etc/udev/rules.d/70-persistent-net.rules
# This file maintains persistent names for network interfaces.
# See udev(7) for syntax.
#
# Entries are automatically added by the 75-persistent-net-generator.rules
# file; however you are also free to add your own entries.

# PCI device 0x8086:0x150e (igb)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="f4:ce:46:a9:37:8e", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth3"

# PCI device 0x8086:0x150e (igb)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="f4:ce:46:a9:37:8f", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth4"

# PCI device 0x8086:0x150e (igb)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="f4:ce:46:a9:37:8d", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth1"

# PCI device 0x8086:0x150e (igb)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="f4:ce:46:a9:37:8c", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x8086:0x1502 (e1000e)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="08:2e:5f:25:dd:6d", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth2"

``````

cat /etc/network/interfaces 
auto lo
iface lo inet loopback

auto bond0
iface bond0 inet static
address 10.1.1.18
netmask 255.255.255.0
slaves eth0 eth1 eth3 eth4
bond_mode 0
bond_miimon 100

``````

lsmod
Module                  Size  Used by
parport_pc             36959  0 
ppdev                  17113  0 
bonding               113695  0 
snd_hda_codec_hdmi     28103  1 
snd_hda_codec_realtek   336693  1 
binfmt_misc            17565  1 
snd_hda_intel          33211  2 
snd_hda_codec         103804  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13604  1 snd_hda_codec
snd_pcm                96625  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30486  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61621  2 snd_seq_midi,snd_seq_midi_event
hp_wmi                 13706  0 
sparse_keymap          13898  1 hp_wmi
i915                  514985  3 
snd_timer              29602  2 snd_pcm,snd_seq
snd_seq_device         14462  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    67382  14 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse                73535  0 
serio_raw              13166  0 
drm_kms_helper         42136  1 i915
drm                   227495  4 i915,drm_kms_helper
soundcore              12680  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
i2c_algo_bit           13400  1 i915
video                  19438  1 i915
lp                     17825  0 
parport                46458  3 parport_pc,ppdev,lp
usbhid                 46956  0 
hid                    91020  1 usbhid
netxen_nic             96984  0 
ahci                   25951  2 
libahci                26642  1 ahci
e1000e                159096  0 
igb                   115875  0 
dca                    15219  1 igb

```

---

### Post by mrcozturk on 2012-04-07
Something interesting has happened.

If I do modprobe -r netxen_nic, then modprobe -r igb, the machine crashes, but upon restart both netxen interfaces are recognized in ifconfig and seem to be working (eth5 and eth6):
```

ifconfig
bond0     Link encap:Ethernet  HWaddr f4:ce:46:a9:39:50  
          inet addr:10.1.1.17  Bcast:10.1.1.255  Mask:255.255.255.0
          inet6 addr: fe80::f6ce:46ff:fea9:3950/64 Scope:Link
          UP BROADCAST RUNNING MASTER MULTICAST  MTU:1500  Metric:1
          RX packets:133 errors:0 dropped:0 overruns:0 frame:0
          TX packets:27 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:41259 (41.2 KB)  TX bytes:5610 (5.6 KB)

eth0      Link encap:Ethernet  HWaddr f4:ce:46:a9:39:50  
          UP BROADCAST RUNNING SLAVE MULTICAST  MTU:1500  Metric:1
          RX packets:31 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:9440 (9.4 KB)  TX bytes:1484 (1.4 KB)
          Memory:fa580000-fa600000 

eth1      Link encap:Ethernet  HWaddr f4:ce:46:a9:39:50  
          UP BROADCAST RUNNING SLAVE MULTICAST  MTU:1500  Metric:1
          RX packets:33 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:10470 (10.4 KB)  TX bytes:1279 (1.2 KB)
          Memory:fa500000-fa580000 

eth2      Link encap:Ethernet  HWaddr f4:ce:46:a9:39:50  
          UP BROADCAST RUNNING SLAVE MULTICAST  MTU:1500  Metric:1
          RX packets:31 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:9317 (9.3 KB)  TX bytes:1735 (1.7 KB)
          Memory:fa480000-fa500000 

eth3      Link encap:Ethernet  HWaddr f4:ce:46:a9:39:50  
          UP BROADCAST RUNNING SLAVE MULTICAST  MTU:1500  Metric:1
          RX packets:38 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:12032 (12.0 KB)  TX bytes:1112 (1.1 KB)
          Memory:fa400000-fa480000 

eth4      Link encap:Ethernet  HWaddr 08:2e:5f:25:de:82  
          inet addr:192.168.1.59  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::a2e:5fff:fe25:de82/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4868 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4542 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3963374 (3.9 MB)  TX bytes:877283 (877.2 KB)
          Interrupt:20 Memory:fa700000-fa720000 

eth5      Link encap:Ethernet  HWaddr f4:ce:46:b0:f0:a4  
          inet addr:10.1.2.17  Bcast:10.1.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:77 

eth6      Link encap:Ethernet  HWaddr f4:ce:46:b0:f0:a0  
          inet addr:10.1.3.17  Bcast:10.1.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:73 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:20 errors:0 dropped:0 overruns:0 frame:0
          TX packets:20 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1488 (1.4 KB)  TX bytes:1488 (1.4 KB)

```

However, if I then restart the machine (without issuing the two modprobe commands) the interfaces are again not recognized. Issuing modprobe -r netxen_nic by itself, then restarting does not work, it seems I need both commands.

What could be the explanation for this erratic behavior?

---

