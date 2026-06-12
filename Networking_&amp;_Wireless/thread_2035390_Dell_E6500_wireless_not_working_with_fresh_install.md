---
title: "Dell E6500 wireless not working with fresh installation of Ubuntu 12.04"
date: 2012-07-30
forum: Networking &amp; Wireless
---

### Post by nprakash on 2012-07-30
Hi Team,

I am quite new to Ubuntu. I was using ubuntu since version 8.04 But after fresh installation of ubuntu 12.04, I am not able to connect to wireless internet. It shows that it is available with very low signal. 

================================================
cat /etc/lsb-release; uname -a
-------------------------
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.04
DISTRIB_CODENAME=precise
DISTRIB_DESCRIPTION="Ubuntu 12.04 LTS"
Linux Chunmun 3.2.0-27-generic-pae #43-Ubuntu SMP Fri Jul 6 15:06:05 UTC 2012 i686 i686 i386 GNU/Linux

========================================================

lspci -nnk | grep -iA2 net
-------------------------
00:19.0 Ethernet controller [0200]: Intel Corporation 82567LM Gigabit Network Connection [8086:10f5] (rev 03)
	Subsystem: Dell Device [1028:024f]
	Kernel driver in use: e1000e
--
0c:00.0 Network controller [0280]: Intel Corporation Ultimate N WiFi Link 5300 [8086:4235]
	Subsystem: Intel Corporation Device [8086:1121]
	Kernel driver in use: iwlwifi

========================================================

lsmod
-------------------------
Module                  Size  Used by
ipt_MASQUERADE         12663  0 
xt_state               12514  0 
ipt_REJECT             12512  0 
xt_tcpudp              12531  0 
iptable_filter         12706  0 
nf_nat_h323            12749  0 
nf_conntrack_h323      52412  1 nf_nat_h323
nf_nat_pptp            12536  0 
nf_conntrack_pptp      13553  1 nf_nat_pptp
nf_conntrack_proto_gre    13395  1 nf_conntrack_pptp
nf_nat_proto_gre       12671  1 nf_nat_pptp
nf_nat_tftp            12420  0 
nf_conntrack_tftp      12817  1 nf_nat_tftp
nf_nat_sip             16921  0 
nf_conntrack_sip       24749  1 nf_nat_sip
nf_nat_irc             12542  0 
nf_conntrack_irc       13138  1 nf_nat_irc
nf_nat_ftp             12595  0 
nf_conntrack_ftp       13183  1 nf_nat_ftp
iptable_nat            13016  0 
nf_nat                 24959  9 ipt_MASQUERADE,nf_nat_h323,nf_nat_pptp,nf_nat_proto_gre,nf_nat_tftp,nf_nat_sip,nf_nat_irc,nf_nat_ftp,iptable_nat
nf_conntrack_ipv4      19084  3 iptable_nat,nf_nat
nf_conntrack           73847  18 ipt_MASQUERADE,xt_state,nf_nat_h323,nf_conntrack_h323,nf_nat_pptp,nf_conntrack_pptp,nf_conntrack_proto_gre,nf_nat_tftp,nf_conntrack_tftp,nf_nat_sip,nf_conntrack_sip,nf_nat_irc,nf_conntrack_irc,nf_nat_ftp,nf_conntrack_ftp,iptable_nat,nf_nat,nf_conntrack_ipv4
nf_defrag_ipv4         12649  1 nf_conntrack_ipv4
ip_tables              18106  2 iptable_filter,iptable_nat
x_tables               21974  7 ipt_MASQUERADE,xt_state,ipt_REJECT,xt_tcpudp,iptable_filter,iptable_nat,ip_tables
bnep                   17830  2 
rfcomm                 38139  12 
parport_pc             32114  0 
ppdev                  12849  0 
vesafb                 13516  1 
joydev                 17393  0 
btusb                  17912  2 
bluetooth             158438  23 bnep,rfcomm,btusb
snd_hda_codec_idt      60251  1 
arc4                   12473  2 
pcmcia                 39791  0 
snd_hda_intel          32765  3 
snd_hda_codec         109562  2 snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80845  2 snd_hda_intel,snd_hda_codec
dell_wmi               12601  0 
sparse_keymap          13658  1 dell_wmi
snd_seq_midi           13132  0 
yenta_socket           27465  0 
pcmcia_rsrc            18367  1 yenta_socket
pcmcia_core            21511  3 pcmcia,yenta_socket,pcmcia_rsrc
snd_rawmidi            25424  1 snd_seq_midi
nvidia               7098356  38 
dell_laptop            17767  0 
snd_seq_midi_event     14475  1 snd_seq_midi
dcdbas                 14098  1 dell_laptop
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28931  2 snd_pcm,snd_seq
iwlwifi               292030  0 
psmouse                72919  0 
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
serio_raw              13027  0 
mac80211              436455  1 iwlwifi
snd                    62064  15 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
uvcvideo               67203  0 
videodev               86588  1 uvcvideo
cfg80211              178679  2 iwlwifi,mac80211
soundcore              14635  1 snd
snd_page_alloc         14108  2 snd_hda_intel,snd_pcm
mac_hid                13077  0 
wmi                    18744  1 dell_wmi
video                  19068  0 
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
usbhid                 41906  0 
hid                    77367  1 usbhid
sdhci_pci              18324  0 
sdhci                  28241  1 sdhci_pci
firewire_ohci          40172  0 
firewire_core          56906  1 firewire_ohci
crc_itu_t              12627  1 firewire_core
e1000e                140005  0 

