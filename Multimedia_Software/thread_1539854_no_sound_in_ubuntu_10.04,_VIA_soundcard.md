---
title: "no sound in ubuntu 10.04, VIA soundcard"
date: 2010-07-27
forum: Multimedia Software
---

### Post by sundays211 on 2010-07-27
hi
i have no sound on my computer. my sound information is listed below
```
sundays211@linux-desktop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: V8237 [VIA 8237], device 0: VIA 8237 [VIA 8237]
  Subdevices: 4/4
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
card 0: V8237 [VIA 8237], device 1: VIA 8237 [VIA 8237]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```the sound has worked on previous versions of ubuntu (5.04 definitely, yes I upgraded all the way from there, but this is a fresh install), but no longer work in 10.04.

---

### Post by sundays211 on 2010-07-31
problem is still there

---

### Post by cchhrriiss121212 on 2010-07-31
Have you checked your levels using alsamixer?

---

### Post by lidex on 2010-08-01
Need more info. Right-click the alsa-info script link in my sig and "save as" to your user folder. Then run this command in a terminal:
```
sudo bash utils_alsa-info.sh
```
Enter your user password when prompted. Choose the upload option and provide a link for the output.

Do you have the same /home from 5.04?

---

### Post by sundays211 on 2010-08-02
nope, as i said i have re-installed as i have had so many problems (complete fresh install) i still have a copy of my old home folder if i need it.

I'm afraid that your command did not work. you did mean my home folder, right?

edit: the name of the file was wrong in the command you gave me. I had to use
```
sudo bash "Alsa Info Script.htm"
```the output file is in: [http://www.alsa-project.org/db/?f=3a6524df717cd9c85a80a123b4942c865961f3ac](http://www.alsa-project.org/db/?f=3a6524df717cd9c85a80a123b4942c865961f3ac)

---

### Post by lidex on 2010-08-02
Follow the alsa-upgrade link in my sig to get v. 1.0.23 and report your results.

---

### Post by sundays211 on 2010-08-03
i guess the simplest way to put it is that the sound still does not work.

---

### Post by lidex on 2010-08-05
Can you post these outputs for me please:
```
sudo dmidecode -t bios
sudo dmidecode -t baseboard

```

---

### Post by sundays211 on 2010-08-05
BIOS:
```
sundays211@linux-desktop:~$ sudo dmidecode -t bios
sudo: unable to resolve host linux-desktop
[sudo] password for sundays211: 
# dmidecode 2.9
SMBIOS 2.3 present.

Handle 0x0000, DMI type 0, 20 bytes
BIOS Information
    Vendor: American Megatrends Inc.
    Version: Version 07.00T
    Release Date: 04/02/01
    Address: 0xF0000
    Runtime Size: 64 kB
    ROM Size: 256 kB
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
        5.25"/360 KB floppy services are supported (int 13h)
        5.25"/1.2 MB floppy services are supported (int 13h)
        3.5"/720 KB floppy services are supported (int 13h)
        3.5"/2.88 MB floppy services are supported (int 13h)
        Print screen service is supported (int 5h)
        8042 keyboard services are supported (int 9h)
        Printer services are supported (int 17h)
        CGA/mono video services are supported (int 10h)
        ACPI is supported
        USB legacy is supported
        AGP is supported
        LS-120 boot is supported
        ATAPI Zip drive boot is supported
        BIOS boot specification is supported

Handle 0x000F, DMI type 13, 22 bytes
BIOS Language Information
    Installable Languages: 4
        English
        Traditional Chinese
        Simplified Chinese
        Japanese
    Currently Installed Language: English

```
MOTHERBOARD:
```
sundays211@linux-desktop:~$ sudo dmidecode -t baseboard
sudo: unable to resolve host linux-desktop
# dmidecode 2.9
SMBIOS 2.3 present.

Handle 0x0002, DMI type 2, 8 bytes
Base Board Information
    Manufacturer: KOBIAN
    Product Name: KVM266PM
    Version: 1.0
    Serial Number: 00000000


```

---

