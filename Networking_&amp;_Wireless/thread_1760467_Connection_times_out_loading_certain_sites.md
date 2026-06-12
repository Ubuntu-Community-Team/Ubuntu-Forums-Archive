---
title: "Connection times out loading certain sites"
date: 2011-05-17
forum: Networking &amp; Wireless
---

### Post by x751 on 2011-05-17
I had recently installed Ubuntu 11.04 (64-bit) and I have trouble loading websites. I use a DSL (PPPoE) connection from NetworkManager to connect to the internet. Some sites like this forum site, stack overflow, etc. do not load. Firefox 4 says 'loading...' and then finally times out. I can ping these sites though.

I tried 'wget stackoverflow.com' and Lynx both timed out. wget sends out a request and waits a long time for response before timing out. These sites load perfectly well on my Fedora 14 (64-bit) & Windows XP installations and both these OSes have Firefox 4. From this I assumed that this is not a problem with Firefox (or any other browser for that matter) but it has got something to do with the network configuration.

I faced the same problem with Ubuntu 10.04 too. I use a Dell Inspiron N5010.

Has anybody faced such problems before? Any ideas?

---

### Post by ivanovnegro on 2011-05-17
I have this also from time to time, especially with Firefox in general, I have no real idea about this but I could imagine Firefox on Linux does this, with Chromium I had not this problems.

---

### Post by x751 on 2011-05-17
Actually, ivanovnegro, even Chrome has this issue for me. As I mentioned earlier, it is not a problem with the browser but with the layers below that.

---

### Post by Hoosie on 2011-06-06
I also have this problem over my wireless link, a Belkin54g. The problem does not exist over a wired connection. I am using an Asus Eee 901. This worked perfectly with Ubuntu 10.10. The problem started when I upgraded to 11.04. The problem is the same with Firefox 4.0.1 and Chrome.
Hope this additional small clue might help someone find an answer.

---

### Post by dineshs on 2011-06-07
Did you try 
1)Disabling[ ipv6]("http://support.mozilla.com/en-US/kb/Firefox%20cannot%20load%20websites%20but%20other%20programs%20can?redirectlocale=en-US&redirectslug=Firefox+cannot+load+web+sites+but+other+programs+can")?
2)Setting a different MTU via network manger?
3)Setting another DNS via network manager?
Can you post the output of ```
ifconfig -a
```

---

### Post by Hoosie on 2011-06-07
IPv6 does not have any effect. Other settings seem fine.
Checked if Ubuntu 11.04 has a firewall. This is switched off.

Listing of ifconfig below. I notice packet errors.  I get impression page would load eventually. In a very long time.

~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:22:15:8f:74:6a  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:1
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:44 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:480 (480.0 B)  TX bytes:480 (480.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:15:af:e6:ec:1d  
          inet addr:192.168.2.4  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::215:afff:fee6:ec1d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:16 errors:0 dropped:0 overruns:0 frame:0
          TX packets:49 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2160 (2.1 KB)  TX bytes:9999 (9.9 KB)


Regards

---

### Post by Hoosie on 2011-06-08
It now works. All the previously difficult pages now load quickly.
Not being a Ubuntu expert, I have lots to learn. Spent some time reading Ubuntu User iss9, section on Networking. The only action I took which may have changed something was to follow the tip:-  To request a DHCP address manually from the DHCP server, open a terminal and type:-       sudo dhclient -v             The server will then assign you a new IP address.

When I returned to Mozilla Firefox, every page loaded perfectly.

Will this work for others?

---

