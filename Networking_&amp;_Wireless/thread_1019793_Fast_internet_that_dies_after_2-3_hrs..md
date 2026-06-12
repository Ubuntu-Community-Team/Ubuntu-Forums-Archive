---
title: "Fast internet that dies after 2-3 hrs."
date: 2008-12-23
forum: Networking &amp; Wireless
---

### Post by eeliottheking on 2008-12-23
Hello, i posted a thread earlier about how my ubuntu 8.04 wireless network was limiting my connection speed to 100KB/s.  well, since I've upgraded to 8.10 this problem has been resolved; however, a new problem has arisen. After about 2-3 hours of internet related activity my internet will completely die.  my connection settings show that i still have an active connection, and continues to show how good my connection is, but nothing will load in my browser, all of my chats in pidgin on all network types die, my skype conversations get dropped, and all active torrents drop to 0 KB/s.  Rebooting my computer completely resolves this problem, for about 2-3 hours untill i have to reboot again.  This can be extremely annoying when im torrenting large files, or i am doing any kind of internet activity that may require me to walk away from the computer a bit.

---

### Post by andguent on 2008-12-23
It is possible that your router may be causing problems. No garuntee though.

Are there any other computers that are on the same network? Have any of them ever had this problem? When in the broken state, can you run the following commands for us and post the output?
```

ifconfig
route -n
cat /etc/resolv.conf
ping -c 6 www.google.com
ping -c 6 64.233.169.147
ping -c 6 `route -n|tail -1|cut -c 17-32`

```

I might recommend copy-pasting them into a text file on the computer so you don't have to manually type them (unless you want to).

---

### Post by eeliottheking on 2008-12-23
> **andguent said:**
> It is possible that your router may be causing problems. No garuntee though.

Are there any other computers that are on the same network? Have any of them ever had this problem? When in the broken state, can you run the following commands for us and post the output?
```

ifconfig
route -n
cat /etc/resolv.conf
ping -c 6 www.google.com
ping -c 6 64.233.169.147
ping -c 6 `route -n|tail -1|cut -c 17-32`

```

I might recommend copy-pasting them into a text file on the computer so you don't have to manually type them (unless you want to).

I have never experienced this particular problem on Ubuntu 8.04, Windows XP, or Windows Vista.  so im assuming it isn't an issue with the router.  We have one other computer (also running ubuntu 8.10) thats wired into the router that does not have this problem.  I will post the above results the next time my internet breaks.

EDIT:  sorry, its going to be a bit.  the power just went out and i had to shutdown because i was running on emergency power.

---

### Post by eeliottheking on 2008-12-23
alright, here are the results for those commands

ifconfig
```
eeliottheking@eeliottheking-cpu:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1f:c6:04:bb:f2  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:222 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2775 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2775 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:246396 (246.3 KB)  TX bytes:246396 (246.3 KB)

wlan0     Link encap:Ethernet  HWaddr 00:16:44:a5:7d:47  
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::216:44ff:fea5:7d47/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1229938 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1479476 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:744932694 (744.9 MB)  TX bytes:864334167 (864.3 MB)

wmaster0  Link encap:UNSPEC  HWaddr 00-16-44-A5-7D-47-64-34-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```


route -n
```
eeliottheking@eeliottheking-cpu:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     2      0        0 wlan0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlan0
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 wlan0

```


cat /etc/resolv.conf
```
eeliottheking@eeliottheking-cpu:~$ cat /etc/resolv.conf
# Generated by NetworkManager
nameserver 192.168.1.1

```


ping -c 6 [www.google.com](www.google.com)
```
eeliottheking@eeliottheking-cpu:~$ ping -c 6 www.google.com
ping: unknown host www.google.com

```


ping -c 6 64.233.169.147
```
eeliottheking@eeliottheking-cpu:~$ ping -c 6 64.233.169.147
PING 64.233.169.147 (64.233.169.147) 56(84) bytes of data.

--- 64.233.169.147 ping statistics ---
6 packets transmitted, 0 received, 100% packet loss, time 5016ms

```


