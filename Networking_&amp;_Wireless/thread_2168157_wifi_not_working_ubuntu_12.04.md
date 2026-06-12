---
title: "wifi not working ubuntu 12.04"
date: 2013-08-16
forum: Networking &amp; Wireless
---

### Post by inderjeet2 on 2013-08-16
WiFi is not working for my Ubuntu installed on windows7 however its working when shifting to windows environment. I have dual operating system on my machine.
Here are outputs of few commands:
**lshw -C Network:**
*-network UNCLAIMED
       description: Network controller
       product: BCM43228 802.11a/b/g/n
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:f7e00000-f7e03fff

  ***-network**
       description: Ethernet interface
       product: NetXtreme BCM5761 Gigabit Ethernet PCIe
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       logical name: eth0
       version: 10
       serial: b8:ca:3a:c4:3f:dd
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.123 firmware=5761-v3.80 latency=0 link=no multicast=yes port=twisted pair
       resources: irq:44 memory:f7c10000-f7c1ffff memory:f7c00000-f7c0ffff


Output of: 
**_rfkill list all:_**
0: hci0: Bluetooth
          Soft blocked: no
          Hard blocked: no

Output of:
_i**fconfig**_
eth0             
Link encap:Ethernet HWaddr b8:ca:3a:c4:3f:dd
                   UP BROADCAST MULTICAST MTU:1500 Metric:1
                   RX packets:0 errors:0 dropped:0 overruns:0 frame:0
                   TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
                   collisions:0 txqueuelen:1000
                   RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)
                   Interrupt:18
lo
                   Link encap:Local Loopback
                   inet addr:127.0.0.1 Mask:255.0.0.0
                   inet6 addr: ::1/128 Scope:Host
                   UP LOOPBACK RUNNING MTU:16436 Metric:1
                   RX packets:6446 errors:0 dropped:0 overruns:0 frame:0
                   TX packets:6446 errors:0 dropped:0 overruns:0 carrier:0
                   collisions:0 txqueuelen:1000
                   RX bytes:3821480 (3.8 MB) TX bytes:3821480 (3.8 MB)

Output for: 
**lspci -nn | grep 0280**
02:00.0 Network controller [0280]: Broadcom Corporation BCM43228 802.11a/b/g/n [14e4:4359]

output for 
cat /etc/network/interfaces
auto lo
iface lo inet loopback

Please help me to sort out this issue. I am stuck up from a long......

Thanks
Inderjeet

---

### Post by Hadaka on 2013-08-16
Hi, give this a try
```
sudo apt-get install linux-headers-generic
sudo apt-get install --reinstall bcmwl-kernel-source
sudo modprobe wl
```
BOOT
*if that doesnt help ..please post..
```
lsmod
```
thanks.

---

### Post by inderjeet2 on 2013-08-16
Command: [B]sudo apt-get install linux-headers-generic
[/B]
sudo apt get install: command not found

command: **lsmod**

Module                  Size  Used by
snd_hda_codec_hdmi     31778  1 
snd_hda_codec_idt      60238  1 
coretemp               13362  0 
kvm_intel             127736  0 
kvm                   365556  1 kvm_intel
aesni_intel            17979  0 
cryptd                 19822  1 aesni_intel
aes_i586               16996  1 aesni_intel
rfcomm                 38104  12 
bnep                   17791  2 
ppdev                  12850  0 
dell_wmi               12602  0 
sparse_keymap          13659  1 dell_wmi
dell_laptop            17210  0 
dcdbas                 14099  1 dell_laptop
microcode              18396  0 
snd_hda_intel          33029  3 
snd_hda_codec         116477  3 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13277  1 snd_hda_codec
psmouse                91022  0 
serio_raw              13032  0 
snd_pcm                81124  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
uvcvideo               72249  0 
videobuf2_core         32212  1 uvcvideo
videodev              100265  2 uvcvideo,videobuf2_core
videobuf2_vmalloc      12757  1 uvcvideo
videobuf2_memops       13213  1 videobuf2_vmalloc
snd_seq_midi           13133  0 
snd_rawmidi            25426  1 snd_seq_midi
snd_seq_midi_event     14476  1 snd_seq_midi
btusb                  17952  0 
snd_seq                51594  2 snd_seq_midi,snd_seq_midi_event
bluetooth             189585  24 rfcomm,bnep,btusb
parport_pc             32115  0 
wmi                    18745  1 dell_wmi
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14138  3 snd_seq_midi,snd_rawmidi,snd_seq
lpc_ich                16993  0 
snd                    62675  16 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              14636  1 snd
snd_page_alloc         14109  2 snd_hda_intel,snd_pcm
i915                  470823  3 
drm_kms_helper         47459  1 i915
drm                   240232  4 i915,drm_kms_helper
i2c_algo_bit           13317  1 i915
video                  19070  1 i915
mei                    36404  0 
mac_hid                13078  0 
lp                     17456  0 
parport                40931  3 ppdev,parport_pc,lp
tg3                   141717  0 
sdhci_pci              18263  0 
sdhci                  32293  1 sdhci_pci

---

### Post by Hadaka on 2013-08-16
Hi, you may have made a typo, please COPY and paste
one line at a time
```
sudo apt-get install linux-headers-generic
sudo apt-get install bcmwl-kernel-source
sudo modprobe wl
```
thanks.

---

### Post by inderjeet2 on 2013-08-16
Thanks
May be I have typo mistake:
output of:**sudo apt-get install linux-headers-generic**
Reading package lists.... Done
Building dependency tree
Reading state information... Done
E: unable to locate package linux-headers-generic

---

### Post by Hadaka on 2013-08-16
great !...ok now copy and paste this...
```
sudo apt-get update
sudo apt-get upgrade
```
this may take some time...so be patient.
then..boot.
wireless should be working
thanks.

---

### Post by inderjeet2 on 2013-08-16
It seems it require internet connection and I do not have any internet connection other than this wifi...
**sudo apt-get update** : end up with many:- Failed to fetch..... statements.
and
**sudo apt-get upgrade** : ends up with:- 
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Just to bring back to you knowledge:
**sudo apt-get install linux-headers-generic: **end up with the line
E: unable to locate package linux-headers-generic

---

### Post by Hadaka on 2013-08-16
OK, you should have stated NO internet connection in the first post.
Am i correct you have no wired or wireless connection?
have you tried turning the router off then back on as well as the computer?

---

### Post by inderjeet2 on 2013-08-18
Am i correct you have no wired or wireless connection?
Yes you are correct.
have you tried turning the router off then back on as well as the computer?
How to turn off the router because I am not using any external route, If you are talking about inbuilt router I do not know how to turn off or on.  Please let me know.

---

