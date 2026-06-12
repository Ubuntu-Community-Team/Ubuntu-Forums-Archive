---
title: "Device not ready firmware missing"
date: 2011-10-31
forum: Networking &amp; Wireless
---

### Post by different_guy on 2011-10-31
Hello dear Ubuntu mates,

I know there are similar and maybe identical threads as mine and I am sorry for opening a new one but I can not solve my problem.

Okay, here it goes. I have HP Probook 4510s. It has Broadcom wireless card in it. And today, I have installed fresh copy of Ubuntu 11.10. Everything is okay but wireless. It says: device not ready, firmware missing. I really do not know why is this happening because I am playing with Ubuntu since 9.10 if memory serves me well and never had issue with wireless. I have tried solutions mentioned in other threads but with no luck. Here is what I have tried: [http://wireless.kernel.org/en/users/Drivers/b43#firmwareinstallation](http://wireless.kernel.org/en/users/Drivers/b43#firmwareinstallation)
[http://ubuntuforums.org/showthread.php?t=1780744](http://ubuntuforums.org/showthread.php?t=1780744)
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#Installing%20STA%20drivers](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#Installing%20STA%20drivers)

I do not have ethernet cable so I am without any means of internet connection.  

It is obvious that I am doing something wrong but question is what. All suggestions are most welcome. Thank you in advance!

---

### Post by wildmanne39 on 2011-10-31
Hi, please post the results of:
```
cat /etc/lsb-release; uname -a
```
```
lspci -nnk | grep -iA2 net
```
```
iwconfig
```
```
rfkill list all
```
```
lsmod
```
by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

### Post by wildmanne39 on 2011-10-31
Wrong thread.

---

### Post by different_guy on 2011-10-31
Hey wildmanne39. You still want me to copy the results of those commands or?

---

### Post by wildmanne39 on 2011-10-31
Hi, Yes
Thank you

---

### Post by different_guy on 2011-10-31
Here you go mate:


Code:
cat /etc/lsb-release; uname -a
Result:
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.10
DISTRIB_CODENAME=oneiric
DISTRIB_DESCRIPTION="Ubuntu 11.10"
Linux different-HP-ProBook-4510s 3.0.0-12-generic #20-Ubuntu SMP Fri Oct 7 14:50:42 UTC 2011 i686 i686 i386 GNU/Linux


Code:
lspci -nnk | grep -iA2 net
Result:
03:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01)
	Subsystem: Hewlett-Packard Company Device [103c:1508]
	Kernel driver in use: b43-pci-bridge
--
86:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd. 88E8072 PCI-E Gigabit Ethernet Controller [11ab:436c] (rev 10)
	Subsystem: Hewlett-Packard Company Device [103c:3074]
	Kernel driver in use: sky2


Code:
iwconfig
Result:
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on


Code:
rfkill list all
Result:
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: hp-wifi: Wireless LAN
	Soft blocked: no
	Hard blocked: no
2: hp-bluetooth: Bluetooth
	Soft blocked: yes
	Hard blocked: no


Code:
lsmod
Result:
Module                  Size  Used by
nls_iso8859_1          12617  1 
nls_cp437              12751  1 
vfat                   17308  1 
fat                    55577  1 vfat
usb_storage            44173  1 
uas                    17699  0 
parport_pc             32114  0 
ppdev                  12849  0 
snd_hda_codec_hdmi     31426  1 
bnep                   17923  2 
rfcomm                 38408  0 
bluetooth             148839  10 bnep,rfcomm
snd_hda_codec_analog    75090  1 
joydev                 17393  0 
hp_wmi                 13652  0 
sparse_keymap          13658  1 hp_wmi
usbhid                 41905  0 
hid                    77367  1 usbhid
uvcvideo               67271  0 
videodev               85626  1 uvcvideo
snd_hda_intel          24262  3 
snd_hda_codec          91754  3 snd_hda_codec_hdmi,snd_hda_codec_analog,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
arc4                   12473  2 
snd_seq_midi           13132  0 
psmouse                73673  0 
snd_pcm                80468  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
serio_raw              12990  0 
snd_rawmidi            25241  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
b43                   318816  0 
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
mac80211              272785  1 b43
cfg80211              172392  2 b43,mac80211
binfmt_misc            17292  1 
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    55902  16 snd_hda_codec_hdmi,snd_hda_codec_analog,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
radeon                925020  3 
wmi                    18744  1 hp_wmi
hp_accel               21632  0 
soundcore              12600  1 snd
lis3lv02d              19280  1 hp_accel
video                  18908  0 
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
input_polldev          13648  1 lis3lv02d
ttm                    65224  1 radeon
drm_kms_helper         32889  1 radeon
drm                   192226  5 radeon,ttm,drm_kms_helper
i2c_algo_bit           13199  1 radeon
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
sky2                   49317  0 
ssb                    50682  1 b43

Can I download drivers or firmware on work and just install them on my machine? If so, which drivers should I look for?

Thanks for helping!

---

### Post by TBABill on 2011-10-31
Connect via ethernet and then go to Additional Drivers. Select the STA driver, activate and then either restart or ```
sudo modprobe wl
``` The driver install should care for blacklisting the open source b43 driver, but in case it does not (check via lsmod output after the driver completes its install) then just ```
gksudo gedit /etc/modprobe.d/blacklist.conf
``` and add the following to the file and save ```
blacklist b43 
blacklist ssb
``` If you have to add that blacklist item, then you can just ```
sudo modprobe -r b43 ssb wl
``` and then ```
sudo modprobe wl
```

---

### Post by different_guy on 2011-10-31
Okay, I will try to do that tomorrow. Thanks! But can I somehow install drivers and firmware without internet connection? I have tried to install some packages from Ubuntu installation disc and when I double click it, Software Center opens but I can not click on install. Strange.

---

### Post by wildmanne39 on 2011-10-31
Hi, this card is suppose to work with the wl driver or the b43 in 11.10 but not both at the same time.

We should trouble shoot this a little further before switching drivers in my opinion.

Please post the results of:
```
nm-tool
```
```
sudo iwlist scan
```
```
iwlist chan
```
If you have a wired connection unplug it, although I am pretty sure you do not, then run this command also.
```
sudo cat /var/log/syslog | grep -e b43 -e firmware -e wlan -e etwork | tail -n45
```
Thank you

---

### Post by different_guy on 2011-10-31
Thanks for helping wildmanne39. I really appreciate it.


Code:
nm-tool
result:
NetworkManager Tool

State: disconnected

- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            b43
  State:             unavailable
  Default:           no
  HW Address:        0C:60:76:77:7B:FC

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            sky2
  State:             unavailable
  Default:           no
  HW Address:        18:A9:05:85:3D:50

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off


Code:
sudo iwlist scan
result:
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Interface doesn't support scanning : Network is down


Code:
iwlist chan
result:
lo        no frequency information.

eth0      no frequency information.

wlan0     14 channels in total; available frequencies :
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


Code:
sudo cat /var/log/syslog | grep -e b43 -e firmware -e wlan -e etwork | tail -n45
result:
Oct 31 22:54:43 different-HP-ProBook-4510s NetworkManager[570]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1c.5/0000:86:00.0/net/eth0, iface: eth0): no ifupdown configuration found.
Oct 31 22:54:43 different-HP-ProBook-4510s NetworkManager[570]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/lo, iface: lo)
Oct 31 22:54:43 different-HP-ProBook-4510s NetworkManager[570]:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/lo, iface: lo): no ifupdown configuration found.
Oct 31 22:54:43 different-HP-ProBook-4510s NetworkManager[570]:    SCPlugin-Ifupdown: end _init.
Oct 31 22:54:43 different-HP-ProBook-4510s NetworkManager[570]: <info> Loaded plugin ifupdown: (C) 2008 Canonical Ltd.  To report bugs please use the NetworkManager mailing list.
Oct 31 22:54:43 different-HP-ProBook-4510s NetworkManager[570]: <info> Loaded plugin keyfile: (c) 2007 - 2010 Red Hat, Inc.  To report bugs please use the NetworkManager mailing list.
Oct 31 22:54:43 different-HP-ProBook-4510s NetworkManager[570]:    Ifupdown: get unmanaged devices count: 0
Oct 31 22:54:43 different-HP-ProBook-4510s NetworkManager[570]:    SCPlugin-Ifupdown: (161080544) ... get_connections.
Oct 31 22:54:43 different-HP-ProBook-4510s NetworkManager[570]:    SCPlugin-Ifupdown: (161080544) ... get_connections (managed=false): return empty list.
Oct 31 22:54:43 different-HP-ProBook-4510s NetworkManager[570]:    Ifupdown: get unmanaged devices count: 0
Oct 31 22:54:43 different-HP-ProBook-4510s NetworkManager[570]: <info> modem-manager is now available
Oct 31 22:54:43 different-HP-ProBook-4510s NetworkManager[570]: <info> monitoring kernel firmware directory '/lib/firmware'.
Oct 31 22:54:43 different-HP-ProBook-4510s NetworkManager[570]: <info> found WiFi radio killswitch rfkill0 (at /sys/devices/pci0000:00/0000:00:1c.1/0000:03:00.0/ssb0:0/ieee80211/phy0/rfkill0) (driver (unknown))
Oct 31 22:54:43 different-HP-ProBook-4510s NetworkManager[570]: <info> WiFi enabled by radio killswitch; enabled by state file
Oct 31 22:54:43 different-HP-ProBook-4510s NetworkManager[570]: <info> WWAN enabled by radio killswitch; enabled by state file
Oct 31 22:54:43 different-HP-ProBook-4510s NetworkManager[570]: <info> WiMAX enabled by radio killswitch; enabled by state file
Oct 31 22:54:43 different-HP-ProBook-4510s NetworkManager[570]: <info> Networking is enabled by state file
Oct 31 22:54:43 different-HP-ProBook-4510s NetworkManager[570]: <info> (wlan0): driver supports SSID scans (scan_capa 0x01).
Oct 31 22:54:43 different-HP-ProBook-4510s NetworkManager[570]: <info> (wlan0): new 802.11 WiFi device (driver: 'b43' ifindex: 3)
Oct 31 22:54:43 different-HP-ProBook-4510s NetworkManager[570]: <info> (wlan0): exported as /org/freedesktop/NetworkManager/Devices/0
Oct 31 22:54:43 different-HP-ProBook-4510s NetworkManager[570]: <info> (wlan0): now managed
Oct 31 22:54:43 different-HP-ProBook-4510s NetworkManager[570]: <info> (wlan0): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Oct 31 22:54:43 different-HP-ProBook-4510s NetworkManager[570]: <info> (wlan0): bringing up device.
Oct 31 22:54:43 different-HP-ProBook-4510s kernel: [   10.629986] b43-phy0 ERROR: Firmware file "b43/ucode15.fw" not found
Oct 31 22:54:43 different-HP-ProBook-4510s kernel: [   10.629991] b43-phy0 ERROR: Firmware file "b43-open/ucode15.fw" not found
Oct 31 22:54:43 different-HP-ProBook-4510s kernel: [   10.629994] b43-phy0 ERROR: You must go to [http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware](http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware for this driver version. Please carefully read all instructions on this website.
Oct 31 22:54:43 different-HP-ProBook-4510s NetworkManager[570]: <warn> (wlan0): firmware may be missing.
Oct 31 22:54:43 different-HP-ProBook-4510s NetworkManager[570]: <info> (wlan0): deactivating device (reason 'managed') [2]
Oct 31 22:54:43 different-HP-ProBook-4510s NetworkManager[570]: <info> (eth0): carrier is OFF
Oct 31 22:54:43 different-HP-ProBook-4510s NetworkManager[570]: <info> (eth0): new Ethernet device (driver: 'sky2' ifindex: 2)
Oct 31 22:54:43 different-HP-ProBook-4510s NetworkManager[570]: <info> (eth0): exported as /org/freedesktop/NetworkManager/Devices/1
Oct 31 22:54:43 different-HP-ProBook-4510s NetworkManager[570]: <info> (eth0): now managed
Oct 31 22:54:43 different-HP-ProBook-4510s NetworkManager[570]: <info> (eth0): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Oct 31 22:54:43 different-HP-ProBook-4510s NetworkManager[570]: <info> (eth0): bringing up device.
Oct 31 22:54:43 different-HP-ProBook-4510s NetworkManager[570]: <info> (eth0): preparing device.
Oct 31 22:54:43 different-HP-ProBook-4510s NetworkManager[570]: <info> (eth0): deactivating device (reason 'managed') [2]
Oct 31 22:54:43 different-HP-ProBook-4510s NetworkManager[570]: <info> Added default wired connection 'Wired connection 1' for /sys/devices/pci0000:00/0000:00:1c.5/0000:86:00.0/net/eth0
Oct 31 22:54:43 different-HP-ProBook-4510s NetworkManager[570]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/lo, iface: lo)
Oct 31 22:54:43 different-HP-ProBook-4510s NetworkManager[570]:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/lo, iface: lo): no ifupdown configuration found.
Oct 31 22:54:43 different-HP-ProBook-4510s NetworkManager[570]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1c.1/0000:03:00.0/ssb0:0/net/wlan0, iface: wlan0)
Oct 31 22:54:43 different-HP-ProBook-4510s NetworkManager[570]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1c.1/0000:03:00.0/ssb0:0/net/wlan0, iface: wlan0): no ifupdown configuration found.
Oct 31 22:54:43 different-HP-ProBook-4510s NetworkManager[570]: <warn> bluez error getting default adapter: The name org.bluez was not provided by any .service files
Oct 31 22:54:43 different-HP-ProBook-4510s kernel: [   10.765312] type=1400 audit(1320116083.783:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=818 comm="apparmor_parser"
Oct 31 22:54:44 different-HP-ProBook-4510s NetworkManager[570]: <warn> bluez error getting default adapter: No such adapter
Oct 31 22:54:44 different-HP-ProBook-4510s NetworkManager[570]: <info> found WiFi radio killswitch rfkill1 (at /sys/devices/platform/hp-wmi/rfkill/rfkill1) (driver hp-wmi)

---

### Post by wildmanne39 on 2011-10-31
Hi, it looks like you are missing the firmware we can try to get it working with this driver, and if we can not we will have to switch to the wl driver.

Download the b43 zip file to a flash drive then drag and drop the file to your ubuntu desktop. Right-click it and select Extract Here. Open a terminal and do:
```
sudo mkdir /lib/firmware/b43
sudo cp Desktop/b43/*  /lib/firmware/b43
sudo rmmod -f b43
sudo rmmod -f ssb
sudo modprobe b43
```
run the commands one line at a time.
Thank you

---

### Post by different_guy on 2011-10-31
wildmanne39, thank you! It worked. If you ever come to Croatia, contact me. Six pack is yours. Cheers my mate!

---

### Post by wildmanne39 on 2011-10-31
Hi, your welcome! would you please go to the top of the page and mark this thread solved by clicking on thread tools. Thank you so much.
Enjoy

---

### Post by rrubi on 2011-11-03
Thanks a lot!

I had the same Firmware problem and it also worked on my Wireless Card ''Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller [14e4:4318] (rev 02)''

Cheers!

---

### Post by wildmanne39 on 2011-11-03
Hi rrubi, your welcome! 
Enjoy

---

### Post by firebird21 on 2011-12-04
Hi, Thanks a lot! 
I had the same issue..firmware missing..It worked like magic.

cheers,

---

### Post by tnymch on 2011-12-09
Hi im having the exact same problem but the firmware I should be looking for is not b43, instead is b57 and I cant find it anywhere.
Hope this can help somehow:
> tnymch@Marcos-Studio-1458:~$ lspci
00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 02)
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 02)
00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)
00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 05)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 05)
00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 05)
00:1c.2 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 3 (rev 05)
00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a5)
00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 05)
00:1f.6 Signal processing controller: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem (rev 05)
02:00.0 Ethernet controller: Broadcom Corporation NetLink BCM57780 Gigabit Ethernet PCIe (rev 01)
05:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g LP-PHY (rev 01)
ff:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers (rev 02)
ff:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 02)
ff:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 02)
ff:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 02)
ff:02.2 Host bridge: Intel Corporation Core Processor Reserved (rev 02)
ff:02.3 Host bridge: Intel Corporation Core Processor Reserved (rev 02)
tnymch@Marcos-Studio-1458:~$ 

