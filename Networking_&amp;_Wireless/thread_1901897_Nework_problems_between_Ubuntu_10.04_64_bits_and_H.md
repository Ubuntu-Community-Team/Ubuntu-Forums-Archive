---
title: "Nework problems between Ubuntu 10.04 64 bits and Huawey HG520"
date: 2011-12-29
forum: Networking &amp; Wireless
---

### Post by Creonte on 2011-12-29
This is my first post, and I am not so fluent in english, so sorry in advance for any possible mistake.

Fist I will describe the context, then the problem, and finally I will include some detailed system information. I have been looking for this problem in the net, without results.

_Context:_
I have just changed my PC from 32 bit architecture to 64 bits. Then I have installed windows 7 and ubuntu 10.04. In previous PC I also had installed ubuntu 10.04 and windows XP (without these problems). The PC is connected, via cable, to a huawey HG520 gateway. 

_Problem:_
The internet connection is unestable: some times it is lost and then it is recovered. The problem lies between the ethernet card and the router, for I cannot reach the router in such cases (ping to 192.168.1.1 gives "host unreachable", and tcpdump gives ARP request "who has 192.168.1.1"). I have not this issue hen the SO is windows 7, and I had not this problem with ubuntu 10.04 when the architecture was 32 bits. I have tried already to set up the network configuration manually, but I always get the same result: inestable conection to Internet.

I have also tried with ubuntu 11.10, with simmilar (even worse) results. 

_System Information_

Result from lshw -C network:

```
*-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: eth0
       version: 06
       serial: 50:e5:49:39:c0:90
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.1.129 latency=0 link=yes multicast=yes port=MII speed=100MB/s
       resources: irq:29 ioport:de00(size=256) memory:fbcff000-fbcfffff(prefetchable) memory:fbcf8000-fbcfbfff(prefetchable)

```

Result from lspci -nn | grep 0280
```
root@Despacho:/home/papa# lspci -nn 
00:00.0 Host bridge [0600]: Intel Corporation Device [8086:0100] (rev 09)
00:01.0 PCI bridge [0604]: Intel Corporation Sandy Bridge PCI Express Root Port [8086:0101] (rev 09)
00:02.0 VGA compatible controller [0300]: Intel Corporation Device [8086:0112] (rev 09)
00:16.0 Communication controller [0780]: Intel Corporation Cougar Point HECI Controller #1 [8086:1c3a] (rev 04)
00:1a.0 USB Controller [0c03]: Intel Corporation Cougar Point USB Enhanced Host Controller #2 [8086:1c2d] (rev 05)
00:1b.0 Audio device [0403]: Intel Corporation Cougar Point High Definition Audio Controller [8086:1c20] (rev 05)
00:1c.0 PCI bridge [0604]: Intel Corporation Cougar Point PCI Express Root Port 1 [8086:1c10] (rev b5)
00:1c.2 PCI bridge [0604]: Intel Corporation 82801 PCI Bridge [8086:244e] (rev b5)
00:1c.3 PCI bridge [0604]: Intel Corporation Cougar Point PCI Express Root Port 4 [8086:1c16] (rev b5)
00:1c.4 PCI bridge [0604]: Intel Corporation Cougar Point PCI Express Root Port 5 [8086:1c18] (rev b5)
00:1d.0 USB Controller [0c03]: Intel Corporation Cougar Point USB Enhanced Host Controller #1 [8086:1c26] (rev 05)
00:1f.0 ISA bridge [0601]: Intel Corporation Device [8086:1c5c] (rev 05)
00:1f.2 SATA controller [0106]: Intel Corporation Cougar Point 6 port SATA AHCI Controller [8086:1c02] (rev 05)
00:1f.3 SMBus [0c05]: Intel Corporation Cougar Point SMBus Controller [8086:1c22] (rev 05)
01:00.0 USB Controller [0c03]: Device [1b6f:7023] (rev 01)
03:00.0 PCI bridge [0604]: Integrated Technology Express, Inc. Device [1283:8892] (rev 10)
05:00.0 SATA controller [0106]: Device [1b4b:9172] (rev 11)
06:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 06)

```

Result from: lsusb
```
root@Despacho:/home/papa# lsusb
Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 003: ID 03f0:8207 Hewlett-Packard 
Bus 002 Device 002: ID 8087:0024  
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:0024  
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
root@Despacho:/home/papa#
```

