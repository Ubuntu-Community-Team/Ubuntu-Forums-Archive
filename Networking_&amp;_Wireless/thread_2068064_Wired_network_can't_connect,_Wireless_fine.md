---
title: "Wired network can't connect, Wireless fine"
date: 2012-10-08
forum: Networking &amp; Wireless
---

### Post by mattjones701 on 2012-10-08
Hey Guys, 

I've been having this weird problem for a few days now. My Laptop which I have recently installed Ubuntu 12.04 on is unable to connect to a wired network. Wireless is working perfect though.
I can see a network under the wired network menu called auto ethernet but it never connects. 

Here are some outputs. Not sure what you'll want so I'll just give some common ones to start.

```
ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:00:00:00:00:00  
          inet6 addr: fe80::200:ff:fe00:0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:8366 errors:0 dropped:0 overruns:0 frame:0
          TX packets:730 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:687974 (687.9 KB)  TX bytes:177927 (177.9 KB)
          Interrupt:48 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:698 errors:0 dropped:0 overruns:0 frame:0
          TX packets:698 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:293678 (293.6 KB)  TX bytes:293678 (293.6 KB)

wlan0     Link encap:Ethernet  HWaddr 00:21:6b:35:df:9c  
          inet addr:192.168.0.3  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::221:6bff:fe35:df9c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:31893 errors:0 dropped:0 overruns:0 frame:0
          TX packets:18077 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:22899778 (22.8 MB)  TX bytes:3302735 (3.3 MB)

```

```
lspci
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:01.0 PCI bridge: Intel Corporation Mobile 4 Series Chipset PCI Express Graphics Port (rev 07)
00:1a.0 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 03)
00:1c.5 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 (rev 03)
00:1d.0 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.3 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1d.7 USB controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801IBM/IEM (ICH9M/ICH9M-E) 4 port SATA Controller [AHCI mode] (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
00:1f.6 Signal processing controller: Intel Corporation 82801I (ICH9 Family) Thermal Subsystem (rev 03)
01:00.0 VGA compatible controller: NVIDIA Corporation G96 [GeForce 9600M GT] (rev a1)
02:00.0 Network controller: Intel Corporation PRO/Wireless 5100 AGN [Shiloh] Network Connection
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)
06:00.0 FireWire (IEEE 1394): JMicron Technology Corp. IEEE 1394 Host Controller
06:00.1 System peripheral: JMicron Technology Corp. SD/MMC Host Controller
06:00.2 SD Host controller: JMicron Technology Corp. Standard SD Host Controller
06:00.3 System peripheral: JMicron Technology Corp. MS Host Controller
06:00.4 System peripheral: JMicron Technology Corp. xD Host Controller

```

Thanks for any help. 

Matt

---

### Post by mattjones701 on 2012-10-08
No ideas?

---

### Post by varunendra on 2012-10-09
> **mattjones701 said:**
> ```

03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. [COLOR=Red]**RTL8111/8168B**[/COLOR] PCI Express Gigabit Ethernet controller (rev 02)
```
That chip is known for such problems. Although the default driver r8169 in latest kernels seems to work for many, there are still some for whom it doesn't.

Please try any of these:
1) Get the latest proprietary driver (r8168 ) from [realtek]("http://www.realtek.com/downloads/downloadsView.aspx?Langid=1&PNid=13&PFid=5&Level=5&Conn=4&DownTypeID=3&GetDown=false"), extract it and follow the instructions in it to install the driver.

Or,

