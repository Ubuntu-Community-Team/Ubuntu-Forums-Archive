---
title: "Netgear WN311B/Broadcom 4321 Problems - Ubuntu 13.04"
date: 2013-05-22
forum: Networking &amp; Wireless
---

### Post by JadarDev on 2013-05-22
Hello!

I'm not absolutely new to unix, but I decided I'd have a go at Ubuntu.. I installed Ubuntu 13.04. So far everything has been good, but my wireless card is not working. The computer is a PC custom build. The card, a NetGear WN311B which uses the Broadcom 4321 chip, works fine on Windows and Mac OS X. I think I have almost gotten it working but it will still not connect to networks. I got it to detect networks, just not connect to them. I installed the b43-fwcutter and firmware-b43-installer, and that is what made it find the networks. But it will not connect to any. Also, it seems the range is significantly lower. I tried to use the ndis thing but I'd rather not rely on Windows drivers on a linux system. Any ideas? Thanks!

---

### Post by JadarDev on 2013-05-23
bump

---

### Post by Hadaka on 2013-05-23
Hi, please post the output of..
```
lsmod
lspci -nn | egrep '0200|0280'
sudo iwconfig wlan0 scan
```
thanks

---

### Post by JadarDev on 2013-05-23
Here: 

```

$ lsmod
Module                  Size  Used by
nls_utf8               12557  2 
hfsplus                88539  2 
bnep                   18036  2 
rfcomm                 42641  0 
bluetooth             228619  10 bnep,rfcomm
snd_hda_codec_hdmi     36913  1 
b43                   378642  1 
bcma                   41051  1 b43
mac80211              606457  1 b43
cfg80211              510937  2 b43,mac80211
snd_hda_codec_realtek    78399  1 
snd_usb_audio         140685  1 
snd_usbmidi_lib        24938  1 snd_usb_audio
ssb_hcd                12869  0 
coretemp               13355  0 
ppdev                  17073  0 
snd_hda_intel          39619  3 
kvm_intel             132891  0 
snd_hda_codec         136453  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
kvm                   443165  1 kvm_intel
snd_hwdep              13602  2 snd_usb_audio,snd_hda_codec
snd_pcm                97451  4 snd_usb_audio,snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
radeon                937749  3 
binfmt_misc            17500  1 
snd_seq_midi           13324  0 
snd_seq_midi_event     14899  1 snd_seq_midi
parport_pc             28152  1 
snd_rawmidi            30180  2 snd_usbmidi_lib,snd_seq_midi
snd_seq                61554  2 snd_seq_midi_event,snd_seq_midi
gpio_ich               13476  0 
ttm                    83187  1 radeon
drm_kms_helper         49394  1 radeon
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              29425  2 snd_pcm,snd_seq
drm                   286313  5 ttm,drm_kms_helper,radeon
snd                    68876  20 snd_hda_codec_realtek,snd_usb_audio,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_usbmidi_lib,snd_hda_codec,snd_hda_intel,snd_seq_device
psmouse                95870  0 
lpc_ich                17061  0 
i2c_algo_bit           13413  1 radeon
soundcore              12680  1 snd
mac_hid                13205  0 
serio_raw              13215  0 
microcode              22881  0 
lp                     17759  0 
parport                46345  3 lp,ppdev,parport_pc
pata_acpi              13038  0 
hid_generic            12540  0 
usbhid                 47074  0 
hid                   101002  2 hid_generic,usbhid
usb_storage            57204  2 
ssb                    56748  2 b43,ssb_hcd
r8169                  67446  0 
ahci                   25731  2 
libahci                31364  1 ahci
pata_jmicron           12758  0 
$ lspci -nn | egrep '0200|0280'
04:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168 PCI Express Gigabit Ethernet controller [10ec:8168] (rev 02)
05:01.0 Network controller [0280]: Broadcom Corporation BCM4321 802.11b/g/n [14e4:4329] (rev 01)
$ sudo iwconfig wlan0 scan
[sudo] password for user: 
iwconfig: unknown command "scan"


```

---

### Post by Hadaka on 2013-05-23
Let's give this a try..
please Copy and paste into a terminal.
```
sudo apt-get install bcmwl-kernel-source
sudo modprobe wl

```
thanks.

---

### Post by JadarDev on 2013-05-23
Oh, also. I have been testing stuff with Synaptic Package Manager and now whenever I deactivate the b43 module and activate it again the system crashes.

---

### Post by Hadaka on 2013-05-23
Not sure if you saw my last post..
please Copy and paste into a terminal..
```
sudo apt-get install bcmwl-kernel-source
echo "blacklist bcma" | sudo tee -a /etc/modprobe.d/blacklist.conf
 sudo modprobe wl
```
thanks.

---

### Post by JadarDev on 2013-05-23
That one didn't do anything. Wifi does not showed up in the Network tab.

---

### Post by JadarDev on 2013-05-23
Also that driver does not let me suspend or restart without hard restarting.

---

### Post by Hadaka on 2013-05-23
That should be the correct driver for your card..

BCM4321 802.11b/g/n [14e4:4329]

plese do..
```
sudo modprobe -rfv wl
sudo modprobe -v wl
dmesg | grep wl
```
thanks

---

### Post by JadarDev on 2013-05-23
This is the output. 

I restarted and now Wifi shows up but to doesn't find any networks.

```

$ sudo modprobe -rfv wl
rmmod wl
rmmod cfg80211
$ sudo modprobe -v wl
insmod /lib/modules/3.8.0-21-generic/kernel/net/wireless/cfg80211.ko 
insmod /lib/modules/3.8.0-21-generic/updates/dkms/wl.ko 
$ dmesg | grep wl
[   11.343947] wl: module license 'MIXED/Proprietary' taints kernel.
[   11.368742] INFO @wl_cfg80211_attach : Registered CFG80211 phy
[   11.423040] Modules linked in: snd_hda_codec_hdmi wl(POF+) lib80211 snd_usb_audio snd_hda_codec_realtek snd_usbmidi_lib snd_hda_intel(+) snd_hda_codec snd_hwdep(F) snd_pcm(F) snd_page_alloc(F) cfg80211 snd_seq_midi(F) snd_seq_midi_event(F) snd_rawmidi(F) snd_seq(F) bnep rfcomm snd_seq_device(F) radeon ppdev(F) bluetooth coretemp kvm_intel snd_timer(F) kvm parport_pc(F) ttm snd(F) drm_kms_helper drm psmouse(F) mac_hid gpio_ich binfmt_misc(F) serio_raw(F) soundcore(F) lpc_ich i2c_algo_bit lp(F) parport(F) microcode(F) pata_acpi hid_generic usbhid hid usb_storage(F) ahci(F) libahci(F) r8169 pata_jmicron
[   87.371750] INFO @wl_cfg80211_attach : Registered CFG80211 phy

```

