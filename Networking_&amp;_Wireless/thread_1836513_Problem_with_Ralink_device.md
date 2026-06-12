---
title: "Problem with Ralink device"
date: 2011-08-31
forum: Networking &amp; Wireless
---

### Post by hungry&amp; on 2011-08-31
I have this HP laptop ; ProBook 4430s ; Natty Narwhale
The problem is, it does not detect any wireless networks.

Here's some data :

```

24:00.0 Network controller: Ralink corp. Device 3592

```


```

nm-tool

NetworkManager Tool

State: disconnected

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             unavailable
  Default:           no
  HW Address:        64:31:50:9E:DD:59

  Capabilities:
    Carrier Detect:  yes
    Speed:           10 Mb/s

  Wired Properties
    Carrier:         off


- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rt2800pci
  State:             disconnected
  Default:           no
  HW Address:        68:A3:C4:F1:85:A9

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 

```

```

sudo lshw -C network
 *-network               
       description: Wireless interface
       product: Ralink corp.
       vendor: Ralink corp.
       physical id: 0
       bus info: pci@0000:24:00.0
       logical name: wlan0
       version: 00
       serial: 68:a3:c4:f1:85:a9
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rt2800pci driverversion=2.6.38-8-generic firmware=0.11 latency=0 link=yes multicast=yes wireless=IEEE 802.11abgn
       resources: irq:19 memory:94700000-9470ffff
  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:25:00.0
       logical name: eth0
       version: 06
       serial: 64:31:50:9e:dd:59
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:40 ioport:2000(size=256) memory:94404000-94404fff memory:94400000-94403fff

```

```


iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:off/any  
          Mode:Ad-Hoc  Frequency:2.412 GHz  Cell: Not-Associated   
          Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on

```

```

rfkill list all
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
2: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no

```

Thank you in advance.

---

### Post by praseodym on 2011-08-31
Hello,

can you show

```
lspci -nnk | grep -iA2 Ralink
lsmod
```
You may have to compile a new driver for this device, so lets see which chipset is used.

You created an Ad-Hoc-Network as is shown by "iwconfig". **Remove** your current wireless profile and setup a **new one** in "Infrasctructure"-mode. Additionally you should turn the "Power-Management" off:

```
sudo iwconfig wlan0 power off
```

---

### Post by hungry&amp; on 2011-08-31
Hello, thanks for replying. 

```
sudo iwconfig wlan0 power off
```
// Since I've already turned this off, do I have to redo the data above?

```
lspci -nnk | grep -iA2 Ralink
24:00.0 Network controller [0280]: Ralink corp. Device [1814:3592]
	Subsystem: Hewlett-Packard Company Device [103c:1638]
	Kernel driver in use: rt2800pci
```