2) Follow this post (replace "r8168-8.028.00.tar.bz2" with "r8168-8.032.00.tar.bz2" as it is the latest version) : [http://ubuntuforums.org/showthread.php?p=11733546](http://ubuntuforums.org/showthread.php?p=11733546)
(Try the "sudo ./autorun.sh" method first as mentioned at the bottom of the post).

You may wish to follow the rest of the posts in the above linked thread as they offer a variety of the same fix.

Please post back whether and which one worked for you.

---

### Post by mattjones701 on 2012-10-09
Hey thanks for your help. I'm glad I at least know what the problem is now. But unfortunately neither method worked for me. I first tried the autorun method and then your instructions. The only one that failed was modprobe -rfv r8169 saying there was no such module. But I thought this is not really a problem as we don't want it anyway?

Any other ideas for me to try? I would really love to be able to get this working.

---

### Post by varunendra on 2012-10-09
Since you first tried the autorun method, I would think that message is normal, since the autorun script must have unloaded, renamed and blacklisted the r8169 module.

Let us take a look at the current situation (run these commands after a reboot):
```
lspci -nnk | grep -iA2 net
lsmod
cat /etc/modprobe.d/blacklist.conf | grep r81
ls /etc/modprobe.d/blacklist*
```

---

### Post by mattjones701 on 2012-10-09
```
lspci -nnk | grep -iA2 net
02:00.0 Network controller [0280]: Intel Corporation PRO/Wireless 5100 AGN [Shiloh] Network Connection [8086:4237]
	Subsystem: Intel Corporation WiFi Link 5100 AGN [8086:1211]
	Kernel driver in use: iwlwifi
--
03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 02)
	Subsystem: Hewlett-Packard Company Device [103c:3603]
	Kernel driver in use: r8168

```

```
lsmod
Module                  Size  Used by
vesafb                 13844  1 
parport_pc             32866  0 
ppdev                  17113  0 
rfcomm                 47604  0 
bnep                   18281  2 
bluetooth             180104  10 rfcomm,bnep
snd_hda_codec_hdmi     32474  1 
snd_hda_codec_idt      70795  1 
arc4                   12529  2 
joydev                 17693  0 
hp_wmi                 18092  0 
sparse_keymap          13890  1 hp_wmi
snd_hda_intel          33773  3 
snd_hda_codec         127706  3 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
snd_pcm                97188  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
nvidia              12319264  53 
snd_seq_midi           13324  0 
ir_lirc_codec          12859  0 
lirc_dev               19204  1 ir_lirc_codec
snd_rawmidi            30748  1 snd_seq_midi
ir_mce_kbd_decoder     12777  0 
ir_sony_decoder        12510  0 
ir_jvc_decoder         12507  0 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29990  2 snd_pcm,snd_seq
uvcvideo               72627  0 
psmouse                97362  0 
serio_raw              13211  0 
videodev               98259  1 uvcvideo
ir_rc6_decoder         12507  0 
v4l2_compat_ioctl32    17128  1 videodev
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
rc_rc6_mce             12502  0 
ir_rc5_decoder         12507  0 
ir_nec_decoder         12507  0 
ene_ir                 18457  0 
jmb38x_ms              17646  0 
iwlwifi               396989  0 
memstick               16569  1 jmb38x_ms
rc_core                26412  10 ir_lirc_codec,ir_mce_kbd_decoder,ir_sony_decoder,ir_jvc_decoder,ir_rc6_decoder,rc_rc6_mce,ir_rc5_decoder,ir_nec_decoder,ene_ir
video                  19596  0 
mac80211              506816  1 iwlwifi
wmi                    19256  1 hp_wmi
hp_accel               25976  0 
lis3lv02d              19876  1 hp_accel
snd                    78855  16 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
input_polldev          13896  1 lis3lv02d
mac_hid                13253  0 
cfg80211              205544  2 iwlwifi,mac80211
soundcore              15091  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
r8168                 244911  0 
firewire_ohci          41000  0 
firewire_core          63558  1 firewire_ohci
crc_itu_t              12707  1 firewire_core
sdhci_pci              18826  0 
sdhci                  33205  1 sdhci_pci

```

```
cat /etc/modprobe.d/blacklist.conf | grep r81
blacklist r8169
blacklist r8169

```

```
ls /etc/modprobe.d/blacklist*
/etc/modprobe.d/blacklist-ath_pci.conf
/etc/modprobe.d/blacklist.conf
/etc/modprobe.d/blacklist-firewire.conf
/etc/modprobe.d/blacklist-framebuffer.conf
/etc/modprobe.d/blacklist-modem.conf
/etc/modprobe.d/blacklist-oss.conf
/etc/modprobe.d/blacklist-rare-network.conf
/etc/modprobe.d/blacklist-watchdog.conf

```

Thanks so much for helping :)

---

### Post by varunendra on 2012-10-09
You're welcome ! We do it because we enjoy it. :)

Everything seems to be in order as expected (except that the r8169 is blacklisted twice ;) which is not a problem).

Have you tried to connect after a reboot? If still not successful, please post the outputs of:
```
ifconfig -a
lshw -C network
dmesg | grep r81
```

