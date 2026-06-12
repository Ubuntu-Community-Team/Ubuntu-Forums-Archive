---
title: "What is the command that pulls up all of your system information?"
date: 2012-10-04
forum: Mythbuntu
---

### Post by RTIInstaller on 2012-10-04
Please!

---

### Post by Bashing-om on 2012-10-04
RTIInstaller; Hi !

I do not know of any one command that "[B]that pulls up all of your system information?"
[/B]A lot depends on the info you are seeking.
Here is a few for hardware and processes:
```
sudo dmidecode
sudo lspci
lsusb
lshal
lshw
------------------
fdisk -lu
df -h
du -h <dir>
top
uname -a
lsb_release -a
```And probably a thousand more ....is there something specific you have in mind ?
[INDENT]warm regards <==BDQ

[/INDENT]

---

### Post by RTIInstaller on 2012-10-04
> **Bashing-om said:**
> RTIInstaller; Hi !

I do not know of any one command that "[B]that pulls up all of your system information?"
[/B]A lot depends on the info you are seeking.
Here is a few for hardware and processes:
```
sudo dmidecode
sudo lspci
lsusb
lshal
lshw
------------------
fdisk -lu
df -h
du -h <dir>
top
uname -a
lsb_release -a
```And probably a thousand more ....is there something specific you have in mind ?[INDENT]warm regards <==BDQ

[/INDENT] 

