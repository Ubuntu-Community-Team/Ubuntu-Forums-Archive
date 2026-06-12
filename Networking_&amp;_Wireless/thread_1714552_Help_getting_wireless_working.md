---
title: "Help getting wireless working"
date: 2011-03-25
forum: Networking &amp; Wireless
---

### Post by FtizaKlick on 2011-03-25
Hello,

I have a Dell Inspiron N5110 with Intel Centrino Wireless-N 1030 card. Fresh install of 10.10, I can't seem to get my wireless working.

```

$ lspci | grep -i net
05:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 05)
09:00.0 Network controller: Intel Corporation Device 008a (rev 34)

```

I tried to install ndiswrapper but I kept running into issues with that; building from source I get this error:
```

~/ndiswrapper-1.56$ make
make -C driver
make[1]: Entering directory `/home/jess/ndiswrapper-1.56/driver'
make -C /usr/src/linux-headers-2.6.35-28-generic M=/home/jess/ndiswrapper-1.56/driver
make[2]: Entering directory `/usr/src/linux-headers-2.6.35-28-generic'
  CC [M]  /home/jess/ndiswrapper-1.56/driver/wrapndis.o
/home/jess/ndiswrapper-1.56/driver/wrapndis.c: In function ‘set_multicast_list’:
/home/jess/ndiswrapper-1.56/driver/wrapndis.c:953: error: ‘struct net_device’ has no member named ‘mc_count’
/home/jess/ndiswrapper-1.56/driver/wrapndis.c:956: error: ‘struct net_device’ has no member named ‘mc_count’
/home/jess/ndiswrapper-1.56/driver/wrapndis.c:960: error: ‘struct net_device’ has no member named ‘mc_count’
/home/jess/ndiswrapper-1.56/driver/wrapndis.c:960: warning: type defaults to ‘int’ in declaration of ‘_min2’
/home/jess/ndiswrapper-1.56/driver/wrapndis.c:960: error: ‘struct net_device’ has no member named ‘mc_count’
/home/jess/ndiswrapper-1.56/driver/wrapndis.c:967: error: ‘struct net_device’ has no member named ‘mc_list’
/home/jess/ndiswrapper-1.56/driver/wrapndis.c:968: error: dereferencing pointer to incomplete type
/home/jess/ndiswrapper-1.56/driver/wrapndis.c:969: error: dereferencing pointer to incomplete type
/home/jess/ndiswrapper-1.56/driver/wrapndis.c:971: error: dereferencing pointer to incomplete type
make[3]: *** [/home/jess/ndiswrapper-1.56/driver/wrapndis.o] Error 1
make[2]: *** [_module_/home/jess/ndiswrapper-1.56/driver] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.35-28-generic'
make[1]: *** [modules] Error 2
make[1]: Leaving directory `/home/jess/ndiswrapper-1.56/driver'
make: *** [all] Error 2

```

Also, when I installed ndiswrapper-common from the repositories I ended up with this problem: 
```

$ sudo modprobe ndiswrapper
FATAL: Module ndiswrapper not found.