---

### Post by mattjones701 on 2012-10-09
No luck with reboot. 

```
ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:00:00:00:00:00  
          inet6 addr: fe80::200:ff:fe00:0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4352 errors:0 dropped:0 overruns:0 frame:0
          TX packets:540 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:346656 (346.6 KB)  TX bytes:133976 (133.9 KB)
          Interrupt:48 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1042 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1042 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1249432 (1.2 MB)  TX bytes:1249432 (1.2 MB)

wlan0     Link encap:Ethernet  HWaddr 00:21:6b:35:df:9c  
          inet addr:192.168.0.3  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::221:6bff:fe35:df9c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:59922 errors:0 dropped:0 overruns:0 frame:0
          TX packets:106158 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:10308437 (10.3 MB)  TX bytes:9772740 (9.7 MB)

```

```
sudo lshw -C network
  *-network               
       description: Wireless interface
       product: PRO/Wireless 5100 AGN [Shiloh] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 00
       serial: 00:21:6b:35:df:9c
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlwifi driverversion=3.2.0-31-generic firmware=8.83.5.1 build 33692 ip=192.168.0.3 latency=0 link=yes multicast=yes wireless=IEEE 802.11abgn
       resources: irq:49 memory:de200000-de201fff
  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       size: 1Gbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8168 driverversion=8.032.00-NAPI duplex=full latency=0 link=yes multicast=yes port=twisted pair speed=1Gbit/s
       resources: irq:48 ioport:6000(size=256) memory:d4010000-d4010fff memory:d4000000-d400ffff memory:d4020000-d402ffff
```

```
dmesg | grep r81
[    0.000000] PERCPU: Embedded 28 pages/cpu @ffff88013fc00000 s83136 r8192 d23360 u524288
[    0.000000] pcpu-alloc: s83136 r8192 d23360 u524288 alloc=1*2097152
[    1.483413] r8168 Gigabit Ethernet driver 8.032.00-NAPI loaded
[    1.483444] r8168 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    1.483468] r8168 0000:03:00.0: setting latency timer to 64
[    1.483535] r8168 0000:03:00.0: irq 48 for MSI/MSI-X
[    1.509594] r8168: This product is covered by one or more of the following patents: US5,307,459, US5,434,872, US5,732,094, US6,570,884, US6,115,776, and US6,327,625.
[    1.509599] r8168  Copyright (C) 2012  Realtek NIC software team <nicfae@realtek.com> 
[   18.620200] r8168: eth0: link down
[   22.071681] r8168: eth0: link up
[   22.620016] r8168: eth0: link up

```

---

### Post by varunendra on 2012-10-09
> **mattjones701 said:**
> ```
sudo lshw -C network
  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
..
..
       configuration: autonegotiation=on broadcast=yes** driver=r8168 **driverversion=8.032.00-NAPI duplex=full latency=0 **link=yes** multicast=yes port=twisted pair **speed=1Gbit/s**
``````
dmesg | grep r81
[   22.071681] r8168: eth0: link up
[   22.620016] r8168: eth0: link up

```
again, everything seems as should be. So I think it is just a network configuration issue now.

Try disconnecting (or disabling if required) the wireless, then retry connecting via cable. Additionally, you may try
```
sudo dhclient
```
to manually attempt getting an IP from the dhcp on your network.

If that does not help, try these while wireless is disconnected and the cable is connected:
```
sudo ifconfig eth0 192.168.0.[COLOR=Red]**xx**[/COLOR]
sudo ifconfig eth0 down
sudo ifconfig eth0 up
```
(replace [COLOR=Red]**xx**[/COLOR] with a suitable number that you think is not in use as IP address by any other device on the network)

Then check if the IP address sticked:
```
ifconfig
```

I'm quite positive it is just a configuration issue now.

---

### Post by mattjones701 on 2012-10-09
Cool. I'll check these approaches tomorrow when I get a chance and I'll post back when I'm done. 

Thanks for all your help :)

---

### Post by mattjones701 on 2012-10-10
Still no success. Tried all of the above methods all resulting in the network trying to connect for a minute than getting a popup saying Wired Network Disconnected. ifconfig was the same as last time after each method. 

Any other ideas?

---

