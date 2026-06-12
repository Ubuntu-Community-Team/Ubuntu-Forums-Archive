---
title: "How to Configure: Network controller: Ralink corp. Device 3592.. in Ubuntu 11.04"
date: 2011-10-03
forum: Networking &amp; Wireless
---

### Post by mavericck on 2011-10-03
I have Network controller: Ralink corp. Device 3592 as my wireless card. But it does not work. Please help!

---

### Post by mavericck on 2011-10-03
I have Network controller: Ralink corp. Device 3592 as my wireless card. But it does not work. Please help!

---

### Post by praseodym on 2011-10-03
Hello,

please show the terminal outputs of:

```
lspci -nnk | grep -iA2 net
iwconfig
rfkill list
lsmod
```

---

### Post by mavericck on 2011-10-03
lspci -nnk | grep -iA2 net

24:00.0 Network controller [0280]: Ralink corp. Device [1814:3592]
    Subsystem: Hewlett-Packard Company Device [103c:1638]
    Kernel modules: rt2800pci
25:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd.  RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev  06)
    Subsystem: Hewlett-Packard Company Device [103c:167d]
    Kernel driver in use: r8169

iwconfig

Command 'iwconfig' is available in '/sbin/iwconfig'
The command could not be located because '/sbin' is not included in the PATH environment variable.
This is most likely caused by the lack of administrative privileges associated with your user account.
iwconfig: command not found


rfkill list

The command could not be located because '/sbin:/usr/sbin' is not included in the PATH environment variable.
This is most likely caused by the lack of administrative privileges associated with your user account.
rfkill: command not found


lsmod

Module                  Size  Used by
ppp_deflate            12990  0 
zlib_deflate           27074  1 ppp_deflate
bsd_comp               12913  0 
ppp_async              17540  1 
crc_ccitt              12667  1 ppp_async
option                 25285  2 
usb_wwan               20407  1 option
usbserial              42908  7 option,usb_wwan
usb_storage            53538  0 
uas                    17996  0 
binfmt_misc            17565  1 
parport_pc             36959  0 
ppdev                  17113  0 
snd_hda_codec_hdmi     28167  1 
snd_hda_codec_idt      71137  1 
joydev                 17606  0 
i915                  515121  3 
snd_hda_intel          33176  2 
snd_hda_codec         103768  3 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel
drm_kms_helper         42136  1 i915
snd_hwdep              13604  1 snd_hda_codec
uvcvideo               68099  0 
snd_pcm                96297  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
videodev               82052  1 uvcvideo
snd_seq_midi           13324  0 
drm                   227498  4 i915,drm_kms_helper
snd_rawmidi            30386  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
v4l2_compat_ioctl32    17042  1 videodev
snd_seq                61585  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29602  2 snd_pcm,snd_seq
i2c_algo_bit           13400  1 i915
snd_seq_device         14462  3 snd_seq_midi,snd_rawmidi,snd_seq
hp_accel               21880  0 
hp_wmi                 13706  0 
psmouse                73535  0 
lis3lv02d              19893  1 hp_accel
lp                     17789  0 
serio_raw              13166  0 
input_polldev          14007  1 lis3lv02d
video                  19438  1 i915
sparse_keymap          13898  1 hp_wmi
jmb38x_ms              17596  0 
memstick               16520  1 jmb38x_ms
parport                46458  3 parport_pc,ppdev,lp
snd                    67346  14 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              12680  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
ahci                   25951  4 
libahci                26642  1 ahci
xhci_hcd               77643  0 
r8169                  48022  0 
sdhci_pci              13989  0 
sdhci                  27387  1 sdhci_pci

---

### Post by praseodym on 2011-10-03
The driver is shown but not "in use". Load it by hand:

```
sudo modprobe -v rt2800pci
sudo depmod -a
sudo update-initramfs -u
```
You should install the package **wireless-tools** and check

