---
title: "Zotac ID82 wireless and bluetooth not working"
date: 2012-09-14
forum: Networking &amp; Wireless
---

### Post by maheshgov on 2012-09-14
Hello Guys,

I bought a ZOTAC ID82 (comes with wireless and bluetooth). I installed Ubuntu 12.04 LTS 64-bit version. Everything works except for the wireless and bluetooth. 

[COLOR=Red][COLOR=Blue]lshw[/COLOR] [/COLOR]gives me the following:

*-network UNCLAIMED
                description: Network controller
                product: Ralink corp.
                vendor: Ralink corp.
                physical id: 0
                bus info: pci@0000:03:00.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: latency=0
                resources: memory:f7d40000-f7d4ffff memory:f7d30000-f7d3ffff
           *-generic UNCLAIMED
                description: Bluetooth
                product: Ralink corp.
                vendor: Ralink corp.
                physical id: 0.1
                bus info: pci@0000:03:00.1
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: latency=0
                resources: memory:f7d20000-f7d2ffff memory:f7d10000-f7d1ffff memory:f7c00000-f7cfffff memory:f7d00000-f7d0ffff

What is the problem? Is it because the OS is 64 bit and the wireless/bluetooth chips are 32 bit?

I understand that the drivers are not installed. 

I tried several things:

Additional drivers: (Ubuntu cannot find any more drivers for this)
I tried Ndiswrapper -- I downloaded the corresponding driver for windows. This software recognized the driver file, but wireless still dint work. So I moved on.

Then I went to the RAlink website [http://www.ralinktech.com/en/04_support/support.php?sn=501](http://www.ralinktech.com/en/04_support/support.php?sn=501)

I tried to install the RT2860 driver from there. I tried the following:

[COLOR=Blue]user-id@ZOTAC2:~/Downloads/2010_07_16_RT2860_Linux_STA_v2.4.0.0$ cd
user-id@ZOTAC2:~$ cd /home/govindarm/Downloads
user-id@ZOTAC2:~/Downloads$ cd 2010_07_16_RT2860_Linux_STA_v2.4.0.0/
user-id@ZOTAC2:~/Downloads/2010_07_16_RT2860_Linux_STA_v2.4.0.0$ gedit os/linux/config.mk

[COLOR=Black]Here I set:

HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=y
HAS_WPA_SUPPLICANT=y

and then saved the file.
[/COLOR]

user-id@ZOTAC2:~/Downloads/2010_07_16_RT2860_Linux_STA_v2.4.0.0$ sudo su make && make install
[sudo] password for user-id: 
Unknown id: make[/COLOR]

I dont know what "unknown id: make" means. 

I had tried installing the same driver before WITHOUT having the 

[COLOR=Blue][COLOR=Black]HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=y
HAS_WPA_SUPPLICANT=y[/COLOR][/COLOR]

Is this the problem? If so, any help to rectify this is appreciated.

I have dealt with Linux at a user level for several years (on and off). But never really had a problem with drivers.

Thanks,
Mahesh

---

