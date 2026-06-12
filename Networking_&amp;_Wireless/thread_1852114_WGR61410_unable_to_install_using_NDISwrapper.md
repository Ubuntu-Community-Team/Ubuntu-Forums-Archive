---
title: "WGR61410 unable to install using NDISwrapper"
date: 2011-09-29
forum: Networking &amp; Wireless
---

### Post by suniyo on 2011-09-29
Hi,

I have got now WGR614v10 - Netgear n150 model wireless router and successfully installed it on windows on my dualboot where everything is working well and I get connection on my laptop and phone easily. 

With Ubuntu I tried to install drivers using NDISwrapper but face a problem there as the downloaded firmware is a .chk file and not .inf and .sys file so how to install it using NDISwrapper in ubuntu?

I have installed drivers on windows using supplied CD automatically and don't know where drivers are located in /windows/system32 folder or anywhere else.

help needed :)

---

### Post by suniyo on 2011-09-29
I have tried to search Windows driver for WGR614v10 but it goes to Netgear page which supplies firmware and not the driver. Firmware is in .chk format...now .inf and .sys is not there anywhere in the windows installation. What to do?

---

### Post by praseodym on 2011-09-29
Hi,

which device is that? Please show

```
lspci -nnk | grep -iA2 net
lsusb
lsmod
iwconfig
rfkill list
```

---

### Post by suniyo on 2011-09-29
My connection is done in this way: DSL/Cable --> TNDSL Modem ---> Netgear N150 WGR614v10 wireless router ---> eth2 on my computer, as described in the manual. 

I am unable to find .inf and .sys files for the driver in windows xp installation as supplied files are in .chk extension and can't be extracted on either xp or in ubuntu.

for the info you asked:

lspci -nnk | grep -iA2 net  ::

00:19.0 Ethernet controller [0200]: Intel Corporation 82578DC Gigabit Network Connection [8086:10f0] (rev 06)
    Kernel driver in use: e1000e
    Kernel modules: e1000e

lsusb  ::

Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 003: ID 15d9:0a4c Dexon 
Bus 005 Device 002: ID 04d9:1702 Holtek Semiconductor, Inc. 
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 046d:080f Logitech, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

lsmod  ::

Module                  Size  Used by
binfmt_misc             6587  1 
nls_utf8                1069  1 
isofs                  29250  1 
xt_limit                1382  8 
xt_tcpudp               2011  28 
ipt_LOG                 4542  8 
ipt_MASQUERADE          1407  0 
xt_DSCP                 1677  0 
ipt_REJECT              1928  1 
nf_conntrack_irc        3332  0 
nf_conntrack_ftp        5381  0 
xt_state                1098  6 
iptable_nat             3543  0 
nf_nat                 15560  2 ipt_MASQUERADE,iptable_nat
nf_conntrack_ipv4      10346  9 iptable_nat,nf_nat
snd_hda_codec_realtek   203376  1 
quota_v2                2686  2 
nf_conntrack           60975  7 ipt_MASQUERADE,nf_conntrack_irc,nf_conntrack_ftp,xt_state,iptable_nat,nf_nat,nf_conntrack_ipv4
quota_tree              7500  1 quota_v2
nf_defrag_ipv4          1073  1 nf_conntrack_ipv4
iptable_mangle          1549  0 
iptable_filter          1369  1 
ip_tables               9899  3 iptable_nat,iptable_mangle,iptable_filter
snd_hda_intel          22069  2 
snd_hda_codec          74201  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               5412  1 snd_hda_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_seq_dummy           1338  0 
snd_pcm                70694  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
x_tables               14175  9 xt_limit,xt_tcpudp,ipt_LOG,ipt_MASQUERADE,xt_DSCP,ipt_REJECT,xt_state,iptable_nat,ip_tables
snd_seq_oss            26722  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              19098  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    54244  16 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
nvidia               9961216  39 
ppdev                   5259  0 
soundcore               6620  1 snd
snd_page_alloc          7076  2 snd_hda_intel,snd_pcm
parport_pc             25962  1 
lp                      7028  0 
parport                32635  3 ppdev,parport_pc,lp
psmouse                63677  0 
serio_raw               3978  0 
uvcvideo               57374  0 
videodev               34361  1 uvcvideo
v4l1_compat            13251  2 uvcvideo,videodev
fbcon                  35102  71 
tileblit                1999  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
uvesafb                22297  1 
video                  17375  0 
output                  1871  1 video
intel_agp              24375  0 
e1000e                119888  0 
agpgart                31724  2 nvidia,intel_agp
usbhid                 36110  0 
hid                    67288  1 usbhid


iwconfig  ::

lo        no wireless extensions.

eth2      no wireless extensions.

rfkill list  ::

no output returns to the command $

Thanks in advance for help ):P

---