```
iwconfig
lsmod
sudo iwlist scan
rfkill list
```

---

### Post by mavericck on 2011-10-03
The wireless-tools package is already installed. The following messages are shown when i run the commands as u mentioned above:-
sysadmin@eobi-notebook:~$ iwconfig
Command 'iwconfig' is available in '/sbin/iwconfig'
The command could not be located because '/sbin' is not included in the PATH environment variable.
This is most likely caused by the lack of administrative privileges associated with your user account.
iwconfig: command not found
sysadmin@eobi-notebook:~$ lsmod
Module                  Size  Used by
arc4                   12529  2 
rt2800pci              18487  0 
rt2800lib              49467  1 rt2800pci
rt2x00pci              14263  1 rt2800pci
rt2x00lib              48766  3 rt2800pci,rt2800lib,rt2x00pci
mac80211              296672  3 rt2800lib,rt2x00pci,rt2x00lib
cfg80211              181865  2 rt2x00lib,mac80211
eeprom_93cx6           12725  1 rt2800pci
ppp_deflate            12990  0 
zlib_deflate           27074  1 ppp_deflate
bsd_comp               12913  0 
ppp_async              17540  1 
crc_ccitt              12667  2 rt2800lib,ppp_async
option                 25285  2 
usb_wwan               20407  1 option
usbserial              42908  7 option,usb_wwan
usb_storage            53538  0 
uas                    17996  0 
binfmt_misc            17565  1 
parport_pc             36959  0 
ppdev                  17113  0 
snd_hda_codec_hdmi     28167  1 
snd_hda_codec_idt      71137  1 
joydev                 17606  0 
snd_hda_intel          33176  2 
i915                  515121  3 
uvcvideo               68099  0 
videodev               82052  1 uvcvideo
drm_kms_helper         42136  1 i915
snd_hda_codec         103768  3 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13604  1 snd_hda_codec
v4l2_compat_ioctl32    17042  1 videodev
drm                   227498  4 i915,drm_kms_helper
hp_accel               21880  0 
snd_pcm                96297  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
lis3lv02d              19893  1 hp_accel
lp                     17789  0 
i2c_algo_bit           13400  1 i915
snd_seq_midi           13324  0 
hp_wmi                 13706  0 
snd_rawmidi            30386  1 snd_seq_midi
psmouse                73535  0 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61585  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29602  2 snd_pcm,snd_seq
snd_seq_device         14462  3 snd_seq_midi,snd_rawmidi,snd_seq
parport                46458  3 parport_pc,ppdev,lp
video                  19438  1 i915
input_polldev          14007  1 lis3lv02d
sparse_keymap          13898  1 hp_wmi
jmb38x_ms              17596  0 
serio_raw              13166  0 
memstick               16520  1 jmb38x_ms
snd                    67346  14 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              12680  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
ahci                   25951  4 
libahci                26642  1 ahci
r8169                  48022  0 
xhci_hcd               77643  0 
sdhci_pci              13989  0 
sdhci                  27387  1 sdhci_pci
sysadmin@eobi-notebook:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth1      Interface doesn't support scanning.

ppp0      Interface doesn't support scanning.

wlan0     Interface doesn't support scanning : Network is down

sysadmin@eobi-notebook:~$ rfkill list
Command 'rfkill' is available in the following places
 * /sbin/rfkill
 * /usr/sbin/rfkill
The command could not be located because '/sbin:/usr/sbin' is not included in the PATH environment variable.
This is most likely caused by the lack of administrative privileges associated with your user account.
rfkill: command not found

---

### Post by praseodym on 2011-10-04
You need to install the packages **wireless-tools** and **rfkill** then post

```
iwconfig
rfkill list
```

again

---

### Post by mavericck on 2011-10-04
iwconfig
Command 'iwconfig' is available in '/sbin/iwconfig'
The command could not be located because '/sbin' is not included in the PATH environment variable.
This is most likely caused by the lack of administrative privileges associated with your user account.
iwconfig: command not found