```

In addition, I installed compat-wireless but that didn't install the driver.

So, any help at this point either with ndiswrapper or another method to get the driver working would be appreciated. 

Thank you,
Jess

---

### Post by FtizaKlick on 2011-03-25
Update: Nevermind-- my entire Ubuntu install just crashed, I'm gonna go back to Windows 7 for a while 8-[

---

### Post by cnwalk on 2011-08-25
I have this same problem, but I love Ubuntu and am not giving up and going back to Win 7!  Please help.

owner@owner-laptop:~$ lshw -c network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: eth0
       version: 05
       serial: 18:03:73:5b:b0:b9
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=r8169 driverversion=2.3LK-NAPI latency=0 multicast=yes
       resources: irq:30 ioport:e000(size=256) memory:f1104000-f1104fff(prefetchable) memory:f1100000-f1103fff(prefetchable)
  *-network UNCLAIMED
       description: Network controller
       product: Intel Corporation
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:09:00.0
       version: 34
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0
       resources: memory:f7e00000-f7e01fff

09:00.0 Network controller: Intel Corporation Device 008a (rev 34)

---

### Post by praseodym on 2011-08-25
Hello,

can you show the outputs of:

```
lspci -nnk | grep -iA2 net
lsmod
iwconfig
rfkill list
sudo iwlist scan
```

---

### Post by cnwalk on 2011-08-26
Thank for your help. I upgraded to 10.10 last night to see if this would fix... it did not. Please see my answers below. Also found that I have no audio.


lspci -nnk | grep -iA2 net
05:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 05)
	Subsystem: Dell Device [1028:04b0]
	Kernel driver in use: r8169
--
09:00.0 Network controller [0280]: Intel Corporation Device [8086:008a] (rev 34)
	Subsystem: Intel Corporation Device [8086:5325]
0b:00.0 USB Controller [0c03]: NEC Corporation uPD720200 USB 3.0 Host Controller [1033:0194] (rev 04)

lsmod
Module                  Size  Used by
nls_utf8                1453  0 
udf                    86514  0 
crc_itu_t               1739  1 udf
binfmt_misc             7984  1 
rfcomm                 40787  4 
sco                     9986  2 
bnep                   11985  2 
l2cap                  42304  16 rfcomm,bnep
parport_pc             30086  0 
ppdev                   6804  0 
snd_hda_codec_intelhdmi    11032  1 
snd_hda_codec_idt      64763  0 
snd_hda_intel          26147  2 
snd_hda_codec         100919  3 snd_hda_codec_intelhdmi,snd_hda_codec_idt,snd_hda_intel
snd_hwdep               6660  1 snd_hda_codec
snd_pcm                89104  2 snd_hda_intel,snd_hda_codec
snd_seq_midi            5932  0 
snd_rawmidi            22207  1 snd_seq_midi
snd_seq_midi_event      7291  1 snd_seq_midi
i915                  335073  3 
drm_kms_helper         32836  1 i915
drm                   206198  3 i915,drm_kms_helper
snd_seq                57512  2 snd_seq_midi,snd_seq_midi_event
snd_timer              23850  2 snd_pcm,snd_seq
arc4                    1497  0 
snd_seq_device          6912  3 snd_seq_midi,snd_rawmidi,snd_seq
lp                     10201  0 
rtl8187                53994  0 
mac80211              267099  1 rtl8187
led_class               3393  1 rtl8187
snd                    64277  13 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
i2c_algo_bit            6208  1 i915
parport                37032  3 parport_pc,ppdev,lp
video                  22176  1 i915
cfg80211              170581  2 rtl8187,mac80211
dell_laptop             6722  0 
dell_wmi                3372  0 
soundcore               1240  1 snd
intel_agp              32334  2 i915
btusb                  12961  2 
snd_page_alloc          8588  2 snd_hda_intel,snd_pcm
dcdbas                  6942  1 dell_laptop
eeprom_93cx6            1789  1 rtl8187
bluetooth              59245  9 rfcomm,sco,bnep,l2cap,btusb
output                  2527  1 video
psmouse                62080  0 
serio_raw               4910  0 
uvcvideo               62411  0 
videodev               49359  1 uvcvideo
v4l1_compat            15519  2 uvcvideo,videodev
v4l2_compat_ioctl32    12614  1 videodev
usb_storage            50788  0 
ahci                   22370  2 
r8169                  42286  0 
libahci                26148  1 ahci
xhci_hcd               62016  0 
mii                     5261  1 r8169


iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.


rfkill list
0: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
1: dell-wifi: Wireless LAN
	Soft blocked: no
	Hard blocked: no
2: dell-bluetooth: Bluetooth
	Soft blocked: no
	Hard blocked: no
3: dell-wwan: Wireless WAN
	Soft blocked: no
	Hard blocked: no

sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

---

### Post by praseodym on 2011-08-26
The driver iwlagn is not loaded:

```
sudo modprobe -rf rtl8187
sudo modprobe -v iwlagn
sudo depmod -a
sudo service network-manager restart
```
Do you have a wireless stick plugged in (module rtl8187)?

Checks:

```
iwconfig
sudo iwlist scan
dmesg | grep iwl
```

---

### Post by cnwalk on 2011-08-26
I have been using a wireless adapter to get online, but have removed it before running any commands.  I will leave it in for these entries. 

This is what I got from each command entered...


sudo modprobe -rf rt18187
[sudo] password for owner: 
FATAL: Module rt18187 not found.
owner@owner-laptop:~$ sudo modprobe -v iwlagn
insmod /lib/modules/2.6.35-30-generic/kernel/drivers/net/wireless/iwlwifi/iwlcore.ko 
insmod /lib/modules/2.6.35-30-generic/kernel/drivers/net/wireless/iwlwifi/iwlagn.ko 11n_disable=1
owner@owner-laptop:~$ sudo depmod -a
owner@owner-laptop:~$ sudo service network-manager restart
network-manager start/running, process 1920
owner@owner-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"Verizon AC30 AFF6"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 98:F5:37:01:AF:F6   
          Bit Rate=5.5 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=52/70  Signal level=-58 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

owner@owner-laptop:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 98:F5:37:01:AF:F6
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=55/70  Signal level=-55 dBm  
                    Encryption key:on
                    ESSID:"Verizon AC30 AFF6"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000004c6b93180
                    Extra: Last beacon: 520ms ago
                    IE: Unknown: 0011566572697A6F6E20414333302041464636
                    IE: Unknown: 010882848B0C12961824
                    IE: Unknown: 030101
                    IE: Unknown: 0706555320010B1B
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK

owner@owner-laptop:~$ dmesg | grep iwl
[  231.616572] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, in-tree:
[  231.616574] iwlagn: Copyright(c) 2003-2010 Intel Corporation

---

### Post by praseodym on 2011-08-26
There is the connection.

You may try WPA2-AES instead of WPA-TKIP. Please show now:

```
route -n
cat /etc/resolv.conf
cat /etc/network/interfaces
rfkill list
```
Also try to remove your current wireless profile and set up a new one

---

### Post by cnwalk on 2011-08-26
Thank you so much for your help. Just a reminder, I am currently using a netgear wireless adapter to get online. Should I pull this out and disconnect when I run these commands? This is frustrating, but I am not going to let this stop me from using Ubuntu. I love this software and want to know more! I have been able to assist several co-workers leave Mac and Windows behind. I have never had so much difficulty getting a computer set up with Ubuntu.

Thanks again!

route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.0.0     0.0.0.0         255.255.255.0   U     2      0        0 wlan0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlan0
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 wlan0


cat /etc/resolv.conf
# Generated by NetworkManager
nameserver 192.168.0.1


cat /etc/resolv.conf
# Generated by NetworkManager
nameserver 192.168.0.1
owner@owner-laptop:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback


rfkill list
0: dell-wifi: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: dell-bluetooth: Bluetooth
	Soft blocked: no
	Hard blocked: no
2: dell-wwan: Wireless WAN
	Soft blocked: no
	Hard blocked: no
3: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
4: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no

---

### Post by praseodym on 2011-08-27
Yes the commands with the stick unplugged (again!). Plus:

```
cat /var/lib/NetworkManager/NetworkManager.state
cat /etc/udev/rules.d/70-persistent-net.rules
cat /etc/NetworkManager/nm-system-settings.conf
```

P.S.: This is a typo:

> sudo modprobe -rf rt[COLOR="Red"]1[/COLOR]8187
its not a one, but a small L

---

