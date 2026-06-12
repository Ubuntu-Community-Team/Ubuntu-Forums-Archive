---
title: "Belkin Play Wireless N USB Adapter"
date: 2010-08-07
forum: Networking &amp; Wireless
---

### Post by trona on 2010-08-07
Hello fellow Ubuntu users.  I am a newbie that has just recently set up a dual boot on my desktop with Ubuntu 10.04.  I really love the operating system, but I've been having some problems setting up my wireless network.  My router is a Belkin N Wireless, and my USB wireless adapter is a Belkin Play N.  I've installed Ndiswrapper and ndisgtk and have tried using these programs to install the requisite drivers with no luck whatsoever.  I've already been successfully using this wireless adapter to connect to the internet on Windows XP.  I discovered the drivers that are used in conjunction with this device by going (in Windows XP) to control panel &#8594; system &#8594; hardware &#8594; device driver and then looking for my device under network adapters and noting which driver it is using.  I copied the files bcmwlhigh5.inf and bcmwlhigh5.sys onto my external drive and put them in a folder that I named 'drivers' once I booted up in Linux again.  (Note, there are several other files in the windows XP folder on the installation CD (bcmh43xx.cat, bcmh43xx64.cat, and bcmwlhigh564.sys.)   I tried installing said drivers using Ndiswrapper through a terminal window by entering the following command:
 

 sudo ndiswrapper -i ~/drivers/bcmwlhigh5.inf
 

 I then ran the following command in terminal to see if the driver was installed and got the following results:
 ndiswrapper -l
 WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.  
 WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.  
 WARNING: /etc/modprobe.d/blacklist line 1: ignoring bad line starting with 'blacklist.conf'  
 bcmwlhigh5 : driver installed  
     device (050D:615A) present  
 

 On seeing that the driver was in fact installed, I next ran the following commands in terminal:
 sudo depmod -a
 sudo modprobe ndiswrapper
 

 I then ran the following command to check for errors:
 

 owner@ubuntu:~$ tail /var/log/messages  
 Aug  6 15:31:16 ubuntu kernel: [ 2476.107792] ndiswrapper version 1.55 loaded (smp=yes, preempt=no)  
 Aug  6 15:31:16 ubuntu kernel: [ 2476.232026] usb 1-5: reset high speed USB device using ehci_hcd and address 3  
 Aug  6 15:31:16 ubuntu loadndisdriver: loadndisdriver: load_driver(358): couldn't load driver bcmwlhigh5  
 Aug  6 15:31:16 ubuntu kernel: [ 2476.371567] usbcore: registered new interface driver ndiswrapper  
 Aug  6 15:33:06 ubuntu kernel: [ 2586.456211] usbcore: deregistering interface driver ndiswrapper  
 Aug  6 15:33:06 ubuntu kernel: [ 2586.457105] ndiswrapper (ntoskernel_exit:2677): object cb528e20(2) was not freed, freeing it now  
 Aug  6 15:33:06 ubuntu kernel: [ 2586.479670] ndiswrapper version 1.55 loaded (smp=yes, preempt=no)  
 Aug  6 15:33:06 ubuntu kernel: [ 2586.604028] usb 1-5: reset high speed USB device using ehci_hcd and address 3  
 Aug  6 15:33:06 ubuntu loadndisdriver: loadndisdriver: load_driver(358): couldn't load driver bcmwlhigh5  
 Aug  6 15:33:06 ubuntu kernel: [ 2586.743577] usbcore: registered new interface driver ndiswrapper  
 owner@ubuntu:~$  
 

 Note: When I go to System &#8594; Administration &#8594; Windows Wireless Drivers and open the program, I get a message reading “Unable to see if hardware is present”.


   
 I've already disabled the opensource driver that comes with Ubuntu 10.04 by typing the following commands in a terminal window:
 echo -e “blacklist.conf\blacklist ssb” | sudo tee -a /etc/modprobe.d/blacklist
 This is correct, yah?
 

 Here's some more useful information that I've gathered by running various commands in a terminal:
 

 owner@ubuntu:~$ sudo lsusb  
 Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub  
 Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub  
 Bus 003 Device 002: ID 046d:c01b Logitech, Inc. MX310 Optical Mouse  
 Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub  
 Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub  
 Bus 001 Device 005: ID 0bc2:3000 Seagate RSS LLC  
 Bus 001 Device 003: ID 050d:615a Belkin Components  
 Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub  
 

 owner@ubuntu:~$ lshw  
 WARNING: you should run this program as super-user.  
 ubuntu                     
     description: Computer  
     width: 32 bits  
   *-core  
        description: Motherboard  
        physical id: 0  
      *-memory  
           description: System memory  
           physical id: 0  
           size: 480MiB  
      *-cpu  
           product: Intel(R) Pentium(R) 4 CPU 2.60GHz  
           vendor: Intel Corp.  
           physical id: 1  
           bus info: cpu@0  
           version: 15.2.9  
           size: 2600MHz  
           width: 32 bits  
           capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe pebs bts cid xtpr  
           configuration: id=0  
         *-logicalcpu:0  
              description: Logical CPU  
              physical id: 0.1  
              width: 32 bits  
              capabilities: logical  
         *-logicalcpu:1  
              description: Logical CPU  
              physical id: 0.2  
              width: 32 bits  
              capabilities: logical  
         *-cache:0  
              description: L1 cache  
              physical id: 0  
              size: 8KiB  
         *-cache:1  
              description: L2 cache  
              physical id: 1  
              size: 512KiB  
      *-pci  
           description: Host bridge  
           product: 82865G/PE/P DRAM Controller/Host-Hub Interface  
           vendor: Intel Corporation  
           physical id: 100  
           bus info: pci@0000:00:00.0  
           version: 02  
           width: 32 bits  
           clock: 33MHz  
           configuration: driver=agpgart-intel  
           resources: irq:0 memory:f8000000-fbffffff(prefetchable)  
         *-display  
              description: VGA compatible controller  
              product: 82865G Integrated Graphics Controller  
              vendor: Intel Corporation  
              physical id: 2  
              bus info: pci@0000:00:02.0 
              version: 02  
              width: 32 bits  
              clock: 33MHz  
              capabilities: bus_master cap_list rom  
              configuration: driver=i915 latency=0  
              resources: irq:16 memory:f0000000-f7ffffff(prefetchable) memory:ffa80000-ffafffff ioport:ec00(size=8)  
         *-generic UNCLAIMED  
              description: System peripheral  
              product: 82865G/PE/P Processor to I/O Memory Interface  
              vendor: Intel Corporation  
              physical id: 6  
              bus info: pci@0000:00:06.0 
              version: 02  
              width: 32 bits  
              clock: 33MHz  
              configuration: latency=0  
              resources: memory:fecf0000-fecf0fff  
         *-usb:0  
              description: USB Controller  
              product: 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1  
              vendor: Intel Corporation  
              physical id: 1d  
              bus info: pci@0000:00:1d.0 
              version: 02  
              width: 32 bits  
              clock: 33MHz  
              capabilities: bus_master  
              configuration: driver=uhci_hcd latency=0  
              resources: irq:16 ioport:c400(size=32)  
         *-usb:1  
              description: USB Controller  
              product: 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2  
              vendor: Intel Corporation  
              physical id: 1d.1  
              bus info: pci@0000:00:1d.1 
              version: 02  
              width: 32 bits  
              clock: 33MHz  
              capabilities: bus_master  
              configuration: driver=uhci_hcd latency=0  
              resources: irq:19 ioport:c800(size=32)  
         *-usb:2  
              description: USB Controller  
              product: 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3  
              vendor: Intel Corporation  
              physical id: 1d.2  
              bus info: pci@0000:00:1d.2 
              version: 02  
              width: 32 bits  
              clock: 33MHz  
              capabilities: bus_master  
              configuration: driver=uhci_hcd latency=0  
              resources: irq:18 ioport:cc00(size=32)  
         *-usb:3  
              description: USB Controller  
              product: 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4  
              vendor: Intel Corporation  
              physical id: 1d.3  
              bus info: pci@0000:00:1d.3 
              version: 02  
              width: 32 bits  
              clock: 33MHz  
              capabilities: bus_master  
              configuration: driver=uhci_hcd latency=0  
              resources: irq:16 ioport:d000(size=32)  
         *-usb:4  
              description: USB Controller  
              product: 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller  
              vendor: Intel Corporation  
              physical id: 1d.7  
              bus info: pci@0000:00:1d.7 
              version: 02  
              width: 32 bits  
              clock: 33MHz  
              capabilities: bus_master cap_list  
              configuration: driver=ehci_hcd latency=0  
              resources: irq:23 memory:ffa7f400-ffa7f7ff  
         *-pci  
              description: PCI bridge  
              product: 82801 PCI Bridge  
              vendor: Intel Corporation  
              physical id: 1e  
              bus info: pci@0000:00:1e.0 
              version: c2  
              width: 32 bits  
              clock: 33MHz  
              capabilities: pci bus_master  
              resources: ioport:b000(size=4096) memory:ff800000-ff8fffff  
            *-communication  
                 description: Modem  
                 product: FA82537EP 56K V.92 Data/Fax Modem PCI  
                 vendor: Intel Corporation  
                 physical id: 2  
                 bus info: pci@0000:01:02.0  
                 version: 03  
                 width: 32 bits  
                 clock: 33MHz  
                 capabilities: bus_master cap_list  
                 configuration: driver=serial latency=32 maxlatency=62 mingnt=1  
                 resources: irq:17 memory:ff8fe000-ff8fefff ioport:b800(size=256)  
            *-network DISABLED  
                 description: Ethernet interface  
                 product: 82562EZ 10/100 Ethernet Controller  
                 vendor: Intel Corporation  
                 physical id: 8  
                 bus info: pci@0000:01:08.0  
                 logical name: eth0  
                 version: 02  
                 serial: 00:07:e9:4b:d7:64  
                 width: 32 bits  
                 clock: 33MHz  
                 capabilities: bus_master cap_list ethernet physical  
                 configuration: broadcast=yes driver=e100 driverversion=3.5.24-k2-NAPI firmware=N/A latency=32 maxlatency=56 mingnt=8 multicast=yes  
                 resources: irq:20 memory:ff8ff000-ff8fffff ioport:bc00(size=64)  
         *-isa  
              description: ISA bridge  
              product: 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge  
              vendor: Intel Corporation  
              physical id: 1f  
              bus info: pci@0000:00:1f.0 
              version: 02  
              width: 32 bits  
              clock: 33MHz  
              capabilities: isa bus_master  
              configuration: latency=0  
         *-ide:0  
              description: IDE interface 
              product: 82801EB/ER (ICH5/ICH5R) IDE Controller  
              vendor: Intel Corporation  
              physical id: 1f.1  
              bus info: pci@0000:00:1f.1 
              version: 02  
              width: 32 bits  
              clock: 33MHz  
              capabilities: ide bus_master  
              configuration: driver=ata_piix latency=0  
              resources: irq:18 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:ffa0(size=16) memory:20000000-200003ff  
         *-ide:1  
              description: IDE interface 
              product: 82801EB (ICH5) SATA Controller  
              vendor: Intel Corporation  
              physical id: 1f.2  
              bus info: pci@0000:00:1f.2 
              version: 02  
              width: 32 bits  
              clock: 66MHz  
              capabilities: ide bus_master  
              configuration: driver=ata_piix latency=0  
              resources: irq:18 ioport:e800(size=8) ioport:e400(size=4) ioport:e000(size=8) ioport:dc00(size=4) ioport:d800(size=16)  
         *-serial UNCLAIMED  
              description: SMBus  
              product: 82801EB/ER (ICH5/ICH5R) SMBus Controller  
              vendor: Intel Corporation  
              physical id: 1f.3  
              bus info: pci@0000:00:1f.3 
              version: 02  
              width: 32 bits  
              clock: 33MHz  
              configuration: latency=0  
              resources: ioport:d400(size=32)  
         *-multimedia  
              description: Multimedia audio controller  
              product: 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller  
              vendor: Intel Corporation  
              physical id: 1f.5  
              bus info: pci@0000:00:1f.5 
              version: 02  
              width: 32 bits  
              clock: 33MHz  
              capabilities: bus_master cap_list  
              configuration: driver=Intel ICH latency=0  
              resources: irq:17 memory:ffa7fc00-ffa7fdff memory:ffa7f800-ffa7f8ff  
   *-scsi  
        physical id: 1  
        bus info: scsi@5  
        logical name: scsi5  
        capabilities: scsi-host  
        configuration: driver=usb-storage  
 

 owner@ubuntu:~$ ifconfig wlan0
 wlan0: error fetching interface information: Device not found  
 

 owner@ubuntu:~$ ifconfig  
 lo        Link encap:Local Loopback   
           inet addr:127.0.0.1  Mask:255.0.0.0  
           inet6 addr: ::1/128 Scope:Host  
           UP LOOPBACK RUNNING  MTU:16436  Metric:1  
           RX packets:12 errors:0 dropped:0 overruns:0 frame:0  
           TX packets:12 errors:0 dropped:0 overruns:0 carrier:0  
           collisions:0 txqueuelen:0  
           RX bytes:720 (720.0 B)  TX bytes:720 (720.0 B)  
 

 owner@ubuntu:~$ iwlist scan  
 lo        Interface doesn't support scanning.  
 

 eth0      Interface doesn't support scanning.  
 

 owner@ubuntu:~$ iwconfig  
 lo        no wireless extensions.  
 

 eth0      no wireless extensions.

---

### Post by trona on 2010-08-07
I forgot to mention that I also tried using the files bcmwlhigh6.inf and bcmwlhigh6.sys with no success.  Furthermore, ever since I've installed these drivers I've been having problems booting up Ubuntu.  Help!

---

### Post by SmrtMouth on 2012-02-18
I'm having the same exact problem. Somebody please help us. Did you already solve this?

---

### Post by overdrank on 2012-02-18
> **SmrtMouth said:**
> I'm having the same exact problem. Somebody please help us. Did you already solve this?

Hi and you have a thread on the issue. Please do not bump old threads. Thread closed.

---

