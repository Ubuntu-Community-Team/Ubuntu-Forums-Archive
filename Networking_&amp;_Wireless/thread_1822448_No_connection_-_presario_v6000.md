---
title: "No connection - presario v6000"
date: 2011-08-10
forum: Networking &amp; Wireless
---

### Post by thommy86 on 2011-08-10
Hello,

 My name is Thommy and am new here on the forum. I am completely new to using Ubuntu.

 Since I had a extra laptop, I installed Ubuntu 11.04 yesterday.
 But now i have no Internet connection.. both wired and wireless do not work.

It is a Compaq Presario V6000 - V6221eu.

 My interest in Ubuntu is actually, because I would like to learn some android development.

 All help and tips are welcome!

---

### Post by chili555 on 2011-08-11
Please open a terminal and run and post:```
lspci -nn | grep -e 0280 -e 0200
```Thanks.

---

### Post by thommy86 on 2011-08-11
> **chili555 said:**
> Please open a terminal and run and post:```
lspci -nn | grep -e 0280 -e 0200
```Thanks.


Nothing happened..

---

### Post by chili555 on 2011-08-11
Then let's broaden the search:```
lspci -nn
```Thanks.

---

### Post by thommy86 on 2011-08-11
```
00:00.0 RAM memory [0500]: nVidia Corporation C51 Host Bridge [10de:02f0] (rev a2)
00:00.1 RAM memory [0500]: nVidia Corporation C51 Memory Controller 0 [10de:02fa] (rev a2)
00:00.2 RAM memory [0500]: nVidia Corporation C51 Memory Controller 1 [10de:02fe] (rev a2)
00:00.3 RAM memory [0500]: nVidia Corporation C51 Memory Controller 5 [10de:02f8] (rev a2)
00:00.4 RAM memory [0500]: nVidia Corporation C51 Memory Controller 4 [10de:02f9] (rev a2)
00:00.5 RAM memory [0500]: nVidia Corporation C51 Host Bridge [10de:02ff] (rev a2)
00:00.6 RAM memory [0500]: nVidia Corporation C51 Memory Controller 3 [10de:027f] (rev a2)
00:00.7 RAM memory [0500]: nVidia Corporation C51 Memory Controller 2 [10de:027e] (rev a2)
00:02.0 PCI bridge [0604]: nVidia Corporation C51 PCI Express Bridge [10de:02fc] (rev a1)
00:03.0 PCI bridge [0604]: nVidia Corporation C51 PCI Express Bridge [10de:02fd] (rev a1)
00:05.0 VGA compatible controller [0300]: nVidia Corporation C51 [Geforce Go 6150] [10de:0244] (rev a2)
00:09.0 RAM memory [0500]: nVidia Corporation MCP51 Host Bridge [10de:0270] (rev a2)
00:0a.0 ISA bridge [0601]: nVidia Corporation MCP51 LPC Bridge [10de:0260] (rev a3)
00:0a.1 SMBus [0c05]: nVidia Corporation MCP51 SMBus [10de:0264] (rev a3)
00:0a.3 Co-processor [0b40]: nVidia Corporation MCP51 PMU [10de:0271] (rev a3)
00:0b.0 USB Controller [0c03]: nVidia Corporation MCP51 USB Controller [10de:026d] (rev a3)
00:0b.1 USB Controller [0c03]: nVidia Corporation MCP51 USB Controller [10de:026e] (rev a3)
00:0d.0 IDE interface [0101]: nVidia Corporation MCP51 IDE [10de:0265] (rev f1)
00:0e.0 IDE interface [0101]: nVidia Corporation MCP51 Serial ATA Controller [10de:0266] (rev f1)
00:10.0 PCI bridge [0604]: nVidia Corporation MCP51 PCI Bridge [10de:026f] (rev a2)
00:10.1 Audio device [0403]: nVidia Corporation MCP51 High Definition Audio [10de:026c] (rev a2)
00:14.0 Bridge [0680]: nVidia Corporation MCP51 Ethernet Controller [10de:0269] (rev a3)
00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration [1022:1100]
00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map [1022:1101]
00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller [1022:1102]
00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control [1022:1103]

