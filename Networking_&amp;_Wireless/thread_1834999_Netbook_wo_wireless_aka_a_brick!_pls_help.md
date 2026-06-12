---
title: "Netbook wo wireless aka a brick! pls help"
date: 2011-08-28
forum: Networking &amp; Wireless
---

### Post by IanUbu on 2011-08-28
OK guys, I have tried reading all the posts I can find and I'm just confusing myself, so its time to ask for help.

Bought a new Samsung N150 with Windoze7 preinstalled, all worked well and I had wired and wireless connections. Having sorted my Windoze software as I wanted I quickly moved onto setting up a dual boot for Ubuntu through a USB stick. All went well and Ubuntu seemed to be working well, but having used Ubuntu on my old laptop I nervously tested the wireless to find it didn't work. First thought was, 'No problem I still have the bookmarked solution from last time' unfortunately that didn't work this time.  I have tried a number of combinations of drivers but without success, only the wired connection works. What makes this an even bigger mess is that Windoze7 doesn't work wired or wireless anymore!

I'll try to provide as much information as I can, please help as this purchase is turning into an expensive brick!

nm-tool with wired connection
> 
NetworkManager Tool

State: connected

- Device: eth0  [Auto eth0] ----------------------------------------------------
  Type:              Wired
  Driver:            sky2
  State:             connected
  Default:           yes
  HW Address:        E8:11:32:09:3D:CB

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.0.4
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.1

    DNS:             4.4.4.4
    DNS:             8.8.8.8


- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            brcm80211
  State:             disconnected
  Default:           no
  HW Address:        00:1B:B1:EB:50:7E

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points
nm-tool with wired disconnected
> 
NetworkManager Tool

State: disconnected

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            sky2
  State:             unavailable
  Default:           no
  HW Address:        E8:11:32:09:3D:CB

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         off


- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            brcm80211
  State:             disconnected
  Default:           no
  HW Address:        00:1B:B1:EB:50:7E

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 
ifconfig
> 
eth0      Link encap:Ethernet  HWaddr e8:11:32:09:3d:cb  
          inet addr:192.168.0.4  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::ea11:32ff:fe09:3dcb/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5831 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6288 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:5480933 (5.4 MB)  TX bytes:940355 (940.3 KB)
          Interrupt:18 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:108 errors:0 dropped:0 overruns:0 frame:0
          TX packets:108 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:8192 (8.1 KB)  TX bytes:8192 (8.1 KB)

wlan0     Link encap:Ethernet  HWaddr 00:1b:b1:eb:50:7e  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
sudo iwlist scan
> 
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     No scan results
lsmod
> 
Module                  Size  Used by
b43                   296610  0 
ssb                    45942  1 b43
easy_slow_down_manager    12985  0 
parport_pc             32111  0 
ppdev                  12849  0 
snd_hda_codec_realtek   255882  1 
snd_hda_intel          24113  2 
snd_hda_codec          90901  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13274  1 snd_hda_codec
binfmt_misc            13213  1 
snd_pcm                80042  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
arc4                   12473  2 
snd_rawmidi            25269  1 snd_seq_midi
rfcomm                 38125  8 
joydev                 17322  0 
snd_seq_midi_event     14475  1 snd_seq_midi
sco                    17827  2 
i915                  451033  3 
bnep                   17785  2 
l2cap                  48656  16 rfcomm,bnep
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
brcm80211             690413  0 
snd_timer              28659  2 snd_pcm,snd_seq
mac80211              257001  2 b43,brcm80211
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
uvcvideo               66851  0 
btusb                  18160  1 
samsung_backlight      13487  0 
psmouse                73312  0 
bluetooth              65493  9 rfcomm,sco,bnep,l2cap,btusb
drm_kms_helper         40745  1 i915
videodev               75143  1 uvcvideo
snd                    55295  13 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
serio_raw              12990  0 
drm                   184164  4 i915,drm_kms_helper
cfg80211              156212  3 b43,brcm80211,mac80211
soundcore              12600  1 snd
snd_page_alloc         14073  2 snd_hda_intel,snd_pcm
i2c_algo_bit           13184  1 i915
video                  18951  1 i915
lp                     13349  0 
parport                36746  3 parport_pc,ppdev,lp
ahci                   21591  2 
libahci                25548  1 ahci
sky2                   49172  0 
rfkill list all
> 
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
Thanks for your help,
Ian

