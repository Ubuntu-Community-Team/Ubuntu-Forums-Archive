---
title: "HardyHeron = wireless 10.04 = no wireless"
date: 2010-11-07
forum: Networking &amp; Wireless
---

### Post by greasy19 on 2010-11-07
Hello, 

I used to run hardy heron, no wireless problems at all. Today I upgraded to 10.04 and I have no wireless.

There is a notification area present in the tool bar at the top but it only displays the Bluetooth icon. I've looked at a few other threads and my network manager appears to be running.

I blindly tried this command: nm-applet --sm-disable - and it didn't seem to do anything. 

I'm currently hard wired through eth0 and eth1 would appear to be my wireless card. 

When I run iwconfig I get:

----------------------------------------

lo        no wireless extensions.

eth0      no wireless extensions.

eth1      unassociated  ESSID:off/any  
          Mode:Managed  Channel=0  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power=20 dBm   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

-----------------------------------------

Any pointers are greatly appreciated.

---

### Post by pauwl on 2010-11-07
Hello Greasy,


it would be good to know what kind of wireless card you have.
Some (like e.g. on some ASUS machines) will require a seperate step for loading a driver.

So it would help if you could mention the make & model of your PC/laptop and wireless card.

Typing the command: lspci
in the command-line terminal might show it up (hopefully). But probably not as you have no wireless yet...

Let us know.

Pauwl

---

### Post by greasy19 on 2010-11-07
Righto, I have a Toshiba Portege M200:

By running 'sudo lshw -C Network' - it gives me the following info about my wireless card:

>  *-network:0             
       description: Wireless interface
       product: PRO/Wireless 2200BG [Calexico2] Network Connection
       vendor: Intel Corporation
       physical id: 5
       bus info: pci@0000:02:05.0
       logical name: eth1
       version: 05
       serial: 00:0e:35:7b:ec:4f
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw2200 driverversion=1.2.2kmprq firmware=ABG:9.0.5.27 (Dec 12 2007) latency=64 link=no maxlatency=24 mingnt=3 multicast=yes wireless=unassociated
       resources: irq:11 memory:fceff000-fcefffff


By running lspci I get:

> 00:00.0 Host bridge: Intel Corporation 82855PM Processor to I/O Controller (rev 21)
00:01.0 PCI bridge: Intel Corporation 82855PM Processor to AGP Controller (rev 21)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 83)
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 03)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 03)
01:00.0 VGA compatible controller: nVidia Corporation NV34M [GeForce FX Go5200 32M/64M] (rev a1)
02:05.0 Network controller: Intel Corporation PRO/Wireless 2200BG [Calexico2] Network Connection (rev 05)
02:08.0 Ethernet controller: Intel Corporation 82801DB PRO/100 VE (MOB) Ethernet Controller (rev 83)
02:0b.0 CardBus bridge: Toshiba America Info Systems ToPIC100 PCI to Cardbus Bridge with ZV Support (rev 33)
02:0d.0 System peripheral: Toshiba America Info Systems SD TypA Controller (rev 05)


It appears to have detected it, network manager appears to be installed, but there do not appear to be any visible wireless settings where I can select my network as I used to with Hardy.

Thanks

---

### Post by uncaspi on 2010-11-07
[http://ubuntuforums.org/showthread.php?t=1538766&highlight=2200BG&page=2](http://ubuntuforums.org/showthread.php?t=1538766&highlight=2200BG&page=2)

You may look at this thread.

---

### Post by greasy19 on 2010-11-07
...and it's magically started working.

Not sure how, I hit the function key and F8 (wireless symbol) and then I get a list of wireless networks pop up.

Very, very embarrassing - but the wireless card was switched on (the light was on!), now time to get VLC to give a smooth picture.

Thank you to those that helped.

---