Thanks!

---

### Post by wildmanne39 on 2011-12-09
Hi, welcome to the forum! Please open a terminal ctrl+alt+t copy and paste the following commands into it one line at a time, then paste the results here:
```

cat /etc/lsb-release; uname -a
lspci -nnk | grep -iA2 net
iwconfig
rfkill list all
lsmod
```
by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

### Post by tnymch on 2011-12-09
```
tnymch@Marcos-Studio-1458:~$ cat /etc/lsb-release; uname -a
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.10
DISTRIB_CODENAME=oneiric
DISTRIB_DESCRIPTION="Ubuntu 11.10"
Linux Marcos-Studio-1458 3.0.0-13-generic #22-Ubuntu SMP Wed Nov 2 13:27:26 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux
``````
tnymch@Marcos-Studio-1458:~$ lspci -nnk | grep -iA2 net
02:00.0 Ethernet controller [0200]: Broadcom Corporation NetLink BCM57780 Gigabit Ethernet PCIe [14e4:1692] (rev 01)
    Subsystem: Dell Device [1028:0414]
    Kernel driver in use: tg3
--
05:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01)
    Subsystem: Dell Wireless 1397 WLAN Mini-Card [1028:000c]
    Kernel driver in use: b43-pci-bridge
``````
tnymch@Marcos-Studio-1458:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on

```
```
tnymch@Marcos-Studio-1458:~$ rfkill list all
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: dell-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no

``````
tnymch@Marcos-Studio-1458:~$ lsmod
Module                  Size  Used by
nls_utf8               12557  1 
isofs                  40253  1 
parport_pc             36962  0 
ppdev                  17113  0 
rfcomm                 47946  0 
bnep                   18436  2 
bluetooth             166112  10 rfcomm,bnep
joydev                 17693  0 
binfmt_misc            17540  1 
snd_hda_codec_hdmi     32040  1 
snd_hda_codec_realtek   330769  1 
dell_wmi               12681  0 
sparse_keymap          13890  1 dell_wmi
uvcvideo               72711  0 
videodev               93004  1 uvcvideo
v4l2_compat_ioctl32    17083  1 videodev
dell_laptop            13831  0 
dcdbas                 14490  1 dell_laptop
arc4                   12529  2 
snd_hda_intel          33390  2 
snd_hda_codec         104802  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
snd_pcm                96755  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30547  1 snd_seq_midi
b43                   341198  0 
snd_seq_midi_event     14899  1 snd_seq_midi
mac80211              462092  1 b43
cfg80211              199587  2 b43,mac80211
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
psmouse                73882  0 
serio_raw              13166  0 
intel_ips              18089  0 
snd_timer              29991  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    68266  14 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
i915                  566711  7 
soundcore              12680  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
drm_kms_helper         42558  1 i915
drm                   236330  3 i915,drm_kms_helper
mei                    41480  0 
i2c_algo_bit           13423  1 i915
wmi                    19256  1 dell_wmi
video                  19412  1 i915
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
ahci                   26002  3 
libahci                26861  1 ahci
ssb                    52752  1 b43
tg3                   147729  0 
```Thanks for the reply!

---

### Post by wildmanne39 on 2011-12-10
Hi, let's check a few other things please post the results of:
```
nm-tool
```
```
sudo iwlist scan
```
```
sudo cat /var/log/syslog | grep -e b43 -e firmware -e wpa -etwork | tail -n55
```
Disconnect your wired connection before you run the commands please.
Thank you

---