rfkill list
Command 'rfkill' is available in the following places
 * /sbin/rfkill
 * /usr/sbin/rfkill
The command could not be located because '/sbin:/usr/sbin' is not included in the PATH environment variable.
This is most likely caused by the lack of administrative privileges associated with your user account.
rfkill: command not found

---

### Post by praseodym on 2011-10-04
Then try:

```
/sbin/rfkill
/usr/sbin/rfkill
```

---

### Post by mavericck on 2011-10-04
/sbin/rfkill
Usage:	/sbin/rfkill [options] command
Options:
	--version	show version (0.4)
Commands:
	help
	event
	list [IDENTIFIER]
	block IDENTIFIER
	unblock IDENTIFIER
where IDENTIFIER is the index no. of an rfkill switch or one of:
	<idx> all wifi wlan bluetooth uwb ultrawideband wimax wwan gps fm


/usr/sbin/rfkill
Usage:	/usr/sbin/rfkill [options] command
Options:
	--version	show version (0.4-1 (Ubuntu))
Commands:
	help
	event
	list [IDENTIFIER]
	block IDENTIFIER
	unblock IDENTIFIER
where IDENTIFIER is the index no. of an rfkill switch or one of:
	<idx> all wifi wlan bluetooth uwb ultrawideband wimax wwan gps fm

Kindly Bear me as im Novice in Ubuntu....

---

### Post by praseodym on 2011-10-04
Sorry:

```
/sbin/rfkill list
/sbin/iwconfig
```

---

### Post by mavericck on 2011-10-04
sysadmin@eobi-notebook:~$ /sbin/iwconfig
lo        no wireless extensions.

eth1      no wireless extensions.

ppp0      no wireless extensions.

 Shows nothing with list command....

---

### Post by praseodym on 2011-10-04
Check with

```
modinfo rt2800pci | grep 3592
```

if the device ID is present in kernel 2.6.38. I found here

