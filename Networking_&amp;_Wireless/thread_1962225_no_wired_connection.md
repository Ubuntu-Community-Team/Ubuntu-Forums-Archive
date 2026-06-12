---
title: "no wired connection"
date: 2012-04-20
forum: Networking &amp; Wireless
---

### Post by songhk on 2012-04-20
Dear all

I just bought new computer without OS. And I installed Ubuntu 11.10 (64 bit). Everything is okay except wired connection. 
Computer tried to get wired connection -> failed -> retried -> failed -> retired -> failed ... failed. 
There is no wireless card at my computer. 

I tried to fix this problem based on other postings, but I couldn't. I need comments. 

What I did are 
First, 
wired connection -> IPv4 setting: Automatic(DHCP), IPv6 setting (Ignore)
; I got similar problems, and this method worked well at my laptop. But this time it doesn't work for desktop PC. 

Second, 
I downloaded the driver for RTL8101E/RTL8102E Eternet controller, installed it, and disabled R8169. Rebooted, but it didn't work. 

Here are some commands. 
I don't know why eth0 doesn't have IP address as follows. 
inet addr: ***  Bcast:***  Mask:***

Thanks.


******************************************************
1. ifconfig
eth0      Link encap:Ethernet  HWaddr 10:78:d2:21:83:6b  
          inet6 addr: fe80::1278:d2ff:fe21:836b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1450 errors:0 dropped:0 overruns:0 frame:0
          TX packets:49 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:96213 (96.2 KB)  TX bytes:12739 (12.7 KB)
          Interrupt:16 Base address:0x4000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:96 errors:0 dropped:0 overruns:0 frame:0
          TX packets:96 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:7584 (7.5 KB)  TX bytes:7584 (7.5 KB)



2. lspci -nnk | grep -iA2 net
04:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 05)
	Subsystem: Elitegroup Computer Systems Device [1019:8105]
	Kernel driver in use: r8101

3. lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 IntRTL8101E/RTL8102Eel Corp. Integrated Rate Matching Hub
Bus 002 Device 003: ID 03f0:0f0c Hewlett-Packard Wireless Keyboard and Optical Mouse receiver
Bus 001 Device 003: ID 0951:160b Kingston Technology 

4. lsmod
Module                  Size  Used by
nls_iso8859_1          12713  1 
nls_cp437              16991  1 
vfat                   17585  1 
fat                    61475  1 vfat
usb_storage            57901  1 
uas                    18027  0 
parport_pc             36962  0 
ppdev                  17113  0 
bnep                   18436  2 
rfcomm                 47946  0 
bluetooth             166112  10 bnep,rfcomm
snd_hda_codec_hdmi     32040  1 RTL8101E/RTL8102E
snd_hda_codec_realtek   330769  1 
binfmt_misc            17540  1 
usbhid                 47198  0 
hid                    95463  1 usbhid
snd_hda_intel          33390  2 
snd_hda_codec         104802  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
snd_pcm                96755  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30547  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29991  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    68266  14 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse                73882  0 
wmi                    19256  0 
i915                  566711  3 
serio_raw              13166  0 
soundcore              12680  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
mei                    41480  0 
drm_kms_helper         42558  1 i915
drm                   236330  4 i915,drm_kms_helper
i2c_algo_bit           13423  1 i915
video                  19412  1 i915
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
r8101                  95550  0 


5. cat /etc/network/interfaces
auto lo
iface lo inet loopback

6. iwconfig
lo        no wireless extensions.
eth0      no wireless extensions.


7. cat /var/lib/NetworkManager/NetworkManager.state 
[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true

8. route -n 
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface

9. lshw -c network 
  *-network               
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: 05
       serial: 10:78:d2:21:83:6b
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8101 driverversion=1.021.00-NAPI duplex=full latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:16 ioport:e000(size=256) memory:d0004000-d0004fff memory:d0000000-d0003fff

---

### Post by wildmanne39 on 2012-04-20
Hi, from what I have researched you need the r8169 driver so you need to start by disabling the r8101 and loading the r8169.
Thanks

---

### Post by songhk on 2012-04-21
wildmanne39

I disabled r8101, and I loaded r8169, but got an error message as follows. 

ifconfig eth0 up:
error while getting interface flags:  device not found

So I just reinstalled Ubuntu 11.10. It has r8169 module. 

$lspci -nnk | grep -iA2 net
04:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 05)
Subsystem: Elitegroup Computer Systems Device [1019:8105]
Kernel driver in use: r8169

But the problem is the same. 
Is this related to hardware problem?
I just bought this, so I think this is not hardward problem.

---

### Post by praseodym on 2012-04-21
How do you want to connect? Router, Modem, or both?

---

### Post by songhk on 2012-04-21
praseodym

My computer is connected to UBee DDM3513 Modem at my home.

---

### Post by songhk on 2012-04-21
wildmanne39

I want to add one. 
You're right. I checked my laptop. (ubuntu 11.10, 64bit)
My configuration is the same as you mentioned. 

My laptop 
$lshw -c network
*-network
product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller

$lspci -nnk | grep -iA2 net
Kernel driver in use: r8169

---

### Post by praseodym on 2012-04-21
So, you got a login and PW from your ISP, right? Add these infos in "DSL" in the network-manager applet.

---

### Post by songhk on 2012-04-21
praseodym

I added the infos about ID, PD from ISP provider to DSL in the network-manager applet.

DSL connection 1 -> DSL -> 
username: ***, Service: ***, Password: ***

Now I can see DSL connection with wired connection. 
But the problem is the same. 

And I think my Eternet card is okay because a light is blinking when I turned on my computer.

---

### Post by songhk on 2012-04-22
From another posting ([http://ubuntuforums.org/showthread.php?t=1879744](http://ubuntuforums.org/showthread.php?t=1879744)), it looks like the problem comes from 
the motherboard with Z68 chipsets and their network driver (r8169 for mycomputer). 

My computer's motherboard is INTEL LGA1155 DDR3 SATA2 PCIe X16 MBoard, and I think it has Z68 chipsets.

I will search the solution continuously.
God please help me. I want to use Internet at my computer.

---

### Post by praseodym on 2012-04-22
Is there any setup in "cable connection"? If yes, remove it and un-tick "connect automatically".

---

### Post by songhk on 2012-04-22
praseodym

I unticked "connect automatically", but still I can't see wired connection.
And also ping doesn't work.

---

### Post by songhk on 2012-04-23
Finally I solved this problem. Someone helped me. 

1. R8169 driver is correct for Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller.

2. Check the Ethernet connection.  
If the light on Ethernet card is blinking, and ping 128.0.0.1 works, this is not hardware problem. 

3. Check the Ethernet card one more ( disconnect, and connect)
   Refresh the setting for wired connection as follows. 
 Network manager -> Edit connections ->  click 'wired connection'  -> delete. then -> add new one. 

  IPv4setting:
  Automatic (DHCP) 
  Check 'Require IPv4 addressing for this connection to complete 
  
  IPv6setting: Ignore

4. Reset modem 
5. Restart computer


The problem was related to network setting, refresh the setting for wired connection. 
 
Thanks for reply. 

I am happy, and I like Ubuntu.

---

