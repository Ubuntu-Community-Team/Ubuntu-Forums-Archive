---
title: "Hardware switch faulty - RTL 81915 won't work"
date: 2011-09-07
forum: Networking &amp; Wireless
---

### Post by aguilla1 on 2011-09-07
Since my hardware switch is off permanently, Ubuntu disables any wireless modem.
I use Ubuntu 11.04. The system sees the internal modem: Broadband BCM 4312 802.11 b/g LP_PHy as well as the USB plugged in modem: Manufacturer Realtek RTL 81915 WLAN adapter but disables them both due to the faulty switch.
 
I am looking for a software change / setting that will allow me to bypass the hardware switch so that one or the other modem will work.
 
For Visa, the Realtek RTL 81915 works even if the hardware switch is turned off.
 
August Guillaume

---

### Post by praseodym on 2011-09-07
Hi,

what PC/note-/netbook do you use? Can you show the terminal outputs of:

```
lspci -nnk | grep -iA2 net
lsusb #with stick
lsmod
rfkill list
cat /etc/udev/rules.d/70-persistent-net.rules
iwconfig
sudo iwlist scan
```

---

### Post by aguilla1 on 2011-09-07
lspci -nnk | grep -iA2 net05:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd. 88E8039 PCI-E Fast Ethernet Controller [11ab:4353] (rev 14)
	Subsystem: Hewlett-Packard Company Device [103c:30cd]
	Kernel driver in use: sky2
--
07:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01)
	Subsystem: Hewlett-Packard Company BCM4312 802.11b/g Wireless LAN Controller [103c:137c]
	Kernel driver in use: wl

lsusb #with stick
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 002: ID 046d:c019 Logitech, Inc. Optical Tilt Wheel Mouse
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 004: ID 0bda:8172 Realtek Semiconductor Corp. RTL8191S WLAN Adapter
Bus 002 Device 003: ID 04f2:b016 Chicony Electronics Co., Ltd VGA 30fps UVC Webcam
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

lsmod
Module                  Size  Used by
r8712u                281937  0 
binfmt_misc            13213  1 
parport_pc             32111  1 
ppdev                  12849  0 
snd_hda_codec_conexant    43782  1 
snd_hda_intel          24113  2 
snd_hda_codec          90901  2 snd_hda_codec_conexant,snd_hda_intel
snd_hwdep              13274  1 snd_hda_codec
snd_pcm                80042  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
joydev                 17322  0 
snd_rawmidi            25269  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
hp_wmi                 13418  0 
sparse_keymap          13666  1 hp_wmi
i915                  451033  3 
uvcvideo               66851  0 
r852                   17878  0 
videodev               75143  1 uvcvideo
sm_common              16737  1 r852
snd_timer              28659  2 snd_pcm,snd_seq
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
psmouse                73312  0 
serio_raw              12990  0 
nand                   49822  2 r852,sm_common
snd                    55295  13 snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
drm_kms_helper         40745  1 i915
lib80211_crypt_tkip    17203  0 
nand_ids                8547  1 nand
soundcore              12600  1 snd
nand_ecc               13070  1 nand
mtd                    26720  2 sm_common,nand
drm                   184164  4 i915,drm_kms_helper
wl                   2642531  0 
i2c_algo_bit           13184  1 i915
lib80211               14570  2 lib80211_crypt_tkip,wl
snd_page_alloc         14073  2 snd_hda_intel,snd_pcm
lp                     13349  0 
video                  18951  1 i915
parport                36746  3 parport_pc,ppdev,lp
usbhid                 41704  0 
hid                    77084  1 usbhid
ahci                   21591  5 
firewire_ohci          31504  0 
libahci                25548  1 ahci
sdhci_pci              13623  0 
sky2                   49172  0 
sdhci                  22720  1 sdhci_pci
firewire_core          56138  1 firewire_ohci
crc_itu_t              12627  1 firewire_core

rfkill list
0: brcmwl-0: Wireless LAN
	Soft blocked: yes
	Hard blocked: yes
1: hp-wifi: Wireless LAN
	Soft blocked: yes
	Hard blocked: no

cat /etc/udev/rules.d/70-persistent-net.rules
# This file maintains persistent names for network interfaces.
# See udev(7) for syntax.
#
# Entries are automatically added by the 75-persistent-net-generator.rules
# file; however you are also free to add your own entries.

# PCI device 0x11ab:0x4353 (sky2)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:1d:72:45:3b:e5", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x14e4:0x4315 (b43-pci-bridge)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:1a:73:de:bb:d1", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

# PCI device 0x14e4:0x4315 (wl)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:1a:73:de:bb:d1", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth1"

# USB device 0x0bda:0x8172 (usb)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:02:72:9f:0a:9b", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan1"

iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11  Access Point: Not-Associated   
          Link Quality:5  Signal level:0  Noise level:0
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0

wlan1     unassociated  Nickname:"rtl_wifi"
          Mode:Managed  Access Point: Not-Associated   Sensitivity:0/0  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sudo iwlist scan
[sudo] password for harriette: 
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Failed to read scan data : Invalid argument

wlan1     No scan results

---

### Post by praseodym on 2011-09-07
Blacklist the following module:

```
echo "blacklist brcm80211" | sudo tee /etc/modprobe.d/blacklist-brcm80211.conf
```
reboot and:

```
sudo rfkill unblock all
sudo service network-manager restart
```
Check:
```

rfkill list
iwconfig
sudo iwlist scan
dmesg | egrep 'r8|wl|brcm|radio|switch'
```
What kind of computer is that (manufacturer)?

