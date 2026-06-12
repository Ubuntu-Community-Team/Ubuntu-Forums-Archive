---
title: "&quot;Network not connected&quot; in Ubuntu 9.04"
date: 2009-05-01
forum: Networking &amp; Wireless
---

### Post by drelyn86 on 2009-05-01
I'm having a network issue with my livecd/USB-installation of Ubuntu Jaunty. 

The "oh so beautiful" notification area is telling me that my network is not connected. 

First, I must get this out of the way: _I have not had this problem with Gutsy, Hardy, Intepid, or my current Archlinux installation._

I don't have to deal with issues like this often, so I'll let you know everything that I know and everything I've tried....

```
ubuntu@ubuntu:~$ uname -a
Linux ubuntu 2.6.28-11-generic #42-Ubuntu SMP Fri Apr 17 01:57:59 UTC 2009 i686 GNU/Linux
```

```
ubuntu@ubuntu:~$ lspci
00:00.0 RAM memory: nVidia Corporation MCP55 Memory Controller (rev a2)
00:01.0 ISA bridge: nVidia Corporation MCP55 LPC Bridge (rev a3)
00:01.1 SMBus: nVidia Corporation MCP55 SMBus (rev a3)
00:02.0 USB Controller: nVidia Corporation MCP55 USB Controller (rev a1)
00:02.1 USB Controller: nVidia Corporation MCP55 USB Controller (rev a2)
00:04.0 IDE interface: nVidia Corporation MCP55 IDE (rev a1)
00:05.0 IDE interface: nVidia Corporation MCP55 SATA Controller (rev a3)
00:05.1 IDE interface: nVidia Corporation MCP55 SATA Controller (rev a3)
00:05.2 IDE interface: nVidia Corporation MCP55 SATA Controller (rev a3)
00:06.0 PCI bridge: nVidia Corporation MCP55 PCI bridge (rev a2)
00:06.1 Audio device: nVidia Corporation MCP55 High Definition Audio (rev a2)
00:08.0 Bridge: nVidia Corporation MCP55 Ethernet (rev a3)
00:09.0 Bridge: nVidia Corporation MCP55 Ethernet (rev a3)
00:0e.0 PCI bridge: nVidia Corporation MCP55 PCI Express bridge (rev a3)
00:0f.0 PCI bridge: nVidia Corporation MCP55 PCI Express bridge (rev a3)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:0b.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link)
03:00.0 VGA compatible controller: nVidia Corporation G94 [GeForce 9600 GT] (rev a1)
```

```
ubuntu@ubuntu:~$ lsmod
Module                  Size  Used by
binfmt_misc            16776  1 
lp                     17156  0 
bridge                 56340  0 
stp                    10500  1 bridge
bnep                   20224  2 
video                  25360  0 
output                 11008  1 video
input_polldev          11912  0 
joydev                 18368  0 
snd_usb_audio          90400  1 
snd_usb_lib            24320  1 snd_usb_audio
snd_hwdep              15108  1 snd_usb_audio
btusb                  19608  2 
ppdev                  15620  0 
psmouse                61972  0 
serio_raw              13316  0 
snd_hda_intel         435636  3 
cfi_cmdset_0002        31232  1 
snd_pcm_oss            46336  0 
snd_mixer_oss          22656  1 snd_pcm_oss
snd_pcm                82948  3 snd_usb_audio,snd_hda_intel,snd_pcm_oss
snd_seq_dummy          10756  0 
snd_seq_oss            37760  0 
snd_seq_midi           14336  0 
snd_rawmidi            29696  2 snd_usb_lib,snd_seq_midi
snd_seq_midi_event     15104  2 snd_seq_oss,snd_seq_midi
snd_seq                56880  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              29704  2 snd_pcm,snd_seq
jedec_probe            20352  0 
snd_seq_device         14988  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
cfi_probe              11520  0 
gen_probe              11264  2 jedec_probe,cfi_probe
cfi_util               13696  2 cfi_cmdset_0002,cfi_probe
k8temp                 12416  0 
pcspkr                 10496  0 
ck804xrom              12932  0 
snd                    62628  19 snd_usb_audio,snd_hwdep,snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
mtd                    23048  3 cfi_cmdset_0002,ck804xrom
soundcore              15200  1 snd
chipreg                11012  3 jedec_probe,cfi_probe,ck804xrom
snd_page_alloc         16904  2 snd_hda_intel,snd_pcm
i2c_nforce2            14980  0 
map_funcs               9984  1 ck804xrom
parport_pc             40100  1 
parport                42220  3 lp,ppdev,parport_pc
squashfs               46344  1 
aufs                  165924  1 
exportfs               12544  1 aufs
nls_iso8859_1          12032  1 
nls_cp437              13696  1 
vfat                   18816  1 
fat                    58272  1 vfat
hid_logitech           16256  0 
ff_memless             13320  1 hid_logitech
usbhid                 42336  1 hid_logitech
usb_storage            82880  1 
ohci1394               38576  0 
ieee1394               94660  1 ohci1394
forcedeth              61712  0 
fbcon                  46112  0 
tileblit               10752  1 fbcon
font                   16384  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit
```
(The module in question is "forcedeth")

