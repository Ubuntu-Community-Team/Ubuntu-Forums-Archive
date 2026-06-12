---
title: "No access to internet, everything seems ok though!?"
date: 2009-08-26
forum: Networking &amp; Wireless
---

### Post by TraBruno on 2009-08-26
Hello,
 
I am about to install ubuntu to dual boot with vista, but I seem to have a problem using my wireless connection to get on the internet on a live session. Everything seems ok though, the system recognizes my wireless adaptor and I can choose my network, fill in the password (WPA personal) and establish a connection. Nevertheless, firefox refuses to go to any remote site. I ran a whole bunch of tests and I'm at a lost. The strange thing is that it seems to affect my connection in vista afterwards! Normally I never have any problem connecting to the net in vista, but two times immediately after running a live session I had problems. Does anyone have a clue? At this point I'm hesitating to go through with installing ubuntu, because I need my connection daily.
 
 
These are the commands I ran in my last live session ubuntu.
 
 
```
ubuntu@ubuntu:~$ iwconfig:
 
lo        no wireless extensions.
eth0      no wireless extensions.
wmaster0  no wireless extensions.
wlan0     IEEE 802.11bg  ESSID:"NETGEARTINA"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:1F:33:22:73:CE   
          Bit Rate=1 Mb/s   Tx-Power=20 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality=30/100  Signal level:-56 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
pan0      no wireless extensions
--------------------------------------------------------------------------------------------
 
ubuntu@ubuntu:~$ sudo lshw -businfo
Bus info          Device      Class       Description
=====================================================
                              system      WIM2160
                              bus         WIM2160
                              memory      100KiB BIOS
[EMAIL="cpu@0"]cpu@0[/EMAIL]                         processor   Genuine Intel(R) CPU           T2130  @ 1.86GHz
                              memory      16KiB L1 cache
                              memory      1MiB L2 cache
                              processor   Logical CPU
                              processor   Logical CPU
                              memory      2GiB System Memory
                              memory      1GiB SODIMM Synchronous
                              memory      1GiB SODIMM Synchronous
[EMAIL="cpu@1"]cpu@1[/EMAIL]                         processor   
                              processor   Logical CPU
                              processor   Logical CPU
pci@0000:00:00.0              bridge      Mobile 945GM/PM/GMS, 943/940GML and 945GT Expres
pci@0000:00:02.0              display     Mobile 945GM/GMS, 943/940GML Express Integrated 
pci@0000:00:02.1              display     Mobile 945GM/GMS/GME, 943/940GML Express Integra
pci@0000:00:1b.0              multimedia  82801G (ICH7 Family) High Definition Audio Contr
pci@0000:00:1c.0              bridge      82801G (ICH7 Family) PCI Express Port 1
pci@0000:00:1c.1              bridge      82801G (ICH7 Family) PCI Express Port 2
pci@0000:04:00.0  eth0        network     RTL8101E/RTL8102E PCI Express Fast Ethernet cont
pci@0000:00:1c.3              bridge      82801G (ICH7 Family) PCI Express Port 4
pci@0000:00:1d.0              bus         82801G (ICH7 Family) USB UHCI Controller #1
pci@0000:00:1d.1              bus         82801G (ICH7 Family) USB UHCI Controller #2
pci@0000:00:1d.2              bus         82801G (ICH7 Family) USB UHCI Controller #3
pci@0000:00:1d.3              bus         82801G (ICH7 Family) USB UHCI Controller #4
pci@0000:00:1d.7              bus         82801G (ICH7 Family) USB2 EHCI Controller
pci@0000:00:1e.0              bridge      82801 Mobile PCI Bridge
pci@0000:0a:09.0              bus         R5C832 IEEE 1394 Controller
pci@0000:0a:09.1              system      R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter
pci@0000:0a:09.2              system      R5C592 Memory Stick Bus Host Adapter
pci@0000:0a:09.3              system      xD-Picture Card Controller
pci@0000:0a:09.4              generic     Illegal Vendor ID
pci@0000:00:1f.0              bridge      82801GBM (ICH7-M) LPC Interface Bridge
pci@0000:00:1f.1  scsi4       storage     82801G (ICH7 Family) IDE Controller
scsi@4:0.0.0      /dev/cdrom  disk        DVDRAM GSA-T20N
                  /dev/cdrom  disk        
pci@0000:00:1f.2  scsi0       storage     82801GBM/GHM (ICH7 Family) SATA AHCI Controller
scsi@0:0.0.0      /dev/sda    disk        160GB WDC WD1600BEVS-2
scsi@0:0.0.0,1    /dev/sda1   volume      30GiB Extended partition
                  /dev/sda5   volume      30GiB W95 FAT32 partition
scsi@0:0.0.0,2    /dev/sda2   volume      104GiB Windows NTFS volume
pci@0000:00:1f.3              bus         82801G (ICH7 Family) SMBus Controller
                  wlan0       network     Wireless interface
                  pan0        network     Ethernet interface
--------------------------------------------------------------------------------------------
ubuntu@ubuntu:~$ ifconfig 
eth0      Link encap:Ethernet  HWaddr 00:16:d3:84:56:78  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:251 Base address:0x6000 
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:100 errors:0 dropped:0 overruns:0 frame:0
          TX packets:100 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:9099 (9.0 KB)  TX bytes:9099 (9.0 KB)
wlan0     Link encap:Ethernet  HWaddr 00:07:ca:06:b6:62  
          inet addr:192.168.1.4  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::207:caff:fe06:b662/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:30 errors:0 dropped:0 overruns:0 frame:0
          TX packets:253 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:5425 (5.4 KB)  TX bytes:22730 (22.7 KB)
wmaster0  Link encap:UNSPEC  HWaddr 00-07-CA-06-B6-62-36-36-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
--------------------------------------------------------------------------------------------
ubuntu@ubuntu:~$ sudo iwlist wlan0 scan
wlan0     Scan completed :
          Cell 01 - Address: 00:1F:33:22:73:CE
                    ESSID:"NETGEARTINA"
                    Mode:Master
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=32/100  Signal level:-55 dBm  
                    Encryption key:on
                    IE: Unknown: 000B4E45544745415254494E41
                    IE: Unknown: 010882848B960C183048
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0100
                    IE: Unknown: 32041224606C
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s; 9 Mb/s; 18 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:tsf=0000029baa391724
                    Extra: Last beacon: 3652ms ago
--------------------------------------------------------------------------------------------
ubuntu@ubuntu:~$ sudo lshw:
 
*-network:0
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:07:ca:06:b6:62
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=192.168.1.4 multicast=yes wireless=IEEE 8
--------------------------------------------------------------------------------------------
ubuntu@ubuntu:~$ ping -c 4 127.0.0.1
PING 127.0.0.1 (127.0.0.1) 56(84) bytes of data.
64 bytes from 127.0.0.1: icmp_seq=1 ttl=64 time=0.051 ms
64 bytes from 127.0.0.1: icmp_seq=2 ttl=64 time=0.039 ms
64 bytes from 127.0.0.1: icmp_seq=3 ttl=64 time=0.039 ms
64 bytes from 127.0.0.1: icmp_seq=4 ttl=64 time=0.040 ms
--- 127.0.0.1 ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 2997ms
rtt min/avg/max/mdev = 0.039/0.042/0.051/0.006 ms
--------------------------------------------------------------------------------------------
ubuntu@ubuntu:~$ ping -c 4 192.168.1.4
PING 192.168.1.4 (192.168.1.4) 56(84) bytes of data.
64 bytes from 192.168.1.4: icmp_seq=1 ttl=64 time=0.054 ms
64 bytes from 192.168.1.4: icmp_seq=2 ttl=64 time=0.045 ms
64 bytes from 192.168.1.4: icmp_seq=3 ttl=64 time=0.044 ms
64 bytes from 192.168.1.4: icmp_seq=4 ttl=64 time=0.044 ms
--- 192.168.1.4 ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 2999ms
rtt min/avg/max/mdev = 0.044/0.046/0.054/0.009 ms
 
--------------------------------------------------------------------------------------------
ubuntu@ubuntu:~$ ping -c 4 216.239.57.99
PING 216.239.57.99 (216.239.57.99) 56(84) bytes of data.
--- 216.239.57.99 ping statistics ---
4 packets transmitted, 0 received, 100% packet loss, time 3025ms
ubuntu@ubuntu:~$ 
 

```
 