ping -c 6 `route -n|tail -1|cut -c 17-32`
```
eeliottheking@eeliottheking-cpu:~$ ping -c 6 `route -n|tail -1|cut -c 17-32`
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.

--- 192.168.1.1 ping statistics ---
6 packets transmitted, 0 received, 100% packet loss, time 5018ms

```

---

### Post by solitaire on 2008-12-23
Does the same thing happen when you don't have the torrent client running?

I've known Network cards (and some routers!) to hang when using torrent clients due to the device not being able to handle the number of connections the torrent client accepts.

Try throttling the number of clients the torrent accepts to 30 or so connections per file, then see how the system runs.

---

### Post by eeliottheking on 2008-12-23
> **solitaire said:**
> Does the same thing happen when you don't have the torrent client running?

I've known Network cards (and some routers!) to hang when using torrent clients due to the device not being able to handle the number of connections the torrent client accepts.

Try throttling the number of clients the torrent accepts to 30 or so connections per file, then see how the system runs.

Yes, this dies regardless of what i have running when it dies.  It died 3 times yesterday while i was running pidgin, skype, and then playing a warsow match.  also, i had no problems leaving it running with a torrent client on 8.04, XP, or vista.

---

### Post by andguent on 2008-12-23
Ah! This is a wireless connection. That changes things. I reread your first post and you did mention that, I just missed it.

I have had very similar issues with my wireless card (would work for 30-60 minutes, and then stop responding). It turned out to be a driver issue. The fact that your issue has changed since before the upgrade lines up with this theory. Mine was quirky back during Feisty, and fixed itself an upgrade or two ago.

Can we have the output of the following commands please?
```

lspci|egrep -i 'network|ethernet|wireless'
lsmod

```

---

### Post by doas777 on 2008-12-23
My gut reaction is a power or thermal issue, but you may be hitting a max connections or whatever. I would check my system log, and failing any clues there, I would probably consider a reinstall, to determine if it's a hardware issue. a rather extreme action, I agree, but necessary if software solutions avail you not, and you suspect a physical problem.

good luck,
franklin

---

### Post by eeliottheking on 2008-12-23
those commans were run while my net was working.  here are the outputs:


lspci|egrep -i 'network|ethernet|wireless'
```
eeliottheking@eeliottheking-cpu:~$ lspci|egrep -i 'network|ethernet|wireless'
00:07.0 Bridge: nVidia Corporation MCP61 Ethernet (rev a2)

```