---

### Post by JadarDev on 2013-05-23
This is the output of ifconfig.

```

eth0      Link encap:Ethernet  HWaddr 6c:f0:49:04:d6:bd  
          inet addr:192.168.2.3  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::6ef0:49ff:fe04:d6bd/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2598 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1782 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2972924 (2.9 MB)  TX bytes:222007 (222.0 KB)


eth1      Link encap:Ethernet  HWaddr 00:24:b2:8b:d1:67  
          inet6 addr: fe80::224:b2ff:fe8b:d167/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:19 Base address:0xc000 


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:295 errors:0 dropped:0 overruns:0 frame:0
          TX packets:295 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:39601 (39.6 KB)  TX bytes:39601 (39.6 KB)

```

And iwconfig:

```

eth0      no wireless extensions.


eth1      IEEE 802.11abg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
lo        no wireless extensions.

```

---

### Post by Hadaka on 2013-05-23
ok, please do..
```
lsmod
cat /etc/modules
cat /etc/network/interfaces
```
thanks.

---

### Post by JadarDev on 2013-05-23
here 

```

$ lsmod
Module                  Size  Used by
wl                   3074449  0 
cfg80211              510937  1 wl
nls_utf8               12557  2 
hfsplus                88539  2 
lib80211_crypt_tkip    17379  0 
snd_hda_codec_hdmi     36913  1 
lib80211               14352  2 wl,lib80211_crypt_tkip
snd_usb_audio         140685  1 
snd_hda_codec_realtek    78399  1 
snd_usbmidi_lib        24938  1 snd_usb_audio
snd_hda_intel          61623  4 
snd_hda_codec         136453  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
snd_hwdep              13602  2 snd_usb_audio,snd_hda_codec
snd_pcm                97451  4 snd_usb_audio,snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
snd_seq_midi           13324  0 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_rawmidi            30180  2 snd_usbmidi_lib,snd_seq_midi
snd_seq                61554  2 snd_seq_midi_event,snd_seq_midi
bnep                   18036  2 
rfcomm                 42641  0 
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
radeon                937749  5 
ppdev                  17073  0 
bluetooth             228619  10 bnep,rfcomm
coretemp               13355  0 
kvm_intel             132891  0 
snd_timer              29425  2 snd_pcm,snd_seq
kvm                   443165  1 kvm_intel
parport_pc             28152  1 
ttm                    83187  1 radeon
snd                    68876  20 snd_hda_codec_realtek,snd_usb_audio,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_usbmidi_lib,snd_hda_codec,snd_hda_intel,snd_seq_device
drm_kms_helper         49394  1 radeon
drm                   286313  7 ttm,drm_kms_helper,radeon
psmouse                95870  0 
mac_hid                13205  0 
gpio_ich               13476  0 
binfmt_misc            17500  1 
serio_raw              13215  0 
soundcore              12680  1 snd
lpc_ich                17061  0 
i2c_algo_bit           13413  1 radeon
lp                     17759  0 
parport                46345  3 lp,ppdev,parport_pc
microcode              22881  0 
pata_acpi              13038  0 
hid_generic            12540  0 
usbhid                 47074  0 
hid                   101002  2 hid_generic,usbhid
usb_storage            57204  2 
ahci                   25731  2 
libahci                31364  1 ahci
r8169                  67446  0 
pata_jmicron           12758  0 
$ cat /etc/modules
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.
# Parameters can be specified after the module name.


loop
lp
rtc
$ cat /etc/network/interfaces
# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

```

thanks :)

---

### Post by Hadaka on 2013-05-23
Did you try loading ndiswrapper or a different broadcom sta backports?
please do..
copy and paste please..
```
sudo echo "lib80211_crypt_tkip" | sudo tee -a /etc/modprobe.d/blacklist.conf
sudo modprobe -rfv wl
sudo modprobe -v wl
dmesg | grep wl
lsmod
cat /etc/modprobe.d/blacklist.conf | grep blacklist
```
thanks.

---

### Post by JadarDev on 2013-05-23
Yes, with ndiswrapper i could not activate the module.

here is the output from the commands that gave data:

```

$ dmesg | grep wl
[   11.343947] wl: module license 'MIXED/Proprietary' taints kernel.
[   11.368742] INFO @wl_cfg80211_attach : Registered CFG80211 phy
[   11.423040] Modules linked in: snd_hda_codec_hdmi wl(POF+) lib80211 snd_usb_audio snd_hda_codec_realtek snd_usbmidi_lib snd_hda_intel(+) snd_hda_codec snd_hwdep(F) snd_pcm(F) snd_page_alloc(F) cfg80211 snd_seq_midi(F) snd_seq_midi_event(F) snd_rawmidi(F) snd_seq(F) bnep rfcomm snd_seq_device(F) radeon ppdev(F) bluetooth coretemp kvm_intel snd_timer(F) kvm parport_pc(F) ttm snd(F) drm_kms_helper drm psmouse(F) mac_hid gpio_ich binfmt_misc(F) serio_raw(F) soundcore(F) lpc_ich i2c_algo_bit lp(F) parport(F) microcode(F) pata_acpi hid_generic usbhid hid usb_storage(F) ahci(F) libahci(F) r8169 pata_jmicron
[   87.371750] INFO @wl_cfg80211_attach : Registered CFG80211 phy
[  460.951570] ERROR @wl_dev_intvar_get : error (-1)
[  460.951575] ERROR @wl_cfg80211_get_tx_power : error (-1)
[10295.268187] INFO @wl_cfg80211_attach : Registered CFG80211 phy
[10347.012780] INFO @wl_cfg80211_attach : Registered CFG80211 phy
$ lsmod
Module                  Size  Used by
wl                   3074449  0 
cfg80211              510937  1 wl
nls_utf8               12557  2 
hfsplus                88539  2 
lib80211_crypt_tkip    17379  0 
snd_hda_codec_hdmi     36913  1 
lib80211               14352  2 wl,lib80211_crypt_tkip
snd_usb_audio         140685  1 
snd_hda_codec_realtek    78399  1 
snd_usbmidi_lib        24938  1 snd_usb_audio
snd_hda_intel          61623  4 
snd_hda_codec         136453  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
snd_hwdep              13602  2 snd_usb_audio,snd_hda_codec
snd_pcm                97451  4 snd_usb_audio,snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
snd_seq_midi           13324  0 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_rawmidi            30180  2 snd_usbmidi_lib,snd_seq_midi
snd_seq                61554  2 snd_seq_midi_event,snd_seq_midi
bnep                   18036  2 
rfcomm                 42641  0 
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
radeon                937749  5 
ppdev                  17073  0 
bluetooth             228619  10 bnep,rfcomm
coretemp               13355  0 
kvm_intel             132891  0 
snd_timer              29425  2 snd_pcm,snd_seq
kvm                   443165  1 kvm_intel
parport_pc             28152  1 
ttm                    83187  1 radeon
snd                    68876  20 snd_hda_codec_realtek,snd_usb_audio,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_usbmidi_lib,snd_hda_codec,snd_hda_intel,snd_seq_device
drm_kms_helper         49394  1 radeon
drm                   286313  7 ttm,drm_kms_helper,radeon
psmouse                95870  0 
mac_hid                13205  0 
gpio_ich               13476  0 
binfmt_misc            17500  1 
serio_raw              13215  0 
soundcore              12680  1 snd
lpc_ich                17061  0 
i2c_algo_bit           13413  1 radeon
lp                     17759  0 
parport                46345  3 lp,ppdev,parport_pc
microcode              22881  0 
pata_acpi              13038  0 
hid_generic            12540  0 
usbhid                 47074  0 
hid                   101002  2 hid_generic,usbhid
usb_storage            57204  2 
ahci                   25731  2 
libahci                31364  1 ahci
r8169                  67446  0 
pata_jmicron           12758  0 
$ cat /etc/modprobe.d/blacklist.conf | grep blacklist
blacklist evbug
blacklist usbmouse
blacklist usbkbd
blacklist eepro100
blacklist de4x5
blacklist eth1394
blacklist snd_intel8x0m
blacklist snd_aw2
blacklist i2c_i801
blacklist prism54
blacklist bcm43xx
blacklist garmin_gps
blacklist asus_acpi
blacklist snd_pcsp
blacklist pcspkr
blacklist amd76x_edac
blacklist bcma
blacklist lib80211_crypt_tkip

```

