---
title: "Broadcom BCM4322"
date: 2013-06-20
forum: Networking &amp; Wireless
---

### Post by Newb987 on 2013-06-20
Hi,

I just installed ubuntu desktop on my laptop last night. I was previously working off of Windows 7, which supported my wireless card just fine and, when I switch back to Windows, still works just fine. Ubuntu loaded on my system without any glitches and recognizes my bluetooth and other hardware. It just doesn't seem to like my wifi card. Under system settings under hardware it lists addtional hardware. When I open the additional hardware, it list Broadcom STA wireless driver. When I tell it to activate it tells me that the installation of the driver failed and that I need to look at the log file for details: /var/log/jockey.log.

I opened the log file but I don't have a background in programming and it all looks like giberish to me.

Any advice would be much apperciated.

---

### Post by chili555 on 2013-06-20
'Additional Drivers' sometimes offers to install the wrong driver for some Broadcom cards. Let's just confirm what you have before we proceed. Please open a terminal Ctrl+Alt+t and run and post:```
lspci -nn -d 14e4:
```Thanks.

---

### Post by Newb987 on 2013-06-21
Thanks for the quick reply.

So I did as you said and this is what I got:

07:00.0 Network Controller [0280]: Broadcom Corporation BCM4322 802.11a/b/g/n Wireless LAN Controller [14e4:4326] (rev 01)

---

### Post by praseodym on 2013-06-21
Hi,

try to install the driver via terminal, cable connection is needed:
```

sudo apt-get install --reinstall linux-headers-$(uname -r) linux-headers-generic build-essential dkms bcmwl-kernel-source
```
Reboot.

---

### Post by Newb987 on 2013-06-21
praseodym, I tried it and it install updates but I still don't have wireless.

---

### Post by praseodym on 2013-06-22
Did you activate it (again)? Please check:
```

lspci -nnk | grep -iA2 net
lsmod
iwconfig
rfkill list
sudo iwlist scan
```

---

### Post by Newb987 on 2013-06-23
Thanks for your help, but no success again.

lspci -nnk | grep -iA2 net showed both my ethernet controller and my broadcom wireless controller.

lsmod showed a list of stuff that I don't really understand.

iwconfig showed that eth0 and lo both have no wireless extensions.

rfkill list showed that my bluetooth isn't block soft or hard (which my bluetooth works fine).

And sudo iwlist scan showed that eth0 and lo interface don't support scanning.

Any other advice?

---

### Post by praseodym on 2013-06-23
Please c/p these outputs into a text file and show us the content for "analysis"

---

### Post by Newb987 on 2013-06-23
K, this is what comes up:

```
lucinda@ubuntu:~$ lspci -nnk | grep -iA2 net
00:0a.0 Ethernet controller [0200]: NVIDIA Corporation MCP79 Ethernet [10de:0ab0] (rev b1)
    Subsystem: Dell Device [1028:02a1]
    Kernel driver in use: forcedeth
--
07:00.0 Network controller [0280]: Broadcom Corporation BCM4322 802.11a/b/g/n Wireless LAN Controller [14e4:432b] (rev 01)
    Subsystem: Broadcom Corporation Device [14e4:04b1]
    Kernel modules: ssb