```

thanks

---

### Post by chili555 on 2011-08-12
> [[COLOR="Red"]0680[/COLOR]]: nVidia Corporation MCP51 Ethernet Controller [10de:0269] (rev a3)Your ethernet card is supposed to work with the module *forcedeth*. Let's load it and then check for interesting kernel messages:```
sudo modprobe forcedeth
dmesg | grep forcedeth
```Thanks.

---

### Post by thommy86 on 2011-08-12
It didnt show anything when typing my password.. but here is the result.

```
thommy@Thommy-Ubuntu:~$ sudo modprobe forcedeth
[sudo] password for thommy: 
Sorry, try again.
[sudo] password for thommy: 
thommy@Thommy-Ubuntu:~$ sudo modprobe forcedeth
thommy@Thommy-Ubuntu:~$ 
thommy@Thommy-Ubuntu:~$ dmesg | grep forcedeth
[    1.410346] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.64.
[    1.410586] forcedeth 0000:00:14.0: PCI INT A -> Link[LMAC] -> GSI 20 (level, high) -> IRQ 20
[    1.410592] forcedeth 0000:00:14.0: setting latency timer to 64
[    1.932740] forcedeth 0000:00:14.0: ifname eth0, PHY OUI 0x0 @ 1, addr 00:16:36:f1:0f:15
[    1.932745] forcedeth 0000:00:14.0: highdma pwrctl lnktim desc-v3
[   14.889401] forcedeth 0000:00:14.0: eth0: no link during initialization
```

---

### Post by chili555 on 2011-08-12
That all looks pretty normal. Do you have an interface eth0?```
ifconfig
sudo ethtool eth0
```

---

### Post by thommy86 on 2011-08-12
if you say so :)

here is the next result.

```
thommy@Thommy-Ubuntu:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:16:36:f1:0f:15  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:20 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:248 errors:0 dropped:0 overruns:0 frame:0
          TX packets:248 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:19488 (19.4 KB)  TX bytes:19488 (19.4 KB)

thommy@Thommy-Ubuntu:~$ 
thommy@Thommy-Ubuntu:~$ sudo ethtool eth0
[sudo] password for thommy: 
sudo: ethtool: command not found
thommy@Thommy-Ubuntu:~$ ^C
thommy@Thommy-Ubuntu:~$ 

```

---

### Post by chili555 on 2011-08-12
Please try:```
sudo mii-tool eth0
```Does Network Manager show an Auto eth0 to try to click and connect? Have you checked both ends of the ethernet cable? Is everything confirmed to be firmly plugged?

---

### Post by thommy86 on 2011-08-12
i tried a lot of cables.. and connection is on automatic..
when i open the manager i can see "auto eth0"

```
thommy@Thommy-Ubuntu:~$ sudo mii-tool eth0
SIOCGMIIPHY on 'eth0' failed: Operation not supported

```

---

### Post by chili555 on 2011-08-12
Yikes...what we are trying to get at is whether the ethernet port sees a router, modem or other access point at the other end. Please check:```
sudo lshw -C network
```We'd like to see this part:> *-network               
       description: Ethernet interface
       product: 82573L Gigabit Ethernet Controller
       vendor: Intel Corporation
       logical name: eth0
       version: 00
       capacity: 1Gbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=1.2.20-k2 firmware=0.5-1 latency=0 [COLOR="Red"]link=yes, no, maybe??[/COLOR] multicast=yes port=twisted pair
This will take a few moments; please be patient.

---

### Post by thommy86 on 2011-08-12
nothing happens.. first i see DMI for 1 second.. then i see "PCI (sysfs)" for a few seconds.. after that everything is gone..

---

### Post by chili555 on 2011-08-12
> **thommy86 said:**
> nothing happens.. first i see DMI for 1 second.. then i see "PCI (sysfs)" for a few seconds.. after that everything is gone..As I said:> This will take a few moments; please be patient. You could also try:```
sudo lshw
```You will get a long list and you can snip out all but your nVidia Corporation MCP51 Ethernet Controller.

-----------------
Note to Chili: It didn't show up as a 0200 and not as -C network. What in the world is goin' on here??

---

### Post by thommy86 on 2011-08-12
ì know.. i waited like you sad.. but really nothing happend.. i was just staring at a blinking square..

```
     *-bridge
          description: Ethernet interface
          product: MCP51 Ethernet Controller
          vendor: nVidia Corporation
          physical id: 14
          bus info: pci@0000:00:14.0
          logical name: eth0
          version: a3
          serial: 00:16:36:f1:0f:15
          capacity: 100000000
          width: 32 bits
          clock: 66MHz
          capabilities: bridge pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
          configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.64 latency=0 link=no maxlatency=20 mingnt=1 multicast=yes port=MII
          resources: irq:20 memory:b0008000-b0008fff ioport:30e0(size=8)
