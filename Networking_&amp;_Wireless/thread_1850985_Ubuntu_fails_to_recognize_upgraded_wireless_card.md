---
title: "Ubuntu fails to recognize upgraded wireless card"
date: 2011-09-27
forum: Networking &amp; Wireless
---

### Post by sysrpl on 2011-09-27
For a while now my laptop has been smoothly running both Windows 7 and Ubuntu 10.10 by swapping SSDs.

Last week I upgraded the wireless card the an Intel 5300abgn card that supports N. The upgrade in Windows went smoothly, but when I switched back to Ubuntu the wireless is no longer working.

I think Ubuntu just doesn't see my new card even though from what I've read the card is widely supported by Ubuntu.

I think I need a driver called iwlwifi installed and configured to work with my kernel (2.6.35-30-generic) but have no idea how to do this. Can I get some help/steps on how to configure my Ubuntu install to work with this new networked card?

thanks.

---

### Post by praseodym on 2011-09-27
Hi,

please show:

```
lspci -nnk | grep -iA2 net
iwconfig
lsmod
rfkill list
cat /etc/udev/rules.d/70-persistent-net.rules
```

---

### Post by sysrpl on 2011-09-27
Here you go:

```
user@machine:~$ lspci -nnk | grep -iA2 net
03:00.0 Ethernet controller [0200]: Broadcom Corporation BCM4401-B0 100Base-TX [14e4:170c] (rev 02)
	Subsystem: Dell Device [1028:0228]
	Kernel driver in use: b44
--
0c:00.0 Network controller [0280]: Intel Corporation Ultimate N WiFi Link 5300 [8086:4235]
	Subsystem: Intel Corporation Device [8086:1001]
	Kernel modules: iwlagn

user@machine:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

user@machine:~$ lsmod
Module                  Size  Used by
parport_pc             26058  0 
ppdev                   5556  0 
joydev                  8767  0 
nvidia              10382361  44 
binfmt_misc             6599  1 
snd_hda_codec_idt      54951  1 
snd_hda_intel          22235  2 
snd_hda_codec          87552  2 snd_hda_codec_idt,snd_hda_intel
snd_hwdep               5040  1 snd_hda_codec
snd_pcm                71475  2 snd_hda_intel,snd_hda_codec
snd_seq_midi            4588  0 
snd_rawmidi            17783  1 snd_seq_midi
snd_seq_midi_event      6047  1 snd_seq_midi
snd_seq                47174  2 snd_seq_midi,snd_seq_midi_event
iwlagn                179111  0 
iwlcore               127415  1 iwlagn
mac80211              231927  2 iwlagn,iwlcore
snd_timer              19067  2 snd_pcm,snd_seq
snd_seq_device          5744  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    49102  13 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
dell_wmi                2852  0 
r852                    9536  0 
sm_common               3285  1 r852
dell_laptop             5730  0 
dcdbas                  5402  1 dell_laptop
cfg80211              144822  3 iwlagn,iwlcore,mac80211
nand                   34905  2 r852,sm_common
nand_ids                2903  1 nand
nand_ecc                3938  1 nand
psmouse                59033  0 
soundcore                880  1 snd
video                  18712  0 
mtd                    18877  2 sm_common,nand
snd_page_alloc          7120  2 snd_hda_intel,snd_pcm
output                  1883  1 video
serio_raw               4022  0 
intel_agp              26566  0 
agpgart                32011  2 nvidia,intel_agp
lp                      7342  0 
parport                31492  3 parport_pc,ppdev,lp
usbhid                 36882  0 
hid                    67742  1 usbhid
firewire_ohci          21234  0 
ahci                   19326  2 
b44                    26253  0 
ssb                    39320  1 b44
sdhci_pci               6633  0 
sdhci                  15922  1 sdhci_pci
led_class               2633  1 sdhci
firewire_core          46643  1 firewire_ohci
crc_itu_t               1383  1 firewire_core
mii                     4425  1 b44
libahci                21728  1 ahci

user@machine:~$ rfkill list
0: dell-wifi: Wireless LAN
	Soft blocked: no
	Hard blocked: no

user@machine:~$ cat /etc/udev/rules.d/70-persistent-net.rules
# This file maintains persistent names for network interfaces.
# See udev(7) for syntax.
#
# Entries are automatically added by the 75-persistent-net-generator.rules
# file; however you are also free to add your own entries.

# PCI device 0x14e4:0x170c (b44)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:1c:23:a0:49:22", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x8086:0x4222 (iwl3945)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:1c:bf:1d:04:18", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

```