```
ubuntu@ubuntu:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1e:8c:45:f4:aa  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:252 

eth1      Link encap:Ethernet  HWaddr 00:1e:8c:46:0f:2a  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:253 Base address:0x8000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```

**This is a very popular fix for a very similar issue. _It did not work for me._**
```
root@ubuntu:~# rmmod forcedeth
root@ubuntu:~# modprobe forcedeth msi=0 msix=0
root@ubuntu:~# /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                   [ OK ] 
```

```
root@ubuntu:~# dhclient eth0
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth0/00:1e:8c:45:f4:aa
Sending on   LPF/eth0/00:1e:8c:45:f4:aa
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 17
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 16
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
root@ubuntu:~# dhclient eth1
There is already a pid file /var/run/dhclient.pid with pid 8123
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth1/00:1e:8c:46:0f:2a
Sending on   LPF/eth1/00:1e:8c:46:0f:2a
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 18
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 12
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

```

```
ubuntu@ubuntu:~$ ping 127.0.0.1
PING 127.0.0.1 (127.0.0.1) 56(84) bytes of data.
64 bytes from 127.0.0.1: icmp_seq=1 ttl=64 time=0.022 ms
64 bytes from 127.0.0.1: icmp_seq=2 ttl=64 time=0.020 ms
64 bytes from 127.0.0.1: icmp_seq=3 ttl=64 time=0.021 ms
64 bytes from 127.0.0.1: icmp_seq=4 ttl=64 time=0.021 ms
64 bytes from 127.0.0.1: icmp_seq=5 ttl=64 time=0.019 ms
^C
--- 127.0.0.1 ping statistics ---
5 packets transmitted, 5 received, 0% packet loss, time 3998ms
rtt min/avg/max/mdev = 0.019/0.020/0.022/0.005 ms
```

I've also tried...
```
# ifconfig eth0 down
# ifconfig eth1 down
# ifconfig lo down
# ifconfig eth0 up
# ifconfig eth1 up
# ifconfig lo up
# /etc/init.d/networking restart
```

(looking for "_eth_0" "_eth_1" and "forced_eth_" messages...)
```
ubuntu@ubuntu:~$ dmesg | grep eth
[    1.249801] Driver 'sd' needs updating - please use bus_type methods
[    1.249807] Driver 'sr' needs updating - please use bus_type methods
[    6.512621] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.61.
[    6.512910] forcedeth 0000:00:08.0: PCI INT A -> Link[APCH] -> GSI 22 (level, low) -> IRQ 22
[    6.512914] forcedeth 0000:00:08.0: setting latency timer to 64
[    7.032639] forcedeth 0000:00:08.0: ifname eth0, PHY OUI 0x5043 @ 1, addr 00:1e:8c:45:f4:aa
[    7.032642] forcedeth 0000:00:08.0: highdma csum vlan pwrctl mgmt timirq gbit lnktim msi desc-v3
[    7.032936] forcedeth 0000:00:09.0: PCI INT A -> Link[AMC1] -> GSI 21 (level, low) -> IRQ 21
[    7.032939] forcedeth 0000:00:09.0: setting latency timer to 64
[    7.552668] forcedeth 0000:00:09.0: ifname eth1, PHY OUI 0x5043 @ 1, addr 00:1e:8c:46:0f:2a
[    7.552671] forcedeth 0000:00:09.0: highdma csum vlan pwrctl mgmt timirq gbit lnktim msi desc-v3
[   78.809016] forcedeth 0000:00:09.0: irq 2301 for MSI/MSI-X
[   78.809236] eth1: no link during initialization.
[   78.809638] ADDRCONF(NETDEV_UP): eth1: link is not ready
[   78.810719] forcedeth 0000:00:08.0: irq 2300 for MSI/MSI-X
[   78.810921] eth0: no link during initialization.
[   78.811325] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  174.732048] forcedeth 0000:00:09.0: PCI INT A disabled
[  174.741203] forcedeth 0000:00:08.0: PCI INT A disabled
[  189.856673] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.61.
[  189.856690] forcedeth 0000:00:08.0: PCI INT A -> Link[APCH] -> GSI 22 (level, low) -> IRQ 22
[  189.856694] forcedeth 0000:00:08.0: setting latency timer to 64
[  190.376931] forcedeth 0000:00:08.0: ifname eth0, PHY OUI 0x5043 @ 1, addr 00:1e:8c:45:f4:aa
[  190.376935] forcedeth 0000:00:08.0: highdma csum vlan pwrctl mgmt timirq gbit lnktim desc-v3
[  190.377120] forcedeth 0000:00:09.0: PCI INT A -> Link[AMC1] -> GSI 21 (level, low) -> IRQ 21
[  190.377124] forcedeth 0000:00:09.0: setting latency timer to 64
[  190.896736] forcedeth 0000:00:09.0: ifname eth1, PHY OUI 0x5043 @ 1, addr 00:1e:8c:46:0f:2a
[  190.896740] forcedeth 0000:00:09.0: highdma csum vlan pwrctl mgmt timirq gbit lnktim desc-v3
[  194.809557] eth0: no link during initialization.
[  194.809968] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  194.811144] eth1: no link during initialization.
[  194.811537] ADDRCONF(NETDEV_UP): eth1: link is not ready
[  412.146886] eth0: no link during initialization.
[  412.147322] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  415.442637] eth1: no link during initialization.
[  415.443048] ADDRCONF(NETDEV_UP): eth1: link is not ready


```