======================================================

lspci -nnk
---------------------------------------
00:00.0 Host bridge [0600]: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub [8086:2a40] (rev 07)
	Subsystem: Dell Device [1028:024f]
00:01.0 PCI bridge [0604]: Intel Corporation Mobile 4 Series Chipset PCI Express Graphics Port [8086:2a41] (rev 07)
	Kernel driver in use: pcieport
	Kernel modules: shpchp
00:19.0 Ethernet controller [0200]: Intel Corporation 82567LM Gigabit Network Connection [8086:10f5] (rev 03)
	Subsystem: Dell Device [1028:024f]
	Kernel driver in use: e1000e
	Kernel modules: e1000e
00:1a.0 USB controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 [8086:2937] (rev 03)
	Subsystem: Dell Device [1028:024f]
	Kernel driver in use: uhci_hcd
00:1a.1 USB controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 [8086:2938] (rev 03)
	Subsystem: Dell Device [1028:024f]
	Kernel driver in use: uhci_hcd
00:1a.2 USB controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 [8086:2939] (rev 03)
	Subsystem: Dell Device [1028:024f]
	Kernel driver in use: uhci_hcd
00:1a.7 USB controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 [8086:293c] (rev 03)
	Subsystem: Dell Device [1028:024f]
	Kernel driver in use: ehci_hcd
00:1b.0 Audio device [0403]: Intel Corporation 82801I (ICH9 Family) HD Audio Controller [8086:293e] (rev 03)
	Subsystem: Dell Device [1028:024f]
	Kernel driver in use: snd_hda_intel
	Kernel modules: snd-hda-intel
00:1c.0 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 [8086:2940] (rev 03)
	Kernel driver in use: pcieport
	Kernel modules: shpchp
00:1c.1 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 [8086:2942] (rev 03)
	Kernel driver in use: pcieport
	Kernel modules: shpchp
00:1c.2 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 [8086:2944] (rev 03)
	Kernel driver in use: pcieport
	Kernel modules: shpchp
00:1c.3 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 [8086:2946] (rev 03)
	Kernel driver in use: pcieport
	Kernel modules: shpchp
00:1d.0 USB controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 [8086:2934] (rev 03)
	Subsystem: Dell Device [1028:024f]
	Kernel driver in use: uhci_hcd
00:1d.1 USB controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 [8086:2935] (rev 03)
	Subsystem: Dell Device [1028:024f]
	Kernel driver in use: uhci_hcd
00:1d.2 USB controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 [8086:2936] (rev 03)
	Subsystem: Dell Device [1028:024f]
	Kernel driver in use: uhci_hcd
00:1d.7 USB controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 [8086:293a] (rev 03)
	Subsystem: Dell Device [1028:024f]
	Kernel driver in use: ehci_hcd
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev 93)
00:1f.0 ISA bridge [0601]: Intel Corporation ICH9M-E LPC Interface Controller [8086:2917] (rev 03)
	Subsystem: Dell Device [1028:024f]
	Kernel modules: iTCO_wdt
00:1f.2 RAID bus controller [0104]: Intel Corporation 82801 Mobile SATA Controller [RAID mode] [8086:282a] (rev 03)
	Subsystem: Dell Device [1028:024f]
	Kernel driver in use: ahci
