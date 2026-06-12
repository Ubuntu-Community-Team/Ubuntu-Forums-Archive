---
title: "HP Pavilion dv5 1290 - Broadcom BCM4312"
date: 2013-03-18
forum: Networking &amp; Wireless
---

### Post by na4evbg on 2013-03-18
Hi, i'm sorry if there is another threads like mine, but i'm really new with the Ubuntu and i don't know what to do and where else to ask. I just installed Ubuntu 12.10 on my HP Pavilion dv5 1290-eq, but i got a internet problem, i can't find any wi-fi connections and ubuntu says (there comes a pop-up massage) that my Wi-Fi is turned off or disabled or something like that.
I'll be very greatful if somebody can help me. :)))

---

### Post by praseodym on 2013-03-18
Hi,

please open a terminal with CTRL+ALT+T and show the outputs of these commands:
```

lspci -nnk
lsusb
lsmod
iwconfig
rfkill list
```
Any button/switch/key/key combination to turn on the wifi? Do you have a cable connection?

---

### Post by na4evbg on 2013-03-18
```
na4ev@ubuntu:~$ lspci -vvn | grep 14e4
02:00.0 0280: 14e4:4315 (rev 01)
na4ev@ubuntu:~$ lspcu -vvn
No command 'lspcu' found, did you mean:
 Command 'lscpu' from package 'util-linux' (main)
 Command 'lspci' from package 'pciutils' (main)
lspcu: command not found
```
```
na4ev@ubuntu:~$ lspci -vvnn | grep 14e4
02:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01)
```
```
na4ev@ubuntu:~$ clear
na4ev@ubuntu:~$ uname -r
3.5.0-17-generic
na4ev@ubuntu:~$ dpkg -l | grep heders
na4ev@ubuntu:~$ dpkg -l | grep headers
ii  linux-generic                             3.5.0.17.19                               amd64        Complete Generic Linux kernel and headers
ii  linux-headers-3.5.0-17                    3.5.0-17.28                               all          Header files related to Linux kernel version 3.5.0
ii  linux-headers-3.5.0-17-generic            3.5.0-17.28                               amd64        Linux kernel headers for version 3.5.0 on 64 bit x86 SMP
ii  linux-headers-generic                     3.5.0.17.19                               amd64        Generic Linux kernel headers
na4ev@ubuntu:~$ home /na4ev/pool/main/d/dkms
No command 'home' found, did you mean:
 Command 'hime' from package 'hime' (universe)
 Command 'hose' from package 'netpipes' (universe)
 Command 'tome' from package 'tome' (multiverse)
home: command not found
na4ev@ubuntu:~$ dc /cdrom/pool/main/d/dkms
dc: Could not open file /cdrom/pool/main/d/dkms
na4ev@ubuntu:~$ cd /cdrom/pool/main/d/dkms
bash: cd: /cdrom/pool/main/d/dkms: No such file or directory
na4ev@ubuntu:~$ cd /home/na4ev/pool/main/d/dkms
bash: cd: /home/na4ev/pool/main/d/dkms: No such file or directory
na4ev@ubuntu:~$ clear
```


