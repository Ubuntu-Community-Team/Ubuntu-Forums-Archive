---
title: "Toshiba Satelite p505d  dual booted with windows 7 and unbuntu 11.04"
date: 2011-06-13
forum: Networking &amp; Wireless
---

### Post by Mistey82 on 2011-06-13
I need HELP WITH my wireless and ethernet I am knew to linux and very aggravated being that I have been trying to figure this out on my own for a week now . here are the spec that I got 


mistey@mistey-laptop:~$ lsusb
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 045e:00e1 Microsoft Corp. Wireless Laser Mouse 6000 Reciever
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 04f2:b128 Chicony Electronics Co., Ltd 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
mistey@mistey-laptop:~$ sudo lsmod
[sudo] password for mistey: 
Module                  Size  Used by
parport_pc             36959  0 
ppdev                  17113  0 
vesafb                 13761  1 
binfmt_misc            17565  1 
joydev                 17606  0 
snd_hda_codec_conexant    57511  1 
snd_hda_intel          33211  4 
snd_hda_codec         103804  2 snd_hda_codec_conexant,snd_hda_intel
snd_hwdep              13604  1 snd_hda_codec
snd_pcm                96391  3 snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30486  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61621  2 snd_seq_midi,snd_seq_midi_event
uvcvideo               72195  0 
snd_timer              29602  2 snd_pcm,snd_seq
snd_seq_device         14462  3 snd_seq_midi,snd_rawmidi,snd_seq
fglrx                2739144  51 
videodev               82052  1 uvcvideo
v4l2_compat_ioctl32    17078  1 videodev
snd                    67382  16 snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
ndiswrapper           249811  0 
sp5100_tco             13744  0 
psmouse                73535  0 
i2c_piix4              13303  0 
soundcore              12680  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
k10temp                13119  0 
sparse_keymap          13898  0 
serio_raw              13166  0 
shpchp                 37297  0 
video                  19438  0 
lp                     17825  0 
parport                46458  3 parport_pc,ppdev,lp
usbhid                 46956  0 
hid                    91020  1 usbhid
firewire_ohci          40370  0 
sdhci_pci              13989  0 
firewire_core          62646  1 firewire_ohci
crc_itu_t              12707  1 firewire_core
sdhci                  27387  1 sdhci_pci
pata_atiixp            13165  0 
atl1c                  41171  0 
ahci                   25951  2 
libahci                26642  1 ahci
mistey@mistey-laptop:~$ sudo lshw -C network
  *-network UNCLAIMED     
       description: Network controller
       product: RTL8192E Wireless LAN Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: ioport:1000(size=256) memory:c8000000-c8003fff
  *-network
       description: Ethernet interface
       product: AR8132 Fast Ethernet
       vendor: Atheros Communications
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: c0
       serial: 00:23:8b:fe:0a:35
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=atl1c driverversion=1.0.1.0-NAPI duplex=full firmware=N/A ip=192.168.1.29 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:45 memory:f0300000-f033ffff ioport:b000(size=128)
mistey@mistey-laptop:~$ 


