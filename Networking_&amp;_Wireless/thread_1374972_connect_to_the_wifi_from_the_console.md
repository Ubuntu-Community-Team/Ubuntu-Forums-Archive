---
title: "connect to the wifi from the console"
date: 2010-01-07
forum: Networking &amp; Wireless
---

### Post by avi93 on 2010-01-07
hello,
is it possible to connect to my internet router from the console?
for some reasone my gnome envirment removed and i want to install it again...

any ideas how to do that?

Thanks!

***sorry for my english***

---

### Post by elliotbeken on 2010-01-07
i dont fully understand 

do you want to access the internet using a console cable connected to a router?

---

### Post by mdmarmer on 2010-01-07
Yes of course you can connect using console.

read here   [http://linux.die.net/man/8/iwconfig](http://linux.die.net/man/8/iwconfig)

common sequence is (if encryption is off)

iwconfig wlan0 essid YOURSSID channel YOURCHANNEL#
dhclient wlan0

Mike

---

### Post by avi93 on 2010-01-07
i tried this and i got an error "permissions denied"
 i also tried 
```
sudo iwconfig wlan0 essid avi1 
sudo iwconfig wlan0 key xxxxxxxxxx 
sudo ifconfig wlan0 up 
sudo dhclient3 wlan0 
```but i also getting an error here:
```



DHCPDISCOVER on wan0 to 255.255.255.255 port 67 interval 8 
DHCPDISCOVER on wan0 to 255.255.255.255 port 67 interval 14 
DHCPDISCOVER on wan0 to 255.255.255.255 port 67 interval 7 
DHCPDISCOVER on wan0 to 255.255.255.255 port 67 interval 17 
DHCPDISCOVER on wan0 to 255.255.255.255 port 67 interval 15 
No DHCPOFFERS received. 
No working leases in persistent database - sleeping. 
*Reloading /etc/samba/smb.con smbd only 
...done. 

```

---

### Post by mdmarmer on 2010-01-11
You need to make sure the kernel module for your wifi is loaded.

example:
modprobe ndiswrapper

if you use ifconfig to bring up the interface, do that before the iwconfig, thus:
(and you need to be root to issue these commands)

modprobe ndiswrapper
ifconfig wlan0 up
iwconfig
iwlist scan
iwconfig wlan0 essid YOURSSID channel YOURCHANNEL#
dhclient wlan0

Mike

---

### Post by mikeroe on 2010-01-11
Hey I think I'm having a similar problem.  I've been trying to learn more about the BASH terminal and CLI's  in general for a while now, but I am having an extremely difficult time trying to connect to a wireless network from the command line.  I've tried quite a few things, including all the steps on the last post, but every time I run:

sudo dhclient wlan0

i get the following:

Listening on LPF/wlan0/00:1b:77:61:9b:20
Sending on   LPF/wlan0/00:1b:77:61:9b:20
Sending on   Socket/fallback
DHCPREQUEST of 192.168.1.108 on wlan0 to 255.255.255.255 port 67
DHCPREQUEST of 192.168.1.108 on wlan0 to 255.255.255.255 port 67
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 15
No DHCPOFFERS received.
Trying recorded lease 192.168.1.108
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.

--- 192.168.1.1 ping statistics ---
1 packets transmitted, 0 received, +1 errors, 100% packet loss, time 0ms

No working leases in persistent database - sleeping.
 * Reloading /etc/samba/smb.conf smbd only
   ...done.

If anyone has any suggestions I would be thrilled to hear them.

Thanks

---