00:1f.3 SMBus [0c05]: Intel Corporation 82801I (ICH9 Family) SMBus Controller [8086:2930] (rev 03)
	Subsystem: Dell Device [1028:024f]
	Kernel modules: i2c-i801
01:00.0 VGA compatible controller [0300]: NVIDIA Corporation G98M [Quadro NVS 160M] [10de:06eb] (rev a1)
	Subsystem: Dell Device [1028:024f]
	Kernel driver in use: nvidia
	Kernel modules: nvidia_173, nouveau, nvidiafb
03:01.0 CardBus bridge [0607]: Ricoh Co Ltd RL5c476 II [1180:0476] (rev ba)
	Subsystem: Dell Device [1028:024f]
	Kernel driver in use: yenta_cardbus
	Kernel modules: yenta_socket
03:01.1 FireWire (IEEE 1394) [0c00]: Ricoh Co Ltd R5C832 IEEE 1394 Controller [1180:0832] (rev 04)
	Subsystem: Dell Device [1028:024f]
	Kernel driver in use: firewire_ohci
	Kernel modules: firewire-ohci
03:01.2 SD Host controller [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter [1180:0822] (rev 21)
	Subsystem: Dell Device [1028:024f]
	Kernel driver in use: sdhci-pci
	Kernel modules: sdhci-pci
0c:00.0 Network controller [0280]: Intel Corporation Ultimate N WiFi Link 5300 [8086:4235]
	Subsystem: Intel Corporation Device [8086:1121]
	Kernel driver in use: iwlwifi
	Kernel modules: iwlwifi


======================================================
lsusb
-------------------------------------------
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 0c45:63f0 Microdia 
Bus 003 Device 002: ID 0a5c:4500 Broadcom Corp. BCM2046B1 USB 2.0 Hub (part of BCM2046 Bluetooth)
Bus 005 Device 002: ID 0a5c:5801 Broadcom Corp. BCM5880 Secure Applications Processor with fingerprint swipe sensor
Bus 003 Device 003: ID 413c:8157 Dell Computer Corp. Integrated Keyboard
Bus 003 Device 004: ID 413c:8158 Dell Computer Corp. Integrated Touchpad / Trackstick
Bus 003 Device 005: ID 413c:8156 Dell Computer Corp. Wireless 370 Bluetooth Mini-card



======================================================

 iwconfig
--------------------------------
lo        no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
eth0      no wireless extensions.

======================================================
rfkill list
------------------------
0: dell-wifi: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: dell-bluetooth: Bluetooth
	Soft blocked: no
	Hard blocked: no
2: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
3: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no


=======================================================




It's my humble request please help me immediately.

Thanks & Regards,
Nprakash

---

### Post by praseodym on 2012-07-30
First:

Uninstall the firewall and the iptables:

```
sudo apt-get remove --purge ufw gufw
sudo iptables -t filter -n -L -v
sudo iptables -F
sudo iptables -X
```

Second:

Deactivate the N-mode of the driver (Bug):

```
echo "options iwlwifi 11n_disable=1" | sudo tee /etc/modprobe.d/iwlwifi.conf
sudo modprobe -rfv iwlwifi
sudo modprobe -v iwlwifi
```

Third:

Remove (not edit) your wireless profile and create a new one in "infrastructure"-mode.

Fourth:

Check:
```

iwconfig
sudo iwlist scan
iwlist chan
rfkill list
dmesg | egrep "iwl|country|dell"
```

---

### Post by nprakash on 2012-07-31
> **praseodym said:**
> First:

Uninstall the firewall and the iptables:

```
sudo apt-get remove --purge ufw gufw
sudo iptables -t filter -n -L -v
sudo iptables -F
sudo iptables -X
```

Second:

Deactivate the N-mode of the driver (Bug):

```
echo "options iwlwifi 11n_disable=1" | sudo tee /etc/modprobe.d/iwlwifi.conf
sudo modprobe -rfv iwlwifi
sudo modprobe -v iwlwifi
```

Third:

Remove (not edit) your wireless profile and create a new one in "infrastructure"-mode.

Fourth:

Check:
```

iwconfig
sudo iwlist scan
iwlist chan
rfkill list
dmesg | egrep "iwl|country|dell"
```
Dear Sir,

Thanks for your quick response.  

Sorry to say it failed to resolve my problem. Also my laptop network is displaying very low frequency  and is not connecting wireless still. I have another official windows Vista laptop and it is working fine with wireless connection.

============================================================
wconfig
-----------------------
No command 'wconfig' found, did you mean:
 Command 'fconfig' from package 'redboot-tools' (main)
 Command 'lwconfig' from package 'likewise-open' (main)
 Command 'zconfig' from package 'python-zconfig' (universe)
 Command 'iwconfig' from package 'wireless-tools' (main)
 Command 'vconfig' from package 'vlan' (main)
 Command 'mconfig' from package 'mono-devel' (main)
wconfig: command not found

============================================================

sudo iwlist scan
-------------------------------------------------
lo        Interface doesn't support scanning.

wlan0     Interface doesn't support scanning : Device or resource busy

eth0      Interface doesn't support scanning.
============================================================

iwlist chan
--------------------------------
lo        no frequency information.

wlan0     32 channels in total; available frequencies :
          Channel 01 : 2.412 GHz
          Channel 02 : 2.417 GHz
          Channel 03 : 2.422 GHz
          Channel 04 : 2.427 GHz
          Channel 05 : 2.432 GHz
          Channel 06 : 2.437 GHz
          Channel 07 : 2.442 GHz
          Channel 08 : 2.447 GHz
          Channel 09 : 2.452 GHz
          Channel 10 : 2.457 GHz
          Channel 11 : 2.462 GHz
          Channel 12 : 2.467 GHz
          Channel 13 : 2.472 GHz
          Channel 36 : 5.18 GHz
          Channel 40 : 5.2 GHz
          Channel 44 : 5.22 GHz
          Channel 48 : 5.24 GHz
          Channel 52 : 5.26 GHz
          Channel 56 : 5.28 GHz
          Channel 60 : 5.3 GHz
          Channel 64 : 5.32 GHz
          Channel 100 : 5.5 GHz
          Channel 104 : 5.52 GHz
          Channel 108 : 5.54 GHz
          Channel 112 : 5.56 GHz
          Channel 116 : 5.58 GHz
          Channel 120 : 5.6 GHz
          Channel 124 : 5.62 GHz
          Channel 128 : 5.64 GHz
          Channel 132 : 5.66 GHz
          Channel 136 : 5.68 GHz
          Channel 140 : 5.7 GHz
eth0      no frequency information.
============================================================

dmesg | egrep "iwl|country"
------------------------------------------------------
[    8.621385] iwlwifi 0000:0c:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    8.621393] iwlwifi 0000:0c:00.0: setting latency timer to 64
[    8.621414] iwlwifi 0000:0c:00.0: pci_resource_len = 0x00002000
[    8.621416] iwlwifi 0000:0c:00.0: pci_resource_base = f87ec000
[    8.621418] iwlwifi 0000:0c:00.0: HW Revision ID = 0x0
[    8.621498] iwlwifi 0000:0c:00.0: irq 47 for MSI/MSI-X
[    8.621532] iwlwifi 0000:0c:00.0: Detected Intel(R) Ultimate N WiFi Link 5300 AGN, REV=0x24
[    8.621587] iwlwifi 0000:0c:00.0: L1 Enabled; Disabling L0S
[    8.643259] iwlwifi 0000:0c:00.0: device EEPROM VER=0x120, CALIB=0x4
[    8.643261] iwlwifi 0000:0c:00.0: Device SKU: 0Xf0
[    8.643333] iwlwifi 0000:0c:00.0: Tunable channels: 13 802.11bg, 24 802.11a channels
[    9.379107] iwlwifi 0000:0c:00.0: loaded firmware version 8.83.5.1 build 33692
[    9.558488] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'
[   16.042384] iwlwifi 0000:0c:00.0: L1 Enabled; Disabling L0S
[   16.045389] iwlwifi 0000:0c:00.0: Radio type=0x0-0x2-0x0
[   16.196587] iwlwifi 0000:0c:00.0: L1 Enabled; Disabling L0S
[   16.199591] iwlwifi 0000:0c:00.0: Radio type=0x0-0x2-0x0