### Post by tnymch on 2011-12-10
```
tnymch@Marcos-Studio-1458:~$ nm-tool

NetworkManager Tool

State: disconnected

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            tg3
  State:             unavailable
  Default:           no
  HW Address:        00:24:E8:83:BA:29

  Capabilities:
    Carrier Detect:  yes
    Speed:           10 Mb/s

  Wired Properties
    Carrier:         off


- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            b43
  State:             unavailable
  Default:           no
  HW Address:        C4:17:FE:28:9B:FA

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 

``````
tnymch@Marcos-Studio-1458:~$ sudo iwlist scan
[sudo] password for tnymch: 
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Interface doesn't support scanning : Network is down

``````
tnymch@Marcos-Studio-1458:~$ sudo cat /var/log/syslog | grep -e b43 -e firmware -e wpa -etwork | tail -n55
Dec 10 02:35:50 Marcos-Studio-1458 NetworkManager[845]: <info> (wlan0): deactivating device (reason 'managed') [2]
Dec 10 02:35:50 Marcos-Studio-1458 kernel: [ 3687.600634] b43-phy0 ERROR: Firmware file "b43/ucode15.fw" not found
Dec 10 02:35:50 Marcos-Studio-1458 kernel: [ 3687.600640] b43-phy0 ERROR: Firmware file "b43-open/ucode15.fw" not found
Dec 10 02:35:50 Marcos-Studio-1458 kernel: [ 3687.600643] b43-phy0 ERROR: You must go to http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware and download the correct firmware for this driver version. Please carefully read all instructions on this website.
Dec 10 02:35:52 Marcos-Studio-1458 NetworkManager[845]: <info> (eth0): carrier now ON (device state 20)
Dec 10 02:35:52 Marcos-Studio-1458 NetworkManager[845]: <info> (eth0): device state change: unavailable -> disconnected (reason 'carrier-changed') [20 30 40]
Dec 10 02:35:52 Marcos-Studio-1458 NetworkManager[845]: <info> Auto-activating connection 'Wired connection 1'.
Dec 10 02:35:52 Marcos-Studio-1458 NetworkManager[845]: <info> Activation (eth0) starting connection 'Wired connection 1'
Dec 10 02:35:52 Marcos-Studio-1458 NetworkManager[845]: <info> (eth0): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Dec 10 02:35:52 Marcos-Studio-1458 NetworkManager[845]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) scheduled...
Dec 10 02:35:52 Marcos-Studio-1458 NetworkManager[845]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) started...
Dec 10 02:35:52 Marcos-Studio-1458 NetworkManager[845]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) scheduled...
Dec 10 02:35:52 Marcos-Studio-1458 NetworkManager[845]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) complete.
Dec 10 02:35:52 Marcos-Studio-1458 NetworkManager[845]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) starting...
Dec 10 02:35:52 Marcos-Studio-1458 NetworkManager[845]: <info> (eth0): device state change: prepare -> config (reason 'none') [40 50 0]
Dec 10 02:35:52 Marcos-Studio-1458 NetworkManager[845]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) successful.
Dec 10 02:35:52 Marcos-Studio-1458 NetworkManager[845]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) scheduled.
Dec 10 02:35:52 Marcos-Studio-1458 NetworkManager[845]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) complete.
Dec 10 02:35:52 Marcos-Studio-1458 NetworkManager[845]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) started...
Dec 10 02:35:52 Marcos-Studio-1458 NetworkManager[845]: <info> (eth0): device state change: config -> ip-config (reason 'none') [50 70 0]
Dec 10 02:35:52 Marcos-Studio-1458 NetworkManager[845]: <info> Activation (eth0) Beginning DHCPv4 transaction (timeout in 45 seconds)
Dec 10 02:35:52 Marcos-Studio-1458 NetworkManager[845]: <info> dhclient started with pid 7914
Dec 10 02:35:52 Marcos-Studio-1458 NetworkManager[845]: <info> Activation (eth0) Beginning IP6 addrconf.
Dec 10 02:35:52 Marcos-Studio-1458 NetworkManager[845]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) complete.
Dec 10 02:35:52 Marcos-Studio-1458 NetworkManager[845]: <info> (eth0): DHCPv4 state changed nbi -> preinit
Dec 10 02:35:55 Marcos-Studio-1458 NetworkManager[845]: <info> (eth0): DHCPv4 state changed preinit -> reboot
Dec 10 02:35:55 Marcos-Studio-1458 NetworkManager[845]: <info> Activation (eth0) Stage 4 of 5 (IP4 Configure Get) scheduled...
Dec 10 02:35:55 Marcos-Studio-1458 NetworkManager[845]: <info> Activation (eth0) Stage 4 of 5 (IP4 Configure Get) started...
Dec 10 02:35:55 Marcos-Studio-1458 NetworkManager[845]: <info>   address 200.127.91.19
Dec 10 02:35:55 Marcos-Studio-1458 NetworkManager[845]: <info>   prefix 24 (255.255.255.0)
Dec 10 02:35:55 Marcos-Studio-1458 NetworkManager[845]: <info>   gateway 200.127.91.1
Dec 10 02:35:55 Marcos-Studio-1458 NetworkManager[845]: <info>   hostname 'Marcos-Studio-1458'
Dec 10 02:35:55 Marcos-Studio-1458 NetworkManager[845]: <info>   nameserver '200.42.0.111'
Dec 10 02:35:55 Marcos-Studio-1458 NetworkManager[845]: <info>   nameserver '200.42.97.111'
Dec 10 02:35:55 Marcos-Studio-1458 NetworkManager[845]: <info>   nameserver '200.42.97.110'
Dec 10 02:35:55 Marcos-Studio-1458 NetworkManager[845]: <info>   nameserver '200.42.0.110'
Dec 10 02:35:55 Marcos-Studio-1458 NetworkManager[845]: <info>   nameserver '172.20.2.213'
Dec 10 02:35:55 Marcos-Studio-1458 NetworkManager[845]: <info> Activation (eth0) Stage 5 of 5 (IP Configure Commit) started...
Dec 10 02:35:56 Marcos-Studio-1458 NetworkManager[845]: <info> (eth0): device state change: ip-config -> activated (reason 'none') [70 100 0]
Dec 10 02:35:56 Marcos-Studio-1458 NetworkManager[845]: <info> Policy set 'Wired connection 1' (eth0) as default for IPv4 routing and DNS.
Dec 10 02:35:56 Marcos-Studio-1458 NetworkManager[845]: <info> Activation (eth0) successful, device activated.
Dec 10 02:35:56 Marcos-Studio-1458 NetworkManager[845]: <info> Activation (eth0) Stage 5 of 5 (IP Configure Commit) complete.
Dec 10 02:35:56 Marcos-Studio-1458 NetworkManager[845]: <info> Activation (eth0) Stage 4 of 5 (IP4 Configure Get) complete.
Dec 10 02:35:56 Marcos-Studio-1458 avahi: Avahi disabled itself. If you want to use Avahi in this network, please
Dec 10 02:36:13 Marcos-Studio-1458 NetworkManager[845]: <info> (eth0): IP6 addrconf timed out or failed.
Dec 10 02:36:13 Marcos-Studio-1458 NetworkManager[845]: <info> Activation (eth0) Stage 4 of 5 (IP6 Configure Timeout) scheduled...
Dec 10 02:36:13 Marcos-Studio-1458 NetworkManager[845]: <info> Activation (eth0) Stage 4 of 5 (IP6 Configure Timeout) started...
Dec 10 02:36:13 Marcos-Studio-1458 NetworkManager[845]: <info> Activation (eth0) Stage 5 of 5 (IP Configure Commit) started...
Dec 10 02:36:13 Marcos-Studio-1458 NetworkManager[845]: <info> Activation (eth0) Stage 5 of 5 (IP Configure Commit) complete.
Dec 10 02:36:13 Marcos-Studio-1458 NetworkManager[845]: <info> Activation (eth0) Stage 4 of 5 (IP6 Configure Timeout) complete.
Dec 10 02:40:13 Marcos-Studio-1458 NetworkManager[845]: <info> (eth0): carrier now OFF (device state 100, deferring action for 4 seconds)
Dec 10 02:40:17 Marcos-Studio-1458 NetworkManager[845]: <info> (eth0): device state change: activated -> unavailable (reason 'carrier-changed') [100 20 40]
Dec 10 02:40:17 Marcos-Studio-1458 NetworkManager[845]: <info> (eth0): deactivating device (reason 'carrier-changed') [40]
Dec 10 02:40:17 Marcos-Studio-1458 NetworkManager[845]: <info> (eth0): canceled DHCP transaction, DHCP client pid 7914
Dec 10 02:40:17 Marcos-Studio-1458 avahi-daemon[8471]: Network interface enumeration completed.

```

Did it with my wired connection disconnected as you told me.
Hope we can fix it.

---

### Post by wildmanne39 on 2011-12-10
Hi, all right this should get you going.

```
sudo apt-get install --reinstall b43-fwcutter firmware-b43-lpphy-installer
```
watch it and tell me if you get any errors while it is installing.
If not reboot with the wired connection unplugged.
Thank you

---

### Post by tnymch on 2011-12-10
You know... I love you, I just love you. You are amazing! Thank you for your support, patience and quick replies.
Seriously, thank you.
:P

---

### Post by wildmanne39 on 2011-12-10
Hi, your welcome!!! I am glad it is working, would you please go to the top of the page and mark this thread solved by clicking on thread tools. 
Thank you

---

### Post by blitzburgh on 2011-12-17
> **wildmanne39 said:**
> Hi, it looks like you are missing the firmware we can try to get it working with this driver, and if we can not we will have to switch to the wl driver.

Download the b43 zip file to a flash drive then drag and drop the file to your ubuntu desktop. Right-click it and select Extract Here. Open a terminal and do:
```
sudo mkdir /lib/firmware/b43
sudo cp Desktop/b43/*  /lib/firmware/b43
sudo rmmod -f b43
sudo rmmod -f ssb
sudo modprobe b43
```run the commands one line at a time.
Thank you


Wildmanne39 I LOVE YOUUUUUUUUUUUU thanks for the solution.

---

### Post by wildmanne39 on 2011-12-17
Hi blitzburgh, your welcome!!! I am glad it worked.
Enjoy

---

### Post by glennbg343 on 2011-12-30
> **wildmanne39 said:**
> Hi, it looks like you are missing the firmware we can try to get it working with this driver, and if we can not we will have to switch to the wl driver.

Download the b43 zip file to a flash drive then drag and drop the file to your ubuntu desktop. Right-click it and select Extract Here. Open a terminal and do:
```
sudo mkdir /lib/firmware/b43
sudo cp Desktop/b43/*  /lib/firmware/b43
sudo rmmod -f b43
sudo rmmod -f ssb
sudo modprobe b43
```run the commands one line at a time.
Thank you

thanks a ton, worked on the first try!!!

---

### Post by wildmanne39 on 2011-12-30
Hi glennbg343, your welcome!
Enjoy

---

### Post by ceesdam on 2012-01-02
> **wildmanne39 said:**
> Hi, it looks like you are missing the firmware we can try to get it working with this driver, and if we can not we will have to switch to the wl driver.

Download the b43 zip file to a flash drive then drag and drop the file to your ubuntu desktop. Right-click it and select Extract Here. Open a terminal and do:
```
sudo mkdir /lib/firmware/b43
sudo cp Desktop/b43/*  /lib/firmware/b43
sudo rmmod -f b43
sudo rmmod -f ssb
sudo modprobe b43
```run the commands one line at a time.
Thank you

wildmann39 thank you! 
I have been looking for a solution for this problem for a long time and due to your post it is now working. I use Ubuntu 11.10 on a DELL latitude D610 with a BCM4306802 network controller.

After I ran threw the steps you posted the text "firmware missing" was gone. Now it said "wireless is disabled by hardware switch". To solve this I only had to push the button (F2) in the upper left of my keyboard in combination with the Fn button in the lower left corner of the keyboard.

After that it worked. Many thanks again!

---

### Post by wildmanne39 on 2012-01-02
Hi ceesdam, your welcome!
Enjoy

---

### Post by Boukyaku on 2012-01-07
Thanks a lot! This solution worked for me as well as I have Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02). The OS has always installed the firmware and software since Ubuntu 9.10 just fine. I wonder why it won't for Ubuntu 11.10?

---

### Post by wildmanne39 on 2012-01-07
Hi Boukyaku, your welcome!
Enjoy

---

### Post by vati on 2012-01-12
As they say "Forking A"   sorted.  ;-))

---

### Post by wildmanne39 on 2012-01-12
Hi, glad to help.

---

### Post by siva2984 on 2012-01-21
> **wildmanne39 said:**
> Hi, it looks like you are missing the firmware we can try to get it working with this driver, and if we can not we will have to switch to the wl driver.

Download the b43 zip file to a flash drive then drag and drop the file to your ubuntu desktop. Right-click it and select Extract Here. Open a terminal and do:
```
sudo mkdir /lib/firmware/b43
sudo cp Desktop/b43/*  /lib/firmware/b43
sudo rmmod -f b43
sudo rmmod -f ssb
sudo modprobe b43
```run the commands one line at a time.
Thank you
  man really u r genius . i hav a same problem in 11.10. but it is working there also
thanku so  much

---

### Post by wildmanne39 on 2012-01-21
Hi, Thank you and I am glad it worked but I just have a good teacher and actually a lot to learn still.

---

### Post by agopad on 2012-01-25
I had the same problem and applied your suggestion. It worked. Thanks.

I am looking for the actual b43 source code, so I can modify certain things and recompile it. Any one knows where I can find the actual source code for the b43 driver?

---

### Post by brooksfb on 2012-01-29
This method worked for me as well. THANK YOU!

---

### Post by wildmanne39 on 2012-02-03
Hi, your welcome!

---

### Post by alnork on 2012-02-12
Great and simple solution.... Thanks a looooooooooooooot

---

### Post by wildmanne39 on 2012-02-12
Hi, your welcome!

---

### Post by gssheena on 2012-02-16
[B]worked for me as well...thank you!!!...you are a genius

[/B]

---

### Post by wildmanne39 on 2012-02-17
Hi, your welcome!
Enjoy

---