Thank you thank, I am at my wits end with this install and I am running out of time as I only have a day left to get this functional before I have to leave town.

 Can not connect to port 6543?   I get this over and over I’m stumped. I have re-installed several times. Back end / front end machine. have a pre-exisiting raid full of movies that I want to migrate to mythbuntu but for the life of me I don't know what I am doing wrong. I just get the upnp error and the cannot connect to 6543.

   
  ```
Starting mythfrontend.real..
  2012-10-03 17:03:24.114 mythfrontend version: fixes/0.24 [v0.24.1-80-g1de0431] [www.mythtv.org]("http://www.mythtv.org")
  2012-10-03 17:03:24.114 Using runtime prefix = /usr
  2012-10-03 17:03:24.114 Using configuration directory = /home/aaron/.mythtv
  2012-10-03 17:03:24.179 ThreadPool:HTTP: Initial 1, Max 25, Timeout 60000
  2012-10-03 17:03:25.317 Empty LocalHostName.
  2012-10-03 17:03:25.318 Using localhost value of backend
  2012-10-03 17:03:25.464 New DB connection, total: 1
  2012-10-03 17:03:25.480 Connected to database 'mythconverg' at host: localhost
  2012-10-03 17:03:25.508 Closing DB connection named 'DBManager0'
  2012-10-03 17:03:25.509 Connected to database 'mythconverg' at host: localhost
  2012-10-03 17:03:25.649 Current locale EN_US
  2012-10-03 17:03:25.650 Reading locale defaults from /usr/share/mythtv//locales/en_us.xml
  2012-10-03 17:03:27.695 ScreenSaverX11Private: XScreenSaver support enabled
  2012-10-03 17:03:27.697 DPMS is disabled.
  2012-10-03 17:03:29.070 Desktop video mode: 1600x900 60.000 Hz
  2012-10-03 17:03:29.791 Enabled verbose msgs:  important general
  2012-10-03 17:03:29.958 Loading en_us translation for module mythfrontend
  2012-10-03 17:03:30.439 LIRC, Error: Failed to connect to Unix socket '/dev/lircd'
                          eno: No such file or directory (2)
  /var/log/mythtv/mythfrontend.log
   
  apt-cache policy mythtv-common
  mythtv-common:
    Installed: 2:0.24.0+fixes.20110908.1de0431-0ubuntu1
    Candidate: 2:0.24.0+fixes.20110908.1de0431-0ubuntu1
    Version table:
   *** 2:0.24.0+fixes.20110908.1de0431-0ubuntu1 0
          500 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric/multiverse i386 Packages
          100 /var/lib/dpkg/status
   
```
  ```
H/W path               Device      Class       Description
  ==========================================================
                                     system      Desktop Computer
  /0                                 bus         MS-7267
  /0/0                               memory      64KiB BIOS
  /0/4                               processor   Intel(R) Core(TM)2 Duo CPU     E4
  /0/4/5                             memory      64KiB L1 cache
  /0/4/6                             memory      2MiB L2 cache
  /0/4/0.1                           processor   Logical CPU
  /0/4/0.2                           processor   Logical CPU
  /0/f                               memory      1GiB System Memory
  /0/f/0                             memory      512MiB DIMM SDRAM Synchronous
  /0/f/1                             memory      DIMM [empty]
  /0/f/2                             memory      512MiB DIMM SDRAM Synchronous
  /0/f/3                             memory      DIMM [empty]
  /0/1                               processor   
  /0/1/0.1                           processor   Logical CPU
  /0/1/0.2                           processor   Logical CPU
  /0/100                             bridge      82945G/GZ/P/PL Memory Controller 
  /0/100/2                           display     82945G/GZ Integrated Graphics Con
  /0/100/1b                          multimedia  N10/ICH 7 Family High Definition 
  /0/100/1c                          bridge      N10/ICH 7 Family PCI Express Port
  /0/100/1d                          bus         N10/ICH 7 Family USB UHCI Control
  /0/100/1d.1                        bus         N10/ICH 7 Family USB UHCI Control
  /0/100/1d.2                        bus         N10/ICH 7 Family USB UHCI Control
  /0/100/1d.3                        bus         N10/ICH 7 Family USB UHCI Control
  /0/100/1d.7                        bus         N10/ICH 7 Family USB2 EHCI Contro
  /0/100/1e                          bridge      82801 PCI Bridge [8086:244E]
  /0/100/1e/2            scsi4       storage     9xxx-series SATA-RAID [13C1:1002]
  /0/100/1e/2/0.0.0      /dev/sdb    disk        4499GB 9500S-8    DISK
  /0/100/1e/2/0.0.0/1    /dev/sdb1   volume      4190GiB Data partition
  /0/100/1e/4            eth0        network     RTL-8110SC/8169SC Gigabit Etherne
  /0/100/1f                          bridge      82801GB/GR (ICH7 Family) LPC Inte
  /0/100/1f.1            scsi0       storage     82801G (ICH7 Family) IDE Controll
  /0/100/1f.1/0.1.0      /dev/cdrom  disk        DVD D  DH16D2P
  /0/100/1f.2            scsi3       storage     N10/ICH7 Family SATA IDE Controll
  /0/100/1f.2/0.0.0      /dev/sda    disk        1500GB ST31500341AS
  /0/100/1f.2/0.0.0/1    /dev/sda1   volume      1396GiB EXT4 volume
  /0/100/1f.2/0.0.0/2    /dev/sda2   volume      1014MiB Extended partition
  /0/100/1f.2/0.0.0/2/5  /dev/sda5   volume      1014MiB Linux swap / Solaris part
  /0/100/1f.3                        bus         N10/ICH 7 Family SMBus Controller
   
  sudo blkid -c /dev/null -o list
  device     fs_type label    mount point    UUID
  -------------------------------------------------------------------------------
  /dev/sda1  ext4             /              d80b81b8-3030-46e4-b2e7-b70e802f5281
  /dev/sda5  swap             <swap>         53036505-44bb-4009-b519-bffe4324d5ff
  /dev/sdb1  ext2             (not mounted)  3d6c407c-1527-4fcf-866f-50384add4c01
   
  # dmidecode 2.9
  SMBIOS 2.3 present.
  27 structures occupying 1346 bytes.
  Table at 0x000FCEB0.
   
  Handle 0x0000, DMI type 0, 24 bytes
  BIOS Information
          Vendor: American Megatrends Inc.
          Version: 080013 
          Release Date: 09/21/2006
          Address: 0xF0000
          Runtime Size: 64 kB
          ROM Size: 512 kB
          Characteristics:
                  ISA is supported
                  PCI is supported
                  PNP is supported
                  APM is supported
                  BIOS is upgradeable
                  BIOS shadowing is allowed
                  ESCD support is available
                  Boot from CD is supported
                  Selectable boot is supported
                  BIOS ROM is socketed
                  EDD is supported
                  5.25"/1.2 MB floppy services are supported (int 13h)
                  3.5"/720 KB floppy services are supported (int 13h)
                  3.5"/2.88 MB floppy services are supported (int 13h)
                  Print screen service is supported (int 5h)
                  8042 keyboard services are supported (int 9h)
                  Serial services are supported (int 14h)
                  Printer services are supported (int 17h)
                  CGA/mono video services are supported (int 10h)
                  ACPI is supported
                  USB legacy is supported
                  LS-120 boot is supported
                  ATAPI Zip drive boot is supported
                  BIOS boot specification is supported
          BIOS Revision: 8.13
   
  Handle 0x0001, DMI type 1, 27 bytes
  System Information
          Manufacturer: MSI
          Product Name: MS-7267
          Version: 3.0
          Serial Number: To Be Filled By O.E.M.
          UUID: 00020003-0004-0005-0006-000700080009
          Wake-up Type: Power Switch
          SKU Number: To Be Filled By O.E.M.
          Family: To Be Filled By O.E.M.
   
  Handle 0x0002, DMI type 2, 15 bytes
  Base Board Information
          Manufacturer: MSI
          Product Name: MS-7267
          Version: 3.0
          Serial Number: To be filled by O.E.M.
          Asset Tag: To Be Filled By O.E.M.
          Features:
                  Board is a hosting board
                  Board is replaceable
          Location In Chassis: To Be Filled By O.E.M.
          Chassis Handle: 0x0003
          Type: Motherboard
          Contained Object Handles: 0
   
  Handle 0x0003, DMI type 3, 21 bytes
  Chassis Information
          Manufacturer: To Be Filled By O.E.M.
          Type: Desktop
          Lock: Not Present
          Version: To Be Filled By O.E.M.
          Serial Number: To Be Filled By O.E.M.
          Asset Tag: To Be Filled By O.E.M.
          Boot-up State: Safe
          Power Supply  State: Safe
          Thermal State: Safe
          Security Status: None
          OEM Information: 0x00000000
          Height: Unspecified
          Number Of Power Cords: 1
          Contained Elements: 0
   
  Handle 0x0004, DMI type 4, 35 bytes
  Processor Information
          Socket Designation: CPU 1
          Type: Central Processor
          Family: <OUT OF SPEC>
          Manufacturer: Intel            
          ID: FD 06 00 00 FF FB EB BF
          Version: Intel(R) Core(TM)2 Duo CPU     E4500  @ 2.20GHz     
          Voltage: 1.2 V
          External Clock: 200 MHz
          Max Speed: 2200 MHz
          Current Speed: 1466 MHz
          Status: Populated, Enabled
          Upgrade: Other
          L1 Cache Handle: 0x0005
          L2 Cache Handle: 0x0006
          L3 Cache Handle: 0x0007
          Serial Number: To Be Filled By O.E.M.
          Asset Tag: To Be Filled By O.E.M.
          Part Number: To Be Filled By O.E.M.
   
  Handle 0x0005, DMI type 7, 19 bytes
  Cache Information
          Socket Designation: L1-Cache
          Configuration: Enabled, Not Socketed, Level 1
          Operational Mode: Write Back
          Location: Internal
          Installed Size: 64 KB
          Maximum Size: 64 KB
          Supported SRAM Types:
                  Other
          Installed SRAM Type: Other
          Speed: Unknown
          Error Correction Type: Parity
          System Type: Data
          Associativity: 8-way Set-associative
   
  Handle 0x0006, DMI type 7, 19 bytes
  Cache Information
          Socket Designation: L2-Cache
          Configuration: Enabled, Not Socketed, Level 2
          Operational Mode: Write Back
          Location: Internal
          Installed Size: 2048 KB
          Maximum Size: 2048 KB
          Supported SRAM Types:
                  Other
          Installed SRAM Type: Other
          Speed: Unknown
          Error Correction Type: Single-bit ECC
          System Type: Instruction
          Associativity: 8-way Set-associative
   
  Handle 0x0007, DMI type 7, 19 bytes
  Cache Information
          Socket Designation: L3-Cache
          Configuration: Disabled, Not Socketed, Level 3
          Operational Mode: Unknown
          Location: Internal
          Installed Size: 0 KB
          Maximum Size: 0 KB
          Supported SRAM Types:
                  Unknown
          Installed SRAM Type: Unknown
          Speed: Unknown
          Error Correction Type: Unknown
          System Type: Unknown
          Associativity: Unknown
   
  Handle 0x0008, DMI type 5, 24 bytes
  Memory Controller Information
          Error Detecting Method: 64-bit ECC
          Error Correcting Capabilities:
                  None
          Supported Interleave: One-way Interleave
          Current Interleave: One-way Interleave
          Maximum Memory Module Size: 4096 MB
          Maximum Total Memory Size: 16384 MB
          Supported Speeds:
                  Other
          Supported Memory Types:
                  DIMM
                  SDRAM
          Memory Module Voltage: 3.3 V
          Associated Memory Slots: 4
                  0x0009
                  0x000A
                  0x000B
                  0x000C
          Enabled Error Correcting Capabilities:
                  None
   
  Handle 0x0009, DMI type 6, 12 bytes
  Memory Module Information
          Socket Designation: DIMM0
          Bank Connections: 0 1
          Current Speed: Unknown
          Type: DIMM SDRAM
          Installed Size: 512 MB (Single-bank Connection)
          Enabled Size: 512 MB (Single-bank Connection)
          Error Status: OK
   
  Handle 0x000A, DMI type 6, 12 bytes
  Memory Module Information
          Socket Designation: DIMM1
          Bank Connections: 2 3
          Current Speed: Unknown
          Type: DIMM SDRAM
          Installed Size: Not Installed
          Enabled Size: Not Installed
          Error Status: OK
   
  Handle 0x000B, DMI type 6, 12 bytes
  Memory Module Information
          Socket Designation: DIMM2
          Bank Connections: 4 5
          Current Speed: Unknown
          Type: DIMM SDRAM
          Installed Size: 512 MB (Single-bank Connection)
          Enabled Size: 512 MB (Single-bank Connection)
          Error Status: OK
   
  Handle 0x000C, DMI type 6, 12 bytes
  Memory Module Information
          Socket Designation: DIMM3
          Bank Connections: 6 7
          Current Speed: Unknown
          Type: DIMM SDRAM
          Installed Size: Not Installed
          Enabled Size: Not Installed
          Error Status: OK
   
  Handle 0x000D, DMI type 13, 22 bytes
  BIOS Language Information
          Installable Languages: 1
                  en|US|iso8859-1
          Currently Installed Language: en|US|iso8859-1
   
  Handle 0x000E, DMI type 15, 55 bytes
  System Event Log
          Area Length: 1008 bytes
          Header Start Offset: 0x1810
          Header Length: 16 bytes
          Data Start Offset: 0x1820
          Access Method: General-purpose non-volatile data functions
          Access Address: 0x0002
          Status: Valid, Not Full
          Change Token: 0x00000000
          Header Format: Type 1
          Supported Log Type Descriptors: 9
          Descriptor 1: Single-bit ECC memory error
          Data Format 1: Multiple-event handle
          Descriptor 2: Multi-bit ECC memory error
          Data Format 2: Multiple-event handle
          Descriptor 3: Parity memory error
          Data Format 3: Multiple-event
          Descriptor 4: I/O channel block
          Data Format 4: Multiple-event
          Descriptor 5: POST error
          Data Format 5: POST results bitmap
          Descriptor 6: PCI parity error
          Data Format 6: Multiple-event handle
          Descriptor 7: PCI system error
          Data Format 7: Multiple-event handle
          Descriptor 8: System limit exceeded
          Data Format 8: Multiple-event system management
          Descriptor 9: OEM-specific
          Data Format 9: POST results bitmap
   
  Handle 0x000F, DMI type 16, 15 bytes
  Physical Memory Array
          Location: System Board Or Motherboard
          Use: System Memory
          Error Correction Type: None
          Maximum Capacity: 4 GB
          Error Information Handle: Not Provided
          Number Of Devices: 4
   
  Handle 0x0010, DMI type 19, 15 bytes
  Memory Array Mapped Address
          Starting Address: 0x00000000000
          Ending Address: 0x0003FFFFFFF
          Range Size: 1 GB
          Physical Array Handle: 0x000F
          Partition Width: 0
   
  Handle 0x0011, DMI type 17, 27 bytes
  Memory Device
          Array Handle: 0x000F
          Error Information Handle: Not Provided
          Total Width: 64 bits
          Data Width: 64 bits
          Size: 512 MB
          Form Factor: DIMM
          Set: None
          Locator: DIMM0
          Bank Locator: BANK0
          Type: SDRAM
          Type Detail: Synchronous
          Speed: Unknown
          Manufacturer: Manufacturer0
          Serial Number: SerNum0
          Asset Tag: AssetTagNum0
          Part Number: PartNum0
   
  Handle 0x0012, DMI type 20, 19 bytes
  Memory Device Mapped Address
          Starting Address: 0x00000000000
          Ending Address: 0x0001FFFFFFF
          Range Size: 512 MB
          Physical Device Handle: 0x0011
          Memory Array Mapped Address Handle: 0x0010
          Partition Row Position: 1
          Interleaved Data Depth: 1
   
  Handle 0x0013, DMI type 17, 27 bytes
  Memory Device
          Array Handle: 0x000F
          Error Information Handle: Not Provided
          Total Width: Unknown
          Data Width: Unknown
          Size: No Module Installed
          Form Factor: DIMM
          Set: None
          Locator: DIMM1
          Bank Locator: BANK1
          Type: Unknown
          Type Detail: Unknown
          Speed: Unknown
          Manufacturer: Manufacturer1
          Serial Number: SerNum1
          Asset Tag: AssetTagNum1
          Part Number: PartNum1
   
  Handle 0x0014, DMI type 20, 19 bytes
  Memory Device Mapped Address
          Starting Address: 0x00000000000
          Ending Address: 0x000000003FF
          Range Size: 1 kB
          Physical Device Handle: 0x0013
          Memory Array Mapped Address Handle: 0x0010
          Partition Row Position: 1
          Interleaved Data Depth: 1
   
  Handle 0x0015, DMI type 17, 27 bytes
  Memory Device
          Array Handle: 0x000F
          Error Information Handle: Not Provided
          Total Width: 64 bits
          Data Width: 64 bits
          Size: 512 MB
          Form Factor: DIMM
          Set: None
          Locator: DIMM2
          Bank Locator: BANK2
          Type: SDRAM
          Type Detail: Synchronous
          Speed: Unknown
          Manufacturer: Manufacturer2
          Serial Number: SerNum2
          Asset Tag: AssetTagNum2
          Part Number: PartNum2
   
  Handle 0x0016, DMI type 20, 19 bytes
  Memory Device Mapped Address
          Starting Address: 0x00020000000
          Ending Address: 0x0003FFFFFFF
          Range Size: 512 MB
          Physical Device Handle: 0x0015
          Memory Array Mapped Address Handle: 0x0010
          Partition Row Position: 1
          Interleaved Data Depth: 1
   
  Handle 0x0017, DMI type 17, 27 bytes
  Memory Device
          Array Handle: 0x000F
          Error Information Handle: Not Provided
          Total Width: Unknown
          Data Width: Unknown
          Size: No Module Installed
          Form Factor: DIMM
          Set: None
          Locator: DIMM3
          Bank Locator: BANK3
          Type: Unknown
          Type Detail: Unknown
          Speed: Unknown
          Manufacturer: Manufacturer3
          Serial Number: SerNum3
          Asset Tag: AssetTagNum3
          Part Number: PartNum3
   
  Handle 0x0018, DMI type 20, 19 bytes
  Memory Device Mapped Address
          Starting Address: 0x00000000000
          Ending Address: 0x000000003FF
          Range Size: 1 kB
          Physical Device Handle: 0x0017
          Memory Array Mapped Address Handle: 0x0010
          Partition Row Position: 1
          Interleaved Data Depth: 1
   
  Handle 0x0019, DMI type 32, 20 bytes
  System Boot Information
          Status: No errors detected
   
  Handle 0x001A, DMI type 127, 4 bytes
  End Of Table
   
  aaron@backend:~$
```

