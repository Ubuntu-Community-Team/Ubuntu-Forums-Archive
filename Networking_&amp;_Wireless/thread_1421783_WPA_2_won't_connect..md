---
title: "WPA 2 won't connect."
date: 2010-03-04
forum: Networking &amp; Wireless
---

### Post by NissanSkylineN1 on 2010-03-04
Hi,
I have a wpa 2 connection and ubuntu 9.10 wont connect. I have turned the password off via another computer using windows and it works. I have a us robotics 5420 adapter with a linksys WRT54G2 router. Any ideas to make it work?

---

### Post by NissanSkylineN1 on 2010-03-07
bump

---

### Post by wieman01 on 2010-03-07
You have tried connecting without any security. Next would be to give WEP a go, then WPA, then WPA2. 

It might be that your wireless adapter does not support WPA2.

---

### Post by NissanSkylineN1 on 2010-03-07
No, my adapter supports WPA2, its a US Robotics 5420.

---

### Post by wieman01 on 2010-03-07
What happens when you issue:
> sudo iwlist scan
Please post the results.

---

### Post by NissanSkylineN1 on 2010-03-07
Here are the results (Note: Infinity is my internet name):
   parham@parham-desktop:~$ sudo iwlist scan
  lo        Interface doesn't support scanning.
   
  eth0      Interface doesn't support scanning.
   
  wlan0     Scan completed :
            Cell 01 - Address: 00:1E:E5:7B:AC:BF
                      Channel:6
                      Frequency:2.437 GHz (Channel 6)
                      Quality=60/100  Signal level=60/100  
                      Encryption key:on
                      ESSID:"Infinity"
                      Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                                24 Mb/s; 36 Mb/s; 54 Mb/s
                      Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                      Mode:Master
                      Extra:tsf=0000000424b1592a
                      Extra: Last beacon: 64ms ago
                      IE: Unknown: 0008496E66696E697479
                      IE: Unknown: 010882848B9624B0486C
                      IE: Unknown: 030106
                      IE: Unknown: 2A0104
                      IE: Unknown: 2F0104
                      IE: IEEE 802.11i/WPA2 Version 1
                          Group Cipher : TKIP
                          Pairwise Ciphers (2) : CCMP TKIP
                          Authentication Suites (1) : PSK
                      IE: Unknown: 32048C129860
                      IE: Unknown: DD7E0050F204104A0001101044000102103B00010310470010138140001DD211B29FFFC67E816B4BFB102100074C696E6B73797310230006526F7574657210240007575254353447321042000C4353563031483355333138301054000800060050F204000110110011576972656C6573732D4720526F75746572100800020084
                      IE: Unknown: DD090010180204F4000000
                      IE: WPA Version 1
                          Group Cipher : TKIP
                          Pairwise Ciphers (2) : CCMP TKIP
                          Authentication Suites (1) : PSK
            Cell 02 - Address: 00:1C:10:35:FF:D2
                      Channel:6
                      Frequency:2.437 GHz (Channel 6)
                      Quality=29/100  Signal level=29/100  
                      Encryption key:on
                      ESSID:"linksys_SES_50928"
                      Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                                24 Mb/s; 36 Mb/s; 54 Mb/s
                      Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                      Mode:Master
                      Extra:tsf=000006379084b6c8
                      Extra: Last beacon: 64ms ago
                      IE: Unknown: 00116C696E6B7379735F5345535F3530393238
                      IE: Unknown: 010882848B962430486C
                      IE: Unknown: 030106
                      IE: Unknown: 2A0104
                      IE: Unknown: 2F0104
                      IE: Unknown: 32040C121860
                      IE: Unknown: DD090010180200F4000000
                      IE: WPA Version 1
                          Group Cipher : TKIP
                          Pairwise Ciphers (1) : TKIP
                          Authentication Suites (1) : PSK
            Cell 03 - Address: 00:14:BF:75:08:D2
                      Channel:6
                      Frequency:2.437 GHz (Channel 6)
                      Quality=14/100  Signal level=14/100  
                      Encryption key:off
                      ESSID:"linksys"
                      Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                                24 Mb/s; 36 Mb/s; 54 Mb/s
                      Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                      Mode:Master
                      Extra:tsf=000006b307cd5717
                      Extra: Last beacon: 64ms ago
                      IE: Unknown: 00076C696E6B737973
                      IE: Unknown: 010882848B962430486C
                      IE: Unknown: 030106
                      IE: Unknown: 2A0104
                      IE: Unknown: 2F0104
                      IE: Unknown: 32040C121860
                      IE: Unknown: DD06001018020104
   
  parham@parham-desktop:~$

---

### Post by wieman01 on 2010-03-08
So were you or were you not able to connect via WEP and WPA?

---

### Post by rory526 on 2010-03-08
If you want to try connecting via the command line:

WPA / WPA2:

