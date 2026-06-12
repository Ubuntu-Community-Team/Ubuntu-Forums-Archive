---
title: "Can't connect to one particular network on laptop"
date: 2010-03-19
forum: Networking &amp; Wireless
---

### Post by wanichan on 2010-03-19
I run Ubuntu 9.04 on a Toshiba NB205. I am suddenly having trouble connecting to the internet using my router or my cable modem for that matter. 

The weird thing is that I can:

(1) connect to other networks just fine, and
(2) my router/internet connection work fine when plugged into my desktop.

I can't connect whether I'm plugged in with the ethernet cable directly from my modem or from my router, although both work fine when plugged into my desktop. Basically two green lights show up on networkmanager but it doesn't go from there to connecting. :confused:
 
So the usual troubleshooting of moving the wires around and trying to connect like that just suggested that my laptop doesn't connect on the one router/internet connection that I happen to need.

sudo ifconfig 
gives:
eth0 Link encap:Ethernet HWaddr xxxxxxxxx
UP BROADCAST MULTICAST MTU:1500 Metric:1
RX packets: 0 errors:0 dropped:0 overruns:0 frame:0
TX packets: 0 errors:0 dropped:0 overruns:0 carrier:0
collision:0 txqueuelen:1000
RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)
Interrupt:250 Base address:0xc000

Thank you for your help!

---

### Post by jobix on 2010-03-19
From the ifconfig output, your interface is not getting assigned an IP address. Normally, it should've looked something like:

> eth0      Link encap:Ethernet  HWaddr xxxxxxxxxx  
          inet addr:192.168.1.10  Bcast:192.168.1.255  Mask:255.255.255.0

Try executing an "ifdown eth0" followed by an "ifup eth0" and see if that works. Also check the system logs. You could also try "/etc/init.d/networking restart". Might need to execute all these commands as "sudo".

---

### Post by wanichan on 2010-03-20
> **jobix said:**
> 
Try executing an "ifdown eth0" followed by an "ifup eth0" and see if that works. Also check the system logs. You could also try "/etc/init.d/networking restart". Might need to execute all these commands as "sudo".

Thanks for that. I tried ifdown eth0 followed by ifup eth0 and alls I get is "ifdown: interface not configured" and "Ignoring unknown interface eth0=eth0". Also tried networking restart and it showed "reconfiguring network interfaces..." but nothing changed. 

Looking under gconf-editor there didn't seem anything out of the ordinary on that connection, but I still can't get assigned an ip addressed.

---

### Post by Iowan on 2010-03-20
I had a [similar]("http://ubuntuforums.org/showthread.php?t=1156441") problem (also on a Jaunty laptop) that went away when I disabled rfc3442 - but a Karmic workstation is working with it enabled.

---

### Post by wanichan on 2010-03-20
So I tried editing the dhclient.conf file as suggested (commenting out the option rfc3442 line and removing the rfc3442 thing in the request line, but the problem persists. Thanks for the suggestion, tho.

---

### Post by wanichan on 2010-03-20
Well I'll be darned; I updated the firmware on the old router and everything is back to working for now - wlan0 has an ip address with it. Thanks for all your help!!!

---