=======================================================================

---

### Post by praseodym on 2012-07-31
Try to deactivate the N-mode in your router, a+b+g only.

Check:

```
iwconfig
rfkill list
```

---

### Post by nprakash on 2012-08-02
Dear Sir,

I am not able to deactivate the N-mode in my router, a+b+g only. However I had executed the commands.
============================================
 iwconfig
-------------------
lo        no wireless extensions.

wlan0     IEEE 802.11abg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
eth0      no wireless extensions.
============================================
rfkill list
--------------------
0: dell-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: dell-bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
3: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
5: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

Please do suggest me how to deactivate the N-mode router a+b+g and my problem of wireless is still not resolved.

Kindly let me know if I can have a online chat with you using some desktop sharing to resolve this.

Thanks & Regards,
Nitish Prakash
Current Location: Kolkata, India

---

### Post by praseodym on 2012-08-02
Try to unload the module dell_wmi:

```
sudo rmmod dell_wmi
```

---

### Post by nprakash on 2012-08-03
No it didn't helped. 

Regards,
Nitish

---

### Post by praseodym on 2012-08-03
Unload "dell_laptop" and reload the other:
> sudo rmmod dell_laptop
sudm modprobe dell_wmi

---

### Post by nprakash on 2012-08-03
Below is the response of the code.