---

### Post by aguilla1 on 2011-09-08
Here are the results.

Much appreciate the work you did to help. I just unplugged the direct connection. Now both modems work again. The internal as well as the external modem. The switch is also working..

The computer is HP-Pavilion-dv2700-Notebook-PC
Manufacturer - HP as far as I can tell.

- AG

rfkill list
0: hp-wifi: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: brcmwl-0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11  Access Point: Not-Associated   
          Link Quality:4  Signal level:196  Noise level:199
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0

wlan1     IEEE 802.11bg  ESSID:"sixtystreetwonder1"  Nickname:"rtl_wifi"
          Mode:Managed  Frequency:2.437 GHz  Access Point: 38:7C:27:B7:60:D9   
          Bit Rate:54 Mb/s   Sensitivity:0/0  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=100/100  Signal level=100/100  Noise level=0/100
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Scan completed :
          Cell 01 - Address: 00:0F:66:25:48:49
                    ESSID:"Vozdoqueclarmanodeserto"
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:1/5  Signal level:-80 dBm  Noise level:-92 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
          Cell 02 - Address: 38:7C:27:B7:60:D9
                    ESSID:"sixtystreetwonder1"
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:4/5  Signal level:-58 dBm  Noise level:-92 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
          Cell 03 - Address: 00:1A:C4:55:48:B1
                    ESSID:"2WIRE673"
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:2/5  Signal level:-75 dBm  Noise level:-92 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
          Cell 04 - Address: 00:21:29:CC:A2:0B
                    ESSID:"bluesky"
                    Mode:Managed
                    Frequency:2.412 GHz (Channel 1)
                    Quality:2/5  Signal level:-76 dBm  Noise level:-92 dBm
                    IE: Unknown: DD710050F204104A0001101044000102103B00010310470010002129CCA209002129CCA2090400E8001021000C4C696E6B73797320496E632E102300075752543331304E1024000776312E30302E34104200033030301054000800060050F2040001101100075752543331304E100800020088
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s

wlan1     Scan completed :
          Cell 01 - Address: 38:7C:27:B7:60:D9
                    ESSID:"sixtystreetwonder1"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Signal level=100/100  
          Cell 02 - Address: 00:21:29:CC:A2:0B
                    ESSID:"bluesky"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:wpa_ie
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD710050F204104A0001101044000102103B00010310470010002129CCA209002129CCA2090400E8001021000C4C696E6B73797320496E632E102300075752543331304E1024000776312E30302E34104200033030301054000800060050F2040001101100075752543331304E100800020088
                    Signal level=46/100  
          Cell 03 - Address: 00:0F:66:25:48:49
                    ESSID:"Vozdoqueclarmanodeserto"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Signal level=46/100 

dmesg | egrep 'r8|wl|brcm|radio|switch'
[    0.000000] DMI: Hewlett-Packard HP Pavilion dv2700 Notebook PC/30CD, BIOS F.26 01/21/2008
[   11.049418] wl: module license 'MIXED/Proprietary' taints kernel.
[   11.070620] wl 0000:07:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[   11.070630] wl 0000:07:00.0: setting latency timer to 64
[   11.249659] r8712u: module is from the staging directory, the quality is unknown, you have been warned.
[   11.254693] r8712u: DriverVersion: v7_0.20100831
[   11.254713] r8712u: register rtl8712_netdev_ops to netdev_ops
[   11.254716] r8712u: USB_SPEED_HIGH with 4 endpoints
[   11.255288] r8712u: Boot from EFUSE: Autoload OK
[   11.396115] r852 0000:08:09.3: PCI INT B -> GSI 18 (level, low) -> IRQ 18
[   11.396412] r852: driver loaded succesfully
[   11.906161] r8712u: CustomerID = 0x0000
[   11.906168] r8712u: MAC Address from efuse = 00:02:72:9f:0a:9b
[   11.907121] usbcore: registered new interface driver r8712u
[   11.975412] Console: switching to colour frame buffer device 160x50
[   12.108777] <30>udev[373]: renamed network interface wlan0 to wlan1
[  107.452534] r8712u: 1 RCR=0x153f00e
[  107.453275] r8712u: 2 RCR=0x553f00e
[  107.560735] ADDRCONF(NETDEV_UP): wlan1: link is not ready
[  125.501057] r8712u: wpa_set_encryption, crypt.alg = WEP
[  125.888628] ADDRCONF(NETDEV_CHANGE): wlan1: link becomes ready
[  136.296034] wlan1: no IPv6 routers present
[  145.964647] ADDRCONF(NETDEV_UP): wlan1: link is not ready
[  156.235198] r8712u: wpa_set_encryption, crypt.alg = WEP
[  156.593253] ADDRCONF(NETDEV_CHANGE): wlan1: link becomes ready
[  167.416026] wlan1: no IPv6 routers present

---

### Post by praseodym on 2011-09-08
:popcorn:

Looks good. If the problem is solved you can mark the thread [SOLVED] by editing the headline of the first postin (pull-down-menu).

---

### Post by aguilla1 on 2011-09-09
I thought I did mark it 'solved', but now can not find the drop down menu!
I clicked on 'edit' for the message but there was no way to mark it that I could find! Ubuntu should make it a lot easier and obvious to mark items 'solved'.
I had to resubmit the order to "blacklist brcm80211" yesterday!

August

---

### Post by praseodym on 2011-09-10
Try this:

after reboot, if its not blocked (means: it is blacklisted):

```
sudo depmod -a
sudo update-initramfs -u
```

---