```
lsmod
Module                  Size  Used by
ipt_MASQUERADE         12663  0 
xt_state               12514  0 
ipt_REJECT             12512  0 
xt_tcpudp              12531  0 
iptable_filter         12706  0 
nf_nat_h323            12749  0 
nf_conntrack_h323      52200  1 nf_nat_h323
nf_nat_pptp            12536  0 
nf_conntrack_pptp      13562  1 nf_nat_pptp
nf_conntrack_proto_gre    13353  1 nf_conntrack_pptp
nf_nat_proto_gre       12671  1 nf_nat_pptp
nf_nat_tftp            12420  0 
nf_conntrack_tftp      12817  1 nf_nat_tftp
nf_nat_sip             16922  0 
nf_conntrack_sip       24652  1 nf_nat_sip
nf_nat_irc             12542  0 
nf_conntrack_irc       13138  1 nf_nat_irc
nf_nat_ftp             12548  0 
nf_conntrack_ftp       13106  1 nf_nat_ftp
iptable_nat            12977  0 
nf_nat                 24827  9 ipt_MASQUERADE,nf_nat_h323,nf_nat_pptp,nf_nat_proto_gre,nf_nat_tftp,nf_nat_sip,nf_nat_irc,nf_nat_ftp,iptable_nat
nf_conntrack_ipv4      19024  3 iptable_nat,nf_nat
nf_conntrack           69744  18 ipt_MASQUERADE,xt_state,nf_nat_h323,nf_conntrack_h323,nf_nat_pptp,nf_conntrack_pptp,nf_conntrack_proto_gre,nf_nat_tftp,nf_conntrack_tftp,nf_nat_sip,nf_conntrack_sip,nf_nat_irc,nf_conntrack_irc,nf_nat_ftp,nf_conntrack_ftp,iptable_nat,nf_nat,nf_conntrack_ipv4
nf_defrag_ipv4         12649  1 nf_conntrack_ipv4
ip_tables              18125  2 iptable_filter,iptable_nat
x_tables               21907  7 ipt_MASQUERADE,xt_state,ipt_REJECT,xt_tcpudp,iptable_filter,iptable_nat,ip_tables
sha256_generic         20911  2 
cryptd                 19801  0 
aes_i586               16956  181 
aes_generic            38023  1 aes_i586
parport_pc             32111  0 
ppdev                  12849  0 
dm_crypt               22463  1 
snd_hda_codec_hdmi     27479  1 
snd_hda_codec_idt      60537  1 
binfmt_misc            13213  1 
rt3562sta             874110  0 
snd_hda_intel          24140  2 
snd_hda_codec          90901  3 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13274  1 snd_hda_codec
snd_pcm                80244  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
arc4                   12473  2 
sco                    17779  2 
snd_seq_midi           13132  0 
rt2800pci              18159  0 
snd_rawmidi            25269  1 snd_seq_midi
bnep                   17785  2 
joydev                 17322  0 
l2cap                  48656  3 bnep
rt2800lib              43824  1 rt2800pci
hp_wmi                 13418  0 
crc_ccitt              12595  1 rt2800lib
rt2x00pci              13986  1 rt2800pci
sparse_keymap          13666  1 hp_wmi
snd_seq_midi_event     14475  1 snd_seq_midi
rt2x00lib              39075  3 rt2800pci,rt2800lib,rt2x00pci
uvcvideo               66851  0 
btusb                  18160  2 
mac80211              257001  3 rt2800lib,rt2x00pci,rt2x00lib
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28659  2 snd_pcm,snd_seq
psmouse                73312  0 
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
videodev               75143  1 uvcvideo
bluetooth              65565  8 sco,bnep,l2cap,btusb
serio_raw              12990  0 
snd                    55295  14 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
hp_accel               21632  0 
cfg80211              156212  2 rt2x00lib,mac80211
lis3lv02d              19285  1 hp_accel
input_polldev          13735  1 lis3lv02d
soundcore              12600  1 snd
xhci_hcd               68062  0 
jmb38x_ms              17364  0 
snd_page_alloc         14073  2 snd_hda_intel,snd_pcm
memstick               15816  1 jmb38x_ms
eeprom_93cx6           12653  1 rt2800pci
lp                     13349  0 
parport                36746  3 parport_pc,ppdev,lp
i915                  450944  3 
usbhid                 41704  0 
hid                    77084  1 usbhid
drm_kms_helper         40745  1 i915
drm                   180037  4 i915,drm_kms_helper
ahci                   21591  2 
i2c_algo_bit           13184  1 i915
sdhci_pci              13623  0 
libahci                25548  1 ahci
video                  18951  1 i915
r8169                  42534  0 
sdhci                  22720  1 sdhci_pci
```

---

### Post by praseodym on 2011-08-31
Two errors: You created an Ad-Hoc-Network, this means "Internet Connection Sharing (ICS)". _Delete_ (not modify) your wireless profile and create a new one in "Infrastructure" mode. Additionally you have two drivers loaded. Please show:

```
modinfo rt3562sta | grep 3592
modinfo rt2800pci | grep 3592
```
Blacklist the old one and reload the other:

```
sudo modprobe -rf rt2800pci rt3562sta
echo "blacklist rt2800pci" | sudo tee /etc/modprobe.d/blacklist-rt2800pci.conf
sudo modprobe -v rt3562sta
sudo depmod -a
sudo update-initramfs -u
sudo service network-manager restart
```
Controls:

```
dmesg | egrep 'rt2|rt3'
iwconfig
sudo iwlist scan
lsmod
iwlist chan
route -n
```
BTW: You normally dont need a firewall being installed.

---

### Post by hungry&amp; on 2011-08-31
Here's what I did :
I rebooted the computer to windows;
I pressed the button to switch off the wireless;
//The button is now orange (deactivated)
Rebooted the system in linux;
//Reactivated wireless button

Entered
```
sudo modprobe -rf rt2800pci rt3562sta
```

```
echo "blacklist rt2800pci" | sudo tee /etc/modprobe.d/blacklist-rt2800pci.conf
```

