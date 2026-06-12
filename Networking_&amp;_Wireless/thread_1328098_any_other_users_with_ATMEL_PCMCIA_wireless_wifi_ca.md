---
title: "any other users with ATMEL PCMCIA wireless wifi card issues in 9.1 ? no wifi here ..."
date: 2009-11-16
forum: Networking &amp; Wireless
---

### Post by bjaz on 2009-11-16
hello all
as described in this thread
                         [PCMCIA wireless adapter, worked fine on all previous versions, doesn"t on Karmic, help..]("http://ubuntuforums.org/showthread.php?t=1322717")

but i'm reposting all the details 
I've switched to ubuntu 9.1, and all is well, except the wifi wireless. 
the machine, an old japanese sony VAIO VGN FS21B has been using an ATMEL PCMCIA wireless adapter on windows XP, then on Xubuntu Jaunty, which was then updated to Xubuntu karmic.

the PCMCIA wifi card, ATMEL  AT76C502A.
FCC ID:KFY-WA1113, worked fine, out of the box

yet for a number of other reason, these other versions were dropped in favour of a standard Ubuntu i386 desktop, which runs beautifully well.

appart from the PCMCIA wifi adapter card. no go. no wifi since, using an ethernet cable since.

have others had this issues and found workarounds ? 

despite the splendid effort to help out made in the thread pasted above, it's stalling. 
ubuntu was reinstalled three times, clean checksummed and verified cd's, no go.

if anyone has any new ideas on how to get this card working, it would be great.

I still have the windows driver if this helps- i just don't quite figure out how it worked in jaunty, and in xubuntu jaunty AND karmic (while there were numerous other bugs due to the update, wifi worked), but will not in a clean install of Ubuntu desktop 9.1...

posting all the specs below

thanks a million

ben

---

### Post by bjaz on 2009-11-16
it is all in the thread link given, but just to make this post more compliant with the how to post a wireless ticket thread, here's the info :

Ubuntu desktop 9.1 i386

model Japanese Sony Vaio VGN-FS21

[B]wireless brand : ATMEL PCMCIA wifi wireless adapter card,
[/B]ATMEL  AT76C502A.
FCC ID:KFY-WA1113
[B]
 worked fine in Jaunty (out of the box), and Xubuntu Jaunty, and continued working in Xubuntu Karmic after the update.

 doesn't work in Ubuntu 9.1 clean install (re-installed 3 times)[/B]

cable ethernet works

-----------------------------


kayo@kayo-oppo:~$ lspcmcia
Socket 0 Bridge:       [yenta_cardbus]     (bus ID: 0000:06:03.0)
Socket 0 Device 0:    [pata_pcmcia]        (bus ID: 0.0)

-----------------------------

kayo@kayo-oppo:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d3)
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
06:03.0 CardBus bridge: Texas Instruments PCI7420 CardBus Controller
06:03.2 FireWire (IEEE 1394): Texas Instruments PCI7x20 1394a-2000 OHCI Two-Port PHY/Link-Layer Controller
06:03.3 Mass storage controller: Texas Instruments PCI7420/7620 Combo CardBus, 1394a-2000 OHCI and SD/MS-Pro Controller
06:08.0 Ethernet controller: Intel Corporation 82562ET/EZ/GT/GZ - PRO/100 VE (LOM) Ethernet Controller Mobile (rev 03)
kayo@kayo-oppo:~$ 

----------------------------------------

kayo@kayo-oppo:~$ lsusb
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

--------------------------------------

kayo@kayo-oppo:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:01:4a:60:fa:c0  
          inet adr:192.168.1.20  Bcast:192.168.1.255  Masque:255.255.255.0
          adr inet6: fe80::201:4aff:fe60:fac0/64 Scope:Lien
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Packets reçus:37285 erreurs:0 :0 overruns:0 frame:0
          TX packets:34956 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:1000 
          Octets reçus:35470092 (35.4 MB) Octets transmis:5552350 (5.5 MB)

lo        Link encap:Boucle locale  
          inet adr:127.0.0.1  Masque:255.0.0.0
          adr inet6: ::1/128 Scope:Hôte
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          Packets reçus:0 erreurs:0 :0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:0 
          Octets reçus:0 (0.0 B) Octets transmis:0 (0.0 B)


----------------


kayo@kayo-oppo:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

------------------

kayo@kayo-oppo:~$ sudo lshw -C network
[sudo] password for kayo: 
  *-network               
       description: ATMEL
       physical id: 0
       version: AT76C502AR_E
       slot: Socket 0
       resources: irq:3
  *-network
       description: Ethernet interface
       product: 82562ET/EZ/GT/GZ - PRO/100 VE (LOM) Ethernet Controller Mobile
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:06:08.0
       logical name: eth0
       version: 03
       serial: 00:01:4a:60:fa:c0
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.24-k2-NAPI duplex=full firmware=N/A ip=192.168.1.20 latency=66 link=yes maxlatency=56 mingnt=8 multicast=yes port=MII speed=100MB/s
       resources: irq:20 memory:b0106000-b0106fff ioport:2000(size=64)


------------------------

kayo@kayo-oppo:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

