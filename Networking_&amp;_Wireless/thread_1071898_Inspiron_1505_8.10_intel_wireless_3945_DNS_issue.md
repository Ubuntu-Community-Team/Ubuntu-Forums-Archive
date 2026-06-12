---
title: "Inspiron 1505 8.10 intel wireless 3945 DNS issue"
date: 2009-02-16
forum: Networking &amp; Wireless
---

### Post by viperuws on 2009-02-16
Inspiron 1505

Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection [8086:4222] (rev 02)

wlan0     IEEE 802.11abg  ESSID:"Home"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:12:17:C4:41:8D   
          Bit Rate=54 Mb/s   Tx-Power=14 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality=95/100  Signal level:-33 dBm  Noise level=-62 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

Running 32bit 8.10 ubuntu


I am still somewhat new to linux.  Now I had dapper and edgy working with my wireless after installing the drivers but ubuntu wasn't updating correctly so i wiped and did a fresh install of intrepid.  My wired network works perfectly fine, wireless works with windows on the same machine (dual boot), I am able to ping ip addresses but not resolve DNS's.

I googled it and tried doing stuff like making static open DNS ips in my routers config, changing it in multiple places like the network manager and resolv.conf and after a restart it stays so its not a problem of the dns info changing.  And after all this I still cant figure out what is wrong.  The only thing I haven't tried was downloading firmware for it which I find somewhat strange considering it worked for previous installations.

I also checked into the whole ipv6 thing and I disabled it and still having issues.

On my router currently I am running no encryption for testings sake, no firewalls or mac filtering.  The only thing out of the ordinary is im running static dhcp to run port forwarding while allowing people that come over to still get a normal dhcp ip.  I have this laptop set as 192.168.1.103 as a static dhcp ip.  This is all on a WRT with hacked firmware. (I wanted port redirection at one point)

anyone have any ideas or need more info?  3 hours is my limit for playing around aimlessly in one day. :(

---