---

### Post by IanUbu on 2011-08-31
Despite providing as much info as I could no one seems to have any suggestions.

Whilst I've been waiting I have reinstalled Ubuntu back to a clean load version and still no luck. I have however sorted Windows 7, which I am very surprised about as I thought Ubuntu would be the easiest to solve because I was expecting a genius in here to point out my stupid error. As it is Windoze has won!!! I hate Windows so not very happy now, please restore my faith and help me get Ubuntu wireless to work so I don't have to give up on it completely.

---

### Post by bkratz on 2011-08-31
> **IanUbu said:**
> Despite providing as much info as I could no one seems to have any suggestions.

Whilst I've been waiting I have reinstalled Ubuntu back to a clean load version and still no luck. I have however sorted Windows 7, which I am very surprised about as I thought Ubuntu would be the easiest to solve because I was expecting a genius in here to point out my stupid error. As it is Windoze has won!!! I hate Windows so not very happy now, please restore my faith and help me get Ubuntu wireless to work so I don't have to give up on it completely.

What wireless chipset is being used? Please do a 

lspci -vnn | grep 14e4

and post the results.  I am a bit confused by your lsmod  vrs. Nm-tool One shows both b43,ssb and the other the new brcm80211 driver.  I think there are still only a few Broadcom cards that use this driver (but I could be wrong). The ones that come to mind are:

BCM4313---- 0x4727
BCM43224--- 0x4353
BCM43225--- 0x4357

Perhaps there is a conflict.

---

### Post by IanUbu on 2011-09-05
Sorry for the delay I have been away and annoyingly unable to use the wireless! Thanks for your help with this, the out put was:

> 05:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller [14e4:4727] (rev 01)


---

### Post by praseodym on 2011-09-05
Hello,

for this device you need the Broadcom-STA-driver. You can install it via cable connection using "Additional drivers"

---

### Post by IanUbu on 2011-09-06
Okay I wiped Ubuntu and reinstalled since I had made a lot f changes trying to solve the problem. We are now starting from a clean install of 11.04

This includes installing the Broadcom proprietary wireless driver under the additional drivers option

Still no luck! What is my next step?

---

### Post by praseodym on 2011-09-06
Ok, 

now show (again):

```
lspci -nnk | grep -iA2 net
lsmod
ifconfig -a
cat /etc/udev/rules.d/70-persistent-net.rules
iwconfig
rfkill list
sudo iwlist scan
```

---

### Post by IanUbu on 2011-09-09
lspci -nnk | grep -iA2 net

> 05:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller [14e4:4727] (rev 01)
    Subsystem: Wistron NeWeb Corp. Device [185f:051a]
    Kernel driver in use: wl
--
09:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd. 88E8040 PCI-E Fast Ethernet Controller [11ab:4354]
    Subsystem: Samsung Electronics Co Ltd Device [144d:c072]
    Kernel driver in use: sky2


lsmod

> 
Module                  Size  Used by
parport_pc             32111  0 
ppdev                  12849  0 
binfmt_misc            13213  1 
snd_hda_codec_realtek   255882  1 
rfcomm                 38125  8 
snd_hda_intel          24113  2 
sco                    17827  2 
bnep                   17785  2 
snd_hda_codec          90901  2 snd_hda_codec_realtek,snd_hda_intel
l2cap                  48656  16 rfcomm,bnep
snd_hwdep              13274  1 snd_hda_codec
joydev                 17322  0 
snd_pcm                80042  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25269  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28659  2 snd_pcm,snd_seq
uvcvideo               66851  0 
i915                  451033  3 
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
btusb                  18160  2 
videodev               75143  1 uvcvideo
bluetooth              65493  9 rfcomm,sco,bnep,l2cap,btusb
lib80211_crypt_tkip    17203  0 
psmouse                73312  0 
wl                   2642531  0 
snd                    55295  13 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
serio_raw              12990  0 
drm_kms_helper         40745  1 i915
drm                   184164  4 i915,drm_kms_helper
lib80211               14570  2 lib80211_crypt_tkip,wl
soundcore              12600  1 snd
snd_page_alloc         14073  2 snd_hda_intel,snd_pcm
i2c_algo_bit           13184  1 i915
video                  18951  1 i915
lp                     13349  0 
parport                36746  3 parport_pc,ppdev,lp
ahci                   21591  2 
libahci                25548  1 ahci
sky2                   49172  0 


