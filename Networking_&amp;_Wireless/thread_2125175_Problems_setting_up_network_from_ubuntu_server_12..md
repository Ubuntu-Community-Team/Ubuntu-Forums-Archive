---
title: "Problems setting up network from ubuntu server 12.04"
date: 2013-03-13
forum: Networking &amp; Wireless
---

### Post by natwhey on 2013-03-13
I have installed Ubuntu Server 12.04 onto my server. As I have no understanding of the Ubuntu Server command line interface - I have installed KDE to aid in setup. (I previously had suse linux enterprise server on the server).

I have two wired network cards in the server - one at eth0, the other at eth1.

eth0 is the one where the internet comes into and is set to Auto DHCP and works fine bringing the internet into the server.

eth1 is the one that connects to my windows box. I have tried to use the settings from the previous suse install - ip address, subnet mask (gateway - what should this be), dns servers & search domains but to no avail - there mut be something I am missing.

The settings are the same as they were on suse, the settings have not changed on the windows box.

HELP!!!

---

### Post by praseodym on 2013-03-13
Please show the terminal outputs of
```

lspci -nnk | grep -iA2 net
cat /etc/udev/rules.d/70-persistent-net.rules
ifconfig -a
lsmod
cat /etc/network/interfaces
cat /etc/resolv.conf
cat /etc/NetworkManager/NetworkManager.conf
```

---

### Post by natwhey on 2013-03-13
How do I get this information?

---

### Post by TK999 on 2013-03-13
Just type these commands into the server's terminal (command line).

---

### Post by natwhey on 2013-03-13
00:07.0 Bridge [0680]: NVIDIA Corporation MCP61 Ethernet [10de:03ef] (rev a2)
        Subsystem: ASRock Incorporation 939NF6G-VSTA Board [1849:03ef]
        Kernel driver in use: forcedeth
--
01:08.0 Ethernet controller [0200]: National Semiconductor Corporation DP83815 (MacPhyter) Ethernet Controller [100b:0020]
        Subsystem: Netgear Device [1385:f331]
        Kernel driver in use: natsemi
        Kernel modules: natsemi

ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:40:f4:59:3b:4d  
          inet6 addr: fe80::240:f4ff:fe59:3b4d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:15145 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8407 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:997908 (997.9 KB)  TX bytes:1863017 (1.8 MB)

eth1      Link encap:Ethernet  HWaddr 00:19:66:0b:d5:2c  
          inet addr:192.168.1.104  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::219:66ff:fe0b:d52c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:50702 errors:0 dropped:0 overruns:0 frame:0
          TX packets:32452 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:55315007 (55.3 MB)  TX bytes:3491926 (3.4 MB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1133 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1133 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:106182 (106.1 KB)  TX bytes:106182 (106.1 KB)

lsmod
Module                  Size  Used by
dm_crypt               23011  0 
snd_hda_codec_hdmi     32007  4 
snd_hda_intel          33491  2 
snd_hda_codec         134212  2 snd_hda_codec_hdmi,snd_hda_intel
snd_hwdep              13602  1 snd_hda_codec
snd_pcm                96580  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30512  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61521  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29425  2 snd_pcm,snd_seq
snd_seq_device         14497  3 snd_seq_midi,snd_rawmidi,snd_seq
edac_core              52451  0 
snd                    78734  13 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
k8temp                 12978  0 
serio_raw              13215  0 
edac_mce_amd           23303  0 
soundcore              15047  1 snd
snd_page_alloc         18484  2 snd_hda_intel,snd_pcm
rfcomm                 46619  0 
bnep                   18140  2 
bluetooth             209199  10 rfcomm,bnep
ppdev                  17073  0 
i2c_nforce2            13013  0 
parport_pc             32688  1 
mac_hid                13205  0 
lp                     17759  0 
parport                46345  3 ppdev,parport_pc,lp
hid_generic            12493  0 
usbhid                 46947  0 
hid                   100366  2 hid_generic,usbhid
nouveau               895609  3 
ttm                    83595  1 nouveau
drm_kms_helper         46784  1 nouveau
drm                   275528  5 nouveau,ttm,drm_kms_helper
sata_nv                31830  3 
natsemi                36296  0 
pata_amd               14118  0 
i2c_algo_bit           13413  1 nouveau
mxm_wmi                12979  1 nouveau
video                  19335  1 nouveau
wmi                    19070  2 nouveau,mxm_wmi
forcedeth              67156  0

cat /etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth1
iface eth1 inet dhcp

cat /etc/resolv.conf
# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
nameserver 192.168.1.1
search default

cat /etc/NetworkManager/NetworkManager.conf
[main]
plugins=ifupdown,keyfile
dns=dnsmasq

no-auto-default=00:40:F4:59:3B:4D,

[ifupdown]
managed=false

---

### Post by SeijiSensei on 2013-03-13
eth0 has not been assigned an address.

You also need to enable IP forwarding by uncommenting the line "net.ipv4.ip_forward=1" in /etc/sysctl.conf.  Read the comments in that file for more details.

You also need an iptables rule to "[masquerade]("https://help.ubuntu.com/community/Internet/ConnectionSharing")" the traffic from the Windows machine.

---

### Post by natwhey on 2013-03-13
why am i assigning an address to a dhcp connection?

how can i edit sysctl.conf when it says it is read only?

How can I do all of the above in KDE as opposed to command line?

---

### Post by SeijiSensei on 2013-03-13
I'm saying eth0 has not received an address from the DHCP server.  If it had, the ifconfig entry would report the address.

You have to edit /etc/sysctl.conf as root with sudo.

As for doing this through KDE, I can't say.  Try opening a terminal and using nano, e.g., "sudo nano /etc/sysctl.conf".

---

### Post by natwhey on 2013-03-14
Hi All,

Still having problems.

Are there any local to Kent Ubuntu Server Experts out there that can set up our server onsite?

---

### Post by steeldriver on 2013-03-14
Although it may seem like you're making life easier by installing the KDE desktop, bringing network-manager into the mix complicates things imho - the two network services don't always play well together, and network-manager really works best with a single active interface (e.g. it disables wireless by default when it detects a wired connection)

I think you would find it easier if you at least removed network-manager (not sure whether KDE uses network-manager-gnome or has its own meta package) and defined BOTH interfaces in /etc/network/interfaces

---