### Post by RedNinja on 2012-02-17
I'm running ubuntu from disk in an attempt to get time files off a dell laptop I'm having issues with. However, when I start up the os all I see is a desktop and clicking, right clicking, or pressing any number of buttons does nothing. After closing the lid and coming back to it later, 4 firmware warn messages come up, and so does "ata1: soft reset failed (device not ready)" I'm hoping this is a symptom of the problem with the computer I've been having all along, and is therefore solvable, but I'm worried that if I can't even get ubuntu to run, I'm basically up a creek and it's over my head with swill. Any help will be met with nauseating amounts of appreciation.

---

### Post by wildmanne39 on 2012-02-18
Hi RedNinja, you should post in absolute beginners section of the forum so you can get help with your problem, this thread is for missing firmware for wireless networking devices only with ubuntu installed, not from a livecd.
Thanks

---

### Post by mvijaykumar456 on 2012-02-23
thank u so much..i have been struglling for past two days with this doing a lot of things... ur solution is very simple....its really amazing....

---

### Post by wildmanne39 on 2012-02-23
Hi, your welcome!
Enjoy

---

### Post by arvindkumar on 2012-03-30
Oh man. Huge thanks to you! you are a live saver!!!

---

### Post by ronkon on 2012-03-31
Worked for me on a Dell 1150 laptop. Thanks.

---

### Post by dell1564 on 2012-03-31
#chris@chris-Inspiron-1564:~$ cat /etc/lsb-release; uname -a
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.10
DISTRIB_CODENAME=oneiric
DISTRIB_DESCRIPTION="Ubuntu 11.10"
Linux chris-Inspiron-1564 3.0.0-17-generic-pae #30-Ubuntu SMP Thu Mar 8 17:53:35 UTC 2012 i686 i686 i386 GNU/Linux
-----------------------------------------------------------
chris@chris-Inspiron-1564:~$ lspci -nnk | grep -iA2 net
03:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01)
    Subsystem: Dell Wireless 1397 WLAN Mini-Card [1028:000c]
    Kernel driver in use: wl
--
04:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 02)
    Subsystem: Dell Device [1028:0434]
    Kernel driver in use: r8169
--------------------------------------------------------------------
chris@chris-Inspiron-1564:~$ lspci -nnk | grep -iA2 net
03:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01)
    Subsystem: Dell Wireless 1397 WLAN Mini-Card [1028:000c]
    Kernel driver in use: wl
--
04:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 02)
    Subsystem: Dell Device [1028:0434]
    Kernel driver in use: r8169
chris@chris-Inspiron-1564:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11  Access Point: Not-Associated   
          Link Quality:5  Signal level:0  Noise level:0
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0
-----------------------------------------------------------------------------
chris@chris-Inspiron-1564:~$ rfkill list all
0: dell-wifi: Wireless LAN
    Soft blocked: yes
    Hard blocked: yes
2: brcmwl-0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
chris@chris-Inspiron-1564:~$ 
--------------------------------------------------------------------------
chris@chris-Inspiron-1564:~$ lsmod
Module                  Size  Used by
lib80211_crypt_tkip    17275  0 
wl                   2646601  0 
lib80211               14570  2 lib80211_crypt_tkip,wl
bnep                   17923  2 
rfcomm                 38408  0 
bluetooth             148839  10 bnep,rfcomm
parport_pc             32114  0 
ppdev                  12849  0 
binfmt_misc            17292  1 
arc4                   12473  0 
snd_hda_codec_hdmi     31426  1 
snd_hda_codec_realtek   254163  1 
joydev                 17393  0 
uvcvideo               67271  0 
videodev               85626  1 uvcvideo
dell_wmi               12601  0 
sparse_keymap          13658  1 dell_wmi
snd_hda_intel          28358  2 
snd_hda_codec          91859  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80435  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
dell_laptop            13519  0 
dcdbas                 14098  1 dell_laptop
snd_rawmidi            25241  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
psmouse                63474  0 
serio_raw              12990  0 
i915                  509554  8 
snd                    55902  14 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
drm_kms_helper         32889  1 i915
drm                   196290  4 i915,drm_kms_helper
i2c_algo_bit           13199  1 i915
mei                    36466  0 
soundcore              12600  1 snd
snd_page_alloc         14108  2 snd_hda_intel,snd_pcm
wmi                    18744  1 dell_wmi
intel_ips              17753  0 
video                  18908  1 i915
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
ahci                   21634  2 
libahci                25761  1 ahci
r8169                  47200  0 
------------------------------------------------------------------------

Hello Wildman! I have been reading all of your post about broadcom drivers on 11.10 and i am still unable to get mine to work.. I can all of the first commands you asked at the beginning of this thread and here are the results! Thanks for the help!

---

### Post by wildmanne39 on 2012-03-31
Hi, please do:
```
sudo apt-get purge bcmwl-kernel-source broadcom-sta-common broadcom-sta-source
```
Then:
```
sudo apt-get install b43-fwcutter firmware-b43-lpphy-installer
```
Watch for errors, when it is done unplug wired connection and reboot.
Thanks

---

### Post by dell1564 on 2012-03-31
chris@chris-Inspiron-1564:~$ cat /etc/lsb-release; uname -a
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.10
DISTRIB_CODENAME=oneiric
DISTRIB_DESCRIPTION="Ubuntu 11.10"
Linux chris-Inspiron-1564 3.0.0-17-generic-pae #30-Ubuntu SMP Thu Mar 8 17:53:35 UTC 2012 i686 i686 i386 GNU/Linux
chris@chris-Inspiron-1564:~$ lspci -nnk | grep -iA2 net
03:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01)
    Subsystem: Dell Wireless 1397 WLAN Mini-Card [1028:000c]
    Kernel driver in use: b43-pci-bridge
--
04:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 02)
    Subsystem: Dell Device [1028:0434]
    Kernel driver in use: r8169
chris@chris-Inspiron-1564:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          
chris@chris-Inspiron-1564:~$ rfkill list all
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: dell-wifi: Wireless LAN
    Soft blocked: yes
    Hard blocked: yes
chris@chris-Inspiron-1564:~$ lsmod
Module                  Size  Used by
rfcomm                 38408  0 
bnep                   17923  2 
bluetooth             148839  10 bnep,rfcomm
parport_pc             32114  0 
ppdev                  12849  0 
joydev                 17393  0 
snd_hda_codec_hdmi     31426  1 
binfmt_misc            17292  1 
snd_hda_codec_realtek   254163  1 
dell_wmi               12601  0 
sparse_keymap          13658  1 dell_wmi
uvcvideo               67271  0 
videodev               85626  1 uvcvideo
arc4                   12473  2 
dell_laptop            13519  0 
dcdbas                 14098  1 dell_laptop
snd_hda_intel          28358  2 
snd_hda_codec          91859  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80435  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25241  1 snd_seq_midi
psmouse                63474  0 
b43                   318816  0 
serio_raw              12990  0 
mac80211              393421  1 b43
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
intel_ips              17753  0 
snd                    55902  14 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
i915                  509554  8 
cfg80211              172427  2 b43,mac80211
soundcore              12600  1 snd
snd_page_alloc         14108  2 snd_hda_intel,snd_pcm
mei                    36466  0 
drm_kms_helper         32889  1 i915
drm                   196290  4 i915,drm_kms_helper
i2c_algo_bit           13199  1 i915
wmi                    18744  1 dell_wmi
video                  18908  1 i915
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
ahci                   21634  2 
libahci                25761  1 ahci
ssb                    50682  1 b43
r8169                  47200  0 


Here are my replies for the second set of commands... I really need some help here =(

---

### Post by dell1564 on 2012-03-31
chris@chris-Inspiron-1564:~$ sudo apt-get purge bcmwl-kernel-source broadcom-sta-common broadcom-sta-source
[sudo] password for chris: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package bcmwl-kernel-source is not installed, so not removed
Package broadcom-sta-common is not installed, so not removed
Package broadcom-sta-source is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 361 not upgraded.
chris@chris-Inspiron-1564:~$ sudo apt-get install b43-fwcutter firmware-b43-lpphy-installer
Reading package lists... Done
Building dependency tree       
Reading state information... Done
b43-fwcutter is already the newest version.
firmware-b43-lpphy-installer is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 361 not upgraded.

Here are the other ones.. Wireless is still not working.

---

### Post by wildmanne39 on 2012-03-31
Hi, please post the output of:
```
lsmod
```
by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

### Post by dell1564 on 2012-03-31
chris@chris-Inspiron-1564:~$ lsmod
Module                  Size  Used by
rfcomm                 38408  0 
bnep                   17923  2 
bluetooth             148839  10 rfcomm,bnep
parport_pc             32114  0 
ppdev                  12849  0 
binfmt_misc            17292  1 
snd_hda_codec_hdmi     31426  1 
snd_hda_codec_realtek   254163  1 
joydev                 17393  0 
dell_wmi               12601  0 
sparse_keymap          13658  1 dell_wmi
snd_hda_intel          28358  2 
snd_hda_codec          91859  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
uvcvideo               67271  0 
snd_pcm                80435  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
videodev               85626  1 uvcvideo
dell_laptop            13519  0 
dcdbas                 14098  1 dell_laptop
arc4                   12473  2 
snd_seq_midi           13132  0 
snd_rawmidi            25241  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
psmouse                63474  0 
serio_raw              12990  0 
b43                   318816  0 
intel_ips              17753  0 
snd                    55902  14 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
mac80211              393421  1 b43
cfg80211              172427  2 b43,mac80211
i915                  509554  8 
mei                    36466  0 
drm_kms_helper         32889  1 i915
drm                   196290  4 i915,drm_kms_helper
soundcore              12600  1 snd
snd_page_alloc         14108  2 snd_hda_intel,snd_pcm
wmi                    18744  1 dell_wmi
i2c_algo_bit           13199  1 i915
video                  18908  1 i915
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
r8169                  47200  0 
ssb                    50682  1 b43
ahci                   21634  2 
libahci                25761  1 ahci

---

### Post by wildmanne39 on 2012-03-31
Hi, try this please if it works we will need to make it permanent.
```
sudo rmmod -f dell-laptop
```
also make sure the switch is on to your wireless it is showing it is off.

Do not reboot, if it does not come on then post the output of:
```
rfkill list all
```again
Thanks

---

### Post by dell1564 on 2012-04-01
0: phy0: Wireless LAN
    Soft blocked: yes
    Hard blocked: no


I am unsure of how to turn it on.. I have pressed FN-F2 but it does not seem like its doing any good

And no...  thank you!

---

### Post by dell1564 on 2012-04-01
OK i figured it out i need to press alt-f2 key to enable wireless. I am able to connect to the router but the connection only last for a few seconds and it disconnects. And starts searching again.




EDIT:FIXED--Did system update and restarted.. Went to system setting>additional drivers)installed STA Broadcom driver and that fixed my problem.. I have restarted a few time and its working great im typing on it right now!! Thanks to Wildman!! You are awesome!

---

### Post by wildmanne39 on 2012-04-01
Hi, your welcome!

---

### Post by pash12 on 2012-04-02
thnks a lot wildmanne39. i also got the same issue. but it got solved.. all credits to u nly

---

### Post by felinvrr on 2012-04-02
thanks! worked perfectly!!

---

### Post by curtis2012 on 2012-04-04
I followed all the steps and still having this problem I have a lenovo c300 series all in one desktop. The system was working great till the update any help would be nice. I tried re-install and no luck broadcom card 4312

---

### Post by wildmanne39 on 2012-04-04
Hi, welcome to the forum! Please open a terminal ctrl+alt+t copy and paste the following commands into it one line at a time, then paste the results here:

```
cat /etc/lsb-release; uname -a
lspci -nnk | grep -iA2 net
lsusb
iwconfig
rfkill list all
lsmod
```
by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

### Post by curtis2012 on 2012-04-05
> **wildmanne39 said:**
> Hi, welcome to the forum! Please open a terminal ctrl+alt+t copy and paste the following commands into it one line at a time, then paste the results here:

```
cat /etc/lsb-release; uname -a
lspci -nnk | grep -iA2 net
lsusb
iwconfig
rfkill list all
lsmod
```by clicking on new reply and click # and paste the information between the brackets.
Thank you

**intel-atom@intelatom-Lenovo-Product:~$ cat /etc/lsb-release; uname -a**
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.10
DISTRIB_CODENAME=oneiric
DISTRIB_DESCRIPTION="Ubuntu 11.10"
Linux intelatom-Lenovo-Product 3.0.0-18-generic #31-Ubuntu SMP Tue Mar 27 16:53:46 UTC 2012 i686 i686 i386 GNU/Linux
intel-atom@intelatom-Lenovo-Product:~$ lspci -nnk | grep -iA2 net
01:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01)
    Subsystem: Broadcom Corporation Device [14e4:04b5]
    Kernel driver in use: wl
--
03:08.0 Ethernet controller [0200]: Intel Corporation PRO/100 VE Network Connection [8086:1094] (rev 01)
    Subsystem: Lenovo Device [17aa:3061]
    Kernel driver in use: e100

**intel-atom@intelatom-Lenovo-Product:~$ lsusb**
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 0ac8:c41d Z-Star Microelectronics Corp. 
Bus 002 Device 003: ID 04b3:310c IBM Corp. Wheel Mouse

**intel-atom@intelatom-Lenovo-Product:~$ iwconfig**
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11  Access Point: Not-Associated   
          Link Quality:5  Signal level:0  Noise level:0
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0

**intel-atom@intelatom-Lenovo-Product:~$ rfkill list all**
0: brcmwl-0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

**intel-atom@intelatom-Lenovo-Product:~$ lsmod**
Module                  Size  Used by
snd_usb_audio         100930  1 
snd_usbmidi_lib        24558  1 snd_usb_audio
usbhid                 41905  0 
hid                    77367  1 usbhid
uvcvideo               67271  0 
videodev               85626  1 uvcvideo
bnep                   17923  2 
rfcomm                 38408  0 
bluetooth             148869  10 bnep,rfcomm
parport_pc             32114  0 
ppdev                  12849  0 
snd_hda_codec_realtek   254163  1 
snd_hda_intel          24262  2 
snd_hda_codec          91888  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13276  2 snd_usb_audio,snd_hda_codec
snd_pcm                80435  3 snd_usb_audio,snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25241  2 snd_usbmidi_lib,snd_seq_midi
r852                   17901  0 
sm_common              16737  1 r852
nand                   49706  2 r852,sm_common
nand_ids                8547  1 nand
nand_bch               13003  1 nand
bch                    21757  1 nand_bch
nand_ecc               13070  1 nand
binfmt_misc            17292  1 
r592                   17808  0 
mtd                    35852  2 sm_common,nand
snd_seq_midi_event     14475  1 snd_seq_midi
memstick               15857  1 r592
lib80211_crypt_tkip    17240  0 
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
wl                   2646601  0 
snd                    55902  17 snd_usb_audio,snd_usbmidi_lib,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
lib80211               14570  2 lib80211_crypt_tkip,wl
i915                  509519  3 
soundcore              12600  1 snd
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
drm_kms_helper         32889  1 i915
drm                   192194  4 i915,drm_kms_helper
i2c_algo_bit           13199  1 i915
video                  18908  1 i915
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
firewire_ohci          35854  0 
firewire_core          56937  1 firewire_ohci
crc_itu_t              12627  1 firewire_core
sdhci_pci              13658  0 
e100                   36289  0 
sdhci                  27360  1 sdhci_pci

intel-atom@intelatom-Lenovo-Product:~$

---

### Post by wildmanne39 on 2012-04-05
Hi, it is possible that the kernel upgrade is what broke the wireless.

Please post the output of:
```
nm-tool
sudo iwlist scan
cat /var/lib/NetworkManager/NetworkManager.state
```
```
sudo cat /var/log/syslog | grep -e wl -e firmware -e wpa -e eth1 -e etork | tail -n55
```
Thanks

---

### Post by curtis2012 on 2012-04-05
> **wildmanne39 said:**
> Hi, it is possible that the kernel upgrade is what broke the wireless. I do not know? I am new to ubuntu I hate windows, I only have one system installed on the HD

Please post the output of:
```
nm-tool
sudo iwlist scan
cat /var/lib/NetworkManager/NetworkManager.state
``````
sudo cat /var/log/syslog | grep -e wl -e firmware -e wpa -e eth1 -e etork | tail -n55
```Thanks
[B]
intel-atom@intelatom-Lenovo-Product:~$ nm-tool[/B]

NetworkManager Tool

State: connected (global)

- Device: eth1  [belkin.fbc] ---------------------------------------------------
  Type:              802.11 WiFi
  Driver:            wl
  State:             connecting (configuring)
  Default:           no
  HW Address:        00:21:00:FB:5E:4B

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 
    belkin.fbc:      Infra, 08:86:3B:5E:3F:BC, Freq 2412 MHz, Rate 0 Mb/s, Strength 100 WPA WPA2
    essence:         Infra, 00:1B:11:54:D9:BD, Freq 2412 MHz, Rate 54 Mb/s, Strength 35 WEP
    your-b27fb1c401-Wireless: Infra, 00:26:F2:7F:5C:64, Freq 2462 MHz, Rate 0 Mb/s, Strength 49 WPA WPA2
    Deathnote100:    Infra, C0:C1:C0:67:24:1A, Freq 2427 MHz, Rate 54 Mb/s, Strength 42 WPA WPA2


- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            e100
  State:             connected
  Default:           yes
  HW Address:        00:23:8B:A6:D6:2B

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.2.3
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.2.1

    DNS:             192.168.2.1


**intel-atom@intelatom-Lenovo-Product:~$ sudo iwlist scan**
[sudo] password for intel-atom: 
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Scan completed :
          Cell 01 - Address: 08:86:3B:5E:3F:BC
                    ESSID:"belkin.fbc"
                    Mode:Managed
                    Frequency:2.412 GHz (Channel 1)
                    Quality:5/5  Signal level:-26 dBm  Noise level:-92 dBm
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DDB50050F204104A0001101044000102103B00010310470010BC329E001DD811B2860108863B5E3FBC1021001442656C6B696E20496E7465726E6174696F6E616C1023001D42656C6B696E204E373530444220576972656C65737320526F757465721024000746394B313130331042000E31323334353647383930313233341054000800060050F20400011011001D42656C6B696E204E373530444220576972656C65737320526F75746572100800020084103C000101
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 12 Mb/s
                              24 Mb/s; 48 Mb/s

**intel-atom@intelatom-Lenovo-Product:~$ cat /var/lib/NetworkManager/NetworkManager.state**

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
**intel-atom@intelatom-Lenovo-Product:~$ sudo cat /var/log/syslog | grep -e wl -e firmware -e wpa -e eth1 -e etork | tail -n55**
Apr  5 17:10:50 intelatom-Lenovo-Product NetworkManager[481]: <info> (eth1): supplicant interface state: scanning -> associating
Apr  5 17:10:55 intelatom-Lenovo-Product wpa_supplicant[579]: Authentication with 08:86:3b:5e:3f:bc timed out.
Apr  5 17:10:55 intelatom-Lenovo-Product NetworkManager[481]: <info> (eth1): supplicant interface state: associating -> scanning
Apr  5 17:10:55 intelatom-Lenovo-Product wpa_supplicant[579]: Trying to associate with 08:86:3b:5e:3f:bc (SSID='belkin.fbc' freq=2412 MHz)
Apr  5 17:10:55 intelatom-Lenovo-Product wpa_supplicant[579]: Association request to the driver failed
Apr  5 17:10:55 intelatom-Lenovo-Product NetworkManager[481]: <info> (eth1): supplicant interface state: scanning -> associating
Apr  5 17:11:00 intelatom-Lenovo-Product wpa_supplicant[579]: Authentication with 08:86:3b:5e:3f:bc timed out.
Apr  5 17:11:00 intelatom-Lenovo-Product NetworkManager[481]: <info> (eth1): supplicant interface state: associating -> scanning
Apr  5 17:11:01 intelatom-Lenovo-Product wpa_supplicant[579]: Trying to associate with 08:86:3b:5e:3f:bc (SSID='belkin.fbc' freq=2412 MHz)
Apr  5 17:11:01 intelatom-Lenovo-Product wpa_supplicant[579]: Association request to the driver failed
Apr  5 17:11:01 intelatom-Lenovo-Product NetworkManager[481]: <info> (eth1): supplicant interface state: scanning -> associating
Apr  5 17:11:06 intelatom-Lenovo-Product wpa_supplicant[579]: Authentication with 08:86:3b:5e:3f:bc timed out.
Apr  5 17:11:06 intelatom-Lenovo-Product NetworkManager[481]: <info> (eth1): supplicant interface state: associating -> scanning
Apr  5 17:11:06 intelatom-Lenovo-Product wpa_supplicant[579]: Trying to associate with 08:86:3b:5e:3f:bc (SSID='belkin.fbc' freq=2412 MHz)
Apr  5 17:11:06 intelatom-Lenovo-Product wpa_supplicant[579]: Association request to the driver failed
Apr  5 17:11:06 intelatom-Lenovo-Product NetworkManager[481]: <info> (eth1): supplicant interface state: scanning -> associating
Apr  5 17:11:11 intelatom-Lenovo-Product wpa_supplicant[579]: Authentication with 08:86:3b:5e:3f:bc timed out.
Apr  5 17:11:11 intelatom-Lenovo-Product NetworkManager[481]: <info> (eth1): supplicant interface state: associating -> scanning
Apr  5 17:11:11 intelatom-Lenovo-Product wpa_supplicant[579]: Trying to associate with 08:86:3b:5e:3f:bc (SSID='belkin.fbc' freq=2412 MHz)
Apr  5 17:11:11 intelatom-Lenovo-Product wpa_supplicant[579]: Association request to the driver failed
Apr  5 17:11:11 intelatom-Lenovo-Product NetworkManager[481]: <info> (eth1): supplicant interface state: scanning -> associating
Apr  5 17:11:16 intelatom-Lenovo-Product wpa_supplicant[579]: Authentication with 08:86:3b:5e:3f:bc timed out.
Apr  5 17:11:16 intelatom-Lenovo-Product NetworkManager[481]: <info> (eth1): supplicant interface state: associating -> scanning
Apr  5 17:11:17 intelatom-Lenovo-Product wpa_supplicant[579]: Trying to associate with 08:86:3b:5e:3f:bc (SSID='belkin.fbc' freq=2412 MHz)
Apr  5 17:11:17 intelatom-Lenovo-Product wpa_supplicant[579]: Association request to the driver failed
Apr  5 17:11:17 intelatom-Lenovo-Product NetworkManager[481]: <info> (eth1): supplicant interface state: scanning -> associating
Apr  5 17:11:17 intelatom-Lenovo-Product NetworkManager[481]: <warn> Activation (eth1/wireless): association took too long.
Apr  5 17:11:17 intelatom-Lenovo-Product NetworkManager[481]: <info> (eth1): device state change: config -> need-auth (reason 'none') [50 60 0]
Apr  5 17:11:17 intelatom-Lenovo-Product NetworkManager[481]: <warn> Activation (eth1/wireless): asking for new secrets
Apr  5 17:11:17 intelatom-Lenovo-Product NetworkManager[481]: <info> (eth1): supplicant interface state: associating -> disconnected
Apr  5 17:11:23 intelatom-Lenovo-Product NetworkManager[481]: <info> Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled...
Apr  5 17:11:23 intelatom-Lenovo-Product NetworkManager[481]: <info> Activation (eth1) Stage 1 of 5 (Device Prepare) started...
Apr  5 17:11:23 intelatom-Lenovo-Product NetworkManager[481]: <info> (eth1): device state change: need-auth -> prepare (reason 'none') [60 40 0]
Apr  5 17:11:23 intelatom-Lenovo-Product NetworkManager[481]: <info> Activation (eth1) Stage 2 of 5 (Device Configure) scheduled...
Apr  5 17:11:23 intelatom-Lenovo-Product NetworkManager[481]: <info> Activation (eth1) Stage 1 of 5 (Device Prepare) complete.
Apr  5 17:11:23 intelatom-Lenovo-Product NetworkManager[481]: <info> Activation (eth1) Stage 2 of 5 (Device Configure) starting...
Apr  5 17:11:23 intelatom-Lenovo-Product NetworkManager[481]: <info> (eth1): device state change: prepare -> config (reason 'none') [40 50 0]
Apr  5 17:11:23 intelatom-Lenovo-Product NetworkManager[481]: <info> Activation (eth1/wireless): connection 'belkin.fbc' has security, and secrets exist.  No new secrets needed.
Apr  5 17:11:23 intelatom-Lenovo-Product NetworkManager[481]: <info> Activation (eth1) Stage 2 of 5 (Device Configure) complete.
Apr  5 17:11:23 intelatom-Lenovo-Product NetworkManager[481]: <info> (eth1): supplicant interface state: disconnected -> scanning
Apr  5 17:11:24 intelatom-Lenovo-Product wpa_supplicant[579]: Trying to associate with 08:86:3b:5e:3f:bc (SSID='belkin.fbc' freq=2412 MHz)
Apr  5 17:11:24 intelatom-Lenovo-Product wpa_supplicant[579]: Association request to the driver failed
Apr  5 17:11:24 intelatom-Lenovo-Product NetworkManager[481]: <info> (eth1): supplicant interface state: scanning -> associating
Apr  5 17:11:29 intelatom-Lenovo-Product wpa_supplicant[579]: Authentication with 08:86:3b:5e:3f:bc timed out.
Apr  5 17:11:29 intelatom-Lenovo-Product NetworkManager[481]: <info> (eth1): supplicant interface state: associating -> scanning
Apr  5 17:11:29 intelatom-Lenovo-Product wpa_supplicant[579]: Trying to associate with 08:86:3b:5e:3f:bc (SSID='belkin.fbc' freq=2412 MHz)
Apr  5 17:11:29 intelatom-Lenovo-Product wpa_supplicant[579]: Association request to the driver failed
Apr  5 17:11:29 intelatom-Lenovo-Product NetworkManager[481]: <info> (eth1): supplicant interface state: scanning -> associating
Apr  5 17:11:34 intelatom-Lenovo-Product wpa_supplicant[579]: Authentication with 08:86:3b:5e:3f:bc timed out.
Apr  5 17:11:34 intelatom-Lenovo-Product NetworkManager[481]: <info> (eth1): supplicant interface state: associating -> scanning
Apr  5 17:11:35 intelatom-Lenovo-Product wpa_supplicant[579]: Trying to associate with 08:86:3b:5e:3f:bc (SSID='belkin.fbc' freq=2412 MHz)
Apr  5 17:11:35 intelatom-Lenovo-Product wpa_supplicant[579]: Association request to the driver failed
Apr  5 17:11:35 intelatom-Lenovo-Product NetworkManager[481]: <info> (eth1): supplicant interface state: scanning -> associating
Apr  5 17:11:40 intelatom-Lenovo-Product wpa_supplicant[579]: Authentication with 08:86:3b:5e:3f:bc timed out.
Apr  5 17:11:40 intelatom-Lenovo-Product NetworkManager[481]: <info> (eth1): supplicant interface state: associating -> scanning
**intel-atom@intelatom-Lenovo-Product:~$ **

