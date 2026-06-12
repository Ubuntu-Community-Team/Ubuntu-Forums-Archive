---
title: "problem"
date: 2012-07-13
forum: Networking &amp; Wireless
---

### Post by morswin on 2012-07-13
Hi,

I've got problem with my wired network connection with Ubuntu 12.04 - it disconnect every time when i'm trying  open several tabs on internet browser, every time Transmissin reach connection speed limit, or i use few apps simultaneously (which uses net). 

I tried: 1) downgrade kernel, 2) using Wicd insead of Network menager, 3) set ip,  netmask and gateway manually, 4) install new drivers (using scripts/driver-select alx, make, sudo make install, modprobe alx). I,m new to ubuntu, and i don't know if i'm doing sth wrong but nothing works.
Any help would be appreciated.:D

Best Regards,
morswin

Some inf:

lspci -nn:
03:00.0 Network controller [0280]: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) [168c:002b] (rev 01)
04:00.0 Ethernet controller [0200]: Atheros Communications Inc. AR8151 v2.0 Gigabit Ethernet [1969:1083] (rev c0)

route -n:
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0

ifconfig:
eth0      Link encap:Ethernet  HWaddr 14:da:e9:ca:7a:5f  
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::16da:e9ff:feca:7a5f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:134038 errors:0 dropped:4132 overruns:4130 frame:4130
          TX packets:96387 errors:0 dropped:0 overruns:0 carrier:1
          collisions:0 txqueuelen:1000 
          RX bytes:156095675 (156.0 MB)  TX bytes:17113129 (17.1 MB)
          Interrupt:45 

lsmod:
Module                  Size  Used by
snd_hda_codec_hdmi     32474  1 
snd_hda_codec_realtek   223867  1 
parport_pc             32866  0 
rfcomm                 47604  0 
ppdev                  17113  0 
bnep                   18281  2 
binfmt_misc            17540  1 
snd_hda_intel          33773  5 
snd_hda_codec         127706  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
snd_pcm                97188  4 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
arc4                   12529  2 
snd_rawmidi            30748  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
ath9k                 132390  0 
mac80211              506816  1 ath9k
ath9k_common           14053  1 ath9k
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
i915                  468745  2 
snd_timer              29990  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
hid_a4tech             12678  0 
joydev                 17693  0 
drm_kms_helper         46978  1 i915
drm                   242038  3 i915,drm_kms_helper
snd                    78855  19 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
asus_nb_wmi            12710  0 
uvcvideo               72627  0 
ath9k_hw              411112  2 ath9k,ath9k_common
videodev               98259  1 uvcvideo
ath                    24067  3 ath9k,ath9k_common,ath9k_hw
asus_wmi               24456  1 asus_nb_wmi
i2c_algo_bit           13423  1 i915
psmouse                87692  0 
usbhid                 47199  0 
hid                    99559  2 hid_a4tech,usbhid
lp                     17799  0 
btusb                  18288  1 
sparse_keymap          13890  1 asus_wmi
serio_raw              13211  0 
mxm_wmi                12979  0 
wmi                    19256  2 asus_wmi,mxm_wmi
video                  19596  1 i915
v4l2_compat_ioctl32    17128  1 videodev
cfg80211              205544  3 ath9k,mac80211,ath
bluetooth             180104  13 rfcomm,bnep,btusb
soundcore              15091  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
mei                    41616  0 
parport                46562  3 parport_pc,ppdev,lp
mac_hid                13253  0 
atl1c                  41717  0


Two more things: Despite i don't have connection network menager and modem still pretends everything is OK ; and connection is back when i run 'sudo service network-menager restart' - but it's not a solution for me. I also use this eth connection on different laptop with ubuntu 11.04 and works like a charm.

---

### Post by Kirk Schnable on 2012-07-13
Looking at the output of your ifconfig, it looks like you've got a lot of dropped packets.  This could indicate a few things, including:

- Bad cable or cable end.
- Bad network card.
- Bad port on the switch.
- Drivers not working well for the network card.

It sounds like you've already explored the drivers although you're not sure if you've done them right...

Have you double checked that it's not a physical problem with your network?  Is that what you meant when you said you use the same eth with another laptop?

Kirk

---

### Post by morswin on 2012-07-13
Hi Kirk,

First of all - thank you for reply.
I do not think it is hardware problem. I had win7 before ubuntu and all was working great.  Also, if I switch to another laptop without touching the rest (cable, modem), all is working well, too. 

It is possible that I'm doing sth wrong while setup drivers. I use "compat-wireless-2012-07-03-pc" ([http://www.orbit-lab.org/kernel/compat-wireless-2.6/](http://www.orbit-lab.org/kernel/compat-wireless-2.6/)) drivers and follow standard procedure. Everything looks fine, there was no any troubles. Ones after restart,  pc refuses to start, so i used older kernel. I really need this ubuntu working properly since i decided to do not use windows.:


 sudo lshw -class network
