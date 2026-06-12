---
title: "Wireless problem w/ Orinico..."
date: 2006-06-22
forum: Networking &amp; Wireless
---

### Post by snakedog on 2006-06-22
...I'm posting this issue again, hopefully in the right forum.

I got Xubuntu installed on an old Thinkpad 600X from the standard "live" cd, dualbooting w/ Win2000. 

Everything seemed ok when booting from the cd to Xubuntu, including the wireless card, an Avaya (Orinico Gold) 802.11b PCMCIA card. But upon rebooting after installing Xubuntu to the hdd, no wireless card. Nothing I can find.

Funny thing is that the same card works under Ubuntu on my other laptop, a Toshiba A45-S120.

And what's even odder is a U.S. Robotics card I use under Win2000, one that Ubuntu 6.06 totally failed to pick up on the other computer and one I had no hope of working under Xubuntu, is indeed found by Xubuntu!  Argh!  The problem I'm having with the USR card is I'm unable to pull an ip address (dhclient, right?) after running iwconfig.  I'd be happy w/ anything that worked.

Go figure...

...somebody?

---

### Post by queenorych on 2006-06-22
what hapens when you type iwconfig?  Does it list an access point?  does dmesg come up with any erros arising out of the Ornico gold?

---

### Post by snakedog on 2006-06-23
OK, here's my "iwconfig":
------------------------------------------------------------------
karl@Dell:~$ sudo iwconfig
Password:
lo        no wireless extensions.

irda0     no wireless extensions.

wlan0     IEEE 802.11b+/g+  ESSID:"STA52CFC3"  Nickname:"acx v0.3.21"
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated
          Bit Rate:54 Mb/s   Tx-Power=15 dBm   Sensitivity=1/3
          Retry min limit:7   RTS thr:off
          Encryption key:off
          Power Management:off
          Link Quality=35/100  Signal level=9/100  Noise level=0/100
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

karl@Dell:~$ sudo iwconfig wlan0 essid MUKI
karl@Dell:~$ sudo iwconfig
lo        no wireless extensions.

irda0     no wireless extensions.

wlan0     IEEE 802.11b+/g+  ESSID:"MUKI"  Nickname:"acx v0.3.21"
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated
          Bit Rate:54 Mb/s   Tx-Power=15 dBm   Sensitivity=1/3
          Retry min limit:7   RTS thr:off
          Encryption key:off
          Power Management:off
          Link Quality=52/100  Signal level=33/100  Noise level=0/100
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

karl@Dell:~$ sudo dhclient wlan0
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

Listening on LPF/wlan0/00:c0:49:52:cf:c3
Sending on   LPF/wlan0/00:c0:49:52:cf:c3
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
karl@Dell:~$
-----------------------------------------------------------------

I've got no idea where it gets that first essid.  There's no such wireless network nearby.   Of course, I seem to get that squared away by pointing the card to the proper essid (MUKI).  But then I'm unable to pull an ip address.  I checked /var/log/dmesg and the only reference to the wlan0 I could find is the line below:

[   74.124893] acx v0.3.21: net device wlan0, driver compiled against wireless extensions 19 and Linux 2.6.15-23-386

I'm not sure of the time stamp on that line, I tried three different cards and have no idea which one generated that particular message.  There's no other error messages as such.  The current card is a U.S. Robotics USR5410 (802.11g).  Thanks.

---

### Post by queenorych on 2006-06-23
Don't worry about dhclient yet, your not connected to anything.  I assume you have a access point (router) you are trying to connect to.  The mac address of the router should be listed next to "Access Point" if you are connected.  Is your access point secured?  Type in iwlist scan, does that list your network.  With your card it's my understanding that it should just work.

If your network doesn't use wep or wap, I would set the channel "iwconfig wlan0 channel X" where X is the channel lsited by iwlist scan.  Then set the ap the same way "iwconfig ap XX:XX:XX..."  Then ifconfig wlan0 up.  Then you should be associated, then do a dhclient wlan0.  Once you get it working on the command line, then you have something to work off of.

Also search the forums, there has got to be a guide for you somewhere.

---