One interesting symptom that I've noticed is that I am not even getting a link-light with this version of Ubuntu... weird.

Again... I haven't had this problem with any of the previous 3 Ubuntu releases nor my current Archlinux installation. So we can rule out hardware and BIOS issues.

Anyways... I'm pretty stumped on this one. Help would be greatly appreciated. If there's any other output you need in helping me diagnose this issue, let me know.

Thanks in advance!

---

### Post by drelyn86 on 2009-05-03
Bump!

---

### Post by drelyn86 on 2009-05-04
Bump!
Surely somebody must have an idea...

---

### Post by tron1point0 on 2009-05-06
I have the exact same issue, except [FONT="Courier New"]lspci | grep -i ethernet[/FONT] produces:
```
00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a3)
```

---

### Post by magnus07 on 2009-05-06
Could be I have solved it....

I had a perfectly running 8.10 kindly made for a friend.
When I moved the PC to her network (Fastweb in Italy), somehow it could not acquire an IP address (DHCP). Another different HW with 8.10 could not either acquire an IP address but a windows XP could.

Slowly and painfully trying many things I tracked it down to the **NetworkManager Applet**.

It looks like that in some networks with possibly not perfectly crafted DHCP servers (embedded in routers) it has problems.

The solution is to get rid of the NetworkManager Applet and manually configure it or with WICD also available with apt-get.

Here are the steps as used by me taken from here:
[COLOR="RoyalBlue"][Kioskea.net]("http://en.kioskea.net/faq/sujet-979-having-a-static-ip-address-under-ubuntu-8-10")[/COLOR]

> [I]
To have a fixed IP persistent:
Uninstall NetworkManager
A straightforward approach is to uninstall NetworkManager:
sudo apt-get remove network-manager network-manager-gnome
Configure manually the interfaces

Modify the following file: /etc/networks/interfaces.
gksudo gedit /etc/network/interfaces

keep the following lines
auto lo
iface lo inet loopback
For a fix IP (10.0.0.1 on your eth1 interface) use:

auto eth1
iface eth1 inet static
address 10.0.0.1
netmask 255.255.255.0
To make use of dynamic IP (e.g eth0):

auto eth0
iface eth0 inet dhcp


then enter : sudo /etc/init.d/networking restart
to take changes in consideration.
DNS

If you want to make use of specific DNS, modify the following file /etc/resolv.conf
Note that if you are using DHCP on one of your interfaces, the contents of this file will be overwritten by the DHCP client.

To force the DHCP client to use a specific DNS, edit the file /etc/dhcp3/dhclient.conf

Add the following line:
prepend domain-name-servers 208.67.222.222,208.67.220.220;

DNS returned by DHCP are will be added after the DNS you specified.[/I]

---

### Post by tron1point0 on 2009-05-06
Turning off the computer for ~10 secs to clear whatever's in the chip's PROM works. Seems to have the same issue as Realtek cards. Seems like Arch sends a 'turn off' signal to the card on shutdown that doesn't clear on a reboot.

---

### Post by Hilko on 2009-05-07
The weirdest thing happened to me, it might be related. Just now i was on a wireless network. Everything was working fine. Then suddenly, for no reason the network connection was gone. I tried to reconnect by disabling and re-eneabling wireless networking. I tried 'sudo dhclient', i rebooted. Nothing worked.
Then I suspended my machine for a minute, woke up again...still not working.
Two minutes after that it suddenly reconnected. ???

It was like suspending and waking up fixed it.
I don't have a clue what happened and how or why it started working again.

---

### Post by HDave on 2009-05-14
I have the exact same problem as the OP drelyn86.  MCP55 chipset and network manager reporting nothing is connected.  However, the network IS functioning as I am posting this from the affect system.  I could learn to live with the incorrect network-manager display, but would prefer to get it working.

---

### Post by drelyn86 on 2009-05-15
tried setting it up to a static IP rather than DHCP... still no success. I didn't really think it would work since I'm not even getting a link light, but it was worth a shot.

also tried shutting down my PC for a while and booting directly into Ubuntu... that didn't work either. I've never have problems doing a reboot from Arch into Windows XP, so I don't see Arch being the problem here.

---