[sudo] password for dirack: 
  *-network DISABLED      
       description: Wireless interface
       product: AR9285 Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 01
       serial: 74:2f:68:81:89:f5
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=3.2.0-25-generic firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11bgn
       resources: irq:17 memory:de200000-de20ffff
  *-network
       description: Ethernet interface
       product: AR8151 v2.0 Gigabit Ethernet
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: c0
       serial: 14:da:e9:ca:7a:5f
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=atl1c driverversion=1.0.1.0-NAPI duplex=full firmware=N/A ip=192.168.1.2 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:45 memory:dd800000-dd83ffff ioport:a000(size=128)


Regards,
morswin

---

### Post by Kirk Schnable on 2012-07-13
Which kernel are you actually running? 

You can get kernel version by running:
```
uname -r
```

You can get the version of the module running by running:
```
modinfo atl1c
```

It looks like atl1c is the module your network card uses.

I'd like to see some of your versions, should provide clues as to what's going wrong.

Kirk

---

### Post by morswin on 2012-07-13
uname -r
3.2.0-25-generic

modinfo atl1c
filename:       /lib/modules/3.2.0-25-generic/kernel/drivers/net/ethernet/atheros/atl1c/atl1c.ko
version:        1.0.1.0-NAPI
license:        GPL
description:    Atheros 1000M Ethernet Network Driver
author:         Jie Yang <jie.yang@atheros.com>
srcversion:     6248FD03EE4F8F50578B63E
alias:          pci:v00001969d00001083sv*sd*bc*sc*i*
alias:          pci:v00001969d00001073sv*sd*bc*sc*i*
alias:          pci:v00001969d00002062sv*sd*bc*sc*i*
alias:          pci:v00001969d00002060sv*sd*bc*sc*i*
alias:          pci:v00001969d00001062sv*sd*bc*sc*i*
alias:          pci:v00001969d00001063sv*sd*bc*sc*i*
depends:        
intree:         Y
vermagic:       3.2.0-25-generic SMP mod_unload modversions 


It seems that described problem exist independently of kernel i use. I used ...-23- and ...-26- kernels with no success. But i'll try again with liveCD and write in 20 minutes.

morswin

---

### Post by Cheesehead on 2012-07-13
> **morswin said:**
> I tried: 1) downgrade kernel, 2) using Wicd insead of Network menager, 3) set ip,  netmask and gateway manually, 4) install new drivers (using scripts/driver-select alx, make, sudo make install, modprobe alx). 

That's a lot of changes. Try to avoid lots of changes like that. It's a good way to break your system.

1) Won't work unless you're dealing with a kernel networking bug or hardware regression. kernel networking is pretty stable. Hardware regresssions are pretty easy to spot - the hardware usually doesn't work at all.

2) Network Manager, despite the claims of some, is both robust and stable. Five years ago it was a different story, but it's changed. And NM would make no difference to your problem - all it really does is present you with a pretty icon to bring the interface up.

3) Same as #2.

4) Changing drivers, more than anything else, can break your system if you don't know how to identify the correct chipset. Most wireless and ethernet chipsets are correctly identified and already supported with existing kernel.

Why is the ifconfig for the wired connection but you're messing with wireless drivers? Does this happen only with wired connections? Or does it happen with both wired and wireless? Can you reproduce the issue at will?

Next time it happens, after reconnecting, get the appropriate lines from /var/log/syslog and dmesg (the last 20 or so), and post them here.

---

### Post by morswin on 2012-07-13
I'm back,

LiveCD ubuntu 12.04 suffers the same problem. I attached file with last lines of mentioned files.  