Result from: ifconfig
```
root@Despacho:/home/papa# ifconfig
eth0      Link encap:Ethernet  direcciónHW 50:e5:49:39:c0:90  
          Direc. inet:192.168.1.129  Difus.:192.168.1.255  Másc:255.255.255.0
          Dirección inet6: fe80::52e5:49ff:fe39:c090/64 Alcance:Enlace
          ACTIVO DIFUSIÓN FUNCIONANDO MULTICAST  MTU:1500  Métrica:1
          Paquetes RX:6656 errores:0 perdidos:6656 overruns:0 frame:6656
          Paquetes TX:8102 errores:0 perdidos:134 overruns:0 carrier:0
          colisiones:0 long.colaTX:1000 
          Bytes RX:3404300 (3.4 MB)  TX bytes:1019373 (1.0 MB)
          Interrupción:29 Dirección base: 0xe000 

lo        Link encap:Bucle local  
          Direc. inet:127.0.0.1  Másc:255.0.0.0
          Dirección inet6: ::1/128 Alcance:Anfitrión
          ACTIVO BUCLE FUNCIONANDO  MTU:16436  Métrica:1
          Paquetes RX:274 errores:0 perdidos:0 overruns:0 frame:0
          Paquetes TX:274 errores:0 perdidos:0 overruns:0 carrier:0
          colisiones:0 long.colaTX:0 
          Bytes RX:31636 (31.6 KB)  TX bytes:31636 (31.6 KB)

root@Despacho:/home/papa#
```

Result from: lsmod
```
root@Despacho:/home/papa# lsmod
Module                  Size  Used by
binfmt_misc             7960  1 
ppdev                   6375  0 
snd_hda_codec_realtek   279104  1 
snd_hda_intel          25805  2 
snd_hda_codec          85759  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               6924  1 snd_hda_codec
snd_pcm_oss            41394  0 
snd_mixer_oss          16299  1 snd_pcm_oss
snd_pcm                87946  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1782  0 
snd_seq_oss            31191  0 
snd_seq_midi            5829  0 
snd_rawmidi            23420  1 snd_seq_midi
snd_seq_midi_event      7267  2 snd_seq_oss,snd_seq_midi
snd_seq                57481  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              23681  2 snd_pcm,snd_seq
snd_seq_device          6888  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
fbcon                  39270  71 
tileblit                2487  1 fbcon
font                    8053  1 fbcon
bitblit                 5811  1 fbcon
softcursor              1565  1 bitblit
snd                    71283  16 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
vga16fb                12757  1 
vgastate                9857  1 vga16fb
lp                      9336  0 
parport                37160  2 ppdev,lp
xhci                   42775  0 
soundcore               8052  1 snd
snd_page_alloc          8500  2 snd_hda_intel,snd_pcm
usbhid                 41116  0 
hid                    83888  1 usbhid
r8169                  39714  0 
mii                     5237  1 r8169
ahci                   38350  3 
root@Despacho:/home/papa# 

```

Thanks in advance for any help

---

### Post by Creonte on 2012-01-02
Finally I found the answer myself in [http://ubuntuforums.org/archive/index.php/t-1436667.html](http://ubuntuforums.org/archive/index.php/t-1436667.html).

As the answer is hidden in a long debate, I copy here the solution:

The problem is due to an incorrect driver loading with the 2.6.32-22-generic-pae kernel (may apply to other kernels also).

This is how I rectified the issue.

1. Check the model number of your ethernet controller:
$ lspci | grep Realtek
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 03)

2. Check the driver your kernel is loading:
$ lsmod | grep r816*
r8169 91629 0

As you can see we have a r8169 driver for a r8168 chipset which is the cause of our issues.

3. Download the 8168 linux drivers from the Realtek website: [http://www.realtek.com.tw/downloads/](http://www.realtek.com.tw/downloads/), choosing the proper card (in my case, PCI Express). 

4. cd to Download directory and extract:
$ tar -xvf r8168-8.027.00.tar.bz2 (or which ever driver was downloaded

5. Run script as superuser to autocompile driver:
$ cd r8168-8.027.00
$ sudo ./autorun.sh

6. [Optional] Test driver
$ sudo rmmod r8169
$ sudo modprobe r8168
$ sudo /etc/init.d/networking restart

Your network should be up and running with the new driver. To make the change permanent.

7. Blacklist r8169.
$ sudo gedit /etc/modprobe.d/blacklist.conf

Append the following lines:
# Blacklist Realtek RTL8111/8169 gigabit driver
blacklist r8169

Save and quit.

8. Update driver cache.
$ update-initramfs -u

REBOOT and see if the correct driver has loaded:

$ lsmod | grep r816*
r8168 91629 0

And everything should be just hunky-dory. ;)

---