nprakash@Chunmun:~$  sudo rmmod dell_laptop
[sudo] password for nprakash: 
ERROR: Module dell_laptop does not exist in /proc/modules
nprakash@Chunmun:~$  sudo modprobe dell_wmi 


can you have a desktop sharing session now to resolve my problem. It's seems that I am real stuck after 5 years using Ubuntu.

Regards,
Nitish

---

### Post by nprakash on 2012-08-05
Hi,

Kindly let me know if I can still have any options to get my problem ( wireless connection not working) resolved.

---

### Post by praseodym on 2012-08-05
Try to blacklist the module:

```
echo "blacklist dell_laptop" | sudo tee /etc/modprobe.d/blacklist-dell.conf
```
and reboot. You can easiliy remove this file if is not working. Additionally/alternatively, try this parameter:

```
sudo rmmod dell_wmi
sudo modprobe -v dell_wmi wireless=1
```
This is temporarily, if it works make it permanent with:

```
echo "options dell_wmi wireless=1" | sudo tee /etc/modprobe.d/dell.conf
```

---

### Post by nprakash on 2012-08-06
Dear Sir, 

I 1st executed the below code and reboot my machine. It didn't worked.

echo "blacklist dell_laptop" | sudo tee /etc/modprobe.d/blacklist-dell.conf

Then I had deleted the file. Now I am able to connect the wireless only if my laptop is just 12 inch away from the wireless modem. Once I move away, it get disconnected. It shows very low frequency.

Please help me to resolve this.

Thanks & Regards,
nprakash

---

### Post by praseodym on 2012-08-06
"Tx-Power=15 dBm" shows that you may use the wrong country codes. Check:

```
dmesg | grep country
```

Use the right ones:

```
sudo apt-get install iw
iw reg get
sudo iw reg set DE # DE for Germany, use your code
iw reg get
```
Check

```
iwconfig
```

---

### Post by nprakash on 2012-08-07
Hi

I had set it for India (i.e. IN) since I am from India. But it didn't resolved my problem.
======================================================
nprakash@Chunmun:~$ sudo iw reg set IN
======================================================
nprakash@Chunmun:~$ iw reg get
-------------------------------------------------------
country IN:
    (2402 - 2482 @ 40), (N/A, 20)
    (5170 - 5250 @ 40), (N/A, 20)
    (5250 - 5330 @ 40), (N/A, 20), DFS
    (5735 - 5835 @ 40), (N/A, 20)
======================================================
nprakash@Chunmun:~$ iwconfig
lo        no wireless extensions.

wlan0     IEEE 802.11abg  ESSID:"ghar"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 80:A1:D7:7C:30:50   
          Bit Rate=1 Mb/s   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=36/70  Signal level=-74 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:10  Invalid misc:73   Missed beacon:0

eth0      no wireless extensions.

The wireless is still showing very less frequency. Also after every restart it set the country as "00".

Thanks & Regards,
nprakash

---

### Post by praseodym on 2012-08-07
Put

> iw reg set IN

as root into the file /etc/rc.local before "exit 0". This will execute the command on every boot-up.

You may also try:

> sudo iwconfig wlan0 txpower 20 [COLOR="Red"]# or 18[/COLOR]

---

### Post by nprakash on 2012-08-07
Dear SIr,

It is still not working. The wireless modem is still showing very low frequency and is not able to connect if the modem is away more than 12 inch.

I had updated the file /etc/rc.local  with the below code before "exit 0".
iw reg set IN


root@Chunmun:~# iwconfig
lo        no wireless extensions.

wlan0     IEEE 802.11abg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:on
          
eth0      no wireless extensions.