```

----------------------------------------------------------------------------------
like the note to yourself :) don't understand it.. but like it..
really thanks for your help!

---

### Post by chili555 on 2011-08-12
Of course, as we suspected, link=no. Notice that my ethernet card is of the class *-network; yours is *-bridge. I don't know if that's a problem, but while I sweat and Google, please let us see:```
dmesg | grep -i -e 00:14 -e warn -e error
```I learn something astounding every day!

---

### Post by chili555 on 2011-08-12
I have seen a lot of MCP51s on Google that identify as 'bridge.' I don't think that's an issue. I saw this: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/315947](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/315947)

Please see post #17. Are you dual-booting with Windows? If you click the Network Manager icon and edit connections, select wired ethernet, is the MAC address shown and correct?> description: Ethernet interface
          product: MCP51 Ethernet Controller
          vendor: nVidia Corporation
          physical id: 14
          bus info: pci@0000:00:14.0
          logical name: eth0
          version: a3
          serial: [COLOR="Red"]00:16:36:f1:0f:15[/COLOR]
          capacity: 100000000
          width: 32 bits
          clock: 66MHz
          capabilities: bridge pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
          configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.64 latency=0 link=no maxlatency=20 mingnt=1 multicast=yes port=MII
          resources: irq:20 memory:b0008000-b0008fff ioport:30e0(size=8)

---

### Post by thommy86 on 2011-08-12
No i'm not having windows on that laptop.. 
did a compleet clean install..

This is the response..
```
thommy@Thommy-Ubuntu:~$ dmesg grep -i -e 0014 -e warn -e error
dmesg: invalid option -- 'i'
Usage: dmesg [-c] [-n level] [-r] [-s bufsize]

```MAC adress is correct.. 00:16:36:F1:0F:15
MTU is on automatic.. and what i think is strange, is that last used is 5 days ago..

---

### Post by chili555 on 2011-08-12
> thommy@Thommy-Ubuntu:~$ dmesg grep -i -e 0014 -e warn -e errorYou forgot the pipe symbol | and the colon.> dmesg [COLOR="Red"]**|**[/COLOR] grep -i -e 00[COLOR="Red"]**:**[/COLOR]14 -e warn -e error

---

### Post by thommy86 on 2011-08-12
woeps sorry.. i am trying to type these things.. so i will learn better.. copy/past this time..

```
thommy@Thommy-Ubuntu:~$ dmesg | grep -i -e 00:14 -e warn -e error 
[    0.083338] pci 0000:00:14.0: [10de:0269] type 0 class 0x000680
[    0.083349] pci 0000:00:14.0: reg 10: [mem 0xb0008000-0xb0008fff]
[    0.083356] pci 0000:00:14.0: reg 14: [io  0x30e0-0x30e7]
[    0.083388] pci 0000:00:14.0: supports D1 D2
[    0.083390] pci 0000:00:14.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.083394] pci 0000:00:14.0: PME# disabled
[    1.410586] forcedeth 0000:00:14.0: PCI INT A -> Link[LMAC] -> GSI 20 (level, high) -> IRQ 20
[    1.410592] forcedeth 0000:00:14.0: setting latency timer to 64
[    1.932740] forcedeth 0000:00:14.0: ifname eth0, PHY OUI 0x0 @ 1, addr 00:16:36:f1:0f:15
[    1.932745] forcedeth 0000:00:14.0: highdma pwrctl lnktim desc-v3
[   13.951283] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
[   14.889401] forcedeth 0000:00:14.0: eth0: no link during initialization
[   17.240187] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
[   34.259077] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0

```

---

### Post by chili555 on 2011-08-13
I wonder if this is an issue. Please see post #7. [http://ubuntuforums.org/showthread.php?t=1585752](http://ubuntuforums.org/showthread.php?t=1585752)

Evidently, the forcedeth driver does not sense the orientation of the cable; either crossover or straight-through. Can you try a different cable?

Your settings and readings look entirely normal.

---

### Post by thommy86 on 2011-08-13
I uses 3 different cables.. en the cable i am using now is working on another laptop when i plug it in.. i am now trying a crossed cable but that doesn't work ether..
 
is there a way to get wifi working.. maybe the slot of the cable is broken?

could it be helpful to install windows on it..? so i can test if all work..

---

### Post by thommy86 on 2011-08-14
I did a clean install again and got this error after the install..
The picture isnt very clear, but you can see what goes wrong..

[IMG]http://i51.tinypic.com/ehyxhj.jpg[/IMG]

---

### Post by thommy86 on 2011-08-15
[chili555]("http://ubuntuforums.org/member.php?u=35909") can you please advice me what my best options are..!

Thanks!

---

### Post by chili555 on 2011-08-16
> is there a way to get wifi working.. Let's try. Is it a USB device? Please run and post:```
lsusb
```I see nothing in your lspci that is a wireless device.

---

### Post by thommy86 on 2011-08-18
There should be a wireless network card build in the laptop. this afternoon i will buy a usb wifi stick.. 
 
will report this evening..

---

### Post by chili555 on 2011-08-18
I'll look forward to your report. I'll be very glad to help you.

---

### Post by thommy86 on 2011-08-26
When i plugged in my new wifi dongle, my internet worked immediately.. 

thanks all for your help, especially chili555

the stick i bought is a Konig WLAN USB Dongle 300 Mbps

---

### Post by northd_tech on 2011-08-26
Did anyone think to go into the BIOS and Enable the onboard ethernet?  (Different BIOS'es have WAAAAY different menus, but it might be/might have been worth a shot).

---