```
na4ev@ubuntu:~$ lspci -nnk
00:00.0 Host bridge [0600]: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub [8086:2a40] (rev 07)
    Subsystem: Hewlett-Packard Company Device [103c:3603]
00:01.0 PCI bridge [0604]: Intel Corporation Mobile 4 Series Chipset PCI Express Graphics Port [8086:2a41] (rev 07)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:1a.0 USB controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 [8086:2937] (rev 03)
    Subsystem: Hewlett-Packard Company Device [103c:3603]
    Kernel driver in use: uhci_hcd
00:1a.1 USB controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 [8086:2938] (rev 03)
    Subsystem: Hewlett-Packard Company Device [103c:3603]
    Kernel driver in use: uhci_hcd
00:1a.7 USB controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 [8086:293c] (rev 03)
    Subsystem: Hewlett-Packard Company Device [103c:3603]
    Kernel driver in use: ehci_hcd
00:1b.0 Audio device [0403]: Intel Corporation 82801I (ICH9 Family) HD Audio Controller [8086:293e] (rev 03)
    Subsystem: Hewlett-Packard Company Device [103c:3621]
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd-hda-intel
00:1c.0 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 [8086:2940] (rev 03)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:1c.1 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 [8086:2942] (rev 03)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:1c.2 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 [8086:2944] (rev 03)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:1c.3 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 [8086:2946] (rev 03)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:1c.4 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 [8086:2948] (rev 03)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:1c.5 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 [8086:294a] (rev 03)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:1d.0 USB controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 [8086:2934] (rev 03)
    Subsystem: Hewlett-Packard Company Device [103c:3603]
    Kernel driver in use: uhci_hcd
00:1d.1 USB controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 [8086:2935] (rev 03)
    Subsystem: Hewlett-Packard Company Device [103c:3603]
    Kernel driver in use: uhci_hcd
00:1d.2 USB controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 [8086:2936] (rev 03)
    Subsystem: Hewlett-Packard Company Device [103c:3603]
    Kernel driver in use: uhci_hcd
00:1d.3 USB controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 [8086:2939] (rev 03)
    Subsystem: Hewlett-Packard Company Device [103c:3603]
    Kernel driver in use: uhci_hcd
00:1d.7 USB controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 [8086:293a] (rev 03)
    Subsystem: Hewlett-Packard Company Device [103c:3603]
    Kernel driver in use: ehci_hcd
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev 93)
00:1f.0 ISA bridge [0601]: Intel Corporation ICH9M LPC Interface Controller [8086:2919] (rev 03)
    Subsystem: Hewlett-Packard Company Device [103c:3603]
    Kernel modules: lpc_ich
00:1f.2 SATA controller [0106]: Intel Corporation 82801IBM/IEM (ICH9M/ICH9M-E) 4 port SATA Controller [AHCI mode] [8086:2929] (rev 03)
    Subsystem: Hewlett-Packard Company Device [103c:3603]
    Kernel driver in use: ahci
00:1f.3 SMBus [0c05]: Intel Corporation 82801I (ICH9 Family) SMBus Controller [8086:2930] (rev 03)
    Subsystem: Hewlett-Packard Company Device [103c:3603]
    Kernel modules: i2c-i801
00:1f.6 Signal processing controller [1180]: Intel Corporation 82801I (ICH9 Family) Thermal Subsystem [8086:2932] (rev 03)
    Subsystem: Hewlett-Packard Company Device [103c:3603]
01:00.0 VGA compatible controller [0300]: NVIDIA Corporation G96 [GeForce 9600M GT] [10de:0649] (rev a1)
    Subsystem: Hewlett-Packard Company Device [103c:3603]
    Kernel driver in use: nouveau
    Kernel modules: nouveau, nvidiafb
02:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01)
    Subsystem: Hewlett-Packard Company BCM4312 802.11b/g Wireless LAN Controller [103c:137d]
    Kernel driver in use: b43-pci-bridge
    Kernel modules: ssb
03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 02)
    Subsystem: Hewlett-Packard Company Device [103c:3603]
    Kernel driver in use: r8169
    Kernel modules: r8169
06:00.0 FireWire (IEEE 1394) [0c00]: JMicron Technology Corp. IEEE 1394 Host Controller [197b:2380]
    Subsystem: Hewlett-Packard Company Device [103c:3603]
    Kernel driver in use: firewire_ohci
    Kernel modules: firewire-ohci
06:00.1 System peripheral [0880]: JMicron Technology Corp. SD/MMC Host Controller [197b:2382]
    Subsystem: Hewlett-Packard Company Device [103c:3603]
    Kernel driver in use: sdhci-pci
    Kernel modules: sdhci-pci
06:00.2 SD Host controller [0805]: JMicron Technology Corp. Standard SD Host Controller [197b:2381]
    Subsystem: Hewlett-Packard Company Device [103c:3603]
    Kernel modules: sdhci-pci
06:00.3 System peripheral [0880]: JMicron Technology Corp. MS Host Controller [197b:2383]
    Subsystem: Hewlett-Packard Company Device [103c:3603]
    Kernel driver in use: jmb38x_ms
    Kernel modules: jmb38x_ms
06:00.4 System peripheral [0880]: JMicron Technology Corp. xD Host Controller [197b:2384]
    Subsystem: Hewlett-Packard Company Device [103c:3603]
```
```
na4ev@ubuntu:~$ lsusb
Bus 001 Device 002: ID 3538:0901 Power Quotient International Co., Ltd 
Bus 002 Device 003: ID 5986:0137 Acer, Inc 
Bus 006 Device 002: ID 138a:0001 Validity Sensors, Inc. VFS101 Fingerprint Reader
Bus 007 Device 002: ID 03f0:171d Hewlett-Packard Bluetooth 2.0 Interface [Broadcom BCM2045]
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```
```
na4ev@ubuntu:~$ lsmod
Module                  Size  Used by
nls_iso8859_1          12713  1 
usb_storage            48838  1 
uas                    17844  0 
coretemp               13400  0 
kvm                   414070  0 
snd_hda_codec_hdmi     32007  1 
snd_hda_codec_idt      70209  1 
snd_hda_intel          33491  3 
snd_hda_codec         134212  3 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13602  1 snd_hda_codec
joydev                 17457  0 
snd_pcm                96580  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
uvcvideo               76749  0 
videobuf2_core         32851  1 uvcvideo
videodev              120309  2 uvcvideo,videobuf2_core
videobuf2_vmalloc      12860  1 uvcvideo
snd_seq_midi           13324  0 
videobuf2_memops       13368  1 videobuf2_vmalloc
microcode              22803  0 
ir_lirc_codec          12859  0 
lirc_dev               19166  1 ir_lirc_codec
ir_mce_kbd_decoder     12723  0 
ir_sanyo_decoder       12513  0 
ir_sony_decoder        12510  0 
ir_jvc_decoder         12507  0 
parport_pc             32688  0 
ir_rc6_decoder         12507  0 
ir_rc5_decoder         12507  0 
ir_nec_decoder         12507  0 
ppdev                  17073  0 
bnep                   18140  2 
rfcomm                 46619  12 
rc_rc6_mce             12502  0 
lp                     17759  0 
parport                46345  3 parport_pc,ppdev,lp
ene_ir                 18320  0 
psmouse                95552  0 
btusb                  18334  0 
rc_core                22330  11 ir_lirc_codec,ir_mce_kbd_decoder,ir_sanyo_decoder,ir_sony_decoder,ir_jvc_decoder,ir_rc6_decoder,ir_rc5_decoder,ir_nec_decoder,rc_rc6_mce,ene_ir
serio_raw              13215  0 
b43                   369753  0 
snd_rawmidi            30512  1 snd_seq_midi
bluetooth             209199  22 bnep,rfcomm,btusb
mac80211              539908  1 b43
snd_seq_midi_event     14899  1 snd_seq_midi
nouveau               895609  3 
hp_accel               25976  0 
ttm                    83595  1 nouveau
lis3lv02d              19829  1 hp_accel
input_polldev          13896  1 lis3lv02d
drm_kms_helper         46784  1 nouveau
cfg80211              206566  2 b43,mac80211
drm                   275528  5 nouveau,ttm,drm_kms_helper
i2c_algo_bit           13413  1 nouveau
mxm_wmi                12979  1 nouveau
jmb38x_ms              17416  0 
snd_seq                61521  2 snd_seq_midi,snd_seq_midi_event
memstick               16554  1 jmb38x_ms
bcma                   35656  1 b43
video                  19335  1 nouveau
mac_hid                13205  0 
wmi                    19070  2 nouveau,mxm_wmi
snd_timer              29425  2 snd_pcm,snd_seq
snd_seq_device         14497  3 snd_seq_midi,snd_rawmidi,snd_seq
lpc_ich                17061  0 
snd                    78734  16 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              15047  1 snd
snd_page_alloc         18484  2 snd_hda_intel,snd_pcm
sdhci_pci              18616  0 
sdhci                  32645  1 sdhci_pci
firewire_ohci          40401  0 
ssb                    52036  1 b43
r8169                  61650  0 
firewire_core          64368  1 firewire_ohci
crc_itu_t              12707  1 firewire_core
```
```
na4ev@ubuntu:~$ iwconfig
eth0      no wireless extensions.


lo        no wireless extensions.
```