Thanks in advance folks!
TraBruno

---

### Post by peepingtom on 2009-08-26
The ubuntu community should always deny responsibility for anything bad, I bet your wireless chipset is fine :D

Try unplugging your laptop, removing your battery and see if Vista is still messed up, this sounds very unpleasant and i'm sorry it happened to you.
These wifi chipsets load firmware through the drivers, something went wrong here I suppose but it shouldn't be permanent after loss of power.

I'm not sure if i'm stupid today, but I didnt see the model number of your wireless device there. Is it a USB device (perhaps internal?) or does 82801G have a wireless component? I probably overlooked this, but if you're brave enough give us ```
lspci &#8211;v | less
``` or ```
lsusb
``` regarding something about wireless or network, please.

Or see if your situation applies to this thread
[http://ubuntuforums.org/showthread.php?t=1176117](http://ubuntuforums.org/showthread.php?t=1176117)

Regardless, someone will help you.

---

### Post by TraBruno on 2009-08-26
I really wouldn't know about that but I'll run those commands and we'll see. Ok, let me just sneak back into a live session, and hope to find a working internet connection waiting for me when I get back!
 
Thanks for replying by the way!

---

### Post by TraBruno on 2009-08-26
Ok,
 
I'm back, yesterday I had enough for the night.
I went back into a live session and ran those commands. As expected my internet connection was dead coming back into vista, but removing the battery worked! A bit harsh though, to implement as a new dual boot policy, so I would still like to solve that problem. 
 
This is what I got:
 
```