---

### Post by Hadaka on 2013-05-23
ok,this statement has me nervous,,,
"Oh, also. I have been testing stuff with Synaptic Package Manager and  now whenever I deactivate the b43 module and activate it again the  system crashes."
sooo..go back into the pacakage mgr. and delete everything you may have tried.
then please do..
```
sudo modprobe -rfv lib80211_crypt_tkip
```
I am not sure just what you may have loaded with the ndiswrapper
so please do these...one line at a time...if you get an error ...ignore it
and do the next line anyway.
```
sudo modprobe -rfv ndiswrapper
sudo apt-get remove --purge ndisgtk ndiswrapper*
sudo rm /etc/modprobe.d/ndis*
sudo rm -r /etc/ndiswrapper/*
 
```
something is giving us a tainted kernel message so there has to be
another module part somewhere...
thanks.

---

### Post by JadarDev on 2013-05-23
Okay, should I just reinstall? It'll be no problem and that way we get a fresh install to mess with.

---

### Post by Hadaka on 2013-05-23
normally I would say no...however...
if you have a fast connection, and nothing to lose]
go for it. Also when it ask if you want to load the proprietary
driver say...NO .. then be sure to run all your updates
by doing this after the load...
```
sudo apt-get update
sudo apt-get upgrade
```
then...i think we should try a different driver..
post back when you are up and running..
thanks.

---

### Post by JadarDev on 2013-05-23
Okay, done. What now?

---

### Post by Hadaka on 2013-05-23
Hi, please post the output of..
```
lspci -nnk | grep -iA3 net
```
thanks

---

### Post by JadarDev on 2013-05-23
Here 

```

$ lspci -nnk | grep -iA3 net
04:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168 PCI Express Gigabit Ethernet controller [10ec:8168] (rev 02)
    Subsystem: Gigabyte Technology Co., Ltd Motherboard [1458:e000]
    Kernel driver in use: r8169
05:01.0 Network controller [0280]: Broadcom Corporation BCM4321 802.11b/g/n [14e4:4329] (rev 01)
    Subsystem: Netgear WN311B RangeMax Next 270 Mbps Wireless PCI Adapter [1385:7d00]
    Kernel driver in use: b43-pci-bridge



```

thanks :)

---

### Post by Hadaka on 2013-05-23
ok, so you loaded the b43. Did you load it
with fwcutter...b43 installer command?
do you see ssid's from your router connection?

---

### Post by JadarDev on 2013-05-23
no thats fresh install. no wireless card is recognized.

thanks

---

### Post by Hadaka on 2013-05-23
this says the b43 is loaded..


Kernel driver in use: b43-pci-bridge

please do..
```
sudo modprobe b43
```
thanks.

---

### Post by JadarDev on 2013-05-23
Nothing.. :/

thanks

---

### Post by Hadaka on 2013-05-23
ok, so lets unload the b43 and try the wl diver that your card calls for.
please do..
```
sudo apt-get remove --purge b43-fwcutter firmware-b43-installer
sudo modprobe -rfv b43
```
then,,
```
sudo apt-get install bcmwl-kernel-source
sudo modprobe -v wl
```
dont boot..and see if wireless is activated
thanks.

---

### Post by JadarDev on 2013-05-24
No, And I do not think the b43-fwcutter was installed. I think it was using some other generic kernel module that wasnt b43xx.. It did not detect wireless with the bcmwl-kernel-source before reboot. I haven't rebooted yet, though. This is iwconfig:

```

eth0      no wireless extensions.

lo        no wireless extensions.

```

---

### Post by Hadaka on 2013-05-24
ok, lets see if the module was loaded ok.
please do
```
lspci -nnk | grep -iA3 net
lsmod
```
thanks

---

### Post by JadarDev on 2013-05-24
here we are, still the old one.