```
$ sudo wpa_passphrase infinity <your WPA password> > /etc/wpa_supplicant.conf
$ sudo wpa_supplicant -B -c /etc/wpa_supplicant.conf -i wlan0
$ sudo dhclient wlan0
```

WEP:

```

$ sudo iwconfig wlan0 ap 00:1E:E5:7B:AC:BF key <your WEP password>
$ sudo dhclient wlan0
```

Of course, you have to set your router to use WEP for the second set of commands.

---

### Post by NissanSkylineN1 on 2010-03-09
> **wieman01 said:**
> So were you or were you not able to connect via WEP and WPA?
I was not able.

Oh, Rory, when I entered your code, I got:
bash: /etc/wpa_supplicant.conf: Permission denied

---

### Post by wieman01 on 2010-03-09
If you can't even connect by means of WPA and WEP, something else is wrong. The driver might may not have installed correctly.

Can you connect with all security turned off?

Please also issue:
> sudo lshw -C
And post the results.

---

### Post by NissanSkylineN1 on 2010-03-10
I can connnect with all security off. Here, i will post the results later.

---

### Post by lovette on 2010-03-10
I have the same issue with latest 9.10 update.  Both my Dell vostro laptops worked fine before with wpa2 security.  After the lastest 9.10 update, I can only connect if I turn off router security completely.  No worky with WPA either.  The Dells both use Intel 4965 AGN cards.  Router is Linksys 150N. If I boot them in XP Pro, both lappys work with wpa2 enabled, so the router and cards must be working properly.    Was there a driver change with the last update?  I can see the available networks.  I get a popup window asking for my wpa2 passkey.  After entering, it attempts to connect, then the same popup appears.

---

### Post by robobart on 2010-03-10
I think I have exactly the same issue as Lovette...

When was the update? Was it tues afternoon sometime? That's when I noticed that it stopped working.

This is quite annoying because I had it working for several months now.

---

### Post by NissanSkylineN1 on 2010-03-11
> **wieman01 said:**
> If you can't even connect by means of WPA and WEP, something else is wrong. The driver might may not have installed correctly.

Can you connect with all security turned off?

Please also issue:

And post the results.

Here are the results (its long, beware):
   [FONT=&quot]parham@parham-desktop:~$ sudo lshw -C
Hardware Lister (lshw) - B.02.14
usage: lshw [-format] [-options ...]
       lshw -version

      -version        print program version (B.02.14)

format can be
      -html           output hardware tree as HTML
      -xml            output hardware tree as XML
      -short          output hardware paths
      -businfo        output bus information

options can be
      -class CLASS    only show a certain class of hardware
      -C CLASS        same as '-class CLASS'
      -c CLASS        same as '-class CLASS'
      -disable TEST   disable a test (like pci, isapnp, cpuid, etc. )
      -enable TEST    enable a test (like pci, isapnp, cpuid, etc. )
      -quiet          don't display status
      -sanitize       sanitize output (remove sensitive information like serial numbers, etc.)
      -numeric        output numeric IDs (for PCI, USB, etc.)

      Since the code you gave me didn't give much info, I decided to try this:

parham@parham-desktop:~$ lshw
WARNING: you should run this program as super-user.
parham-desktop            
    description: Computer
    width: 32 bits
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 0
          size: 503MiB
     *-cpu
          product: Intel(R) Celeron(R) CPU 2.53GHz
          vendor: Intel Corp.
          physical id: 1
          bus info: cpu@0
          version: 15.3.3
          serial: 0000-0F33-0000-0000-0000-0000
          size: 2550MHz
          width: 32 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe constant_tsc up pebs bts pni dtes64 monitor ds_cpl cid
          configuration: id=0
     *-pci
          description: Host bridge
          product: 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 03
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel
          resources: irq:0 memory:e8000000-ebffffff(prefetchable)
        *-display UNCLAIMED
             description: VGA compatible controller
             product: 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: latency=0
             resources: memory:e0000000-e7ffffff(prefetchable) memory:ee000000-ee07ffff
        *-usb:0
             description: USB Controller
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:16 ioport:d800(size=32)
        *-usb:1
             description: USB Controller
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:19 ioport:d000(size=32)
        *-usb:2
             description: USB Controller
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:18 ioport:d400(size=32)
        *-usb:3
             description: USB Controller
             product: 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:23 memory:ee080000-ee0803ff
        *-pci
             description: PCI bridge
             product: 82801 PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: 82
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master
             resources: ioport:c000(size=4096) memory:ec000000-edffffff memory:20000000-200fffff(prefetchable)
           *-communication UNCLAIMED
                description: Communication controller
                product: V.92 56K WinModem
                vendor: Agere Systems
                physical id: b
                bus info: pci@0000:01:0b.0
                version: 03
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: latency=32 maxlatency=14 mingnt=252
                resources: memory:ed001000-ed0010ff ioport:c000(size=8) ioport:c400(size=256)
           *-network
                description: Ethernet interface
                product: RTL-8139/8139C/8139C+
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: c
                bus info: pci@0000:01:0c.0
                logical name: eth0
                version: 10
                serial: 00:11:09:70:58:f8
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list rom ethernet physical
                configuration: broadcast=yes driver=8139too driverversion=0.9.28 latency=32 maxlatency=64 mingnt=32 multicast=yes
                resources: irq:23 ioport:c800(size=256) memory:ed000000-ed0000ff memory:20000000-2000ffff(prefetchable)
        *-isa
             description: ISA bridge
             product: 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-ide
             description: IDE interface
             product: 82801DB (ICH4) IDE Controller
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@0000:00:1f.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master
             configuration: driver=ata_piix latency=0
             resources: irq:16 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:f000(size=16) memory:20100000-201003ff
        *-serial UNCLAIMED
             description: SMBus
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 02
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
             resources: ioport:500(size=32)
        *-multimedia
             description: Multimedia audio controller
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller
             vendor: Intel Corporation
             physical id: 1f.5
             bus info: pci@0000:00:1f.5
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=Intel ICH latency=0
             resources: irq:17 ioport:e000(size=256) ioport:e400(size=64) memory:ee081000-ee0811ff memory:ee082000-ee0820ff
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:c0:49:dd:38:99
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=rndis_wlan driverversion=22-Aug-2005 firmware=Wireless RNDIS device, BCM4320a usb-0000:00:1d.7-1 multicast=yes wireless=IEEE 802.11bg
parham@parham-desktop:~$ 



 [/FONT]