---

### Post by wildmanne39 on 2012-04-05
Hi, it is having trouble with encryption it looks like, let's try the other driver please:
```
sudo apt-get purge bcmwl-kernel-source broadcom-sta-common broadcom-sta-source
```
```
sudo apt-get install b43-fwcutter firmware-b43-lpphy-installer
```
```
sudp rmmod -f wl
sudo modprobe b43
```
Thanks

---

### Post by mhguda on 2012-04-07
> **wildmanne39 said:**
> Hi, it looks like you are missing the firmware we can try to get it working with this driver, and if we can not we will have to switch to the wl driver.

Download the b43 zip file to a flash drive then drag and drop the file to your ubuntu desktop. Right-click it and select Extract Here. Open a terminal and do:
```
sudo mkdir /lib/firmware/b43
sudo cp Desktop/b43/*  /lib/firmware/b43
sudo rmmod -f b43
sudo rmmod -f ssb
sudo modprobe b43
```run the commands one line at a time.
Thank you

wildmanne39, this worked for me too, and I want to thank you for it. I followed the instructions to the letter and could see my network connection come back. Very happy I found this thread.

---

### Post by wildmanne39 on 2012-04-07
Hi, your welcome! you can think chili555 for teaching me this one.

---

### Post by cssutto on 2012-04-07
I have followed this thread and am impressed, but I am running 104  64 bit and don't kow enough to adapt your instructions to my system.

Apparentyl I have no wireless driver but don't know which driver I need.

Could you please help?

My output is:

claude@claude-laptop:~$ cat /etc/lsb-release; uname -a
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.04
DISTRIB_CODENAME=lucid
DISTRIB_DESCRIPTION="Ubuntu 10.04.4 LTS"
Linux claude-laptop 2.6.32-40-generic #87-Ubuntu SMP Tue Mar 6 00:56:56 UTC 2012 x86_64 GNU/Linux
claude@claude-laptop:~$ lspci -nnk | grep -iA2 net
07:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 06)
	Kernel driver in use: r8169
	Kernel modules: r8169
0d:00.0 Network controller [0280]: Intel Corporation Device [8086:008b] (rev 34)
13:00.0 Class [ff00]: Realtek Semiconductor Co., Ltd. Device [10ec:5209] (rev 01)
13:00.1 SD Host controller [0805]: Realtek Semiconductor Co., Ltd. Device [10ec:5209] (rev 01)
claude@claude-laptop:~$ lsusb
Bus 003 Device 008: ID 046d:c52b Logitech, Inc. 
Bus 003 Device 006: ID 1163:0100 DeLorme Publishing, Inc. Earthmate GPS (orig)
Bus 003 Device 005: ID 051d:0002 American Power Conversion Uninterruptible Power Supply
Bus 003 Device 004: ID 03f0:7311 Hewlett-Packard 
Bus 003 Device 003: ID 050d:0416 Belkin Components 
Bus 003 Device 002: ID 046d:c52b Logitech, Inc. 
Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 003: ID 8086:0189 Intel Corp. 
Bus 002 Device 002: ID 8087:0024  
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 064e:d281 Suyin Corp. 
Bus 001 Device 003: ID 138a:0018 DigitalPersona, Inc 
Bus 001 Device 002: ID 8087:0024  
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
claude@claude-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

claude@claude-laptop:~$ rfkill list all
0: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
claude@claude-laptop:~$ lsmod
Module                  Size  Used by
nls_iso8859_1           4633  0 
nls_cp437               6351  0 
vfat                   10866  0 
fat                    55350  1 vfat
cypress_m8             20185  0 
usbserial              39973  1 cypress_m8
rfcomm                 40425  4 
binfmt_misc             7960  1 
ppdev                   6375  0 
sco                     9649  2 
bridge                 53248  0 
stp                     2171  1 bridge
bnep                   11916  2 
l2cap                  34839  16 rfcomm,bnep
usblp                  12407  0 
usb_storage            50633  0 
snd_hda_codec_idt      61546  1 
joydev                 11104  0 
usbhid                 41116  2 
hid                    83888  1 usbhid
snd_hda_intel          25805  2 
snd_hda_codec          85791  2 snd_hda_codec_idt,snd_hda_intel
snd_hwdep               6924  1 snd_hda_codec
snd_pcm_oss            41394  0 
snd_mixer_oss          16299  1 snd_pcm_oss
snd_pcm                87946  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1782  0 
snd_seq_oss            31191  0 
snd_seq_midi            5829  0 
snd_rawmidi            23420  1 snd_seq_midi
snd_seq_midi_event      7267  2 snd_seq_oss,snd_seq_midi
snd_seq                57481  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
uvcvideo               62915  0 
fbcon                  39270  71 
videodev               40614  1 uvcvideo
tileblit                2487  1 fbcon
font                    8053  1 fbcon
v4l1_compat            15495  2 uvcvideo,videodev
snd_timer              23681  2 snd_pcm,snd_seq
btusb                  13097  2 
snd_seq_device          6888  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
bluetooth              58717  9 rfcomm,sco,bnep,l2cap,btusb
v4l2_compat_ioctl32    11892  1 videodev
bitblit                 5811  1 fbcon
softcursor              1565  1 bitblit
sdhci_pci               6700  0 
sdhci                  17960  1 sdhci_pci
snd                    71283  16 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
vga16fb                12757  1 
vgastate                9857  1 vga16fb
psmouse                65040  0 
serio_raw               4918  0 
soundcore               8052  1 snd
snd_page_alloc          8500  2 snd_hda_intel,snd_pcm
xhci                   42775  0 
video                  20623  0 
output                  2503  1 video
hp_accel               12168  0 
lis3lv02d               7648  1 hp_accel
input_polldev           3106  1 lis3lv02d
led_class               3764  2 sdhci,hp_accel
lp                      9336  0 
parport                37160  2 ppdev,lp
ahci                   38350  2 
r8169                  39714  0 
mii                     5237  1 r8169
claude@claude-laptop:~$

---

### Post by wildmanne39 on 2012-04-07
Hi, I will try to help you but I want you to know that you already have the best with chili555 in your other thread.

Please do:
```
sudo modprobe iwlagn
```
```
nm-tool
rfkill list all
cat /var/lib/NetworkManager/NetworkManager.state
lsmod | grep iwl
```
```
sudo cat /var/log/syslog | grep -e iwl -e firmware -e wpa -e wlan -e etork | tail -n55
```
Thanks

---

### Post by cssutto on 2012-04-07
chilli555 did help me a lot, but the way I got off that thread and on this is that after I got, I thought, the wireless working I thought I had a problem communicating with my wirless routher.

In searching for an answer as to why my router was ignoring me, I found this thread.

That came about because I tried to boot up windows and extablish a wireless connection to the router and windows told me that I had no wireless even though my wireless light is illuminated on the keyboard.

A long explanation, but I want to make the point that chilli555 was very kind and helpful to me and I am not here because I am dissatisfied with his help.

I am here because I am a blind man stumbling looking for a light.

the results:

[sudo] password for claude: 
claude@claude-laptop:~$ sudo modprobe iwlagn
claude@claude-laptop:~$ 