```

$ lspci -nnk | grep -iA3 net
04:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168 PCI Express Gigabit Ethernet controller [10ec:8168] (rev 02)
    Subsystem: Realtek Semiconductor Co., Ltd. RTL8111/8168 PCI Express Gigabit Ethernet controller [10ec:8168]
    Kernel driver in use: r8169
05:01.0 Network controller [0280]: Broadcom Corporation BCM4321 802.11b/g/n [14e4:4329] (rev 01)
    Subsystem: Netgear WN311B RangeMax Next 270 Mbps Wireless PCI Adapter [1385:7d00]
    Kernel driver in use: b43-pci-bridge
$ lsmod
Module                  Size  Used by
wl                   3074449  0 
lib80211               14352  1 wl
cfg80211              510937  1 wl
btrfs                 785967  0 
zlib_deflate           26885  1 btrfs
ufs                    74597  0 
qnx4                   13317  0 
hfs                    54503  0 
minix                  36072  0 
ntfs                   96967  0 
msdos                  17332  0 
jfs                   185045  0 
xfs                   869118  0 
libcrc32c              12615  2 xfs,btrfs
reiserfs              241608  0 
ext2                   72837  0 
nls_utf8               12557  1 
hfsplus                88539  1 
bnep                   18036  2 
rfcomm                 42641  0 
bluetooth             228619  10 bnep,rfcomm
snd_hda_codec_hdmi     36913  1 
snd_hda_codec_realtek    78399  1 
snd_hda_intel          39619  6 
snd_usb_audio         140685  2 
snd_hda_codec         136453  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
snd_usbmidi_lib        24938  1 snd_usb_audio
snd_hwdep              13602  2 snd_usb_audio,snd_hda_codec
snd_pcm                97451  4 snd_usb_audio,snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
snd_seq_midi           13324  0 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_rawmidi            30180  2 snd_usbmidi_lib,snd_seq_midi
snd_seq                61554  2 snd_seq_midi_event,snd_seq_midi
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
radeon                937749  3 
snd_timer              29425  2 snd_pcm,snd_seq
snd                    68876  28 snd_hda_codec_realtek,snd_usb_audio,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_usbmidi_lib,snd_hda_codec,snd_hda_intel,snd_seq_device
soundcore              12680  1 snd
ttm                    83187  1 radeon
coretemp               13355  0 
drm_kms_helper         49394  1 radeon
drm                   286313  5 ttm,drm_kms_helper,radeon
kvm_intel             132891  0 
kvm                   443165  1 kvm_intel
psmouse                95870  0 
serio_raw              13215  0 
i2c_algo_bit           13413  1 radeon
gpio_ich               13476  0 
ppdev                  17073  0 
lp                     17759  0 
lpc_ich                17061  0 
parport_pc             28152  1 
parport                46345  3 lp,ppdev,parport_pc
mac_hid                13205  0 
ssb_hcd                12869  0 
microcode              22881  0 
pata_acpi              13038  0 
hid_generic            12540  0 
usbhid                 47074  0 
hid                   101002  2 hid_generic,usbhid
usb_storage            57204  1 
ssb                    56748  1 ssb_hcd
r8169                  67446  0 
ahci                   25731  2 
libahci                31364  1 ahci
pata_jmicron           12758  0 

```

---

### Post by Hadaka on 2013-05-24
Hi, the ssb module from the b43 is still in the lsmod
dump. Lets toos that  into the blackhole..
please do..
```
echo "blaklist ssb" | sudo tee -a /etc/modprobe.d/blacklist.conf
sudo modprobe -rfv ssb
sudo modprobe -rfv wl
sudo modprobe wl
```
do you have wireless?

---

### Post by JadarDev on 2013-05-24
With a reboot wifi shows up, but no networks show up. (Before those commands.) After those commands nothing changed.

---

### Post by Hadaka on 2013-05-24
ok, thats a good thing.
lets look if there are any reasons
why its not up yet..
please do..
```
sudo modprobe wl
dmesg | grep wl
ifconfig
iwconfig
lsmod
```
thanks

---

### Post by JadarDev on 2013-05-24
here 

```

$ dmesg | grep wl
[    9.724751] wl: module license 'MIXED/Proprietary' taints kernel.
[    9.800918] INFO @wl_cfg80211_attach : Registered CFG80211 phy
$ ifconfig
eth0      Link encap:Ethernet  HWaddr 6c:f0:49:04:d6:bd  
          inet addr:192.168.2.3  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::6ef0:49ff:fe04:d6bd/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1356 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1033 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1350491 (1.3 MB)  TX bytes:132388 (132.3 KB)

eth1      Link encap:Ethernet  HWaddr 00:24:b2:8b:d1:67  
          inet6 addr: fe80::224:b2ff:fe8b:d167/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:19 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:307 errors:0 dropped:0 overruns:0 frame:0
          TX packets:307 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:31919 (31.9 KB)  TX bytes:31919 (31.9 KB)

$ iwconfig
eth0      no wireless extensions.

eth1      IEEE 802.11abg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
lo        no wireless extensions.

$ lsmod
Module                  Size  Used by
nls_utf8               12557  2 
hfsplus                88539  2 
snd_hda_codec_hdmi     36913  1 
bnep                   18036  2 
rfcomm                 42641  0 
bluetooth             228619  10 bnep,rfcomm
snd_usb_audio         140685  1 
snd_hda_codec_realtek    78399  1 
snd_usbmidi_lib        24938  1 snd_usb_audio
snd_hda_intel          39619  3 
snd_hda_codec         136453  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
snd_hwdep              13602  2 snd_usb_audio,snd_hda_codec
snd_pcm                97451  4 snd_usb_audio,snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
snd_seq_midi           13324  0 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_rawmidi            30180  2 snd_usbmidi_lib,snd_seq_midi
snd_seq                61554  2 snd_seq_midi_event,snd_seq_midi
coretemp               13355  0 
kvm_intel             132891  0 
kvm                   443165  1 kvm_intel
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              29425  2 snd_pcm,snd_seq
ppdev                  17073  0 
gpio_ich               13476  0 
lib80211_crypt_tkip    17379  0 
snd                    68876  20 snd_hda_codec_realtek,snd_usb_audio,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_usbmidi_lib,snd_hda_codec,snd_hda_intel,snd_seq_device
parport_pc             28152  1 
wl                   3074449  0 
lib80211               14352  2 wl,lib80211_crypt_tkip
radeon                937749  3 
cfg80211              510937  1 wl
ttm                    83187  1 radeon
drm_kms_helper         49394  1 radeon
drm                   286313  5 ttm,drm_kms_helper,radeon
psmouse                95870  0 
mac_hid                13205  0 
serio_raw              13215  0 
microcode              22881  0 
soundcore              12680  1 snd
i2c_algo_bit           13413  1 radeon
lpc_ich                17061  0 
lp                     17759  0 
parport                46345  3 lp,ppdev,parport_pc
pata_acpi              13038  0 
hid_generic            12540  0 
usbhid                 47074  0 
hid                   101002  2 hid_generic,usbhid
usb_storage            57204  2 
ahci                   25731  2 
libahci                31364  1 ahci
r8169                  67446  0 
pata_jmicron           12758  0 

```

thats strankge. it doesnt see it as a wireless n device.

thanks :)

---

### Post by Hadaka on 2013-05-24
Hi, i dont know where it is getting this..

module license 'MIXED/Proprietary' taints kernel
please do..
```
sudo modprobe -rfv wl
sudo rmmod ssb
sudo rmmod bcma
sudo modprobe wl
```
thanks.

---

### Post by JadarDev on 2013-05-24
here.

```

$ sudo modprobe -rfv wl
[sudo] password for user: 
rmmod wl
rmmod cfg80211
$ sudo rmmod ssb
Error: Module ssb is not currently loaded
$ sudo rmmod bcma
Error: Module bcma is not currently loaded
$ sudo modprobe wl

```

