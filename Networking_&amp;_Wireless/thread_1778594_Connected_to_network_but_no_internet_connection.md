---
title: "Connected to network but no internet connection"
date: 2011-06-09
forum: Networking &amp; Wireless
---

### Post by coolinux on 2011-06-09
Connected to network but no internet connection

Hi Guys!
I'm  new to linux and this is my first installation. I hope you can help with my problem. I already done some config in network tools (applying IP manually). I can ping my other computer but I don't have internet connection. I'm using Ubuntu 10.10.

Thanks in Advance! ! !

---

### Post by poolet on 2011-06-09
Write the following code on terminal and paste the output here:::: 

```
ifconfig
```

```
lshw -C network
```

```
lspci | grep network 
``` if you don't get output just ```
lspci
```

```
lsmod | grep network
``` the same thing here if you don't get output  ```
lsmod
```

---

### Post by coolinux on 2011-06-09
Question Sir, how do I transfer my codes in linux to windows via network? Sorry I don't have so much experience in linux. Btw thanks for the reply.

---

### Post by syoung27 on 2011-06-09
your output? you could printscrn and share it over the network. or put it on a thumbdrive:)

---

### Post by poolet on 2011-06-09
i really don't understand your question... Just go to Applications -> Accessories -> Terminal 
and copy and paste each of the previous code on terminal. Each of this one it will be show you an output, just copy and paste the output here.....

---

### Post by coolinux on 2011-06-09
this is what i get

```
ifconfig 
eth0      Link encap:Ethernet  HWaddr 00:1e:90:b2:32:a1   
          inet addr:192.168.0.105  Bcast:192.168.0.255  Mask:255.255.255.0 
          inet6 addr: fe80::21e:90ff:feb2:32a1/64 Scope:Link 
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1 
          RX packets:208 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:42 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000 
          RX bytes:21202 (21.2 KB)  TX bytes:6966 (6.9 KB) 
          Interrupt:41 Base address:0xa000 

lo        Link encap:Local Loopback   
          inet addr:127.0.0.1  Mask:255.0.0.0 
          inet6 addr: ::1/128 Scope:Host 
          UP LOOPBACK RUNNING  MTU:16436  Metric:1 
          RX packets:1136 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:1136 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0 
          RX bytes:89336 (89.3 KB)  TX bytes:89336 (89.3 KB) 

```

```
lshw -C network 
*-network                
       description: Ethernet interface 
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller 
       vendor: Realtek Semiconductor Co., Ltd. 
       physical id: 0 
       bus info: pci@0000:02:00.0 
       logical name: eth0 
       version: 02 
       serial: 00:1e:90:b2:32:a1 
       width: 64 bits 
       clock: 33MHz 
       capabilities: bus_master cap_list rom ethernet physical 
       configuration: broadcast=yes driver=r8169 driverversion=2.3LK-NAPI ip=192.168.0.105 latency=0 multicast=yes 
       resources: irq:41 ioport:e800(size=256) memory:febff000-febfffff memory:fdff0000-fdffffff memory:febc0000-febdffff 

```

```
lspci 
00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge 
00:01.0 PCI bridge: Elitegroup Computer Systems Device 9602 
00:07.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 3) 
00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [IDE mode] 
00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller 
00:12.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller 
00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller 
00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller 
00:13.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller 
00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller 
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3a) 
00:14.1 IDE interface: ATI Technologies Inc SB700/SB800 IDE Controller 
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA) 
00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller 
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge 
00:14.5 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI2 Controller 
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration 
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map 
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller 
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control 
01:05.0 VGA compatible controller: ATI Technologies Inc Radeon 3100 Graphics 
01:05.1 Audio device: ATI Technologies Inc RS780 Azalia controller 
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02) 

