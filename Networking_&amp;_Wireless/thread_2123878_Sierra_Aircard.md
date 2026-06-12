---
title: "Sierra Aircard"
date: 2013-03-09
forum: Networking &amp; Wireless
---

### Post by aussielinuxguy on 2013-03-09
Hello,

 I have ubuntu 10.04 LTS on a spare hard drive and trying to connect my Sierra  4G Aircard 320U. 

I added my settings in the Network Manager but it won`t connect. I`m not sure how to setup this connection.

Any help apperciated.

This is what i have checked:

root@ubuntu:/home/derek# lsusb

```
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
[COLOR=#0000ff] Bus 001 Device 003: ID 0f3d:68aa Airprime, Incorporated [/COLOR]
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

root@ubuntu:/home/derek# ifconfig

```
eth0      Link encap:Ethernet  HWaddr 00:1c:23:9c:4d:0d   
          UP BROADCAST MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B) 
          Interrupt:18 

lo        Link encap:Local Loopback   
          inet addr:127.0.0.1  Mask:255.0.0.0 
          inet6 addr: ::1/128 Scope:Host 
          UP LOOPBACK RUNNING  MTU:16436  Metric:1 
          RX packets:76 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:76 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0 
          RX bytes:5840 (5.8 KB)  TX bytes:5840 (5.8 KB)

```

root@ubuntu:/home/derek# iwconfig

```
lo        no wireless extensions. 

eth0      no wireless extensions.
```

---

### Post by praseodym on 2013-03-09
Check here:

[http://www.simonsaysbiz.com/technology/telstra-4g-sierra-aircard-ubuntu-install/](http://www.simonsaysbiz.com/technology/telstra-4g-sierra-aircard-ubuntu-install/)

---

### Post by aussielinuxguy on 2013-03-09
praseodym,

 Thanks for that link, i will follow what it says and tell you how i go or if i have trouble.

---

### Post by aussielinuxguy on 2013-03-09
i need the file usb-modeswitch-data 20110227-1 but i cant find the right one to download.

---

### Post by praseodym on 2013-03-09
[http://packages.ubuntu.com/lucid/usb-modeswitch](http://packages.ubuntu.com/lucid/usb-modeswitch)

[http://packages.ubuntu.com/lucid/usb-modeswitch-data](http://packages.ubuntu.com/lucid/usb-modeswitch-data)

---

### Post by aussielinuxguy on 2013-03-09
Now i have them installed, i`ll try that link you gave me.

---

### Post by praseodym on 2013-03-09
usb-modeswith was updated significantly from Ubuntu 10.10 and on. So, maybe you try an updated version, maybe from 12.04. Remember, that the support for 10.04 ends in April!

---

### Post by aussielinuxguy on 2013-03-10
I have ubuntu 12.10 working now and trying to get connected to the net with that.

 That link you gave me to get connected, i followed it up until where it says, 

```
Now you&#8217;ll need to remove the module from the running kernel using:

rmmod usbserial
```

When i type rmmod usbserial as su, i get the Error:

```
ERROR: module usbserial in use by sierra

```
I`m not sure what to do now.

---

### Post by praseodym on 2013-03-10
Reboot to load the new module

---

### Post by aussielinuxguy on 2013-03-10
I did a reboot but no change. Tried to connect but still nothing.

 If i click on the Network Manager up the top, i can see the new connection i made from that link you gave me, but it is greyed out.

---

### Post by praseodym on 2013-03-10
Start the network-manager from terminal```

gksu nm-connection-editor
```

---

### Post by aussielinuxguy on 2013-03-11
praseodym,

 On the panel up the top, the icon next to the battery icon, which is the network connection manager. I can click on Edit Connections but my new one called Telstra LTE is greyed out and i can`t click on it.

That`s the new connection i made with the link you gave me. Wonder why it is greyed out, any ideas ?

If i could take a screenshot i can show you what i mean.

---

