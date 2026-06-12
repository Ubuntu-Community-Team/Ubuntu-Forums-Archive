---
title: "Major problems with WNDA3100v2 on 11.04"
date: 2011-10-08
forum: Networking &amp; Wireless
---

### Post by lynux77 on 2011-10-08
I have been wrestling back and forth these past few days between ndiswrapper and my USB wireless adapter. At the current time, my ndiswrapper gives me a white screen and refuses to start after I installed bcmwlhigh5.inf. Its been a long and frustrating journey through countless threads and i finally decided to post my own thread and explain my situation.

The adapter is a NETGEAR WNDA3100v2. I run it on a Windows Vista operating system, and the current driver to run it is bcmwlhigh6.inf. (That is what I found in the 
\drivers\VISTA folder.) My Windows Vista installation is 32 bit. My current ubuntu version is 11.04 and is 64 bit. As I explained earlier, my ndiswrapper shows me a white screen, even though I completely uninstalled all packages related to ndiswrapper and reinstalled them.

I am very new to linux and ubuntu, just installed it a couple of days ago, and all this jargon is getting to my head. If could help me fix this problem, I would be eternally grateful.

---

### Post by lynux77 on 2011-10-08
Disregard the part about my ndiswrapper not working, it is currently working. Just had to do a little restart. :D
To restate, my problem is that the both bcmwlhigh drivers show that the hardware is present, but no networks show up and the adapter shows no light.

By the way, the USB adapters on thinkpenguin.com, are they worth it? I would like to have some reviews on those before I buy it.

---

### Post by lynux77 on 2011-10-09
Sorry for the tri post, but I really want to get this working and help anyone else with this problem.

What drivers do I use? There are a slew of drivers to choose from, and I don't know which one to use. The one that always crashes on me is bcmwlhigh5. The one that was provided to me by netgear on my vista system is bcmwlhigh6. I know there are more floating around, but I don't know thier exact names.

---

### Post by praseodym on 2011-10-09
Hi,

you are sure using the right driver? Please show:

```
lsusb
lsmod
ndiswrapper -l
cat /etc/modprobe.d/ndiswrapper.conf
rfkill list
iwconfig
dmesg | grep ndis
```

---

### Post by lynux77 on 2011-10-09
First off, thanks for responding to my thread. I appreciate it. :)

Here are all the commands you asked to show. The command rfkill list had no output, as shown below.

sebastian@ubuntu:~$ lsusb
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 002: ID 413c:2003 Dell Computer Corp. Keyboard
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 046d:c044 Logitech, Inc. LX3 Optical Mouse
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 058f:6387 Alcor Micro Corp. Transcend JetFlash Flash Drive
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 0846:9011 NetGear, Inc. WNDA3100(v2) 802.11n
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

sebastian@ubuntu:~$ lsmod
Module                  Size  Used by
nls_iso8859_1          12713  1 
nls_cp437              16991  1 
vfat                   21708  1 
fat                    61374  1 vfat
parport_pc             36959  1 
ppdev                  17113  0 
snd_hda_codec_idt      71137  1 
binfmt_misc            17565  1 
snd_hda_intel          33176  2 
snd_hda_codec         103804  2 snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13604  1 snd_hda_codec
snd_pcm                96391  2 snd_hda_intel,snd_hda_codec
nvidia              10709116  41 
snd_seq_midi           13324  0 
snd_rawmidi            30486  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61621  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29602  2 snd_pcm,snd_seq
snd_seq_device         14462  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    67382  13 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse                73535  0 
serio_raw              13166  0 
soundcore              12680  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
video                  19438  0 
lp                     17825  0 
parport                46458  3 parport_pc,ppdev,lp
usbhid                 46956  0 
hid                    91020  1 usbhid
usb_storage            53538  1 
uas                    17996  0 
e1000e                159096  0 
firewire_ohci          40370  0 
firewire_core          62646  1 firewire_ohci
crc_itu_t              12707  1 firewire_core

sebastian@ubuntu:~$ ndiswrapper -l
bcmwlhigh6 : driver installed
    device (0846:9011) present