root@Chunmun:~# iw reg get
country IN:
    (2402 - 2482 @ 40), (N/A, 20)
    (5170 - 5250 @ 40), (N/A, 20)
    (5250 - 5330 @ 40), (N/A, 20), DFS
    (5735 - 5835 @ 40), (N/A, 20)

I had also the below code as suggested by you.

root@Chunmun:~# sudo iwconfig wlan0 txpower 20
Error for wireless request "Set Tx Power" (8B26) :
    SET failed on device wlan0 ; Invalid argument.
root@Chunmun:~# sudo iwconfig wlan0 txpower 18
Error for wireless request "Set Tx Power" (8B26) :
    SET failed on device wlan0 ; Invalid argument.
root@Chunmun:~# 


Thanks & Regards,
Nprakash

---

### Post by nprakash on 2012-08-07
Can I have a skype based session with you to resolve my problem?

Regards,
nprakash

---

### Post by praseodym on 2012-08-07
Deactivate the Power-Management:

```
sudo iwconfig wlan0 power off
```
Sometimes the PM is buggy, this often helps:

```
wget http://media.cdn.ubuntu-de.org/forum/attachments/38/32/4675487-power_d_skripte.tar.gz
sudo tar xvf 4675487-power_d_skripte.tar.gz -C /etc/pm/power.d 
```
From here:

[http://forum.ubuntuusers.de/topic/sendeleistung-der-wlan-antenne-einstellbar/?highlight=wlan+power+management+wget#post-4675487](http://forum.ubuntuusers.de/topic/sendeleistung-der-wlan-antenne-einstellbar/?highlight=wlan+power+management+wget#post-4675487)

---

### Post by nprakash on 2012-08-08
Dear Sir,

Still not working. I am not able to do anything. Not able to connect to wireless. Same status :(

root@Chunmun:~# iwconfig
lo        no wireless extensions.

wlan0     IEEE 802.11abg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:on
          
eth0      no wireless extensions.

Thanks & Regards,
Nprakash

---

### Post by praseodym on 2012-08-08
Could you please try this script:

[http://forum.ubuntuusers.de/topic/herstellung-der-wlan-verbindung-dauert-sehr-la/#Diagnoseskript](http://forum.ubuntuusers.de/topic/herstellung-der-wlan-verbindung-dauert-sehr-la/#Diagnoseskript)

and run it with "-f" or "-Af"? Please check the "black boxes" how to do it.

---

### Post by nprakash on 2012-08-09
Dear praseodym,

Thanks for all your support so far. But it seems that noting is coming out for getting my problem solved. I am quite bad in linux. Since the day I trusted Ubuntu 8.04 as user friendly, I was working with that without any worry. Now it seems that 12.04 version is no longer supporting my system configuration.

Kindly let me know how can I install ubuntu 10.04 version again. 

Thanks & Regards,
Nprakash

---

### Post by praseodym on 2012-08-10
Unfortunately, downgrading is not possible. Download the ISO-file from here:

[http://releases.ubuntu.com/10.04/](http://releases.ubuntu.com/10.04/)

64bit: [http://releases.ubuntu.com/10.04/ubuntu-10.04.4-desktop-amd64.iso](http://releases.ubuntu.com/10.04/ubuntu-10.04.4-desktop-amd64.iso)

32bit: [http://releases.ubuntu.com/10.04/ubuntu-10.04.4-desktop-i386.iso](http://releases.ubuntu.com/10.04/ubuntu-10.04.4-desktop-i386.iso)

In the nautilus file manager right-click on the ISO and "write to CD/DVD" burns the ISO-image. Save your data and reinstall 10.04.

---

### Post by nprakash on 2012-08-17
[COLOR=black][FONT=Tahoma]Hi Praseodym,[/FONT][/COLOR]
[COLOR=black][FONT=Tahoma] [/FONT][/COLOR]
[COLOR=black][FONT=Tahoma]My wireless problem is resolved. I found that the intel wireless card was not functioning properly. I made a completely fresh installation of Ubuntu 12.04 with new intel wireless card and it is working absolutely fine. [/FONT][/COLOR]
[COLOR=black][FONT=Tahoma]I would suggest if this problem someone else had faced, then they should verify their hardware linked to it.[/FONT][/COLOR]
[COLOR=black][FONT=Tahoma] [/FONT][/COLOR]
[COLOR=black][FONT=Tahoma]Thanks & Regards,[/FONT][/COLOR]
[COLOR=black][FONT=Tahoma]nprakash[/FONT][/COLOR]

---

