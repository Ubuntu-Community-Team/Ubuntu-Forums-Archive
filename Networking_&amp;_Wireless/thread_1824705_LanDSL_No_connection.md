---
title: "Lan/DSL No connection"
date: 2011-08-14
forum: Networking &amp; Wireless
---

### Post by zissshh on 2011-08-14
I was using a DSL Connection,which was working fine,until two days back,it stopped connecting,The connections created were there but remained and failed to connect.
   after contacting the service guy,he responded saying my lan card has stopped working,
he had a technique of knowing it,whatever it may be,
    He sugessts replacingthe Lan and since i use UBUNTU 10.10,,They have no Idea of it,,

After running tests for Network, The report does not open in Google Chrome....

will post more reults from terminal testing,,as iam in Cyber CAfe

---

### Post by zissshh on 2011-08-15
```
sudhir@sudhir-desktop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:24:1d:59:72:fa  
          inet6 addr: fe80::224:1dff:fe59:72fa/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:20831 errors:0 dropped:0 overruns:0 frame:0
          TX packets:34 errors:0 dropped:0 overruns:0 carrier:1
          collisions:0 txqueuelen:1000 
          RX bytes:2059481 (2.0 MB)  TX bytes:4245 (4.2 KB)
          Interrupt:44 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:10088 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10088 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:669053 (669.0 KB)  TX bytes:669053 (669.0 KB)




sudhir@sudhir-desktop:~$ lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation 82G33/G31/P35/P31 Express DRAM Controller [8086:29c0] (rev 10)
00:02.0 VGA compatible controller [0300]: Intel Corporation 82G33/G31 Express Integrated Graphics Controller [8086:29c2] (rev 10)
00:1b.0 Audio device [0403]: Intel Corporation N10/ICH 7 Family High Definition Audio Controller [8086:27d8] (rev 01)
00:1c.0 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 1 [8086:27d0] (rev 01)
00:1c.1 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 2 [8086:27d2] (rev 01)
00:1d.0 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 [8086:27c8] (rev 01)
00:1d.1 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 [8086:27c9] (rev 01)
00:1d.2 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 [8086:27ca] (rev 01)
00:1d.3 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 [8086:27cb] (rev 01)
00:1d.7 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller [8086:27cc] (rev 01)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 PCI Bridge [8086:244e] (rev e1)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge [8086:27b8] (rev 01)
00:1f.2 IDE interface [0101]: Intel Corporation N10/ICH7 Family SATA IDE Controller [8086:27c0] (rev 01)
00:1f.3 SMBus [0c05]: Intel Corporation N10/ICH 7 Family SMBus Controller [8086:27da] (rev 01)
02:00.0 Ethernet controller [0200]: Atheros Communications AR8131 Gigabit Ethernet [1969:1063] (rev c0)


sudhir@sudhir-desktop:~$ lshw
WARNING: you should run this program as super-user.
sudhir-desktop            
    description: Computer
    width: 32 bits
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 0
          size: 2002MiB
     *-cpu
          product: Intel(R) Core(TM)2 Duo CPU     E7500  @ 2.93GHz
          vendor: Intel Corp.
          physical id: 1
          bus info: cpu@0
          version: 6.7.10
          serial: 0001-067A-0000-0000-0000-0000
          size: 1600MHz
          capacity: 1600MHz
          width: 64 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx x86-64 constant_tsc arch_perfmon pebs bts aperfmperf pni dtes64 monitor ds_cpl est tm2 ssse3 cx16 xtpr pdcm sse4_1 xsave lahf_lm cpufreq
          configuration: id=0
        *-logicalcpu:0
             description: Logical CPU
             physical id: 0.1
             width: 64 bits
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 0.2
             width: 64 bits
             capabilities: logical
     *-pci
          description: Host bridge
          product: 82G33/G31/P35/P31 Express DRAM Controller
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 10
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel
          resources: irq:0
        *-display
             description: VGA compatible controller
             product: 82G33/G31 Express Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 10
             width: 32 bits
             clock: 33MHz
             capabilities: vga_controller bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:42 memory:f0200000-f027ffff ioport:e000(size=8) memory:e0000000-efffffff memory:f0000000-f00fffff
        *-multimedia
             description: Audio device
             product: N10/ICH 7 Family High Definition Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 01
             width: 64 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=HDA Intel latency=0
             resources: irq:43 memory:f0280000-f0283fff
        *-pci:0
             description: PCI bridge
             product: N10/ICH 7 Family PCI Express Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:40 ioport:c000(size=4096) memory:7f600000-7f7fffff ioport:7f800000(size=2097152)
        *-pci:1
             description: PCI bridge
             product: N10/ICH 7 Family PCI Express Port 2
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@0000:00:1c.1
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:41 ioport:d000(size=4096) memory:f0100000-f01fffff ioport:7fa00000(size=2097152)
           *-network
                description: Ethernet interface
                product: AR8131 Gigabit Ethernet
                vendor: Atheros Communications
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: eth0
                version: c0
                serial: 00:24:1d:59:72:fa
                width: 64 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical
                configuration: broadcast=yes driver=atl1c driverversion=1.0.0.2-NAPI firmware=N/A latency=0 multicast=yes
                resources: irq:44 memory:f0100000-f013ffff ioport:d000(size=128)
        *-usb:0
             description: USB Controller
             product: N10/ICH 7 Family USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:23 ioport:e100(size=32)
        *-usb:1
             description: USB Controller
             product: N10/ICH 7 Family USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:19 ioport:e200(size=32)
        *-usb:2
             description: USB Controller
             product: N10/ICH 7 Family USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:18 ioport:e300(size=32)
        *-usb:3
             description: USB Controller
             product: N10/ICH 7 Family USB UHCI Controller #4
             vendor: Intel Corporation
             physical id: 1d.3
             bus info: pci@0000:00:1d.3
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:16 ioport:e400(size=32)
        *-usb:4
             description: USB Controller
             product: N10/ICH 7 Family USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:23 memory:f0284000-f02843ff
        *-pci:2
             description: PCI bridge
             product: 82801 PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: e1
             width: 32 bits
             clock: 33MHz
             capabilities: pci subtractive_decode bus_master cap_list
             resources: ioport:b000(size=4096)
        *-isa
             description: ISA bridge
             product: 82801GB/GR (ICH7 Family) LPC Interface Bridge
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: latency=0
        *-ide
             description: IDE interface
             product: N10/ICH7 Family SATA IDE Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             version: 01
             width: 32 bits
             clock: 66MHz
             capabilities: ide bus_master cap_list
             configuration: driver=ata_piix latency=0
             resources: irq:19 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:f000(size=16)
        *-serial UNCLAIMED
             description: SMBus
             product: N10/ICH 7 Family SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 01
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
             resources: ioport:500(size=32)
```