---

### Post by Malteser on 2010-03-12
Ye I have a Dell oldish inspiron will an Intel Pro Wireless 3945ABG adapter. Same problem, a few updated came along, I trusted them and installed them. I reboot and now I can only connect to connections with no security enabled.

sudo lshw -C Network
  *-network               
       description: Wireless interface
       product: PRO/Wireless 3945ABG [Golan] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:0b:00.0
       logical name: wmaster0
       version: 02
       serial: 00:18:de:d7:7f:cd
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 ip=192.168.1.36 latency=0 multicast=yes wireless=IEEE 802.11abg
       resources: irq:27 memory:efcff000-efcfffff
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:15:c5:ca:2a:56
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=half latency=64 link=no multicast=yes port=twisted pair speed=10MB/s
       resources: irq:17 memory:ef9fe000-ef9fffff

---

### Post by wieman01 on 2010-03-12
Have you guys filed a bug report or checked for one on launchpad?

---

### Post by NissanSkylineN1 on 2010-03-12
No, what's launchpad?
Edit: [https://bugs.launchpad.net/ubuntu/+bugs?field.searchtext=wpa+&orderby=-importance&search=Search&field.status%3Alist=NEW&field.status%3Alist=INCOMPLETE_WITH_RESPONSE&field.status%3Alist=INCOMPLETE_WITHOUT_RESPONSE&field.status%3Alist=CONFIRMED&field.status%3Alist=TRIAGED&field.status%3Alist=INPROGRESS&field.status%3Alist=FIXCOMMITTED&field.assignee=&field.bug_reporter=&field.omit_dupes=on&field.has_patch=&field.has_no_package=](https://bugs.launchpad.net/ubuntu/+bugs?field.searchtext=wpa+&orderby=-importance&search=Search&field.status%3Alist=NEW&field.status%3Alist=INCOMPLETE_WITH_RESPONSE&field.status%3Alist=INCOMPLETE_WITHOUT_RESPONSE&field.status%3Alist=CONFIRMED&field.status%3Alist=TRIAGED&field.status%3Alist=INPROGRESS&field.status%3Alist=FIXCOMMITTED&field.assignee=&field.bug_reporter=&field.omit_dupes=on&field.has_patch=&field.has_no_package=)

---

### Post by lovette on 2010-03-15
> **robobart said:**
> I think I have exactly the same issue as Lovette...

When was the update? Was it tues afternoon sometime? That's when I noticed that it stopped working.

This is quite annoying because I had it working for several months now.

it was the update to 2.6.31-20, don't remember the exact date but was last week sometime

---

### Post by GeoH2102 on 2010-03-17
I appear to be having this problem too :(

```
geo@geo-laptop:~$ lspci | grep -i net
05:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)
07:08.0 Ethernet controller: Intel Corporation PRO/100 VE Network Connection (rev 02)
```

---

### Post by lovette on 2010-03-21
I tried installing wicd, and using it instead of gnome network manager.  Success!!

 sudo apt-get install wicd

---

### Post by NissanSkylineN1 on 2010-04-29
I'm disappointed. They haven't fixed this bug in 10.04 either.:(

---