someone please walk me through steps to fix this :(

---

### Post by chili555 on 2011-06-13
Please run and post:```
ndiswrapper -l
```That's a lower-case L for 'list.' Also post:```
lspci -nn | grep Realtek
dmesg | grep ndis
```The pipe symbol | is on the right side of my US keyboard on the same key with \. Thanks.

---

### Post by Mistey82 on 2011-06-13
mistey@mistey-laptop:~$ dmesg / grep ndis
Usage: dmesg [-c] [-n level] [-r] [-s bufsize]
mistey@mistey-laptop:~$ lspci -nn | grep Realtek
02:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8192E Wireless LAN Controller [10ec:8192] (rev 01)
mistey@mistey-laptop:~$ dmesg | grep ndis
[   18.701658] ndiswrapper version 1.56 loaded (smp=yes, preempt=no)
[   19.117406] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisAllocateNetBufferAndNetBufferList'
[   19.117417] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisAllocateMdl'
[   19.117424] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisMAllocateNetBufferSGList'
[   19.117431] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisMDeregisterMiniportDriver'
[   19.117438] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisMIndicateReceiveNetBufferLists'
[   19.117445] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisMFreeNetBufferSGList'
[   19.117452] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisAllocateIoWorkItem'
[   19.117463] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisMOidRequestComplete'
[   19.117478] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisMIndicateStatusEx'
[   19.117484] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisOpenConfigurationEx'
[   19.117514] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisFreeNetBufferListPool'
[   19.117520] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisFreeIoWorkItem'
[   19.117527] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisQueueIoWorkItem'
[   19.117536] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisMSetBusData'
[   19.117543] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisMSendNetBufferListsComplete'
[   19.117550] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisMRegisterMiniportDriver'
[   19.117556] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisFreeMdl'
[   19.117563] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisMDeregisterInterruptEx'
[   19.117570] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisFreeNetBufferList'
[   19.117580] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisMSetMiniportAttributes'
[   19.117586] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisAllocateMemoryWithTagPriority'
[   19.117599] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisMGetBusData'
[   19.117605] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisMDeregisterScatterGatherDma'
[   19.117618] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisMRegisterScatterGatherDma'
[   19.117625] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisMSynchronizeWithInterruptEx'
[   19.117632] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisMRegisterInterruptEx'
[   19.117638] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisAllocateNetBufferListPool'
[   19.117641] ndiswrapper (load_sys_files:206): couldn't prepare driver 'net819xp'
[   19.118332] ndiswrapper (load_wrap_driver:108): couldn't load driver net819xp; check system log for messages from 'loadndisdriver'
[   19.235589] usbcore: registered new interface driver ndiswrapper
mistey@mistey-laptop:~$ ndiswrapper -l
autorun : invalid driver!
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
net819xp : driver installed
    device (10EC:8192) present (alternate driver: r8192e_pci)

---

### Post by chili555 on 2011-06-13
You have the wrong driver for ndiswrapper and the built-in driver that will probably driver the device quite well is evidently also trying to load. If this were the doctors Toshiba, I'd remove ndiswrapper and troubleshoot the native driver r8192e_pci. Are you ready to proceed? If so, do:```
sudo ndiswrapper -e net819xp
sudo ndiswrapper -e autorun
sudo modprobe r8192e_pci
iwconfig
```Is your wireless working now? We may need to do a bit more fine tuning.

---

### Post by Mistey82 on 2011-06-13
mistey@mistey-laptop:~$ sudo ndiswrapper -e net819xp
[sudo] password for mistey: 
couldn't delete /etc/ndiswrapper/net819xp: No such file or directory
mistey@mistey-laptop:~$ sudo ndiswrapper -e autorun
couldn't delete /etc/ndiswrapper/autorun: No such file or directory
mistey@mistey-laptop:~$ sudo modprobe r8192e_pci
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
mistey@mistey-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan1     802.11bgn  Mode:Managed  Access Point: Not-Associated   
          Bit Rate:1 Mb/s   
          Retry:on   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/100  Signal level=0 dBm  Noise level=0 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

mistey@mistey-laptop:~$

---

### Post by chili555 on 2011-06-13
We're getting there. Now let's see:```
rfkill list all
cat /etc/modprobe.d/ndiswrapper
ls /etc/ndiswrapper
```Thanks.

---

### Post by Mistey82 on 2011-06-13
mistey@mistey-laptop:~$ rfkill list all
mistey@mistey-laptop:~$ cat /etc/modprobe.d/ndiswrapper
alias pci:v000007AAd00000044sv*sd*bc*sc*i* ndiswrapper
alias pci:v000007AAd00000046sv*sd*bc*sc*i* ndiswrapper
alias pci:v000007AAd00000047sv*sd*bc*sc*i* ndiswrapper
alias pci:v000010ECd00008171sv*sd*bc*sc*i* ndiswrapper
alias pci:v000010ECd00008172sv0000E020sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008172sv*sd*bc*sc*i* ndiswrapper
alias pci:v000010ECd00008173sv*sd*bc*sc*i* ndiswrapper
alias pci:v000010ECd00008174sv*sd*bc*sc*i* ndiswrapper
alias pci:v000010ECd00008190sv00003304sd00001186bc*sc*i* ndiswrapper
alias pci:v000010ECd00008190sv00008190sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008190sv0000C12Dsd00001259bc*sc*i* ndiswrapper
alias pci:v000010ECd00008190sv*sd*bc*sc*i* ndiswrapper
alias pci:v000010ECd00008192sv0000005Esd00001B0Abc*sc*i* ndiswrapper
alias pci:v000010ECd00008192sv00006896sd00001462bc*sc*i* ndiswrapper
alias pci:v000010ECd00008192sv00007160sd0000144Fbc*sc*i* ndiswrapper
alias pci:v000010ECd00008192sv00008152sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008192sv00008153sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008192sv00008181sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008192sv00008182sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008192sv00008183sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008192sv00008186sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008192sv00008192sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008192sv0000E01Csd0000105Bbc*sc*i* ndiswrapper
alias pci:v000010ECd00008192sv0000E01Dsd0000105Bbc*sc*i* ndiswrapper
alias pci:v000010ECd00008192sv*sd*bc*sc*i* ndiswrapper
mistey@mistey-laptop:~$ ls /etc/ndiswrapper
mistey@mistey-laptop:~$ ls /etc/ndiswrapper
mistey@mistey-laptop:~$

---

### Post by Mistey82 on 2011-06-13
oh yea and thanks for taking the time with me I really appreciate this , I've been at this for days :KS

---

### Post by chili555 on 2011-06-13
I believe you can safely do:```
sudo rm /etc/modprobe.d/ndiswrapper
sudo gedit /etc/modules
```Add one line at the end:```
r8192e_pci
```Proofread carefully twice, save and close gedit. Reboot and tell us if your wireless is working. If not, please post:```
dmesg | grep 819
```Thanks.

---

### Post by Mistey82 on 2011-06-13
0.000000] PERCPU: Embedded 28 pages/cpu @ffff8800b7c00000 s84416 r8192 d22080 u1048576
[    0.000000] pcpu-alloc: s84416 r8192 d22080 u1048576 alloc=1*2097152
[    0.630338] pci 0000:02:00.0: [10ec:8192] type 0 class 0x000280
[   22.595369] r8192e_pci: module is from the staging directory, the quality is unknown, you have been warned.
[   22.610773] Linux kernel driver for RTL8192 based WLAN cards
[   22.610862] rtl819xE 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   22.610873] rtl819xE 0000:02:00.0: setting latency timer to 64
[   24.420100] rtl819xE:Download Firmware: Put code fail!
[   24.420112] rtl819xE:ERR in CPUcheck_maincodeok_turnonCPU()
[   24.420117] rtl819xE:ERR in init_firmware()
[   24.420124] rtl819xE:ERR!!! _rtl8192_up(): initialization is failed!
[   27.819252] [fglrx] Gart USWC size:1160 M.
[   27.819267] [fglrx] Gart cacheable size:459 M.
[   27.819280] [fglrx] Reserved FB block: Shared offset:0, size:1000000 
[   27.819288] [fglrx] Reserved FB block: Unshared offset:fffb000, size:5000

---

### Post by chili555 on 2011-06-13
> rtl819xE:ERR in CPUcheck_maincodeok_turnonCPU()I think we have finally discovered why your wireless device didn't work and then motivated you to try ndiswrapper! Let's have a look at your firmware files:```
ls -al /lib/firmware/RTL8192E
```

---

### Post by Mistey82 on 2011-06-13
total 76
drwxr-xr-x  2 root root  4096 2011-06-12 23:02 .
drwxr-xr-x 59 root root 20480 2011-06-12 23:28 ..
-rw-r--r--  1 root root   344 2010-11-18 15:20 boot.img
-rw-r--r--  1 root root   848 2010-11-18 15:20 data.img
-rw-r--r--  1 root root 42944 2010-11-18 15:20 main.img

---

### Post by chili555 on 2011-06-13
Your firmware files look perfect. The same size, permissions, etc. as on my machine. That's the good news.

The bad news is that I've discovered it's a known bug: [https://bugs.launchpad.net/ubuntu/+source/linux-firmware/+bug/508746](https://bugs.launchpad.net/ubuntu/+source/linux-firmware/+bug/508746)

[https://bugs.launchpad.net/ubuntu/+source/linux-firmware/+bug/674663](https://bugs.launchpad.net/ubuntu/+source/linux-firmware/+bug/674663)

I'm still looking, so I'll post back in a few...

---

### Post by chili555 on 2011-06-13
[https://lists.linux-foundation.org/pipermail/bugme-new/2010-November/026165.html](https://lists.linux-foundation.org/pipermail/bugme-new/2010-November/026165.html)

I haven't found a fix yet, still looking. My next step is to see if Realtek has a newer driver version we might try.

Maybe ndiswrapper is not such a bad idea!

---

### Post by Mistey82 on 2011-06-13
okay well I just brought a neatgear wg111 v3 wireless network usb i put the cd in but how do i install it to ubuntu 11.04 ???

---

### Post by chili555 on 2011-06-13
Please show me:```
lsusb
```Thanks.

---

### Post by Mistey82 on 2011-06-13
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 045e:00e1 Microsoft Corp. Wireless Laser Mouse 6000 Reciever
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 04f2:b128 Chicony Electronics Co., Ltd 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 0846:4260 NetGear, Inc. WG111v3 54 Mbps Wireless [realtek RTL8187B]
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

---

### Post by chili555 on 2011-06-13
> ID 0846:4260 NetGear, Inc. WG111v3 54 Mbps Wireless [realtek RTL8187B]This is supposed to work with the module rtl8187. I think you just need to insert it and be off and running. If not, please do:```
sudo modprobe rtl8187
iwconfig
```Do you have a new wireless interface, wlan1 perhaps?

---

### Post by Mistey82 on 2011-06-13
yes the netgear usb plug in wg111 v3 i just went by bestbuy and brought it about an hour ago I thought it would help but >>>>..... no I still have to keep ethernet pluged in for internet 
and the little triangle in the top right hand corner doesn't register anything at all

---

### Post by chili555 on 2011-06-13
Please detach the ethernet cable and do:```
sudo modprobe rtl8187
iwconfig
dmesg | grep -i rtl
```Please post the result.

---

### Post by Mistey82 on 2011-06-13
mistey@mistey-laptop:~$ sudo modprobe rtl8187
[sudo] password for mistey: 
mistey@mistey-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan1     802.11bgn  Mode:Managed  Access Point: Not-Associated   
          Bit Rate:1 Mb/s   
          Retry:on   RTS thr:off   Fragment thr: off
          Power Management:off
          Link Quality=0/100  Signal level=0 dBm  Noise level=0 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
mistey@mistey-laptop:~$ dmesg | grep -i rtl
[   20.485527] Linux kernel driver for RTL8192 based WLAN cards
[   20.485615] rtl819xE 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   20.485628] rtl819xE 0000:02:00.0: setting latency timer to 64
[   22.780131] rtl819xE:Download Firmware: Put code fail!
[   22.780146] rtl819xE:ERR in CPUcheck_maincodeok_turnonCPU()
[   22.780154] rtl819xE:ERR in init_firmware()
[   22.780162] rtl819xE:ERR!!! _rtl8192_up(): initialization is failed!
[   24.036267] ieee80211 phy0: hwaddr e0:91:f5:9e:54:62, RTL8187BvE V0 + rtl8225z2, rfkill mask 2
[   24.059871] rtl8187: Customer ID is 0x00
[   24.062779] Registered led device: rtl8187-phy0::radio
[   24.065128] Registered led device: rtl8187-phy0::tx
[   24.067938] Registered led device: rtl8187-phy0::rx
[   24.075658] rtl8187: wireless switch is on
[   24.077854] usbcore: registered new interface driver rtl8187
[  739.489383] ieee80211 phy1: hwaddr e0:91:f5:9e:54:62, RTL8187BvE V0 + rtl8225z2, rfkill mask 2
[  739.535664] rtl8187: Customer ID is 0x00
[  739.535743] Registered led device: rtl8187-phy1::radio
[  739.535778] Registered led device: rtl8187-phy1::tx
[  739.535801] Registered led device: rtl8187-phy1::rx
[  739.536521] rtl8187: wireless switch is on
mistey@mistey-laptop:~$

---

### Post by chili555 on 2011-06-13
> rtl8187: wireless switch is onIs there a switch on your laptop? Does the message change if you manipulate the switch?

The first time I saw this a few years ago, I thought I was ready for the crazy house; however, I turned off the switch on my laptop, plugged in a USB wireless device and it complained about the switch!

---

### Post by Mistey82 on 2011-06-13
Well I did have the switch off but i just put it back on lol now what ... I am determined to get this

---

### Post by Mistey82 on 2011-06-13
this is the message with it turned on 


mistey@mistey-laptop:~$ dmesg | grep -i rtl
[   20.485527] Linux kernel driver for RTL8192 based WLAN cards
[   20.485615] rtl819xE 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   20.485628] rtl819xE 0000:02:00.0: setting latency timer to 64
[   22.780131] rtl819xE:Download Firmware: Put code fail!
[   22.780146] rtl819xE:ERR in CPUcheck_maincodeok_turnonCPU()
[   22.780154] rtl819xE:ERR in init_firmware()
[   22.780162] rtl819xE:ERR!!! _rtl8192_up(): initialization is failed!
[   24.036267] ieee80211 phy0: hwaddr e0:91:f5:9e:54:62, RTL8187BvE V0 + rtl8225z2, rfkill mask 2
[   24.059871] rtl8187: Customer ID is 0x00
[   24.062779] Registered led device: rtl8187-phy0::radio
[   24.065128] Registered led device: rtl8187-phy0::tx
[   24.067938] Registered led device: rtl8187-phy0::rx
[   24.075658] rtl8187: wireless switch is on
[   24.077854] usbcore: registered new interface driver rtl8187
[  739.489383] ieee80211 phy1: hwaddr e0:91:f5:9e:54:62, RTL8187BvE V0 + rtl8225z2, rfkill mask 2
[  739.535664] rtl8187: Customer ID is 0x00
[  739.535743] Registered led device: rtl8187-phy1::radio
[  739.535778] Registered led device: rtl8187-phy1::tx
[  739.535801] Registered led device: rtl8187-phy1::rx
[  739.536521] rtl8187: wireless switch is on

---

### Post by Mistey82 on 2011-06-13
this is the message when i take out the usb 


   20.485527] Linux kernel driver for RTL8192 based WLAN cards
[   20.485615] rtl819xE 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   20.485628] rtl819xE 0000:02:00.0: setting latency timer to 64
[   22.780131] rtl819xE:Download Firmware: Put code fail!
[   22.780146] rtl819xE:ERR in CPUcheck_maincodeok_turnonCPU()
[   22.780154] rtl819xE:ERR in init_firmware()
[   22.780162] rtl819xE:ERR!!! _rtl8192_up(): initialization is failed!
[   24.036267] ieee80211 phy0: hwaddr e0:91:f5:9e:54:62, RTL8187BvE V0 + rtl8225z2, rfkill mask 2
[   24.059871] rtl8187: Customer ID is 0x00
[   24.062779] Registered led device: rtl8187-phy0::radio
[   24.065128] Registered led device: rtl8187-phy0::tx
[   24.067938] Registered led device: rtl8187-phy0::rx
[   24.075658] rtl8187: wireless switch is on
[   24.077854] usbcore: registered new interface driver rtl8187
[  739.489383] ieee80211 phy1: hwaddr e0:91:f5:9e:54:62, RTL8187BvE V0 + rtl8225z2, rfkill mask 2
[  739.535664] rtl8187: Customer ID is 0x00
[  739.535743] Registered led device: rtl8187-phy1::radio
[  739.535778] Registered led device: rtl8187-phy1::tx
[  739.535801] Registered led device: rtl8187-phy1::rx
[  739.536521] rtl8187: wireless switch is on

---

### Post by chili555 on 2011-06-13
> [ [COLOR="Red"]739.536521[/COLOR]] rtl8187: wireless switch is onThe time-stamp is the same; so no change. Please try:```
sudo rfkill unblock all
dmesg | grep 8187
```Any new listings?

Does the wireless light or LED change? May I see:```
lsmod | grep -e wmi -e laptop
```

---

### Post by Mistey82 on 2011-06-13
first command did nothing here's the rest 



mistey@mistey-laptop:~$ dmesg | grep 8187
[   26.039314] ieee80211 phy0: hwaddr e0:91:f5:9e:54:62, RTL8187BvE V0 + rtl8225z2, rfkill mask 2
[   26.061242] rtl8187: Customer ID is 0x00
[   26.061368] Registered led device: rtl8187-phy0::radio
[   26.061431] Registered led device: rtl8187-phy0::tx
[   26.061485] Registered led device: rtl8187-phy0::rx
[   26.064479] rtl8187: wireless switch is on
[   26.065545] usbcore: registered new interface driver rtl8187
mistey@mistey-laptop:~$ lsmod | grep -e wmi -e laptop
snd_rawmidi            30486  1 snd_seq_midi
snd_seq_device         14462  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    67382  13 snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device

---

### Post by chili555 on 2011-06-13
I'm done for this evening; see you tomorrow.

---

### Post by Mistey82 on 2011-06-13
okay whew yea i'm tired thanks

---

### Post by moaoci on 2011-06-14
By now, with only the rtl8192e plugged in, you should be seeing a red exclamation mark over the wireless icon on the top right corner of your screen.  It probably means that the wireless is recognized but unusable.

The first reason for this is that the linux kernel now comes with the staging rtl819x drivers activated.  And guess what, staging rtl8192e does not work as is and it seems to lock out the wireless.  Some people have found a way to make the staging driver work, I didn't even try since my realtek driver works for me.

So the first thing to do is to delete the staging driver from the linux kernel (and delete it again at each new linux kernel version ) (  Open a terminal, sudo nautilus, and then go to  filesystem/lib/modules/(your current kernel  number)/kernel/driver/staging.  Find the RTL8192E directory and delete  it (yes, delete it.).) Then reboot.  

With the staging driver removed, it will be easier to get whatever solution you are trying to implement succeed.

For my part,  I am not using NDISWrapper;  I am using the realtek RTL8192E driver (version 13 on Ubuntu 10.04 on my Toshiba satellite L505D). You can get your own realtek rtl8192e driver only by writing to [email]wlanfae@realtek.com[/email] and specify your Ubuntu version and 64bits.  If the driver you receive doesn't work for you, write back and they will work with you to correct whatever problem you get. I did that with them and the result was the version 13, the first realtek driver to work just out of the box.  

I could help you more by trying 11.04 but I do not want to go to Ubuntu 11.04 ( I don't like it on my desktop and I prefer the 10.04 look).   

See[ http://ubuntuforums.org/showpost.php?p=9951334&postcount=12]("http://http://ubuntuforums.org/showpost.php?p=9951334&postcount=12")
and other post from me for more details...

Hope this helps

---

### Post by chili555 on 2011-06-14
> So the first thing to do is to delete the staging driver from the linux kernel (and delete it again at each new linux kernel version ) ( Open a terminal, sudo nautilus, and then go to filesystem/lib/modules/(your current kernel number)/kernel/driver/staging. Find the RTL8192E directory and delete it (yes, delete it.).) Then reboot. It's certainly worth a shot, Mistey. Let me know if you need more help. Then let's continue our rtl8187 efforts.

---