```

```
lsmod 
Module                  Size  Used by 
nls_iso8859_1           3261  1 
nls_cp437               4931  1 
vfat                    9201  1 
fat                    48240  1 vfat 
usb_storage            40172  1 
snd_hda_codec_atihdmi     2411  1 
binfmt_misc             6599  1 
snd_hda_codec_realtek   217980  1 
radeon                825934  3 
snd_hda_intel          22107  2 
snd_hda_codec          87552  3 snd_hda_codec_atihdmi,snd_hda_codec_realtek,snd_hda_intel 
snd_hwdep               5040  1 snd_hda_codec 
snd_pcm                71475  2 snd_hda_intel,snd_hda_codec 
snd_seq_midi            4588  0 
ttm                    56633  1 radeon 
snd_rawmidi            17783  1 snd_seq_midi 
drm_kms_helper         30200  1 radeon 
snd_seq_midi_event      6047  1 snd_seq_midi 
snd_seq                47174  2 snd_seq_midi,snd_seq_midi_event 
drm                   168054  5 radeon,ttm,drm_kms_helper 
snd_timer              19067  2 snd_pcm,snd_seq 
ppdev                   5556  0 
snd_seq_device          5744  3 snd_seq_midi,snd_rawmidi,snd_seq 
parport_pc             26058  1 
psmouse                59033  0 
snd                    49006  13 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device 
serio_raw               4022  0 
hid_a4tech              2018  0 
k8temp                  3132  0 
agpgart                32011  2 ttm,drm 
i2c_algo_bit            5168  1 radeon 
joydev                  8735  0 
soundcore                880  1 snd 
snd_page_alloc          7120  2 snd_hda_intel,snd_pcm 
shpchp                 29886  0 
i2c_piix4               8635  0 
lp                      7342  0 
parport                31492  3 ppdev,parport_pc,lp 
usbhid                 36882  0 
hid                    67742  2 hid_a4tech,usbhid 
ahci                   19013  0 
r8169                  36489  0 
pata_atiixp             3288  3 
libahci                21667  1 ahci 
mii                     4425  1 r8169 

```[/QUOTE]

---

### Post by poolet on 2011-06-09
Unplug the cable from your interface

Open up a new terminal type::

```
sudo su 
"your password"
```

then
/etc/rc.d/rc.inet1 eth0_restart

```
ifconfig eth0 up
dhcpcd eth0
```
if it's works then:: 
```
chmod +x /etc/rc.d/rc.inet1
```

if isn't works, your running **r8169** try to download **r8168** mod and load it by following link:: 

[http://wiki.hetzner.de/index.php/Installation_of_r8168_network_driver]("http://wiki.hetzner.de/index.php/Installation_of_r8168_network_driver")

---

### Post by coolinux on 2011-06-09
Sir I downloaded the R8168 how do I install to this? I paste on the ubuntu home folder. 

I do this 
aptitude install build-essential linux-headers-`uname -r`

but is not working.

---

### Post by poolet on 2011-06-09
first login as root::

```
sudo su 
your password

```then 

```
aptitude install build-essential linux-headers-`uname -r`

``````
cd /tmp
wget [http://download.hetzner.de/drivers/r8168-8.019.00.tar.bz2](http://download.hetzner.de/drivers/r8168-8.019.00.tar.bz2)
tar xjf r8168-8.019.00.tar.bz2
```if you have already download the drivers from another website... just 
paste on it on your desktop and on terminal type...

```

cd desktop 
tar xjf "the file name (driver) that you have download"....

```when you install it you need to updated moduled 

```

depmod -a

```Black list the other mods
```

Ubuntu:
echo "blacklist r8169" >> /etc/modprobe.d/blacklist.conf
Debian:
echo "blacklist r8169" >> /etc/modprobe.d/blacklist

```rebuild 
```

update-initramfs -v -u -k `uname -r`

```

---

### Post by coolinux on 2011-06-09
I got this error

```
root@eric-A780VM-M2:/home/eric# ls 
Desktop    examples.desktop  Public              Templates 
Documents  Music             r8168-8.019.00      Videos 
Downloads  Pictures          r8168-8.019.00.tar 
root@eric-A780VM-M2:/home/eric# tar xjf r8168-8.019.00.tar 
bzip2: (stdin) is not a bzip2 file. 
tar: Child returned status 2 
tar: Error is not recoverable: exiting now 
```

---

### Post by coolinux on 2011-06-10
Update for this.

---

### Post by coolinux on 2011-06-10
up

---

### Post by coolinux on 2011-06-11
Up 

Thanks! ! !

---

### Post by coolinux on 2011-06-13
up

---

