---
title: "problem with sound and streaming"
date: 2010-09-23
forum: Multimedia Software
---

### Post by Alkser on 2010-09-23
I have 2 problems:

1st - The sound doesn't come from my speakers or headphones, but from the computer, and I have no idea how to change that.

2nd is streaming. I can't normally play files on my computer or watch videos on the internet because it goes by 2 seconds, not by default 1

How do I fix this ?

---

### Post by lkjoel on 2010-09-23
> **Alkser said:**
> I have 2 problems:

1st - The sound doesn't come from my speakers or headphones, but from the computer, and I have no idea how to change that.

2nd is streaming. I can't normally play files on my computer or watch videos on the internet because it goes by 2 seconds, not by default 1

How do I fix this ?
Have you checked that everything is plugged in right?

---

### Post by Alkser on 2010-09-24
I've fixed the second one.

First thing: When I go to sound preferences and then hardware it doesn't show me anything, it's just empty.

lkjoel: Yes, everything is plugged in right.

---

### Post by lkjoel on 2010-09-24
Try Fix your sound! in my signature.
Then use Post-Fix your sound! in my signature.

---

### Post by lidex on 2010-09-25
> **Alkser said:**
> I have 2 problems:
1st - The sound doesn't come from my speakers or headphones, but from the computer, and I have no idea how to change that.
How do I fix this ?