### Post by varunendra on 2012-10-10
> **mattjones701 said:**
> ifconfig was the same as last time after each method...meaning no IP address even after manually assigning one? That's strange!

Please retry with:
```
sudo ifconfig eth0 192.168.0.80
```
then post the outputs of:
```
ifconfig
ping -c 4 192.168.0.1
ping -c 4 192.168.0.3
```

---

### Post by mattjones701 on 2012-10-11
```
 sudo ifconfig eth0 192.168.0.80
matt@matt:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:00:00:00:00:00  
          inet addr:192.168.0.80  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::200:ff:fe00:0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:8782 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1334 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:748470 (748.4 KB)  TX bytes:146008 (146.0 KB)
          Interrupt:48 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:6637 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6637 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1916136 (1.9 MB)  TX bytes:1916136 (1.9 MB)

wlan0     Link encap:Ethernet  HWaddr 00:21:6b:35:df:9c  
          inet addr:192.168.0.3  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::221:6bff:fe35:df9c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2487239 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3940313 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:932102260 (932.1 MB)  TX bytes:1072597217 (1.0 GB)

```

```

matt@matt:~$ ping -c 4 192.168.0.1
connect: Network is unreachable
matt@matt:~$ ping -c 4 192.168.0.3
connect: Network is unreachable

```

---

