---
title: "After update neither the wired or wireless is working anymore,Realtek RTL8111/8168B"
date: 2012-09-09
forum: Networking &amp; Wireless
---

### Post by stefanth on 2012-09-09
Hi

I need help to restore my internet connection on PC after I made an update of my pc last Friday (2012-09-07), I just executed aynaptic and agreed to all updates so I do not know which one was updated.

I have lost both my wired and wireless internet connection.

The wireless connection does not show up at all and the wired refuse to connect to the internet (I do not even see my PC's MAC address in my router leasing table)

As you notice below I have tried to make a step back on the Realtek driver from r8169 to r816, according to a post I read that seemed had the same problem as me)




```
# uname -srvmipo
Linux 3.2.0-29-generic #46-Ubuntu SMP Fri Jul 27 17:03:23  GNU/Linux

# ls /lib/modules/3.2.0-29-generic/kernel/drivers/net/ethernet/realtek/
8139cp.ko  8139too.ko  atp.ko  r8168.ko  r8169.bak

# iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

# ifconfig wlan0 up
wlan0: ERROR while getting interface flags: Enheten finns inte


```The "UP LOOPBACK RUNNING" in the following printout is worrying me I do not understand what it is or if it is affecting my connection

```

# ifconfig
eth0      Link encap:Ethernet  HWaddr 20:cf:30:c1:c0:61  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:41 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1148 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1148 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:91600 (91.6 KB)  TX bytes:91600 (91.6 KB)

```

```
# cat /etc/network/interfaces

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
#iface eth0 inet dhcp


``````

# lspci -v

04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 03)
    Subsystem: ASUSTeK Computer Inc. M4A785TD Motherboard
    Flags: bus master, fast devsel, latency 0, IRQ 41
    I/O ports at e800 [size=256]
    Memory at f8fff000 (64-bit, prefetchable) [size=4K]
    Memory at f8ff8000 (64-bit, prefetchable) [size=16K]
    Expansion ROM at fbff0000 [disabled] [size=64K]
    Capabilities: [40] Power Management version 3
    Capabilities: [50] MSI: Enable+ Count=1/1 Maskable- 64bit+
    Capabilities: [70] Express Endpoint, MSI 01
    Capabilities: [ac] MSI-X: Enable- Count=4 Masked-
    Capabilities: [cc] Vital Product Data
    Capabilities: [100] Advanced Error Reporting
    Capabilities: [140] Virtual Channel
    Capabilities: [160] Device Serial Number 00-00-00-00-00-00-00-00
    Kernel driver in use: r8168
    Kernel modules: r8168



# lscpi -nnk


04:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 03)
    Subsystem: ASUSTeK Computer Inc. M4A785TD Motherboard [1043:83a3]
    Kernel driver in use: r8168
    Kernel modules: r8168

```No driver/card conflict 
```
# lsmod
Module                  Size  Used by
nls_iso8859_1          12713  2 
nls_cp437              16991  2 
vfat                   17585  2 
fat                    61512  1 vfat
autofs4                37024  1 
bnep                   18281  2 
rfcomm                 47604  0 
bluetooth             180104  10 bnep,rfcomm
parport_pc             32866  0 
ppdev                  17113  0 
binfmt_misc            17540  1 
nfsd                  277809  2 
nfs                   356410  0 
lockd                  86161  2 nfsd,nfs
fscache                61529  1 nfs
auth_rpcgss            53380  2 nfsd,nfs
nfs_acl                12883  2 nfsd,nfs
sunrpc                245464  6 nfsd,nfs,lockd,auth_rpcgss,nfs_acl
dm_crypt               23125  0 
snd_hda_codec_hdmi     32474  1 
snd_hda_codec_realtek   224066  1 
nvidia              12319264  40 
snd_hda_intel          33773  2 
snd_hda_codec         127706  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
snd_pcm                97188  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30748  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
psmouse                87692  0 
snd_timer              29990  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
shpchp                 37277  0 
serio_raw              13211  0 
snd                    78855  14 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              15091  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
joydev                 17693  0 
i2c_nforce2            13058  0 
asus_atk0110           18078  0 
wmi                    19256  0 
mac_hid                13253  0 
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
vesafb                 13844  1 
usbhid                 47199  0 
hid                    99559  1 usbhid
r8168                 244911  0 
usb_storage            49198  2 

```I have also tried

 ```
sudo /etc/init.d/network-manager restart
Rather than invoking init scripts through /etc/init.d, use the service(8)
utility, e.g. service network-manager restart

Since the script you are attempting to invoke has been converted to an
Upstart job, you may also use the stop(8) and then start(8) utilities,
e.g. stop network-manager ; start network-manager. The restart(8) utility is also available.
network-manager stop/waiting
network-manager start/running, process 3388

```But still disconnected