Is this a laptop or desktop?
Can you post the output of these terminal commands for me please:
```
uname -a
aplay -l
dpkg -l | grep "alsa"
head -n 1 /proc/asound/card*/codec#* 
```
Terminal="Applications->Accessories->Terminal"
**Please also include the make/model of your PC/Laptop.**
Please post text output using code tags (the # in toolbar)

---

### Post by Alkser on 2010-09-25
> **lidex said:**
> Is this a laptop or desktop?
Can you post the output of these terminal commands for me please:
```
uname -a
aplay -l
dpkg -l | grep "alsa"
head -n 1 /proc/asound/card*/codec#* 
```Terminal="Applications->Accessories->Terminal"
**Please also include the make/model of your PC/Laptop.**
Please post text output using code tags (the # in toolbar)

Here it is:
```
scene@ubuntu:~$ uname -a
Linux ubuntu 2.6.32-24-generic #43-Ubuntu SMP Thu Sep 16 14:17:33 UTC 2010 i686 GNU/Linux
scene@ubuntu:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC260 Analog [ALC260 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
scene@ubuntu:~$ dpkg -l | grep "alsa"
ii  alsa-base                            1.0.22.1+dfsg-0ubuntu3                          ALSA driver configuration files
ii  alsa-utils                           1.0.22-0ubuntu5                                 ALSA utilities
ii  bluez-alsa                           4.60-0ubuntu8                                   Bluetooth audio support
ii  gstreamer0.10-alsa                   0.10.28-1                                       GStreamer plugin for ALSA
ii  libsnack2-alsa                       2.2.10-dfsg1-9                                  Sound extension to Tcl/Tk and Python/Tkinter
scene@ubuntu:~$ head -n 1 /proc/asound/card*/codec#*
==> /proc/asound/card0/codec#2 <==
Codec: Realtek ALC260

==> /proc/asound/card1/codec#0 <==
Codec: ATI R6xx HDMI
scene@ubuntu:~$
```

This is desktop pc Intel Celeron D, not laptop.

---

### Post by lkjoel on 2010-09-25
> **Alkser said:**
> Here it is:
```
scene@ubuntu:~$ uname -a
Linux ubuntu 2.6.32-24-generic #43-Ubuntu SMP Thu Sep 16 14:17:33 UTC 2010 i686 GNU/Linux
scene@ubuntu:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC260 Analog [ALC260 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
scene@ubuntu:~$ dpkg -l | grep "alsa"
ii  alsa-base                            1.0.22.1+dfsg-0ubuntu3                          ALSA driver configuration files
ii  alsa-utils                           1.0.22-0ubuntu5                                 ALSA utilities
ii  bluez-alsa                           4.60-0ubuntu8                                   Bluetooth audio support
ii  gstreamer0.10-alsa                   0.10.28-1                                       GStreamer plugin for ALSA
ii  libsnack2-alsa                       2.2.10-dfsg1-9                                  Sound extension to Tcl/Tk and Python/Tkinter
scene@ubuntu:~$ head -n 1 /proc/asound/card*/codec#*
==> /proc/asound/card0/codec#2 <==
Codec: Realtek ALC260

==> /proc/asound/card1/codec#0 <==
Codec: ATI R6xx HDMI
scene@ubuntu:~$
```

This is desktop pc Intel Celeron D, not laptop.
This seems like you should do this in a Terminal window:
```
sudo apt-get purge alsa-base
sudo apt-get purge alsamixer
sudo apt-get purge alsa-utils
sudo apt-get install alsa-base
sudo apt-get install alsamixer
sudo apt-get install alsa-utils
```
Then restart.
Tell me if this works.
If it doesn't, follow my previous suggestion.

---

### Post by Alkser on 2010-09-25
When I try to install alsamixer I get this:

```
scene@ubuntu:~$ sudo apt-get install alsamixer
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package alsamixer

```

---

### Post by lkjoel on 2010-09-25
Type this in:
```
sudo apt-get update
sudo apt-get install alsamixer
sudo apt-get install alsa-utils
```

---

### Post by Alkser on 2010-09-25
Still get the same message.

---

### Post by perspectoff on 2010-09-25
gnome-alsamixer

---

### Post by Yellow Pasque on 2010-09-25
> 1st - The sound doesn't come from my speakers or headphones, but from the computer, and I have no idea how to change that.
I don't understand "from the computer" (like the PC speaker?)

---

### Post by lidex on 2010-09-25
> **Alkser said:**
> Still get the same message.

There is no alsamixer package - it's part of alsa-utils.

Post this output please:
```
sudo dmidecode -t bios
sudo dmidecode -t baseboard

```

---

### Post by Alkser on 2010-09-25
> **lidex said:**
> There is no alsamixer package - it's part of alsa-utils.

Post this output please:
```
sudo dmidecode -t bios
sudo dmidecode -t baseboard

```

Here it is:
```
scene@ubuntu:~$ sudo dmidecode -t bios
[sudo] password for scene: 
# dmidecode 2.9
SMBIOS 2.34 present.

Handle 0x0000, DMI type 0, 20 bytes
BIOS Information
    Vendor: FUJITSU SIEMENS // Phoenix Technologies Ltd.
    Version: 5.00 R1.01.2151.A1              
    Release Date: 04/26/2005
    Address: 0xE7880
    Runtime Size: 100224 bytes
    ROM Size: 512 kB
    Characteristics:
        PCI is supported
        PNP is supported
        APM is supported
        BIOS is upgradeable
        BIOS shadowing is allowed
        ESCD support is available
        Boot from CD is supported
        Selectable boot is supported
        Japanese floppy for NEC 9800 1.2 MB is supported (int 13h)
        Japanese floppy for Toshiba 1.2 MB is supported (int 13h)
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

scene@ubuntu:~$ sudo dmidecode -t baseboard
# dmidecode 2.9
SMBIOS 2.34 present.

Handle 0x0002, DMI type 2, 8 bytes
Base Board Information
    Manufacturer: FUJITSU SIEMENS
    Product Name: D2151-A1
    Version: S26361-D2151-A1
    Serial Number: B009C7A0

Handle 0x001D, DMI type 10, 14 bytes
On Board Device 1 Information
    Type: Other
    Status: Disabled
    Description: SMsC SuperI/O
On Board Device 2 Information
    Type: Sound
    Status: Disabled
    Description: Realtek ALC260
On Board Device 3 Information
    Type: Video
    Status: Disabled
    Description: Intel 945G
On Board Device 4 Information
    Type: Other
    Status: Disabled
    Description: Heimdall
On Board Device 5 Information
    Type: Ethernet
    Status: Disabled
    Description: BCM5751
```

---

### Post by lkjoel on 2010-09-25
> **Alkser said:**
> Still get the same message.
Download the script from Post-Fix your sound! into your homedir.
Then type this into a Terminal:
```
cd ~
chmod +x CPanel.sh
./CPanel.sh osspart1
# RESTART COMPUTER NOW
./CPanel.sh osspart2
./CPanel.sh -r
```

---

### Post by lidex on 2010-09-25
You could probably do with a bios update.

---

### Post by Alkser on 2010-09-25
> **lkjoel said:**
> Download the script from Post-Fix your sound! into your homedir.
Then type this into a Terminal:
```
cd ~
chmod +x CPanel.sh
./CPanel.sh osspart1
# RESTART COMPUTER NOW
./CPanel.sh osspart2
./CPanel.sh -r
```

I've done this and I don't have sound at all now.

---

### Post by Alkser on 2010-09-29
I still have problem with the sound.

---

### Post by lidex on 2010-09-29
> **Alkser said:**
> I still have problem with the sound.

You may want to PM *lkjoel*. I have no idea what that script did to your system.

---

### Post by Alkser on 2010-10-01
Doesn't matter anymore, I've deleted Ubuntu and installed Kubuntu.

Thanks for the help guys.

---

