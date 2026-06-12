---
title: "Upgrade to 12.04 - wireless doesn't work and crashes the whole network."
date: 2012-05-06
forum: Networking &amp; Wireless
---

### Post by wkcchampion on 2012-05-06
Hi, I've just upgraded to Ubuntu 12.04 (**EDIT: I know I mistyped in the title, sorry**) on my Asus EEEpc 1000H and the wireless doesn't work. It says it's connected to my home network named "Befyabe", but no web page can't be opened with either Chrome or Firefox. I also noticed that the whole network temporarily goes down when I attempt to connect with this computer!
* It works fine uses the Ethernet cable
* The network works as the mobile phones do connect
* I affirm that the network goes down because when the computer says "connection established", the other devices can't open any web page as well.

I launched all the commands listed in the Sticky thread, here are the results. Thanks for the help in advance.


```

marco@marco-1000H:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GSE Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GSE Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 02)
00:1c.3 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 4 (rev 02)
00:1d.0 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 02)
00:1d.1 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02)
00:1d.2 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02)
00:1d.3 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02)
00:1d.7 USB controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7-M Family) SATA Controller [IDE mode] (rev 02)
03:00.0 Ethernet controller: Atheros Communications Inc. AR8121/AR8113/AR8114 Gigabit or Fast Ethernet (rev b0)
marco@marco-1000H:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 04f2:b071 Chicony Electronics Co., Ltd 2.0M UVC Webcam / CNF7129
Bus 003 Device 002: ID 046d:c016 Logitech, Inc. Optical Wheel Mouse
marco@marco-1000H:~$ lspci -nn | grep 'Wireless Brand'
marco@marco-1000H:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:23:54:63:8a:8e  
          indirizzo inet:192.168.0.5  Bcast:192.168.0.255  Maschera:255.255.255.0
          indirizzo inet6: fe80::223:54ff:fe63:8a8e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:9065 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8677 errors:0 dropped:0 overruns:0 carrier:2
          collisioni:0 txqueuelen:1000 
          Byte RX:8506408 (8.5 MB)  Byte TX:1372111 (1.3 MB)
          Interrupt:43 

lo        Link encap:Loopback locale  
          indirizzo inet:127.0.0.1  Maschera:255.0.0.0
          indirizzo inet6: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:744 errors:0 dropped:0 overruns:0 frame:0
          TX packets:744 errors:0 dropped:0 overruns:0 carrier:0
          collisioni:0 txqueuelen:0 
          Byte RX:70150 (70.1 KB)  Byte TX:70150 (70.1 KB)

marco@marco-1000H:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

marco@marco-1000H:~$ iwconfig wlan0
wlan0     No such device

marco@marco-1000H:~$ lsmod
Module                  Size  Used by
dm_crypt               22528  0 
joydev                 17393  0 
arc4                   12473  0 
snd_hda_codec_realtek   174055  1 
snd_hda_intel          32765  3 
snd_hda_codec         109562  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80845  2 snd_hda_intel,snd_hda_codec
rt2800pci              18340  0 
snd_seq_midi           13132  0 
rt2800lib              53264  1 rt2800pci
snd_rawmidi            25424  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
crc_ccitt              12595  1 rt2800lib
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
rt2x00pci              14202  1 rt2800pci
rt2x00lib              48858  3 rt2800pci,rt2800lib,rt2x00pci
snd_timer              28931  2 snd_pcm,snd_seq
mac80211              436455  3 rt2800lib,rt2x00pci,rt2x00lib
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
uvcvideo               67203  0 
videodev               86588  1 uvcvideo
psmouse                87213  0 
cfg80211              178679  2 rt2x00lib,mac80211
serio_raw              13027  0 
snd                    62064  15 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
eeprom_93cx6           12653  1 rt2800pci
rfcomm                 38139  0 
bnep                   17830  2 
bluetooth             158438  10 bnep,rfcomm
parport_pc             32114  0 
ppdev                  12849  0 
soundcore              14635  1 snd
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
binfmt_misc            17292  1 
eeepc_laptop           19464  0 
sparse_keymap          13658  1 eeepc_laptop
mac_hid                13077  0 
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
usbhid                 41906  0 
hid                    77367  1 usbhid
atl1e                  32872  0 
i915                  414568  2 
drm_kms_helper         45466  1 i915
drm                   197692  3 i915,drm_kms_helper
i2c_algo_bit           13199  1 i915
video                  19068  1 i915
marco@marco-1000H:~$ lsmod | grep "wlan_module_name"
marco@marco-1000H:~$ sudo lshw -C network
[sudo] password for marco: 
Sorry, try again.
[sudo] password for marco: 
PCI (sysfs)  
  *-network               
       description: Ethernet interface
       product: AR8121/AR8113/AR8114 Gigabit or Fast Ethernet
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: b0
       serial: 00:23:54:63:8a:8e
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=ATL1E driverversion=1.0.0.7-NAPI duplex=full firmware=L1e ip=192.168.0.5 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:43 memory:fbfc0000-fbffffff ioport:ec00(size=128)
marco@marco-1000H:~$ 
marco@marco-1000H:~$ 


```