---

### Post by varunendra on 2011-08-15
First off, please edit your above post to wrap the outputs with 'code' tags. It'll make it easy to read. To do so, type [noparse]```
 at the beginning of the output part of a command (which is the text we want to wrap), and 
```[/noparse] at the end of the output. You can do this easily in 'Advance' editing mode by selecting the desired text with your cursor, and clicking on the **#** symbol at the top of the editing box.

I'm tagging only the edited part here which is important:
> **zissshh said:**
> sudhir@sudhir-desktop:~$ ifconfig
```
eth0      Link encap:Ethernet  HWaddr 00:24:1d:59:72:fa  
          inet6 addr: fe80::224:1dff:fe59:72fa/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:20831 errors:0 dropped:0 overruns:0 frame:0
          TX packets:34 errors:0 dropped:0 overruns:0 carrier:1
          collisions:0 txqueuelen:1000 
          RX bytes:2059481 (2.0 MB)  TX bytes:4245 (4.2 KB)
          Interrupt:44 ....)
```

sudhir@sudhir-desktop:~$ lspci -nn
```
....
....
02:00.0 Ethernet controller [0200]: Atheros Communications **AR8131 Gigabit Ethernet** [1969:1063] (rev c0)
```


sudhir@sudhir-desktop:~$ lshw
```
....
....
           *-network
                description: Ethernet interface
                product: AR8131 Gigabit Ethernet
                vendor: Atheros Communications
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: eth0
                version: c0
                serial: 00:24:1d:59:72:fa
                width: 64 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical
                configuration: broadcast=yes driver=atl1c driverversion=1.0.0.2-NAPI firmware=N/A latency=0 multicast=yes
                resources: irq:44 memory:f0100000-f013ffff ioport:d000(size=128)
