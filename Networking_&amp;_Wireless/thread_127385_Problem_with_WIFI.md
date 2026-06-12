---
title: "Problem with WIFI"
date: 2006-02-08
forum: Networking &amp; Wireless
---

### Post by ia_ on 2006-02-08
I need to set up a driver for a D-Link DWL-650 wifi card. As far as I know there are two ways to do this. 


1. I could use ndiswrapper, which I've installed. The driver recommended by ndiswrapper is the D-Link XP driver located at [ftp://ftp.dlink.com/Wireless/DWL650/Driver/dwl650_driver_1737F.exe](ftp://ftp.dlink.com/Wireless/DWL650/Driver/dwl650_driver_1737F.exe). The INF drivers are somewhere in one of the two CAB files in that package. 

The problem I have is that I have no way to open those CAB files. Winzip refuses to open them, saying they are 'not in the standard Microsoft CAB format (as defined in mid-1998). The "signature bytes" required by the Microsoft CAB specification are missing.' I don't have a clue how to get around this. I searched for an alternate D-Link DWL-650 XP driver and found one, netcw10.inf. After installing this with ndiswrapper, System->Administration->Wireless Network Drivers listed this driver as being installed, but also said "Hardware present: No".


2. I could use the linux-native linux-wlan-ng driver, version 2.3.0. It's hosted at [ftp://ftp.linux-wlan.org/pub/linux-wlan-ng/](ftp://ftp.linux-wlan.org/pub/linux-wlan-ng/). As far as I've been able to find, there aren't pre-existing binaries I can use. The linux-wlan-ng driver readme tells me that to build it I need 1. a configured kernel source code for the kernel I'm running and 2. the configured PCMCIA source code for the pcmcia_cs subsystem I'm running. 

I don't know how to get a copy of the source code because I don't have a working internet connection on the laptop in question, and so I can't use any apt-get type commands. I do have an internet connection, but it's attached to a desktop running XP and RH9 (old, I know). I don't know how to get the configured PCMCIA source code (specific to my laptop?) because I'm a newbie. 

Can anyone help with either of these problems?

__________________________________________
Here is my configuration:

 @ia:~$ sudo lshw -C network
  *-network
	description: Link DWL-650 11Mbps WLAN Card
	product: Version 01.02
	vendor: D
	physical id: 0
	slot: Socket 0
	resources: irq:3
  *-network
	description: Wireless interface
	physical id: 1
	logical name: eth0
	serial: 00:05:5d:a7:2b:c2
	capabilities: ethernet physical wireless
	configuration: broadcast=yes ip=192.168.0.6 multicast=yes wireless=IEEE 802.11-DS 


 @ia:~$ lspci
0000:00:00.0 Host bridge: Intel Corp. 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (rev 03)
0000:00:01.0 PCI bridge: Intel Corp. 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge (rev 03)
0000:00:02.0 CardBus bridge: Texas Instruments PCI1450 (rev 03)
0000:00:02.1 CardBus bridge: Texas Instruments PCI1450 (rev 03)
0000:00:03.0 Communications controller: Lucent Microelectronics WinModem 56k (rev 01)
0000:00:05.0 Multimedia audio controller: Cirrus Logic CS 4614/22/24 [CrystalClear SoundFusion Audio Accelerator] (rev 01)
0000:00:07.0 Bridge: Intel Corp. 82371AB/EB/MB PIIX4 ISA (rev 02)
0000:00:07.1 IDE interface: Intel Corp. 82371AB/EB/MB PIIX4 IDE (rev 01)
0000:00:07.2 USB Controller: Intel Corp. 82371AB/EB/MB PIIX4 (rev 01)
0000:00:07.3 Bridge: Intel Corp. 82371AB/EB/MB PIIX4 ACPI (rev 03)
0000:01:00.0 VGA compatible controller: S3 Inc. 86C270-294 Savage/IX-MV (rev 13)

 @ia:~$ lspci -n
0000:00:00.0 0600: 8086:7190 (rev 03)
0000:00:01.0 0604: 8086:7191 (rev 03)
0000:00:02.0 0607: 104c:ac1b (rev 03)
0000:00:02.1 0607: 104c:ac1b (rev 03)
0000:00:03.0 0780: 11c1:0449 (rev 01)
0000:00:05.0 0401: 1013:6003 (rev 01)
0000:00:07.0 0680: 8086:7110 (rev 02)
0000:00:07.1 0101: 8086:7111 (rev 01)
0000:00:07.2 0c03: 8086:7112 (rev 01)
0000:00:07.3 0680: 8086:7113 (rev 03)
0000:00:00.0 0300: 5333:8c12 (rev 13)

 @ia:~$ sudo cardctl ident