sebastian@ubuntu:~$ cat /etc/modprobe.d/ndiswrapper.conf
alias usb:v0846p9011d*dc*dsc*dp*ic*isc*ip* ndiswrapper

sebastian@ubuntu:~$ rfkill list

sebastian@ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

sebastian@ubuntu:~$ dmesg | grep ndis
[  200.519869] ndiswrapper version 1.56 loaded (smp=yes, preempt=no)
[  200.526437] usbcore: registered new interface driver ndiswrapper
[  220.730185] usbcore: deregistering interface driver ndiswrapper
[  220.751185] ndiswrapper version 1.56 loaded (smp=yes, preempt=no)
[  221.035148] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisQueueIoWorkItem'
[  221.035162] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisFreeIoWorkItem'
[  221.035171] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisMSetMiniportAttributes'
[  221.035188] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisMResetComplete'
[  221.035197] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisAllocateIoWorkItem'
[  221.035206] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisMSendNetBufferListsComplete'
[  221.035216] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisMDeregisterMiniportDriver'
[  221.035225] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisAllocateNetBufferListPool'
[  221.035242] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisAllocateNetBufferAndNetBufferList'
[  221.035252] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisMIndicateReceiveNetBufferLists'
[  221.035261] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisMOidRequestComplete'
[  221.035270] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisFreeNetBufferListPool'
[  221.035283] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisOpenConfigurationEx'
[  221.035294] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisMIndicateStatusEx'
[  221.035303] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisFreeNetBufferList'
[  221.035320] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisMGetBusData'
[  221.035330] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisMRegisterMiniportDriver'
[  221.035367] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisAllocateMdl'
[  221.035379] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisFreeMdl'
[  221.035388] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisAllocateMemoryWithTagPriority'
[  221.035398] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisGetSystemUpTimeEx'
[  221.035405] ndiswrapper (import:233): unknown symbol: WDFLDR.SYS:'WdfVersionBind'
[  221.035413] ndiswrapper (import:233): unknown symbol: WDFLDR.SYS:'WdfVersionUnbind'
[  221.035417] ndiswrapper (load_sys_files:206): couldn't prepare driver 'bcmwlhigh6'
[  221.036110] ndiswrapper (load_wrap_driver:108): couldn't load driver bcmwlhigh6; check system log for messages from 'loadndisdriver'
[  221.036172] usbcore: registered new interface driver ndiswrapper

---

### Post by praseodym on 2011-10-09
Remove the current config and try the attached driver:

```
sudo modprobe -rf ndiswrapper
sudo rm /etc/modprobe.d/ndiswrapper.conf
sudo rm -r /etc/ndiswrapper/* 
```

---

### Post by lynux77 on 2011-10-09
I installed both drivers, but only bcmn43xx32 showed that my hardware was present.

I placed your code in and my terminal spitted this out:

sebastian@ubuntu:~$ sudo modprobe -rf ndiswrapper
[sudo] password for sebastian:

(nothing came out for this function)

 
sebastian@ubuntu:~$ sudo rm /etc/modprobe.d/ndiswrapper.conf
rm: cannot remove `/etc/modprobe.d/ndiswrapper.conf': No such file or directory

sebastian@ubuntu:~$ sudo rm -r /etc/ndiswrapper/*
rm: cannot remove `/etc/ndiswrapper/*': No such file or directory

---

### Post by praseodym on 2011-10-09
Ok, try the installation by hand:

```
sudo ndiswrapper -i /path/to/*.inf
ndiswrapper -l #test 1
cat /etc/modprobe.d/ndiswrapper.conf #test 2
sudo modprobe -v ndiswrapper
sudo ndiswrapper -ma
```
Check:

```
lsmod
grep loadndisdriver /var/log/syslog
iwconfig
dmesg | grep ndis
```

---

### Post by lynux77 on 2011-10-09
```
sebastian@ubuntu:~$ sudo ndiswrapper -i /home/sebastian/Music/Broadcom_bcm43xx_USB_32_64bit_v2/bcmn43xx64.inf
couldn't find SourceDisksFiles section - continuing anyway...
installing bcmn43xx64 ...
couldn't find install section "BCM43XXN32" -
installation may be incomplete

sebastian@ubuntu:~$ sudo ndiswrapper -i /home/sebastian/Music/Broadcom_bcm43xx_USB_32_64bit_v2/bcmn43xx32.inf
driver bcmn43xx32 is already installed

sebastian@ubuntu:~$ ndiswrapper -l
bcmn43xx32 : driver installed
    device (0846:9011) present
bcmn43xx64 : driver installed

sebastian@ubuntu:~$ cat /etc/modprobe.d/ndiswrapper.conf
alias usb:v050Dp6050d*dc*dsc*dp*ic*isc*ip* ndiswrapper
alias usb:v050Dp615Ad*dc*dsc*dp*ic*isc*ip* ndiswrapper
alias usb:v050Dp825Cd*dc*dsc*dp*ic*isc*ip* ndiswrapper
alias usb:v0846p9011d*dc*dsc*dp*ic*isc*ip* ndiswrapper
alias usb:v0846p9020d*dc*dsc*dp*ic*isc*ip* ndiswrapper
sebastian@ubuntu:~$ sudo modprobe -v ndiswrapper
(nothing appeared)
sebastian@ubuntu:~$ sudo ndiswrapper -ma
module configuration information is stored in /etc/modprobe.d/ndiswrapper.conf

sebastian@ubuntu:~$ lsmod
Module                  Size  Used by
ndiswrapper           249811  0 
nls_iso8859_1          12713  1 
nls_cp437              16991  1 
vfat                   21708  1 
fat                    61374  1 vfat
parport_pc             36959  1 
ppdev                  17113  0 
snd_hda_codec_idt      71137  1 
binfmt_misc            17565  1 
snd_hda_intel          33176  2 
snd_hda_codec         103804  2 snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13604  1 snd_hda_codec
snd_pcm                96391  2 snd_hda_intel,snd_hda_codec
nvidia              10709116  51 
snd_seq_midi           13324  0 
snd_rawmidi            30486  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61621  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29602  2 snd_pcm,snd_seq
snd_seq_device         14462  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    67382  13 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse                73535  0 
serio_raw              13166  0 
soundcore              12680  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
video                  19438  0 
lp                     17825  0 
parport                46458  3 parport_pc,ppdev,lp
usbhid                 46956  0 
hid                    91020  1 usbhid
usb_storage            53538  1 
uas                    17996  0 
e1000e                159096  0 
firewire_ohci          40370  0 
firewire_core          62646  1 firewire_ohci
crc_itu_t              12707  1 firewire_core

sebastian@ubuntu:~$ grep loadndisdriver /var/log/syslog
Oct  8 23:29:48 ubuntu loadndisdriver: loadndisdriver: load_driver(358): couldn't load driver bcmwlhigh6
Oct  8 23:29:48 ubuntu kernel: [ 9404.336302] ndiswrapper (load_wrap_driver:108): couldn't load driver bcmwlhigh6; check system log for messages from 'loadndisdriver'
Oct  8 23:31:05 ubuntu kernel: [   11.445237] ndiswrapper (load_wrap_driver:108): couldn't load driver bcmwlhigh6; check system log for messages from 'loadndisdriver'
Oct  8 23:33:53 ubuntu loadndisdriver: loadndisdriver: load_driver(358): couldn't load driver bcmwlhigh6
Oct  8 23:33:53 ubuntu kernel: [  179.866192] ndiswrapper (load_wrap_driver:108): couldn't load driver bcmwlhigh6; check system log for messages from 'loadndisdriver'
Oct  9 10:23:20 ubuntu loadndisdriver: loadndisdriver: load_driver(358): couldn't load driver bcmwlhigh6
Oct  9 10:23:20 ubuntu kernel: [  932.756056] ndiswrapper (load_wrap_driver:108): couldn't load driver bcmwlhigh6; check system log for messages from 'loadndisdriver'
Oct  9 10:24:34 ubuntu loadndisdriver: loadndisdriver: load_driver(358): couldn't load driver bcmwlhigh6
Oct  9 10:24:34 ubuntu kernel: [ 1007.116051] ndiswrapper (load_wrap_driver:108): couldn't load driver bcmwlhigh6; check system log for messages from 'loadndisdriver'
Oct  9 10:24:57 ubuntu loadndisdriver: loadndisdriver: load_driver(358): couldn't load driver bcmwlhigh6
Oct  9 10:24:57 ubuntu kernel: [ 1029.639454] ndiswrapper (load_wrap_driver:108): couldn't load driver bcmwlhigh6; check system log for messages from 'loadndisdriver'
Oct  9 11:01:57 ubuntu loadndisdriver: loadndisdriver: load_driver(358): couldn't load driver bcmwlhigh6
Oct  9 11:01:57 ubuntu kernel: [  203.366134] ndiswrapper (load_wrap_driver:108): couldn't load driver bcmwlhigh6; check system log for messages from 'loadndisdriver'
Oct  9 18:36:46 ubuntu loadndisdriver: loadndisdriver: load_driver(358): couldn't load driver bcmwlhigh6
Oct  9 18:36:46 ubuntu kernel: [  221.036110] ndiswrapper (load_wrap_driver:108): couldn't load driver bcmwlhigh6; check system log for messages from 'loadndisdriver'
Oct  9 18:50:06 ubuntu loadndisdriver: loadndisdriver: load_driver(358): couldn't load driver bcmn43xx32
Oct  9 18:50:06 ubuntu kernel: [ 1020.745034] ndiswrapper (load_wrap_driver:108): couldn't load driver bcmn43xx32; check system log for messages from 'loadndisdriver'
Oct  9 19:11:50 ubuntu loadndisdriver: loadndisdriver: load_driver(358): couldn't load driver bcmn43xx32
Oct  9 19:11:50 ubuntu kernel: [ 2325.015168] ndiswrapper (load_wrap_driver:108): couldn't load driver bcmn43xx32; check system log for messages from 'loadndisdriver'

sebastian@ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

sebastian@ubuntu:~$ dmesg | grep ndis
[  200.519869] ndiswrapper version 1.56 loaded (smp=yes, preempt=no)
[  200.526437] usbcore: registered new interface driver ndiswrapper
[  220.730185] usbcore: deregistering interface driver ndiswrapper
[  220.751185] ndiswrapper version 1.56 loaded (smp=yes, preempt=no)
[  221.035148] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisQueueIoWorkItem'
[  221.035162] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisFreeIoWorkItem'
[  221.035171] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisMSetMiniportAttributes'
[  221.035188] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisMResetComplete'
[  221.035197] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisAllocateIoWorkItem'
[  221.035206] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisMSendNetBufferListsComplete'
[  221.035216] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisMDeregisterMiniportDriver'
[  221.035225] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisAllocateNetBufferListPool'
[  221.035242] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisAllocateNetBufferAndNetBufferList'
[  221.035252] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisMIndicateReceiveNetBufferLists'
[  221.035261] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisMOidRequestComplete'
[  221.035270] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisFreeNetBufferListPool'
[  221.035283] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisOpenConfigurationEx'
[  221.035294] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisMIndicateStatusEx'
[  221.035303] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisFreeNetBufferList'
[  221.035320] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisMGetBusData'
[  221.035330] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisMRegisterMiniportDriver'
[  221.035367] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisAllocateMdl'
[  221.035379] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisFreeMdl'
[  221.035388] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisAllocateMemoryWithTagPriority'
[  221.035398] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisGetSystemUpTimeEx'
[  221.035405] ndiswrapper (import:233): unknown symbol: WDFLDR.SYS:'WdfVersionBind'
[  221.035413] ndiswrapper (import:233): unknown symbol: WDFLDR.SYS:'WdfVersionUnbind'
[  221.035417] ndiswrapper (load_sys_files:206): couldn't prepare driver 'bcmwlhigh6'
[  221.036110] ndiswrapper (load_wrap_driver:108): couldn't load driver bcmwlhigh6; check system log for messages from 'loadndisdriver'
[  221.036172] usbcore: registered new interface driver ndiswrapper
[ 1006.680238] usbcore: deregistering interface driver ndiswrapper
[ 1006.680372] ndiswrapper (ntoskernel_exit:2677): object ffff88012495be30(2) was not freed, freeing it now
[ 1006.701236] ndiswrapper version 1.56 loaded (smp=yes, preempt=no)
[ 1006.714572] usbcore: registered new interface driver ndiswrapper
[ 1020.430180] usbcore: deregistering interface driver ndiswrapper
[ 1020.451707] ndiswrapper version 1.56 loaded (smp=yes, preempt=no)
[ 1020.744428] ndiswrapper (check_nt_hdr:141): kernel is 64-bit, but Windows driver is not 64-bit;bad magic: 010B
[ 1020.744436] ndiswrapper (load_sys_files:206): couldn't prepare driver 'bcmn43xx32'
[ 1020.745034] ndiswrapper (load_wrap_driver:108): couldn't load driver bcmn43xx32; check system log for messages from 'loadndisdriver'
[ 1020.745091] usbcore: registered new interface driver ndiswrapper
[ 1053.280184] usbcore: deregistering interface driver ndiswrapper
[ 1053.280292] ndiswrapper (ntoskernel_exit:2677): object ffff8800770aba30(2) was not freed, freeing it now
[ 2324.732897] ndiswrapper version 1.56 loaded (smp=yes, preempt=no)
[ 2325.014561] ndiswrapper (check_nt_hdr:141): kernel is 64-bit, but Windows driver is not 64-bit;bad magic: 010B
[ 2325.014570] ndiswrapper (load_sys_files:206): couldn't prepare driver 'bcmn43xx32'
[ 2325.015168] ndiswrapper (load_wrap_driver:108): couldn't load driver bcmn43xx32; check system log for messages from 'loadndisdriver'
[ 2325.015229] usbcore: registered new interface driver ndiswrapper
```

Where do I go from here?  My kernel is 64 bit, but when I install the 64 bit driver, ndiswrapper says my hardware is not present.

---

### Post by lynux77 on 2011-10-14
An update on the current situation. 

I installed Oneiric, and managed to install bcmwlhigh5.inf without it crashing. However, it did give me this when I tried to install it: Module could not be loaded. Error was: [BLANK]

I am not sure about the correct drivers. There are many I have been tinkering with, and i need just 1. Could someone tell me which one would be correct for my system?

---

### Post by praseodym on 2011-10-14
> ```
sebastian@ubuntu:~$ ndiswrapper -l
bcmn43xx32 : driver installed
    device (0846:9011) present
bcmn43xx64 : driver installed
```
2 drivers installed? Remove the configuration and try this driver again, it shows up this time.

```
sudo modprobe -rfv ndiswrapper
sudo rm /etc/modprobe.d/ndiswrapper.conf
sudo rm -r /etc/ndiswrapper/*
```

---

### Post by lynux77 on 2011-10-14
I removed the drivers and put in bcmn43xx32. When I click install, ndiswrapper freezes and I have to force close it. But when I load it up again, it shows the driver is installed and the hardware is present. The same exact thing with bcmn43xx64. This never happened under 11.04, and I upgraded to 11.10, thinking there would be driver that could make my device work.

Seems I have hit a dead end here. Nothing is really working. Thanks for all your help, praseodym.


Edit: ndiswrapper crashes no matter what driver you put in it on 11.10. I have tried all the drivers, everytime I click install, it crashes and I have to force close it.

---

### Post by praseodym on 2011-10-15
> [ 2325.014561] ndiswrapper (check_nt_hdr:141): kernel is 64-bit, but Windows driver is not 64-bit;bad magic: 010B
You always try the 64bit driver? Please show:

```
grep loadndisdriver /var/log/syslog
```

---

### Post by lynux77 on 2011-10-15
I can't post the code anymore because i disconnected my ethernet, but it said that my old driver, bcmwlhigh6, could'nt be loaded, even though i deleted it from ndiswrapper.

---

