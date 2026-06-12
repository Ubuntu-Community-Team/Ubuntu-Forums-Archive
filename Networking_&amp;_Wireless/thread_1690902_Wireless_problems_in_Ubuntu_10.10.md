---
title: "Wireless problems in Ubuntu 10.10"
date: 2011-02-19
forum: Networking &amp; Wireless
---

### Post by danba185 on 2011-02-19
Hello, I'm quite new to Linux and Ubuntu 10.10. As a lot of other people I have problems with the wireless connection to my router (the wired connection works fine). I have tried all the methods I could find on Internet but nothing seems to work for me, I'm using an old laptop (Acer Travelmate 2460 series). At the top bar in the network drop-down list, the device not ready (firmware missing) is displayed under Wireless Networks. I haven't familiarised with the Network manager and I'll list all the things I have tried, but also some other useful information:


My first approach was this:
System -> Administration -> Additional Drivers

Tried to activate: Broadcom B43 wireless driver 
(Supported chipsets:- BCM4306/3- BCM4311- BCM4312- BCM4318)

Resulted in: SystemError: installArchives() failed
-------------------------------------------------------------------------------------------------------------

I have followed the tutorial [[HTML]http://wireless.kernel.org/en/users/Drivers/b43[/HTML]]("http://wireless.kernel.org/en/users/Drivers/b43") including commands like: 
sudo apt-get install b43-fwcutter
but as you can figure out,  it didn't work for me. 
-------------------------------------------------------------------------------------------------------------

The last thing I really thought would work for was this:
sudo apt-get --purge remove firmware-b43-installer
sudo apt-get --purge remove dkms
sudo apt-get --purge remove bcmwl-kernel-source
sudo apt-get install bcmwl-kernel-source
sudo reboot
but it didn't work either.
-------------------------------------------------------------------------------------------------------------
Useful printouts from the terminal:

```

ifconfig -a
eth0      Link encap:Ethernet  HWaddr XX:XX:XX:XX:XX:XX  
          inet addr:192.168.0.4  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: XXXX::XXX:XXXX:XXXX:XXXX/XX Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1178 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1145 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1103773 (1.1 MB)  TX bytes:208525 (208.5 KB)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:28 errors:0 dropped:0 overruns:0 frame:0
          TX packets:28 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:2016 (2.0 KB)  TX bytes:2016 (2.0 KB)

wlan0     Link encap:Ethernet  HWaddr YY:YY:YY:YY:YY:YY (not the same as above)  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          
-------------------------------------------------------------------------------------------------------------          
sudo lspci -vv
...
09:04.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
    Subsystem: AMBIT Microsystem Corp. TravelMate 2410
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap- 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 64
    Interrupt: pin A routed to IRQ 22
    Region 0: Memory at d0300000 (32-bit, non-prefetchable) [size=8K]
    Kernel driver in use: b43-pci-bridge
    Kernel modules: ssb
      
------------------------------------------------------------------------------------------------------------- 
sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: 88E8038 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: eth0
       version: 14
       serial: XX:XX:XX:XX:XX:XX
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.28 duplex=full firmware=N/A ip=192.168.0.4 latency=0 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: irq:41 memory:d0200000-d0203fff ioport:a000(size=256)
  *-network
       description: Network controller
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 4
       bus info: pci@0000:09:04.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64
       resources: irq:22 memory:d0300000-d0301fff
  *-network DISABLED
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: YY:YY:YY:YY:YY:YY
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=b43 driverversion=2.6.35-22-generic firmware=N/A link=yes multicast=yes wireless=IEEE 802.11bg

------------------------------------------------------------------------------------------------------------- 
rfkill list all
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

------------------------------------------------------------------------------------------------------------- 
$sudo iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off       


```I have also tried the following commands without any success:
sudo rfkill unblock all 
rfkill list

Then I changed WirelessEnabled=true in /var/lib/NetworkManager/NetworkManager.state but nothing spectacularly happened. 

I'm grateful for any kind of assistance.
/Daniel

---

### Post by jermanbdogg on 2011-02-20
I had issues with the broadcom chip as well. I managed to get mine fixed. Perhaps I can help. What is the output of:

lspci -vnn | grep 14e4

---

### Post by danba185 on 2011-02-21
Hello, here is the output from the terminal:

```

lspci -vnn | grep 14e4
09:04.0 Network controller [0280]: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller [14e4:4318] (rev 02)

```

---

### Post by jermanbdogg on 2011-02-23
Sorry for the delay. Have you tried installing the latest driver from Broadcom by source? (latest is 5.100.82.38) according to broadcom:
[http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php). 

Unfortunately, that is all that I can think of since you already tried the kernel.org guide (thats what i used). 

I can help walk through installing from source if you need it.

---

### Post by danba185 on 2011-02-25
Unfortunately did not your proposed method work for me. I went through the readme file and found this:

Some distros (Ubuntu and Fedora at the least) already have a version of
this driver in their repositories precompiled, tested and ready to go.
You just use the package manager to install the proper package ...

And then:

Ubuntu:
------
From the shell:
sudo apt-get update 
sudo apt-get --reinstall install bcmwl-kernel-source

Reboot

Now go back to System->Administration->Hardware Drivers
and you should see the driver enabled and working.

This resulted in: SystemError: installArchives() failed

----------------------------------------------------------
I suppose this is same approach as the one I have tried before:
sudo apt-get --purge remove firmware-b43-installer
sudo apt-get --purge remove dkms
sudo apt-get --purge remove bcmwl-kernel-source
sudo apt-get install bcmwl-kernel-source
sudo reboot


Do you think it will work better if I try the other method which is mentioned in the readme file? I.e. installing everything step by step?

---