I don't use wireless connection, so i don't know if there is sth wrong with it (and currently i'm unable to check  ). All i know that with win7 it worked.  

ifconfig:
eth0      Link encap:Ethernet  HWaddr 14:da:e9:ca:7a:5f  
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::16da:e9ff:feca:7a5f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2246 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2185 errors:0 dropped:0 overruns:0 carrier:1
          collisions:0 txqueuelen:1000 
          RX bytes:1574910 (1.5 MB)  TX bytes:395969 (395.9 KB)
          Interrupt:45 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:260 errors:0 dropped:0 overruns:0 frame:0
          TX packets:260 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:23200 (23.2 KB)  TX bytes:23200 (23.2 KB)

---

### Post by morswin on 2012-07-13
"Why is the ifconfig for the wired connection but you're messing with wireless drivers?"

That's actually good question.  It's because the only relevant driver to atheros  ar8151 (which controls wired connection) i found is  "compat-wireless-2012-07-03-pc".  Or i just don't understand something...

---

### Post by Cheesehead on 2012-07-13
Ah. Interesting.

```
Jul 13 20:57:33 dirack-K73SV NetworkManager[859]: <info> Unmanaged Device found; state CONNECTED forced. (see http://bugs.launchpad.net/bugs/191889)
```

There are lots of clues like this in that log dump. They seem to point to a fight going on within your system. Two different (incompatible) methods of controlling the ethernet interface are fighting for control of the hardware.

If true, that's easy enough to fix. If you make a lot of changes to your network settings in different places, try different software, etc, that is one of the risks.

Here's the most common reason for a network-setting fight: Take a look at your /etc/network/interfaces file. Is should look like the example below. If it doesn't then edit it to conform. Network Manager does not use the file to configure interfaces...but ifup (which NM uses) **does** use the file. See how that can cause a fight?
```
auto lo
iface lo inet loopback
```
If you make changes, right-click on Network Manager to disable networking, then open a terminal window and run ifconfig. Manually bring down any interfaces (except lo) that are still up. Then re-enable networking using NM.

If that doesn't solve the problem, let us know. There are other ways to mess up network settings...

---

### Post by morswin on 2012-07-13
Hi,  

many thanks for your advice, despite it doesn't work. File  /etc/network/interfaces looks exactly like your example. When i disable networking and run ifconfig it shows:

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:137 errors:0 dropped:0 overruns:0 frame:0
          TX packets:137 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:10457 (10.4 KB)  TX bytes:10457 (10.4 KB)

I really don't think it's my fault theres sth wrong because, like i said, with LiveCD or brand new installed OS everything goes equally wrong. 

Interesting thing is, that when i started installing ubuntu  there was a message that i do not have Ethernet  connection (although it was). After installation the connection appears properly, but with described issue. 

Regards,
morswin

---

### Post by Cheesehead on 2012-07-14
Aha. I found another possibility:

According to bugs:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/708307](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/708307)
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/749980](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/749980)
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/927782](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/927782) ,
your ethernet card should be using the driver atl1e instead of atl1c.

So try
```
sudo modprobe -r atl1c
sudo modprobe -a atl1e
```
and see if that makes a difference.

---

### Post by morswin on 2012-07-14
It's funny, because i simply can't do it. If i run:
sudo modprobe -r atl1c connection disappears, but after running second code nothing happen. When i then run 

sudo modprobe -a atl1c then the network is back. I tried everything: reboot, reinstall drivers, try different package , use alx ([http://elrepo.org/bugs/view.php?id=189](http://elrepo.org/bugs/view.php?id=189)) instead of atl1e. Folder 
'/lib/modules/3.2.0-26-generic/kernel/drivers/net/ethernet/atheros/atl1e' exist ( as well as '/lib/modules/3.2.0-26-generic/kernel/drivers/net/ethernet/atheros/atl1c'). When i remove atl1c driver, then after reboot it comes back. It looks like alt1c would be untouchable....

I'd like to know the man who invented this feature...


P. S. Today i also tried to remove 'resolveconf' and 'avahi' but it didn't help.  The only change i've noticed was in resolve.conf file. The content has changed from:

  1 # Generated by resolvconf
  2 search Home
  3 nameserver 127.0.0.1

to 

  1 # Generated by NetworkManager
  2 domain Home
  3 search Home
  4 nameserver 127.0.0.1

---

### Post by satish_j on 2012-07-20
> **morswin said:**
> 
I tried: 1) downgrade kernel, 2) using Wicd insead of Network menager, 3) set ip,  netmask and gateway manually, 4) install new drivers (using scripts/driver-select alx, make, sudo make install, modprobe alx). I,m new to ubuntu, and i don't know if i'm doing sth wrong but nothing works.
Any help would be appreciated.:D


Wait,you said you installed new drivers 'alx'..Did you removed the old atl1c drivers and blacklisted them.
Can you post the output of
```

lspci -v

```

---

### Post by morswin on 2012-07-30
Hi ,
 	Code:
 	lspci -v:

03:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)
    Subsystem: AzureWave AW-NB037H 802.11bgn Wireless Half-size Mini PCIe Card [AR9002WB-1NGCD]
    Flags: bus master, fast devsel, latency 0, IRQ 17
    Memory at de200000 (64-bit, non-prefetchable) [size=64K]
    Capabilities: <access denied>
    Kernel driver in use: ath9k
    Kernel modules: ath9k

04:00.0 Ethernet controller: Atheros Communications Inc. AR8151 v2.0 Gigabit Ethernet (rev c0)
    Subsystem: ASUSTeK Computer Inc. Device 1851
    Flags: bus master, fast devsel, latency 0, IRQ 45
    Memory at dd800000 (64-bit, non-prefetchable) [size=256K]
    I/O ports at a000 [size=128]
    Capabilities: <access denied>
    Kernel driver in use: atl1c
    Kernel modules: atl1c


I skipped the rest. What mean "blacklist drivers". Can you tell me what is the proper way to install those bloody drivers, becouse "scripts/driver-select alx, make, sudo make install, modprobe (-a -r) alx (atl1c, atl1e)" does not work.

Best regards,
morswin

---

