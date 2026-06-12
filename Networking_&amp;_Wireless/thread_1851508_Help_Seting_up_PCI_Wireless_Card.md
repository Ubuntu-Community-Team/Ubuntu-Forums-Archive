---
title: "Help Seting up PCI Wireless Card"
date: 2011-09-28
forum: Networking &amp; Wireless
---

### Post by tcb2185 on 2011-09-28
I just installed ubuntu 11.04 32bit along Side of my my windows 7 32bit but i can not for the life of me figger out how to setup my pci wireless card. Any help would be Great!

---

### Post by wildmanne39 on 2011-09-28
Hi, welcome to the forum! please open a terminal by hitting ctrl+alt+t then copy and paste the commands into the terminal then paste the results here:
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

### Post by tcb2185 on 2011-09-28
```
Code:
cat /etc/lsb-release; uname -a
tim@tim-desktop:~$ cat /etc/lsb-release; uname -a

DISTRIB_ID=Ubuntu

DISTRIB_RELEASE=11.04

DISTRIB_CODENAME=natty

DISTRIB_DESCRIPTION="Ubuntu 11.04"

Linux tim-desktop 2.6.38-8-generic #42-Ubuntu SMP Mon Apr 11 03:31:50 UTC 2011 i686 i686 i386 GNU/Linux

```

```

Code:
lspci -nnk | grep -iA2 net
tim@tim-desktop:~$ lspci -nnk | grep -iA2 net

02:02.0 Network controller [0280]: Ralink corp. Device [1814:3062]

	Subsystem: Ralink corp. Device [1814:3062]

	Kernel driver in use: rt2800pci

--

02:08.0 Ethernet controller [0200]: Intel Corporation 82562EZ 10/100 Ethernet Controller [8086:1050] (rev 01)

	Subsystem: Intel Corporation Desktop Board D865GBF [8086:302f]

	Kernel driver in use: e100

```

```
Code:
iwconfig
tim@tim-desktop:~$ iwconfig

lo        no wireless extensions.



eth0      no wireless extensions.



wlan0     IEEE 802.11bgn  ESSID:off/any  

          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   

          Retry  long limit:7   RTS thr:off   Fragment thr:off

          Power Management:off

```

```

Code:
rfkill list all  
tim@tim-desktop:~$ rfkill list all

0: phy0: Wireless LAN

	Soft blocked: no

	Hard blocked: no

```

```

Code:
lsmod
tim@tim-desktop:~$ lsmod

Module                  Size  Used by

snd_usb_audio          91410  1 

snd_intel8x0           33213  2 

snd_hwdep              13274  1 snd_usb_audio

snd_ac97_codec        105614  1 snd_intel8x0

ac97_bus               12642  1 snd_ac97_codec

arc4                   12473  2 

snd_pcm                80244  3 snd_usb_audio,snd_intel8x0,snd_ac97_codec

snd_usbmidi_lib        24388  1 snd_usb_audio

rt2800pci              18159  0 

snd_seq_midi           13132  0 

rt2800lib              43824  1 rt2800pci

crc_ccitt              12595  1 rt2800lib

rt2x00pci              13986  1 rt2800pci

rt2x00lib              39075  3 rt2800pci,rt2800lib,rt2x00pci

mac80211              257001  3 rt2800lib,rt2x00pci,rt2x00lib

snd_rawmidi            25269  2 snd_usbmidi_lib,snd_seq_midi

binfmt_misc            13213  1 

ppdev                  12849  0 

snd_seq_midi_event     14475  1 snd_seq_midi

snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event

cfg80211              156212  2 rt2x00lib,mac80211

nouveau               621970  1 

ttm                    65184  1 nouveau

drm_kms_helper         40745  1 nouveau

drm                   180037  4 nouveau,ttm,drm_kms_helper

snd_timer              28659  2 snd_pcm,snd_seq

snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq

parport_pc             32111  1 

i2c_algo_bit           13184  1 nouveau

joydev                 17322  0 

psmouse                73312  0 

uvcvideo               66851  0 

video                  18951  1 nouveau

videodev               75143  1 uvcvideo

snd                    55295  16 snd_usb_audio,snd_hwdep,snd_intel8x0,snd_ac97_codec,snd_pcm,snd_usbmidi_lib,snd_rawmidi,snd_seq,snd_timer,snd_seq_device

eeprom_93cx6           12653  1 rt2800pci

serio_raw              12990  0 

soundcore              12600  1 snd

snd_page_alloc         14073  2 snd_intel8x0,snd_pcm

shpchp                 32345  0 

lp                     13349  0 

parport                36746  3 ppdev,parport_pc,lp

usbhid                 41704  0 

hid                    77084  1 usbhid

e100                   40108  0 

```

