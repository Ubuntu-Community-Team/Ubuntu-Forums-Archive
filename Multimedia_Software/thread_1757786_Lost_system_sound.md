---
title: "Lost system sound"
date: 2011-05-13
forum: Multimedia Software
---

### Post by jpardi on 2011-05-13
Wondering if someone could help me.  I upgraded to 11.04 and am having a problem with sound.  I don't believe it is a hardware issue since I have a dual boot with Vista and the sound is working on that OS.

I don't have a sound card and am using what's on the motherboard, which is an Intel motherboard.

I have attached the info from the Alsa Info script.

Any help would be appreciated.

- Joe

---

### Post by lidex on 2011-05-14
I'll try, but I've not seen that codec:
```
SigmaTel STAC9274D
```
What is the make/model/motherboard of this machine?
This output would also be helpful:
```
sudo dmidecode -t bios
sudo dmidecode -t baseboard

```

---

### Post by jpardi on 2011-05-15
The motherboard is the following:

Intel BOXD975XBX2KR LGA 775 Intel 975X ATX Intel Motherboard

Below are the results from the commands ... (thanks for your help):

```
joe@jpardi-ubuntu:~$ sudo dmidecode -t bios
[sudo] password for joe: 
# dmidecode 2.9
SMBIOS 2.4 present.

Handle 0x0004, DMI type 0, 24 bytes
BIOS Information
        Vendor: Intel Corp.
        Version: BX97520J.86A.2792.2007.0905.1804
        Release Date: 09/05/2007
        Address: 0xF0000
        Runtime Size: 64 kB
        ROM Size: 1024 kB
        Characteristics:
                PCI is supported
                BIOS is upgradeable
                BIOS shadowing is allowed
                Boot from CD is supported
                Selectable boot is supported
                EDD is supported
                8042 keyboard services are supported (int 9h)
                Serial services are supported (int 14h)
                Printer services are supported (int 17h)
                CGA/mono video services are supported (int 10h)
                ACPI is supported
                USB legacy is supported
                ATAPI Zip drive boot is supported
                BIOS boot specification is supported
                Function key-initiated network boot is supported
                Targeted content distribution is supported
        BIOS Revision: 0.0
        Firmware Revision: 0.0

Handle 0x0014, DMI type 13, 22 bytes
BIOS Language Information
        Installable Languages: 1
                enUS
        Currently Installed Language: enUS

joe@jpardi-ubuntu:~$ sudo dmidecode -t baseboard
# dmidecode 2.9
SMBIOS 2.4 present.

Handle 0x0006, DMI type 2, 20 bytes
Base Board Information
        Manufacturer: Intel Corporation
        Product Name: D975XBX2
        Version: AAD53350-507                                                                                                                                  
        Serial Number: BQB273300371
        Asset Tag: Base Board Asset Tag
        Features:
                Board is a hosting board
                Board is replaceable
        Location In Chassis: Base Board Chassis Location
        Chassis Handle: 0x0007
        Type: Unknown
        Contained Object Handles: 0

Handle 0x0010, DMI type 10, 6 bytes
On Board Device Information
        Type: Ethernet
        Status: Enabled
        Description: Intel (R) 82562 Ethernet Device

Handle 0x0011, DMI type 10, 6 bytes
On Board Device Information
        Type: Sound
        Status: Enabled
        Description: Intel(R) Azalia Audio Device

Handle 0x0012, DMI type 10, 6 bytes
On Board Device Information
        Type: Other
        Status: Enabled
        Description: Marvell 6145 SATA RAID Controller

Handle 0x0013, DMI type 10, 6 bytes
On Board Device Information
        Type: Other
        Status: Enabled
        Description: Texas Instruments TSB82AA2 1394A/B Controller

joe@jpardi-ubuntu:~$
```

---

### Post by lidex on 2011-05-15
One thing I notice is your alsa libs seem not to match:
```
!!ALSA Version
!!------------

Driver version:     1.0.23
[COLOR="Red"]Library version:    1.0.20[/COLOR]
Utilities version:  1.0.24.2

```

Let's try a re-install first. 
Using a Terminal="Applications->Accessories->Terminal"
```
sudo aptitude --purge reinstall linux-sound-base alsa-base alsa-utils linux-image-`uname -r` linux-ubuntu-modules-`uname -r` libasound2
```
**Reboot.**

For a 'command not found' error simply install aptitude:
```
sudo apt-get install aptitude
```

---

### Post by jpardi on 2011-05-15
Thanks ... still no sound but it did seem to hilite something strange.  During the install, it looks like it tried to get alsa fully to 1.0.24 but the script reports otherwise.

**REINSTALL:**
```
Setting up libasound2 (1.0.24.1-0ubuntu5) ...
Setting up linux-sound-base (1.0.24+dfsg-0ubuntu1) ...
Setting up alsa-base (1.0.24+dfsg-0ubuntu1) ...
Setting up alsa-utils (1.0.24.2-0ubuntu6) ...
```


**SCRIPT RESULTS:**
```
!!ALSA Version
!!------------

Driver version:     1.0.23
Library version:    1.0.20
Utilities version:  1.0.24.2
```

Anyway, I've attached the command's results as well as what the script reports.

- Joe

---

### Post by lidex on 2011-05-15
Something strange going on. Also i see you are using the pae kernel, have you tried the default?

---

### Post by jpardi on 2011-05-18
I did as you say and switched off the pae kernel and that seemed to do the trick.  My Alsa libraries stayed as they were, but I'm happy I have sound now.

I appreciate your help (and time)!

Thanks,
Joe

---

### Post by lidex on 2011-05-19
Good stuff. Please mark the thread solved using 'Thread Tools' up top.

---