```
na4ev@ubuntu:~$ rfkill list
0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
na4ev@ubuntu:~$

```

P.S. the first rows are some despered tryings of mine.
       thanks for the help btw :)

---

### Post by 23senick on 2013-03-18
Don't worry you'll get over this little setback.  Others will be able to help more technically, but my advice (based on slightly different HP laptop with different wireless card is to try different drivers).  Afraid Broadcom wireless cards are very common, but can take a bit of setting up in Ubuntu. Actually mine is temperamental in Windows!

Starting point I would suggest is this.  Will try to explain simply (sorry if too simple!).  You need a wired connection to your router to provide internet.  

Click on the top right icon, select system settings, then additional drivers (under the Hardware row). Wait and you will get a list of two or three (may only be one) proprietary drivers. This means they come from the manufacturer, not Ubuntu.  There will probably be one for your Broadcom wireless card (4312).  Select it by clicking on it, and at the bottom select activate. 

This will take a couple of minutes, and at the end it may not be very clear what has happened. But if you reboot you may well find wireless working. If it doesn't help you can always switch off the proprietary driver by de-selecting it.

Sometimes it may take a bit more work but there are lots of helpful people on this forum with loads of technical knowledge. Post the results if not working.  And once you've got Ubuntu running, you'll probably wonder why you sat waiting for windows to load, update virus software, shut down, etc etc

