---
title: "Ubuntu 11.10 - issues with Edimax 7711ln PCI"
date: 2012-07-29
forum: Networking &amp; Wireless
---

### Post by Ivir Baggins on 2012-07-29
I am using an Edimax EW7711 ln PCI card. I've installed both the hardware and the software, yet it cannot find my local network. There are 4 networks in range, and it cannot even find my home one. I have to tell it to connect to "hidden network", but when I do, it asks for the password three times despite it already being typed in automatically, then fails to connect. Can someone help?

---

### Post by Ivir Baggins on 2012-08-02
Bump.

---

### Post by praseodym on 2012-08-02
Please show the outputs of:

```
uname -a
lspci -nnk | grep -iA2 net
lsusb
lsmod
iwconfig
rfkill list
dmesg | egrep 'rt2|wlan'
```

---

### Post by Ivir Baggins on 2012-08-02
uname -a:
Linux gamesroom-Dell-DM051 3.0.0-23-generic #39-Ubuntu SMP Thu Jul 19 19:18:53 UTC 2012 i686 i686 i386 GNU/Linux

lspci -nnk | grep -iA2 net:
03:02.0 Network controller [0280]: Ralink corp. Device [1814:3062]
    Subsystem: Edimax Computer Co. Device [1432:7722]
    Kernel driver in use: rt2800pci
--
03:08.0 Ethernet controller [0200]: Intel Corporation N10/ICH 7 Family LAN Controller [8086:27dc] (rev 01)
    Subsystem: Dell Device [1028:01ab]
    Kernel driver in use: e100

lsusb:
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 14cd:6700 Super Top Card Reader
Bus 001 Device 005: ID 090c:1000 Feiya Technology Corp. Flash Drive
Bus 003 Device 002: ID 1241:1111 Belkin Mouse
Bus 004 Device 002: ID 046d:c509 Logitech, Inc. Cordless Keyboard & Mouse

lsmod:
Module                  Size  Used by
snd_seq_dummy          12686  0 
nls_iso8859_1          12617  1 
nls_cp437              12751  1 
vfat                   17308  1 
fat                    55577  1 vfat
snd_hrtimer            12648  1 
bnep                   17923  2 
rfcomm                 38408  0 
bluetooth             148869  10 bnep,rfcomm
parport_pc             32114  0 
ppdev                  12849  0 
arc4                   12473  2 
rt2800pci              18340  0 
rt2800lib              48909  1 rt2800pci
crc_ccitt              12595  1 rt2800lib
rt2x00pci              14202  1 rt2800pci
rt2x00lib              48146  3 rt2800pci,rt2800lib,rt2x00pci
binfmt_misc            17292  1 
mac80211              393421  3 rt2800lib,rt2x00pci,rt2x00lib
dcdbas                 14098  0 
radeon                933705  3 
psmouse                73673  0 
snd_hda_codec_idt      60049  1 
cfg80211              172427  2 rt2x00lib,mac80211
snd_hda_intel          28358  4 
snd_hda_codec          91888  2 snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
usbhid                 41905  0 
hid                    77367  1 usbhid
snd_pcm                80435  3 snd_hda_intel,snd_hda_codec
serio_raw              12990  0 
eeprom_93cx6           12653  1 rt2800pci
ttm                    65224  1 radeon
drm_kms_helper         32889  1 radeon
drm                   192194  5 radeon,ttm,drm_kms_helper
snd_seq_midi           13132  0 
snd_rawmidi            25241  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  4 snd_seq_dummy,snd_seq_midi,snd_seq_midi_event
snd_timer              28932  3 snd_hrtimer,snd_pcm,snd_seq
snd_seq_device         14172  4 snd_seq_dummy,snd_seq_midi,snd_rawmidi,snd_seq
snd                    55902  17 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
i2c_algo_bit           13199  1 radeon
lp                     17455  0 
soundcore              12600  1 snd
parport                40930  3 parport_pc,ppdev,lp
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
usb_storage            44172  1 
uas                    17829  0 
e100                   36289  0 

iwconfig:
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off

rfkill list:
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

dmesg | egrep 'rt2|wlan':
[   17.881454] rt2800pci 0000:03:02.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   18.124936] Registered led device: rt2800pci-phy0::radio
[   18.125045] Registered led device: rt2800pci-phy0::assoc
[   18.125156] Registered led device: rt2800pci-phy0::quality
[   18.628298] phy0 -> rt2800pci_mcu_status: Error - MCU request failed, no response from hardware
[   18.653179] ADDRCONF(NETDEV_UP): wlan0: link is not ready

---

### Post by praseodym on 2012-08-02
>  [ 18.628298] phy0 -> rt2800pci_mcu_status: Error - MCU request failed, no response from hardware
Try to reset the BIOS

---

### Post by Ivir Baggins on 2012-08-03
How?

---

### Post by praseodym on 2012-08-03
If you reboot, there should be a key shown (DEL or F12?) to enter the BIOS. Normally you reset there with F9 and "Save&Exit" with F10

---

### Post by Ivir Baggins on 2012-08-04
I pressed F12 when you said, but pressing F9 did nothing. I'm using a Dell Dimension 5150 if that's any help.

---

### Post by praseodym on 2012-08-04
Maybe its F5? Have a look, how to reset, use the arrow keys to move

---

### Post by praseodym on 2012-08-04
Alternatively, install the "old" driver:

```
wget http://www.pchsws.net/DATEIEN/rt2860sta.deb
sudo dpkg -i rt2860sta.deb
echo -e "blacklist rt2800pci\nblacklist rt2800lib" | sudo tee -a /etc/modprobe.d/blacklist.conf
```
Reboot.

---

### Post by Ivir Baggins on 2012-08-04
For the second step of that, I got this:

Selecting previously deselected package rt3090-dkms.
(Reading database ... 267081 files and directories currently installed.)
Unpacking rt3090-dkms (from rt2860sta.deb) ...
dpkg: dependency problems prevent configuration of rt3090-dkms:
 rt3090-dkms depends on dkms; however:
  Package dkms is not installed.
dpkg: error processing rt3090-dkms (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 rt3090-dkms


How do I solve these errors?

---

### Post by praseodym on 2012-08-04
Install all needed packages for successful compiling:

```
sudo apt-get install --reinstall linux-headers-generic build-essential dkms
```
Then try it again.

---

