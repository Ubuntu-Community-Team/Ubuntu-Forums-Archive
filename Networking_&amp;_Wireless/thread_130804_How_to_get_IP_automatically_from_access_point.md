---
title: "How to get IP automatically from access point?"
date: 2006-02-15
forum: Networking &amp; Wireless
---

### Post by Paloseco on 2006-02-15
I have succesfully configured a wireless network with WPA. Each time I start ubuntu or I reconnect I have to do "dhclient eth0". Is there any way to automatically get IP from access point at the startup of ubuntu and each time I disconnect/reconnect to the network? wpa_supplicant always reconnects correctly.

This is my configuration:
[http://ubuntuforums.org/showthread.php?t=128043](http://ubuntuforums.org/showthread.php?t=128043)

---

### Post by jrb114 on 2006-02-15
I think you need to put 

```
 auto eth0 
```

(where eth0 refers to your network adaptor) in your /etc/network/interfaces

This tells the system to automatically configure eth0 on boot. (You've got it for loopback and eth1 (which you say doesn't exist, so you could remove).)

J

---

### Post by Paloseco on 2006-02-15
[QUOTE=jrb114]I think you need to put 

```
 auto eth0 
```

(where eth0 refers to your network adaptor) in your /etc/network/interfaces

This tells the system to automatically configure eth0 on boot. (You've got it for loopback and eth1 (which you say doesn't exist, so you could remove).)

J[/QUOTE]
That does not work. For some reason seems that /etc/network/interfaces has nothing to do with dhclient. :-k

---

### Post by mips on 2006-02-15
[QUOTE=Paloseco]That does not work. For some reason seems that /etc/network/interfaces has nothing to do with dhclient. :-k[/QUOTE]

iface eth0 inet dhcp

---

### Post by Paloseco on 2006-02-15
[QUOTE=mips]iface eth0 inet dhcp[/QUOTE]I am afraid that does not work either. Note that each time I change a configuration file I restart the entire operating system in order to check wheter connects at the beginning or not. Maybe there is a bug or something, is imposible to get working this.

---

### Post by Lambert on 2006-02-15
Let me expand on what jrb114 said about auto eth0

During boot, /etc/init.d/networking is started. When that script is called on it runs the command ifup -a. What this does is reads the /etc/network/interfaces file and brings up any interface with the auto xxxx stanza.

So adding auto eth0 should start it at boot but it's not.

So here's a test, after boot run these commands.

sudo ifconfig eth0 down
sudo ifup -a

and see if you have connection.

---

### Post by Paloseco on 2006-02-15
This is what is shown. If I run "ifconfig eth0 down" I get offline. Aparently the same IP is kept. Then I do "dhclient eth0" and then kwireless manager says that the IP is unavailable. Then I do "ifup -a" I get connected to wifi, but I have to do "dhclient eth0" again in order to get connected. It was supposed that ifup gets automatically the IP from the access point.

> root@ubuntu:~# ifup -a
/etc/network/interfaces:22: misplaced option
ifup: couldn't read interfaces file "/etc/network/interfaces"
root@ubuntu:~# /etc/init.d/networking
Usage: /etc/init.d/networking {start|stop|restart|force-reload}
root@ubuntu:~# /etc/init.d/networking stop
 * Deconfiguring network interfaces...                                                                                                                                /etc/network/interfaces:22: misplaced option
ifdown: couldn't read interfaces file "/etc/network/interfaces"
                                                                                                                                                               [fail]
root@ubuntu:~# /etc/init.d/networking start
 * Configuring network interfaces...                                                                                                                                  /etc/network/interfaces:22: misplaced option
ifup: couldn't read interfaces file "/etc/network/interfaces"
                                                                                                                                                               [fail]
root@ubuntu:~# /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                                                                                                                /etc/network/interfaces:22: misplaced option
ifdown: couldn't read interfaces file "/etc/network/interfaces"
/etc/network/interfaces:22: misplaced option
ifup: couldn't read interfaces file "/etc/network/interfaces"
The line 22 has:
> pre-up /etc/init.d/wpasupplicant restart

---

### Post by Lambert on 2006-02-15
What happens if you change restart to start on line 22

then run the commands again from my last post.

---

### Post by Paloseco on 2006-02-15
Exactly the same. "Ifup -a" does not ask for a new IP after reconnecting.

> root@ubuntu:~# ifconfig eth0 down
root@ubuntu:~# ifup -a
/etc/network/interfaces:22: misplaced option
ifup: couldn't read interfaces file "/etc/network/interfaces"
root@ubuntu:~# ping -c 4 [www.ubuntulinux.com](www.ubuntulinux.com)
ping: unknown host [www.ubuntulinux.com](www.ubuntulinux.com)
root@ubuntu:~# dhclient eth0
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

/etc/dhcp3/dhclient.conf line 1: no option named dhcp-class-identifier
send dhcp-class-identifier "NetcfgDHClient"
     ^
