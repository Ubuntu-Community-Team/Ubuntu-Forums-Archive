---
title: "Unable to activate PCI wireless card"
date: 2011-11-21
forum: Networking &amp; Wireless
---

### Post by chip35pdx on 2011-11-21
I'm having a terrible time with my PCI wireless receiver. Its status says "inactive" and I can't seem to enable it so it will recognize the router in my house. How do I re-enable it? Thanks....

---

### Post by aha2095 on 2011-11-21
Same, I'm on 11.10 and I'm a real noob to ubuntu the wireless card I'm using is an edimax ew 7722in.

---

### Post by chip35pdx on 2011-11-21
Mine is an on-board Intel ethernet wireless PCI receiver but I don't know the model number.

---

### Post by aha2095 on 2011-11-22
Can anyone help us?

---

### Post by praseodym on 2011-11-22
Please show the outputs of

```
lspci -nnk | grep -iA2 net
lsmod
rfkill list
iwconfig
```

---

### Post by aha2095 on 2011-11-22
```
alec@ubuntu:~$ lspci -nnk | grep -iA2 net
00:14.0 Bridge [0680]: nVidia Corporation MCP51 Ethernet Controller [10de:0269] (rev a3)
	Subsystem: ASUSTeK Computer Inc. Device [1043:8221]
	Kernel driver in use: forcedeth
--
04:07.0 Network controller [0280]: Ralink corp. Device [1814:3062]
	Subsystem: Edimax Computer Co. Device [1432:7722]
	Kernel driver in use: rt2800pci
alec@ubuntu:~$ lsmod
Module                  Size  Used by
nls_iso8859_1          12713  1 
nls_utf8               12557  1 
nls_cp437              16991  1 
vfat                   17585  1 
fat                    61475  1 vfat
isofs                  40253  1 
lp                     17799  0 
rfcomm                 47946  0 
bnep                   18436  2 
bluetooth             166112  10 rfcomm,bnep
binfmt_misc            17540  1 
snd_hda_codec_realtek   330769  1 
ppdev                  17113  0 
joydev                 17693  0 
snd_hda_intel          33390  2 
snd_hda_codec         104802  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
snd_pcm                96755  2 snd_hda_intel,snd_hda_codec
arc4                   12529  2 
snd_seq_midi           13324  0 
snd_rawmidi            30547  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29991  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
rt2800pci              18715  0 
rt2800lib              54306  1 rt2800pci
crc_ccitt              12667  1 rt2800lib
rt2x00pci              14578  1 rt2800pci
rt2x00lib              50325  3 rt2800pci,rt2800lib,rt2x00pci
snd                    68266  13 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
mac80211              310872  3 rt2800lib,rt2x00pci,rt2x00lib
cfg80211              199587  2 rt2x00lib,mac80211
eeprom_93cx6           12725  1 rt2800pci
nouveau               728662  3 
ttm                    76805  1 nouveau
drm_kms_helper         42558  1 nouveau
soundcore              12680  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
drm                   236330  5 nouveau,ttm,drm_kms_helper
psmouse                73882  0 
i2c_algo_bit           13423  1 nouveau
mxm_wmi                12979  1 nouveau
wmi                    19256  1 mxm_wmi
video                  19412  1 nouveau
serio_raw              13166  0 
parport_pc             36962  1 
nv_tco                 13687  0 
parport                46562  3 lp,ppdev,parport_pc
i2c_nforce2            13058  0 
asus_atk0110           18078  0 
hid_microsoft          12848  0 
firewire_ohci          40722  0 
firewire_core          63626  1 firewire_ohci
usbhid                 47198  0 
hid                    95463  2 hid_microsoft,usbhid
usb_storage            57901  2 
uas                    18027  0 
crc_itu_t              12707  1 firewire_core
forcedeth              67563  0 
pata_amd               14121  0 
sata_nv                32305  1 
ahci                   26002  0 
libahci                26861  1 ahci
floppy                 70365  0 
alec@ubuntu:~$ rfkill list
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
alec@ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
```

---

### Post by praseodym on 2011-11-22
Install this driver by cable connection:

```
sudo apt-get install linux-headers-$(uname -r) build-essential 
wget http://media.cdn.ubuntu-de.org/forum/attachments/2739482/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217_prepared.tar.gz
tar xvf DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217_prepared.tar.gz
cd DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217_prepared
sudo make
sudo make install 
echo "blacklist rt2800pci" | sudo tee -a /etc/modprobe.d/blacklist.conf 
```
and reboot. Check:

```
uname -a
iwconfig
rfkill list
iwlist chan
sudo iwlist scan
dmesg | grep rt3
lsmod
```

---