[http://wiki.debian.org/rt2800pci](http://wiki.debian.org/rt2800pci)

sth., that the ID is present from kernel 3.0.0-1. We'll see...

---

### Post by mavericck on 2011-10-05
/sbin/modinfo rt2800pci | grep 3592
alias:          pci:v00001814d00003592sv*sd*bc*sc*i*

---

### Post by mavericck on 2011-10-05
Still Not working please help......feeling frustrated....

---

### Post by praseodym on 2011-10-05
Please show

```
uname -a
dmesg >> dmesg.txt
```

and upload the dmesg.txt file

---

### Post by mavericck on 2011-10-05
Linux eobi-notebook 2.6.38-11-server #50-Ubuntu SMP Mon Sep 12 21:34:27 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux

Sorry i dont know how to upload text file? can i paste it here?

---

### Post by mavericck on 2011-10-05
> **mavericck said:**
> Linux eobi-notebook 2.6.38-11-server #50-Ubuntu SMP Mon Sep 12 21:34:27 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux

Sorry i dont know how to upload text file? can i paste it here?

got it....

---

### Post by mavericck on 2011-10-07
Still No Luck Please Help.....

---

### Post by mavericck on 2011-10-10
Where are all the networking gurus?????????

---

### Post by praseodym on 2011-10-10
Try to update the firmware via:

```
sudo apt-get install --reinstall linux-firmware
```
Maybe you directly use the Oneiric package:

```
wget http://de.archive.ubuntu.com/ubuntu/pool/main/l/linux-firmware/linux-firmware_1.60_all.deb
sudo dpkg -i linux-*.deb
```
and reboot.

Check:

```
iwconfig
dmesg | grep rt2
sudo iwlist scan
lsmod
```

---

### Post by mavericck on 2011-10-10
Here is the out put after the installation of package:- 

sysadmin@eobi-notebook:~$ /sbin/iwconfig
lo        no wireless extensions.

eth1      no wireless extensions.

ppp0      no wireless extensions.

sysadmin@eobi-notebook:~$ dmesg | grep rt2
sysadmin@eobi-notebook:~$ dmesg | grep rt2
sysadmin@eobi-notebook:~$ sudo iwlist scan
[sudo] password for sysadmin: 
lo        Interface doesn't support scanning.

eth1      Interface doesn't support scanning.

ppp0      Interface doesn't support scanning.

sysadmin@eobi-notebook:~$ lsmod
Module                  Size  Used by
ppp_deflate            12990  0 
zlib_deflate           27074  1 ppp_deflate
bsd_comp               12913  0 
ppp_async              17540  1 
crc_ccitt              12667  1 ppp_async
binfmt_misc            17565  1 
parport_pc             36959  0 
ppdev                  17113  0 
snd_hda_codec_hdmi     28167  1 
snd_hda_codec_idt      71137  1 
option                 25285  2 
usb_wwan               20407  1 option
snd_hda_intel          33176  2 
snd_hda_codec         103768  3 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13604  1 snd_hda_codec
snd_pcm                96297  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30386  1 snd_seq_midi
joydev                 17606  0 
hp_wmi                 13706  0 
sparse_keymap          13898  1 hp_wmi
snd_seq_midi_event     14899  1 snd_seq_midi
usbserial              42908  7 option,usb_wwan
snd_seq                61585  2 snd_seq_midi,snd_seq_midi_event
uvcvideo               68099  0 
videodev               82052  1 uvcvideo
v4l2_compat_ioctl32    17042  1 videodev
snd_timer              29602  2 snd_pcm,snd_seq
snd_seq_device         14462  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    67346  14 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
i915                  515121  3 
psmouse                73535  0 
serio_raw              13166  0 
jmb38x_ms              17596  0 
soundcore              12680  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
hp_accel               21880  0 
memstick               16520  1 jmb38x_ms
drm_kms_helper         42136  1 i915
lis3lv02d              19893  1 hp_accel
drm                   227498  4 i915,drm_kms_helper
i2c_algo_bit           13400  1 i915
input_polldev          14007  1 lis3lv02d
video                  19438  1 i915
lp                     17789  0 
parport                46458  3 parport_pc,ppdev,lp
usb_storage            53538  0 
uas                    17996  0 
ahci                   25951  4 
r8169                  48022  0 
libahci                26642  1 ahci
xhci_hcd               77643  0 
sdhci_pci              13989  0 
sdhci                  27387  1 sdhci_pci

---

### Post by praseodym on 2011-10-10
Ok, now there is no driver loaded. Check

```
grep rt28 /etc/modprobe.d/*
sudo modprobe -v rt2800pci
sudo service network-manager restart
dmesg | grep rt2
rfkill list
iwconfig
```

---

### Post by mavericck on 2011-10-10
/etc/modprobe.d/blacklist.conf:blacklist rt2800pci
/etc/modprobe.d/blacklist.conf:blacklist rt2800lib
/etc/modprobe.d/blacklist.conf:blacklist rt2800usb
/etc/modprobe.d/blacklist.conf:#blacklist rt2860
/etc/modprobe.d/blacklist.conf:#blacklist rt2860pci 
/etc/modprobe.d/blacklist-rt2800pci.conf:blacklist rt2800pci
sysadmin@eobi-notebook:~$ sudo modprobe -v rt2800pci
[sudo] password for sysadmin: 
insmod /lib/modules/2.6.38-11-server/updates/cw-2.6.39/eeprom_93cx6.ko 
insmod /lib/modules/2.6.38-11-server/updates/cw-2.6.39/cfg80211.ko 
insmod /lib/modules/2.6.38-11-server/updates/cw-2.6.39/mac80211.ko 
insmod /lib/modules/2.6.38-11-server/updates/cw-2.6.39/rt2x00lib.ko 
insmod /lib/modules/2.6.38-11-server/updates/cw-2.6.39/rt2x00pci.ko 
insmod /lib/modules/2.6.38-11-server/updates/cw-2.6.39/rt2800lib.ko 
insmod /lib/modules/2.6.38-11-server/updates/cw-2.6.39/rt2800pci.ko 
sysadmin@eobi-notebook:~$ sudo service network-manager restart
network-manager start/running, process 2889
sysadmin@eobi-notebook:~$ dmesg | grep rt2
[ 4321.312012] rt2800pci 0000:24:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[ 4321.312027] rt2800pci 0000:24:00.0: setting latency timer to 64
[ 4321.358754] Registered led device: rt2800pci-phy0::radio
[ 4321.358782] Registered led device: rt2800pci-phy0::assoc
[ 4321.358805] Registered led device: rt2800pci-phy0::quality
[ 4321.512030] phy0 -> rt2800pci_mcu_status: Error - MCU request failed, no response from hardware
sysadmin@eobi-notebook:~$ rfkill list
Command 'rfkill' is available in the following places
 * /sbin/rfkill
 * /usr/sbin/rfkill
The command could not be located because '/sbin:/usr/sbin' is not included in the PATH environment variable.
This is most likely caused by the lack of administrative privileges associated with your user account.
rfkill: command not found
sysadmin@eobi-notebook:~$ /sbin/rfkill
Usage:    /sbin/rfkill [options] command
Options:
    --version    show version (0.4)
Commands:
    help
    event
    list [IDENTIFIER]
    block IDENTIFIER
    unblock IDENTIFIER
where IDENTIFIER is the index no. of an rfkill switch or one of:
    <idx> all wifi wlan bluetooth uwb ultrawideband wimax wwan gps fm
sysadmin@eobi-notebook:~$ /usr/sbin/rfkill
Usage:    /usr/sbin/rfkill [options] command
Options:
    --version    show version (0.4-1 (Ubuntu))
Commands:
    help
    event
    list [IDENTIFIER]
    block IDENTIFIER
    unblock IDENTIFIER
where IDENTIFIER is the index no. of an rfkill switch or one of:
    <idx> all wifi wlan bluetooth uwb ultrawideband wimax wwan gps fm
sysadmin@eobi-notebook:~$ iwconfig
Command 'iwconfig' is available in '/sbin/iwconfig'
The command could not be located because '/sbin' is not included in the PATH environment variable.
This is most likely caused by the lack of administrative privileges associated with your user account.
iwconfig: command not found
sysadmin@eobi-notebook:~$ /sbin/iwconfig
lo        no wireless extensions.

eth1      no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off

---

### Post by praseodym on 2011-10-10
You should login to a "sudo" user:

> This is most likely caused by the lack of administrative privileges associated with your user account.
and try "rfkill list" again. BTW: The card is "off":

> wlan0 IEEE 802.11abgn ESSIDff/any
Mode:Managed Access Point: Not-Associated Tx-Power=[COLOR="Red"]off[/COLOR] 
Button/Switch/key combination? Try
```
sudo rfkill unblock all
```
If you are already the "sudo" user, checkbox all user rights in "Users&Groups" and login again.

---

### Post by skillew on 2011-10-10
> **mavericck said:**
> /etc/modprobe.d/blacklist.conf:blacklist rt2800pci
/etc/modprobe.d/blacklist.conf:blacklist rt2800lib
/etc/modprobe.d/blacklist.conf:blacklist rt2800usb
/etc/modprobe.d/blacklist.conf:#blacklist rt2860
/etc/modprobe.d/blacklist.conf:#blacklist rt2860pci 
/etc/modprobe.d/blacklist-rt2800pci.conf:blacklist rt2800pci
sysadmin@eobi-notebook:~$ sudo modprobe -v rt2800pci
[sudo] password for sysadmin: 
insmod /lib/modules/2.6.38-11-server/updates/cw-2.6.39/eeprom_93cx6.ko 
insmod /lib/modules/2.6.38-11-server/updates/cw-2.6.39/cfg80211.ko 
insmod /lib/modules/2.6.38-11-server/updates/cw-2.6.39/mac80211.ko 
insmod /lib/modules/2.6.38-11-server/updates/cw-2.6.39/rt2x00lib.ko 
insmod /lib/modules/2.6.38-11-server/updates/cw-2.6.39/rt2x00pci.ko 
insmod /lib/modules/2.6.38-11-server/updates/cw-2.6.39/rt2800lib.ko 
insmod /lib/modules/2.6.38-11-server/updates/cw-2.6.39/rt2800pci.ko 
sysadmin@eobi-notebook:~$ sudo service network-manager restart
network-manager start/running, process 2889
sysadmin@eobi-notebook:~$ dmesg | grep rt2
[ 4321.312012] rt2800pci 0000:24:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[ 4321.312027] rt2800pci 0000:24:00.0: setting latency timer to 64
[ 4321.358754] Registered led device: rt2800pci-phy0::radio
[ 4321.358782] Registered led device: rt2800pci-phy0::assoc
[ 4321.358805] Registered led device: rt2800pci-phy0::quality
[ 4321.512030] phy0 -> rt2800pci_mcu_status: Error - MCU request failed, no response from hardware
sysadmin@eobi-notebook:~$ rfkill list
Command 'rfkill' is available in the following places
 * /sbin/rfkill
 * /usr/sbin/rfkill
The command could not be located because '/sbin:/usr/sbin' is not included in the PATH environment variable.
This is most likely caused by the lack of administrative privileges associated with your user account.
rfkill: command not found
sysadmin@eobi-notebook:~$ /sbin/rfkill
Usage:    /sbin/rfkill [options] command
Options:
    --version    show version (0.4)
Commands:
    help
    event
    list [IDENTIFIER]
    block IDENTIFIER
    unblock IDENTIFIER
where IDENTIFIER is the index no. of an rfkill switch or one of:
    <idx> all wifi wlan bluetooth uwb ultrawideband wimax wwan gps fm
sysadmin@eobi-notebook:~$ /usr/sbin/rfkill
Usage:    /usr/sbin/rfkill [options] command
Options:
    --version    show version (0.4-1 (Ubuntu))
Commands:
    help
    event
    list [IDENTIFIER]
    block IDENTIFIER
    unblock IDENTIFIER
where IDENTIFIER is the index no. of an rfkill switch or one of:
    <idx> all wifi wlan bluetooth uwb ultrawideband wimax wwan gps fm
sysadmin@eobi-notebook:~$ iwconfig
Command 'iwconfig' is available in '/sbin/iwconfig'
The command could not be located because '/sbin' is not included in the PATH environment variable.
This is most likely caused by the lack of administrative privileges associated with your user account.
iwconfig: command not found
sysadmin@eobi-notebook:~$ /sbin/iwconfig
lo        no wireless extensions.

eth1      no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off


Whats the name of your computer?

---

### Post by mavericck on 2011-10-11
Its HP ProBook 4530s.

---

### Post by praseodym on 2011-10-11
Try to remove the module hp_wmi:

```
sudo rmmod hp_wmi
sudo rfkill unblock all
```

---

### Post by mavericck on 2011-10-12
Still No Luck :(!

---

### Post by mitulv4u on 2011-11-02
I am having HP ProBook 4430s

I am facing a similar problem, Wifi Hardware is detected in the top notification bar, but no networks are detected.
I am using Ubuntu 11.10.

________________________________________________________________________________________________________________
Check this:
mitul@mitul-HP-ProBook-4430s:~$ /sbin/iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
_________

Another output lspci

23:00.2 SD Host controller: JMicron Technology Corp. Standard SD Host Controller (rev 30)
23:00.3 System peripheral: JMicron Technology Corp. MS Host Controller (rev 30)
24:00.0 Network controller: Ralink corp. Device 3592
25:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 06)
__________________

Please someone help!!!!!!

---

### Post by praseodym on 2011-11-02
Hi mitulv4u,

shut off the power management:

```
sudo iwconfig wlan0 power off
```

---

### Post by mitulv4u on 2011-11-02
Hi praseodym,

Thanks for your reply.
I did so, but what does it do? I still don't see wireless networks visible.

---

### Post by praseodym on 2011-11-02
Ok,

please show:

```
lspci -nnk | grep -iA2 net
iwconfig #again
sudo iwlist scan
lsmod
uname -a
dmesg | egrep 'rt3|rt2'
rfkill list
```

---

### Post by mitulv4u on 2011-11-02
Hi,

Attached is the output in a text file.

---

### Post by iooma on 2011-11-06
Network controller: Ralink corp. Device 3592

Yes,wireless somehow doesnt work 

try this? 
translated from a Russian site

[B]Solving Problems with Ralink RT3592

I think many familiar with the situation when the laptop identifies all devices except the wireless connection, well, or, as in my case, the device is recognized but not working.

To determine what kind of device is responsible for the wireless connection, you can execute the following command:

$ Lspci-v | grep-i-A 5 "network controller"
24:00.0 Network controller: Ralink corp. Device 3592
Subsystem: Hewlett-Packard Company Device 1638
Flags: bus master, fast devsel, latency 0, IRQ 19
Memory at d4700000 (32-bit, non-prefetchable) [size = 64K]
Capabilities:
Kernel driver in use: rt2800pci

As can be seen, the device is identified as Ralink RT3592, and even found a driver rt2800pci. In the description of the driver does have this card, but the device does not wish to be connected to the network.

Googling, I learned that I am not the only one who have the problem. Many advised to go to the official website of Ralink, download a tarball with the drivers and follow the instructions to install them. Installing the truth was make & & make install, which I personally do not like: I want to know what, where and why is copied to my system, so that if something were to look for the problem easier.

So. The first thing you need - is to download a tarball with the driver from the official site (have to sign the agreement).

The manufacturer's website says that these drivers are suitable for the RT3060, RT3062, RT3562 and RT3592. I tested only on its chip.

Next, unpack the tarball and the directory contains files inside README_STA_pci, where you can read all the installation instructions (including the infamous make install).

Next steps.

1. modify Makefile according to the instructions (I did not need)
2. change the os / linux / config.mk according to instructions (changing settings):

HAS_WPA_SUPPLICANT = y
HAS_NATIVE_WPA_SUPPLICANT_SUPPORT = y

3. make: I gave an error when creating a directory in the root (strange that it's in the make), but the assembly was completed
4. sudo mkdir-p / etc/Wireless/RT2860STA
5. sudo cp RT2860STA.dat / etc/Wireless/RT2860STA
6. sudo cp RT2860STACard.dat / etc/Wireless/RT2860STA
6. sudo cp os/linux/rt3562sta.ko / lib / modules / $ (uname-r) / kernel/drivers/net/wireless/rt2860sta.ko
7. sudo depmod $ (uname-r)
8. add a module to the blacklist rt2800pci for Ubuntu is equivalent to adding to / etc / modprobe.d / blacklist.conf lines:

blacklist rt2800pci

9. reboot

In principle, until the eighth paragraph to see success, you can try the following:

$ Sudo modprobe-r rt2800pci
$ Sudo modprobe rt2860sta

... And restart the network. If everything goes well, we can safely add a free module in the blacklist.

Of course, in an amicable way to compile the package, but the time for analysis of the principles of the assembly, I was not. But such a package is in the repository Russian Fedora (Respect), and the AUR PKGBUILD for too simple.[/B]

---

### Post by mitulv4u on 2012-12-21
It works good with Ubuntu 12.04. Jus some problems and issues with frequent disconnection.

---

