---
title: "Can't get wireless to work properly"
date: 2006-06-03
forum: Networking &amp; Wireless
---

### Post by Jammy_Stuff on 2006-06-03
I am installing my Edimax EW-7318Ug and have used ndisgtk to install it. That shows that the driver is installed correctly and the hardware is present, as does a ndiswrapper -l.

Configuring it in networking then seems to work but once it is configured it takes a long time to connect. If I then try and use firefox for example it immediately says the server isn't found.

Below is the output from a ifdown:

> james@james-desktop:~$ sudo ifdown wlan0
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

Listening on LPF/wlan0/00:0e:2e:66:34:63
Sending on   LPF/wlan0/00:0e:2e:66:34:63
Sending on   Socket/fallback
DHCPRELEASE on wlan0 to **192.168.1.1** port 67
send_packet: Network is unreachable
send_packet: please consult README file regarding broadcast address.
Error for wireless request "Set ESSID" (8B1A) :
    SET failed on device wlan0 ; Invalid argument.

I have put the part where I think it is going wrong in bold. My gateway's IP address is 192.169.110.1 rather than 192.168.1.1.

Here is the output from a ifup:

> james@james-desktop:~$ sudo ifup wlan0
Error for wireless request "Set ESSID" (8B1A) :
    SET failed on device wlan0 ; Invalid argument.
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

Listening on LPF/wlan0/00:0e:2e:66:34:63
Sending on   LPF/wlan0/00:0e:2e:66:34:63
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

I have tried disabling WEP and MAC addrees filtering and still have the same problem. Does anyone know what is wrong?

---

### Post by Titus A Duxass on 2006-06-03
Post the output from the following:

ifconfig and iwconfig.

Did you put ndiswrapper in /etc/modules and then a modprobe ndiswrapper?

Also you may need to edit your /etc/network/interfaces file for the wlan0 settings.

I am surprised that dapper did not recognize your card, what chipset does it have?

---

### Post by Jammy_Stuff on 2006-06-03
I'll remember those commands and boot back into Ubuntu in a minute. As for the chipset it is a Zydas 1211 chipset.

---

### Post by Titus A Duxass on 2006-06-03
"Zydas 1211 chipset" - I've not heard of this chipset before.  I recommend that you stay with the ndiswrapper route.

If you have problems getting the card to activate after all the steps try:

Shutdown but don't remove power,

Reboot and go into BIOS and make sure the other net interfaces are disable (i.e. - eth0).

If the card still does not activate but you get the power light on or flashing try:

Shutdown leave power connected,
remove wireless card,
reboot,
shutdown leave power connected,
replace wireless card,
reboot.

That usually works for me, well it did 30 mins ago.

---

### Post by Jammy_Stuff on 2006-06-03
I think I've found the problem. The ifconfig gave this:

> james@james-desktop:~$ ifconfig
lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:11 errors:0 dropped:0 overruns:0 frame:0
          TX packets:11 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:572 (572.0 b)  TX bytes:572 (572.0 b)

wlan0     Link encap:Ethernet  HWaddr 00:0E:2E:66:34:63
          inet addr:**192.168.1.6**  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20e:2eff:fe66:3463/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:75 errors:0 dropped:0 overruns:0 frame:0
          TX packets:25 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:10309 (10.0 KiB)  TX bytes:4372 (4.2 KiB)

The first problem is that I was assigned an IP that was 192.168.1.x rather than a 192.168.110.x. I wondered why this was but the iwconfig gave the answer:

> james@james-desktop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     802.11b/g NIC  **ESSID:"linksys"**
          Mode:Managed  Frequency=2.462 GHz  Access Point: 00:0C:41:A1:71:A4
          Bit Rate:11 Mb/s
          Retry:off   RTS thr=2432 B   Fragment thr:off
          Power Management:off
          Link Quality=28/92  Signal level=9/154  Noise level=161/154
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:833  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

It has connected to a neighbours network even though /etc/network/interfaces clearly instructs it to connect to my SSID. Any idea how to sort this out?

---

### Post by Titus A Duxass on 2006-06-03
Do you have the following line in your interfaces file:

wireless-essid XXXX - replace XXXX with your essid.

---

### Post by Jammy_Stuff on 2006-06-03
That's the thing in my interfaces to tell it to connect to my network so yes it is there.

---

### Post by Titus A Duxass on 2006-06-03
Here is a copy of my interfaces file:

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface

iface wlan0 inet static
        address 192.168.2.101
        netmask 255.255.255.0
        network 192.168.2.0
        broadcast 192.168.2.255
        gateway 192.168.2.1
        # dns-* options are implemented by the resolvconf package, if installed
        dns-nameservers 192.168.2.1
        wireless-essid WLAN
auto wlan0

---

### Post by Jammy_Stuff on 2006-06-03
I just reinstalled Ubuntu and this time it found the adapter and installed it. Still have the same problem though. I've tried using static IP rather than DCHP but still no luck.

Any more ideas as this is the one thing that's stopping me from using Ubuntu?

---

### Post by Jammy_Stuff on 2006-06-03
I've deicded that its either down to the router or to the adapter. I've got a spare router which I'll try to connect to but should that still not work could people let me know of cheap PCI or USB adapters that work with Dapper with no fiddling (or ndiswrapper). Thanks.

---

### Post by Jammy_Stuff on 2006-06-04
Please can someone help? I really want to make the switch to Ubuntu. Alternatively, is there any way of connecting my spare Belkin WiFi router to my PC vis ethernet and instruct that to allow me to connect to the WiFi network through it.

---

### Post by rodica.balasa on 2008-01-18
I managed to make it work in gutsy, with edimax dirvers, here is the howto:
[URL="http://www.len.ro/work/tools/old-new-i8000-2"]
http://www.len.ro/work/tools/old-new-i8000-2[/URL]

---

