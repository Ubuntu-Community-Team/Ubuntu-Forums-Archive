---
title: "Wireless will not connect (12.04LTS Acer Aspire V3-571G)"
date: 2013-05-13
forum: Networking &amp; Wireless
---

### Post by aesoptheterrific on 2013-05-13
Hey there.

I recently have decided to migrate over to linux, and I set up a dual boot (from clean installs) of windows 7 and ubuntu 12.04LTS. I am on an Acer Aspire V3-571G. I am able to connect to the internet through a wired connection, but I have been unable to connect to multiple wireless sources as various locations. Specifically, I am able to see a multitude of wireless sources, but I cannot ever connect to them. If anyone has any ideas, I'd be thrilled. My internet searches haven't been that helpful thusfar.

My current wireless source has a WPA encryption key. I don't know if that helps anything.

Thanks

---

### Post by Hadaka on 2013-05-13
Hi, please post the output of..
```
lspci -nn | grep 0280
lsmod
rfkill list all
```
thanks

---

### Post by aesoptheterrific on 2013-05-13
Aspire-V3-571G:~$ lspci -nn 
00:00.0 Host bridge [0600]: Intel Corporation 2nd Generation Core Processor Family DRAM Controller [8086:0104] (rev 09)
00:01.0 PCI bridge [0604]: Intel Corporation Xeon E3-1200/2nd Generation Core Processor Family PCI Express Root Port [8086:0101] (rev 09)
00:02.0 VGA compatible controller [0300]: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller [8086:0126] (rev 09)
00:14.0 USB controller [0c03]: Intel Corporation Panther Point USB xHCI Host Controller [8086:1e31] (rev 04)
00:16.0 Communication controller [0780]: Intel Corporation Panther Point MEI Controller #1 [8086:1e3a] (rev 04)
00:1a.0 USB controller [0c03]: Intel Corporation Panther Point USB Enhanced Host Controller #2 [8086:1e2d] (rev 04)
00:1b.0 Audio device [0403]: Intel Corporation Panther Point High Definition Audio Controller [8086:1e20] (rev 04)
00:1c.0 PCI bridge [0604]: Intel Corporation Panther Point PCI Express Root Port 1 [8086:1e10] (rev c4)
00:1c.1 PCI bridge [0604]: Intel Corporation Panther Point PCI Express Root Port 2 [8086:1e12] (rev c4)
00:1d.0 USB controller [0c03]: Intel Corporation Panther Point USB Enhanced Host Controller #1 [8086:1e26] (rev 04)
00:1f.0 ISA bridge [0601]: Intel Corporation Panther Point LPC Controller [8086:1e57] (rev 04)
00:1f.2 SATA controller [0106]: Intel Corporation Panther Point 6 port SATA Controller [AHCI mode] [8086:1e03] (rev 04)
00:1f.3 SMBus [0c05]: Intel Corporation Panther Point SMBus Controller [8086:1e22] (rev 04)
01:00.0 VGA compatible controller [0300]: NVIDIA Corporation Device [10de:0de9] (rev a1)
02:00.0 Ethernet controller [0200]: Broadcom Corporation NetLink BCM57785 Gigabit Ethernet PCIe [14e4:16b5] (rev 10)
02:00.1 SD Host controller [0805]: Broadcom Corporation NetXtreme BCM57765 Memory Card Reader [14e4:16bc] (rev 10)
02:00.2 System peripheral [0880]: Broadcom Corporation Device [14e4:16be] (rev 10)
02:00.3 System peripheral [0880]: Broadcom Corporation Device [14e4:16bf] (rev 10)
03:00.0 Network controller [0280]: Atheros Communications Inc. AR9462 Wireless Network Adapter [168c:0034] (rev 01)
Aspire-V3-571G:~$ lspci --nn | grep 0280
lspci: invalid option -- '-'
Usage: lspci [<switches>]

Basic display modes:
-mm        Produce machine-readable output (single -m for an obsolete format)
-t        Show bus tree