---

### Post by Hadaka on 2013-05-24
ok, lets take a look at the logs..see what they have to say..
please do..
```
sudo cat /var/log/syslog | grep -e b43 -e wl -e firmware -e eth1 | tail -n35
 
```
thanks.

---

### Post by JadarDev on 2013-05-24
```

$ sudo cat /var/log/syslog | grep -e b43 -e wl -e firmware -e eth1 | tail -n35
May 24 13:43:20 Ubuntu NetworkManager[989]: <info> (eth1): new 802.11 WiFi device (driver: 'wl' ifindex: 4)
May 24 13:43:20 Ubuntu NetworkManager[989]: <info> (eth1): exported as /org/freedesktop/NetworkManager/Devices/2
May 24 13:43:20 Ubuntu NetworkManager[989]: <info> (eth1): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
May 24 13:43:20 Ubuntu NetworkManager[989]: <info> (eth1): bringing up device.
May 24 13:43:20 Ubuntu kernel: [10560.603811] eth1: Broadcom BCM4329 802.11 Hybrid Wireless Controller 6.20.155.1 (r326264)
May 24 13:43:20 Ubuntu NetworkManager[989]: <info> (eth1): preparing device.
May 24 13:43:20 Ubuntu NetworkManager[989]: <info> (eth1): deactivating device (reason 'managed') [2]
May 24 13:43:20 Ubuntu NetworkManager[989]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1e.0/0000:05:01.0/net/eth1, iface: eth1)
May 24 13:43:20 Ubuntu NetworkManager[989]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1e.0/0000:05:01.0/net/eth1, iface: eth1): no ifupdown configuration found.
May 24 13:43:20 Ubuntu NetworkManager[989]: <info> rfkill3: found WiFi radio killswitch (at /sys/devices/pci0000:00/0000:00:1e.0/0000:05:01.0/net/eth1/rfkill3) (driver wl)
May 24 13:43:20 Ubuntu NetworkManager[989]: <info> (eth1) supports 1 scan SSIDs
May 24 13:43:20 Ubuntu NetworkManager[989]: <info> (eth1): supplicant interface state: starting -> ready
May 24 13:43:20 Ubuntu NetworkManager[989]: <info> (eth1): device state change: unavailable -> disconnected (reason 'supplicant-available') [20 30 42]
May 24 13:43:20 Ubuntu NetworkManager[989]: <info> (eth1): supplicant interface state: ready -> inactive
May 24 13:43:20 Ubuntu NetworkManager[989]: <info> (eth1) supports 1 scan SSIDs
May 24 13:43:22 Ubuntu avahi-daemon[944]: Joining mDNS multicast group on interface eth1.IPv6 with address fe80::224:b2ff:fe8b:d167.
May 24 13:43:22 Ubuntu avahi-daemon[944]: New relevant interface eth1.IPv6 for mDNS.
May 24 13:43:22 Ubuntu avahi-daemon[944]: Registering new address record for fe80::224:b2ff:fe8b:d167 on eth1.*.
May 24 13:43:37 Ubuntu NetworkManager[989]: <info> Activation (eth1) starting connection 'Rhodaccess'
May 24 13:43:37 Ubuntu NetworkManager[989]: <info> (eth1): device state change: disconnected -> prepare (reason 'none') [30 40 0]
May 24 13:43:37 Ubuntu NetworkManager[989]: <info> Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled...
May 24 13:43:37 Ubuntu NetworkManager[989]: <info> Activation (eth1) Stage 1 of 5 (Device Prepare) started...
May 24 13:43:37 Ubuntu NetworkManager[989]: <info> Activation (eth1) Stage 2 of 5 (Device Configure) scheduled...
May 24 13:43:37 Ubuntu NetworkManager[989]: <info> Activation (eth1) Stage 1 of 5 (Device Prepare) complete.
May 24 13:43:37 Ubuntu NetworkManager[989]: <info> Activation (eth1) Stage 2 of 5 (Device Configure) starting...
May 24 13:43:37 Ubuntu NetworkManager[989]: <info> (eth1): device state change: prepare -> config (reason 'none') [40 50 0]
May 24 13:43:37 Ubuntu NetworkManager[989]: <info> Activation (eth1/wireless): connection 'Rhodaccess' has security, and secrets exist.  No new secrets needed.
May 24 13:43:37 Ubuntu NetworkManager[989]: <info> Activation (eth1) Stage 2 of 5 (Device Configure) complete.
May 24 13:43:37 Ubuntu NetworkManager[989]: <info> (eth1): supplicant interface state: inactive -> scanning
May 24 13:44:02 Ubuntu NetworkManager[989]: <warn> Activation (eth1/wireless): association took too long, failing activation.
May 24 13:44:02 Ubuntu NetworkManager[989]: <info> (eth1): device state change: config -> failed (reason 'SSID not found') [50 120 53]
May 24 13:44:02 Ubuntu NetworkManager[989]: <warn> Activation (eth1) failed for connection 'Rhodaccess'
May 24 13:44:02 Ubuntu NetworkManager[989]: <info> (eth1): device state change: failed -> disconnected (reason 'none') [120 30 0]
May 24 13:44:02 Ubuntu NetworkManager[989]: <info> (eth1): deactivating device (reason 'none') [0]
May 24 13:44:02 Ubuntu NetworkManager[989]: <info> (eth1): supplicant interface state: scanning -> inactive$ sudo cat /var/log/syslog | grep -e b43 -e wl -e firmware -e eth1 | tail -n35
May 24 13:43:20 Ubuntu NetworkManager[989]: <info> (eth1): new 802.11 WiFi device (driver: 'wl' ifindex: 4)
May 24 13:43:20 Ubuntu NetworkManager[989]: <info> (eth1): exported as /org/freedesktop/NetworkManager/Devices/2
May 24 13:43:20 Ubuntu NetworkManager[989]: <info> (eth1): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
May 24 13:43:20 Ubuntu NetworkManager[989]: <info> (eth1): bringing up device.
May 24 13:43:20 Ubuntu kernel: [10560.603811] eth1: Broadcom BCM4329 802.11 Hybrid Wireless Controller 6.20.155.1 (r326264)
May 24 13:43:20 Ubuntu NetworkManager[989]: <info> (eth1): preparing device.
May 24 13:43:20 Ubuntu NetworkManager[989]: <info> (eth1): deactivating device (reason 'managed') [2]
May 24 13:43:20 Ubuntu NetworkManager[989]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1e.0/0000:05:01.0/net/eth1, iface: eth1)
May 24 13:43:20 Ubuntu NetworkManager[989]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1e.0/0000:05:01.0/net/eth1, iface: eth1): no ifupdown configuration found.
May 24 13:43:20 Ubuntu NetworkManager[989]: <info> rfkill3: found WiFi radio killswitch (at /sys/devices/pci0000:00/0000:00:1e.0/0000:05:01.0/net/eth1/rfkill3) (driver wl)
May 24 13:43:20 Ubuntu NetworkManager[989]: <info> (eth1) supports 1 scan SSIDs
May 24 13:43:20 Ubuntu NetworkManager[989]: <info> (eth1): supplicant interface state: starting -> ready
May 24 13:43:20 Ubuntu NetworkManager[989]: <info> (eth1): device state change: unavailable -> disconnected (reason 'supplicant-available') [20 30 42]
May 24 13:43:20 Ubuntu NetworkManager[989]: <info> (eth1): supplicant interface state: ready -> inactive
May 24 13:43:20 Ubuntu NetworkManager[989]: <info> (eth1) supports 1 scan SSIDs
May 24 13:43:22 Ubuntu avahi-daemon[944]: Joining mDNS multicast group on interface eth1.IPv6 with address fe80::224:b2ff:fe8b:d167.
May 24 13:43:22 Ubuntu avahi-daemon[944]: New relevant interface eth1.IPv6 for mDNS.
May 24 13:43:22 Ubuntu avahi-daemon[944]: Registering new address record for fe80::224:b2ff:fe8b:d167 on eth1.*.
May 24 13:43:37 Ubuntu NetworkManager[989]: <info> Activation (eth1) starting connection 'Rhodaccess'
May 24 13:43:37 Ubuntu NetworkManager[989]: <info> (eth1): device state change: disconnected -> prepare (reason 'none') [30 40 0]
May 24 13:43:37 Ubuntu NetworkManager[989]: <info> Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled...
May 24 13:43:37 Ubuntu NetworkManager[989]: <info> Activation (eth1) Stage 1 of 5 (Device Prepare) started...
May 24 13:43:37 Ubuntu NetworkManager[989]: <info> Activation (eth1) Stage 2 of 5 (Device Configure) scheduled...
May 24 13:43:37 Ubuntu NetworkManager[989]: <info> Activation (eth1) Stage 1 of 5 (Device Prepare) complete.
May 24 13:43:37 Ubuntu NetworkManager[989]: <info> Activation (eth1) Stage 2 of 5 (Device Configure) starting...
May 24 13:43:37 Ubuntu NetworkManager[989]: <info> (eth1): device state change: prepare -> config (reason 'none') [40 50 0]
May 24 13:43:37 Ubuntu NetworkManager[989]: <info> Activation (eth1/wireless): connection 'Rhodaccess' has security, and secrets exist.  No new secrets needed.
May 24 13:43:37 Ubuntu NetworkManager[989]: <info> Activation (eth1) Stage 2 of 5 (Device Configure) complete.
May 24 13:43:37 Ubuntu NetworkManager[989]: <info> (eth1): supplicant interface state: inactive -> scanning
May 24 13:44:02 Ubuntu NetworkManager[989]: <warn> Activation (eth1/wireless): association took too long, failing activation.
May 24 13:44:02 Ubuntu NetworkManager[989]: <info> (eth1): device state change: config -> failed (reason 'SSID not found') [50 120 53]
May 24 13:44:02 Ubuntu NetworkManager[989]: <warn> Activation (eth1) failed for connection 'Rhodaccess'
May 24 13:44:02 Ubuntu NetworkManager[989]: <info> (eth1): device state change: failed -> disconnected (reason 'none') [120 30 0]
May 24 13:44:02 Ubuntu NetworkManager[989]: <info> (eth1): deactivating device (reason 'none') [0]
May 24 13:44:02 Ubuntu NetworkManager[989]: <info> (eth1): supplicant interface state: scanning -> inactive

```