lucinda@ubuntu:~$ lsmod
Module                  Size  Used by
nouveau               924024  3 
ttm                    88495  1 nouveau
drm_kms_helper         49259  1 nouveau
drm                   290344  5 nouveau,ttm,drm_kms_helper
ir_lirc_codec          12860  0 
lirc_dev               19205  1 ir_lirc_codec
parport_pc             32867  0 
ppdev                  17114  0 
lp                     17800  0 
parport                46563  3 parport_pc,ppdev,lp
ir_mce_kbd_decoder     12778  0 
snd_hda_codec_idt      70774  1 
joydev                 17694  0 
ir_sanyo_decoder       12514  0 
rfcomm                 47562  12 
bnep                   18240  2 
ir_sony_decoder        12511  0 
ir_jvc_decoder         12508  0 
coretemp               13642  0 
kvm                   422160  0 
ir_rc6_decoder         12508  0 
i2c_algo_bit           13565  1 nouveau
btusb                  22432  0 
ir_rc5_decoder         12508  0 
bluetooth             211812  24 rfcomm,bnep,btusb
dell_wmi               12682  0 
sparse_keymap          13891  1 dell_wmi
ir_nec_decoder         12508  0 
mxm_wmi                13022  1 nouveau
rc_rc6_mce             12503  0 
video                  19598  1 nouveau
wmi                    19257  3 nouveau,dell_wmi,mxm_wmi
snd_hda_intel          34117  3 
snd_hda_codec         135141  2 snd_hda_codec_idt,snd_hda_intel
snd_hwdep              17765  1 snd_hda_codec
snd_pcm                97523  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13325  0 
snd_rawmidi            30750  1 snd_seq_midi
ite_cir                25777  0 
rc_core                26423  11 ir_lirc_codec,ir_mce_kbd_decoder,ir_sanyo_decoder,ir_sony_decoder,ir_jvc_decoder,ir_rc6_decoder,ir_rc5_decoder,ir_nec_decoder,rc_rc6_mce,ite_cir
snd_seq_midi_event     14900  1 snd_seq_midi
snd_seq                61931  2 snd_seq_midi,snd_seq_midi_event
r852                   18282  0 
sm_common              16861  1 r852
nand                   54999  2 r852,sm_common
nand_ids               12724  1 nand
mtd                    44946  2 sm_common,nand
nand_bch               13148  1 nand
bch                    22064  1 nand_bch
snd_timer              29990  2 snd_pcm,snd_seq
snd_seq_device         14498  3 snd_seq_midi,snd_rawmidi,snd_seq
r592                   18145  0 
memstick               16606  1 r592
snd                    83674  15 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
nand_ecc               13274  1 nand
uvcvideo               78117  0 
psmouse               102075  0 
videobuf2_core         33025  1 uvcvideo
microcode              23030  0 
videodev              125126  2 uvcvideo,videobuf2_core
soundcore              15092  1 snd
videobuf2_vmalloc      12861  1 uvcvideo
shpchp                 37278  0 
snd_page_alloc         18573  2 snd_hda_intel,snd_pcm
mac_hid                13254  0 
videobuf2_memops       13405  1 videobuf2_vmalloc
i2c_nforce2            13059  0 
serio_raw              13216  0 
hid_generic            12541  0 
usbhid                 47259  0 
hid                   100815  2 hid_generic,usbhid
sdhci_pci              18749  0 
sdhci                  33145  1 sdhci_pci
firewire_ohci          41034  0 
firewire_core          64697  1 firewire_ohci
crc_itu_t              12708  1 firewire_core
forcedeth              67947  0 
lucinda@ubuntu:~$ iwconfig
eth0      no wireless extensions.

lo        no wireless extensions.

lucinda@ubuntu:~$ rfkill list
0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
lucinda@ubuntu:~$ sudo iwlist scan
[sudo] password for lucinda: 
eth0      Interface doesn't support scanning.

lo        Interface doesn't support scanning.
```

---

### Post by praseodym on 2013-06-23
The driver is activated in "additional drivers"? Try to load it by hand
```

sudo modprobe -v wl
iwconfig
sudo iwlist scan
route -n
```

---

### Post by Newb987 on 2013-06-23
No go:
```

lucinda@ubuntu:~$ sudo modprobe -v wl
[sudo] password for lucinda: 
FATAL: Module wl not found.
lucinda@ubuntu:~$ iwconfig
eth0      no wireless extensions.

lo        no wireless extensions.

lucinda@ubuntu:~$ sudo iwlist scan
eth0      Interface doesn't support scanning.

lo        Interface doesn't support scanning.