---

### Post by wildmanne39 on 2011-09-28
Hi, how did you install this driver and from where?
Thank you

---

### Post by tcb2185 on 2011-09-28
What the 11.04? i downloaded it right from ubuntu website. and made a disk. and put it in there and installed it..?

---

### Post by wildmanne39 on 2011-09-28
Hi, no I meant how did you install the the driver for your wireless? did you activate it in additional drivers? or install it another way or is it just present in the kernel?

That does not matter here is a link follow the directions and you should get a working wireless card, all the directions are in post 20.
[http://ubuntuforums.org/showthread.php?t=1780136&page=2](http://ubuntuforums.org/showthread.php?t=1780136&page=2)
Thank you

---

### Post by tcb2185 on 2011-09-30
is there a easyer way of doing this? i mean Im not a very Tech type of guy. but i can handle some small stuff.. ?

---

### Post by tcb2185 on 2011-09-30
is there a easyer way of doing this? i mean Im not a very Tech type of guy. but i can handle some small stuff.. ?  I Also have all the Drivers on a Cd that came with the PCI Card.

---

### Post by praseodym on 2011-09-30
Hi,

you need to install a driver by hand. Just copy/paste the following lines into the terminal via cable connection:

```
sudo apt-get install linux-headers-$(uname -r) build-essential dkms
wget http://media.cdn.ubuntu-de.org/forum/attachments/2739482/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217_prepared.tar.gz
tar xvf DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217_prepared.tar.gz
cd DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217_prepared
sudo make
sudo make install 
echo "blacklist rt2800pci" | sudo tee -a /etc/modprobe.d/blacklist.conf 
```
Reboot. Then you should update your system:

```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
sudo apt-get install linux-headers-generic
```
Reboot, now

```
uname -a
```

should show kernel 2.6.38-11-generic. If the wireless doesnt work with that you have to compile again, so dont delete the folder:

```
cd DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217_prepared
sudo make clean 
sudo make
sudo make install 
```
Check with the new kernel:

```
lspci -nnk | grep -iA2 net
iwconfig
rfkill list
lsmod
sudo iwlist scan
```

---

### Post by tcb2185 on 2011-09-30
```
rfkill list
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
tim@tim-desktop:~$ lsmod
Module                  Size  Used by
rt2870sta             410104  0 
arc4                   12473  2 
rt2800usb              17907  0 
rt2800lib              43824  1 rt2800usb
crc_ccitt              12595  2 rt2870sta,rt2800lib
rt2x00usb              19693  1 rt2800usb
rt2x00lib              39075  3 rt2800usb,rt2800lib,rt2x00usb
mac80211              257001  3 rt2800lib,rt2x00usb,rt2x00lib
cfg80211              156212  2 rt2x00lib,mac80211
nls_utf8               12493  1 
isofs                  39571  1 
snd_usb_audio          91410  1 
snd_intel8x0           33213  2 
snd_ac97_codec        105614  1 snd_intel8x0
ac97_bus               12642  1 snd_ac97_codec
snd_pcm                80042  3 snd_usb_audio,snd_intel8x0,snd_ac97_codec
snd_hwdep              13274  1 snd_usb_audio
snd_usbmidi_lib        24388  1 snd_usb_audio
snd_seq_midi           13132  0 
snd_rawmidi            25269  2 snd_usbmidi_lib,snd_seq_midi
joydev                 17322  0 
nouveau               621970  2 
binfmt_misc            13213  1 
ppdev                  12849  0 
snd_seq_midi_event     14475  1 snd_seq_midi
ttm                    65184  1 nouveau
drm_kms_helper         40745  1 nouveau
drm                   184164  4 nouveau,ttm,drm_kms_helper
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
usbhid                 41704  0 
uvcvideo               66851  0 
i2c_algo_bit           13184  1 nouveau
video                  18951  1 nouveau
snd_timer              28659  2 snd_pcm,snd_seq
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
psmouse                73312  0 
hid                    77084  1 usbhid
snd                    55295  16 snd_usb_audio,snd_intel8x0,snd_ac97_codec,snd_hwdep,snd_usbmidi_lib,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
videodev               75143  1 uvcvideo
serio_raw              12990  0 
parport_pc             32111  1 
soundcore              12600  1 snd
snd_page_alloc         14073  2 snd_intel8x0,snd_pcm
shpchp                 32345  0 
lp                     13349  0 
parport                36746  3 ppdev,parport_pc,lp
e100                   40108  0 
floppy                 60032  0 
tim@tim-desktop:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 40:4A:03:07:AE:25
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=39/70  Signal level=-71 dBm  
                    Encryption key:off
                    ESSID:"ZyXEL"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000002f2c31c07f
                    Extra: Last beacon: 12ms ago
                    IE: Unknown: 00055A7958454C
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD960050F204104A0001101044000101103B0001031047001063041253101920061228404A0307AE251021001B5265616C74656B2053656D69636F6E647563746F7220436F72702E1023000752544C383138361024000D45562D323030362D30372D32371042000F3132333435363738393031323334371054000800060050F20400011011000B5A7958454C205033333057100800020086
                    IE: Unknown: DD0700E04C01020300
          Cell 02 - Address: C0:3F:0E:D2:86:A4
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=23/70  Signal level=-87 dBm  
                    Encryption key:on
                    ESSID:"NTGR_pFzhW0izaKlZEnaJI8IIJo"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000083cee54195
                    Extra: Last beacon: 296ms ago
                    IE: Unknown: 001B4E5447525F70467A685730697A614B6C5A456E614A493849494A6F
                    IE: Unknown: 010882840B162430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 050400030000
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1A7C181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D160B080000000000000000000000000000000000000000
                    IE: Unknown: DD0E0050F204104A0001101044000102
                    IE: Unknown: DD090010180200F0050000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C337C181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C340B080000000000000000000000000000000000000000
          Cell 03 - Address: E0:91:F5:D7:E1:F8
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=31/70  Signal level=-79 dBm  
                    Encryption key:on
                    ESSID:"CARLSONS-PC_Network"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000002f2c94e9b7
                    Extra: Last beacon: 4784ms ago
                    IE: Unknown: 00134341524C534F4E532D50435F4E6574776F726B
                    IE: Unknown: 010882840B162430486C
                    IE: Unknown: 030101
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD7F0050F204104A00011010440001021041000100103B00010310470010536C9835AC408D83F4D3199914A26BC21021000D4E4554474541522C20496E632E10230009574752363134763130102400095747523631347631301042000538333235381054000800060050F204000110110009574752363134763130100800020084
                    IE: Unknown: DD090010180200F0050000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00

```

---

### Post by tcb2185 on 2011-09-30
Still not working the only thing working is my usb wifi adapter and i really dont want to use that..

---

### Post by praseodym on 2011-10-01
Did you install the driver? Please show:

```
modinfo rt3562sta | egrep 'versi|filen'
sudo modprobe -v rt3562sta
lspci -nnk | grep -iA2 net
lsusb
```

---

### Post by kurt18947 on 2011-10-01
deleted. Unreable formatting

---

### Post by kurt18947 on 2011-10-01
Pardon my intrusion here.  I haven't had to mess with Ralink devices but looking at the output of lsmod:
```
rfkill list
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
tim@tim-desktop:~$ lsmod
Module                  Size  Used by
rt2870sta             410104  0 
arc4                   12473  2 
rt2800usb              17907  0 
rt2800lib              43824  1 rt2800usb
crc_ccitt              12595  2 rt2870sta,rt2800lib
rt2x00usb              19693  1 rt2800usb
rt2x00lib              39075  3 rt2800usb,rt2800lib,rt2x00usb
mac80211              257001  3 rt2800lib,rt2x00usb,rt2x00lib
cfg80211              156212  2 rt2x00lib,mac80211
```is there more than one module trying to run the same device?  Perhaps trying to blacklist everything but rt2870sta or rt2800usb and see what happens?

---

### Post by praseodym on 2011-10-01
There are only modules loaded for the USB-device (2 of them, I am wondering it is working). No PCI module loaded. Please show

```
lsmod #completely
lspci -nnk | grep -iA2 net
lsusb
iwconfig
cat /etc/udev/rules.d/70-persistent-net.rules
dmesg | egrep 'rt2|rt3'
```

---

### Post by tcb2185 on 2011-10-01
> **praseodym said:**
> There are only modules loaded for the USB-device (2 of them, I am wondering it is working). No PCI module loaded. Please show

```
lsmod #completely
lspci -nnk | grep -iA2 net
lsusb
iwconfig
cat /etc/udev/rules.d/70-persistent-net.rules
dmesg | egrep 'rt2|rt3'
```

```
tim@tim-desktop:~$ lsmod #completely
Module                  Size  Used by
nls_utf8               12493  1 
isofs                  39571  1 
vesafb                 13449  1 
binfmt_misc            13213  1 
snd_intel8x0           33213  2 
snd_ac97_codec        105614  1 snd_intel8x0
ac97_bus               12642  1 snd_ac97_codec
nvidia               9766978  38 
rt2870sta             410104  0 
arc4                   12473  2 
rt2800usb              17907  0 
snd_usb_audio          91410  1 
rt2800lib              43824  1 rt2800usb
crc_ccitt              12595  2 rt2870sta,rt2800lib
snd_pcm                80042  3 snd_intel8x0,snd_ac97_codec,snd_usb_audio
rt2x00usb              19693  1 rt2800usb
rt2x00lib              39075  3 rt2800usb,rt2800lib,rt2x00usb
snd_hwdep              13274  1 snd_usb_audio
snd_usbmidi_lib        24388  1 snd_usb_audio
snd_seq_midi           13132  0 
mac80211              257001  3 rt2800lib,rt2x00usb,rt2x00lib
snd_rawmidi            25269  2 snd_usbmidi_lib,snd_seq_midi
joydev                 17322  0 
snd_seq_midi_event     14475  1 snd_seq_midi
ppdev                  12849  0 
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
cfg80211              156212  2 rt2x00lib,mac80211
usbhid                 41704  0 
uvcvideo               66851  0 
snd_timer              28659  2 snd_pcm,snd_seq
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
parport_pc             32111  1 
snd                    55295  16 snd_intel8x0,snd_ac97_codec,snd_usb_audio,snd_pcm,snd_hwdep,snd_usbmidi_lib,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
hid                    77084  1 usbhid
psmouse                73312  0 
videodev               75143  1 uvcvideo
soundcore              12600  1 snd
snd_page_alloc         14073  2 snd_intel8x0,snd_pcm
shpchp                 32345  0 
serio_raw              12990  0 
lp                     13349  0 
parport                36746  3 ppdev,parport_pc,lp
floppy                 60032  0 
e100                   40108  0 
tim@tim-desktop:~$ lspci -nnk | grep -iA2 net
02:02.0 Network controller [0280]: Ralink corp. Device [1814:3062]
	Subsystem: Ralink corp. Device [1814:3062]
	Kernel modules: rt2800pci
02:08.0 Ethernet controller [0200]: Intel Corporation 82562EZ 10/100 Ethernet Controller [8086:1050] (rev 01)
	Subsystem: Intel Corporation Desktop Board D865GBF [8086:302f]
	Kernel driver in use: e100
tim@tim-desktop:~$ lsusb
Bus 005 Device 002: ID 046d:c51b Logitech, Inc. V220 Cordless Optical Mouse for Notebooks
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 04b3:300a IBM Corp. Rapid Access IIIe Keyboard
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 0c45:62e0 Microdia MSI Starcam Racer
Bus 001 Device 002: ID 148f:2070 Ralink Technology, Corp. RT2070 Wireless Adapter
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
tim@tim-desktop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"ZyXEL"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 40:4A:03:07:AE:25   
          Bit Rate=48 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=43/70  Signal level=-67 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:306  Invalid misc:37   Missed beacon:0

tim@tim-desktop:~$ cat /etc/udev/rules.d/70-persistent-net.rules
# This file maintains persistent names for network interfaces.
# See udev(7) for syntax.
#
# Entries are automatically added by the 75-persistent-net-generator.rules
# file; however you are also free to add your own entries.

# PCI device 0x8086:0x1050 (e100)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:11:11:cd:97:b8", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# USB device 0x148f:0x2070 (usb)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:e0:4c:32:cd:39", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

# PCI device 0x1814:0x3062 (rt2800pci)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:a1:b0:62:86:ef", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan1"
tim@tim-desktop:~$ dmesg | egrep 'rt2|rt3'

```

---

### Post by tcb2185 on 2011-10-01
> **praseodym said:**
> Did you install the driver? Please show:

```
modinfo rt3562sta | egrep 'versi|filen'
sudo modprobe -v rt3562sta
lspci -nnk | grep -iA2 net
lsusb
```
```
FATAL: Module rt3562sta not found.

```

---

### Post by wildmanne39 on 2011-10-01
Hi, did you ever follow the directions in post 6?
Thank you

---

### Post by praseodym on 2011-10-01
Ok, several things to do:

Blacklist the driver rt2800usb for the stick:

```
echo "blacklist rt2800usb" | sudo tee -a /etc/modprobe.d/blacklist.conf
```
Normally the device ID is missing in the rt2870sta, following _one-liner_ (copy/paste) helps:
```
echo 'install rt2870sta modprobe --ignore-install rt2870sta ; /bin/echo "148f 2070" > /sys/bus/usb/drivers/rt2870/new_id' | sudo tee /etc/modprobe.d/rt2870sta.conf 
```
Add an UDEV-rule additionally:

```
gksudo gedit /etc/udev/rules.d/10-wlan_stick.rules 
```
Insert:
```
# UDEV-Rule for ID 148f:2070
SUBSYSTEM=="usb", ATTR{idVendor}=="148f", ATTR{idProduct}=="2070", RUN+="/sbin/modprobe rt2870sta"
```
save, close, and:
```
sudo service udev reload
```
After that, create another UDEV-rule according to [this]("http://ubuntuforums.org/showpost.php?p=11247931&postcount=13") posting; replace [COLOR="Red"]b43[/COLOR] from that example with [COLOR="Red"]rt2800pci[/COLOR] This unloads the internal PCI-driver if the stick is plugged in.

Reboot after all these changes, and check:

```
lspci -nnk | grep -iA2 net
lsmod
iwconfig
cat /etc/udev/rules.d/70-persistent-net.rules
sudo iwlist scan
```
We'll see then, if the right module is replaced.

---