---

### Post by oldfred on 2012-10-05
Please use code tags. Highlight like copy & paste and click on # in edit panel and you can automatically add them.

I do not know RAID nor mythbuntu.

But to get Ubuntu to work with RAID you have to use the Alternative installer or add drivers if not directly installed into the RAID to allow you to mount the RAID.

Does Ubuntu boot? Do you add RAID drivers and enable your RAID system?

With Linux RAID & LVM 
[https://help.ubuntu.com/12.04/serverguide/advanced-installation.html](https://help.ubuntu.com/12.04/serverguide/advanced-installation.html)

---

### Post by RTIInstaller on 2012-10-05
> **oldfred said:**
> Please use code tags. Highlight like copy & paste and click on # in edit panel and you can automatically add them.

I do not know RAID nor mythbuntu.

But to get Ubuntu to work with RAID you have to use the Alternative installer or add drivers if not directly installed into the RAID to allow you to mount the RAID.

Does Ubuntu boot? Do you add RAID drivers and enable your RAID system?

With Linux RAID & LVM 
[https://help.ubuntu.com/12.04/serverguide/advanced-installation.html](https://help.ubuntu.com/12.04/serverguide/advanced-installation.html)
My raid is working But am having serious myth issues with connecting to the backend port and upnp problems

---

### Post by nickrout on 2012-10-05
> **RTIInstaller said:**
> My raid is working But am having serious myth issues with connecting to the backend port and upnp problemsPerhaps describe EXACTLY the problem you are seeing and where you se it.

---

### Post by RTIInstaller on 2012-10-05
> **nickrout said:**
> Perhaps describe EXACTLY the problem you are seeing and where you se it.

I just re-installed from scratch carfully walking through each step and now I am not getting upnp error nor the cant find port 6543 error.

as a test I copied some VOB movies and covert art files over to the appropriate myth lib folders.

I just closed the front end setup and all I have now is the dark grey desktop, its been this way for the last 15 minutes, I am kind of afraid to mess with it because I am not sure if it is doing something in the background?

---

### Post by nickrout on 2012-10-05
Does your TV have overscan? The menu bar may be off the edge of the screen.

If so, start a new thread with an exact description of your hardware (particularly graphics card), driver versions for the graphics card and so forth.

If it is overscan your TV set hopefully has the best fix, setting the TV to not overscan. That depends on the TV though.

As I say, new problem, new thread, precise description.

---

### Post by RTIInstaller on 2012-10-05
> **nickrout said:**
> Does your TV have overscan? The menu bar may be off the edge of the screen.

If so, start a new thread with an exact description of your hardware (particularly graphics card), driver versions for the graphics card and so forth.

If it is overscan your TV set hopefully has the best fix, setting the TV to not overscan. That depends on the TV though.

As I say, new problem, new thread, precise description.
Ok I will start a new thread. I am using a computer monitor for setup purposes.

Thanks

---

### Post by RTIInstaller on 2012-10-05
> **Bashing-om said:**
> RTIInstaller; Hi !

I do not know of any one command that "[B]that pulls up all of your system information?"
[/B]A lot depends on the info you are seeking.
Here is a few for hardware and processes:
```
sudo dmidecode
sudo lspci
lsusb
lshal
lshw
------------------
fdisk -lu
df -h
du -h <dir>
top
uname -a
lsb_release -a
```And probably a thousand more ....is there something specific you have in mind ?[INDENT]warm regards <==BDQ

[/INDENT]
Can you pull up myth error logs from a terminal?

---

### Post by nickrout on 2012-10-05
Yes of cot course. Look in /var/log/mythtv

---

### Post by RTIInstaller on 2012-10-05
> **nickrout said:**
> Yes of cot course. Look in /var/log/mythtv
There are application logs in there but when you click on them it just pulls up a blank terminal

---

### Post by nickrout on 2012-10-05
> **RTIInstaller said:**
> There are application logs in there but when you click on them it just pulls up a blank terminal

Try the less command

---

### Post by josephmills on 2012-10-05
besides looking at the myth error logs (suggested above) I would also log into my router or firewall or what ever and make sure that the port is open and not shut. best of luck.

---

### Post by RTIInstaller on 2012-10-05
> **josephmills said:**
> besides looking at the myth error logs (suggested above) I would also log into my router or firewall or what ever and make sure that the port is open and not shut. best of luck.

I am already port forwarding 6543 to my servers ip address 


:razz:

---

### Post by Bashing-om on 2012-10-05
No experience with mythtv...the majority of ubuntu's logs are located at:
/var/log/
```
ls -la /var/log/

```
list all files and sub-directories there.

[INDENT]hth <==BDQ

[/INDENT]

---

### Post by RTIInstaller on 2012-10-06
> **Bashing-om said:**
> No experience with mythtv...the majority of ubuntu's logs are located at:
/var/log/
```
ls -la /var/log/

```list all files and sub-directories there.
[INDENT]hth <==BDQ

[/INDENT]

Thank You! ):P

---

### Post by nickrout on 2012-10-06
> **RTIInstaller said:**
> I am already port forwarding 6543 to my servers ip address 


:razz:why? are you trying to access myth from outside your lan? don't!!!!

---