---

### Post by praseodym on 2011-09-27
Setup a new udev-file:

```
sudo mv /etc/udev/rules.d/70-persistent-net.rules /etc/udev/rules.d/70-persistent-net.bak
sudo udevadm trigger
sudo service udev reload
```
You may reboot and check again as seen above.

---

### Post by sysrpl on 2011-09-27
Okay, here is what get after moving that file and rebooting:

```
user@machine:~$ lspci -nnk | grep -iA2 net
03:00.0 Ethernet controller [0200]: Broadcom Corporation BCM4401-B0 100Base-TX [14e4:170c] (rev 02)
	Subsystem: Dell Device [1028:0228]
	Kernel driver in use: b44

user@machine:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

user@machine:~$ lsmod
Module                  Size  Used by
parport_pc             26058  0 
ppdev                   5556  0 
nvidia              10382361  44 
joydev                  8767  0 
binfmt_misc             6599  1 
snd_hda_codec_idt      54951  1 
snd_hda_intel          22235  2 
snd_hda_codec          87552  2 snd_hda_codec_idt,snd_hda_intel
snd_hwdep               5040  1 snd_hda_codec
snd_pcm                71475  2 snd_hda_intel,snd_hda_codec
snd_seq_midi            4588  0 
snd_rawmidi            17783  1 snd_seq_midi
snd_seq_midi_event      6047  1 snd_seq_midi
snd_seq                47174  2 snd_seq_midi,snd_seq_midi_event
snd_timer              19067  2 snd_pcm,snd_seq
snd_seq_device          5744  3 snd_seq_midi,snd_rawmidi,snd_seq
r852                    9536  0 
sm_common               3285  1 r852
nand                   34905  2 r852,sm_common
nand_ids                2903  1 nand
nand_ecc                3938  1 nand
snd                    49102  13 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
mtd                    18877  2 sm_common,nand
dell_wmi                2852  0 
psmouse                59033  0 
soundcore                880  1 snd
dell_laptop             5730  0 
snd_page_alloc          7120  2 snd_hda_intel,snd_pcm
serio_raw               4022  0 
dcdbas                  5402  1 dell_laptop
intel_agp              26566  0 
video                  18712  0 
agpgart                32011  2 nvidia,intel_agp
output                  1883  1 video
lp                      7342  0 
parport                31492  3 parport_pc,ppdev,lp
b44                    26253  0 
ahci                   19326  2 
ssb                    39320  1 b44
firewire_ohci          21234  0 
sdhci_pci               6633  0 
firewire_core          46643  1 firewire_ohci
libahci                21728  1 ahci
sdhci                  15922  1 sdhci_pci
led_class               2633  1 sdhci
crc_itu_t               1383  1 firewire_core
mii                     4425  1 b44

user@machine:~$ rfkill list

user@machine:~$ cat /etc/udev/rules.d/70-persistent-net.rules
# This file was automatically generated by the /lib/udev/write_net_rules
# program, run by the persistent-net-generator.rules rules file.
#
# You can modify it, as long as you keep each rule on a single
# line, and change only the value of the NAME= key.

# PCI device 0x14e4:0x170c (b44)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:1c:23:a0:49:22", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

```

---

### Post by praseodym on 2011-09-27
Strange, remove the new file and reboot:

```
sudo rm /etc/udev/rules.d/70-persistent-net.rules
```
Check the file plus

```
lspci -nnk | grep -iA2 net
modinfo iwlagn | egrep '8086|4235'
```
If the device ID is not shown, install the newest driver:

```
sudo apt-get install --reinstall linux-headers-$(uname -r) build-essential 
wget http://linuxwireless.org/download/compat-wireless-2.6/compat-wireless-2.6.tar.bz2
```
Watch if it is downloaded 100 %, if not remove the file
```
rm -r compat-wireless-2.6.tar.bz2
```and try again. After that compile:```

tar jxvf compat-wireless-2.6.tar.bz2
cd compat-wireless-20*
make clean
make
sudo make install 
```
and newer firmware:
```
wget http://media.cdn.ubuntu-de.org/forum/attachments/2767012/Intel_Firmware.tar.gz
sudo tar xvf Intel_Firmware.tar.gz -C /lib/firmware
```
and reboot.

---