[sudo] password for claude: 
claude@claude-laptop:~$ sudo modprobe iwlagn
claude@claude-laptop:~$ 

nm-tool

NetworkManager Tool

State: connected

- Device: eth0  [Auto eth0] ----------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             connected
  Default:           yes
  HW Address:        08:2E:5F:8A:54:BA

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.0.199
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.1

    DNS:             192.168.0.1


claude@claude-laptop:~$ rfkill list all
0: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
claude@claude-laptop:~$ cat /var/lib/NetworkManager/NetworkManager.state

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
claude@claude-laptop:~$ lsmod | grep iwl
iwlagn                123060  0 
iwlcore               125250  1 iwlagn
mac80211              238928  2 iwlagn,iwlcore
cfg80211              148725  3 iwlagn,iwlcore,mac80211
led_class               3764  3 iwlcore,sdhci,hp_accel
claude@claude-laptop:~$ 
claude@claude-laptop:~$ 
claude@claude-laptop:~$ sudo cat /var/log/syslog | grep -e iwl -e firmware -e wpa -e wlan -e etork | tail -n55
Apr  7 14:50:31 claude-laptop kernel: [48902.225020] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, 1.3.27k
Apr  7 14:50:31 claude-laptop kernel: [48902.225022] iwlagn: Copyright(c) 2003-2009 Intel Corporation
claude@claude-laptop:~$

---

### Post by wildmanne39 on 2012-04-07
Hi, did you have a kernel upgrade since chili555 helped you fix your wireless? did you boot from it instead of the one you added the boot parameters too?

It is not connecting in ubuntu or windows is that correct?

Please do not reboot your until we are done.

Post the output of:
```
lsmod
```
Thanks

---

### Post by cssutto on 2012-04-07
He did fix it in that the light on the panel said that it was fixed.

I did not succeed in connecting with the router but mure important at the time was the fact that the windoze disk that came with the computer could not bring back Windows 7, which ubuntu had broken.

I worried with that for a long time and then decided the only fix would be to do a complete new install of windoze and then install ubuntu.

During my attempt to repair windows, I downloaded ubuntu LIVE and liked it better than the 10.4 for downloading only so I used it to reinstall ubuntu.

I used Gparted to create a new partition table, which created one in MS-DOS that replaced all previous partitions.

When I started up Ubuntu after the reinstall, the blue light on the keyboard came on and from that I assumed that ubuntu had installed all of the drivers I need to talk to the router.

AAs for windoze, I don't worry too much that I could not commect with it because O have done very little with windoze since 2000 professional.

7 is so different that I am lost init.

I realize each has its own driver.

I will use windoze very little for connecting with the outside due to the windoze security problems.




> **wildmanne39 said:**
> Hi, did you have a kernel upgrade since chili555 helped you fix your wireless? did you boot from it instead of the one you added the boot parameters too?

It is not connecting in ubuntu or windows is that correct?

Please do not reboot your until we are done.

Post the output of:
```
lsmod
```
Thanks


claude@claude-laptop:~$ lsmod
Module                  Size  Used by
iwlagn                123060  0 
iwlcore               125250  1 iwlagn
mac80211              238928  2 iwlagn,iwlcore
cfg80211              148725  3 iwlagn,iwlcore,mac80211
nls_iso8859_1           4633  0 
nls_cp437               6351  0 
vfat                   10866  0 
fat                    55350  1 vfat
cypress_m8             20185  0 
usbserial              39973  1 cypress_m8
rfcomm                 40425  4 
binfmt_misc             7960  1 
ppdev                   6375  0 
sco                     9649  2 
bridge                 53248  0 
stp                     2171  1 bridge
bnep                   11916  2 
l2cap                  34839  16 rfcomm,bnep
usblp                  12407  0 
usb_storage            50633  0 
snd_hda_codec_idt      61546  1 
joydev                 11104  0 
usbhid                 41116  2 
hid                    83888  1 usbhid
snd_hda_intel          25805  2 
snd_hda_codec          85791  2 snd_hda_codec_idt,snd_hda_intel
snd_hwdep               6924  1 snd_hda_codec
snd_pcm_oss            41394  0 
snd_mixer_oss          16299  1 snd_pcm_oss
snd_pcm                87946  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1782  0 
snd_seq_oss            31191  0 
snd_seq_midi            5829  0 
snd_rawmidi            23420  1 snd_seq_midi
snd_seq_midi_event      7267  2 snd_seq_oss,snd_seq_midi
snd_seq                57481  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
uvcvideo               62915  0 
fbcon                  39270  71 
videodev               40614  1 uvcvideo
tileblit                2487  1 fbcon
font                    8053  1 fbcon
v4l1_compat            15495  2 uvcvideo,videodev
snd_timer              23681  2 snd_pcm,snd_seq
btusb                  13097  2 
snd_seq_device          6888  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
bluetooth              58717  9 rfcomm,sco,bnep,l2cap,btusb
v4l2_compat_ioctl32    11892  1 videodev
bitblit                 5811  1 fbcon
softcursor              1565  1 bitblit
sdhci_pci               6700  0 
sdhci                  17960  1 sdhci_pci
snd                    71283  16 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
vga16fb                12757  1 
vgastate                9857  1 vga16fb
psmouse                65040  0 
serio_raw               4918  0 
soundcore               8052  1 snd
snd_page_alloc          8500  2 snd_hda_intel,snd_pcm
xhci                   42775  0 
video                  20623  0 
output                  2503  1 video
hp_accel               12168  0 
lis3lv02d               7648  1 hp_accel
input_polldev           3106  1 lis3lv02d
led_class               3764  3 iwlcore,sdhci,hp_accel
lp                      9336  0 
parport                37160  2 ppdev,lp
ahci                   38350  3 
r8169                  39714  0 
mii                     5237  1 r8169
claude@claude-laptop:~$

---

### Post by wildmanne39 on 2012-04-07
Hi, it looks like you reinstalled 10.04 is that not the same version of ubuntu that you had installed before when chili555 helped you if it is then you need to add the boot options to the kernel like you did before.
Thanks

---

### Post by cssutto on 2012-04-07
I did.

ifconfig still shows no wlan0.

---

### Post by cssutto on 2012-04-07
The results this far:

---

### Post by wildmanne39 on 2012-04-07
Hi, are you still using wicd? it looks like network manager is also installed is that correct?
Thanks

---

### Post by cssutto on 2012-04-07
Yes on both counts.

---

### Post by wildmanne39 on 2012-04-08
Hi, you can only have one installed at a time, so if you want to use wicd run this command:
```
sudo apt-get purge network-manager network-manager-gnome
```
Then reboot and you must disconnect all internet connections before you reboot like wired, usb adapter, cell phone.
Thanks

---

### Post by cssutto on 2012-04-08
Still no wireless.

I am confused.

If wicd requires that I show wlan0 as the wireless interface and

ifconfig returns:

claude@claude-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 08:2e:5f:8a:54:ba  
          inet addr:192.168.0.196  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::a2e:5fff:fe8a:54ba/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1023 errors:0 dropped:0 overruns:0 frame:0
          TX packets:942 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:740113 (740.1 KB)  TX bytes:194430 (194.4 KB)
          Interrupt:30 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:720 (720.0 B)  TX bytes:720 (720.0 B)



Then it would appear that wicd is not able to find wlan0 either.

---

### Post by wildmanne39 on 2012-04-08
Hi for some reason your driver is not loading at boot so please do:
```
sudo su 
echo iwlagn >> /etc/modules 
exit
```

Also delete your wireless connection then reboot and set it up again.

I believe with wicd you need to set a static ip, disable IPV6 if it gives you that option.
Thanks

---

### Post by cssutto on 2012-04-08
Did all of that and still ifconfig gives the same result....no wlan0.

---

### Post by wildmanne39 on 2012-04-08
Hi, please post the output of:
```
iwconfig
rfkill list all
lsmod
```
Thanks

---

### Post by cssutto on 2012-04-08
claude@claude-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 08:2e:5f:8a:54:ba  
          inet6 addr: fe80::a2e:5fff:fe8a:54ba/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:120 (120.0 B)  TX bytes:468 (468.0 B)
          Interrupt:30 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:720 (720.0 B)  TX bytes:720 (720.0 B)

claude@claude-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 08:2e:5f:8a:54:ba  
          inet addr:192.168.0.196  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::a2e:5fff:fe8a:54ba/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:349 errors:0 dropped:0 overruns:0 frame:0
          TX packets:362 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:330748 (330.7 KB)  TX bytes:42467 (42.4 KB)
          Interrupt:30 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:16 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:960 (960.0 B)  TX bytes:960 (960.0 B)

claude@claude-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

claude@claude-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

claude@claude-laptop:~$ rfkill list all
0: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
claude@claude-laptop:~$ lsmodclear
lsmodclear: command not found
claude@claude-laptop:~$ clear

claude@claude-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

claude@claude-laptop:~$ rfkill list all
0: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
claude@claude-laptop:~$ lsmod

---

### Post by jerneja on 2012-04-08
> **wildmanne39 said:**
> Hi, it looks like you are missing the firmware we can try to get it working with this driver, and if we can not we will have to switch to the wl driver.

Download the b43 zip file to a flash drive then drag and drop the file to your ubuntu desktop. Right-click it and select Extract Here. Open a terminal and do:
```
sudo mkdir /lib/firmware/b43
sudo cp Desktop/b43/*  /lib/firmware/b43
sudo rmmod -f b43
sudo rmmod -f ssb
sudo modprobe b43
```run the commands one line at a time.
Thank you


thank you sooo much

---

### Post by wildmanne39 on 2012-04-08
Hi, try this command again please it should have output:
```
lsmod
```
Thanks

---

### Post by cssutto on 2012-04-08
claude@claude-laptop:~$ 
claude@claude-laptop:~$ lsmod
Module                  Size  Used by
cypress_m8             20185  0 
usbserial              39973  1 cypress_m8
rfcomm                 40425  4 
binfmt_misc             7960  1 
ppdev                   6375  0 
sco                     9649  2 
bridge                 53248  0 
stp                     2171  1 bridge
bnep                   11916  2 
l2cap                  34839  16 rfcomm,bnep
snd_hda_codec_idt      61546  1 
iwlagn                123060  0 
joydev                 11104  0 
usbhid                 41116  2 
hid                    83888  1 usbhid
iwlcore               125250  1 iwlagn
mac80211              238928  2 iwlagn,iwlcore
snd_hda_intel          25805  2 
snd_hda_codec          85791  2 snd_hda_codec_idt,snd_hda_intel
snd_hwdep               6924  1 snd_hda_codec
snd_pcm_oss            41394  0 
snd_mixer_oss          16299  1 snd_pcm_oss
snd_pcm                87946  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1782  0 
snd_seq_oss            31191  0 
snd_seq_midi            5829  0 
snd_rawmidi            23420  1 snd_seq_midi
snd_seq_midi_event      7267  2 snd_seq_oss,snd_seq_midi
snd_seq                57481  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
uvcvideo               62915  0 
snd_timer              23681  2 snd_pcm,snd_seq
videodev               40614  1 uvcvideo
snd_seq_device          6888  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
v4l1_compat            15495  2 uvcvideo,videodev
btusb                  13097  2 
v4l2_compat_ioctl32    11892  1 videodev
bluetooth              58717  9 rfcomm,sco,bnep,l2cap,btusb
snd                    71283  16 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
fbcon                  39270  71 
tileblit                2487  1 fbcon
font                    8053  1 fbcon
bitblit                 5811  1 fbcon
softcursor              1565  1 bitblit
cfg80211              148725  3 iwlagn,iwlcore,mac80211
soundcore               8052  1 snd
snd_page_alloc          8500  2 snd_hda_intel,snd_pcm
sdhci_pci               6700  0 
sdhci                  17960  1 sdhci_pci
xhci                   42775  0 
psmouse                65040  0 
serio_raw               4918  0 
vga16fb                12757  1 
vgastate                9857  1 vga16fb
hp_accel               12168  0 
lis3lv02d               7648  1 hp_accel
input_polldev           3106  1 lis3lv02d
video                  20623  0 
output                  2503  1 video
led_class               3764  3 iwlcore,sdhci,hp_accel
lp                      9336  0 
parport                37160  2 ppdev,lp
r8169                  39714  0 
mii                     5237  1 r8169
ahci                   38350  2 
claude@claude-laptop:~$

