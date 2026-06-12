---
title: "Network transfer speed issues"
date: 2010-12-29
forum: Networking &amp; Wireless
---

### Post by mikeobeda on 2010-12-29
I just installed a 1 gigabit switch in the home network in order to increase the transfer speed of video files from a windows machine to the machine running ubuntu server edition (trying my hand at setting up a media server).  The transfer speed still peaks out at 10 megabytes/second.

Initially, the light on the switch said it was connected to a 100 megabit network card on the ubuntu server, so I downloaded the tar.bz2 file from the realtek site for their 8110sc card.  I was able to decompress the bz2 file, and follow the instructions in the readme for installation, and then ran the command to force 1000 megabit mode on the card, and the switch indicated it was connected to a gigabit card.

I need the transfer speed to be faster, so that loading movies goes quicker, but also so that playing blu-ray files off the server over the network is possible.  Right now, when playing blu-ray files off the server on my windows laptop (using samba), the playback halts every few seconds for a second or two.  However, it seems to be able to play the 1080p avi big buck bunny smoothly over the network, so I just need a little more speed for it to be usable.

What I'm looking for here are some suggestions on getting the streaming to go a little faster so that streaming hi-def videos is possible.  Here are some tech specs on the ubuntu server, and note that I am currently not using a upnp serving system, and the server is not doing any transcoding:

1GB RAM, 200GB ATA hard drive, (ext4)(os drive), 2 TB SATA drive, (ext2)(data drive for videos), realtek 8110sc network card, and a 3.2 core 2 duo processor.  It is running ubuntu 10.10 server, no GUI is installed.

---

### Post by supershin on 2010-12-29
In order to get the 1 Gbps speed you need to have a 1Gbps switch and two 1 Gbps network cards. Does your windows machine have one?

---

### Post by mikeobeda on 2010-12-29
My windows laptop does have a gigabit network card, and so does the windows xp machine I will use for the primary purpose of ripping dvds and then transferring them to the ubuntu server.  When using my laptop to transfer, I turned off its wireless to be sure it was going through the gigabit card.  The 10/100/1000 switch indicates that both machines have a gigabit card.

However, the switch is connected to a router, and that connection is only 100 megabit.  The router is what's telling the ubuntu machine its ip address, but since both the ubuntu server and my windows machines are plugged in to the gigabit switch, as far as I can tell I should be getting a better transfer speed (correct me if I'm wrong)

---

### Post by mikeobeda on 2010-12-29
Here is the output of the hwinfo --short command:

obeda@ubuntuserver:~$ hwinfo --short
> hal.1: read hal dataprocess 2342: arguments to dbus_move_error() were incorrect, assertion "(dest) == NULL || !dbus_error_is_set ((dest))" failed in file dbus-errors.c line 280.
This is normally a bug in some application using the D-Bus library.
libhal.c 3483 : Error unsubscribing to signals, error=The name org.freedesktop.Hal was not provided by any .service files
cpu:
                       Intel(R) Pentium(R) 4 CPU 3.20GHz, 2800 MHz
                       Intel(R) Pentium(R) 4 CPU 3.20GHz, 2800 MHz
graphics card:
                       Intel 945G
storage:
                       Floppy disk controller
                       Intel 82801G (ICH7 Family) IDE Controller
                       Intel 82801GB/GR/GH (ICH7 Family) SATA IDE Controller
network:
  eth0                 Realtek RTL-8110SC/8169SC Gigabit Ethernet
network interface:
  lo                   Loopback network interface
  eth0                 Ethernet network interface
disk:
  /dev/sda             ST3200826A
  /dev/sdb             SAMSUNG SP1213C
  /dev/sdc             WDC WD20EARS-00J
partition:
  /dev/sda1            Partition
  /dev/sda2            Partition
  /dev/sda5            Partition
  /dev/sdb1            Partition
  /dev/sdc1            Partition
cdrom:
  /dev/sr0             HL-DT-ST DVD-RAM GSA-H54N
usb controller:
                       Intel 82801G (ICH7 Family) USB UHCI Controller #1
                       Intel 82801G (ICH7 Family) USB UHCI Controller #2
                       Intel 82801G (ICH7 Family) USB UHCI Controller #3
                       Intel 82801G (ICH7 Family) USB UHCI Controller #4
                       Intel 82801G (ICH7 Family) USB2 EHCI Controller
bios:
                       BIOS
