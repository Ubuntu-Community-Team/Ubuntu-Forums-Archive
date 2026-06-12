---
title: "can't get wifi to work Packard Bell Centrino laptop"
date: 2006-07-14
forum: Networking &amp; Wireless
---

### Post by harperd on 2006-07-14
I'm been trying for a few weeks to get my laptop's wifi to work with Dapper. I use dual-boot with XP and with XP it works fine. With Wireless Lan manager I get a message that the radio card is off and offers to turn it on. After saying yes it detects the essid but when I try to connect it fails. If I run it again it repeats the message that the radio card is off. I'm a newbie but I can remember a a command something like tx-power that I ran but which gave me an error.

I also have a cable Ethernet connection to my router and sometimes I have to disable the wifi card (eth0) in order to get the a connection through the Ethernet adapter to work.

Any help would be appreciated.

Dave from Madrid, Spain

---

### Post by infoburner on 2006-07-14
can you run "lspci" (without quotes) in a terminal and copy and paste the result back here please?

---

### Post by harperd on 2006-07-15
Here goes! Thanks

0000:00:00.0 Host bridge: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
0000:00:00.1 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
0000:00:00.3 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
0000:00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
0000:00:02.1 Display controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
0000:00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 03)
0000:00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 03)
0000:00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 03)
0000:00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 83)
0000:00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 03)
0000:00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 03)
0000:00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 03)
0000:00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)
0000:00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 03)
0000:01:01.0 Network controller: Intel Corporation PRO/Wireless LAN 2100 3B Mini PCI Adapter (rev 04)
0000:01:02.0 Ethernet controller: VIA Technologies, Inc. VT6105 [Rhine-III] (rev 8b)
0000:01:03.0 CardBus bridge: Texas Instruments PCI1410 PC card Cardbus Controller (rev 02)

---

### Post by infoburner on 2006-07-15
> 
0000:01:01.0 Network controller: Intel Corporation PRO/Wireless LAN 2100 3B Mini PCI Adapter (rev 04)


this line tells me that you need to use the ipw2100 kernel module to use this card. it is included in ubuntu by default. just type 
```

sudo modprobe ipw2100

```
to load the module, then you should be able to configure the card with System->Administration->Networking.

post back here if you need more help

---

### Post by harperd on 2006-07-15
Sorry but no luck. In Kwifimanager it tells me the radio is disabled. I click the option to turn the radio on and I get a dialogue box asking me for the root password and indicating that it will enter the following command 
iwconfig 'eth0' 'txpower' 'on'
When I open Kwifimanager after, the card is still disabled although it seems to see the network (WLAN). I guess maybe the command is failing for some reason.

---

### Post by infoburner on 2006-07-15
is kwifimanager configure to use the correct interface? i see you also have a ethernet card. since ethernet drivers usually load before any wireless driver, im willing to bet that your wifi card is named something like eth1, if not wlan0 or wifi0. 

try doing by hand to skip whatever kwifi manager does. first of all, type "sudo iwconfig" to see a list of your interfaces. everthing that is not a wireless card should say something like "eth0   no wireless extensions". one of them will give you more info, that is the name of your wireless interface.
after booting up, type the following into a terminal, replacing "wlan0" with whatever the name of your interface is
```

sudo iwconfig wlan0 essid "your essid"
sudo ifconfig eth0 down
sudo dhclient wlan0

```

---

### Post by harperd on 2006-07-16
I wansn't entirely clear on your earlier instructions but "sudo dhclient wlan0" gave me the following

Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

SIOCSIFADDR: No such device
wlan0: ERROR while getting interface flags: No such device
wlan0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device


iwconfig gives me this

lo        no wireless extensions.

eth1      no wireless extensions.

eth0      unassociated  ESSID:"WLAN"  Nickname:"ipw2100"
          Mode:Managed  Channel=0  Access Point: Not-Associated
          Bit Rate=0 kb/s   Tx-Power:off
          Retry min limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

---

### Post by infoburner on 2006-07-16
ok, from the output of iwconfig, we know that your wireless is eth0 (i thought it wouldnt be). try the following:
```

sudo iwconfig eth0 essid "your essid"
sudo ifconfig eth1 down
sudo dhclient eth0

```

---

### Post by harperd on 2006-07-19
Thanks, haven't had time to try this. Will get back later in the week. I'm using static ip addresses. Does this make a difference?

---

### Post by infoburner on 2006-07-19
yeah, static ip will make a difference. if your router is configured for static ip, then do this:
```

sudo ifconfig eth1 down
sudo iwconfig eth0 essid "your essid"
sudo ifconfig eth0 ip.addr.you.want
sudo ifconfig eth0 up

```

---

### Post by harperd on 2006-07-21
well I've got it to work with your help and some messing with various settings. Kwifimanager still says the card is disabled so I'm still a little puzzled.

Thanks for your help - it's much appreciated!

---