### Post by aha2095 on 2011-11-23
```

alec@ubuntu:~$ uname -a
Linux ubuntu 3.0.0-12-generic #20-Ubuntu SMP Fri Oct 7 14:56:25 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux
alec@ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

ra0       Ralink STA  
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0


alec@ubuntu:~$ rfkill list
alec@ubuntu:~$ iwlist chan
lo        no frequency information.

eth0      no frequency information.

ra0       no frequency information.

alec@ubuntu:~$ iwlist chan
lo        no frequency information.

eth0      no frequency information.

ra0       no frequency information.

alec@ubuntu:~$ ddsudo iwlist scan
[sudo] password for alec: 
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

ra0       Interface doesn't support scanning.



alec@ubuntu:~$ dmesg | grep rt3
[   19.045765] rt3562sta: module license 'unspecified' taints kernel.
alec@ubuntu:~$ lsmod
Module                  Size  Used by
nls_iso8859_1          12713  1 
nls_cp437              16991  1 
vfat                   17585  1 
fat                    61475  1 vfat
nls_utf8               12557  1 
isofs                  40253  1 
lp                     17799  0 
bnep                   18436  2 
rfcomm                 47946  0 
bluetooth             166112  10 bnep,rfcomm
binfmt_misc            17540  1 
snd_hda_codec_realtek   330769  1 
ppdev                  17113  0 
rt3562sta             906415  0 
snd_hda_intel          33390  2 
snd_hda_codec         104802  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
snd_pcm                96755  2 snd_hda_intel,snd_hda_codec
joydev                 17693  0 
snd_seq_midi           13324  0 
snd_rawmidi            30547  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29991  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    68266  13 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse                73882  0 
serio_raw              13166  0 
soundcore              12680  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
parport_pc             36962  1 
parport                46562  3 lp,ppdev,parport_pc
nouveau               728662  3 
ttm                    76805  1 nouveau
drm_kms_helper         42558  1 nouveau
nv_tco                 13687  0 
i2c_nforce2            13058  0 
drm                   236330  5 nouveau,ttm,drm_kms_helper
asus_atk0110           18078  0 
i2c_algo_bit           13423  1 nouveau
mxm_wmi                12979  1 nouveau
wmi                    19256  1 mxm_wmi
video                  19412  1 nouveau
hid_microsoft          12848  0 
firewire_ohci          40722  0 
firewire_core          63626  1 firewire_ohci
usbhid                 47198  0 
hid                    95463  2 hid_microsoft,usbhid
usb_storage            57901  2 
uas                    18027  0 
forcedeth              67563  0 
crc_itu_t              12707  1 firewire_core
sata_nv                32305  1 
pata_amd               14121  0 
ahci                   26002  0 
libahci                26861  1 ahci
floppy                 70365  0 


```

---

### Post by praseodym on 2011-11-23
Remove (not edit) your wireless profile in the network-manager applet and create a new one. Check then
```
iwconfig
dmesg | egrep 'rt2|rt3'
sudo iwlist scan
cat /var/lib/NetworkManager/NetworkManager.state
cat /etc/udev/rules.d/70-persistent-net.rules
```

---

### Post by aha2095 on 2011-11-24
I'd just like to say thanks whether or not it works, also some of the options that are usually there have disappeared i.e. on the network drop down; I can take a screen shot if you want.

```

alec@ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

ra0       Ralink STA  
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0

alec@ubuntu:~$ dmesg| egrep 'rt2 | rt3'
[   18.821120] rt3562sta: module license 'unspecified' taints kernel.
alec@ubuntu:~$ cat /var/libcat /var/lib/NetworkManager/NetworkManager.state
alec@ubuntu:~$ sudo iwlist scan
[sudo] password for alec: 
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

ra0       Interface doesn't support scanning.


cat: /var/libcat: No such file or directory

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true
alec@ubuntu:~$ cat /etc/udev/rules.d/70-persistent-net.rules
# This file was automatically generated by the /lib/udev/write_net_rules
# program, run by the persistent-net-generator.rules rules file.
#
# You can modify it, as long as you keep each rule on a single
# line, and change only the value of the NAME= key.

# PCI device 0x10de:0x0269 (forcedeth)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:1f:c6:8c:f7:46", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x1814:0x3062 (rt2800pci)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="80:1f:02:0f:75:d4", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

```

---

### Post by praseodym on 2011-11-24
Check with

```
ifconfig -a
```
and adjust the line from "wlan0" to "ra0" in /etc/udev/rules.d/70-persistent-net.rules, dont forget the Hardware address. Or try:

```
sudo cp /etc/udev/rules.d/70-persistent-net.rules /etc/udev/rules.d/70-persistent-net.bak
sudo udevadm trigger
sudo service udev reload
```
or reboot

---

