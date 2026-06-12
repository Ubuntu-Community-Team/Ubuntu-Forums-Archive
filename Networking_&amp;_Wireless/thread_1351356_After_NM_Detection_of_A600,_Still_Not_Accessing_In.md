---
title: "After NM Detection of A600, Still Not Accessing Internet."
date: 2009-12-10
forum: Networking &amp; Wireless
---

### Post by pdc7 on 2009-12-10
Hi everyone,

Although I am new here as a registered user, I have been here many times in the past couple years and learned much.  So first off, I want to express my gratitude for this forum and what it stands for.

I bought a Cricket A600 USB modem (which is also a USB memory drive) after checking to see if it was possible to use with Ubuntu.  Based on these forums, I bought it.

I followed the instructions to the letter, installing the usbmodeswitch .deb file and then implementing the command in terminal "sudo ./flipflop.sh".

And *voila!*  Network Manager detects the modem (" Cricket Communications").  However, when I open a browser (Epiphany, Opera, Chrome, Firefox, Konqueror, etc), the browser tells me I am _not _connected to the Internet.

I have tried to "edit" the Cricket connection in NM (to include phone number, username, password), but those changes don't seem to stick.

I then tried Gnome PPP, but it won't detect my modem (even after I do "sudo ./flipflop.sh") and I don't know how to add a modem to its selections, so I am stuck with the usual tty's they offer.

I am not too keen on Terminal use, so if there is a GUI method with minimal command line, I would be grateful.

Thank-you in advance!

---

### Post by uncaspi on 2009-12-10
Open a terminal after you are connected to the modem using NM. Post the printout of netstat -r and sudo /sbin/ifconfig   please.

---

### Post by pdc7 on 2009-12-10
Thank-you, uncaspi, for your quick reply.

I turned off wi-fi and bluetooth before doing this.

I wasn't sure how to do a "printout" so I just did copy/paste.  Also, I am on a Lenovo Ideapad S10 with 250GB HD and 1GB RAM. Here are the results you requested:

peter@lenovo-ideapad:~$ netstat -r
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
10.133.28.9     *               255.255.255.255 UH        0 0          0 ppp0
192.168.122.0   *               255.255.255.0   U         0 0          0 virbr0
link-local      *               255.255.0.0     U         0 0          0 ppp0
default         10.133.28.9     0.0.0.0         UG        0 0          0 ppp0
peter@lenovo-ideapad:~$ sudo /sbin/ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1e:68:af:66:90  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 

eth1      Link encap:Ethernet  HWaddr 00:23:4d:4e:51:21  
          inet6 addr: fe80::223:4dff:fe4e:5121/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:4041 errors:0 dropped:0 overruns:0 frame:9088
          TX packets:4061 errors:7 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2616051 (2.6 MB)  TX bytes:564387 (564.3 KB)
          Interrupt:18 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:498 errors:0 dropped:0 overruns:0 frame:0
          TX packets:498 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:234417 (234.4 KB)  TX bytes:234417 (234.4 KB)

ppp0      Link encap:Point-to-Point Protocol  
          inet addr:10.106.57.58  P-t-P:10.133.28.9  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:96 errors:0 dropped:0 overruns:0 frame:0
          TX packets:173 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:31542 (31.5 KB)  TX bytes:25205 (25.2 KB)

virbr0    Link encap:Ethernet  HWaddr 12:cf:6c:ad:d0:6a  
          inet addr:192.168.122.1  Bcast:192.168.122.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:72 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:8882 (8.8 KB)

Thanks for your help on this!

---

### Post by pdc7 on 2009-12-13
Just a little more info.  I'm using Ubuntu 9.10.  I noticed I didn't have network-admin installed, but I've taken care of that now.  However, even with network-admin installed, the problem persists.  The actual message that appears on the browsers is "Cannot resolve  hostname."

Is this basically a settings problem?  Any help, please?

---

### Post by pdc7 on 2010-01-15
Wow. I'm genuinely disappointed at the lack of help in this forum.  For a first-time participant (after years of being a passive reader and learner here), this has been a disillusionment for me.

Moving along, I went on holiday to New England for a few weeks.  Most of New England does not have Cricket service so I did not use the modem at all.  When I returned to Colorado, I plugged it in for kicks, and *voila la!* it works!!!

Not only that, but it works really well.  I get the same speeds as in Windows and it works automatically.  I don't need to key in " flipflop"  or anything!  Also, it works simultaneously as a USB drive, which is cool.  (Some forums said that in Linux it wouldn't be able to do both -- modem and storage drive -- but it does!)

So I don't know what I did or didn't do, if it was an update on the system (Ubuntu 9.10), or whatever.  It would be nice if somebody could explain it and post it here for the benefit of anybody else who comes to have this issue.

---