lsmod
```
eeliottheking@eeliottheking-cpu:~$ lsmod
Module                  Size  Used by
nls_iso8859_1          12032  2 
nls_cp437              13696  2 
vfat                   18816  2 
fat                    57376  1 vfat
ipv6                  263972  16 
af_packet              25728  4 
binfmt_misc            16904  1 
sco                    18308  2 
bridge                 56980  0 
stp                    10628  1 bridge
bnep                   20480  2 
rfcomm                 44432  0 
l2cap                  30464  6 bnep,rfcomm
bluetooth              61924  6 sco,bnep,rfcomm,l2cap
ppdev                  15620  0 
powernow_k8            22148  1 
cpufreq_conservative    14600  0 
cpufreq_stats          13188  0 
cpufreq_powersave       9856  0 
cpufreq_ondemand       14988  1 
freq_table             12672  3 powernow_k8,cpufreq_stats,cpufreq_ondemand
cpufreq_userspace      11396  0 
container              11520  0 
wmi                    14504  0 
sbs                    19464  0 
sbshc                  13440  1 sbs
video                  25104  0 
output                 11008  1 video
pci_slot               12552  0 
battery                18436  0 
iptable_filter         10752  0 
ip_tables              19600  1 iptable_filter
x_tables               22916  1 ip_tables
ac                     12292  0 
parport_pc             39204  0 
lp                     17156  0 
parport                42604  3 ppdev,parport_pc,lp
serio_raw              13444  0 
k8temp                 12416  0 
pcspkr                 10624  0 
psmouse                45200  0 
arc4                    9984  2 
ecb                    10880  2 
crypto_blkcipher       25476  1 ecb
nvidia               6900560  36 
agpgart                42184  1 nvidia
shpchp                 37908  0 
pci_hotplug            35236  1 shpchp
rt73usb                30464  0 
crc_itu_t              10112  1 rt73usb
rt2x00usb              18816  1 rt73usb
rt2x00lib              36224  2 rt73usb,rt2x00usb
rfkill                 17176  1 rt2x00lib
led_class              12164  1 rt2x00lib
mac80211              216820  2 rt2x00usb,rt2x00lib
evdev                  17696  8 
cfg80211               32392  2 rt2x00lib,mac80211
snd_usb_audio          89728  2 
snd_usb_lib            24192  1 snd_usb_audio
snd_hwdep              15236  1 snd_usb_audio
usblp                  20480  0 
snd_hda_intel         381488  3 
snd_pcm_oss            46848  0 
snd_mixer_oss          22784  1 snd_pcm_oss
snd_pcm                83204  3 snd_usb_audio,snd_hda_intel,snd_pcm_oss
snd_seq_dummy          10884  0 
snd_seq_oss            38528  0 
snd_seq_midi           14336  0 
snd_rawmidi            29824  2 snd_usb_lib,snd_seq_midi
snd_seq_midi_event     15232  2 snd_seq_oss,snd_seq_midi
snd_seq                57776  7 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              29960  2 snd_pcm,snd_seq
snd_seq_device         15116  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    63268  22 snd_usb_audio,snd_hwdep,snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              15328  1 snd
snd_page_alloc         16136  2 snd_hda_intel,snd_pcm
button                 14224  0 
i2c_nforce2            14468  0 
i2c_core               31892  2 nvidia,i2c_nforce2
ext3                  133384  1 
jbd                    55444  1 ext3
mbcache                16004  1 ext3
usbhid                 35840  0 
hid                    50560  1 usbhid
usb_storage            81728  1 
sbp2                   29324  1 
sd_mod                 42264  7 
crc_t10dif              9984  1 sd_mod
sr_mod                 22212  0 
cdrom                  43168  1 sr_mod
sg                     39732  0 
pata_acpi              12160  0 
libusual               27156  1 usb_storage
pata_amd               18692  0 
sata_nv                30600  2 
ata_generic            12932  0 
ohci1394               37936  1 
ohci_hcd               31888  0 
forcedeth              61328  0 
ehci_hcd               43276  0 
ieee1394               96324  2 sbp2,ohci1394
libata                177312  4 pata_acpi,pata_amd,sata_nv,ata_generic
scsi_mod              155212  6 usb_storage,sbp2,sd_mod,sr_mod,sg,libata
dock                   16656  1 libata
usbcore               148848  11 rt73usb,rt2x00usb,snd_usb_audio,snd_usb_lib,usblp,usbhid,usb_storage,libusual,ohci_hcd,ehci_hcd
thermal                23708  0 
processor              42156  2 powernow_k8,thermal
fan                    12548  0 
fbcon                  47648  0 
tileblit               10880  1 fbcon
font                   16512  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit
fuse                   60828  3 

```

---

### Post by andguent on 2008-12-24
I was expecting more output from your lspci command. Lets try a few more commands for info purposes:
```
hwinfo --wlan
hwinfo --netcard
hwinfo --network
ndiswrapper -l
```

---

### Post by andguent on 2008-12-24
I was expecting more output from your lspci command. Lets try a few more commands for info purposes:
```
hwinfo --wlan
hwinfo --netcard
hwinfo --network
ndiswrapper -l
```

---

### Post by eeliottheking on 2008-12-24
> **andguent said:**
> I was expecting more output from your lspci command. Lets try a few more commands for info purposes:
```
hwinfo --wlan
hwinfo --netcard
hwinfo --network
ndiswrapper -l
```