### Post by sysrpl on 2011-09-27
Okay, I was having an error with the make. There was an error

```
if_usb.c:1118: error: implicit declaration of function 'olpc_ec_wakeup_clear'
```

I ran this script and reran make then sudo make install:

```
./scripts/driver-select iwlagn
```

After that the firmware command and finally reboot. Still no wireless. 

I re-ran:

```
sudo mv /etc/udev/rules.d/70-persistent-net.rules /etc/udev/rules.d/70-persistent-net.bak
sudo udevadm trigger
sudo service udev reload
```

And reboot. This is what I am getting:

```
user@machine:~$ lspci -nnk | grep -iA2 net
03:00.0 Ethernet controller [0200]: Broadcom Corporation BCM4401-B0 100Base-TX [14e4:170c] (rev 02)
	Subsystem: Dell Device [1028:0228]
	Kernel driver in use: b44
--
0c:00.0 Network controller [0280]: Intel Corporation Ultimate N WiFi Link 5300 [8086:4235]
	Subsystem: Intel Corporation Device [8086:1001]
	Kernel modules: iwlagn

user@machine:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

user@machine:~$ lsmod
Module                  Size  Used by
parport_pc             26058  0 
ppdev                   5556  0 
joydev                  8767  0 
binfmt_misc             6599  1 
nvidia              10382361  44 
snd_hda_codec_idt      54951  1 
snd_hda_intel          22235  2 
snd_hda_codec          87552  2 snd_hda_codec_idt,snd_hda_intel
snd_hwdep               5040  1 snd_hda_codec
snd_pcm                71475  2 snd_hda_intel,snd_hda_codec
snd_seq_midi            4588  0 
snd_rawmidi            17783  1 snd_seq_midi
snd_seq_midi_event      6047  1 snd_seq_midi
snd_seq                47174  2 snd_seq_midi,snd_seq_midi_event
iwlagn                225008  0 
mac80211              270653  1 iwlagn
snd_timer              19067  2 snd_pcm,snd_seq
snd_seq_device          5744  3 snd_seq_midi,snd_rawmidi,snd_seq
r852                    9536  0 
dell_wmi                2852  0 
sm_common               3285  1 r852
nand                   34905  2 r852,sm_common
nand_ids                2903  1 nand
nand_ecc                3938  1 nand
dell_laptop             5730  0 
snd                    49102  13 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
video                  18712  0 
mtd                    18877  2 sm_common,nand
psmouse                59033  0 
output                  1883  1 video
intel_agp              26566  0 
dcdbas                  5402  1 dell_laptop
cfg80211              162382  2 iwlagn,mac80211
serio_raw               4022  0 
compat                 20020  3 iwlagn,mac80211,cfg80211
soundcore                880  1 snd
snd_page_alloc          7120  2 snd_hda_intel,snd_pcm
agpgart                32011  2 nvidia,intel_agp
lp                      7342  0 
parport                31492  3 parport_pc,ppdev,lp
b44                    26253  0 
firewire_ohci          21234  0 
sdhci_pci               6633  0 
sdhci                  15922  1 sdhci_pci
ssb                    39320  1 b44
firewire_core          46643  1 firewire_ohci
ahci                   19326  2 
led_class               2633  3 iwlagn,compat,sdhci
crc_itu_t               1383  1 firewire_core
mii                     4425  1 b44
libahci                21728  1 ahci
user@machine:~$ rfkill list
0: dell-wifi: Wireless LAN
	Soft blocked: no
	Hard blocked: no

user@machine:~$ cat /etc/udev/rules.d/70-persistent-net.rules
# This file was automatically generated by the /lib/udev/write_net_rules
# program, run by the persistent-net-generator.rules rules file.
#
# You can modify it, as long as you keep each rule on a single
# line, and change only the value of the NAME= key.

# PCI device 0x14e4:0x170c (b44)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:1c:23:a0:49:22", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
```

---

### Post by sysrpl on 2011-09-27
I think I may have found my problem. The wireless isn't working, but at least I have an idea why.

When I do:

```
dmesg | grep iwl
```

I get the in the text a one point this message:

```
Unsupported (too old) EEPROM VER=0x114 < 0x11a CALIB=0x3 < 0x4
```

Other people discuss this problem here:

[http://bugzilla.intellinuxwireless.org/show_bug.cgi?id=1997](http://bugzilla.intellinuxwireless.org/show_bug.cgi?id=1997)

---

