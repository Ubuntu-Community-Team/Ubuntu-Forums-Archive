---
title: "DWA 130 REV C and 11.04 trouble!"
date: 2011-05-09
forum: Networking &amp; Wireless
---

### Post by Dammittman on 2011-05-09
[SIZE=2]I have really been working on trying to find out what the H is up with my wireless adapter and from what i have read that seems to be the only "catch" to using linux compared to any other OS . I love the look and feel and customization of linux and with 11.04 i m hard pressed to say an OS could be better. So far i have tried ndis with no luck and I am not quite familiar enough with linux do do the whole make , make install and all that, not sure i understand all that yet. Anyone willing to help could reply here or email me , feel free , I am pretty sure everyone has a few bugs they are dealing with still and i wish you good health and great times. THX [EMAIL="dammittman@gmail.com"]dammittman@gmail.com[/EMAIL] [/SIZE]

---

### Post by chili555 on 2011-05-10
Did you try ndiswrapper with the Windows XP drivers? That's what ndiswrapper is designed to work with. Windows 7 or Vista files will never work.

Please tell us more about your wireless card. Please open a terminal and run and post:```
lspci -nn
lsusb
ndiswrapper -l
```That last character is an L for list; not a one.

---

### Post by bkratz on 2011-05-10
@Chili555--as you know I always am interested in DWA130 problems (I have a version A) anyway the Linux drivers for the version C are at the following address:

[http://www.dlink.com/products/?tab=3&pid=DWA-130&rev=DWA-130_revC](http://www.dlink.com/products/?tab=3&pid=DWA-130&rev=DWA-130_revC)

The readme file is a little above me, but I am sure you will understand it!  The windows drivers (both the inf and sys are there too (not a .exe!).

---

### Post by chili555 on 2011-05-10
@OP-

I recommend you try the *XP* inf and sys files at the link bkratz provided.

---

### Post by Dammittman on 2011-07-23
yea I have tried NdisWrapper and tried to install the linux drivers from D-Link and its probably something silly easy to do but i just dont understand it , maybe the whole process of installing drivers ,,, on another note i ran lsusb and it shows my mouse keyboard and wireless card still no luck getting it to work though. maybe you can make some instructions i could understand so in the future i will be able to install things and be one big step closer to knowing my way around linux !!! Would love the help!!!!!

---

### Post by chili555 on 2011-07-23
Please open a terminal and run and post:```
lsusb
ndiswrapper -l
```That's a lower-case L for 'list." Thanks.

---

### Post by Dammittman on 2011-07-23
Lsusb
Bus 002 Device 006: ID 046d:c225 Logitech, Inc. G11/G15 Keyboard / G keys 
Bus 002 Device 005: ID 046d:c221 Logitech, Inc. G11/G15 Keyboard / Keyboard 
Bus 002 Device 004: ID 046d:c048 Logitech, Inc. 
Bus 002 Device 003: ID 046d:c223 Logitech, Inc. G11/G15 Keyboard / USB Hub 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
Bus 001 Device 002: ID 2001:3301 D-Link Corp. DWA-130 802.11n Wireless N Adapter(rev.C1) [Realtek RTL8192U] 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub 
    ndiswrapper -l
net8192u : driver installed 
    device (2001:3301) present (alternate driver: r8192u_usb)

---

### Post by chili555 on 2011-07-23
> ndiswrapper -l
[COLOR="Red"]net8192u : driver installed[/COLOR]
device (2001:3301) present (alternate driver: [COLOR="Red"]r8192u_usb[/COLOR]) This indicates that both the native driver and ndiswrapper are installed and probably conflicting. Let's see if there are any kernel messages that help us decide which is better and which to remove. Please run and post:```
dmesg | grep -e ndis -e 8192
```The pipe symbol | is on the right side of my US keyboard on the same key with \. Thanks.

---

### Post by Dammittman on 2011-07-23
Lsusb
Bus 002 Device 006: ID 046d:c225 Logitech, Inc. G11/G15 Keyboard / G keys 
Bus 002 Device 005: ID 046d:c221 Logitech, Inc. G11/G15 Keyboard / Keyboard 
Bus 002 Device 004: ID 046d:c048 Logitech, Inc. 
Bus 002 Device 003: ID 046d:c223 Logitech, Inc. G11/G15 Keyboard / USB Hub 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
Bus 001 Device 002: ID 2001:3301 D-Link Corp. DWA-130 802.11n Wireless N Adapter(rev.C1) [Realtek RTL8192U] 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub 
    ndiswrapper -l
net8192u : driver installed 
    device (2001:3301) present (alternate driver: r8192u_usb) 

    dmeag
 dmeag | grep -e ndis -e 8192 
No command 'dmeag' found, did you mean: 
 Command 'dmesg' from package 'util-linux' (main) 
dmeag: command not found

---

### Post by Dammittman on 2011-07-23
maybe worth mentioning , on my connections all i have is loopback or lo  and auto etho to select from

---

### Post by chili555 on 2011-07-23
> dmeag | grep -e ndis -e 8192 Please try:```
dmesg | grep -e ndis -e 8192 
```

---

### Post by Dammittman on 2011-07-23
Dmesg
dmesg | grep -e ndis -e 8192 
[    0.000000] PERCPU: Embedded 28 pages/cpu @ffff88007fc00000 s84416 r8192 d22080 u1048576 
[    0.000000] pcpu-alloc: s84416 r8192 d22080 u1048576 alloc=1*2097152 
[   18.240304] ndiswrapper version 1.56 loaded (smp=yes, preempt=no) 
[   22.863001] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisMRegisterMiniportDriver' 
[   22.863009] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisMIndicateReceiveNetBufferLists' 
[   22.863015] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisAllocateMemoryWithTagPriority' 
[   22.863021] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisAllocateMdl' 
[   22.863029] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisMSetMiniportAttributes' 
[   22.863034] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisFreeNetBufferListPool' 
[   22.863040] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisAllocateNetBufferAndNetBufferList' 
[   22.863048] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisMOidRequestComplete' 
[   22.863073] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisOpenConfigurationEx' 
[   22.863086] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisMIndicateStatusEx' 
[   22.863092] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisFreeNetBufferList' 
[   22.863106] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisAllocateIoWorkItem' 
[   22.863111] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisFreeIoWorkItem' 
[   22.863117] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisQueueIoWorkItem' 
[   22.863128] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisMDeregisterMiniportDriver' 
[   22.863134] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisMSendNetBufferListsComplete' 
[   22.863140] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisFreeMdl' 
[   22.863146] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisAllocateNetBufferListPool' 
[   22.863151] ndiswrapper (import:233): unknown symbol: WDFLDR.SYS:'WdfVersionBind' 
[   22.863155] ndiswrapper (import:233): unknown symbol: WDFLDR.SYS:'WdfVersionUnbind' 
[   22.863157] ndiswrapper (load_sys_files:206): couldn't prepare driver 'net8192u' 
[   22.863657] ndiswrapper (load_wrap_driver:108): couldn't load driver net8192u; check system log for messages from 'loadndisdriver' 
[   22.863710] usbcore: registered new interface driver ndiswrapper

---

### Post by chili555 on 2011-07-23
It obviously doesn't like ndiswrapper one bit!! Let's get rid of it for now:```
sudo ndiswrapper -e net8192u
sudo rm -rf /etc/ndiswrapper/*
```Please be very careful about typos here. Now do:```
sudo modprobe r8192u_usb
iwconfig
```Now that we have loaded the native driver, can you see networks when you click the Network Manager icon? If not, let's look at messages again:```
dmesg | grep 8192
```These are temporary steps, when we find out which works, we'll need to tweak a file or two to make it persistent.

---

### Post by Dammittman on 2011-07-23
damian@damian-desktop ~ $ sudo modprobe r8192u.usb  
 FATAL: Module r8192u.usb not found.  
 damian@damian-desktop ~ $ iw config  
 nl80211 not found.  
 damian@damian-desktop ~ $ dmesg | grep 8192  
 [    0.000000] PERCPU: Embedded 28 pages/cpu @ffff88007fc00000 s84416 r8192 d22080 u1048576  
 [    0.000000] pcpu-alloc: s84416 r8192 d22080 u1048576 alloc=1*2097152  
 [   22.140058] ndiswrapper (load_sys_files:206): couldn't prepare driver 'net8192u'  
 [   22.140532] ndiswrapper (load_wrap_driver:108): couldn't load driver net8192u; check system log for messages from 'loadndisdriver'

---

### Post by bkratz on 2011-07-24
> **Dammittman said:**
> damian@damian-desktop ~ $ [COLOR="Red"]sudo modprobe r8192u.usb[/COLOR]  
 FATAL: Module r8192u.usb not found.  
 damian@damian-desktop ~ $ iw config  
 nl80211 not found.  
 damian@damian-desktop ~ $ dmesg | grep 8192  
 [    0.000000] PERCPU: Embedded 28 pages/cpu @ffff88007fc00000 s84416 r8192 d22080 u1048576  
 [    0.000000] pcpu-alloc: s84416 r8192 d22080 u1048576 alloc=1*2097152  
 [   22.140058] ndiswrapper (load_sys_files:206): couldn't prepare driver 'net8192u'  
 [   22.140532] ndiswrapper (load_wrap_driver:108): couldn't load driver net8192u; check system log for messages from 'loadndisdriver'



From Dr. Chili's note

"
[COLOR="Red"]Please be very careful about typos here[/COLOR]. Now do:
Code:
sudo modprobe [COLOR="Red"]r8192u_usb[/COLOR]
iwconfig
"

note the difference?

---

### Post by chili555 on 2011-07-24
> ndiswrapper (load_sys_files:206): couldn't prepare driver 'net8192u' It looks like ndiswrapper is still loading. Please see if the file that does so is still around:```
ls /etc/modprobe.d | grep ndis
```If the command returns a file listing like /etc/modprobe.d/ndiswrapper or similar, remove it:```
sudo rm /etc/modprobe.d/ndiswrapper
```Now let's unload ndiswrapper:```
sudo rmmod -f ndiswrapper
```Now try again:```
sudo modprobe r8192u_usb
iwconfig
```Please be very careful about typos here.

---

### Post by Dammittman on 2011-07-24
lo        no wireless extensions.  
 

 eth0      no wireless extensions.  
 

 wlan0     802.11b/g/n  Mode:Managed  Access Point: Not-Associated    
           Bit Rate:1 Mb/s    
           Retry min limit:7   RTS thr:off   Fragment thr:off  
           Power Management:off  
           Link Quality=0/100  Signal level=0 dBm  Noise level=0 dBm  
           Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0  
           Tx excessive retries:0  Invalid misc:0   Missed beacon:0 



seriously I don't have typos usually ! THX

---

### Post by chili555 on 2011-07-25
After we removed ndiswrapper and loaded the native driver, we have a wireless interface wlan0. Can you click the Network Manager icon, see your network and connect? Does it scan?```
sudo iwlist wlan0 scan

```If these steps are not successful, please post:```
dmesg | grep -e wlan -e 819
```Thanks.

---

### Post by Dammittman on 2011-07-25
damian@damian-desktop ~ $ sudo iwlist wlan0 scan
[sudo] password for damian: 
Sorry, try again.
[sudo] password for damian: 
wlan0     Interface doesn't support scanning : Network is down

damian@damian-desktop ~ $ dmesg |grep -e wlan0 -e 819
[    0.000000] PERCPU: Embedded 28 pages/cpu @ffff88007fc00000 s84416 r8192 d22080 u1048576
[    0.000000] pcpu-alloc: s84416 r8192 d22080 u1048576 alloc=1*2097152
[    7.840207] r8192u_usb: module is from the staging directory, the quality is unknown, you have been warned.
[    7.849512] Linux kernel driver for RTL8192 based WLAN cards
[    8.376130] usbcore: registered new interface driver rtl819xU
[   11.618199] nvidia 0000:02:00.0: PCI INT A -> Link[APC8] -> GSI 16 (level, low) -> IRQ 16
[   17.283021] rtl819xU:request firmware fail!
[   17.283026] rtl819xU:ERR in init_firmware()
[   17.283029] rtl819xU:ERR!!! rtl8192_adapter_start(): Firmware download is failed
[   17.283031] rtl819xU:ERR!!! _rtl8192_up(): initialization is failed!
[   17.675518] rtl819xU:request firmware fail!
[   17.675523] rtl819xU:ERR in init_firmware()
[   17.675526] rtl819xU:ERR!!! rtl8192_adapter_start(): Firmware download is failed
[   17.675528] rtl819xU:ERR!!! _rtl8192_up(): initialization is failed!
damian@damian-desktop ~ $ dmesg | grep -e wlan -e 819
[    0.000000] PERCPU: Embedded 28 pages/cpu @ffff88007fc00000 s84416 r8192 d22080 u1048576
[    0.000000] pcpu-alloc: s84416 r8192 d22080 u1048576 alloc=1*2097152
[    7.840207] r8192u_usb: module is from the staging directory, the quality is unknown, you have been warned.
[    7.849512] Linux kernel driver for RTL8192 based WLAN cards
[    8.376130] usbcore: registered new interface driver rtl819xU
[   11.618199] nvidia 0000:02:00.0: PCI INT A -> Link[APC8] -> GSI 16 (level, low) -> IRQ 16
[   17.283021] rtl819xU:request firmware fail!
[   17.283026] rtl819xU:ERR in init_firmware()
[   17.283029] rtl819xU:ERR!!! rtl8192_adapter_start(): Firmware download is failed
[   17.283031] rtl819xU:ERR!!! _rtl8192_up(): initialization is failed!
[   17.675518] rtl819xU:request firmware fail!
[   17.675523] rtl819xU:ERR in init_firmware()
[   17.675526] rtl819xU:ERR!!! rtl8192_adapter_start(): Firmware download is failed
[   17.675528] rtl819xU:ERR!!! _rtl8192_up(): initialization is failed!

---

### Post by chili555 on 2011-07-25
> rtl819xU:ERR in init_firmware()Your driver version requires firmware. Please see this post and follow the procedure carefully. Post back if you get stuck. [http://ubuntuforums.org/showpost.php?p=10339484&postcount=29](http://ubuntuforums.org/showpost.php?p=10339484&postcount=29)

---

### Post by Dammittman on 2011-07-25
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     802.11b/g linked  ESSID:"6YNQV"  
          Mode:Managed  Frequency=2.462 GHz  Access Point: 00:24:D2:C4:84:4F   
          Bit Rate=36 Mb/s   
          Retry min limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=69/100  Signal level=-66 dBm  Noise level=-104 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

I don't even know you , and I love you ! THX A TON man!

---

### Post by chili555 on 2011-07-25
It looks like you are connected beautifully! Your iwconfig is even smiling. I'm glad it's working. Would you please use thread tools at the top and Mark Solved?

---

