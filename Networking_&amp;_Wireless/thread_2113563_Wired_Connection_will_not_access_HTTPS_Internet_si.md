---
title: "Wired Connection will not access HTTPS Internet sites"
date: 2013-02-07
forum: Networking &amp; Wireless
---

### Post by wjdearborn on 2013-02-07
Suddenly my internet connection will no longer reach any sites that require the https (e.g. google sites, twitter etc.) using either Chrome or Firefox, most other websites load only part way (i.e. the circular icon continues to spin on many sites) usually those with ads that are not loaded, and my email program (Thunderbird) has stopped connecting with my various email accounts.

My connection is WIRED to my D-Link HD Media Router 3000 Dual Band N+ router which is wired to a cable modem. The wireless connections to other machines in the household are working perfectly ... to a Windows machine, two Nexus 7s, etc... Another wired machine running ubuntu 12.04 LTS accesses all sire.  Also when tested with the wired swapped out on second wired machine running Ubuntu 12.04 the connection worked perfectly hence the wire is OK. Changing the wire on the main machine does not correct the problem.

This occurred once before and then suddenly was corrected as I tried numerous commands from in this forum and on Askubuntu - but for the life of me I cannot get it to come back this time. At that time I raised the question here, but received no replies ... I hope ...

Below I have provided information that others have been asked for in this forum. I hope it will be helpful in sorting through this strange issue.


```

root@BLACKBIRD:/# lsb_release -a

LSB Version:    core-2.0-amd64:core-2.0-noarch:core-3.0-amd64:core-3.0-noarch:core-3.1-amd64:core-3.1-noarch:core-3.2-amd64:core-3.2-noarch:core-4.0-amd64:core-4.0-noarch
Distributor ID:    Ubuntu
Description:    Ubuntu 12.10
Release:    12.10
Codename:    quantal

``````

root@BLACKBIRD:/# uname -a

Linux BLACKBIRD 3.5.0-23-generic #35-Ubuntu SMP Thu Jan 24 13:15:40 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux

``````

root@BLACKBIRD:/# lspci -nnk | grep -iA2 net
00:07.0 Bridge [0680]: NVIDIA Corporation MCP61 Ethernet [10de:03ef] (rev a2)
    Subsystem: Giga-byte Technology Device [1458:e000]
    Kernel driver in use: forcedeth

``````

root@BLACKBIRD:/# lsmod
Module                  Size  Used by
snd_hda_codec_hdmi     32049  4 
rfcomm                 46620  4 
snd_hda_codec_realtek    78048  1 
bnep                   18141  2 
bluetooth             209249  10 rfcomm,bnep
parport_pc             32689  0 
ppdev                  17074  0 
binfmt_misc            17501  1 
nvidia              11257760  40 
snd_hda_intel          33492  5 
snd_hda_codec         134213  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              17699  1 snd_hda_codec
snd_pcm                96668  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13325  0 
snd_rawmidi            30513  1 snd_seq_midi
snd_seq_midi_event     14900  1 snd_seq_midi
snd_seq                61555  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29426  2 snd_pcm,snd_seq
snd_seq_device         14498  3 snd_seq_midi,snd_rawmidi,snd_seq
kvm_amd                55605  0 
snd                    78921  20 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
kvm                   414071  1 kvm_amd
soundcore              15048  1 snd
i2c_nforce2            13014  0 
snd_page_alloc         18485  2 snd_hda_intel,snd_pcm
edac_core              52452  0 
edac_mce_amd           23304  0 
serio_raw              13216  0 
joydev                 17458  0 
k10temp                13127  0 
microcode              22804  0 
mac_hid                13206  0 
lp                     17760  0 
parport                46346  3 parport_pc,ppdev,lp
firewire_ohci          40402  0 
firewire_core          64369  1 firewire_ohci
hid_generic            12541  0 
usbhid                 46987  0 
hid                   100411  2 hid_generic,usbhid
crc_itu_t              12708  1 firewire_core
sata_nv                31831  2 
forcedeth              67157  0

``````

root@BLACKBIRD:/# ifconfig
eth0      Link encap:Ethernet  HWaddr 50:e5:49:6c:eb:9a  
          inet addr:192.168.0.101  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::52e5:49ff:fe6c:eb9a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2391 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2154 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1291019 (1.2 MB)  TX bytes:329999 (329.9 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:423 errors:0 dropped:0 overruns:0 frame:0
          TX packets:423 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:44356 (44.3 KB)  TX bytes:44356 (44.3 KB)

``````

root@BLACKBIRD:/# nm-tool
NetworkManager Tool
State: connected (global)

- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            forcedeth
  State:             connected
  Default:           yes
  HW Address:        50:E5:49:6C:EB:9A

  Capabilities:
    Carrier Detect:  yes
    Speed:           1000 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.0.101
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.1

    DNS:             192.168.0.1

``````

root@BLACKBIRD:/# route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
192.168.0.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0

``````

root@BLACKBIRD:/# cat /etc/network/interfaces
auto lo
iface lo inet loopback

``````

root@BLACKBIRD:/# ifconfig eth0 down
root@BLACKBIRD:/# ifconfig eth0 up
root@BLACKBIRD:/# dhclient
RTNETLINK answers: File exists

```

---