hwinfo --wlan
```
eeliottheking@eeliottheking-cpu:~$ hwinfo --wlan
26: USB 00.0: 0282 WLAN controller                              
  [Created at usb.122]
  UDI: /org/freedesktop/Hal/devices/usb_device_15a9_4_noserial_if0
  Unique ID: TVZz.qqG_K37CToE
  Parent ID: pBe4.OqydEZZ981A
  SysFS ID: /devices/pci0000:00/0000:00:02.1/usb2/2-9/2-9:1.0
  SysFS BusID: 2-9:1.0
  Hardware Class: network
  Model: "Ralink 802.11 bg WLAN"
  Hotplug: USB
  Vendor: usb 0x15a9 "Ralink"
  Device: usb 0x0004 "802.11 bg WLAN"
  Revision: "0.01"
  Driver: "rt73usb"
  Driver Modules: "rt73usb"
  Device File: wlan0
  Features: WLAN
  Speed: 480 Mbps
  HW Address: 00:16:44:a5:7d:47
  Link detected: yes
  WLAN channels: 1 2 3 4 5 6 7 8 9 10 11
  WLAN frequencies: 2.412 2.417 2.422 2.427 2.432 2.437 2.442 2.447 2.452 2.457 2.462
  WLAN encryption modes: WEP40 WEP104 TKIP CCMP
  WLAN authentication modes: open sharedkey wpa-psk wpa-eap
  Module Alias: "usb:v15A9p0004d0001dc00dsc00dp00icFFiscFFipFF"
  Driver Info #0:
    Driver Status: rt73usb is active
    Driver Activation Cmd: "modprobe rt73usb"
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #28 (Hub)

```



hwinfo --netcard
```
eeliottheking@eeliottheking-cpu:~$ hwinfo --netcard
16: PCI 07.0: 0200 Ethernet controller                          
  [Created at pci.310]
  UDI: /org/freedesktop/Hal/devices/pci_10de_3ef
  Unique ID: rBUF.CL2IZ2Rc7M9
  SysFS ID: /devices/pci0000:00/0000:00:07.0
  SysFS BusID: 0000:00:07.0
  Hardware Class: network
  Model: "nVidia MCP61 Ethernet"
  Vendor: pci 0x10de "nVidia Corporation"
  Device: pci 0x03ef "MCP61 Ethernet"
  SubVendor: pci 0x103c "Hewlett-Packard Company"
  SubDevice: pci 0x2a66 
  Revision: 0xa2
  Driver: "forcedeth"
  Driver Modules: "forcedeth"
  Device File: eth0
  Memory Range: 0xfe02d000-0xfe02dfff (rw,non-prefetchable)
  I/O Ports: 0xec00-0xec07 (rw)
  IRQ: 222 (78718 events)
  HW Address: 00:1f:c6:04:bb:f2
  Link detected: no
  Module Alias: "pci:v000010DEd000003EFsv0000103Csd00002A66bc06sc80i00"
  Driver Info #0:
    Driver Status: forcedeth is active
    Driver Activation Cmd: "modprobe forcedeth"
  Config Status: cfg=new, avail=yes, need=no, active=unknown

44: USB 00.0: 0282 WLAN controller
  [Created at usb.122]
  UDI: /org/freedesktop/Hal/devices/usb_device_15a9_4_noserial_if0
  Unique ID: TVZz.qqG_K37CToE
  Parent ID: pBe4.OqydEZZ981A
  SysFS ID: /devices/pci0000:00/0000:00:02.1/usb2/2-9/2-9:1.0
  SysFS BusID: 2-9:1.0
  Hardware Class: network
  Model: "Ralink 802.11 bg WLAN"
  Hotplug: USB
  Vendor: usb 0x15a9 "Ralink"
  Device: usb 0x0004 "802.11 bg WLAN"
  Revision: "0.01"
  Driver: "rt73usb"
  Driver Modules: "rt73usb"
  Device File: wlan0
  Features: WLAN
  Speed: 480 Mbps
  HW Address: 00:16:44:a5:7d:47
  Link detected: yes
  WLAN channels: 1 2 3 4 5 6 7 8 9 10 11
  WLAN frequencies: 2.412 2.417 2.422 2.427 2.432 2.437 2.442 2.447 2.452 2.457 2.462
  WLAN encryption modes: WEP40 WEP104 TKIP CCMP
  WLAN authentication modes: open sharedkey wpa-psk wpa-eap
  Module Alias: "usb:v15A9p0004d0001dc00dsc00dp00icFFiscFFipFF"
  Driver Info #0:
    Driver Status: rt73usb is active
    Driver Activation Cmd: "modprobe rt73usb"
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #46 (Hub)

```



