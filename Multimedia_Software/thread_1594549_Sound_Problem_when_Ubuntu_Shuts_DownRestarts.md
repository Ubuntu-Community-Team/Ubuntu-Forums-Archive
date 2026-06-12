---
title: "Sound Problem when Ubuntu Shuts Down/Restarts"
date: 2010-10-12
forum: Multimedia Software
---

### Post by C09JayLT on 2010-10-12
Good morning,

I have an interesting problem that I hope you can help me with. Whenever I shut down/restart Ubuntu (10.04) and boot back into Ubuntu my sound does not work in Ubuntu. If I boot into Windows 7 then restart and boot into Ubuntu, my sound works.  I have reinstalled pulse and alsa several times for a separate sound problem that I solved, so I do not think the issue lies with them. 

Extra info:
Using a soundblaster card (ca0106 driver)
aplay -l lists the card
lspci lists the card

Thanks in advance for any/all help

:guitar:

---

### Post by C09JayLT on 2010-10-14
Some additional information: I figure this is a problem somewhere in the shutdown sequence, so it would at the worst it'd not help to update to 10.10. I did and there was no effect. Ubuntu still won't play sound unless I boot into Windows and reboot into Ubuntu.

---

### Post by C09JayLT on 2010-10-16
Noone has any ideas?

---

### Post by lidex on 2010-10-17
> The biggest problem with audigy cards is that by default the driver selects the digital output so you need to change the analog/digital switch in the alsa mixer to get any sound.
*~markbuntu*

---

### Post by C09JayLT on 2010-10-18
lidex, just checked and Pulse says everything is set to analog. Also, the audigy card is listed as the primary over my internal audio. Thanks for giving me some feedback here.

I dunno if this bit helps, but I am now getting static until I go into gnome and turn up the volume. The sound is set to ~85% and when I turn it up I get silence rather than static.

---

### Post by lidex on 2010-10-19
> **C09JayLT said:**
> lidex, just checked and Pulse says everything is set to analog. Also, the audigy card is listed as the primary over my internal audio. Thanks for giving me some feedback here.

I dunno if this bit helps, but I am now getting static until I go into gnome and turn up the volume. The sound is set to ~85% and when I turn it up I get silence rather than static.

Open alsamixer or gnome-alsamixer to check/toggle that setting - don't think pulse will do it.

---

### Post by C09JayLT on 2010-10-19
I am not seeing a whole lot of options in Gnome ALSA Mixer. I can check the box Analog Source, but it won't stay checked. alsamixer is giving me even less info that gnome-alsamixer; I don't see anything about analog/digital on it.

Hopefully I am just missing something stupid.

---

### Post by C09JayLT on 2010-10-19
Just rebooted from Windows 7 to Ubuntu. The sound works; I attached my ALSA/Pulse settings.

---

### Post by C09JayLT on 2010-10-22
Just uninstalled and reinstalled pulse and alsa yet again, and no dice. I still get static from a Ubuntu shutdown/reboot followed by a Ubuntu boot.

---

### Post by lidex on 2010-10-23
Can you post this output please:
```
sudo dmidecode -t bios
sudo dmidecode -t baseboard

```
Also this. Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.
[Terminal="Applications->Accessories->Terminal"]

---