### Post by praseodym on 2011-09-29
You dont need a windows driver/software for your router. Remove ndiswrapper completely:

```
sudo modprobe -rf ndiswrapper
sudo apt-get remove --purge ndiswrapper-common ndiswrapper-utils-1.9 ndisgtk
sudo rm /etc/modprobe.d/ndiswrapper.conf
sudo rm -r /etc/ndiswrapper/* 
sudo depmod -a
```
Remove your wired and DSL profiles (if there) in the network-manager applet and reboot. If you want to update the firmware of the router, there should be an option in the router interface. Just type the IP-address (handbook?) of the router into your browser.

Check after reboot:

```
uname -a
ifconfig -a
cat /etc/udev/rules.d/70-persistent-net.rules
route -n
cat /etc/resolv.conf
cat /etc/network/interfaces
```

---

### Post by suniyo on 2011-09-29
> **praseodym said:**
> 

Remove your wired and DSL profiles (if there) in the network-manager applet and reboot. If you want to update the firmware of the router, there should be an option in the router interface. Just type the IP-address (handbook?) of the router into your browser.



I have tried it without ndiswrapper but neither my router interface nor my modem interface is accessible on ubuntu. though if i connect modem directly it works well as I have static ip defined in my TNDSL modem using interface that is accessible in windows.

Anyways let me remove it and proceed as you said. Will post output here in moment.

---

### Post by suniyo on 2011-09-29
Bingo Buddy!!! 

It started working perfectly well and router interface is also accessible now ... but connection is still listed as wired eth2. I have setup access password of the router in windows so I think I don't need to change it here WA2 encryption, m I right?

anyways thanks for all the help.

---

### Post by suniyo on 2011-09-29
> **praseodym said:**
> You dont need a windows driver/software for your router. Remove ndiswrapper completely:


Just for my knowledge, can you tell me from which parameters you concluded that my device don't need it? It me help me learn and to help other with similar problems.

thanks :D

---

### Post by praseodym on 2011-09-29
In Ubuntu/most Linux distros you dont need additional drivers for routers. Check the file "70-persistent-net.rules", you can rename your interface therein.

---

### Post by suniyo on 2011-09-29
Problem appeared again after restart.... Once I restarted the machine problem is back.. now I am not able to connect again... though I am able to connect to network if I connect modem directly to ubuntu machine not via router.

Where is the problem?

---

### Post by suniyo on 2011-09-29
Info you asked:

uname -a ::

Linux tusker-machine 2.6.32-33-generic #72-Ubuntu SMP Fri Jul 29 21:08:37 UTC 2011 i686 GNU/Linux


ifconfig -a ::

eth2      Link encap:Ethernet  HWaddr 70:71:bc:50:ad:c9  
          inet addr:59.162.116.181  Bcast:59.162.116.255  Mask:255.255.255.0
          inet6 addr: fe80::7271:bcff:fe50:adc9/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1281 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1299 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:1368473 (1.3 MB)  TX bytes:152414 (152.4 KB)
          Memory:fb100000-fb120000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:276961 errors:0 dropped:0 overruns:0 frame:0
          TX packets:276961 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:27862338 (27.8 MB)  TX bytes:27862338 (27.8 MB)


cat /etc/udev/rules.d/70-persistent-net.rules ::

# This file maintains persistent names for network interfaces.
# See udev(7) for syntax.
#
# Entries are automatically added by the 75-persistent-net-generator.rules
# file; however you are also free to add your own entries.

# PCI device 0x8086:0x1064 (e100)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:13:20:0d:4f:df", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# USB device 0x0a5c:0x6300 (usb)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:1e:e3:09:55:58", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth1"

# PCI device 0x8086:0x10f0 (e1000e)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="70:71:bc:50:ad:c9", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth2"

# USB device 0x0a5c:0x6300 (usb)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:1e:e3:f8:1e:ce", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth3"


route -n ::

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
59.162.116.0    0.0.0.0         255.255.255.0   U     1      0        0 eth2
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth2
0.0.0.0         59.162.116.1    0.0.0.0         UG    0      0        0 eth2


cat /etc/resolv.conf ::

# Generated by NetworkManager
nameserver 202.54.10.2
nameserver 202.54.26.5

cat /etc/network/interfaces ::

auto lo
iface lo inet loopback

---

### Post by suniyo on 2011-09-29
In all cases mentioned above Wireless connection connected through router works perfectly well. Problem is connection with the local ubuntu machine to which the wireless router is connected.

If I connect like this: -> DSL modem --> Wireless router --> Machine it works perfectly well all my windows xp and laptop also but it doesn't work with ubuntu which is dual boot with windows xp. When I am logged into ubuntu wireless network is active and it works for other deviecs like laptop and phone but not on local machine. Strange. 

Apart from that all other problems are solved now.

Is there any mis-configuration in my modem?

---