---

### Post by Hadaka on 2013-05-24
please post the output of..
```
cat /etc/modules
cat /etc/network/interfaces
cat etc/NetworkManager/NetworkManager.conf
cat etc/modprobe.d/blacklist.conf | grep blacklist
```
thanks

---

### Post by JadarDev on 2013-05-24
here

```

$ cat /etc/modules
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.
# Parameters can be specified after the module name.

loop
lp
rtc
$ cat /etc/network/interfaces
# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback
$ cat /etc/NetworkManager/NetworkManager.conf 
[main]
plugins=ifupdown,keyfile
dns=dnsmasq

[ifupdown]
managed=false    
$ cat /etc/modprobe.d/blacklist.conf | grep blacklist
blacklist evbug
blacklist usbmouse
blacklist usbkbd
blacklist eepro100
blacklist de4x5
blacklist eth1394
blacklist snd_intel8x0m
blacklist snd_aw2
blacklist i2c_i801
blacklist prism54
blacklist bcm43xx
blacklist garmin_gps
blacklist asus_acpi
blacklist snd_pcsp
blacklist pcspkr
blacklist amd76x_edac
blacklist ssb

```

---

### Post by Hadaka on 2013-05-24
ok, please do..
```
sudo gedit /etc/modprobe.d/blacklist.conf
```
remove this one line..should be the last one..
```
blacklist ssb
```
save and close gedit
then do..
```
sudo apt-get remove --purge bcmwl-kernel-source
sudo modprobe -rfv wl
```
then..
```
sudo apt-get install linux-firmware-nonfree
sudo modprobe b43
```
boot and report back.
thanks.

---

### Post by JadarDev on 2013-05-24
Okay, now networks are seen, but it won't connect. Just tested WPA.

