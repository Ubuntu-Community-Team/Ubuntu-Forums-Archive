---
title: "Wireless Intel 3945abg Help"
date: 2009-12-28
forum: Networking &amp; Wireless
---

### Post by DrDmoney on 2009-12-28
Alright I am very new to Ubuntu. I have tried to use it before and have never got my head around on how to install broken drivers. I am completely tired of Windows so I am making a switch for good. When I first installed Ubuntu 9.10 yesterday my wireless was working. Now my wireless is not.

Gateway C-142XL - Link for specifications
Intel 3945abg Wireless

I ran "sudo lshw -C network" in the terminial and got this.
>   *-network               
       description: Ethernet interface
       product: 82566MC Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth0
       version: 03
       serial: 00:e0:b8:d0:54:dd
       size: 100MB/s
       capacity: 1GB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=1.0.2-k2 duplex=full firmware=0.3-0 ip=192.168.2.2 latency=0 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: irq:27 memory:f8500000-f851ffff memory:f8524000-f8524fff ioport:1800(size=32)
  *-network UNCLAIMED
       description: Network controller
       product: PRO/Wireless 3945ABG [Golan] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress cap_list
       configuration: latency=0
       resources: memory:f8100000-f8100fff
I am new to Ubuntu so more information is better.

---

### Post by chili555 on 2009-12-28
Please see here: [https://help.ubuntu.com/community/NetworkManager0.7](https://help.ubuntu.com/community/NetworkManager0.7) especially:> Network Manager aims for Network Connectivity which "Just Works". The computer should use the wired network connection when it's plugged in, but automatically switch to a wireless connection when the user unplugs it and walks away from the desk. Likewise, when the user plugs the computer back in, the computer should switch back to the wired connection. The user should, most times, not even notice that their connection has has been managed for them; they should simply see uninterrupted network connectivity.You have a connection by ethernet:> ip=192.168.2.2 latency=0 link=yesI suggest you detach the ethernet cable and try again. If this doesn't help, please open a terminal and do:```
dmesg | grep iwl
```Post the result.

---

### Post by DrDmoney on 2009-12-28
> [   24.514055] iwl3945 0000:02:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
[   24.535309] iwl3945 0000:02:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
[   24.556569] iwl3945 0000:02:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
[   24.577834] iwl3945 0000:02:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
[   24.599085] iwl3945 0000:02:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
[   24.620339] iwl3945 0000:02:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
[   24.641594] iwl3945 0000:02:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
[   24.655299] iwl3945 0000:02:00.0: Error: saturation power is -1, less than minimum expected 40
[   24.655301] iwl3945 0000:02:00.0: Invalid power index
[   24.655304] iwl3945 0000:02:00.0: initializing driver failed
[   24.655330] iwl3945 0000:02:00.0: PCI INT A disabled
[   24.655981] iwl3945: probe of 0000:02:00.0 failed with error -5

I was connected to a wire because my wireless went down.

---

### Post by DrDmoney on 2009-12-28
I am sorry but I just cant fix this problem. I hate this headache. I have tried a  windows wireless driver method but that failed. I also am trying IPW39451.2.2 but I am getting lost with that. I know that for experts with linux its a easy fix. I am however no expert with linux. I keep running into errors. I follow directions, but it just won't work. Any help at all is appreciated.

---

### Post by blackienl on 2009-12-28
I've had alot of problems with my intel3945 as well with network manager. Quick and easy solution that worked for my situation was to replace it with Wicd. Just paste this in the terminal window to install and replace network manager.
 ```
sudo apt-get install wicd

```

---

### Post by margazhang on 2009-12-29
blackienl is right - just install wicd to replace NM.

If you are not comfortable with the command line install, open Synaptic and search for wicd to install it. The install will remove NM and replace it with wicd. 

Make sure you have a wired connection before installing wicd.

---

### Post by chili555 on 2009-12-29
With all due respect to my esteemed friends, Wicd isn't going to fix this:> [ 24.641594] iwl3945 0000:02:00.0: MAC is in deep sleep!. CSR_GP_CNTRL = 0xFFFFFFFF
[ 24.655299] iwl3945 0000:02:00.0: Error: saturation power is -1, less than minimum expected 40
[ 24.655301] iwl3945 0000:02:00.0: Invalid power index
[ 24.655304] iwl3945 0000:02:00.0: initializing driver failedDoes this happen upon resuming from sleep or suspend only, or on cold boot? Please do:```
sudo rmmod -f iwl3945
sudo modprobe iwl3945
dmesg | grep iwl
```Does it look like your wireless interface comes to life?

---

### Post by DrDmoney on 2009-12-29
Wicd didn't work as expected. I know that this has to be a driver malfunction, or a driver missing. 
Sorry chili555 your method didn't work. It brings up the same arror as before.

This is exactly what I did. I intstalled ubuntu. My wireless worked. I then ubdated ubuntu, and turned off the computer for the night by shutting down. I started it back up and my wireless didn't work. The option to turn  on was missing.

---

### Post by chili555 on 2009-12-31
> I know that this has to be a driver malfunction, or a driver missing. The driver is present but misbehaving. If you boot into an earlier kernel, 2.6.31-14-generic, perhaps, by interrupting the boot process with *Esc* and selecting an earlier version, does your wireless work? If so, I'd open Synaptic and search for *linux-image-2.6.31-16-generic* and right-click and select 'Mark for re-installation.' Then reboot into the latest (now re-installed) kernel and see if the driver and wireless are now working. 

Do you have *linux-backports-modules* installed? There is a newer version of *iwl3945* there.

---