hwinfo --network
```
eeliottheking@eeliottheking-cpu:~$ hwinfo --network
30: None 00.0: 10701 Ethernet                                   
  [Created at net.124]
  Unique ID: fLK9.ndpeucax6V1
  SysFS ID: /class/net/pan0
  Hardware Class: network interface
  Model: "Ethernet network interface"
  Driver: "bridge"
  Device File: pan0
  HW Address: c2:5a:57:4a:10:92
  Config Status: cfg=new, avail=yes, need=no, active=unknown

31: None 00.0: 1070a WLAN
  [Created at net.124]
  Unique ID: AYEt.QXn1l67RSa1
  Parent ID: TVZz.mPsrMh8eQx2
  SysFS ID: /class/net/wlan0
  SysFS Device Link: /devices/pci0000:00/0000:00:02.1/usb2/2-9/2-9:1.0
  Hardware Class: network interface
  Model: "WLAN network interface"
  Driver: "rt73usb"
  Driver Modules: "rt73usb"
  Device File: wlan0
  HW Address: 00:16:44:a5:7d:47
  Link detected: yes
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #26 (Unclassified device)

32: None 00.0: 10780 Network Interface
  [Created at net.124]
  Unique ID: agy+.GSopYcFr9cF
  SysFS ID: /class/net/wmaster0
  SysFS Device Link: /devices/pci0000:00/0000:00:02.1/usb2/2-9/2-9:1.0
  Hardware Class: network interface
  Model: "Network Interface"
  Driver: "rt73usb"
  Driver Modules: "rt73usb"
  Device File: wmaster0
  HW Address: 00:16:44:a5:7d:47
  Link detected: yes
  Config Status: cfg=new, avail=yes, need=no, active=unknown

33: None 00.0: 10701 Ethernet
  [Created at net.124]
  Unique ID: usDW.ndpeucax6V1
  Parent ID: rBUF.CL2IZ2Rc7M9
  SysFS ID: /class/net/eth0
  SysFS Device Link: /devices/pci0000:00/0000:00:07.0
  Hardware Class: network interface
  Model: "Ethernet network interface"
  Driver: "forcedeth"
  Driver Modules: "forcedeth"
  Device File: eth0
  HW Address: 00:1f:c6:04:bb:f2
  Link detected: no
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #10 (Ethernet controller)

34: None 00.0: 10700 Loopback
  [Created at net.124]
  Unique ID: ZsBS.GQNx7L4uPNA
  SysFS ID: /class/net/lo
  Hardware Class: network interface
  Model: "Loopback network interface"
  Device File: lo
  Link detected: yes
  Config Status: cfg=new, avail=yes, need=no, active=unknown

```



ndiswrapper -l

well, i was missing this application, so i installed it, and when i run it i get this error:
```
eeliottheking@eeliottheking-cpu:~$ ndiswrapper -l
Error: no ndiswrapper utils found!

```

---

### Post by eeliottheking on 2008-12-24
bump

---

### Post by Wolfhere on 2008-12-24
Try disabling IPv6 - kudos to Mark
[http://ubuntuforums.org/showthread.php?t=6841]("http://ubuntuforums.org/showthread.php?t=6841")

---

### Post by eeliottheking on 2008-12-25
i have disabled IPv6 and limited torrents to 30 connections max, yet this problem is still occurring.  any ideas?

---

### Post by eeliottheking on 2008-12-26
bump

---

### Post by doas777 on 2008-12-28
I try to never suggest a full reinstall to anyone, since no one learns anything, but sometimes it's called for. if the problem annoys you enough, then it's probably worthwhile. if you have your home on a separate partition, then a rebuild is extra easy.


another place you may want to look. is power management settings. something may be powering you nic down.

anyway, good luck!

---

### Post by sirebral on 2008-12-28
You might want to check to see if you have the most up to date driver for your wireless card:

[http://www.radarsync.com/driver/ralink](http://www.radarsync.com/driver/ralink)

---