As I entered :
```
sudo modprobe -v rt3562sta
```
The computer crashed and I rebooted again.

This time it could detect wireless networks.
I opened Mozilla but there was no internet connectivity.
//Problem with the ip assignment?
I disconnected from my wifi and entered the following

```
sudo modprobe -rf rt2800pci rt3562sta
echo "blacklist rt2800pci" | sudo tee /etc/modprobe.d/blacklist-rt2800pci.conf
sudo modprobe -v rt3562sta
sudo depmod -a
sudo update-initramfs -u
sudo service network-manager restart
```

Restarted the computer.

 Then entered the following
```
dmesg | egrep 'rt2|rt3'
[   28.692930] rt28xx_get_wireless_stats --->
[   28.692932] <--- rt28xx_get_wireless_stats
[   28.694155] rt28xx_get_wireless_stats --->
[   28.694158] <--- rt28xx_get_wireless_stats
[   35.131065] rt28xx_get_wireless_stats --->
[   35.131067] <--- rt28xx_get_wireless_stats
[   41.124284] rt28xx_get_wireless_stats --->
[   41.124286] <--- rt28xx_get_wireless_stats
[   47.118131] rt28xx_get_wireless_stats --->
[   47.118133] <--- rt28xx_get_wireless_stats
[   53.110392] rt28xx_get_wireless_stats --->
[   53.110394] <--- rt28xx_get_wireless_stats
[   59.109100] rt28xx_get_wireless_stats --->
[   59.109102] <--- rt28xx_get_wireless_stats
[   65.102881] rt28xx_get_wireless_stats --->
[   65.102883] <--- rt28xx_get_wireless_stats
[   83.077662] rt28xx_get_wireless_stats --->
[   83.077667] <--- rt28xx_get_wireless_stats
[   89.075730] rt28xx_get_wireless_stats --->
[   89.075735] <--- rt28xx_get_wireless_stats
[   95.069720] rt28xx_get_wireless_stats --->
[   95.069725] <--- rt28xx_get_wireless_stats
[  101.062987] rt28xx_get_wireless_stats --->
[  101.062992] <--- rt28xx_get_wireless_stats
[  107.055938] rt28xx_get_wireless_stats --->
[  107.055943] <--- rt28xx_get_wireless_stats
[  113.046135] rt28xx_get_wireless_stats --->
[  113.046140] <--- rt28xx_get_wireless_stats
[  119.038838] rt28xx_get_wireless_stats --->
[  119.038843] <--- rt28xx_get_wireless_stats
[  125.032957] rt28xx_get_wireless_stats --->
[  125.032962] <--- rt28xx_get_wireless_stats
[  137.018155] rt28xx_get_wireless_stats --->
[  137.018161] <--- rt28xx_get_wireless_stats
[  143.012952] rt28xx_get_wireless_stats --->
[  143.012957] <--- rt28xx_get_wireless_stats
[  149.006165] rt28xx_get_wireless_stats --->
[  149.006171] <--- rt28xx_get_wireless_stats
[  154.999887] rt28xx_get_wireless_stats --->
[  154.999892] <--- rt28xx_get_wireless_stats
[  164.724386] rt28xx_get_wireless_stats --->
[  164.724392] <--- rt28xx_get_wireless_stats
[  166.986750] rt28xx_get_wireless_stats --->
[  166.986755] <--- rt28xx_get_wireless_stats
[  172.981051] rt28xx_get_wireless_stats --->
[  172.981055] <--- rt28xx_get_wireless_stats
[  178.975728] rt28xx_get_wireless_stats --->
[  178.975733] <--- rt28xx_get_wireless_stats

```
```
iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

ra0       Ralink STA  ESSID:""  Nickname:"RT3562STA"
          Mode:Auto  Frequency=2.457 GHz  Access Point: 00:1E:58:E0:98:60   
          Bit Rate=1 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=56/100  Signal level:-59 dBm  Noise level:-59 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```