### Post by C09JayLT on 2010-10-23
While my sound is working (Post booting into Windows 7, then out and into Ubuntu):
```
sudo dmidecode -t bios
# dmidecode 2.9
SMBIOS 2.4 present.

Handle 0x0000, DMI type 0, 24 bytes
BIOS Information
    Vendor: Award Software International, Inc.
    Version: F5
    Release Date: 01/29/2008
    Address: 0xE0000
    Runtime Size: 128 kB
    ROM Size: 512 kB
    Characteristics:
        PCI is supported
        PNP is supported
        APM is supported
        BIOS is upgradeable
        BIOS shadowing is allowed
        Boot from CD is supported
        Selectable boot is supported
        EDD is supported
        5.25"/360 KB floppy services are supported (int 13h)
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
        Targeted content distribution is supported

Handle 0x0018, DMI type 13, 22 bytes
BIOS Language Information
    Installable Languages: 3
        n|US|iso8859-1
        n|US|iso8859-1
        r|CA|iso8859-1
    Currently Installed Language: n|US|iso8859-1

``````
sudo dmidecode -t baseboard
# dmidecode 2.9
SMBIOS 2.4 present.

Handle 0x0002, DMI type 2, 8 bytes
Base Board Information
    Manufacturer: Gigabyte Technology Co., Ltd.
    Product Name: P31-S3G
    Version: x.x
    Serial Number: 

```[http://www.alsa-project.org/db/?f=c5b0c7ead56dc2445f71c5bfe90a1f065977590b](http://www.alsa-project.org/db/?f=c5b0c7ead56dc2445f71c5bfe90a1f065977590b)

Do you want any of this while sound does not work (Ubuntu to Ubuntu boot?) as well?

---

### Post by C09JayLT on 2010-10-24
Sound currently not working:
```
sudo dmidecode -t bios
# dmidecode 2.9
SMBIOS 2.4 present.

Handle 0x0000, DMI type 0, 24 bytes
BIOS Information
    Vendor: Award Software International, Inc.
    Version: F5
    Release Date: 01/29/2008
    Address: 0xE0000
    Runtime Size: 128 kB
    ROM Size: 512 kB
    Characteristics:
        PCI is supported
        PNP is supported
        APM is supported
        BIOS is upgradeable
        BIOS shadowing is allowed
        Boot from CD is supported
        Selectable boot is supported
        EDD is supported
        5.25"/360 KB floppy services are supported (int 13h)
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
        Targeted content distribution is supported

Handle 0x0018, DMI type 13, 22 bytes
BIOS Language Information
    Installable Languages: 3
        n|US|iso8859-1
        n|US|iso8859-1
        r|CA|iso8859-1
    Currently Installed Language: n|US|iso8859-1

``````
sudo dmidecode -t baseboard
# dmidecode 2.9
SMBIOS 2.4 present.

Handle 0x0002, DMI type 2, 8 bytes
Base Board Information
    Manufacturer: Gigabyte Technology Co., Ltd.
    Product Name: P31-S3G
    Version: x.x
    Serial Number:  

```[http://www.alsa-project.org/db/?f=d380cb2d68b413f173b26308e46bfafbb2833c15](http://www.alsa-project.org/db/?f=d380cb2d68b413f173b26308e46bfafbb2833c15)

---

### Post by C09JayLT on 2010-10-24
[FONT=Verdana]The differences I can see in the uploads to alsa-project.org:

node 0x09 has a change in "Amp-In vals:  [0x9f 0x9f]" when working, but[/FONT][FONT=Verdana] "Amp-In vals:  [0x80 0x80]" when not[/FONT][FONT=Verdana]

APLAY has "Subdevices: 0/1" in 3/4 listings of my primary card when it worked and "Subdevices: 1/1" in 4/4 listings of my primary card when it is not

Volume settings are different in the alsamixer section, with 100% when working and 81% when not on primary card and many differences on secondary card

Alsaclt has different values across the board

The list of loaded modules is different[/FONT][FONT=Verdana]

ALSA/HDA dmesg has different output


I hope this helps

[/FONT]

---

### Post by C09JayLT on 2010-10-27
Re-accomplished Sound Troubleshooting Guide yet again, but still no dice. Booting into Windows 7 is the only thing that lets me have sound

---

### Post by lidex on 2010-10-27
This will probably need to be fixed in alsa. File a bug report using this method. Try running this command in a terminal for 10.04 or later:
```
ubuntu-bug audio
```
Reference the Ubuntu-Bug Audio link in my sig.

---

### Post by C09JayLT on 2010-10-28
For future reference, here is the bug report link:

[https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/668092](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/668092)

I will post the outcome.

Thanks for all your help lidex!

---

### Post by lidex on 2010-10-28
> **C09JayLT said:**
> For future reference, here is the bug report link:

[https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/668092](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/668092)

I will post the outcome.

Thanks for all your help lidex!

Nice work and thank you for your patience and for helping to make ubuntu better. I will be following this.

---

