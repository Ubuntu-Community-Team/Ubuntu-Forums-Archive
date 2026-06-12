---
title: "Beginner: Wireless not working - help!"
date: 2011-02-13
forum: Networking &amp; Wireless
---

### Post by catjunior on 2011-02-13
Hi,
I've just loaded ubuntu to give my old laptop a new leece of life. Everything is fine expect that I can't get the wireless card to work. It just doesn't seem to be exist on my computer anymore. The computer has a button to turn wireless on and off, which worked when it was a windows system, but doesn't seem to do anything anymore. I'm an aboslute ubuntu beginner, so any help or advice would be very welcome, 
Thanks in advance!

---

### Post by Choad on 2011-02-13
step 1, find out what the system knows about your wireless card

open up a terminal (applications > accessories > terminal) and run the following commands

```

ifconfig
lspci

```

the first command will list all the network devices that are loaded, the second command will list everything in your computer connected to the pci bus (and most wireless cards are pci, unless you know yours is usb, in which case run lsusb instead) 

paste the resulting output here and someone will be able to help you in the next steps

---

### Post by catjunior on 2011-02-13
Hi, Thanks for replying, here's the response from the commands you mentioned (it's mostly Greek to me!):
cat@cat-AMILO-M:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0a:e4:21:f1:d0  
          inet addr:192.168.1.69  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20a:e4ff:fe21:f1d0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4617 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3855 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:5657745 (5.6 MB)  TX bytes:598656 (598.6 KB)
          Interrupt:10 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:720 (720.0 B)  TX bytes:720 (720.0 B)

cat@cat-AMILO-M:~$ lspci
00:00.0 Host bridge: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.1 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.3 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:02.1 Display controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 83)
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 03)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 03)
02:03.0 FireWire (IEEE 1394): Agere Systems FW322/323 (rev 61)
02:05.0 Ethernet controller: Broadcom Corporation BCM4401 100Base-T (rev 01)
02:06.0 Network controller: Intel Corporation PRO/Wireless LAN 2100 3B Mini PCI Adapter (rev 04)
02:09.0 CardBus bridge: Texas Instruments PCI1510 PC card Cardbus Controller

---

### Post by Choad on 2011-02-13
well the output of ifconfig says your system has the following network interfaces: "eth0" and "lo"

eth0 is short for ethernet0 which is your wired network port. lo is a "loopback" address which you don't need to be concerned with.

so your system definitely hasn't detected the wireless (well, that much was obvious from the start but it's good to make sure)

the lspci command tells us, along with a bunch of irrelevant stuff, that your wireless card is an "Intel Corporation PRO/Wireless LAN 2100 3B Mini PCI Adapter"

this card does work in linux, but for some reason isn't being detected.

im not really sure what is causing this.

you might try going in to the bios settings. it's usually F2 or Esc or something just after you turn on the computer, it should say somewhere "press <some key> for settings" or similar. if you poke your nose around in those settings you might see something for the wireless card being enabled or disabled. if you do find it, set it to enabled. if you don't, post back here and pray that someone else has some insight?

---

### Post by grahammechanical on 2011-02-13
I do not have a laptop but I can tell this, that button that turns wireless on and off does do something. It still turns wireless on and off! That has not changed. If wireless has been turned off in hardware than Ubuntu will not detect the wireless adapter.

From the listing that you gave I can see that you are connected to the modem by ethernet cable. Do you see the words UP and RUNNING. That tells us that eth0 (the first ethernet adapter) is working and connected. Do you see inet addr:192.168.1.6. That is IP address of your router. You want to see something similar alongside the word wlan0 (that will be your wireless adapter)

Do you see the network icon? If you are connected by wire (ethernet) then it will be two arrows going in opposite directions. If you left click do you see a list of available wireless network in range? If you do and you can see your wireless network then click on it. Of course you need to press the key on the keyboard or we are wasting our time.

If you cannot see a list of available wireless networks then, with a wired connection, go to System>Administration>Additional Drivers and see if there is available a driver for you wireless adapter. If so than try to activate it . Reboot afterwards. Start off with doing this.

Regards.

---

### Post by catjunior on 2011-02-14
Hi,
Thanks for the assistance so far. I'm still having a few problems...
I went into the bios as you suggested, and the wireless was set to disabled. I've changed that now and at the wireless light is now on all the time. However, I still cant seem get the get the wireless card to work.
If I go to the network icon, the 'wireless networks'  is shaded out. I've searched for additional drivers as sugested, but it doesn't find any. 
Hopefully we're getting there! 
Any other ideas?
Thanks

---

### Post by Choad on 2011-02-17
run ifconfig again whenever you change something to see if the card is picked up.
- try the key combination that turns on the wireless again
- right click the network icon make sure "enable wireless" is checked

i'm out :S

---

### Post by grahammechanical on 2011-02-17
Ok, now we know how to switch the wireless adapter on in hardware. We are left with switching it on in software. As you guessed it requires a right click of the icon. But the Enable Wireless is greyed out. 

So, click the line Enable Networking to remove the tick mark and then click it a second time to replace the tick mark. You might find that Enable Wireless is no longer grayed out and you have a tick mark against as well. Clicking Enable Networking is like a on/off switch.

Remember also, that a shutdown and reboot is sometimes necessary when configuration files have been changed. so, try that. 

Then left click the icon and with a bit of luck you will see your wireless network in the list. Select it and authenticate the connection. Network Manage will remember the pass phrase that you put in. If you edit the connection to connect automatically then it will do just that each time to boot.

Regards.

---

### Post by catjunior on 2011-02-21
Thanks for the continued help! 
I've tried all those suggestions and still no joy. The 'enable wireless' and 'wireless networks' are still greyed out, despite reboots and toggling 'enable networking'. I've also tried searching for drivers again just on the off-chance.
I thought I'd post ifconfig and lspci just incase you can make sense of any changes since I've turned the wireless hardware on:

cat@cat-AMILO-M:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0a:e4:21:f1:d0  
          inet addr:192.168.1.73  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20a:e4ff:fe21:f1d0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:12378 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8487 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:6836491 (6.8 MB)  TX bytes:1897677 (1.8 MB)
          Interrupt:10 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:720 (720.0 B)  TX bytes:720 (720.0 B)

cat@cat-AMILO-M:~$ lspci
00:00.0 Host bridge: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.1 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.3 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:02.1 Display controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 83)
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 03)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 03)
02:03.0 FireWire (IEEE 1394): Agere Systems FW322/323 (rev 61)
02:05.0 Ethernet controller: Broadcom Corporation BCM4401 100Base-T (rev 01)
02:06.0 Network controller: Intel Corporation PRO/Wireless LAN 2100 3B Mini PCI Adapter (rev 04)
02:09.0 CardBus bridge: Texas Instruments PCI1510 PC card Cardbus Controller

---

