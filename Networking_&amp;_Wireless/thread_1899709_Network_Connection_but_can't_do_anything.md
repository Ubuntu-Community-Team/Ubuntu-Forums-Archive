---
title: "Network Connection but can't do anything"
date: 2011-12-24
forum: Networking &amp; Wireless
---

### Post by clucas on 2011-12-24
My MacBook connects to the wireless home network without any problem (to both the 2 ghz and 5 ghz). Full strength. Yet when I try to use any Internet app (browser, email, app update) it says there is no internet connection. Can't understand. Was working without problems for weeks but not now. Haven't installed any new apps other than doing an update. Have Ubuntu 11.10.

---

### Post by praseodym on 2011-12-24
Hi,

please show:

```
lspci -nnk | grep -iA2 net
lsusb
lsmod
ifconfig -a
iwconfig
cat /var/lib/NetworkManager/NetworkManager.state
sudo iwlist scan
cat /etc/resolv.conf
```

---

### Post by clucas on 2011-12-24
Here it is:


carl@carl-MacBook:~$ lspci -nnk | grep -iA2 net
02:00.0 Network controller [0280]: Broadcom Corporation BCM4321 802.11a/b/g/n [14e4:4328] (rev 03)
	Subsystem: Apple Computer Inc. Device [106b:0088]
	Kernel driver in use: wl
--
03:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd. 88E8058 PCI-E Gigabit Ethernet Controller [11ab:436a] (rev 13)
	Subsystem: Marvell Technology Group Ltd. Device [11ab:00ba]
	Kernel driver in use: sky2
carl@carl-MacBook:~$ lspci -nnk | grep -iA2 net
02:00.0 Network controller [0280]: Broadcom Corporation BCM4321 802.11a/b/g/n [14e4:4328] (rev 03)
	Subsystem: Apple Computer Inc. Device [106b:0088]
	Kernel driver in use: wl
--
03:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd. 88E8058 PCI-E Gigabit Ethernet Controller [11ab:436a] (rev 13)
	Subsystem: Marvell Technology Group Ltd. Device [11ab:00ba]
	Kernel driver in use: sky2
carl@carl-MacBook:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 05ac:8501 Apple, Inc. Built-in iSight [Micron]
Bus 007 Device 002: ID 05ac:8242 Apple, Inc. IR Receiver [built-in]
Bus 007 Device 003: ID 05ac:0229 Apple, Inc. Internal Keyboard/Trackpad (MacBook Pro) (ANSI)
Bus 003 Device 003: ID 05ac:8205 Apple, Inc. Bluetooth HCI
carl@carl-MacBook:~$ lsmod
Module                  Size  Used by
hid_magicmouse         13570  0 
hidp                   22351  1 
bnep                   17923  2 
rfcomm                 38408  8 
parport_pc             32114  0 
ppdev                  12849  0 
binfmt_misc            17292  1 
btusb                  18160  4 
bluetooth             148839  28 hidp,bnep,rfcomm,btusb
snd_hda_codec_realtek   254125  1 
joydev                 17393  0 
snd_hda_intel          24262  2 
snd_hda_codec          91754  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80435  2 snd_hda_intel,snd_hda_codec
appletouch             17318  0 
hid_apple              13166  0 
snd_seq_midi           13132  0 
applesmc               18978  0 
input_polldev          13648  1 applesmc
lib80211_crypt_tkip    17240  0 
snd_rawmidi            25241  1 snd_seq_midi
wl                   2646601  0 
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28932  2 snd_pcm,snd_seq
lib80211               14570  2 lib80211_crypt_tkip,wl
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
i915                  505159  3 
snd                    55902  13 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
drm_kms_helper         32889  1 i915
drm                   192194  4 i915,drm_kms_helper
i2c_algo_bit           13199  1 i915
soundcore              12600  1 snd
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
video                  18908  1 i915
apple_bl               13049  0 
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
usbhid                 41905  0 
hid                    77367  4 hid_magicmouse,hidp,hid_apple,usbhid
firewire_ohci          35854  0 
firewire_core          56937  1 firewire_ohci
crc_itu_t              12627  1 firewire_core
sky2                   49317  0 
carl@carl-MacBook:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:1e:c2:0d:25:f6  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 

eth1      Link encap:Ethernet  HWaddr 00:1e:52:c5:87:8e  
          inet addr:192.168.0.6  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::21e:52ff:fec5:878e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:171 errors:0 dropped:0 overruns:0 frame:1259
          TX packets:214 errors:21 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:30021 (30.0 KB)  TX bytes:24214 (24.2 KB)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:116 errors:0 dropped:0 overruns:0 frame:0
          TX packets:116 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:8984 (8.9 KB)  TX bytes:8984 (8.9 KB)

carl@carl-MacBook:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11  Access Point: Not-Associated   
          Link Quality:5  Signal level:212  Noise level:199
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0

