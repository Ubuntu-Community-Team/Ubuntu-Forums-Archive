---
title: "inconsistent wireless problems"
date: 2009-05-08
forum: Networking &amp; Wireless
---

### Post by guy9567 on 2009-05-08
Ok, so I'm having really weird problems with my wireless.  I'm duel booting jaunty (the lame way) and my internet will just stop working periodically.  It doesn't disconnect, my bitrate just drops to 0 for no reason, then will decide randomly to start back up again.  It makes it impossible to listen to internet radio, watch movies, etc.  I don't have this problem when running vista, and i really don't want to go back to vista, but this problem is infuriating.  I don't think it's firefox related because opera does the same thing.  i get stuck at "looking up ---.com" or "connecting to ---.com" in the status bar.  

I isntalled ndiswrapper and windows drivers, but that didn't fix it.  then i tried disabling IPV6 through firefox, but that didn't fix it.  then i tired disabling IPV6 through Ubuntu, but that didn't fix it.  

I've got a Broadcom wireless card on a hp dv2000 laptop.  I'm broadcasting from a trendnet n-router with tkip encryption.  i'm sure that's it's a software problem and not a hardware, network, or isp problem.  I've searched around and no one seems to have this problem.  I'd really appreciate any help with this since i've resigned myself to having failed at fixing it myself.  

Also, my connection to gchat in pidgin disconnects randomly, and its probably related, but if it's not, is there a way to fix that, too?  aim works fine always.

---

### Post by superprash2003 on 2009-05-09
post output of **ifconfig** from the terminal.try using opendns servers [http://www.prash-babu.com/2008/04/how-to-configure-dns-servers-in-linux.html](http://www.prash-babu.com/2008/04/how-to-configure-dns-servers-in-linux.html)

---

### Post by guy9567 on 2009-05-09
ok, i tried opendns servers and it seemed to work at first, but then it started acting up again.  I truly appreciate the help, but do you have any other suggestions?

the output from ifconfig is as follows:

eth0      Link encap:Ethernet  HWaddr 00:16:d3:a4:c8:79  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 Base address:0x4000 

eth1      Link encap:Ethernet  HWaddr 00:1a:73:6f:fe:93  
          inet addr:192.168.1.197  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21a:73ff:fe6f:fe93/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:36708 errors:0 dropped:0 overruns:0 frame:42734
          TX packets:21964 errors:6 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:46839216 (46.8 MB)  TX bytes:2484709 (2.4 MB)
          Interrupt:19 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:608 (608.0 B)  TX bytes:608 (608.0 B)

---

### Post by superprash2003 on 2009-05-10
you could try changing MTU values although 1500 should be fine . [http://www.prash-babu.com/2008/06/how-to-change-mtu-values-in-linux.html](http://www.prash-babu.com/2008/06/how-to-change-mtu-values-in-linux.html)

---

### Post by guy9567 on 2009-05-10
I went to change my mtu values and the contents of /etc/network/interfaces read:

auto lo
iface lo inet loopback

I assume that since i'm connected through eth1 that it should read as such, so should I change this file to something like

iface eth1 inet dhcp
mtu 1492 

or is there something else that would help?

Thanks again-
****

---

### Post by superprash2003 on 2009-05-11
yes.. add an auto eth1 line also..

---

### Post by guy9567 on 2009-05-13
Was I supposed to append to the file or replace it?  either way, i tired both, and both times my wireless manager refused to work when i rebooted.  if i did iwlist scan, i could still see the networks i wanted to connect to, but i wasn't able to do so.  is there a way around that or is there a way to connect without having the wireless manager see anything?

---