ifconfig -a

> eth0      Link encap:Ethernet  HWaddr e8:11:32:09:3d:cb  
          inet addr:192.168.0.5  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::ea11:32ff:fe09:3dcb/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:15704 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10946 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:22591291 (22.5 MB)  TX bytes:928352 (928.3 KB)
          Interrupt:18 

eth1      Link encap:Ethernet  HWaddr 00:1b:b1:eb:50:7e  
          inet6 addr: fe80::21b:b1ff:feeb:507e/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:16 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:960 (960.0 B)  TX bytes:960 (960.0 B)



cat /etc/udev/rules.d/70-persistent-net.rules

> # This file maintains persistent names for network interfaces.
# See udev(7) for syntax.
#
# Entries are automatically added by the 75-persistent-net-generator.rules
# file; however you are also free to add your own entries.

# PCI device 0x11ab:0x4354 (sky2)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="e8:11:32:09:3d:cb", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x14e4:0x4727 (brcm80211)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:1b:b1:eb:50:7e", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

# PCI device 0x14e4:0x4727 (wl)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:1b:b1:eb:50:7e", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth1"



iwconfig
> 
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11  Access Point: Not-Associated   
          Link Quality:5  Signal level:0  Noise level:245
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0


rfkill list

> 0: brcmwl-0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no


sudo iwlist scan
> 
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      No scan results


Thanks for all your help, wish I understood half of this!

---

### Post by praseodym on 2011-09-10
Blacklist the module:

```
echo "blacklist brcm80211" | sudo tee /etc/modprobe.d/blacklist-brcm80211.conf
```
and reboot.

---

### Post by IanUbu on 2011-09-10
I tried that code and went to the folder to check and the blacklist file was there with  "blacklist brcm80211" as the only entry (without the " s)
 
I rebooted and it still doesn't work, please help

---

### Post by praseodym on 2011-09-10
Try to remove your current profile and create a new one. Check:

```
iwconfig
rfkill list
sudo iwlist scan
dmesg | grep wl
lsmod
```

---

### Post by IanUbu on 2011-09-10
All the new account did was remove all of my settings and email setup etc!

iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11  Access Point: Not-Associated   
          Link Quality:5  Signal level:0  Noise level:246
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0


rfkill list
0: brcmwl-0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no


sudo iwlist scan
[sudo] password for ian: 
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      No scan results


dmesg | grep wl
[   15.835138] wl: module license 'MIXED/Proprietary' taints kernel.
[   16.070861] wl 0000:05:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   16.070887] wl 0000:05:00.0: setting latency timer to 64


lsmod
Module                  Size  Used by
parport_pc             32111  0 
ppdev                  12849  0 
snd_hda_codec_realtek   255882  1 
binfmt_misc            13213  1 
snd_hda_intel          24113  2 
rfcomm                 38125  8 
snd_hda_codec          90901  2 snd_hda_codec_realtek,snd_hda_intel
sco                    17827  2 
bnep                   17785  2 
snd_hwdep              13274  1 snd_hda_codec
l2cap                  48656  16 rfcomm,bnep
joydev                 17322  0 
snd_pcm                80042  2 snd_hda_intel,snd_hda_codec
i915                  451033  3 
snd_seq_midi           13132  0 
snd_rawmidi            25269  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28659  2 snd_pcm,snd_seq
btusb                  18160  2 
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
uvcvideo               66851  0 
psmouse                73312  0 
bluetooth              65493  9 rfcomm,sco,bnep,l2cap,btusb
serio_raw              12990  0 
videodev               75143  1 uvcvideo
drm_kms_helper         40745  1 i915
lib80211_crypt_tkip    17203  0 
drm                   184164  4 i915,drm_kms_helper
wl                   2642531  0 
snd                    55295  13 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
i2c_algo_bit           13184  1 i915
video                  18951  1 i915
lib80211               14570  2 lib80211_crypt_tkip,wl
soundcore              12600  1 snd
snd_page_alloc         14073  2 snd_hda_intel,snd_pcm
lp                     13349  0 
parport                36746  3 parport_pc,ppdev,lp
ahci                   21591  2 
libahci                25548  1 ahci
sky2                   49172  0

---

### Post by praseodym on 2011-09-10
Try a WPA2-AES encryption instead of WPA or mixed WPA/WPA2. Otherwise you can try Wicd instead of the network-manager.

---