### Post by varunendra on 2012-10-11
So the IP sticks, but still no communication. Try these now, only one at a time, with cable connected and wireless disabled (after each attempt, retry the 'ifconfig up/down' commands and see if you can ping your router or wifi access point):
[LIST=1]
[*]Edit your 'Wired Connection' *(click nm-applet > Edit Connections... > Double-click your connection listed under 'Wired' tab)* > Goto 'IPv6' tab > set 'Method' to 'Ignore' (it is safe to leave IPv6 as 'ignored' even if it doesn't help).
[*]Check your physical connection. Are any of the lights (usually orange/green) on the ethernet port lit? Are they stable or blinking? Usually one is stable (indicating a physical connection), and the other is blinking (indicating data transfer). If none is lit, or only one is lit but blinking, then it indicates a physical problem in the connection.
[*]Make sure the firewall is disabled: ```
sudo ufw status
```
[/LIST]
Right now, I can't think of anything else. Please check these and post back the status. If possible also try changing the cable you are using to connect with a fresh or tested one. Although the 'Link=yes' in lshw output suggest it 'should' be ok, but just to make sure...

---

### Post by surajkumarr on 2012-10-11
are you using a router. Get the IP of router, and try following commands
```

sudo ifconfig eth0 192.168.0.80 netmask 255.255.255.0
sudo route add default gw 192.168.0.xxx
ping 8.8.8.8

```
192.168.0.xxx is your router IP

---

### Post by elsontimana on 2012-10-12
vanuenda i saw your posts and i liked so much, and i thought that you can help me, my situation is this:

my  hard disk had a issue then i formated and i've installed ubuntu 12.04 LTS but when the installation end, wireless already not work the laptop reference is: hp g5000.

please help.

---

### Post by mattjones701 on 2012-10-13
> **varunendra said:**
> So the IP sticks, but still no communication. Try these now, only one at a time, with cable connected and wireless disabled (after each attempt, retry the 'ifconfig up/down' commands and see if you can ping your router or wifi access point):
[LIST=1]
[*]Edit your 'Wired Connection' *(click nm-applet > Edit Connections... > Double-click your connection listed under 'Wired' tab)* > Goto 'IPv6' tab > set 'Method' to 'Ignore' (it is safe to leave IPv6 as 'ignored' even if it doesn't help).
[*]Check your physical connection. Are any of the lights (usually orange/green) on the ethernet port lit? Are they stable or blinking? Usually one is stable (indicating a physical connection), and the other is blinking (indicating data transfer). If none is lit, or only one is lit but blinking, then it indicates a physical problem in the connection.
[*]Make sure the firewall is disabled: ```
sudo ufw status
```
[/LIST]
Right now, I can't think of anything else. Please check these and post back the status. If possible also try changing the cable you are using to connect with a fresh or tested one. Although the 'Link=yes' in lshw output suggest it 'should' be ok, but just to make sure...

Finally got around to trying these methods out. Nothing worked :(
Tried with a different cable still with same results. IPV6 is set to ignore. Firewall is set to inactive. And there is a steady Green light and a blinking orange one on the laptop connection. I'm plugging into a netgear n600 router/modem which another housemate is using for a windows pc and it works fine.

Thanks for all your help. Let me know if you have any other ideas?

---

### Post by varunendra on 2012-10-14
Hmm.. these kind of issues keep reminding me that it's a huge mistake to take things for granted in networking stuff!

Well.. at least the port lights confirm the physical connection status to be ok. But I wonder why that orange light is blinking if there is no communication between the router and laptop. You also had a considerable amount of transferred and received data packets (in ifconfig output) even when eth0 was not assigned any IP(v4) address. Although there hasn't been any large amount of data transfers so far, yet still considerable enough to make me suspicious if IPv6 is causing or adding to the problem. So let's first force-disable it by adding a few rules in sysctl file. Open it as super-user:
```
gksu gedit /etc/sysctl.conf
```
Then add the following lines at its end:
> # force-disable IPv6
net.ipv6.conf.all.disable_ipv6=1
net.ipv6.conf.default.disable_ipv6=1
net.ipv6.conf.lo.disable_ipv6=1
Proofread, save and close the file. Now apply these changes by-
```
sudo sysctl -p
```
Afterwards, another 'sounding-stupid' but 'may-help' thing to do is to power off your router > wait for a couple of minutes (usually 20-30 sec is enough though, to allow the router to completely unload its firmware from memory by discharging) > then power it on again. *[Although this weird exercise is related to some firmware incompatibility, especially between Linux kernel and some d-link routers, that possibly existed waayyyy.. back in the past, and I haven't seen it again for at least since Ubuntu 10.10]* Then on your laptop, (while the wireless is disabled) redo-
```
sudo ifconfig eth0 down
sudo ifconfig eth0 up
```

Then post back the overall current status:
```
ifconfig -a
nm-tool
sudo lshw -C network
lsmod | grep r81
dmesg | grep r81
cat /etc/NetworkManager/NetworkManager.conf
cat /etc/network/interfaces
cat /etc/nsswitch.conf
cat /var/lib/NetworkManager/NetworkManager.state
```

As a side note, can you boot from the live cd/usb and see how's the connection there? Usually it works even with the default r8169 driver.

If all of these turned out to be normal, then I guess the next thing to try would be to re-install the driver.

I hope you won't give it up yet as it is not usually such a big problem, and despite this one being unusual, we look close. (even those who have problem with r8169 driver, report 'intermittent' connections with it, not a complete black-out).

---

### Post by mattjones701 on 2012-10-14
Still no luck :( Tried everything but the live CD as I don't have it atm. Haven't reinstalled drivers either. Should we try a different/earlier one perhaps?

```
ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:00:00:00:00:00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:724 errors:0 dropped:0 overruns:0 frame:0
          TX packets:36 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:86827 (86.8 KB)  TX bytes:12312 (12.3 KB)
          Interrupt:48 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8533 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8533 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1922621 (1.9 MB)  TX bytes:1922621 (1.9 MB)

wlan0     Link encap:Ethernet  HWaddr 00:21:6b:35:df:9c  
          inet addr:192.168.0.3  Bcast:192.168.0.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:484205 errors:0 dropped:0 overruns:0 frame:0
          TX packets:572246 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:319035884 (319.0 MB)  TX bytes:250866784 (250.8 MB)

```

```
nm-tool

NetworkManager Tool

State: connected (global)

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8168
  State:             disconnected
  Default:           no
  HW Address:        00:00:00:00:00:00

  Capabilities:
    Carrier Detect:  yes
    Speed:           1000 Mb/s

  Wired Properties
    Carrier:         on


- Device: wlan0  [SlowNet] -----------------------------------------------------
  Type:              802.11 WiFi
  Driver:            iwlwifi
  State:             connected
  Default:           yes
  HW Address:        00:21:6B:35:DF:9C

  Capabilities:
    Speed:           150 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    Shiann:          Infra, 4C:60:DE:F2:3F:4E, Freq 2437 MHz, Rate 54 Mb/s, Strength 45 WPA2
    Hoot Hoot:       Infra, 74:44:01:4A:AF:3D, Freq 2412 MHz, Rate 54 Mb/s, Strength 37 WPA2
    BigPond4D1635:   Infra, 00:26:44:4D:16:35, Freq 2462 MHz, Rate 54 Mb/s, Strength 19 WPA WPA2
    *SlowNet:        Infra, 4C:60:DE:F2:3F:4F, Freq 5180 MHz, Rate 54 Mb/s, Strength 76 WPA2

  IPv4 Settings:
    Address:         192.168.0.3
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.1

    DNS:             192.168.0.1

```

```
sudo lshw -C network
  *-network               
       description: Wireless interface
       product: PRO/Wireless 5100 AGN [Shiloh] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 00
       serial: 00:21:6b:35:df:9c
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlwifi driverversion=3.2.0-31-generic firmware=8.83.5.1 build 33692 ip=192.168.0.3 latency=0 link=yes multicast=yes wireless=IEEE 802.11abgn
       resources: irq:49 memory:de200000-de201fff
  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       size: 1Gbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8168 driverversion=8.032.00-NAPI duplex=full latency=0 link=yes multicast=yes port=twisted pair speed=1Gbit/s
       resources: irq:48 ioport:6000(size=256) memory:d4010000-d4010fff memory:d4000000-d400ffff memory:d4020000-d402ffff

```

```
lsmod | grep rt8
dmesg | grep rt8

```

```
cat /etc/NetworkManager/NetworkManager.conf
[main]
plugins=ifupdown,keyfile
#dns=dnsmasq

no-auto-default=00:00:00:00:00:00,00:00:00:00:00:00

[ifupdown]
managed=false

```

```
cat /etc/network/interfaces
auto lo
iface lo inet loopback

```

```
cat /etc/nsswitch.conf
# /etc/nsswitch.conf
#
# Example configuration of GNU Name Service Switch functionality.
# If you have the `glibc-doc-reference' and `info' packages installed, try:
# `info libc "Name Service Switch"' for information about this file.

passwd:         compat
group:          compat
shadow:         compat

hosts:          files mdns4_minimal [NOTFOUND=return] dns mdns4
networks:       files

protocols:      db files
services:       db files
ethers:         db files
rpc:            db files

netgroup:       nis

```

```
cat /var/lib/NetworkManager/NetworkManager.state

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true

```

---

### Post by varunendra on 2012-10-14
I've been constantly ignoring one more thing, that is the state of your wlan0. All of your ifconfig outputs (and now nm-tool also) are showing it as 'UP' and connected. Did you try to disable it while trying to connect via ethernet?

Disable it physically if your laptop has a physical switch or a 'Fn+<some key>' combination for doing so. Since both connect to the same network, the system may not even try the eth0 interface while it 'sees' wlan0 as connected.

If you don't have a physical switch, nor a 'Fn' key combination to disable it, just clear the tick-mark from "Enable Wireless" section in nm-applet drop-down menu. This will 'soft-block' the wlan0 interface.


**PS:**
[COLOR="Red"]Correction -[/COLOR] it should have been 'r81' (not rt8 ) in both dmesg and lsmod commands. I'm correcting that in my original post above.

---

### Post by mattjones701 on 2012-10-14
Tried again with Wireless adapter turned off at laptop. No luck. I have been disconnecting the wireless when trying to connect beforehand. From now on I'll turn off properly but it seems to have made no difference.

---

### Post by varunendra on 2012-10-14
Are ifconfig and nm-tool are still showing wlan0 as 'UP' and 'Connected' respectively?

If so, then I'll have to consult someone who has much better experience than me. Perhaps I'm still missing something obvious.

---

### Post by firekage on 2012-10-14
> **mattjones701 said:**
> Tried again with Wireless adapter turned off at laptop. No luck. I have been disconnecting the wireless when trying to connect beforehand. From now on I'll turn off properly but it seems to have made no difference.

Try this:
> 
firekage@deusex:/etc/NetworkManager$ cat NetworkManager.conf
[main]
plugins=ifupdown,keyfile
dns=dnsmasq

[ifupdown]
**managed=true**
firekage@deusex:/etc/NetworkManager$also i have to have something like this in /etc/network/interfaces to work correctly:

> firekage@deusex:/etc/network$ cat interfaces 
# the loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
#auto eth0
#iface eth0 inet dhcp

# The secondary network interface
auto eth1
iface eth1 inet dhcp
Than reboot machine/service.

---