---

### Post by JoeRacette on 2012-05-07
Same problem w/eee 1000HA - 11.04 worked fine, 12.04 no wifi.

---

### Post by wkcchampion on 2012-05-07
JoeRacette, you should post the output of the commands u find in the Sticky.

---

### Post by marcoav on 2012-05-07
Hi,
I just upgrade from 11.10 to 12.04 and the wireless network is requesting the passcode every 3 minutes.
marco@HP-Mini-110-1020LA:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GSE Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GSE Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 02)
00:1d.0 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 02)
00:1d.1 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02)
00:1d.2 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02)
00:1d.3 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02)
00:1d.7 USB controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7-M Family) SATA Controller [IDE mode] (rev 02)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 02)
01:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g LP-PHY (rev 01)
02:00.0 Ethernet controller: Atheros Communications Inc. AR8132 Fast Ethernet (rev c0)

---

### Post by JoeRacette on 2012-05-08
Machine Brand and Model: ASUS eeePC 1000HA

Wireless Brand, Model and Wireless Chipset:

$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GSE Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GSE Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 02)
00:1c.3 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 4 (rev 02)
00:1d.0 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 02)
00:1d.1 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02)
00:1d.2 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02)
00:1d.3 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02)
00:1d.7 USB controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7-M Family) SATA Controller [IDE mode] (rev 02)
01:00.0 Ethernet controller: Atheros Communications Inc. AR242x / AR542x Wireless Network Adapter (PCI-Express) (rev 01)
03:00.0 Ethernet controller: Atheros Communications Inc. AR8121/AR8113/AR8114 Gigabit or Fast Ethernet (rev b0)


lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 058f:6335 Alcor Micro Corp. SD/MMC Card Reader
Bus 001 Device 004: ID 04f2:b071 Chicony Electronics Co., Ltd 2.0M UVC Webcam / CNF7129
Bus 002 Device 002: ID 046d:c52b Logitech, Inc. Unifying Receiver

information about the Wireless:
lspci -nn | grep 'Wireless'
01:00.0 Ethernet controller [0200]: Atheros Communications Inc. AR242x / AR542x Wireless Network Adapter (PCI-Express) [168c:001c] (rev 01)

check interface:

ifconfig
eth0      Link encap:Ethernet  HWaddr 00:23:54:47:f7:d1  
          inet addr:192.168.1.101  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::223:54ff:fe47:f7d1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:257468 errors:0 dropped:0 overruns:0 frame:0
          TX packets:132255 errors:0 dropped:0 overruns:0 carrier:6
          collisions:0 txqueuelen:1000 
          RX bytes:122702585 (122.7 MB)  TX bytes:25641473 (25.6 MB)
          Interrupt:44 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8403 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8403 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:742415 (742.4 KB)  TX bytes:742415 (742.4 KB)

