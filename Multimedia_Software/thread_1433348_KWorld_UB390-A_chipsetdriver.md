---
title: "KWorld UB390-A chipset/driver"
date: 2010-03-18
forum: Multimedia Software
---

### Post by burdebc on 2010-03-18
I have a KWorld UB390-A USB TV Tuner and need to know what chipset it uses and if there is a driver for it.  Here is the line showing my tuner when I ran lsusb: Bus 002 Device 004: ID 1b80:e390 Afatech.  Thanks in advance for the help

---

### Post by burdebc on 2010-11-06
Here is the info from USBview:

PVR-TV UB390-A
Manufacturer: PVR-TV UB390-A
Speed: 480Mb/s (high)
USB Version:  2.00
Device Class: 00(>ifc )
Device Subclass: 00
Device Protocol: 00
Maximum Default Endpoint Size: 64
Number of Configurations: 1
Vendor Id: 1b80
Product Id: e390
Revision Number:  0.01

Config Number: 1
    Number of Interfaces: 1
    Attributes: a0
    MaxPower Needed: 500mA

    Interface Number: 0
        Name: (none)
        Alternate Number: 0
        Class: ff(vend.) 
        Sub Class: 00
        Protocol: ff
        Number of Endpoints: 3

            Endpoint Address: 81
            Direction: in
            Attribute: 1
            Type: Isoc
            Max Packet Size: 0
            Interval: 125us

            Endpoint Address: 82
            Direction: in
            Attribute: 2
            Type: Bulk
            Max Packet Size: 512
            Interval: 0ms

            Endpoint Address: 83
            Direction: in
            Attribute: 3
            Type: Int.
            Max Packet Size: 0
            Interval: 125us

    Interface Number: 0
        Name: (none)
        Alternate Number: 1
        Class: ff(vend.) 
        Sub Class: 00
        Protocol: ff
        Number of Endpoints: 3

            Endpoint Address: 81
            Direction: in
            Attribute: 1
            Type: Isoc
            Max Packet Size: 3072
            Interval: 125us

            Endpoint Address: 82
            Direction: in
            Attribute: 2
            Type: Bulk
            Max Packet Size: 512
            Interval: 0ms

            Endpoint Address: 83
            Direction: in
            Attribute: 3
            Type: Int.
            Max Packet Size: 4
            Interval: 125us

    Interface Number: 0
        Name: (none)
        Alternate Number: 2
        Class: ff(vend.) 
        Sub Class: 00
        Protocol: ff
        Number of Endpoints: 3

            Endpoint Address: 81
            Direction: in
            Attribute: 1
            Type: Isoc
            Max Packet Size: 0
            Interval: 125us

            Endpoint Address: 82
            Direction: in
            Attribute: 2
            Type: Bulk
            Max Packet Size: 512
            Interval: 0ms

            Endpoint Address: 83
            Direction: in
            Attribute: 3
            Type: Int.
            Max Packet Size: 4
            Interval: 125us

    Interface Number: 0
        Name: (none)
        Alternate Number: 3
        Class: ff(vend.) 
        Sub Class: 00
        Protocol: ff
        Number of Endpoints: 3

            Endpoint Address: 81
            Direction: in
            Attribute: 1
            Type: Isoc
            Max Packet Size: 3072
            Interval: 125us

            Endpoint Address: 82
            Direction: in
            Attribute: 2
            Type: Bulk
            Max Packet Size: 512
            Interval: 0ms

            Endpoint Address: 83
            Direction: in
            Attribute: 3
            Type: Int.
            Max Packet Size: 0
            Interval: 125us

---

### Post by burdebc on 2012-04-25
I have found out that it is an Afatech 9015.  If anybody can help me get this working in Linux I will be very grateful.  I am now running Kubuntu 12.04

---

### Post by Xenomorph on 2012-04-28
I'd like to know how to get this working under Ubuntu as well.

I've been using TV Cards in my computers since 1996 (starting with the STB TV PCI), and I have dozens of cards now. My main system has a Hauppauge WinTV-HVR-2250, and I have an HDHome Run serving my network.

For NTSC, the KWorld UB390-A USB has been the absolute **best** TV card I've ever owned (and that covers *16 years* of using TV cards). It works great under Windows with ChrisTV. Quick channel changing, perfectly stable, etc.

I'm running Ubuntu 12.04.
I found this page: [http://www.linuxtv.org/wiki/index.php/Afatech_AF9015](http://www.linuxtv.org/wiki/index.php/Afatech_AF9015), so I know there is support for the driver in the kernel.

---

