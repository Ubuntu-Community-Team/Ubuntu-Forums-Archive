---
title: "Can't seem to connect to wireless router. &quot;NO DHCPOFFERS received&quot;"
date: 2011-02-16
forum: Networking &amp; Wireless
---

### Post by pareLi on 2011-02-16
Hey, I've run into a problem while trying to fix another problem.

Original post: [http://ubuntuforums.org/showthread.php?t=1685759](http://ubuntuforums.org/showthread.php?t=1685759)

A quick sum up: Error; *"Your screen, graphics card and input device settings could not be detected correctly. You will need to configure these yourself."* popped up 3 days after my first Ubuntu installation while booting up. I think i have found the solution, but i can't seem to get it fixed without internet.

**/etc/network/interfaces:**
```
auto lo
iface lo inet loopback

auto wlan0
iface wlan0 inet DHCP
wireless-essid GIGABYTE
wireless-key s:1234567891
```

And this is what happens when I'm trying to connect:
```
root@xxxxx:~# sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                          
There is already a pid file /var/run/dhclient.wlan0.pid with pid 2065
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.1.3
Copyright 2004-2009 Internet Systems Consortium.
All rights reserved.
For info, please visit https://www.isc.org/software/dhcp/

Listening on LPF/wlan0/00:1d:e0:a6:30:2f
Sending on   LPF/wlan0/00:1d:e0:a6:30:2f
Sending on   Socket/fallback
Error for wireless request "Set Encode" (8B2A) :
    SET failed on device wlan0 ; Invalid argument.
Internet Systems Consortium DHCP Client V3.1.3
Copyright 2004-2009 Internet Systems Consortium.
All rights reserved.
For info, please visit https://www.isc.org/software/dhcp/

Listening on LPF/wlan0/00:1d:e0:a6:30:2f
Sending on   LPF/wlan0/00:1d:e0:a6:30:2f
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 21
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
[COLOR="Red"]No DHCPOFFERS received.
No working leases in persistent database - sleeping.[/COLOR]
```

How can i get this fixed? I'l post any info requested.

Thanks in advance.

---

### Post by chili555 on 2011-02-16
First and foremost, manual methods will be very difficult and, prehaps impossible to connect if Network Manager is installed and running. If you want to use them, remove NM and reboot. Otherwise, remove the wlan0 lines from /etc/network/interfaces and click the NM icon and connect.

Second, this should read dhcp, not DHCP; it makes a difference:> auto lo
iface lo inet loopback

auto wlan0
iface wlan0 inet [COLOR="Red"]DHCP[/COLOR]
wireless-essid GIGABYTE
wireless-key s:1234567891Likewise, if your ESSID is Gigabyte or gigabyte and not GIGABYTE, you will never connect.

Last, your key is preceded with s: implying an ASCII key. These are rare, although not unknown. However, your example is ten characters long. ASCII keys are either five or thirteen keys long.

I understand and agree that you need to obscure your exact details, however, please double-check.

---

### Post by pareLi on 2011-02-16
There is some things that i forgot to mention in the sum-up. When i start the computer and the error occurs i get a few choices, but the only one who works is "exit to console". From there i use startx.
Network-Manager is supposed to work in startx right? No network-manager anywhere. Tried starting the service but not installed.. tried to install with dpkg but I failed.
Therefore i have to connect manually...

I've edited /etc/network/intefaces: (btw, the one i posted before was wrong, i just copied it from my other post so the /etc/network/interfaces looked almost like the one under but it contained s: infront of the key.
```

auto lo
iface lo inet loopback

auto wlan0
iface wlan0 inet dhcp
wireless-essid GIGABYTE
wireless-key 1234567891
wireless-channel 6
wireless-mode managed
```This is the key I have been using since i started using the router,
same key as I always used on xp64. Also the essid is correct.

Same outcome:
```
xxxxxxxxx:~$ sudo dhclient wlan0
[sudo] password for xxxxxxxxx:
There is already a pid file /var/run/dhclient.pid with pid 2440
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.1.3
Copyright 2004-2009 Internet Systems Consortium.
All rights reserved.
For info, please visit https://www.isc.org/software/dhcp/

Listening on LPF/wlan0/00:1d:e0:a6:30:2f
Sending on   LPF/wlan0/00:1d:e0:a6:30:2f
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 20
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
```**While typing the draft of this post it suddenly worked**, I typed in iwconfig and i saw something that made me wonder:

```
xxxxxxxxxxx:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11abg  ESSID:"[COLOR=Red]off/any[/COLOR]"
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated  
          Tx-Power=15 dBm  
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
```So i thought the reason was that I had used wireless-essid GIGABYTE instead of wireless-essid "GIGABYTE", but when changing that i got ESSID:""GIGABYTE"" and that must be wrong..
After changing back i tried dhclient wlan0, and voila it suddenly worked! :)

```

xxxxxxxxxxxxx:~$ sudo dhclient wlan0
[sudo] password for xxxxxxxxxx: 
There is already a pid file /var/run/dhclient.pid with pid 2492
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.1.3
Copyright 2004-2009 Internet Systems Consortium.
All rights reserved.
For info, please visit https://www.isc.org/software/dhcp/

Listening on LPF/wlan0/00:1d:e0:a6:30:2f
Sending on   LPF/wlan0/00:1d:e0:a6:30:2f
Sending on   Socket/fallback
DHCPREQUEST of 192.168.1.2 on wlan0 to 255.255.255.255 port 67
DHCPACK of 192.168.1.2 from 192.168.1.254
bound to 192.168.1.2 -- renewal in 20191 seconds.

```How did I fix this? I can't say that i did any major changes or anything.. Would be great if someone had any input on this since i really want to know how it got fixed.

---