wlan0     Link encap:Ethernet  HWaddr 00:22:43:4e:d5:b4  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


iwconfig wlan0
wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off

Check for modules:
lsmod

ath5k                 145127  0 
ath                    19387  1 ath5k
binfmt_misc            17292  1 
mac80211              436455  1 ath5k
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
cfg80211              178679  3 ath5k,ath,mac80211

Kernel boot messages:

dmesg | grep "ath5k"
[    8.151702] ath5k 0000:01:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    8.151729] ath5k 0000:01:00.0: setting latency timer to 64
[    8.151837] ath5k 0000:01:00.0: registered as 'phy0'
[    9.284991] Registered led device: ath5k-phy0::rx
[    9.285071] Registered led device: ath5k-phy0::tx
[    9.285103] ath5k phy0: Atheros AR2425 chip found (MAC: 0xe2, PHY: 0x70)
[46541.563682] ath5k phy0: failed to wakeup the MAC Chip
[46541.628599] ath5k 0000:01:00.0: PCI INT A disabled
[49445.461638] ath5k 0000:01:00.0: enabling device (0000 -> 0002)
[49445.461673] ath5k 0000:01:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[49445.461717] ath5k 0000:01:00.0: setting latency timer to 64
[49445.461917] ath5k 0000:01:00.0: registered as 'phy1'
[49445.984989] Registered led device: ath5k-phy1::rx
[49445.985246] Registered led device: ath5k-phy1::tx
[49445.985325] ath5k phy1: Atheros AR2425 chip found (MAC: 0xe2, PHY: 0x70)
[50803.975458] ath5k phy1: failed to wakeup the MAC Chip
[50804.096630] ath5k 0000:01:00.0: PCI INT A disabled
[212216.929583] ath5k 0000:01:00.0: enabling device (0000 -> 0002)
[212216.929619] ath5k 0000:01:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[212216.929662] ath5k 0000:01:00.0: setting latency timer to 64
[212216.929863] ath5k 0000:01:00.0: registered as 'phy2'
[212217.450283] Registered led device: ath5k-phy2::rx
[212217.450488] Registered led device: ath5k-phy2::tx
[212217.450575] ath5k phy2: Atheros AR2425 chip found (MAC: 0xe2, PHY: 0x70)

Network configuration:

sudo lshw -C network
PCI (sysfs)  
  *-network               
       description: Ethernet interface
       product: AR8121/AR8113/AR8114 Gigabit or Fast Ethernet
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: b0
       serial: 00:23:54:47:f7:d1
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=ATL1E driverversion=1.0.0.7-NAPI duplex=full firmware=L1e ip=192.168.1.101 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:44 memory:fbfc0000-fbffffff ioport:ec00(size=128)
  *-network
       description: Wireless interface
       product: AR242x / AR542x Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: wlan0
       version: 01
       serial: 00:22:43:4e:d5:b4
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath5k driverversion=3.2.0-24-generic firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11bg
       resources: irq:19 memory:f8000000-f800ffff

Scan for networks:
iwlist scan 
wlan0     No scan results

Ubuntu Version: 
lsb_release -d
Description:	Ubuntu 12.04 LTS

Kernel/architecture (including 32 vs. 64 bit): 

uname -mr
3.2.0-24-generic i686

Restarting the network:
sudo /etc/init.d/networking restart
 * Running /etc/init.d/networking restart is deprecated because it may not enable again some interfaces
 * Reconfiguring network interfaces...                                   [ OK ]

---

### Post by wkcchampion on 2012-05-09
Bump as the problem is still **unresolved **and quite a few people are experiencing it.

---

### Post by wkcchampion on 2012-05-13
Bump. Still **_unresolved_**! Can anybody help please?

---

### Post by steeldriver on 2012-05-13
> **wkcchampion said:**
> Bump. Still **_unresolved_**! Can anybody help please?

