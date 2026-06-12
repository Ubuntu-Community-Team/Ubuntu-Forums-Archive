---
title: "need help with rt2870"
date: 2011-12-30
forum: Networking &amp; Wireless
---

### Post by pofs77 on 2011-12-30
Hello
I have usb alpha with rt2870 i tried more than once to instal on my ubuntu and I followed the instructions exactly but:(:(:(But I did not pass

The problem is When i Run Make the output is 
(make: *** No targets specified and no makefile found.  Stop)

and when i run the (cd 2010_0709_RT2870_Linux_STA_v2.4.0.1/)
the output is: (bash: cd: 2010_0709_RT2870_Linux_STA_v2.4.0.1/: No such file or directory)
so as you see I can not access to files from the terminal and the files on the desktop


Note: The operating system installed on the E: partition not on the c:
is this make diffident ??

---

### Post by wildmanne39 on 2011-12-30
Hi, welcome to the forum! Please open a terminal ctrl+alt+t copy and paste the following commands into it one line at a time, then paste the results here:
```
cat /etc/lsb-release; uname -a
lsusb
iwconfig
rfkill list all
lsmod
```
by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

### Post by pofs77 on 2011-12-31
thanks for your replay and i attach pic for output commands because am anew on the ubuntu 
thank you for yor help

---

### Post by wildmanne39 on 2011-12-31
Hi, I think you have a driver issue but I can not see the picture well enough to tell for sure.

To copy and past the results just hold down the left mouse button and scroll all the information in the window then right click and select copy then post here by right click and choose paste.
Thanks

---

### Post by praseodym on 2011-12-31
Hi,

what about your internal device? The driver rt2870sta should work with this device ID. Try the stick only on-the-fly:
```
sudo modprobe -rfv rt2870sta r8192se_pci
sudo modprobe -v rt2870sta
```
and replug the stick.

---

### Post by pofs77 on 2012-01-01
> **wildmanne39 said:**
> Hi, I think you have a driver issue but I can not see the picture well enough to tell for sure.

To copy and past the results just hold down the left mouse button and scroll all the information in the window then right click and select copy then post here by right click and choose paste.
Thanks
```
hp@ubuntu:~$ cat /etc/lsb-release; uname -a
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.04
DISTRIB_CODENAME=natty
DISTRIB_DESCRIPTION="Ubuntu 11.04"
Linux ubuntu 2.6.38-11-generic #50-Ubuntu SMP Mon Sep 12 21:17:25 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux
hp@ubuntu:~$ lsusb
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 03f0:231d Hewlett-Packard 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 004: ID 148f:3070 Ralink Technology, Corp. RT2870/RT3070 Wireless Adapter
Bus 002 Device 002: ID 12d1:1003 Huawei Technologies Co., Ltd. E220 HSDPA Modem / E270 HSDPA/HSUPA Modem
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 0461:4db6 Primax Electronics, Ltd 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
hp@ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

ppp0      no wireless extensions.

wlan0     Ralink STA  ESSID:""  Nickname:"RT2870STA"
          Mode:Auto  Frequency=2.412 GHz  Access Point: Not-Associated   
          Bit Rate:1 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=10/100  Signal level:0 dBm  Noise level:-115 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

hp@ubuntu:~$ rfkill list all
0: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
2: hp-wifi: Wireless LAN
	Soft blocked: no
	Hard blocked: no
3: hp-bluetooth: Bluetooth
	Soft blocked: no
	Hard blocked: no
hp@ubuntu:~$ lsmod
Module                  Size  Used by
rt2870sta             450556  1 
ppp_deflate            12990  0 
zlib_deflate           27074  1 ppp_deflate
bsd_comp               12913  0 
ppp_async              17540  1 
crc_ccitt              12667  2 rt2870sta,ppp_async
rfcomm                 47694  8 
binfmt_misc            17565  1 
sco                    18187  2 
bnep                   18308  2 
l2cap                  53570  16 rfcomm,bnep
parport_pc             36959  0 
ppdev                  17113  0 
snd_hda_codec_hdmi     28167  1 
snd_hda_codec_idt      71137  1 
snd_hda_intel          33176  2 
joydev                 17606  0 
snd_hda_codec         103804  3 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13604  1 snd_hda_codec
snd_pcm                96391  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30486  1 snd_seq_midi
option                 25285  2 
snd_seq_midi_event     14899  1 snd_seq_midi
usb_wwan               20407  1 option
hp_wmi                 13706  0 
usbserial              42908  7 option,usb_wwan
snd_seq                61621  2 snd_seq_midi,snd_seq_midi_event
uvcvideo               72195  0 
i915                  515121  3 
snd_timer              29602  2 snd_pcm,snd_seq
sparse_keymap          13898  1 hp_wmi
videodev               82052  1 uvcvideo
snd_seq_device         14462  3 snd_seq_midi,snd_rawmidi,snd_seq
psmouse                73535  0 
v4l2_compat_ioctl32    17078  1 videodev
serio_raw              13166  0 
snd                    67382  14 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
btusb                  18600  2 
drm_kms_helper         42136  1 i915
drm                   227534  4 i915,drm_kms_helper
bluetooth              72320  9 rfcomm,sco,bnep,l2cap,btusb
soundcore              12680  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
i2c_algo_bit           13400  1 i915
video                  19438  1 i915
lp                     17825  0 
parport                46458  3 parport_pc,ppdev,lp
uas                    17996  0 
usb_storage            53538  0 
r8169                  48022  0 
hp@ubuntu:~$ 

```

ths is the output 
thank you

---

### Post by pofs77 on 2012-01-01
> **praseodym said:**
> Hi,

what about your internal device? The driver rt2870sta should work with this device ID. Try the stick only on-the-fly:
```
sudo modprobe -rfv rt2870sta r8192se_pci
sudo modprobe -v rt2870sta
```
and replug the stick.

```
hp@ubuntu:~$ sudo modprobe -rfv rt2870sta r8192se_pci
FATAL: Module rt2870sta is in use.
hp@ubuntu:~$ sudo modprobe -v rt2870sta
hp@ubuntu:~$ 
```

thank you

---

### Post by praseodym on 2012-01-01
Unplug the stick, and check if the driver is still loaded:

```
lsmod | grep rt2
```
after that unload the other:
```
sudo modprobe -rfv r8192se_pci
```
and replug the stick. Check the driver again.

---

### Post by wildmanne39 on 2012-01-01
Hi, out of curiosity would you please post the output of:
```
lspci -nnk | grep -iA2 net
```
I'm guessing you still have an internal wireless card is that correct? 
Thanks

---

### Post by pofs77 on 2012-01-02
> **wildmanne39 said:**
> Hi, out of curiosity would you please post the output of:
```
lspci -nnk | grep -iA2 net
```
I'm guessing you still have an internal wireless card is that correct? 
Thanks
hi.that is correct i have internal wireless it is realtek r8192se
but it dos not work with aircrack is that correct??
so i have external usb rt2870 

thank you

---

### Post by pofs77 on 2012-01-02
??

---

### Post by pofs77 on 2012-01-02
> **wildmanne39 said:**
> Hi, out of curiosity would you please post the output of:
```
lspci -nnk | grep -iA2 net
```
I'm guessing you still have an internal wireless card is that correct? 
Thanks

```
hp@ubuntu:~$ lspci -nnk | grep -iA2 net
02:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8191SEvA Wireless LAN Controller [10ec:8171] (rev 10)
	Subsystem: Hewlett-Packard Company Device [103c:1467]
	Kernel modules: r8192se_pci
85:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 02)
	Subsystem: Hewlett-Packard Company Device [103c:1526]
	Kernel driver in use: r8169
```
thank you

---

### Post by pofs77 on 2012-01-02
> **praseodym said:**
> Unplug the stick, and check if the driver is still loaded:

```
lsmod | grep rt2
```
after that unload the other:
```
sudo modprobe -rfv r8192se_pci
```
and replug the stick. Check the driver again.
```
hp@ubuntu:~$ lsmod | grep rt2
rt2870sta             450556  1 
crc_ccitt              12667  2 rt2870sta,ppp_async
```

```
hp@ubuntu:~$ sudo modprobe -rfv r8192se_pci
hp@ubuntu:~$ 
```

nothing happen?? :(:(

---

### Post by pofs77 on 2012-01-02
hi there this some pic from driver files i hope to be useful :popcorn::popcorn: 

thank you and happy new year :):)

---

### Post by pofs77 on 2012-01-04
hi guys need help

---

### Post by praseodym on 2012-01-04
In Ubuntu 11.04 you can try the module rt2800usb, too. Unplug the stick and:

```
sudo modprobe -rfv rt2870sta
sudo modprobe -v rt2800usb
```
Replug it and check:

```
iwconfig
ifconfig -a
dmesg | grep rt28
rfkill list
lsmod
sudo iwlist scan
```

---