lspci -v | less
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Expre
ss Memory Controller Hub (rev 03)
        Subsystem: Wistron Corp. Device 4070
        Flags: bus master, fast devsel, latency 0
        Capabilities: <access denied>
        Kernel driver in use: agpgart-intel
        Kernel modules: intel-agp
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Expr
ess Integrated Graphics Controller (rev 03)
        Subsystem: Wistron Corp. Device 4070
        Flags: bus master, fast devsel, latency 0, IRQ 16
        Memory at d8100000 (32-bit, non-prefetchable) [size=512K]
        I/O ports at 1800 [size=8]
        Memory at c0000000 (32-bit, prefetchable) [size=256M]
        Memory at d8200000 (32-bit, non-prefetchable) [size=256K]
        Capabilities: <access denied>
        Kernel modules: intelfb
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express
 Integrated Graphics Controller (rev 03)
        Subsystem: Wistron Corp. Device 4070
        Flags: bus master, fast devsel, latency 0
        Memory at d8180000 (32-bit, non-prefetchable) [size=512K]
        Capabilities: <access denied>
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Con
troller (rev 02)
        Subsystem: Wistron Corp. Device 4071
        Flags: bus master, fast devsel, latency 0, IRQ 21
        Memory at d8440000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>
        Kernel driver in use: HDA Intel
        Kernel modules: snd-hda-intel
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=02, subordinate=03, sec-latency=0
        I/O behind bridge: 00002000-00002fff
        Memory behind bridge: d4000000-d5ffffff
        Prefetchable memory behind bridge: 00000000d0000000-00000000d1ffffff
        Capabilities: <access denied>
        Kernel driver in use: pcieport-driver
        Kernel modules: shpchp
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=04, subordinate=05, sec-latency=0
        I/O behind bridge: 00003000-00003fff
        Memory behind bridge: d6000000-d7ffffff
        Prefetchable memory behind bridge: 00000000d2000000-00000000d3ffffff
        Capabilities: <access denied>
        Kernel driver in use: pcieport-driver
        Kernel modules: shpchp
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 02)
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=06, subordinate=06, sec-latency=0
        Capabilities: <access denied>
        Kernel driver in use: pcieport-driver
        Kernel modules: shpchp
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
        Subsystem: Wistron Corp. Device 4071
        Flags: bus master, medium devsel, latency 0, IRQ 23
        I/O ports at 1820 [size=32]
        Kernel driver in use: uhci_hcd
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
        Subsystem: Wistron Corp. Device 4071
        Flags: bus master, medium devsel, latency 0, IRQ 17
        I/O ports at 1840 [size=32]
        Kernel driver in use: uhci_hcd
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
        Subsystem: Wistron Corp. Device 4071
        Flags: bus master, medium devsel, latency 0, IRQ 18
        I/O ports at 1860 [size=32]
        Kernel driver in use: uhci_hcd
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
        Subsystem: Wistron Corp. Device 4071
        Flags: bus master, medium devsel, latency 0, IRQ 19
        I/O ports at 1880 [size=32]
        Kernel driver in use: uhci_hcd
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02) (prog-if 20)
        Subsystem: Wistron Corp. Device 4071
        Flags: bus master, medium devsel, latency 0, IRQ 23
        Memory at d8444000 (32-bit, non-prefetchable) [size=1K]
        Capabilities: <access denied>
        Kernel driver in use: ehci_hcd
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2) (prog-if 01)
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=0a, subordinate=0a, sec-latency=32
        Memory behind bridge: d8000000-d80fffff
        Capabilities: <access denied>
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
        Subsystem: Wistron Corp. Device 4071
        Flags: bus master, medium devsel, latency 0
        Capabilities: <access denied>
        Kernel modules: iTCO_wdt, intel-rng
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02) (prog-if 8a [Master SecP PriP])
        Subsystem: Wistron Corp. Device 4071
        Flags: bus master, medium devsel, latency 0, IRQ 19
        I/O ports at 01f0 [size=8]
        I/O ports at 03f4 [size=1]
        I/O ports at 0170 [size=8]
        I/O ports at 0374 [size=1]
        I/O ports at 1810 [size=16]
        Kernel driver in use: ata_piix