/etc/dhcp3/dhclient.conf line 1: semicolon expected.

^
Listening on LPF/eth0/00:13:ce:4c:d2:50
Sending on   LPF/eth0/00:13:ce:4c:d2:50
Sending on   Socket/fallback
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPACK from 10.3.1.2
bound to 10.20.46.190 -- renewal in 21594 seconds.
root@ubuntu:~# ping -c 4 [www.ubuntulinux.com](www.ubuntulinux.com)
PING [www.ubuntulinux.com](www.ubuntulinux.com) (82.211.81.166) 56(84) bytes of data.
From 10.20.40.1 icmp_seq=1 Packet filtered
From 10.20.40.1 icmp_seq=2 Packet filtered
From 10.20.40.1 icmp_seq=3 Packet filtered
From 10.20.40.1 icmp_seq=4 Packet filtered

--- [www.ubuntulinux.com](www.ubuntulinux.com) ping statistics ---
4 packets transmitted, 0 received, +4 errors, 100% packet loss, time 3002ms


---

### Post by Lambert on 2006-02-15
See if this page helps. Look for the section "integration with dhcp"

[https://wiki.ubuntu.com/WPAHowto](https://wiki.ubuntu.com/WPAHowto)

---

### Post by Paloseco on 2006-02-15
I had read that wiki already. My wpa_action looks like that:

> #! /bin/bash 

  IFNAME=$1
  CMD=$2

  if [ "$CMD" == "CONNECTED" ]; then
    SSID=`wpa_cli -i$IFNAME status | grep ^ssid= | cut -f2- -d=`
    logger "WiFi: Connecting `$IFNAME' to network `$SSID'"
    ifup $IFNAME
  elif [ "$CMD" == "DISCONNECTED" ]; then
    logger "WiFi: Disconnecting `$IFNAME'"
    ifdown $IFNAME
  fi

And then I added another line to start dhclient (I think you meant that) but does not refresh the neither.
> #! /bin/bash 

  IFNAME=$1
  CMD=$2

  if [ "$CMD" == "CONNECTED" ]; then
    SSID=`wpa_cli -i$IFNAME status | grep ^ssid= | cut -f2- -d=`
    logger "WiFi: Connecting `$IFNAME' to network `$SSID'"
    ifup $IFNAME
    sleep 2
    dhclient  $IFNAME
  elif [ "$CMD" == "DISCONNECTED" ]; then
    "WiFi: Disconnecting `$IFNAME'"
    ifdown $IFNAME
  fi

I have found something interesting here:
[http://lists.shmoo.com/pipermail/hostap/2006-February/012501.html](http://lists.shmoo.com/pipermail/hostap/2006-February/012501.html)

---

### Post by Lambert on 2006-02-16
Not sure but have one more suggestion to test.

This won't work on boot, this is just to test that line 22 error and ifup

comment out the pre-up lines in the interface file, so the only lines you should have for the interface are.

iface eth0 inet dhcp
auto eth0

make sure interface is down

  sudo ifconfig eth0 down

start wpa supplicant

  sudo /etc/init.d/wpasupplicant start (or restart)

now run

  sudo ifup -a

test your connection

---

### Post by Paloseco on 2006-02-16
Doing what you say the connection will not work again. "ifconfig eth0 down" does not shut down neither wpasupplicant nor wpa_action. After restarting /etc/init.d/wpasupplicant I connect to wifi and after doing "ifup -a" I still cannot connect. Firefox says "Unable to find the proxy server". After doing "dhclient eth0" I have network again. 

After that I have updated the entire system thru adept and now I get connected to wifi after booting up. Also, if I disconnect with Fn+Wifi_card_key and I enter the combination again a minute later, after about 20 seconds I have network running. Now I have realized that an instance of dhclient is running. I do not know, but I think that before updating that did not happen.

> root@ubuntu:~# ps aux | grep dh
dhcp      3613  0.0  0.1   2336   760 ?        Ss   20:41   0:00 dhclient3 -pf /var/run/dhclient.eth0.pid -lf /var/lib/dhcp3/dhclient.eth0.leases eth0
root      4016  0.0  0.1   1896   660 ?        Ss   20:41   0:00 /sbin/dhcdbd --system
dhcp      5367  0.0  0.1   2336   760 ?        Ss   20:51   0:00 dhclient eth0
dhcp      5482  0.0  0.1   2340   540 ?        Ss   20:57   0:00 dhclient eth0
root      5560  0.0  0.1   2904   860 pts/1    S+   21:03   0:00 grep dh


NOTES:
When booting ubuntu shows "starting nfs statd" for lot of time.
I am connecting to a newtork that has multiple access points to access to the same network. I move to different parts of the building and automatically reconnects to the other access point thru a different channel (frecuency), so now seem that everything works ok.

---

