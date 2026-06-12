---
title: "dhclient will not return IP - Please Help!"
date: 2010-01-12
forum: Networking &amp; Wireless
---

### Post by mikeroe on 2010-01-12
Hello,
I've been using Ubuntu for a few months now and I'm starting to get more and more interested in running my machine from the command line.  I've been trying to figure out how to connect to a wireless internet connection from the bash terminal but I've really only connected with a bottle of tylenol from all the headaches.  It works every time I use the GUI method, but that's so boring.  I've read through the forums and several other websites, but nothing seems to be working.  I've even posted on a few existing threads, but to no avail.  So, if there's anybody out there that can tell me what is going on, I would very much appreciate that.  Here we go.

When I want to connect to a wireless internet connection, these are the steps I take.

sudo iwlist wlan0 scan
sudo iwconfig wlan0 essid NETWORK_ID key s:ASCII.WIRELESS_KEY
sudo dhclient wlan0

When I run the dhclient, I get the following output:

----------------------------------------------------------------------------------------------------
Internet Systems Consortium DHCP Client V3.1.2
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/wlan0/00:1b:77:61:9b:20
Sending on   LPF/wlan0/00:1b:77:61:9b:20
Sending on   Socket/fallback
DHCPREQUEST of 192.168.1.108 on wlan0 to 255.255.255.255 port 67
DHCPREQUEST of 192.168.1.108 on wlan0 to 255.255.255.255 port 67
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 19
No DHCPOFFERS received.
Trying recorded lease 192.168.1.108
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.

--- 192.168.1.1 ping statistics ---
1 packets transmitted, 0 received, +1 errors, 100% packet loss, time 0ms

No working leases in persistent database - sleeping.
 * Reloading /etc/samba/smb.conf smbd only
   ...done.
---------------------------------------------------------------------------------------------------

I have also tried  'sudo udhcpc wlan0' and that returns:

---------------------------------------------------------------
Sending discover...
Sending discover...
Sending discover...
Lease failed:
Sending discover...
Sending discover...
Sending discover...
Lease failed:
--------------------------------------------------------

Over and over and over again.

Again, if anyone out there knows what is going on and can point me in the right direction, I would greatly appreciate that.

Thank you

---

### Post by adam814 on 2010-01-12
Hmm...you only use the s: for a WEP passphrase.  If you're using hex for your WEP key you don't need the "s:"

If you're using WPA things are different.  Then you'll need to use "wpa_cli".  I'll try to figure out the syntax you'll need when I get home and I'm at my laptop.

---

### Post by mikeroe on 2010-01-12
Yeah, the network is WPA.

---