Display options:
-v        Be verbose (-vv for very verbose)
-k        Show kernel drivers handling each device
-x        Show hex-dump of the standard part of the config space
-xxx        Show hex-dump of the whole config space (dangerous; root only)
-xxxx        Show hex-dump of the 4096-byte extended config space (root only)
-b        Bus-centric view (addresses and IRQ's as seen by the bus)
-D        Always show domain numbers

Resolving of device ID's to names:
-n        Show numeric ID's
-nn        Show both textual and numeric ID's (names & numbers)
-q        Query the PCI ID database for unknown ID's via DNS
-qq        As above, but re-query locally cached entries
-Q        Query the PCI ID database for all ID's via DNS

Selection of devices:
-s [[[[<domain>]:]<bus>]:][<slot>][.[<func>]]    Show only devices in selected slots
-d [<vendor>]:[<device>]            Show only devices with specified ID's

Other options:
-i <file>    Use specified ID database instead of /usr/share/misc/pci.ids.gz
-p <file>    Look up kernel modules in a given file instead of default modules.pcimap
-M        Enable `bus mapping' mode (dangerous; root only)

PCI access options:
-A <method>    Use the specified PCI access method (see `-A help' for a list)
-O <par>=<val>    Set PCI access parameter (see `-O help' for a list)
-G        Enable PCI access debugging
-H <mode>    Use direct hardware access (<mode> = 1 or 2)
-F <file>    Read PCI configuration dump from a given file
Aspire-V3-571G:~$ lsmod
Module                  Size  Used by
parport_pc             32867  0 
ppdev                  17114  0 
rfcomm                 47562  12 
bnep                   18240  2 
dm_crypt               23126  0 
snd_hda_codec_hdmi     32476  1 
snd_hda_codec_realtek    79855  1 
coretemp               13642  0 
kvm_intel             137888  0 
kvm                   422160  1 kvm_intel
nvidia              11309216  0 
arc4                   12530  2 
snd_hda_intel          34063  5 
snd_hda_codec         135141  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              17765  1 snd_hda_codec
microcode              23030  0 
snd_pcm                97523  4 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13325  0 
snd_rawmidi            30750  1 snd_seq_midi
ath9k                 133095  0 
mac80211              555272  1 ath9k
snd_seq_midi_event     14900  1 snd_seq_midi
ath9k_common           14054  1 ath9k
ath9k_hw              399752  2 ath9k,ath9k_common
ath                    24124  3 ath9k,ath9k_common,ath9k_hw
psmouse               102075  0 
cfg80211              208382  3 ath9k,mac80211,ath
serio_raw              13216  0 
snd_seq                61931  2 snd_seq_midi,snd_seq_midi_event
uvcvideo               78117  0 
videobuf2_core         33025  1 uvcvideo
videodev              125126  2 uvcvideo,videobuf2_core
videobuf2_vmalloc      12861  1 uvcvideo
videobuf2_memops       13405  1 videobuf2_vmalloc
lpc_ich                17145  0 
snd_timer              29990  2 snd_pcm,snd_seq
snd_seq_device         14498  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    83674  19 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
btusb                  22432  0 
bluetooth             211812  24 rfcomm,bnep,btusb
soundcore              15092  1 snd
snd_page_alloc         18573  2 snd_hda_intel,snd_pcm
joydev                 17694  0 
mei                    41410  0 
acer_wmi               32845  0 
sparse_keymap          13891  1 acer_wmi
wmi                    19257  1 acer_wmi
mac_hid                13254  0 
lp                     17800  0 
parport                46563  3 parport_pc,ppdev,lp
ghash_clmulni_intel    13221  0 
aesni_intel            51134  548 
cryptd                 20531  2 ghash_clmulni_intel,aesni_intel
aes_x86_64             17256  1 aesni_intel
i915                  530851  2 
drm_kms_helper         49259  1 i915
drm                   290344  3 i915,drm_kms_helper
i2c_algo_bit           13565  1 i915
ahci                   25869  3 
libahci                27338  1 ahci
tg3                   156646  0 
sdhci_pci              18749  0 
sdhci                  33145  1 sdhci_pci
video                  19653  2 acer_wmi,i915
Aspire-V3-571G:~$ rfkill list all
0: acer-wireless: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: acer-bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
2: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
3: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

---

### Post by Hadaka on 2013-05-13
Hi ,give this a try..
COPY and paste one line at a time...
```
echo "blacklist acer_wmi" | sudo tee -a /etc/modprobe.d/blacklist.conf
sudo modprobe -rfv ath9k
sudo modprobe ath9k nohwcrypt=1
```

if that helps without booting..then do..

```
sudo gedit /etc/modprobe.d/ath9k.conf
```
and add this one line..
```
options ath9k nohwcrypt=1
```
SAVE and close gedit.
boot and see if that helps.
thanks.

---

### Post by aesoptheterrific on 2013-05-13
Will try it now and will update this post with results.

EDIT

Yeah I tried it twice, and neither time it worked. I went through the command sudo modprobe ath9k nohwcrypt=1

---

### Post by Hadaka on 2013-05-13
Hi, please post the output of...

```
cat /etc/modprobe.d/blacklist.conf
cat /etc/modules
```
thanks.

---

### Post by aesoptheterrific on 2013-05-13
Aspire-V3-571G:~$ cat /etc/modprobe.d/blacklist.conf
# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# Conflicts with dvb driver (which is better for handling this device)
blacklist snd_aw2

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801

# replaced by p54pci
blacklist prism54

# replaced by b43 and ssb.
blacklist bcm43xx

# most apps now use garmin usb driver directly (Ubuntu: #114565)
blacklist garmin_gps

# replaced by asus-laptop (Ubuntu: #184721)
blacklist asus_acpi

# low-quality, just noise when being used for sound playback, causes
# hangs at desktop session start (Ubuntu: #246969)
blacklist snd_pcsp

# ugly and loud noise, getting on everyone's nerves; this should be done by a
# nice pulseaudio bing (Ubuntu: #77010)
blacklist pcspkr

# EDAC driver for amd76x clashes with the agp driver preventing the aperture
# from being initialised (Ubuntu: #297750). Blacklist so that the driver
# continues to build and is installable for the few cases where its
# really needed.
blacklist amd76x_edac
blacklister acer_wmi
blacklist acer_wmi
blacklist acer_wmi
Aspire-V3-571G:~$ cat /etc/modules
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
rtc

---

### Post by Hadaka on 2013-05-13
Hi, looks like you have an unknown module in /etc/modules
and a typo in /etc/modprobe.d/blacklist.conf.
Please open gedit and edit these 2 files..
```
sudo gedit /etc/modules
```
remove    rtc       
```
sudo gedit /etc/modprobe.d/blacklist.conf
```
remove blacklister acer_wmi and the extra blacklist acer_wmi
so you only have one entry of that.
save and close gedit
boot and see if that helps.

---

### Post by aesoptheterrific on 2013-05-13
I fixed those errors, to no avail.

---

### Post by Hadaka on 2013-05-13
OK, please do a hard boot, as in power off then
back on. Try to connect with wireless, if it does not
then please do ...
```
dmesg | grep ath9k
ifconfig
```
copy and paste back the results
thanks.

---

### Post by aesoptheterrific on 2013-05-13
Aspire-V3-571G:~$ dmesg | grep ath9k
[   18.874218] ieee80211 phy0: Selected rate control algorithm 'ath9k_rate_control'
[   18.874490] Registered led device: ath9k-phy0
Aspire-V3-571G:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr b8:88:e3:04:ea:1b  
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
          RX bytes:1312 (1.3 KB)  TX bytes:1312 (1.3 KB)

wlan0     Link encap:Ethernet  HWaddr 08:ed:b9:3e:4e:11  
          inet6 addr: fe80::aed:b9ff:fe3e:4e11/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:27 errors:0 dropped:0 overruns:0 frame:0
          TX packets:25 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4414 (4.4 KB)  TX bytes:5898 (5.8 KB)

---

### Post by Hadaka on 2013-05-13
ok, not much in the dmesg..lets look at
```
iwconfig
```
and 
```
iwlist wlan0 scan
```
post the output
also, have you tried unplugging the wired connection
and connecting the wifi?

---

### Post by aesoptheterrific on 2013-05-14
I've had the wired out for most of the tests. That doesn't change things. Thanks for sticking with it and helping me. Hopefully we can figure it out. Note that all smileys are :_o without the underscore.

Aspire-V3-571G:~$ iwconfig
eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:"edited out wifi"  
          Mode:Managed  Frequency:2.417 GHz  Access Point: 00:24:B2:61:18:B5   
          Bit Rate=130 Mb/s   Tx-Power=27 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-34 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:135  Invalid misc:73   Missed beacon:0

Aspire-V3-571G:~$ iwlist wlan0 scan
wlan0     Scan completed :
          Cell 01 - Address: 00:24:B2:61:18:B5
                    Channel:2
                    Frequency:2.417 GHz (Channel 2)
                    Quality=70/70  Signal level=-36 dBm  
                    Encryption key:on
                    ESSID:"edited out wifi"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000001fa2a2180
                    Extra: Last beacon: 81260ms ago
                    IE: Unknown: 000C6772696D6C65792077696669
                    IE: Unknown: 010882848B0C12961824
                    IE: Unknown: 030102
                    IE: Unknown: 0706555320010B1B
                    IE: Unknown: 200100
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2A0103
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F2020101020003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C334C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 2D1A4C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3402001B00000000000000000000000000000000000000
                    IE: Unknown: 3D1602001B00000000000000000000000000000000000000
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD0A00037F04010000000000
                    IE: Unknown: DD820050F204104A000110104400010210570001001041000100103B00010310470010565AA94967C14C0EAA8FF349E6F593111021000D4E6574676561722C20496E632E10230007574E523230303010240007574E523230303010420004353637381054000800060050F204000110110007574E5232303030100800020084103C000103

---

### Post by Hadaka on 2013-05-14
Hi, you are getting a good strong signal from the
router and the driver is correct, the only thing i can
think of is to change the encryption from TKIP
to just wpa/wpa2 or just wpa2 but unload the TKIP
tripple check your wifi card settings in netork mgr
and at the router to make sure they match...
post back how that goes.
thanks.

---

### Post by chili555 on 2013-05-14
I suggest the following:

* Change the router encryption method from TKIP to AES (sometimes known as CCMP);

* Change the router setting to B and G mode only and not B, G and N:> wlan0 IEEE 802.11abgn ESSID:"edited out wifi"
Mode:Managed Frequency:2.417 GHz Access Point: 00:24:B2:61:18:B5
[COLOR="#FF0000"]Bit Rate=130 Mb/s[/COLOR] Tx-Power=27 dBm 

* Please do:```
sudo gedit /etc/modprobe.d/ath9k.conf
```Change the file within to:```
[COLOR="#FF0000"]#[/COLOR]options ath9k nohwcrypt=1
```In other words, temporarily comment it out. Proofread, save and close gedit. Reboot. Can you connect? If not, change the ath9k.conf file back and reboot. Now can you connect?

* Please show us:```
dmesg | grep -e ath -e 80211
```Thanks.

---

### Post by aesoptheterrific on 2013-05-14
The issue is now fixed. Thanks everyone for your help.

My family actually had a new router that they wanted installed (one with multiple frequencies). I installed it and made sure to use WPA2 AES rather than TKIP. That seems to have fixed the issue.

Thanks again everyone! This thread can now be changed to solved (I don't know how though!).

---

### Post by chili555 on 2013-05-14
Awesome. Glad it's working.

[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