```


Now onto the problem-
Your LAN interface is detected by the OS and (apparently) a suitable driver is loaded for it. Thus it seems to be an external factor.

Do you connect to an adsl modem or is there a direct cable provided by your ISP that you connect to?

Do you use an ID/password to connect?

Answers to these will decide the further course of action to troubleshoot the problem.

---

### Post by zissshh on 2011-08-17
i have a dsl connection ,,the service guy changed the plug to the cable,,,but still no connection

 yes,,,i have a id and password

i shall check again


sorry for noo quotes,,,was in hurry

---

### Post by zissshh on 2011-08-17
```
sudhir@sudhir-desktop:~$ sudo dhclient
Internet Systems Consortium DHCP Client V3.1.3
Copyright 2004-2009 Internet Systems Consortium.
All rights reserved.
For info, please visit [https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/)

Listening on LPF/eth0/00:24:1d:59:72:fa
Sending on   LPF/eth0/00:24:1d:59:72:fa
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
DHCPOFFER of 192.168.0.215 from 192.168.0.1
DHCPREQUEST of 192.168.0.215 on eth0 to 255.255.255.255 port 67
DHCPACK of 192.168.0.215 from 192.168.0.1
bound to 192.168.0.215 -- renewal in 253 seconds.


sudhir@sudhir-desktop:~$ sudo ifup eth0
Ignoring unknown interface eth0=eth0.


sudhir@sudhir-desktop:~$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: AR8131 Gigabit Ethernet
       vendor: Atheros Communications
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: c0
       serial: 00:24:1d:59:72:fa
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=atl1c driverversion=1.0.0.2-NAPI duplex=full firmware=N/A latency=0 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: irq:44 memory:f0100000-f013ffff ioport:d000(size=128)
```

now the service guy has changed the entire cable,,,,still no connection,,,,,,

earlier the network manager showed the the two settings for logging in or connecting,,,even they are missing,,,

---

### Post by varunendra on 2011-08-18
Sorry for a late response, I've got extra busy for a few days, may not get back until monday, so just a quick reply here-
> **zissshh said:**
> ```

sudhir@sudhir-desktop:~$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: AR8131 Gigabit Ethernet
....
....
....**driver=atl1c** driverversion=1.0.0.2-NAPI duplex=full **firmware=N/A** ....
```
Apparently, the missing firmware is the cause. So let's have a look at
```
dmesg | grep -iE "atl1c|AR8131"
```

To install the firmware, see if this helps: [https://help.ubuntu.com/10.10/installation-guide/i386/loading-firmware.html](https://help.ubuntu.com/10.10/installation-guide/i386/loading-firmware.html)

I didn't read it myself, so in case of problems, please try to google it yourself or post back here hoping someone with exact 'know-how' may see and respond. I'll get back as soon as I can.

---

### Post by zissshh on 2011-08-20
```
dmesg | grep -iE "atl1c|AR8131"

results were

( 00823390) atl1c 0000:02:0.0: PCI INT A -> GSI 17 ( level low) -> IRQ 17
[0.823400]  atl1c 0000:02:0.0: setting latency times to 64
[0.823400]  atl1c 0000:02:00.0: version 1.0.02-NAPI
[0.823400]  atl1c 0000:02:00.0: irq 44 for MSI/MSI-X



```
these were type written ,,,as i lost my pen drive...

moreover the "atl1c" were in RED

---

### Post by varunendra on 2011-08-22
Did you try the guide to install the firmware? Didn't it help?

And the word "atl1c" being in red is normal. Any word that is searched using 'grep' is returned in red colour. It is just a method to highlight it. Sorry, but I still have not enough time to look any deeper into this issue. I've requested chili (the best man for these issues) to have a look at it. Hope you get some comprehensive reply soon.

---

### Post by praseodym on 2011-08-22
Do you use the Network-Manager-Tool? Please show the following outputs:
```

cat /etc/network/interfaces
cat /etc/resolv.conf
cat /var/lib/NetworkManager/NetworkManager.state
```

---

### Post by zissshh on 2011-08-22
there was no firmware available for the hardware, i am using

---

### Post by chili555 on 2011-08-22
> **zissshh said:**
> there was no firmware available for the hardware, i am usingNor is any firmware needed. It looks to me like you are connected:> Listening on LPF/eth0/00:24:1d:59:72:fa
Sending on   LPF/eth0/00:24:1d:59:72:fa
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
DHCPOFFER of 192.168.0.215 from 192.168.0.1
DHCPREQUEST of 192.168.0.215 on eth0 to 255.255.255.255 port 67
DHCPACK of 192.168.0.215 from 192.168.0.1
[COLOR="Red"]bound to 192.168.0.215[/COLOR] -- renewal in 253 seconds.Are you unable to surf the web?

If you have the option to do so, I'd set the DSL username and password in the router. Then the computer sees an ordinary ethernet connection with no special configuration.

---

### Post by zissshh on 2011-08-23
```
sudhir@sudhir-desktop:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback





sudhir@sudhir-desktop:~$ cat /etc/resolv.conf
nameserver 192.168.0.1
domain mshome.net
search mshome.net



sudhir@sudhir-desktop:~$ cat /var/lib/NetworkManager/NetworkManager.state

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=false


```
EVERY THING WAS WORKING FINE WITH THE SAME CONNECTION EARLIER,,,UNABLE TO SURF AS UNABLE TO CONNECT
SOMEBODY SUGGEST ME A SOLUTION  asap :)

I SHALL TRY  and RESET THE DSL rajesh hathway connection,,,USER ID & PAssWORD ,,,asking the servicing guy to do it

---

### Post by praseodym on 2011-08-23
Did you insert your login and password in the router interface?

---

### Post by zissshh on 2011-08-24
yes ,,the Network Manager ICon shows RED CROSS and does not even show the two DSL CONECTIONs,which i had to click to connect 

THE service guy says the Ethernet card is not working :]

---

### Post by chili555 on 2011-08-24
If you have set up the DSL username and password in the router, then there is no need to set up a DSL connection in Network Manager. The router is providing authentication to the DSL provider. Your computer should just see an ordinary ethernet connection. When you click the Network Manager icon, do you see Auto eth0 as an option? Can you click it and try to connect? What happens?

If you have set up DSL details in Network Manager, they need to be removed, since the router is providing authentication to the DSL provider.

Every indication we see about your ethernet card suggests it's healthy:> DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
DHCPOFFER of 192.168.0.215 from 192.168.0.1
DHCPREQUEST of 192.168.0.215 on eth0 to 255.255.255.255 port 67
DHCPACK of 192.168.0.215 from 192.168.0.1
bound to 192.168.0.215 -- renewal in 253 seconds.Also:> *-network               
       description: Ethernet interface
       product: AR8131 Gigabit Ethernet
       vendor: Atheros Communications
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: c0
       serial: 00:24:1d:59:72:fa
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes [COLOR="Red"]driver=atl1c [/COLOR]driverversion=1.0.0.2-NAPI duplex=full firmware=N/A latency=0 [COLOR="Red"]link=yes[/COLOR] multicast=yes port=twisted pair speed=100MB/s
       resources: irq:44 memory:f0100000-f013ffff ioport:d000(size=128)An ethernet card that is defective will not detect a link and report it.

---

### Post by praseodym on 2011-08-24
chili555 is right. Delete _all_ profiles in the NM-applet under "Cable" _and_ "DSL" and reboot your system. Wired should work now.

---

### Post by zissshh on 2011-08-24
HERE In INdia,,Atleast Regarding ME,the dsl provider is providing me a username and password,,which i can change

i created a profile under dsl on the given name and password with the name of the provider,,

it works and the nm aplet is to be rightclicked and select the connection and then u go surf,,

but my nm apllet is unable to show the two connection,,,

---

### Post by chili555 on 2011-08-24
> **zissshh said:**
> HERE In INdia,,Atleast Regarding ME,the dsl provider is providing me a username and password,,which i can change

i created a profile under dsl on the given name and password with the name of the provider,,

it works and the nm aplet is to be rightclicked and select the connection and then u go surf,,

but my nm apllet is unable to show the two connection,,,So you did *NOT* set the DSL username and password in the router as we suggested? Is that an option or not? Please see attached.

---

### Post by zissshh on 2011-08-25
i have made a connection named RajeshEDGE4 in network connections under dsl connection with a username and a password..

for the attachment that you suggest is not possible as iam not  able to connect,,and afterall the service provider has provided me the username and pwd so he must have made an account

---

### Post by zissshh on 2011-08-26
After lot of attempts and removing earlier setting in connections,,,and lot more attempts and restarting a couple of time,,,i have got to connect,,,,
i dont know what happenend:)

---