------------------

kayo@kayo-oppo:~$ lsb_release -d
Description:    Ubuntu 9.10

-------------------

kayo@kayo-oppo:~$ uname -mr
2.6.31-14-generic i686

-----------------------------

kayo@kayo-oppo:~$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                          Ignoring unknown interface eth0=eth0.

--------------

demsg included as an odt file to this post

issue : to wifi via the the PCMCIA card which worked fine in jaunty, and xubuntu, even after the update to xubuntu karmic.
using ubuntu desktop.
windows driver available.

card ref :

ATMEL AT76C502A.
FCC ID:KFY-WA1113


thanks in advance

ben

---

### Post by bjaz on 2009-11-17
is there any chance this will be fixed or that there is a workaround with windows driver ?

i tried connecting it with an inventel wireless lan usb adapter, which also used to work- wireless network can be enabled, it can see various wifi, but it's unable to connect for a reason.
 it's odd as the network is fine, so's the wep key and everything. the connecting icon just stays looping, and the connection doesn't happen, i'm wondering if this isn't an actual ubuntu issue as well.....

only ethernet seems to work like it should. problem is we'll have a 10 connection break as we switched providers, and i was planning to use another wireless access i have here. 10 days with no internet on my wife's computer might be difficult, as she needs it for work here as well.....

so, any ideas of should i reinstall a jaunty version and reconsider---it's too bad because things are great otherwise, better than before on this old sony vaio

b

---

### Post by bjaz on 2009-11-18
bump
could a formerly supported hardware become unsupported for a reason ?

---

### Post by bjaz on 2009-11-19
any idea on what could have caused this (drop of a hardware supports? -) and ways to fix it ?

b

---

### Post by bjaz on 2009-11-19
since i'm not getting any answers or pointer, for safety's sake, i just reinstalled Xubuntu 9.04.
the ATMEL wifi PCMCIA adapter works out of the box again. we'll replace XFCE with gnome and go with that for now, but I really hope someone can help.

I wonder what could be causing the problem with Ubuntu Karmic...

b

---

### Post by Dude-PWB- on 2009-11-19
Did you try ndiswrapper with the windows drivers for the device?

---

### Post by bjaz on 2009-11-19
no not yet. I saw this mentioned in another thread, which is why i mentioned i had the driver, but haven't tried.

i will once i finished configuring the xubuntu install, my wife'll be happy to have the wireless back

thanks

b

---

### Post by bjaz on 2009-11-23
this is the windows driver for this card

 [http://download.porciello.com/inventel/dwb200/Pilotes_Carte_PCMCIA_WiFi_ATMEL.zip](http://download.porciello.com/inventel/dwb200/Pilotes_Carte_PCMCIA_WiFi_ATMEL.zip)

i really wonder why it works in 9.04 and not in 9.10

---

### Post by bjaz on 2009-11-26
bumpitty bump.

i there anything that can go wrong with the wrapper manoeuvre ?

---

### Post by growlf on 2010-02-04
Have you tried this:

[http://packages.ubuntu.com/lt/karmic/atmel-firmware](http://packages.ubuntu.com/lt/karmic/atmel-firmware)

I have a Compaq tablet that has an Atmel in it, I will try it as well with Karmic and post back later.

[UPDATE]

Nope.  Did not work for me either.  In fact it hosed it up.  No answer so far, and may need to file a bug on this?

---

### Post by bjaz on 2010-03-04
sorry for the late reply, i just upgraded the vaio to 1.2go ram...bliss
on ethernet now, fdownloading the karmic updates

the link didn't fix it it, still no atmel pcmcia card availaible, and it still works fine on xubuntu jaunty---and i still have the windows driver for it

ethernet connection works, the lights on the pcmcia card light up, it works on xubunto jaunty but what could be wrong ?

what else could i try so my wife can jump into this wonderful unbuntu karmic insteak of staying on xubuntunu jaunty ?

thanks

b

---

### Post by bjaz on 2010-03-05
sorry for the very naive tone of this questio, but since this external ATMEL PCMCIA card works on the same computer under xubuntu jaunty, isn't there a way the few code lines  extract what makes it work and experimentally implant them into ubunto karmic ?

i really don't understand  what to do. the card is powered, what can I try to make it work, i see existing wirelessnetwork and conect to mined uneder ubuntu, like it does in xubuntu ?

thanks

b

this would be the cards latest INF windows driver

----
I checked on the working xubuntu Jaunty version, the driver used by the PCMCIA  atmel_cs

I really wonder why the same card on the same computer neither works on Ubuntu Karmic nor Xubuntu Karmic

---

### Post by bjaz on 2010-03-05
if this ca help, there's something i've omitted from the start -- when shutting down the Xubuntu Jaunty where the Atmel PCMCIA card works fine, there is a short error message at the end : eth1 cannot start ATMEL AF76C502.bin is missing

now this is on shutting down the xubuntu jaunty where the wireless works fine.

on the same box, we once tried updating xubuntu to karmic : no wireless

we also installed a clean install of Ubuntu Karmic, did the updates via ethernet, still no way to get that ATMEL PCMCIA card working

thanks a lot

ben

---