```

 Ubuntu NetworkManager[972]: <info> Activation (wlan0) starting connection 'WirelessNetwork'
May 24 15:13:12 Ubuntu NetworkManager[972]: <info> (wlan0): device state change: disconnected -> prepare (reason 'none') [30 40 0]
May 24 15:13:12 Ubuntu NetworkManager[972]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
May 24 15:13:12 Ubuntu NetworkManager[972]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
May 24 15:13:12 Ubuntu NetworkManager[972]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
May 24 15:13:12 Ubuntu NetworkManager[972]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
May 24 15:13:12 Ubuntu NetworkManager[972]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
May 24 15:13:12 Ubuntu NetworkManager[972]: <info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0]
May 24 15:13:12 Ubuntu NetworkManager[972]: <info> Activation (wlan0/wireless): access point 'WirelessNetwork' has security, but secrets are required.
May 24 15:13:12 Ubuntu NetworkManager[972]: <info> (wlan0): device state change: config -> need-auth (reason 'none') [50 60 0]
May 24 15:13:12 Ubuntu NetworkManager[972]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
May 24 15:13:12 Ubuntu NetworkManager[972]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
May 24 15:13:12 Ubuntu NetworkManager[972]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
May 24 15:13:12 Ubuntu NetworkManager[972]: <info> (wlan0): device state change: need-auth -> prepare (reason 'none') [60 40 0]
May 24 15:13:12 Ubuntu NetworkManager[972]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
May 24 15:13:12 Ubuntu NetworkManager[972]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
May 24 15:13:12 Ubuntu NetworkManager[972]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
May 24 15:13:12 Ubuntu NetworkManager[972]: <info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0]
May 24 15:13:12 Ubuntu NetworkManager[972]: <info> Activation (wlan0/wireless): connection 'WirelessNetwork' has security, and secrets exist.  No new secrets needed.
May 24 15:13:12 Ubuntu NetworkManager[972]: <info> Config: added 'ssid' value 'WirelessNetwork'
May 24 15:13:12 Ubuntu NetworkManager[972]: <info> Config: added 'scan_ssid' value '1'
May 24 15:13:12 Ubuntu NetworkManager[972]: <info> Config: added 'key_mgmt' value 'WPA-PSK'
May 24 15:13:12 Ubuntu NetworkManager[972]: <info> Config: added 'psk' value '<omitted>'
May 24 15:13:12 Ubuntu NetworkManager[972]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
May 24 15:13:12 Ubuntu NetworkManager[972]: <info> Config: set interface ap_scan to 1
May 24 15:13:12 Ubuntu NetworkManager[972]: <info> (wlan0): supplicant interface state: disconnected -> scanning
May 24 15:13:38 Ubuntu NetworkManager[972]: <warn> Activation (wlan0/wireless): association took too long, failing activation.
May 24 15:13:38 Ubuntu NetworkManager[972]: <info> (wlan0): device state change: config -> failed (reason 'SSID not found') [50 120 53]
May 24 15:13:38 Ubuntu NetworkManager[972]: <warn> Activation (wlan0) failed for connection 'WirelessNetwork'
May 24 15:13:38 Ubuntu NetworkManager[972]: <info> (wlan0): device state change: failed -> disconnected (reason 'none') [120 30 0]
May 24 15:13:38 Ubuntu NetworkManager[972]: <info> (wlan0): deactivating device (reason 'none') [0]
May 24 15:13:38 Ubuntu NetworkManager[972]: <warn> Couldn't disconnect supplicant interface: This interface is not connected.
May 24 15:13:38 Ubuntu NetworkManager[972]: <warn> Couldn't disconnect supplicant interface: This interface is not connected.
May 24 15:13:38 Ubuntu NetworkManager[972]: <info> (wlan0): supplicant interface state: scanning -> inactive

```

---

### Post by Hadaka on 2013-05-24
ok, didnt like that one,what kind of computer is this?

---

### Post by JadarDev on 2013-05-24
It's just a desktop that I build a few years ago with a Core2Duo, RadeonHD6450, and 12Gb Ram.

---

### Post by Hadaka on 2013-05-24
ok, sounds like a nice machine..stuborn..but nice.
your card..is suppse to use the wl driver..lets go back to that
one more time..see if the tainted kernel messege is still happening.
please do..
you may get ..not found..
```
sudo apt-get --purge remove b43-fwcutter firmware-b43-installer
sudo apt-get --purge remove linux-firmware-nonfree
sudo apt-get update
```
then..
```
sudo apt-get install bcmwl-kernel-source
sudo modprobe wl
```
unplug the wired connection..boot and see what happens.
thanks.

---

### Post by JadarDev on 2013-05-24
Nope.. :( thanks

---

### Post by Hadaka on 2013-05-24
ok, well lets see if it got all the modules out it was
suppose to.
please post..
```
lsmod
```
thanks.

---

### Post by JadarDev on 2013-05-24
here. thanks :)

```

$ lsmod
Module                  Size  Used by
lib80211_crypt_tkip    17379  0 
wl                   3074449  0 
lib80211               14352  2 wl,lib80211_crypt_tkip
cfg80211              510937  1 wl
nls_utf8               12557  2 
hfsplus                88539  2 
rfcomm                 42641  0 
bnep                   18036  2 
bluetooth             228619  10 bnep,rfcomm
snd_hda_codec_hdmi     36913  1 
snd_hda_codec_realtek    78399  1 
snd_hda_intel          39619  3 
snd_usb_audio         140685  1 
snd_hda_codec         136453  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
snd_usbmidi_lib        24938  1 snd_usb_audio
snd_hwdep              13602  2 snd_usb_audio,snd_hda_codec
snd_pcm                97451  4 snd_usb_audio,snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
snd_seq_midi           13324  0 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_rawmidi            30180  2 snd_usbmidi_lib,snd_seq_midi
snd_seq                61554  2 snd_seq_midi_event,snd_seq_midi
ppdev                  17073  0 
coretemp               13355  0 
kvm_intel             132891  0 
kvm                   443165  1 kvm_intel
parport_pc             28152  1 
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              29425  2 snd_pcm,snd_seq
radeon                937749  3 
gpio_ich               13476  0 
ttm                    83187  1 radeon
snd                    68876  20 snd_hda_codec_realtek,snd_usb_audio,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_usbmidi_lib,snd_hda_codec,snd_hda_intel,snd_seq_device
drm_kms_helper         49394  1 radeon
drm                   286313  5 ttm,drm_kms_helper,radeon
mac_hid                13205  0 
psmouse                95870  0 
lpc_ich                17061  0 
i2c_algo_bit           13413  1 radeon
serio_raw              13215  0 
microcode              22881  0 
soundcore              12680  1 snd
lp                     17759  0 
parport                46345  3 lp,ppdev,parport_pc
pata_acpi              13038  0 
hid_generic            12540  0 
usbhid                 47074  0 
hid                   101002  2 hid_generic,usbhid
usb_storage            57204  2 
pata_jmicron           12758  0 
ahci                   25731  2 
libahci                31364  1 ahci
r8169                  67446  0 



```

---

### Post by Hadaka on 2013-05-24
The lsmod looks better than before, lets do..
```
sudo modprobe -rfv wl
sudo modprobe -v wl
dmesg | egrep 'wl|eth'
```
thanks.

---

### Post by JadarDev on 2013-05-24
here.

