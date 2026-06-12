---
title: "Gateway series m laptop wireless problem"
date: 2011-12-29
forum: Networking &amp; Wireless
---

### Post by eino1953 on 2011-12-29
Here is the information on the system. It shows that it's working but it's not.  Thanks in advance for your help. 

> barbra@barbra-laptop:~$ lspci -nnk | grep -iA2 net
02:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd. Device [11ab:2a08] (rev 03)
06:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 01)
    Kernel driver in use: r8169
    Kernel modules: r8169
barbra@barbra-laptop:~$ lsusb
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 0bda:0158 Realtek Semiconductor Corp. Mass Storage Device
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 04f2:b027 Chicony Electronics Co., Ltd Gateway USB 2.0 Webcam
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
barbra@barbra-laptop:~$ lsmod
Module                  Size  Used by
binfmt_misc             6587  1 
joydev                  8740  0 
snd_hda_codec_idt      52042  1 
ppdev                   5259  0 
fbcon                  35102  71 
tileblit                1999  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
vga16fb                11385  0 
vgastate                8961  1 vga16fb
snd_hda_intel          22069  2 
snd_hda_codec          74201  2 snd_hda_codec_idt,snd_hda_intel
snd_hwdep               5412  1 snd_hda_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70694  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1338  0 
snd_seq_oss            26722  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              19130  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
i915                  289715  3 
drm_kms_helper         29329  1 i915
uvcvideo               57438  0 
snd                    54244  16 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
lp                      7028  0 
videodev               34425  1 uvcvideo
v4l1_compat            13251  2 uvcvideo,videodev
psmouse                63677  0 
drm                   163747  4 i915,drm_kms_helper
i2c_algo_bit            5028  1 i915
serio_raw               3978  0 
soundcore               6620  1 snd
snd_page_alloc          7076  2 snd_hda_intel,snd_pcm
usb_storage            39969  0 
intel_agp              24375  2 i915
video                  17375  1 i915
agpgart                31724  2 drm,intel_agp
output                  1871  1 video
parport                32635  2 ppdev,lp
ahci                   32680  2 
r8169                  34140  0 
mii                     4381  1 r8169
barbra@barbra-laptop:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:e0:b8:e4:d0:17  
          inet addr:192.168.1.7  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::2e0:b8ff:fee4:d017/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:644 errors:0 dropped:0 overruns:0 frame:0
          TX packets:389 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:736238 (736.2 KB)  TX bytes:39005 (39.0 KB)
          Interrupt:27 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:720 (720.0 B)  TX bytes:720 (720.0 B)

barbra@barbra-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

barbra@barbra-laptop:~$ cat /var/lib/NetworkManager/NetworkManager.state

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
barbra@barbra-laptop:~$ sudo iwlist scan
[sudo] password for barbra: 
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

barbra@barbra-laptop:~$ 


---

### Post by eino1953 on 2011-12-30
I just installed a new driver. It shows that it's present, and working. But It don't show any 
 extensions. I would like to know what to do next, to solve the problem.

---

### Post by eino1953 on 2011-12-30
Looks like I'm going to do more research on the subject. If I come up with answers, I will post them, and mark the post solved.

---

### Post by eino1953 on 2012-01-01
[INDENT]                             Here is all the steps to get the wireless working.
First I had to install wine because the driver was an windows exe file. After opening the program, and the files i closed wine.
1. opened the terminal
2. entered in "cd .wine/drive_c/Program\ Files/NETGEAR/WN511T/" to change the directory.
3. sudo ndiswrapper -i NetMW14x.inf
4. sudo ndiswrapper -a 11ab:2a08 netmw14x This came up with a warning just ignore it, and move on.
5. sudo ndiswrapper -m
6. sudo depmod -a
7. sudo modprobe ndiswrapper


I had a problem with the wireless after reboot or shutdown. I had to run  modprobe ndiswrapper in the terminal. I tried a script with just the  modprobe ndiswrapper, but it didn't work this is what worked.


gksudo gedit /etc/init.d/wirelessfix.sh 

when the file pops up type in:

#!/bin/bash
cd .wine/drive_c/Program\ Files/NETGEAR/WN511T/
sudo ndiswrapper -i NetMW14x.inf
sudo ndiswrapper -a 11ab:2a08 netmw14x
sudo ndiswrapper -m
sudo depmod -a
sudo modprobe ndiswrapper

then save the file and go back into the terminal

cd /etc/init.d/

sudo chmod 755 wirelessfix.sh

sudo update-rc.d wirelessfix.sh defaults

The system take a few more seconds to start, But I have a reliable  connection.  I haven't tested it,  to see what happens after the notebook  goes to sleep.                         [/INDENT]

---