00:1f.2 SATA controller: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA AHCI Controller (rev 02) (prog-if 01)
        Subsystem: Wistron Corp. Device 4071
        Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 2300
        I/O ports at 18d0 [size=8]
        I/O ports at 18c4 [size=4]
        I/O ports at 18c8 [size=8]
        I/O ports at 18c0 [size=4]
        I/O ports at 18b0 [size=16]
        Memory at d8444400 (32-bit, non-prefetchable) [size=1K]
        Capabilities: <access denied>
        Kernel driver in use: ahci
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
        Subsystem: Wistron Corp. Device 4071
        Flags: bus master, medium devsel, latency 0
        Capabilities: <access denied>
        Kernel modules: iTCO_wdt, intel-rng
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02) (prog-if 8a [Master SecP PriP])
        Subsystem: Wistron Corp. Device 4071
        Flags: bus master, medium devsel, latency 0, IRQ 19
        I/O ports at 01f0 [size=8]
        I/O ports at 03f4 [size=1]
        I/O ports at 0170 [size=8]
        I/O ports at 0374 [size=1]
        I/O ports at 1810 [size=16]
        Kernel driver in use: ata_piix
00:1f.2 SATA controller: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA AHCI Controller (rev 02) (prog-if 01)
        Subsystem: Wistron Corp. Device 4071
        Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 2300
        I/O ports at 18d0 [size=8]
        I/O ports at 18c4 [size=4]
        I/O ports at 18c8 [size=8]
        I/O ports at 18c0 [size=4]
        I/O ports at 18b0 [size=16]
        Memory at d8444400 (32-bit, non-prefetchable) [size=1K]
        Capabilities: <access denied>
        Kernel driver in use: ahci
0a:09.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 0a)
        Subsystem: Wistron Corp. Device 3305
        Flags: medium devsel, IRQ 11
        Memory at d8000c00 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>
        Kernel driver in use: ricoh-mmc
        Kernel modules: ricoh_mmc
0a:09.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 05)
        Subsystem: Wistron Corp. Device 3305
        Flags: medium devsel, IRQ 11
        Memory at d8001000 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>
0a:09.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff) (prog-if ff)
        !!! Unknown header type 7f