```

$ sudo modprobe -rfv wl
rmmod wl
rmmod cfg80211
$ sudo modprobe -v wl
insmod /lib/modules/3.8.0-19-generic/kernel/net/wireless/cfg80211.ko 
insmod /lib/modules/3.8.0-19-generic/updates/dkms/wl.ko 
$ dmesg | egrep 'wl|eth'
[    0.545756] r8169 0000:04:00.0 eth0: RTL8168c/8111c at 0xffffc90001826000, 6c:f0:49:04:d6:bd, XID 1c4000c0 IRQ 44
[    0.545759] r8169 0000:04:00.0 eth0: jumbo features [frames: 6128 bytes, tx checksumming: ko]
[   11.022971] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   11.731051] INFO @wl_cfg80211_attach : Registered CFG80211 phy
[   11.791902] eth1: Broadcom BCM4329 802.11 Hybrid Wireless Controller 6.20.155.1 (r326264)
[   12.617301] r8169 0000:04:00.0 eth0: link down
[   12.617322] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   12.617516] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   19.010061] r8169 0000:04:00.0 eth0: link up
[   19.010081] IPv6: ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[  720.689848] INFO @wl_cfg80211_attach : Registered CFG80211 phy
[  720.719636] eth1: Broadcom BCM4329 802.11 Hybrid Wireless Controller 6.20.155.1 (r326264)

```

---

### Post by Hadaka on 2013-05-24
ok, please do..
```
sudo ifconfig eth1 down
sudo ifconfig eth1 up
```
im running out of ideas..im goingto do more research.

---

### Post by JadarDev on 2013-05-24
Well, if you have helped me as much as you can, I should just go and buy an Atheros card..

---

### Post by Hadaka on 2013-05-24
Hi, the card should work, there are plenty of
the same card using ubuntu and working, I dont know
at this point if its a 13.04 issue as wl driver has had some
problems with the os. But, it all depends on the machine the
exact card and other possibilities,I will do some research, and
also have someone more knowledgable than i look at it.
thanks for hanging in there.

---

### Post by praseodym on 2013-05-24
Please be sure that the modules bcma (bus driver!!!), b43 and ssb are not blacklisted. Uninstall the STA driver:
```

sudo modprobe -rfv wl
sudo apt-get remove --purge bcmwl-kernel-source
sudo rm /etc/modprobe.d/blacklist-bcm43.conf
sudo rm /etc/modprobe.d/broadcom-sta-common.conf
sudo rm /etc/modprobe.d/broadcom-sta-dkms.conf 
```
and install this firmware file:
```

wget http://media.cdn.ubuntu-de.org/forum/attachments/04/32/2480236-Broadcom_Firmware.tar.gz 
sudo tar xvf 2480236-Broadcom_Firmware.tar.gz -C /lib/firmware/ 
```
Reboot and check:
```
lspci -nnk | grep -iA2 net
lsmod
iwconfig
dmesg | grep b43
```

---

### Post by JadarDev on 2013-05-24
So, that makes networks be discovered, but it won't connect to my network. the lwconfig sees it as an abg card not n. thanks :)

```

$ lspci -nnk | grep -iA2 net
04:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168 PCI Express Gigabit Ethernet controller [10ec:8168] (rev 02)
	Subsystem: Gigabyte Technology Co., Ltd Motherboard [1458:e000]
	Kernel driver in use: r8169
05:01.0 Network controller [0280]: Broadcom Corporation BCM4321 802.11b/g/n [14e4:4329] (rev 01)
	Subsystem: Netgear WN311B RangeMax Next 270 Mbps Wireless PCI Adapter [1385:7d00]
	Kernel driver in use: b43-pci-bridge
$ lsmod
Module                  Size  Used by
nls_utf8               12557  2 
hfsplus                88539  2 
vesafb                 13828  1 
arc4                   12615  2 
b43                   378642  0 
bcma                   41051  1 b43
mac80211              606457  1 b43
bnep                   18036  2 
rfcomm                 42641  0 
bluetooth             228619  10 bnep,rfcomm
ssb_hcd                12869  0 
cfg80211              510937  2 b43,mac80211
snd_hda_codec_hdmi     36913  1 
snd_hda_codec_realtek    78399  1 
snd_hda_intel          39619  3 
snd_usb_audio         140685  1 
snd_hda_codec         136453  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
snd_usbmidi_lib        24938  1 snd_usb_audio
snd_hwdep              13602  2 snd_usb_audio,snd_hda_codec
snd_pcm                97451  4 snd_usb_audio,snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
snd_seq_midi           13324  0 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_rawmidi            30180  2 snd_usbmidi_lib,snd_seq_midi
snd_seq                61554  2 snd_seq_midi_event,snd_seq_midi
binfmt_misc            17500  1 
ppdev                  17073  0 
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
coretemp               13355  0 
snd_timer              29425  2 snd_pcm,snd_seq
parport_pc             28152  1 
kvm_intel             132891  0 
kvm                   443165  1 kvm_intel
fglrx                5196509  108 
snd                    68876  20 snd_hda_codec_realtek,snd_usb_audio,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_usbmidi_lib,snd_hda_codec,snd_hda_intel,snd_seq_device
gpio_ich               13476  0 
amd_iommu_v2           19068  1 fglrx
psmouse                95870  0 
serio_raw              13215  0 
lpc_ich                17061  0 
microcode              22881  0 
soundcore              12680  1 snd
mac_hid                13205  0 
lp                     17759  0 
parport                46345  3 lp,ppdev,parport_pc
pata_acpi              13038  0 
hid_generic            12540  0 
usbhid                 47074  0 
hid                   101002  2 hid_generic,usbhid
usb_storage            57204  3 
ssb                    56748  2 b43,ssb_hcd
r8169                  67446  0 
pata_jmicron           12758  0 
ahci                   25731  2 
libahci                31364  1 ahci
$ iwconfig
eth0      no wireless extensions.


lo        no wireless extensions.


wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
$ dmesg | grep b43
[   13.066981] b43-phy0: Broadcom 4321 WLAN found (core revision 11)
[   13.108015] b43-phy0: Found PHY: Analog 5, Type 4 (N), Revision 1
[   13.504025] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[   13.598052] b43-phy0 ERROR: Fatal DMA error: 0x00000400, 0x00000000, 0x00000000, 0x00000000, 0x00000000, 0x00000000
[   13.598107] b43-phy0 ERROR: This device does not support DMA on your system. It will now be switched to PIO.
[   13.598151] b43-phy0: Controller RESET (DMA error) ...
[   13.808021] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[   13.880052] b43-phy0 warning: Forced PIO by use_pio module parameter. This should not be needed and will result in lower performance.
[   13.900513] b43-phy0: Controller restarted

```

---

### Post by praseodym on 2013-05-25
Change the mode to b+g+n in the router interface

---

### Post by JadarDev on 2013-05-25
It's automatic. There is a/n and b/g and automatic.

---

### Post by JadarDev on 2013-05-27
Thanks soo much for helping and trying to get my card working. But I just ordered a new one that is sure to work. Its one that runs on an Atheros chip and it will work out of the box for all 3 of my OS(s). Thanks again for the help. :D

---