---

### Post by chili555 on 2012-09-10
> The "UP LOOPBACK RUNNING" in the following printout is worrying me I do not understand what it is or if it is affecting my connection
The loopback interface lo is needed internally by the system. It is insignificant.> # cat /etc/network/interfaces

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
[COLOR="Red"]#[/COLOR]iface eth0 inet dhcpYou have told the system you wish to manually control the ethernet interface, but not how. DHCP? Static? Bridged? Mind control?

Generally, Network Manager will handle all these details for you. If it were me, I'd remove the highlighted parts:```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

[COLOR="Red"]# The primary network interface
auto eth0
#iface eth0 inet dhcp[/COLOR]
```Restart the computer and start your troubleshooting again:```
dmesg | grep -e eth0 -e r816
```

---

### Post by stefanth on 2012-09-10
Hi

After commenting the lines and restarted the computer, the result is as follow

```
$ dmesg | grep -e eth0 -e r816
[    2.295733] r8168 Gigabit Ethernet driver 8.032.00-NAPI loaded
[    2.296850] r8168 0000:04:00.0: PCI INT A -> Link[LN3A] -> GSI 19 (level, low) -> IRQ 19
[    2.296899] r8168 0000:04:00.0: setting latency timer to 64
[    2.297009] r8168 0000:04:00.0: irq 41 for MSI/MSI-X
[    2.326020] r8168: This product is covered by one or more of the following patents: US5,307,459, US5,434,872, US5,732,094, US6,570,884, US6,115,776, and US6,327,625.
[    2.326039] eth0: Identified chip type is 'RTL8168D/8111D'.
[    2.326050] r8168  Copyright (C) 2012  Realtek NIC software team <nicfae@realtek.com> 
[   16.677118] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   19.594674] r8168: eth0: link down
[   19.595945] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   19.597352] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   82.924612] r8168: eth0: link down
[   82.925453] ADDRCONF(NETDEV_UP): eth0: link is not ready

```Regards

---

### Post by chili555 on 2012-09-10
I wonder if Network Manager has a problem:```
nm-tool
cat /etc/NetworkManager/NetworkManager.conf
```Thanks.

---

### Post by stefanth on 2012-09-10
Hi

Thanks a lot for taking the time to help me, I appreciate it very much 

This is the result

```
$ nm-tool

NetworkManager Tool

State: disconnected

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8168
  State:             unavailable
  Default:           no
  HW Address:        20:CF:30:C1:C0:61

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off
``````
$ cat /etc/NetworkManager/NetworkManager.conf 
[main]
plugins=ifupdown,keyfile
dns=dnsmasq

[ifupdown]
managed=false

```
Regards

---

### Post by chili555 on 2012-09-11
Your NetworkManager.conf looks fine. This:> State: disconnected

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8168
  State:             unavailable
  Default:           no
  HW Address:        20:CF:30:C1:C0:61

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    [COLOR="Red"]Carrier:         off[/COLOR]...implies the cable is not connected, there is a problem with the cable or a problem with the port on the router. Can you please check?

---

### Post by stefanth on 2012-09-11
Hi

You are right there was something fuzzy with the cable, the two LED's on each side of the cable contact was not lighted as normal.

After checking the cable was working with another computer 

I went into the BIOS set-up and switch on a LAN test option twice and then everything started up as normal.

Thanks a lot for your patient and help

Regards
/Stefan

---

### Post by chili555 on 2012-09-11
Awesome! Glad it's working.

---