-----------------------------------------------------------------------------
lsusb
[EMAIL="ubuntu@ubuntu:~$"]ubuntu@ubuntu:~$[/EMAIL] lsusb
Bus 001 Device 003: ID 0bda:8189 Realtek Semiconductor Corp. RTL8187B Wireless 802.11g 54Mbps Network Adapter
Bus 001 Device 002: ID 064e:a100 Suyin Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```
 
Hope this helps to find a possible flaw in my system, cause I don't make anything out of it!
 
Greetings

---

### Post by TraBruno on 2009-08-26
Just found out this wireless device of mine causes lot's of trouble for lot's of people. Hope I can get anything out of it, cause I'm not an expert in recompiling, scripting, 'power user' commands, sudo and 'lshrxddfg/::!!' stuff! :) Wish me luck

---

### Post by Iowan on 2009-08-26
The problem when switching between Linux and Windows seems to be recurring - goes both ways.  There was a post some time ago that mentioned interface drivers don't always get reset when going between the two unless a power-down restart is performed.

---

### Post by peepingtom on 2009-08-27
To sum up: the issue is with internal USB Device Bus 001 Device 003: ID 0bda:8189 Realtek Semiconductor Corp. RTL8187B Wireless 802.11g 54Mbps Network Adapter

RTL8187B does in fact seem to take issue with Linux :( . Ubuntu is really cool and lots of people want you to make the switch, i'll google around and hopefully have something for you in a few hours. 

[Here]("https://launchpad.net/ubuntu/+bugs?field.searchtext=RTL8187B&orderby=-importance&search=Search&field.status%3Alist=NEW&field.status%3Alist=INCOMPLETE_WITH_RESPONSE&field.status%3Alist=INCOMPLETE_WITHOUT_RESPONSE&field.status%3Alist=CONFIRMED&field.status%3Alist=TRIAGED&field.status%3Alist=INPROGRESS&field.status%3Alist=FIXCOMMITTED&field.assignee=&field.bug_reporter=&field.omit_dupes=on&field.has_patch=&field.has_no_package=") are the relavant bug reports for Ubuntu regarding your card. Other people have the exact same problem, and some [have solved it]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/346987").

You can try using [http://cdimage.ubuntu.com/releases/karmic/alpha-4/"]Karmic Koala]("), the version of Ubuntu set to be released in October. It has a newer version of the Linux kernel (Drivers tend to be a part of the kernel). Since some people fixed their card using a backport module (which I believe is when they send stuff from a later version of software to an older one), you should DEFINITELY TRY THIS......and then wait for Karmic to stabilise a bit before using it, unless you want headaches.

[http://www.datanorth.net/~cuervo/blog/rtl8187b-drivers-and-patches/](http://www.datanorth.net/~cuervo/blog/rtl8187b-drivers-and-patches/)
^^This guy has patched the driver for Linux and seems to have it working, this is a complicated solution though. However, he says the problems are fixed after 2.6.27 Linux Kernel so TRY KARMIC KOALA :D This patch is old and I bet it doesn't work and then nobody will help you around here, also you'd need an internet connection to even pursue this. Might work though, i'm no programmer.

The easy way out of course would be to spend $12 on an external USB wireless device, monoprice.com has cheap ones with cheap shipping if you're in the US, I use one advertised as ralink 2571 that's actually rt2870sta.
Does wireless in Vista work if instead of restarting from the live-CD you shut down and turn on again, or do you have to pull the battery?

Any way (except KARMIC fixing it :D) the solution is inelegant and this sucks, hopefully we can get your internal one working without headache after some people put effort into it. If you fix this, file a bug report and let people know so this doesn't happen to someone else. You might be responsible for 50 other people switching without headaches, these are the worst kinds of bugs!

---

### Post by TraBruno on 2009-08-27
Hello Peepingtom,
 
I couldn't keep myself from installing the system so I did, even if I still don't have a connection. I did find a thread on the forum ([http://ubuntuforums.org/showthread.php?t=792092&highlight=RTL8187b+%26amp%3B+HOWTO%3A&page=26](http://ubuntuforums.org/showthread.php?t=792092&highlight=RTL8187b+%26amp%3B+HOWTO%3A&page=26)) where someone posted a new driver for my card directly from the manufacturer that seemed to work for quite a few people so I wanted to try that out. Problem now is that I can't seem to boot into ubuntu anymore since I reinstalled the vista bootloader and installed neogrub. I was just about to post another please-help-me-out-someone thread about this.
 
If I reboot into vista from ubuntu without pulling out the battery, I still don't have a connection there either, to aswer that question, but hopefully, IF I get back into ubuntu, and IF I manage to install this new driver, I will be able get cracking.
 
Thanks for looking into it! Hope to catch you later
(let's get posting my new problem...)

---

### Post by TraBruno on 2009-08-27
Hi!
I'm very happy, proud and excited to make my first entry on the forum from firefox running on ubuntu 9.04!

Boot problem fixed with NeoSmart EasyBCD 2.0, the beta version. I used the instructions posted in the neosmart forum on this location: [http://neosmart.net/forums/showthread.php?t=3990&highlight=neogrub+dual](http://neosmart.net/forums/showthread.php?t=3990&highlight=neogrub+dual)

Solving the wifi problem was easy enough following the instructions posted here: [http://ubuntuforums.org/showthread.php?p=7157415#post7157415](http://ubuntuforums.org/showthread.php?p=7157415#post7157415)

Anyone with the Realtek **RTL8187B **card having any problem should check it out.

Thanks everyone for helping out, I'm very happy. This is a nice forum, and I love my new system!

Ciao for now,
TraBruno

---

### Post by TraBruno on 2009-08-27
Epilogue: after a whole bunch of automatic upgrades and rebooting, there was no wireless signal AT ALL. Had something to do with blacklisting the native driver I suppose and not yet installing the alternative. Anyway, I just did the same I did before and it runs like a dream.
Good luck

---