bridge:
                       Intel 82945G/GZ/P/PL Memory Controller Hub
                       Intel 82801 PCI Bridge
                       Intel 82801GB/GR (ICH7 Family) LPC Interface Bridge
hub:
                       Linux 2.6.35-24-server ehci_hcd EHCI Host Controller
                       Linux 2.6.35-24-server uhci_hcd UHCI Host Controller
                       Linux 2.6.35-24-server uhci_hcd UHCI Host Controller
                       Linux 2.6.35-24-server uhci_hcd UHCI Host Controller
                       Linux 2.6.35-24-server uhci_hcd UHCI Host Controller
memory:
                       Main Memory
unknown:
                       FPU
                       DMA controller
                       PIC
                       Timer
                       Keyboard controller
  /dev/lp0             Parallel controller
                       Intel 82801G (ICH7 Family) SMBus Controller
                       Serial controller

---

### Post by supershin on 2010-12-30
Since your router is only 100Mbit then somehow the laptop is transferring files to the xp machine via the router, hence the slowdown. 

Running a tracert should show the router ip address somewhere, that is causing your slow speeds. 

Where does your XP machine gets its ip address? If from the switch then you should set the laptop to get it from the switch as well. That way it shouldn't go through the router. Anything passing through the router can only pass through at 100MBit. Think the greatest speed you can get is only as fast as the weakest link, ie, the slowest speed. 

So you should have it connected like this.

laptop   XP
"    \   /    "
   switch
     |
   router

---

### Post by mikeobeda on 2010-12-30
I think I wasn't the clearest when describing my setup.  I have 3 machines.  One running ubuntu server, it is a desktop machine.  I have an XP desktop as well, and a windows 7 laptop.  The xp desktop and the ubuntu server are both connected to the switch.  When I use the laptop to do the transfers, I unplug the ethernet cable from my xp desktop and plug it in to my laptop.

I tried typing in the tracert command, and the tracer command, and those commands don't seem to exist, and it suggested i install pvm, so I did, and it still had trouble.  Running a sudo ethtool eth0 gives me this output however:


obeda@ubuntuserver:~$ sudo ethtool eth0
Settings for eth0:
        Supported ports: [ TP MII ]
        Supported link modes:   10baseT/Half 10baseT/Full
                                100baseT/Half 100baseT/Full
                                1000baseT/Half 1000baseT/Full
        Supports auto-negotiation: Yes
        Advertised link modes:  10baseT/Half 10baseT/Full
                                100baseT/Half 100baseT/Full
                                1000baseT/Half 1000baseT/Full
        Advertised pause frame use: No
        Advertised auto-negotiation: Yes
        Link partner advertised link modes:  10baseT/Half 10baseT/Full
                                             100baseT/Half 100baseT/Full
        Link partner advertised pause frame use: No
        Link partner advertised auto-negotiation: Yes
        Speed: 100Mb/s
        Duplex: Full
        Port: MII
        PHYAD: 0
        Transceiver: internal
        Auto-negotiation: on
        Supports Wake-on: pumbg
        Wake-on: g
        Current message level: 0x00000033 (51)
        Link detected: yes

It says that the link partner is 100 megabit.  Would the link partner be my router?  The ubuntu server does get its ip address from the router, but if there is a switch between it and the router, and the switch is also between the xp machine and the router, shouldn't the switch just direct the traffic so it's directly between the two machines through the gigabit switch, and bypass the router?

---

### Post by mikeobeda on 2010-12-30
Here is a schematic of how part of my network looks like.  The switch is gigabit, and the router is 100 megabit.  The fastest route should be from ubuntuserver to switch to xpmachine.  How can I see what path the files are taking?  I know the ip addresses of the ubuntu server and the xp machine.


                        router
                           |
                        switch
                      /          \
           ubuntuserver    xpmachine

---

### Post by supershin on 2010-12-31
Well your diagram is just the reverse of mine so that doesn't change anything. 

The ethtool has speed as 100Mb/s. Does your laptop/XP machine have auto-negotiation, full duplex on? 

More importantly, the switch is not the one giving out ip addresses. Your setup should be the switch uses it DCHP server to give out ip address to computers and the default gateway for the computers is the switch and the switch forwards that to the router. 

> How can I see what path the files are taking? I know the ip addresses of the ubuntu server and the xp machine.
By running the tracert command i told you about.

---