Hi, sorry but this thread has become VERY confusing, likely there are 3 different problems here

In your own case it looks like neither lspci/lsusb nor iwconfig find a  wireless device? if so I don't understand how you got it to connect at  all. However if you are getting connectivity issues on *other* devices  after connecting this one, my first thought would be an IP address  conflict (do you have static IP assignments anywhere?)

```

.
.
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7-M Family) SATA Controller [IDE mode] (rev 02) 
03:00.0 Ethernet controller: Atheros Communications Inc. AR8121/AR8113/AR8114 Gigabit or Fast Ethernet (rev b0) 
marco@marco-1000H:~$ lsusb 
.
.

``````

marco@marco-1000H:~$ iwconfig 
lo        no wireless extensions.  
eth0      no wireless extensions. 

```[Also, FWIW when the instructions say to use the command "lspci -nn|grep 'Wireless brand'" that does not mean the literal string 'Wireless brand' it means take the brand of the wireless device shown in the first lspci output and grep for that in the lspci -nn command. In your case the plain lspci didn't return any wireless device so the point is moot. Same applies to lsmod | grep "wlan_module_name".]

---

### Post by wkcchampion on 2012-05-14
> **steeldriver said:**
> Hi, sorry but this thread has become VERY confusing, likely there are 3 different problems here

In your own case it looks like neither lspci/lsusb nor iwconfig find a  wireless device? if so I don't understand how you got it to connect at  all. However if you are getting connectivity issues on *other* devices  after connecting this one, my first thought would be an IP address  conflict (do you have static IP assignments anywhere?)

```

.
.
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7-M Family) SATA Controller [IDE mode] (rev 02) 
03:00.0 Ethernet controller: Atheros Communications Inc. AR8121/AR8113/AR8114 Gigabit or Fast Ethernet (rev b0) 
marco@marco-1000H:~$ lsusb 
.
.

``````

marco@marco-1000H:~$ iwconfig 
lo        no wireless extensions.  
eth0      no wireless extensions. 

```[Also, FWIW when the instructions say to use the command "lspci -nn|grep 'Wireless brand'" that does not mean the literal string 'Wireless brand' it means take the brand of the wireless device shown in the first lspci output and grep for that in the lspci -nn command. In your case the plain lspci didn't return any wireless device so the point is moot. Same applies to lsmod | grep "wlan_module_name".]

Ok. What should I try then?
Thanks

---

### Post by steeldriver on 2012-05-14
Well a bit of searching suggests yours might be an eeepc specific issue

[http://ubuntuforums.org/showthread.php?p=9358368](http://ubuntuforums.org/showthread.php?p=9358368)

You can see if

```
rfkill list all
```comes up with anything - I would also check that wireless is enabled in the BIOS - if that doesn't work you can move on to the more exotic suggestions about init scripts

---

### Post by nothingspecial on 2012-05-14
> **wkcchampion said:**
> Hi, I've just upgraded to Ubuntu 12.04 (**EDIT: I know I mistyped in the title, sorry**) 

Fixed :)

---

### Post by wkcchampion on 2012-05-15
> **steeldriver said:**
> Well a bit of searching suggests yours might be an eeepc specific issue

[http://ubuntuforums.org/showthread.php?p=9358368](http://ubuntuforums.org/showthread.php?p=9358368)

You can see if

```
rfkill list all
```comes up with anything - I would also check that wireless is enabled in the BIOS - if that doesn't work you can move on to the more exotic suggestions about init scripts

Here it goes:

```

marco@marco-1000H:~$ rfkill list all
0: eeepc-wlan: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: eeepc-bluetooth: Bluetooth
	Soft blocked: yes
	Hard blocked: no
2: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no

```

---

### Post by cdoebbler on 2012-10-23
> **nothingspecial said:**
> Fixed :)

How was this fixed? 

I have the same problem with a Compaq/HP Mini 100c and can't seem to fix it wirh the work-arounds described here. Am I missing something.

---