---

### Post by wildmanne39 on 2012-04-08
Hi, please post the output of:
```
lspci -nnk | grep -iA2 net
```
```
cat /var/lib/NetworkManager/NetworkManager.state
```
```
cat /etc/udev/rules.d/70-persistent-net.rules
```
Thanks

---

### Post by cssutto on 2012-04-09
Out untul late Monday.

Will do then.

---

### Post by cssutto on 2012-04-09
claude@claude-laptop:~$ lspci -nnk | grep -iA2 net
07:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 06)
	Kernel driver in use: r8169
	Kernel modules: r8169
0d:00.0 Network controller [0280]: Intel Corporation Device [8086:008b] (rev 34)
13:00.0 Class [ff00]: Realtek Semiconductor Co., Ltd. Device [10ec:5209] (rev 01)
13:00.1 SD Host controller [0805]: Realtek Semiconductor Co., Ltd. Device [10ec:5209] (rev 01)
claude@claude-laptop:~$ 
claude@claude-laptop:~$ 
claude@claude-laptop:~$ cat /var/lib/NetworkManager/NetworkManager.state

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
claude@claude-laptop:~$

---

### Post by centless on 2012-05-11
thnx... really helped.

---

### Post by bjarmon on 2012-08-10
wildmanne39 was a huge help getting this going for me.  Thanks a million

---

### Post by readaboook on 2012-08-14
@wildmanne39  thank you!!!! your solution was exactly what I needed. :D

---

### Post by T Bone on 2012-08-19
I am an absolute beginner with Ubuntu (despite using it for about 2  years I am completely lost once I pass surface level) but still managed  to put together bits of this thread to fix my gf's Dell Inspiron 6400 after installing Ubuntu had apparently killed wireless capability.  

I'm hugely indebted to Wildman for the time he has spent helping people here, which has helped me by proxy. If you are ever in Scotland I'll shout you a beer.

:D

---

### Post by wesf90 on 2012-08-19
> **Wild Man said:**
> Hi, it looks like you are missing the firmware we can try to get it working with this driver, and if we can not we will have to switch to the wl driver.

Download the b43 zip file to a flash drive then drag and drop the file to your ubuntu desktop. Right-click it and select Extract Here. Open a terminal and do:
```
sudo mkdir /lib/firmware/b43
sudo cp Desktop/b43/*  /lib/firmware/b43
sudo rmmod -f b43
sudo rmmod -f ssb
sudo modprobe b43
```
run the commands one line at a time.
Thank you

After 6 hours and giving up on ubuntu + wifi, I found this page and it solved all my problems. THANK YOU!

---

### Post by T Bone on 2012-08-20
I may have been too hasty in declaring success. Having turned the device back on today the wireless has completely disappeared, after working with no issues at all last night!

Initially I had no option to  use wireless, but after cack-handedly trying some of the fixes here it appeared, but with no firmware. After some more attempts to follow the thread here everything was working fine. This morning, it is as if there is no wireless at all again!

Any ideas what could be wrong?

---

### Post by Hey Gary on 2012-08-25
Wildman, you solution worked for me too, thanks.  I had been working this for weeks and then took a few weeks off to return to this working solution.  I have a Dell Latitude D800 with a broadcom BCM4306 802.11 a/b/g wireless card, ID 14e4:4324 rev 03.  Driver is B43 legacy and chip id is BCM4309 phy ver Gr1 and Gr5.

Hopefully this helps you and someone else get wireless working on another repurposed laptop.  I am using Xubuntu 12.4 and the PC is flying.  Much better than it had with old unsupported versions of windows.

Thanks again,
Gary

---

### Post by ekarner on 2012-08-25
> **Wild Man said:**
> Hi, all right this should get you going.

```
sudo apt-get install --reinstall b43-fwcutter firmware-b43-lpphy-installer
```watch it and tell me if you get any errors while it is installing.
If not reboot with the wired connection unplugged.
Thank you

Hi Wild Man,

I gave this a shot after installing Pangolin on my Dell, and it's still not working. I also tried the Additional Drivers method highlighted earlier in the thread, but always ended up with the error message "Sorry, installation of this driver failed.

Please have a look at the log file for details: /var/log/jockey.log"

I can't find the log, so details don't seem available.  Can you help?

**EDIT** I found the solution [here]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#Installing%20STA%20drivers"). It was a weird one, but my computer always seems to be the weird one.

---

### Post by stainwayne on 2012-09-02
this did not work for me please help me someone i am having a very hard time with this stuff am very new to it

---

### Post by wildmanne39 on 2012-09-02
Hi, copy and paste this command in the terminal (ctrl+alt+t) please:
```
wget -N -t 5 -T 10 http://dl.dropbox.com/u/57264241/wireless_script && chmod +x wireless_script && ./wireless_script
```
It will download a script and create a text file in your home folder with wireless information so we can see the condition of your wireless at this time and the Mac address, WPA key and WEP key are removed for your security,  then reply back  and attach the netinfo.txt file.
Thanks

---

### Post by OldNovice on 2012-09-16
I had installed Ubuntu 12.04 from a CD on a Dell Latitude D610, which had been wiped clean.  I had this missing firmware problem with the internal Broadcom BCM4318 card, so I used a USB wireless chipset to complete the installation, and establish a connection to the web.  Looking through this very relevant thread, marked by WildMan's incredible patience and expertise, and also the linked page in user documentation about Broadcom 43xx series wirelass cards, and trying a few things, I found that the following command did the trick:
sudo apt-get install --install b43-fwcutter firmware-b43-installer
That brought the wireless card back to life, so when I shut the system down, unplugged the USB wireless card, and rebooted, I was guided automatically through the steps needed to connect to the router through the 4318.
Many thanks, WildMan.

---

### Post by acme_labs on 2012-11-23
> **Wild Man said:**
> Hi, it looks like you are missing the firmware we can try to get it working with this driver, and if we can not we will have to switch to the wl driver.

Download the b43 zip file to a flash drive then drag and drop the file to your ubuntu desktop. Right-click it and select Extract Here. Open a terminal and do:
```
sudo mkdir /lib/firmware/b43
sudo cp Desktop/b43/*  /lib/firmware/b43
sudo rmmod -f b43
sudo rmmod -f ssb
sudo modprobe b43
```run the commands one line at a time.
Thank you

This worked for the HP dv5020us, which has the bcm4318 (rev2)
Thank you Wild Man, you just made this Thanksgiving day, a little more thankfull!:)

---

### Post by upliftingmail on 2012-12-02
Worked for me too, thanks

> **firebird21 said:**
> Hi, Thanks a lot! 
I had the same issue..firmware missing..It worked like magic.

cheers,

---

### Post by eidelmaim on 2012-12-04
so Wildman, i hear you are the master of all things wireless !

i am completely new to Ubuntu, i was trying to follow along to your commands but i seem to have gotten a little lost maybe... 

sudo mkdir /lib/firmware/b43 
sudo cp Desktop/b43/*  /lib/firmware/b43 


these commands return : ERROR: Removing 'b43': No such file or directory
sudo rmmod -f b43 
sudo rmmod -f ssb

this command is returning : WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
sudo modprobe b43

i sure could use your expertise in solving this.

i am running Ubuntu 12.10
i have installed a Linksys WMP300n wireless N card
i am running a ASUS M3N78-EM motherboard with the latest bios flash.
this is a 64 bit platform

i can see you have beaten this dog beyond dead and i hate to bring it up again, but i could really use some help, let me know what else you may need to help me solve this wireless issue.

Thanks, Eidel

i have ran the script below and attached the netinfo.txt file

wget -N -t 5 -T 10 [http://dl.dropbox.com/u/57264241/wireless_script](http://dl.dropbox.com/u/57264241/wireless_script) && chmod +x wireless_script && ./wireless_script


*** update ***
um.. so wow... after running that netinfo scrit the wireless network just started working on its own ! .. i dont know why..... ok so another update... it is "working" by being able to see my networks now... but for some reason it will not connect to these networks. it is constantly wanting to know my wpa/wpa2 key. i have verified it several times in my router GUI and even C/P it but to no avail.... i am going to do a open network test in a min... and i am going to upload a new netinfo.txt also.

---

### Post by wildmanne39 on 2012-12-04
Hi, copy and paste this command in the terminal (ctrl+alt+t) please:
```
wget -N -t 5 -T 10 http://dl.dropbox.com/u/57264241/wireless_script && chmod +x wireless_script && ./wireless_script
```
It will download a script and create a text file in your home folder with wireless information so we can see the condition of your wireless at this time and the Mac address, WPA key and WEP key are removed for your security,  then reply back  and attach the netinfo.txt file.

No I am not the master that would be chili555.

I am starting a new job so if I am here when you post I will help but you need to be quick otherwise there are some other people here that will help you.
Thanks

---

### Post by wildmanne39 on 2012-12-04
Hi, please do:
```
sudo apt-get remove --purge b43-fwcutter firmware-b43-installer
```
```
sudo apt-get install --reinstall linux-headers-$(uname -r) build-essential dkms
```
```
sudo apt-get install bcmwl-kernel-source broadcom-sta-common broadcom-sta-source
```
Reboot

If it still does not connect tell us what network you are trying to connect too.

I recommend changing your encryption in the router to just wpa2 if you have that option.
Thanks

---

### Post by eidelmaim on 2012-12-04
> **Wild Man said:**
> Hi, please do:
```
sudo apt-get remove --purge b43-fwcutter firmware-b43-installer
``````
sudo apt-get install --reinstall linux-headers-$(uname -r) build-essential dkms
``````
sudo apt-get install bcmwl-kernel-source broadcom-sta-common broadcom-sta-source
```Reboot

If it still does not connect tell us what network you are trying to connect too.

I recommend changing your encryption in the router to just wpa2 if you have that option.
Thanks

i ran these commands, here is what i am getting. the system is seeing the networks. it will not however connect to them. i removed all network security and ran a open network. still unable to connect and pull a proper IP address from the router.

i ran the network script and included the attachment. ( i have to split up the attachment as it is 35.8kbs and exceeds the forum limits)

** Just after posting this the computer stopped being able to "see" the networks... like they were never there in the first place

---

### Post by wildmanne39 on 2012-12-04
Hi, it says you are still using the b43 driver, please copy and paste the commands into the terminal for accuracy and watch for errors.

What is the name of the network you want to connect too?
Thanks

---

### Post by trallallero on 2013-01-04
Same problem here, driver iwlagn, firmware missing.
Ubuntu 12.04, worst os ever :x

---