lucinda@ubuntu:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
192.168.0.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0
```

---

### Post by praseodym on 2013-06-23
Obviously the installation from above did not work?!

---

### Post by Hadaka on 2013-06-23
Hi, give this a try..
please copy and paste the following
into a terminal input..
```
sudo apt-get remove --purge bcmwl-kernel-source
```
you may get a "not found" on the above..this is ok
then do.
```
sudo modprobe -rf ssb
sudo apt-get install linux-firmware-nonfree
sudo modprobe b43
```
boot and report back please.
thanks.

---

### Post by Newb987 on 2013-06-23
Did as you said. The wireless still doesn't work.

@ everyone and anyone: If I post the /var/log/jockey.log file, which I'm told to look at every time I try to activate my wifi card, could someone analyse what it actually says? It's pretty long.

---

### Post by chili555 on 2013-06-23
> **Newb987 said:**
> Did as you said. The wireless still doesn't work.

@ everyone and anyone: If I post the /var/log/jockey.log file, which I'm told to look at every time I try to activate my wifi card, could someone analyse what it actually says? It's pretty long.I suggest you paste it here and give us the link in your reply.  [http://paste.ubuntu.com/](http://paste.ubuntu.com/)

---

### Post by Newb987 on 2013-06-23
Did as you suggested chili555.

Here's the link to the var/log/jockey.log file: [link]("http://paste.ubuntu.com/5794058/")

---

### Post by chili555 on 2013-06-24
The parts relevant to our case are quoted here:> 2013-06-23 14:56:01,031 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'wl', 'package': 'bcmwl-kernel-source'}
2013-06-23 14:56:01,031 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2013-06-23 14:56:01,031 DEBUG: found match in handler pool kmod:wl([BroadcomWLHandler, nonfree, disabled] Broadcom STA wireless driver)
2013-06-23 14:56:01,035 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2013-06-23 14:56:01,035 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2013-06-23 14:56:01,035 DEBUG: got handler kmod:wl([BroadcomWLHandler, nonfree, disabled] Broadcom STA wireless driver)
2013-06-23 14:56:01,036 DEBUG: searching handler for driver ID {'driver_type': 'kernel_module', 'kernel_module': 'ssb'}
2013-06-23 14:56:01,036 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ssb', 'jockey_handler': 'KernelModuleHandler'}Studying....

---

### Post by chili555 on 2013-06-24
I'd like to understand what is or isn't happening as you try to reinstall bcmwl-kernel-source. Logs! We need logs! This won't really help us:> Did as you said. The wireless still doesn't work.As you take each of the following steps, copy and paste the terminal output to a text document ('Text Editor') and paste it in your reply or in paste.ubuntu.com as above. We need juicy details! 

This also won't help us; from post #3:> Broadcom Corporation BCM4322 802.11a/b/g/n Wireless LAN Controller [14e4:432[COLOR="#FF0000"]6[/COLOR]] (rev 01) But then from post #9:> Broadcom Corporation BCM4322 802.11a/b/g/n Wireless LAN Controller [14e4:432[COLOR="#FF0000"]b[/COLOR]]I understand that people make typographical errors; I'me mage a fwe even tuday. However, please copy and paste so that we have accurate information to work from.

First,let's find out the status of the parts needed to install bcmwl-kernel-source:```
sudo dpkg -s linux-headers-generic | head -n5
sudo dpkg -s linux-headers-$(uname -r) | head -n5
sudo dpkg -s bcmwl-kernel-source | head -n5
```Now let's back up your current log:```
sudo mv  /var/log/jockey.log  /var/log/jockey.log.bak
```Now let's try to re-install the driver and see what happens and then read the new log:```
sudo apt-get install --reinstall bcmwl-kernel-source
```Now paste the newly created /var/log/jockey.log into paste.ubuntu.com and give us a link.

Hopefully, we will see what's going wrong here and fix it.

Details! Logs!! Data!!!

---

### Post by Newb987 on 2013-06-24
Status:

```
lucinda@ubuntu:~$ sudo dpkg -s linux-headers-generic | head -n5
[sudo] password for lucinda: 
Package: linux-headers-generic
Status: install ok installed
Priority: optional
Section: devel
Installed-Size: 31
lucinda@ubuntu:~$ sudo dpkg -s linux-headers-$(uname -r) | head -n5
Package: linux-headers-3.5.0-23-generic
Status: install ok installed
Priority: optional
Section: devel
Installed-Size: 10957
lucinda@ubuntu:~$ sudo dpkg -s bcmwl-kernel-source | head -n5
Package `bcmwl-kernel-source' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
```

Backed up /var/log/jockey.log:

```
lucinda@ubuntu:~$ sudo mv /var/log/jockey.log /var/log/jockey.log.bak
```

Reinstalled bcmwl-kernel-source:

```
lucinda@ubuntu:~$ sudo apt-get install --reinstall bcmwl-kernel-source
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  bcmwl-kernel-source
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0 B/1,151 kB of archives.
After this operation, 3,514 kB of additional disk space will be used.
Selecting previously unselected package bcmwl-kernel-source.
(Reading database ... 166256 files and directories currently installed.)
Unpacking bcmwl-kernel-source (from .../bcmwl-kernel-source_5.100.82.38+bdcom-0ubuntu6_amd64.deb) ...
Setting up bcmwl-kernel-source (5.100.82.38+bdcom-0ubuntu6) ...
Loading new bcmwl-5.100.82.38+bdcom DKMS files...
First Installation: checking all kernels...
Building only for 3.5.0-23-generic
Building for architecture x86_64
Building initial module for 3.5.0-23-generic
ERROR (dkms apport): kernel package linux-headers-3.5.0-23-generic is not supported
Error! Bad return status for module build on kernel: 3.5.0-23-generic (x86_64)
Consult /var/lib/dkms/bcmwl/5.100.82.38+bdcom/build/make.log for more information.
update-initramfs: deferring update (trigger activated)
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.5.0-23-generic
Warning: No support for locale: en_US.utf8
```

---

### Post by Newb987 on 2013-06-24
Okay, so I rebooted my computer and tried to find the /var/log/jockey.log file, but I don't have one. Should I try installing my wifi card through Additional Drivers again?

---

### Post by chili555 on 2013-06-24
Not yet. Please see:> ERROR (dkms apport): kernel package linux-headers-3.5.0-23-generic is not supportedHere is a post with the same problem: [http://ubuntuforums.org/showthread.php?t=2143125](http://ubuntuforums.org/showthread.php?t=2143125)  Please see and follow post #9.

---

### Post by Newb987 on 2013-06-24
@Everyone, especially Chili555

Thank you so much for your time and all your help. I now have wireless internet. Chili555 you made my day!

---

### Post by chili555 on 2013-06-24
Awesome! Great news.

---