```
sudo iwlist scan

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

ra0       Scan completed :
          Cell 01 - Address: 5C:D9:98:FF:71:D0
                    Protocol:802.11b/g/n
                    ESSID:"hanimsmf@unifi"
                    Mode:Managed
                    Frequency:2.412 GHz (Channel 1)
                    Quality:23/100  Signal level:-81 dBm  Noise level:-87 dBm
                    Encryption key:on
                    Bit Rates:300 Mb/s
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD130050F204104A00011010440001021041000100
          Cell 02 - Address: 00:22:B0:40:88:31
                    Protocol:802.11b/g
                    ESSID:"YM"
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:7/100  Signal level:-87 dBm  Noise level:-82 dBm
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    IE: Unknown: DD0E0050F204104A0001101044000102
          Cell 03 - Address: 00:1E:58:E0:98:60
                    Protocol:802.11b/g/n
                    ESSID:"lspyng_unifi"
                    Mode:Managed
                    Frequency:2.457 GHz (Channel 10)
                    Quality:100/100  Signal level:-47 dBm  Noise level:-92 dBm
                    Encryption key:on
                    Bit Rates:300 Mb/s
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD130050F204104A00011010440001021041000100

```
```
lsmod
Module                  Size  Used by
sha256_generic         20911  2 
cryptd                 19801  0 
aes_i586               16956  16 
aes_generic            38023  1 aes_i586
parport_pc             32111  0 
ppdev                  12849  0 
dm_crypt               22463  1 
snd_hda_codec_hdmi     27479  1 
snd_hda_codec_idt      60537  1 
binfmt_misc            13213  1 
sco                    17779  2 
bnep                   17785  2 
l2cap                  48656  3 bnep
joydev                 17322  0 
snd_hda_intel          24140  2 
snd_hda_codec          90901  3 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13274  1 snd_hda_codec
snd_pcm                80244  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25269  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
hp_accel               21632  0 
lis3lv02d              19285  1 hp_accel
snd_timer              28659  2 snd_pcm,snd_seq
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
hp_wmi                 13418  0 
sparse_keymap          13666  1 hp_wmi
uvcvideo               66851  0 
snd                    55295  14 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
btusb                  18160  2 
input_polldev          13735  1 lis3lv02d
rt3562sta             874110  1 
jmb38x_ms              17364  0 
bluetooth              65565  8 sco,bnep,l2cap,btusb
psmouse                73312  0 
videodev               75143  1 uvcvideo
xhci_hcd               68062  0 
soundcore              12600  1 snd
memstick               15816  1 jmb38x_ms
snd_page_alloc         14073  2 snd_hda_intel,snd_pcm
serio_raw              12990  0 
lp                     13349  0 
parport                36746  3 parport_pc,ppdev,lp
usbhid                 41704  0 
hid                    77084  1 usbhid
i915                  450944  3 
ahci                   21591  2 
r8169                  42534  0 
libahci                25548  1 ahci
drm_kms_helper         40745  1 i915
drm                   180037  4 i915,drm_kms_helper
i2c_algo_bit           13184  1 i915
video                  18951  1 i915
sdhci_pci              13623  0 
sdhci                  22720  1 sdhci_pci
```
```
iwlist chan
lo        no frequency information.

eth0      no frequency information.

ra0       14 channels in total; available frequencies :
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
          Channel 14 : 2.484 GHz
          Current Frequency=2.457 GHz (Channel 10)
```

```
route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
```

Opened Firefox,
google.com doesn't to load, icons keeps spinning

---

### Post by praseodym on 2011-09-01
You may remove your current wireless profile and create a new one (in "Infrastructure"-modus), because the interface name changed from wlan0 to ra0.

---

### Post by hungry&amp; on 2011-09-01
> **praseodym said:**
> You may remove your current wireless profile and create a new one (in "Infrastructure"-modus), because the interface name changed from wlan0 to ra0.

I'm sorry, mind telling me how to do that?

---

### Post by nm_geo on 2011-09-01
Right click on the Wifi/Radar looking Icon near upper right corner.
Edit Connections
Wireless Tab
Delete current wireless 

Then add new wireless connection 
Put the name of your AP in the SSID
be sure to choose Infrastructure (not Ad-Hoc)
Click both auto connect and available to all users
Security tab set up to match your wireless router Protection

---

### Post by hungry&amp; on 2011-09-02
praseodym & nm_geo I thank you from the bottom of my heart. I'm typing this from my Linux laptop now. Looking forward to using it to it's full potential. Thanks again! :]

---

### Post by nm_geo on 2011-09-02
> **hungry& said:**
> praseodym & nm_geo I thank you from the bottom of my heart. I'm typing this from my Linux laptop now. Looking forward to using it to it's full potential. Thanks again! :]
 
Glad you got it working.. praseodym did the heavy lifting I just explained what he had told you..  Please go to top and marked Solved.. It may help other searchers.

---

