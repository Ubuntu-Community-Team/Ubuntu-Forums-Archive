---
title: "Installing  Intel 4965AGN on 10.04"
date: 2011-07-04
forum: Networking &amp; Wireless
---

### Post by tpwjayson on 2011-07-04
Hi I am new to ubuntu. I installed 10.04 on my T61p laptop and everything works except for the wireless card. I tried to follow a few different directions for getting it to work but this may be above my skill level. 

Any help would be really appreciated

---

### Post by wolfen69 on 2011-07-04
Did you search **Hardware Drivers** for them? Go to System>Administration>Hardware Drivers. You will need to be wired to the net for this.

---

### Post by tpwjayson on 2011-07-05
Yeah one came up for the nvidia graphics card but not for the wireless

---

### Post by mikewhatever on 2011-07-05
Intel 4965AGN should work out of the box with Ubuntu, and it doesn't have a proprietary driver. If there is a switch of button, make sure it's on. If that doesn't help, post the outputs of the following from a terminal window:

```
ifconfig

sudo lshw -C network

rfkill list all
```

---

### Post by tpwjayson on 2011-07-05
It is on

ifconfig gives me

```
eth0      Link encap:Ethernet  HWaddr 00:1e:37:8c:f9:b9  
          inet addr:192.168.2.10  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::21e:37ff:fe8c:f9b9/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:226972 errors:0 dropped:0 overruns:0 frame:0
          TX packets:93730 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:326925029 (326.9 MB)  TX bytes:7448823 (7.4 MB)
          Memory:fe200000-fe220000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:20 errors:0 dropped:0 overruns:0 frame:0
          TX packets:20 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1200 (1.2 KB)  TX bytes:1200 (1.2 KB)

```


sudo lshw -C network 
```
*-network               
       description: Ethernet interface
       product: 82566MM Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth0
       version: 03
       serial: 00:1e:37:8c:f9:b9
       size: 100MB/s
       capacity: 1GB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=1.0.2-k2 duplex=full firmware=0.3-0 ip=192.168.2.10 latency=0 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: irq:30 memory:fe200000-fe21ffff memory:fe225000-fe225fff ioport:1840(size=32)
  *-network DISABLED
       description: Wireless interface
       product: PRO/Wireless 4965 AG or AGN [Kedron] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 61
       serial: 00:1f:3b:05:65:c9
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn latency=0 multicast=yes wireless=IEEE 802.11abgn
       resources: irq:32 memory:df2fe000-df2fffff

```

rfkill list all
```
0: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
1: tpacpi_bluetooth_sw: Bluetooth
	Soft blocked: no
	Hard blocked: no
2: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no

```

---

### Post by mikewhatever on 2011-07-05
The wireless interface is down for some reason, try bringing it up with the following:
```
sudo ifconfig wlan0 up
```

If successful, you should be able to connect to your network.

Can you also post the output of **dmesg | grep -i wlan0**.

---

### Post by tpwjayson on 2011-07-05
When I tried 

sudo ifconfig wlan0 up

i got ```
SIOCSIFFLAGS: Connection timed out

```

dmesg | grep -i wlan0

doesn't give me anything

---

### Post by tpwjayson on 2011-07-05
Any one have any other suggestions?

---

### Post by mikewhatever on 2011-07-06
No idea really. I am going to ask the mods to move your thread to the Networking and Wireless section where some real experts can see it. ;)

---

### Post by Elfy on 2011-07-06
Thread moved to Networking & Wireless.

---

### Post by chili555 on 2011-07-06
May we see:```
sudo modprobe iwlagn
dmesg | grep iwl
ls /lib/firmware | grep iwl
```Finally, Network Manager is designed to *disallow* a wireless connection if you have wired, which you do. Please detach the cable.

Some of these commands may return nothing. Please tell us because silence speaks volumes.

---

### Post by tpwjayson on 2011-07-06
Ok network cable unplugged. 

Here is what I get

```
sudo modprobe iwlagn 
WARNING: All config files need .conf: /etc/modprobe.d/emc2, it will be ignored in a future release.

```


```
dmesg | grep iwl
[   13.688854] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, 1.3.27k
[   13.688857] iwlagn: Copyright(c) 2003-2009 Intel Corporation
[   13.689008] iwlagn 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   13.689048] iwlagn 0000:03:00.0: setting latency timer to 64
[   13.689160] iwlagn 0000:03:00.0: Detected Intel Wireless WiFi Link 4965AGN REV=0x4
[   13.743099] iwlagn 0000:03:00.0: Tunable channels: 11 802.11bg, 13 802.11a channels
[   13.743300] iwlagn 0000:03:00.0: irq 32 for MSI/MSI-X
[   13.754929] phy0: Selected rate control algorithm 'iwl-agn-rs'
[   14.119431] iwlagn 0000:03:00.0: firmware: requesting iwlwifi-4965-2.ucode
[   14.142536] iwlagn 0000:03:00.0: loaded firmware version 228.61.2.24
[   18.148574] iwlagn 0000:03:00.0: START_ALIVE timeout after 4000ms.
[   22.168036] iwlagn 0000:03:00.0: START_ALIVE timeout after 4000ms.
jayson@jayson-laptop:~$ ls /lib/firmware | grep iwl

```

```
ls /lib/firmware | grep iwl
iwlwifi-1000-3.ucode
iwlwifi-3945-2.ucode
iwlwifi-4965-2.ucode
iwlwifi-5000-1.ucode
iwlwifi-5000-2.ucode
iwlwifi-5000-5.ucode

```


Thanks for the help

---

### Post by chili555 on 2011-07-06
> WARNING: All config files need .conf: /etc/modprobe.d/emc2, it will be ignored in a future release.Mind if we have a look?```
cat /etc/modprobe.d/emc2
```I am quite confident this is the issue; I have been Googling but haven't yet found the answer:> iwlagn 0000:03:00.0: START_ALIVE timeout after 4000ms.

---

### Post by tpwjayson on 2011-07-06
Ok here is what I get

```
cat /etc/modprobe.d/emc2
# Remove the '#' before 'install' below to prevent regular Linux programs
# from accessing the parallel port.  This also means that the linux
# parport number may not be used to identify the port in loadrt hal_parport.
#install parport_pc /bin/true

```

---

### Post by chili555 on 2011-07-07
The file is all commented out, but available in the proper wording in the future, if needed. Let's convert it to the proper format so you don't get those warnings:```
sudo mv /etc/modprobe.d/emc2 /etc/modprobe.d/emc2.conf
```Let's both keep Googling this:> iwlagn 0000:03:00.0: START_ALIVE timeout after 4000ms.I wonder if there are any interesting errors or warnings in demsg. Please post:```
dmesg | grep -i warn
dmesg | grep -i error
```

---

### Post by tpwjayson on 2011-07-07
Ran the first code and nothing came up

```
 dmesg | grep -i warn
[    0.000000] ACPI Warning: 32/64X length mismatch in Gpe1Block: 0/32 (20090903/tbfadt-526)
[    0.000000] ACPI Warning: Optional field Gpe1Block has zero address or length: 000000000000102C/0 (20090903/tbfadt-557)

```

The last code didn't give me anything

I will keep googling ```
iwlagn 0000:03:00.0: START_ALIVE timeout after 4000ms.

```

---

### Post by tpwjayson on 2011-07-10
I re-installed ubuntu 10.04 and wireless works now. Thanks for the help.

---

