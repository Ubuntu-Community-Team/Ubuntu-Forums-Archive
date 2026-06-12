---
title: "Azio AWD102N wireless card-rt3562 driver install woes"
date: 2011-07-17
forum: Networking &amp; Wireless
---

### Post by Tengo_Hambre on 2011-07-17
Hi all,

i recently purchased a new custom-built computer and thought i would give ubuntu a shot (read: i'm a linux noob).  i'm running 11.04.  anyway, i can't get my pci wireless card to work.  i downloaded the rt3562 driver from ralink's site, followed the directions in this tutorial [http://ubuntuforums.org/showthread.php?t=1608095](http://ubuntuforums.org/showthread.php?t=1608095)
 and i keep getting an error message when i try to do "sudo make":

```
make -C tools
make[1]: Entering directory `/home/brock/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217 2/tools'
gcc -g bin2h.c -o bin2h
make[1]: Leaving directory `/home/brock/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217 2/tools'
/home/brock/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217 2/tools/bin2h
make: /home/brock/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217: Command not found
make: *** [build_tools] Error 127
```i have build essential, the latest version of linux headers, and gcc installed

sudo apt-get install build-essential
```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```sudo apt-get install gcc
```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
gcc is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```uname -mr

```
2.6.38-10-generic-pae i686
```i have no idea what is causing this or why things aren't working...installing the rt2860 driver caused no such problems with the make command.

anyway, based on the "how to post a new thread" guidelines, i guess some of the following may be useful:

Lspci: 

```
04:00.0 Network controller: Ralink corp. Device 3062
    Subsystem: Ralink corp. Device 3062
    Flags: bus master, slow devsel, latency 32, IRQ 11
    Memory at fbbe0000 (32-bit, non-prefetchable) [size=64K]
    Capabilities: <access denied>
    Kernel modules: rt2800pci
```ifconfig

```
eth0      Link encap:Ethernet  HWaddr 50:e5:49:37:04:b9  
          inet6 addr: fe80::52e5:49ff:fe37:4b9/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:74 errors:0 dropped:74 overruns:0 frame:74
          TX packets:47 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:11374 (11.3 KB)  TX bytes:10134 (10.1 KB)
          Interrupt:42 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:32 errors:0 dropped:0 overruns:0 frame:0
          TX packets:32 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:2072 (2.0 KB)  TX bytes:2072 (2.0 KB)
```iwconfig

```

lo        no wireless extensions.

eth0      no wireless extensions.
```if any of you can help me with this, i would be very grateful.  thanks for taking the time to read!

---

### Post by chili555 on 2011-07-17
> DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217 [COLOR="Red"]2[/COLOR]I think it might be stumbling on the (2) in the file name that got created when you extracted the file. Is there one there? If so, right click the file and rename it RT3562. Then do:```
cd /home/brock/RT3562
sudo make
sudo alltherestofit
```If that doesn't fix it, post back and we'll help.

---

### Post by Tengo_Hambre on 2011-07-17
i don't know how you caught that, Chili, but you're truly something else.  Thanks!

---

### Post by chili555 on 2011-07-17
> **Tengo_Hambre said:**
> i don't know how you caught that, Chili, but you're truly something else.  Thanks!So it's working like a champ now? Please use thread tools at the top and Mark Solved.

I think I have made every mistake in the book ten or so times. Eventually, I learned a lot of things including the old (2) trick. I cursed myself for an hour before I figured it out a couple of years ago.

---