Socket 0:
  product info: "D", "Link DWL-650 11Mbs WLAN Card", "Version 01.02",""
  manfid: 0x0156, 0x0002
  function:  6 (network)
Socket 1:
  no product info available

---

### Post by ia_ on 2006-02-10
Two days and no replies... Can anyone help?

---

### Post by dcast on 2006-02-10
are ou sure the package isnt in synaptic?

---

### Post by dcast on 2006-02-10
oh woops sorry didnt real thoroughly. no internet...

---

### Post by dcast on 2006-02-10
that might help:

[http://stef.tvk.rwth-aachen.de/~nazgul/debian/DWL-650+_Howto.html](http://stef.tvk.rwth-aachen.de/~nazgul/debian/DWL-650+_Howto.html)

---

### Post by Lambert on 2006-02-10
I'll give you some help with option 1.

1. download and copy the win drivers onto your ubuntu pc
2. From the following link, download and copy to your ubntu pc the correct .deb files of:
   1. unshield
   2. libunshield
[http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=unshield&searchon=names&subword=1&version=breezy&release=all](http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=unshield&searchon=names&subword=1&version=breezy&release=all)

do not worry about the libunshield-dev file, you do not need.

Then from a terminal go to the directory you copied the files to and in this order

```

dpkg -i libunshield.deb
dpkg -i unshield.deb

``` 
you will need to make sure the package name is correct as mine probably isn't

Now, first unzip the .exe file

```

unzip dwl650_driver_1737F.exe

``` 
then to extract the .cab files you would type

```

unshield x data1.cab
unshield x data2.cab

``` 
You should now have your driver files in a directory called WinXP_Driver_Files, you can continue with using ndiswrapper.

---

### Post by ia_ on 2006-02-14
Hi, 

I followed your steps and was able to make some progress, but I'm stuck again. 

The extracted XP driver files (CW10.sys and netcw10.inf), when put into a directory together, don't install properly with ndiswrapper (sudo ndiswrapper -i ~/drivers/xp-wifi/netcw10.inf). I get the error "invalid driver". 

The Windows 2000 driver files (PRISMDS.sys and PRISMNIC.inf) install correctly, and ndiswrapper -l lists "driver present", but I still have the error in System->Administration->Windows Wireless Drivers "Hardware not present".

sudo lshw -C network lists:
 *-network
         description: Link DWL-650 11Mbps WLAN Card
         product: Version 01.02
         vendor: D
         physical id: 0
         slot: Socket 0
         resources: irq:3
 *-network
         description: Wireless interface
         physical id: 1
         logical name: eth0
         serial: 00:05:5d:a7:b2:c2
         capabilities: ethernet physical wireless
         configuration: broadcast=yes ip=192.168.0.6 multicast=yes wireless=IEEE 802.11-DS

How do I make the card and drivers see each other? I also have a 56k modem that shows up under sudo lshw -C communication. Could this be interfering?

---

### Post by Lambert on 2006-02-14
Now that I look closer I believe you already have a driver loaded and bound to the device. run these two commands.

cat /etc/pcmcia/config | grep -A 3 -B 2 "0x0156, 0x0002"

and 

lsmod | grep ori

and post output here.

If this is the case, all you have to do is configure eth0 (which is the logical interface assigned to the device) in system->administration->networking

It also looks like you have an ip address assigned to the device 192.168.0.6

So also post output of 

iwconfig
ifconfig
arp -a
ping -c 4 82.211.81.166
ping -c 4 [www.ubuntulinux.com](www.ubuntulinux.com)

what are your results?

---

### Post by ia_ on 2006-02-14
I typed in the ip address, along with the network name and a few other things in System->Networking when I first put the card in. 

Here's output from those commands:

@ia:~$ cat /etc/pcmcia/config | grep -A 3 -B 2 "0x0002"

card "Allied Telesis LA-PCM Ethernet"
  manfid 0xc00f, 0x0002
  cis "cis/LA-PCM.dat"
  bind "pcnet_cs"

--

card "Intersil PRISM2 11 Mbps Wireless Adapter"
  manfid 0x0156, 0x0002
  bind "orinoco_cs"

card "Actiontec HWC01170-01"
--

card "ASUS SpaceLink WL-100"
  manfid 0x02aa, 0x0002
  bind "orinoco_cs"

card "3Com AirConnect"
--

card "Compaq WL100 11 Mbps Wireless Adapter"
  manfid 0x0138, 0x0002
  bind "orinoco_cs"

card "Compaq HNW-100 11 Mbps Wireless Adapter"
  manfid 0x028a, 0x0002
  bind "orinoco_cs"

card "Corega PCCA-11"
--

card "Safeway 802.11b Wireless Adapter"
  manfid 0xd601, 0x0002
  bind "orinoco_cs"

card "SAMSUNG 11Mbps WLAN Card"
--
card "SpeedStream SS1021 Wireless Adapter"
  #version "Siemens", "SpeedStream Wireless PCMCIA"
  manfid 0x02ac, 0x0002
  bind "orinoco_cs"

card "Xircom CreditCard Netwave"
--
card "ZCOMAX AirRunner/XI-300"
  #version "ZCOMAX", "AirRunner/XI-300"
  manfid 0xd601, 0x0002
  bind "orinoco_cs"

card "AirWay 802.11 Adapter (PCMCIA)"
  #version "AirWay", "802.11 Adapter (PCMCIA)"
  manfid 0x0261, 0x0002
  bind "orinoco_cs"

card "NetGear MA401RA"
--

card "Conceptronic CON11Cpro"
  manfid 0xc250, 0x0002
  bind "orinoco_cs"

#
--
# too generic
#card "Brain Boxes 2-Port RS-232"
#  manfid 0x0160, 0x0002
#  bind "serial_cs" to 0, "serial_cs" to 1

card "Brain Boxes BL-500 Bluetooth Adapter"
  #manfid 0x0160, 0x0002
  version "Brain Boxes", "Bluetooth PC Card"
  bind "serial_cs"
______________________________________________

@ia:~$ lsmod | grep ori
orinoco_cs              8456  1
orinoco                33932  1 orinoco_cs
hermes                  6912  2 orinoco_cs,orinoco
pcmcia                 24584  5 orinoco_cs
pcmcia_core            44932  4 orinoco_cs,pcmcia,yenta_socket,rsrc_nonstatic
______________________________________________

@ia:~$ iwconfig
lo        no wireless extensions.

eth0      IEEE 802.11-DS  ESSID:"linksys7208skynet"  Nickname:"Prism  I"
          Mode:Managed  Frequency:2.462 GHz  Access Point: 44:44:44:44:44:44
          Bit Rate:2 Mb/s   Tx-Power=15 dBm   Sensitivity:1/3
          Retry min limit:8   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/92  Signal level=-68 dBm  Noise level=-122 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.
______________________________________________

@ia:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:05:5D:A7:2B:C2
          inet addr:192.168.0.6  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::205:5dff:fea7:2bc2/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:3 Base address:0x100

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2077 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2077 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:187278 (182.8 KiB)  TX bytes:187278 (182.8 KiB)
______________________________________________

@ia:~$ arp -a  (there was no output)
______________________________________________

@ia:~$ ping -c 4 82.211.81.166
PING 82.211.81.166 (82.211.81.166) 56(84) bytes of data.
From 192.168.0.6 icmp_seq=2 Destination Host Unreachable
From 192.168.0.6 icmp_seq=3 Destination Host Unreachable
From 192.168.0.6 icmp_seq=4 Destination Host Unreachable

--- 82.211.81.166 ping statistics ---
4 packets transmitted, 0 received, +3 errors, 100% packet loss, time 2998ms
, pipe 3
______________________________________________

@ia:~$ ping -c 4 [www.ubuntu.com](www.ubuntu.com)
ping: unknown host [www.ubuntu.com](www.ubuntu.com)

---

### Post by Lambert on 2006-02-15
>  eth0      IEEE 802.11-DS  ESSID:"linksys7208skynet"  Nickname:"Prism  I"
          Mode:Managed  Frequency:2.462 GHz  Access Point: 44:44:44:44:44:44

Do you know what this is? Is this your access point?

Card looks like it's working, associated with an ap, and assigned an ip. But there's no connection on the physical layer which arp -a shows....hmmmm

this looks weird with the 802.11-ds and all 4s in the ap mac address.

Also if you unplug the card, then plug it back in, and then run dmesg what output do you get?

---

### Post by ia_ on 2006-02-15
eth0 IEEE 802.11-DS ESSID:"linksys7208skynet" Nickname:"Prism I"
Mode:Managed Frequency:2.462 GHz Access Point: 44:44:44:44:44:44

I typed in the access point and ip manually when I first plugged in the card, in System->Administration->Networking. I don't know where "Prism I" came from, I never typed that in. I also don't know where all 4's came from, the AP's lan mac address is 00:12:17:6A:DE:10. 

Taking the card out and putting it back in, dmesg gives:

@ia:~$ dmesg
4>[4294667.296000] Built 1 zonelists
[4294667.296000] Kernel command line: root=/dev/hda1 ro quiet splash
[4294667.296000] Local APIC disabled by BIOS -- you can enable it with "lapic"
[4294667.296000] mapped APIC to ffffd000 (01201000)
[4294667.296000] Initializing CPU#0
[4294667.296000] PID hash table entries: 2048 (order: 11, 32768 bytes)
[4294667.296000] Detected 697.071 MHz processor.
[4294667.296000] Using pmtmr for high-res timesource
[4294667.296000] Console: colour VGA+ 80x25
[4294671.038000] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[4294671.040000] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[4294671.068000] Memory: 251396k/262144k available (1415k kernel code, 9960k res erved, 763k data, 224k init, 0k highmem)
[4294671.068000] Checking if this processor honours the WP bit even in superviso r mode... Ok.
[4294671.068000] Calibrating delay loop... 1380.35 BogoMIPS (lpj=690176)
[4294671.091000] Security Framework v1.0.0 initialized
[4294671.091000] SELinux:  Disabled at boot.
[4294671.091000] Mount-cache hash table entries: 512
[4294671.091000] CPU: After generic identify, caps: 0383f9ff 00000000 00000000 0 0000000 00000000 00000000 00000000
[4294671.091000] CPU: After vendor identify, caps: 0383f9ff 00000000 00000000 00 000000 00000000 00000000 00000000
[4294671.091000] CPU: L1 I cache: 16K, L1 D cache: 16K
[4294671.091000] CPU: L2 cache: 256K
[4294671.091000] CPU: After all inits, caps: 0383f9ff 00000000 00000000 00000040  00000000 00000000 00000000
[4294671.091000] CPU: Intel Pentium III (Coppermine) stepping 0a
[4294671.091000] Enabling fast FPU save and restore... done.
[4294671.091000] Enabling unmasked SIMD FPU exception support... done.
[4294671.091000] Checking 'hlt' instruction... OK.
[4294671.095000] Checking for popad bug... OK.
[4294671.095000] checking if image is initramfs... it is
[4294672.170000] Freeing initrd memory: 4821k freed
[4294672.172000] ACPI: Looking for DSDT in initrd... not found!
[4294672.349000]  not found!
[4294672.414000] ACPI: setting ELCR to 0200 (from 0800)
[4294672.442000] NET: Registered protocol family 16
[4294672.442000] EISA bus registered
[4294672.442000] ACPI: bus type pci registered
[4294672.442000] PCI: PCI BIOS revision 2.10 entry at 0xfd94f, last bus=7
[4294672.442000] PCI: Using configuration type 1
[4294672.442000] mtrr: v2.0 (20020519)
[4294672.443000] ACPI: Subsystem revision 20050729
[4294672.858000] ACPI: Interpreter enabled
[4294672.858000] ACPI: Using PIC for interrupt routing
[4294672.860000] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 10 *11)
[4294672.861000] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 9 10 *11)
[4294672.863000] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 9 10 *11)
[4294672.865000] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 9 10 *11)
[4294672.866000] ACPI: PCI Root Bridge [PCI0] (0000:00)
[4294672.866000] PCI: Probing PCI hardware (bus 00)
[4294672.867000] ACPI: Assume root bridge [\_SB_.PCI0] segment is 0
[4294672.867000] ACPI: Assume root bridge [\_SB_.PCI0] bus is 0
[4294672.979000] Boot video device is 0000:01:00.0
[4294672.995000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[4294673.209000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGP_._PRT]
[4294673.211000] ACPI: Power Resource [PSER] (off)
[4294673.211000] ACPI: Power Resource [PSIO] (on)
[4294673.213000] burst-mode-ec-10-Aug
[4294673.213000] ACPI: Embedded Controller [EC] (gpe 9)
[4294673.218000] Linux Plug and Play Support v0.97 (c) Adam Belay
[4294673.218000] pnp: PnP ACPI init
[4294673.330000] pnp: PnP ACPI: found 15 devices
[4294673.330000] PnPBIOS: Disabled by ACPI PNP
[4294673.330000] PCI: Using ACPI for IRQ routing
[4294673.330000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps , post a report
[4294673.337000] pnp: 00:01: ioport range 0x1000-0x103f could not be reserved
[4294673.337000] pnp: 00:01: ioport range 0x1040-0x104f has been reserved
[4294673.337000] pnp: 00:01: ioport range 0xfe00-0xfe0f has been reserved
[4294673.337000] pnp: 00:08: ioport range 0x15e0-0x15ef has been reserved
[4294673.338000] Simple Boot Flag at 0x35 set to 0x1
[4294673.339000] audit: initializing netlink socket (disabled)
[4294673.339000] audit: initialized
[4294673.339000] VFS: Disk quotas dquot_6.5.1
[4294673.339000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[4294673.339000] devfs: 2004-01-31 Richard Gooch (rgooch@atnf.csiro.au)
[4294673.339000] devfs: boot_options: 0x0
[4294673.339000] Initializing Cryptographic API
[4294673.339000] Limiting direct PCI/PCI transfers.
[4294673.340000] isapnp: Scanning for PnP cards...
[4294673.693000] isapnp: No Plug & Play device found
[4294673.736000] PNP: PS/2 Controller [PNP0303:KBD,PNP0f13:MOU] at 0x60,0x64 irq  1,12
[4294673.749000] serio: i8042 AUX port at 0x60,0x64 irq 12
[4294673.751000] serio: i8042 KBD port at 0x60,0x64 irq 1
[4294673.751000] Serial: 8250/16550 driver $Revision: 1.90 $ 54 ports, IRQ shari ng enabled
[4294673.758000] pnp: Device 00:0b activated.
[4294673.758000] ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[4294673.758000] io scheduler noop registered
[4294673.758000] io scheduler anticipatory registered
[4294673.758000] io scheduler deadline registered
[4294673.758000] io scheduler cfq registered
[4294673.759000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 bl ocksize
[4294673.762000] EISA: Probing bus 0 at eisa.0
[4294673.762000] Cannot allocate resource for EISA slot 1
[4294673.762000] EISA: Detected 0 cards.
[4294673.762000] NET: Registered protocol family 2
[4294673.771000] IP: routing cache hash table of 2048 buckets, 16Kbytes
[4294673.771000] TCP established hash table entries: 16384 (order: 5, 131072 byt es)
[4294673.771000] TCP bind hash table entries: 16384 (order: 4, 65536 bytes)
[4294673.772000] TCP: Hash tables configured (established 16384 bind 16384)
[4294673.772000] NET: Registered protocol family 8
[4294673.772000] NET: Registered protocol family 20
[4294673.772000] ACPI wakeup devices:
[4294673.772000]  LID SLPB PCI0  USB UART
[4294673.772000] ACPI: (supports S0 S1 S3 S4 S5)
[4294673.773000] Freeing unused kernel memory: 224k freed
[4294673.800000] input: AT Translated Set 2 keyboard on isa0060/serio0
[4294673.816000] vga16fb: initializing
[4294673.816000] vga16fb: mapped to 0xc00a0000
[4294673.951000] Console: switching to colour frame buffer device 80x30
[4294673.951000] fb0: VGA16 VGA frame buffer device
[4294675.133000] Capability LSM initialized
[4294675.165000] NET: Registered protocol family 1
[4294675.203000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[4294675.203000] ide: Assuming 33MHz system bus speed for PIO modes; override wi th idebus=xx
[4294675.203000] ACPI: bus type ide registered
[4294675.214000] PIIX4: IDE controller at PCI slot 0000:00:07.1
[4294675.214000] PIIX4: chipset revision 1
[4294675.214000] PIIX4: not 100% native mode: will probe irqs later
[4294675.214000]     ide0: BM-DMA at 0x1c10-0x1c17, BIOS settings: hda:DMA, hdb: pio
[4294675.214000]     ide1: BM-DMA at 0x1c18-0x1c1f, BIOS settings: hdc:DMA, hdd: pio
[4294675.214000] Probing IDE interface ide0...
[4294675.478000] hda: IBM-DJSA-232, ATA DISK drive
[4294676.091000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[4294676.091000] Probing IDE interface ide1...
[4294676.763000] hdc: HITACHI DVD-ROM GD-S250, ATAPI CD/DVD-ROM drive
[4294677.375000] ide1 at 0x170-0x177,0x376 on irq 15
[4294677.479000] Probing IDE interface ide2...
[4294677.992000] Probing IDE interface ide3...
[4294678.504000] Probing IDE interface ide4...
[4294679.016000] Probing IDE interface ide5...
[4294679.538000] hda: max request size: 128KiB
[4294679.566000] hda: 62506080 sectors (32003 MB) w/1874KiB Cache, CHS=65535/15/ 63, UDMA(33)
[4294679.566000] hda: cache flushes not supported
[4294679.566000]  /dev/ide/host0/bus0/target0/lun0: p1 p2 < p5 >
[4294679.623000] hdc: ATAPI 24X DVD-ROM drive, 512kB Cache
[4294679.623000] Uniform CD-ROM driver Revision: 3.20
[4294680.297000] Attempting manual resume
[4294680.302000] swsusp: Suspend partition has wrong signature?
[4294680.488000] usbcore: registered new driver usbfs
[4294680.488000] usbcore: registered new driver hub
[4294680.492000] USB Universal Host Controller Interface driver v2.2
[4294680.493000] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 11
[4294680.493000] PCI: setting IRQ 11 as level-triggered
[4294680.493000] ACPI: PCI Interrupt 0000:00:07.2[D] -> Link [LNKD] -> GSI 11 (l evel, low) -> IRQ 11
[4294680.494000] uhci_hcd 0000:00:07.2: Intel Corporation 82371AB/EB/MB PIIX4 US B
[4294680.556000] uhci_hcd 0000:00:07.2: new USB bus registered, assigned bus num ber 1
[4294680.556000] uhci_hcd 0000:00:07.2: irq 11, io base 0x00001c20
[4294680.556000] hub 1-0:1.0: USB hub found
[4294680.556000] hub 1-0:1.0: 2 ports detected
[4294683.406000] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[4294683.406000] ACPI: Processor [CPU] (supports 8 throttling states)
[4294683.411000] ACPI: Thermal Zone [THM0] (24 C)
[4294683.643000] Attempting manual resume
[4294683.643000] swsusp: Suspend partition has wrong signature?
[4294683.677000] kjournald starting.  Commit interval 5 seconds
[4294683.677000] EXT3-fs: mounted filesystem with ordered data mode.
[4294685.352000] md: md driver 0.90.1 MAX_MD_DEVS=256, MD_SB_DISKS=27
[4294690.898000] Adding 746980k swap on /dev/hda5.  Priority:-1 extents:1
[4294691.240000] EXT3 FS on hda1, internal journal
[4294702.276000] parport: PnPBIOS parport detected.
[4294702.276000] parport0: PC-style at 0x3bc, irq 7 [PCSPP,TRISTATE]
[4294702.372000] lp0: using parport0 (interrupt-driven).
[4294702.445000] mice: PS/2 mouse device common for all mice
[4294703.464000] input: PS/2 Generic Mouse on isa0060/serio1
[4294704.075000] ts: Compaq touchscreen protocol output
[4294707.280000] device-mapper: 4.4.0-ioctl (2005-01-12) initialised: dm-devel@r edhat.com
[4294708.553000] cdrom: open failed.
[4294712.228000] Linux agpgart interface v0.101 (c) Dave Jones
[4294712.247000] agpgart: Detected an Intel 440BX Chipset.
[4294712.294000] agpgart: AGP aperture is 64M @ 0xf8000000
[4294712.528000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[4294712.546000] shpchp: acpi_shpchprm:\_SB_.PCI0 evaluate _BBN fail=0x5
[4294712.546000] shpchp: acpi_shpchprm:get_device PCI ROOT HID fail=0x5
[4294712.792000] Linux Kernel Card Services
[4294712.792000]   options:  [pci] [cardbus] [pm]
[4294712.832000] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 11
[4294712.832000] ACPI: PCI Interrupt 0000:00:02.0[A] -> Link [LNKA] -> GSI 11 (l evel, low) -> IRQ 11
[4294712.832000] Yenta: CardBus bridge found at 0000:00:02.0 [1014:0130]
[4294712.833000] Yenta: Using INTVAL to route CSC interrupts to PCI
[4294712.833000] Yenta: Routing CardBus interrupts to PCI
[4294712.833000] Yenta TI: socket 0000:00:02.0, mfunc 0x00001000, devctl 0x66
[4294713.054000] Yenta: ISA IRQ mask 0x0438, PCI irq 11
[4294713.054000] Socket status: 30000010
[4294713.098000] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 11
[4294713.098000] ACPI: PCI Interrupt 0000:00:02.1[B] -> Link [LNKB] -> GSI 11 (l evel, low) -> IRQ 11
[4294713.098000] Yenta: CardBus bridge found at 0000:00:02.1 [1014:0130]
[4294713.098000] Yenta: Using INTVAL to route CSC interrupts to PCI
[4294713.098000] Yenta: Routing CardBus interrupts to PCI
[4294713.098000] Yenta TI: socket 0000:00:02.1, mfunc 0x00001000, devctl 0x66
[4294713.319000] Yenta: ISA IRQ mask 0x0438, PCI irq 11
[4294713.319000] Socket status: 30000006
[4294714.167000] ACPI: PCI Interrupt 0000:00:05.0[A] -> Link [LNKA] -> GSI 11 (l evel, low) -> IRQ 11
[4294714.740000] gameport: CS46xx Gameport is pci0000:00:05.0/gameport0, speed 1 807kHz
[4294716.207000] piix4_smbus 0000:00:07.3: Found 0000:00:07.3 device
[4294716.207000] piix4_smbus 0000:00:07.3: IBM Laptop detected; this module may corrupt your serial eeprom! Refusing to load module!
[4294716.207000] piix4_smbus: probe of 0000:00:07.3 failed with error -1
[4294717.832000] input: PC Speaker
[4294718.204000] Real Time Clock Driver v1.12
[4294718.667000] Floppy drive(s): fd0 is 1.44M
[4294718.681000] FDC 0 is a National Semiconductor PC87306
[4294719.125000] irda_init()
[4294719.125000] NET: Registered protocol family 23
[4294724.894000] ACPI: AC Adapter [AC] (on-line)
[4294725.134000] ACPI: Battery Slot [BAT0] (battery present)
[4294725.191000] ACPI: Power Button (FF) [PWRF]
[4294725.191000] ACPI: Lid Switch [LID]
[4294725.191000] ACPI: Sleep Button (CM) [SLPB]
[4294725.487000] ibm_acpi: IBM ThinkPad ACPI Extras v0.8
[4294725.487000] ibm_acpi: [http://ibm-acpi.sf.net/](http://ibm-acpi.sf.net/)
[4294725.487000] ibm_acpi: dock device not present
[4294725.907000] ACPI: Video Device [VID] (multi-head: yes  rom: no  post: no)
[4294729.565000] capifs: Rev 1.1.2.3
[4294740.815000] IBM machine detected. Enabling interrupts during APM calls.
[4294740.815000] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[4294740.815000] apm: overridden by ACPI.
[4294742.649000] cs: IO port probe 0x100-0x4ff: excluding 0x4d0-0x4d7
[4294742.650000] cs: IO port probe 0x100-0x4ff: excluding 0x4d0-0x4d7
[4294742.652000] cs: IO port probe 0xc00-0xcf7: clean.
[4294742.652000] cs: IO port probe 0xc00-0xcf7: clean.
[4294742.653000] cs: IO port probe 0xa00-0xaff: clean.
[4294742.653000] cs: IO port probe 0xa00-0xaff: clean.
[4294742.655000] cs: memory probe 0xa0000000-0xa0ffffff: clean.
[4294743.645000] orinoco 0.14alpha2 (David Gibson <hermes@gibson.dropbear.id.au> , Pavel Roskin <proski@gnu.org>, et al)
[4294743.654000] orinoco_cs 0.14alpha2 (David Gibson <hermes@gibson.dropbear.id. au>, Pavel Roskin <proski@gnu.org>, et al)
[4294743.816000] eth0: Hardware identity 8008:0001:0001:0000
[4294743.816000] eth0: Station identity  001f:0004:0001:0003
[4294743.816000] eth0: Firmware determined as Intersil 1.3.4
[4294743.816000] eth0: Ad-hoc demo mode supported
[4294743.816000] eth0: IEEE standard IBSS ad-hoc mode supported
[4294743.816000] eth0: WEP supported, 104-bit key
[4294743.816000] eth0: MAC address 00:05:5D:A7:2B:C2
[4294743.816000] eth0: Station name "Prism  I"
[4294743.817000] eth0: ready
[4294743.824000] eth0: index 0x01: Vcc 3.3, irq 3, io 0x0100-0x013f
[4294745.418000] NET: Registered protocol family 10
[4294745.418000] Disabled Privacy Extensions on device c02eb280(lo)
[4294745.419000] IPv6 over IPv4 tunneling driver
[4294745.783000] Bluetooth: Core ver 2.7
[4294745.783000] NET: Registered protocol family 31
[4294745.783000] Bluetooth: HCI device and connection manager initialized
[4294745.783000] Bluetooth: HCI socket layer initialized
[4294745.834000] Bluetooth: L2CAP ver 2.7
[4294745.834000] Bluetooth: L2CAP socket layer initialized
[4294745.880000] Bluetooth: RFCOMM ver 1.5
[4294745.881000] Bluetooth: RFCOMM socket layer initialized
[4294745.881000] Bluetooth: RFCOMM TTY layer initialized
[4294755.522000] eth0: no IPv6 routers present
[4294868.300000] orinoco 0.14alpha2 (David Gibson <hermes@gibson.dropbear.id.au> , Pavel Roskin <proski@gnu.org>, et al)
[4294868.317000] orinoco_cs 0.14alpha2 (David Gibson <hermes@gibson.dropbear.id. au>, Pavel Roskin <proski@gnu.org>, et al)
[4294868.475000] eth0: Hardware identity 8008:0001:0001:0000
[4294868.476000] eth0: Station identity  001f:0004:0001:0003
[4294868.476000] eth0: Firmware determined as Intersil 1.3.4
[4294868.476000] eth0: Ad-hoc demo mode supported
[4294868.476000] eth0: IEEE standard IBSS ad-hoc mode supported
[4294868.476000] eth0: WEP supported, 104-bit key
[4294868.476000] eth0: MAC address 00:05:5D:A7:2B:C2
[4294868.476000] eth0: Station name "Prism  I"
[4294868.476000] eth0: ready
[4294868.487000] eth0: index 0x01: Vcc 3.3, irq 3, io 0x0100-0x013f
_____________________________________________________________

As a side note I'm surprised the cpu is being read as 700mhz, it's 900mhz. It has a feature where it uses less power and runs at a slower speed when the laptop is on battery, but it's plugged in now. Maybe I'll worry about that later. edit: The laptop wasn't plugged in when I started booting it, but rebooting with the cord plugged in gives 900mhz. So I guess processor speed won't change on the fly. Also, thanks for the help so far.

---

### Post by jcaceres on 2006-02-15
IA,
at home i connect with this script shell :

[B]iwconfig wlan0 essid Wireless.JCY
iwconfig wlan0 key s:<Password>
dhclient wlan0[/B]

where wlan0 is my interface to wireless net.

---

### Post by Lambert on 2006-02-15
jcaceres is mentioning how to configure the interface from the command line. OPen up a terminal and try what he is saying

sudo ifconfig eth0 down
sudo ifconfig etho up
sudo iwconfig etho essid _____
sudo iwconfig etho ap ___________ (put ap mac address here xx:xx:xx:..)
sudo dhclient eth0

the run iwconfig and see if all the 4s went away. It should show your ap mac address. You should also be able to surf at this point.

---

### Post by ia_ on 2006-02-15
Where I said "I typed in the access point and ip manually when I first plugged in the card", I should have said I typed in the ESSID and ip manually, not the ap. 

Configuring from the command line goes smoothly until:

@ia:~$ sudo iwconfig eth0 ap 00:12:17:6A:DE:10
Error for wireless request "Set AP Address" (8B14) :
    SET failed on device eth0 ; Operation not supported.

---

### Post by ia_ on 2006-02-17
Trying those commands I get the error message "SET failed on device eth0 ; Operation not permitted."

Any ideas? Am I doing something wrong?

---

### Post by ia_ on 2006-02-18
When I sudo lshw -C network, I get two distinct results. 

@ia:~$ sudo lshw -C network
*-network
        description: Link DWL-650 11Mbps WLAN Card
        product: Version 01.02
        vendor: D
        physical id: 0
        slot: Socket 0
*-network
        description: Wireless interface
        physical id: 1
        logical name: eth0
        serial: 00:05:5d:a7:2b:c2
        capabilities: ethernet physical wireless
        configuration: broadcast=yes ip=192.168.0.6 multicast=yes wireless=IEEE 802.11-DS

One of these has the name of my card, and was recognized by itself. It has a 'physical id: 0', whatever that is, and it has no logical name listed as being associated with it. 
The second, I don't know what it is. It has the IP I setup in Networking associated with it, it has 'physical id: 1', logical name: eth0, and a serial number I never typed in.

Are these the same device? If so, why do they have seperate 'physical id' numbers, and why doesn't the first one have a logical name? Neither of them have ndiswrapper drivers associated with them.

---

### Post by ia_ on 2006-03-05
Thanks for abandoning my thread..

I was able to get everything working properly in debian. The end.

---

### Post by shafi on 2007-03-10
Dear all, I have problem using my modem, i have a Toshiba laptop but the modem is not working, i am using Ubuntu Edgy Eft Gnom,i tried to connect it using **wvdial** but i couldn't, i dont know what's wrong
my modem is   AC97 Data Fax SoftModem
when i try
 wvdial
i get these errores:
 -->WvDial: Internet dialer version 1.56
 -->cannot open /dev/ttyS1: input/output error
 -->cannot open /dev/ttyS1: input/output error
 -->cannot open /dev/ttyS1: input/output error

I also tried /dev/ttyS0, /dev/ttyS2 and S3 and also /dev/Modem

i also could not solve it using scanModem
please help me what to do, thanks alot:confused:

---