---

### Post by na4evbg on 2013-03-18
Thank you very much :)
There are 2 options "Using Broadcom 802.11 Linux STA wireless driver" and "Do not use the device". When i choose the "Using Broadcom 802.11...", then a go to "Apply Changes", there is like 10-20 seconds of loading and at the end... nothing is happening, It goes to "Do not use the device" by it self again.

---

### Post by varunendra on 2013-03-19
> **na4evbg said:**
> 
```
na4ev@ubuntu:~$ lspci -vvnn | grep 14e4
02:00.0 Network controller [0280]: Broadcom Corporation **BCM4312** 802.11b/g LP-PHY [**14e4:4315**] (rev 01)
```
While being connected via cable, please run following commands in terminal -
```
sudo apt-get purge bcmwl-kernel-source broadcom-sta-common broadcom-sta-source
sudo apt-get install b43-fwcutter firmware-b43-lpphy-installer
sudo modprobe -rfv b43
sudo modprobe -v b43
```

Disconnect the cable and try to connect via wireless. If required, do a restart.

Post back the result. Thanks!

---

### Post by na4evbg on 2013-03-19
I just tried, but i cannot set up a connection even via cable, it's kind a strange, i don't know really...

---

### Post by varunendra on 2013-03-19
> **na4evbg said:**
> I just tried, but i cannot set up a connection even via cable, it's kind a strange, i don't know really...

Please download the linux-firmware-nonfree package from here on a computer which has a working internet connection : [http://packages.ubuntu.com/precise/all/linux-firmware-nonfree/download](http://packages.ubuntu.com/precise/all/linux-firmware-nonfree/download)

Copy it back to the Ubuntu computer and double-click to install. Run the first line of command from my previous post -
```
sudo apt-get purge bcmwl-kernel-source broadcom-sta-common broadcom-sta-source
```
Reboot and let us know how it went.

---

### Post by na4evbg on 2013-03-19
```

na4ev@ubuntu:~/Desktop$ sudo apt-get purge bcmwl-kernel-source broadcom-sta-common broadcom-sta-source
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package 'broadcom-sta-common' is not installed, so not removed
Package 'broadcom-sta-source' is not installed, so not removed
The following packages will be REMOVED:
  bcmwl-kernel-source*
0 upgraded, 0 newly installed, 1 to remove and 2 not upgraded.
After this operation, 3,367 kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 148526 files and directories currently installed.)
Removing bcmwl-kernel-source ...
Removing all DKMS Modules (1)
Done.
update-initramfs: deferring update (trigger activated)
Purging configuration files for bcmwl-kernel-source ...
update-initramfs: deferring update (trigger activated)
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.5.0-17-generic
Warning: No support for locale: en_US.utf8
na4ev@ubuntu:~/Desktop$ ^C
na4ev@ubuntu:~/Desktop$ 

```

---

### Post by na4evbg on 2013-03-19
You can mark this thread as SOLVED, i'm proud of myself :D 
Second day using Ubuntu and resolve this problem all alone 
btw... the problem was in the driver, i installed b43 driver and everything now is alright

---

### Post by varunendra on 2013-03-19
> **na4evbg said:**
> You can mark this thread as SOLVED, i'm proud of myself :D 
Second day using Ubuntu and resolve this problem all alone 
btw... the problem was in the driver, i installed b43 driver and everything now is alright

Congratulations! You ought to be proud, but just so you know in case of future problems -

**1)** The b43 driver is a part of the kernel, you don't need to download it separately.

**2)** The sta driver you installed 'blacklists' the b43 driver, so it doesn't load even though it is present in the kernel. This is done to avoid conflicts.

**3)** The b43 driver needs a firmware which you do need to install separately, as it can't be distributed with Ubuntu. The package I asked you to download and install includes that firmware (among many others). So once installed, and the sta driver is removed, the wireless will work after a reboot or a module unload/load cycle.

I am marking the thread as  [Solved] as you requested, please follow the 'see how' link in my signature to see how to do it yourself. :)

Thanks for the feedback.
Enjoy!

---

