---
title: "Unable to associate using iwconfig"
date: 2010-09-17
forum: Networking &amp; Wireless
---

### Post by jlanza on 2010-09-17
Hi,

I'm using Intel 3945 ABG card, using Lucid with network-manager disabled.

I'm trying to associate with a network using iwconfig but it is not possible. The network is open.

I run as root:
ifconfig wlan0 up
iwconfig wlan0 mode Managed essid mynet

And afterwards iwconfig displays Access Point: not associated. Of course the network exists and the device is up.

Any help!!! I'm desperate.

---

### Post by jlanza on 2010-09-17
More info to see if you can help me out.

It seems that after a reboot the first time I try to connect everything goes smoothly. 

However the second time I try to connecto to a different wireless network it doesn't work at all :(

---

### Post by MaindotC on 2010-09-17
Off the top of my head I'm not really sure why iwconfig is doing that - perhaps the settings should be saved in /etc/network/interfaces.  However, is there a reason you're not using a graphical utility such as [Network Manager]("https://launchpad.net/~network-manager")?

---

### Post by jlanza on 2010-09-17
I need to use iwconfig as I'm developing a script to setup the wifi interface based on some parameters.

Any idea?

---

### Post by MaindotC on 2010-09-17
I'm not sure why it's not associating with the AP because this is a very straight forward command.  I'm also using the same wireless card:```
03:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
```.  I stopped NetworkManager, then used iwconfig and I connected just fine :(```
x@x:~$ sudo ifconfig wlan1 up
x@x:~$ sudo iwconfig wlan1 essid MSCguest
x@x:~$ iwconfig wlan1

wlan1     IEEE 802.11g  ESSID:"MSCguest"  Nickname:""
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:0C:E6:28:2A:00   
          Bit Rate=54 Mb/s   Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Power Management:off
          Link Quality=93/100  Signal level=-33 dBm  Noise level=-67 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

x@x:~$ sudo dhclient wlan1
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/wlan1/00:13:02:4a:1c:03
Sending on   LPF/wlan1/00:13:02:4a:1c:03
Sending on   Socket/fallback
DHCPDISCOVER on wlan1 to 255.255.255.255 port 67 interval 5
DHCPOFFER of 136.204.234.32 from 136.204.224.1
DHCPREQUEST of 136.204.234.32 on wlan1 to 255.255.255.255 port 67
DHCPACK of 136.204.234.32 from 136.204.224.1
bound to 136.204.234.32 -- renewal in 10101 seconds.

```

---

### Post by jlanza on 2010-09-17
In other computers I have tried it's also working but the issue is that in mine some problem is showing up.

The issue is I would like to find out why is not working.

---

### Post by MaindotC on 2010-09-17
Check syslog - see if there are any errors associated with the time that you issue the iwconfig.

---

### Post by miodziu on 2010-11-15
Your problem seems to be the same as in [http://ubuntuforums.org/showthread.php?t=1621777](http://ubuntuforums.org/showthread.php?t=1621777)
Good luck.

---

### Post by uncaspi on 2010-11-15
Try to also issue channel in the iwconfig command.See man iwconfig
i.e 
sudo iwconfig wlan0 essid "mjauritz" mode managed channel 6

---

