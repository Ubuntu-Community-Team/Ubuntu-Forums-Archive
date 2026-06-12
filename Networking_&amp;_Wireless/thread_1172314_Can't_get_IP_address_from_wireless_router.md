---
title: "Can't get IP address from wireless router"
date: 2009-05-28
forum: Networking &amp; Wireless
---

### Post by SteelSlasher on 2009-05-28
Hi, its been about 4 months using Xubuntu right now and it ran a bit slow with xfce and so i moved to using lxde which was much faster i was still unimpressed by sudden slowdowns when moving between windows. I then tried icewm but unlike my past two window managers icewm won't or will not connect to my router.

I am running xubuntu on my 5 year Dell Inspiron which has a 1.4Ghz Celeron M, intel intergrated graphics, 256 RAM, and inbuilt wireless card (thats not the entire machine its just to be concise).

Now when using wifi-radar in xfce or lxde it would auto connect almost instantly to logging in but in icewm i have to load the program through the menu (which helps save power in a way) but when i click on a profile and then connect it will show window with a progress bar and would say it is acquiring an IP address. But every single time it fails, (i am using lxde for this message) i have checked my router (which is a netgear) and had a look at attached devices.

When i use icewm the attached devices list shows my desktop and this laptop, the laptop shows no device name or ip address. When i use lxde the device name is shown and an ip address. I would really like to use icewm since it seems to run much more smoothly than lxde but since i would use my large "netbook" for mainly internet related purposes icewm is practically worthless.

Also on an unrelated point, whenever i load the synaptic package manager the laptop seizes up for 5 minutes and then asks for a password (only with lxde and xfce)

I have tried to follow the HOWTO but it my wireless card isnt attached by pci or usb.

---

### Post by SteelSlasher on 2009-05-29
Bump

---

### Post by SteelSlasher on 2009-05-30
I would really like to solve this problem now, can't anyone help me.

---

### Post by Chris_no on 2009-05-30
I have no idea if I can but I'll try.

Obviously the way icewm access your network card is differnet in some way.

Type in terminal:

> iwlist scanning

Do this in both icewm and one of the others.

Can they both see the same?

---

### Post by SteelSlasher on 2009-05-30
they both say exactly the same thing except for two lines

LXDE:
Quality=95/100 Signal level=-32 dBm
Extra: Last beacon: 2216ms ago

Icewm:
Quality=94/100 Signla level=-30dBm
Extra: Last beacon: 8ms ago

I didnt bother with XFCE since i find it a bit too sluggish

---

### Post by Chris_no on 2009-05-30
Try /etc/init.d/networking start in terminal in icewm.

If that works add "/etc/init.d/networking start" to your /etc/rc.local file.

---

### Post by SteelSlasher on 2009-05-30
how would i open that file with SU rights and should i just append that string before the "exit 0"

---

### Post by Chris_no on 2009-05-30
Write:

> sudo gedit /etc/rc.local

Yes before the exit 0!

---

### Post by SteelSlasher on 2009-05-30
done that, now wifi radar doesnt launch via the menu

---

### Post by Chris_no on 2009-05-30
But are you online with icewm or not?

The whole point was to not need wifi-radar in the first place.

---

### Post by SteelSlasher on 2009-05-30
unfortunately no

---

### Post by Chris_no on 2009-05-30
Did you try to enter in terminal?

> sudo /etc/init.d/networking start

If that didn't get you online there is no point in enter anything into the file.

Could you post output of

> sudo ifconfig -a

> sudo iwconfig

> sudo lshw -C network

> sudo cat /etc/network/interfaces

Just to make sure that we are on the same page.

---

### Post by SteelSlasher on 2009-05-30
EDIT!!!! OMG my Wifi WORKS FINE NOW!!! I should have a go at it for not working for the past few weeks! I am not sure if this is a one of thing or if it is well and truly fixed!
SECOND EDIT!!! Just restarted and it looks not fixed!

Here you go!

sudo ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:12:3f:d1:f0:55  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:18 

eth1      Link encap:Ethernet  HWaddr 00:12:f0:76:a6:7a  
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:176 errors:0 dropped:0 overruns:0 frame:0
          TX packets:26 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:17525 (17.5 KB)  TX bytes:3039 (3.0 KB)
          Interrupt:17 Base address:0xc000 Memory:dfdfd000-dfdfdfff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

pan0      Link encap:Ethernet  HWaddr 46:a0:e3:7d:2b:b9  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

sudo iwconfig
eth1      IEEE 802.11g  Mode:Managed  Frequency:2.462 GHz  
          Access Point: 00:1B:2F:E5:8E:F0   Bit Rate:54 Mb/s   Tx-Power=20 dBm   
          Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=95/100  Signal level=-32 dBm  Noise level=-91 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sudo lshw -C network
  *-network:0
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:12:3f:d1:f0:55
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=half latency=64 link=no module=ssb multicast=yes port=twisted pair speed=10MB/s
  *-network:1
       description: Wireless interface
       product: PRO/Wireless 2200BG [Calexico2] Network Connection
       vendor: Intel Corporation
       physical id: 3
       bus info: pci@0000:03:03.0
       logical name: eth1
       version: 05
       serial: 00:12:f0:76:a6:7a
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw2200 driverversion=1.2.2kmprq firmware=ABG:9.0.2.6 (Mar 22 2005) ip=192.168.1.2 latency=64 link=yes maxlatency=24 mingnt=3 module=ipw2200 multicast=yes wireless=IEEE 802.11g
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 46:a0:e3:7d:2b:b9
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

sudo cat /etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

---

### Post by Chris_no on 2009-05-30
It seems to me that since you have used wifi-radar you have never had your
network files configured to start networking.

And since wifi-radar somehow doesn't manage to connect in icewm you will
have to configure your wireless manually.

Use

> sudo gedit /etc/network/interfaces

and add to bottom of file

> auto eth1
iface eth1 inet dhcp
wireless-key ******** --Only use if on WEP
wireless-essid ********--Only use if on WEP

then do

> sudo /etc/init.d/networking restart

---

### Post by SteelSlasher on 2009-06-07
Wow! Thanks a lot that really fixed it well and truly. Also, i have noticed that logging to LXDE and to icewm will grant me a wifi connection.

Sorry about the late reply, i have had exams everyday for the past week and so was a bit busy studying, no of to work experience at Airbus tomorrow.

---

