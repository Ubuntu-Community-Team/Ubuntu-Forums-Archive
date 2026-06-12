---
title: "Wireless lost on battery power Ubuntu 9.10 32-bit"
date: 2010-02-11
forum: Networking &amp; Wireless
---

### Post by Nesbiteme on 2010-02-11
Anyone have solutions for this problem: Can not establish or re-establish wireless connectivity while on battery power. Below are specifications

nesbiteme-laptop               
    description: Notebook
    product: Satellite T135
    vendor: TOSHIBA
    version: PST3AU-00J008
    serial: Y9149440W
    width: 32 bits
    capabilities: smbios-2.5 dmi-2.5 smp-1.4 smp
    configuration: administrator_password=disabled boot=normal chassis=notebook cpus=2 frontpanel_password=unknown keyboard_password=unknown power-on_password=disabled uuid=C040BF69-ECDB-DE11-89BB-00269E9E4563
  *-core
       description: Motherboard
       product: Satellite T135
       vendor: TOSHIBA
       physical id: 0
       version: Not Applicable
       serial: Y9149440W
     *-firmware
          description: BIOS
          vendor: TOSHIBA
          physical id: 0
          version: V1.90 (11/06/2009)
          size: 111KiB
          capacity: 1984KiB
          capabilities: isa pci pcmcia pnp upgrade shadowing escd cdboot acpi usb biosbootspecification
     *-cpu:0
          description: CPU
          product: Genuine Intel(R) CPU           U4100  @ 1.30GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 6.7.10
          serial: 0001-067A-0000-0000-0000-0000
          slot: U2E1
          size: 1200MHz
          capacity: 4096MHz
          width: 64 bits
          clock: 200MHz
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx x86-64 constant_tsc arch_perfmon pebs bts pni dtes64 monitor ds_cpl est tm2 ssse3 cx16 xtpr pdcm xsave lahf_lm cpufreq
          configuration: id=1

Driver: Linux driver for Realtek RTL819x WiFi cards











*-network
                description: Wireless interface
                product: Realtek Semiconductor Co., Ltd.
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:08:00.0
                logical name: wlan0
                version: 10
                serial: 00:26:b6:75:cd:a5
                width: 32 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=rtl819xSE driverversion=0013.1127.2009 firmware=74 ip=192.168.0.103 latency=0 link=yes multicast=yes wireless=802.11bg
                resources: irq:17 ioport:3000(size=256) memory:c0100000-c0103fff
Thnx

---

### Post by emuh on 2010-02-14
Hi    

I also had problems with the r819xSE driver. 

Your report is a bit short, and I'm not sure that your problem is related to mine. 
Works everything fine if you are plugged in? 
If you unplug what says dmesg and /var/log/messages?   


Now here is my Problem and its solution: 

After startup everything works fine, but after a short period time, I lose my wlan-connection. 
The kernel tells me that my wlan is telling the AP that its waking up from LPS (ugly sentence I now^^).  

My solution is to deactivate the LPS option of the driver. I'm not quite sure what this feature does, but I think its an power saving option (leisure power save).   
To deactivate the LPS Option I took the dirty way and modified the Makefile of the driver (./HAL/rtl8192/Makefile)  in line 
55                 -DENABLE_LPS                            \   
I simply deleted the whole line.  

After building and loading the new driver everything seems to work fine. In the near future, I will look more closely for alternatives.  

Sry for the sub-optimal english, I'm trying (but not too hard ;-P)  

Emuh

---

### Post by Nesbiteme on 2010-02-14
> **emuh said:**
> Hi    

My solution is to deactivate the LPS option of the driver. I'm not quite sure what this feature does, but I think its an power saving option (leisure power save).   
To deactivate the LPS Option I took the dirty way and modified the Makefile of the driver (./HAL/rtl8192/Makefile)  in line 
55                 -DENABLE_LPS                            \   

Emuh


I think you are on to a solution to my problem. I tried commenting out this line, then make, make install etc. etc.. However my system became unstable after reboot, I will try to comment out all line with -DENABLE_LPS\ in the (./HAL/rtl8192/Makefile), and see if this works for me. I'll reprt back.

---

### Post by niffcreature on 2010-02-14
maybe you guys should try the power savings inhibit applet, if it only has to do with battery power

---