carl@carl-MacBook:~$ cat /var/lib/NetworkManager/NetworkManager.state

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true
carl@carl-MacBook:~$ sudo iwlist scan
[sudo] password for carl: 
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Scan completed :
          Cell 01 - Address: C4:3D:C7:8E:CE:15
                    ESSID:"Lucas Network 2.4ghz b/g/n/"
                    Mode:Managed
                    Frequency:2.457 GHz (Channel 10)
                    Quality:5/5  Signal level:-31 dBm  Noise level:-92 dBm
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD860050F204104A0001101044000102103B0001031047001000000000000010000000C43DC78ECE151021000D4E6574676561722C20496E632E10230008574E4452333730301024000456314831104200046E6F6E651054000800060050F204000110110017574E445233373030763228576972656C65737320415029100800020086103C000103
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
          Cell 02 - Address: 00:E0:98:CC:27:AB
                    ESSID:"awanas1"
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:1/5  Signal level:-82 dBm  Noise level:-92 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                              6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
          Cell 03 - Address: C4:3D:C7:8E:CE:17
                    ESSID:"Lucas Network 5ghz a/n"
                    Mode:Managed
                    Frequency:5.23 GHz
                    Quality:5/5  Signal level:-46 dBm  Noise level:-92 dBm
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD860050F204104A0001101044000102103B0001031047001000000000000010000000C43DC78ECE151021000D4E6574676561722C20496E632E10230008574E4452333730301024000456314831104200046E6F6E651054000800060050F204000110110017574E445233373030763228576972656C65737320415029100800020086103C000103
                    Encryption key:on
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s

carl@carl-MacBook:~$ cat /etc/resolv.conf
# Generated by NetworkManager
nameserver 192.168.0.252

---

### Post by praseodym on 2011-12-24
I forgot to ask:

> rfkill list

---

### Post by clucas on 2011-12-24
0: brcmwl-0: Wireless LAN
       Soft blocked: no
       Hard Blocked: no
2: hci0: Bluetooth
       Soft Blocked: no
       Hard Blocked: no

---

### Post by praseodym on 2011-12-24
Blacklist the module "brcm80211" and reboot.

---

### Post by clucas on 2011-12-24
I'm sure I'm to edit a file to do that but, excuse my ignorance, what file and where is it at?

---

### Post by praseodym on 2011-12-24
In one line:

```
echo "blacklist brcm80211" | sudo tee -a /etc/modprobe.d/blacklist.conf
```
or
```
gksu gedit /etc/modprobe.d/blacklist.conf
```
and add the line
```
blacklist brcm80211
```
save, close gedit, and reboot

---

### Post by clucas on 2011-12-24
That did it!!! Thanks!!!!!!!!!!

---

### Post by clucas on 2011-12-24
I spoke too soon. It was working then I got busy doing something else. And it was not connecting to any site like before. I rebooted but still have the same situation. Anything else I can try?

---

### Post by praseodym on 2011-12-24
Check now:

```
iwconfig
sudo iwlist scan
dmesg | grep wl
```
I recommend WPA2-AES encryption

---

### Post by clucas on 2011-12-24
The results:


lo	no wireless extensions.

Eth0	no wireless extensions.


eth1      IEEE 802.11  Access Point: Not-Associated   
          Link Quality:5  Signal level:211  Noise level:199
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0


eth1      Scan completed :
          Cell 01 - Address: C4:3D:C7:8E:CE:17
                    ESSID:"Lucas Network 5ghz a/n"
                    Mode:Managed
                    Frequency:5.23 GHz
                    Quality:5/5  Signal level:-48 dBm  Noise level:-92 dBm
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD860050F204104A0001101044000102103B0001031047001000000000000010000000C43DC78ECE151021000D4E6574676561722C20496E632E10230008574E4452333730301024000456314831104200046E6F6E651054000800060050F204000110110017574E445233373030763228576972656C65737320415029100800020086103C000103
                    Encryption key:on
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
          Cell 02 - Address: 00:E0:98:CC:27:AB
                    ESSID:"awanas1"
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:1/5  Signal level:-81 dBm  Noise level:-92 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                              6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
          Cell 03 - Address: C4:3D:C7:8E:CE:15
                    ESSID:"Lucas Network 2.4ghz b/g/n/"
                    Mode:Managed
                    Frequency:2.457 GHz (Channel 10)
                    Quality:5/5  Signal level:-31 dBm  Noise level:-92 dBm
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD860050F204104A0001101044000102103B0001031047001000000000000010000000C43DC78ECE151021000D4E6574676561722C20496E632E10230008574E4452333730301024000456314831104200046E6F6E651054000800060050F204000110110017574E445233373030763228576972656C65737320415029100800020086103C000103
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s




[   18.719465] wl: module license 'MIXED/Proprietary' taints kernel.
[   19.139655] wl 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   19.139663] wl 0000:02:00.0: setting latency timer to 64

---

### Post by clucas on 2011-12-24
Meant to tell you, for what it's worth, that I have no trouble accessing the other computers on the network.

Oh...and Merry Christmas!

---

### Post by praseodym on 2011-12-24
Are these your networks to connect to:

> ESSID:"Lucas Network 5ghz a/n"
...
ESSID:"Lucas Network 2.4ghz b/g/n/"
?
Change the ESSIDs to sth. without blanks!

---

### Post by clucas on 2011-12-25
Yes, they are the networks. I have a Netgear N600 Wireless Dual Band Gigabit Router.

How do I change the ESSID? And why should I? They are the networks I can use.

---

### Post by praseodym on 2011-12-25
Both networks start with "Lucas Network" and a blank, maybe the NM gets confused" (it really does!) and it wants to connect to either of it. You change the ESSID connecting via cable to the router (because you change settings there; with wireless you would get a disconnect) and change it there for any of your networks.

---

