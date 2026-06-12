---
title: "Suddenly internet stopped working?"
date: 2012-06-04
forum: Networking &amp; Wireless
---

### Post by boy18nj on 2012-06-04
I've been happy Ubuntu user since 2 years.

In my current ubuntu 12.04, toshiba satellite A215-7422,
after i installed dropbox, the internet stopped working.

Not necessarily it stopped because of dropbox, it's suspect. But i uninstalled it, but the internet still doesn't works.

The interesting thing is i can connect to my router either thru wireless or ethernet, it says connection established. the only problem is in chrome, it won't connect to internet.

I'm out of luck. Just to let know i never installed any modified drivers or anything my internet always works out of box in ubuntu.

Please note that the problem is not related to wireless or ethernet because connection is established in both just the internet is not working. My internet was working fine, it just suddenly stopped.

Please suggest fix or anyway to reset the internet thingy.

---

### Post by papibe on 2012-06-04
Hi boy18nj.

Could you post the result of these commands?
```
ifconfig

route -n

nslookup ubuntu.com

grep dnsmasq /etc/NetworkManager/NetworkManager.conf

cat /var/run/nm-dns-dnsmasq.conf
```
Regards.

---

### Post by boy18nj on 2012-06-04
Currently I'm away from laptop. In the evening, I'll reply.

Thank you very much for replying.

---

### Post by boy18nj on 2012-06-04
rocky@rocky-laptop:~/Desktop$ sh ./shsh.sh
eth0      Link encap:Ethernet  HWaddr 00:a0:d1:84:6d:d4  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:43 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:16:44:19:fd:42  
          inet addr:192.168.0.103  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::216:44ff:fe19:fd42/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:980 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1138 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:68102 (68.1 KB)  TX bytes:121909 (121.9 KB)

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 wlan0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlan0
192.168.0.0     0.0.0.0         255.255.255.0   U     2      0        0 wlan0
;; connection timed out; no servers could be reached

dns=dnsmasq
server=209.18.47.61
server=209.18.47.62
rocky@rocky-laptop:~/Desktop$

---

### Post by boy18nj on 2012-06-04
server=209.18.47.61
server=209.18.47.62


Please see attached. Let me know what to do next.

---

### Post by papibe on 2012-06-04
You missed one:
```
nslookup ubuntu.com
```

BTW, by any change this command solve your problem?
```
sudo service network-manager restart
```
Regards.

---

### Post by boy18nj on 2012-06-04
This is the output of nslookup command.
;; connection timed out; no servers could be reached

---

### Post by papibe on 2012-06-04
It looks like dnsmasq is not working properly. Check if disable it solve the problem.

Follow this [steps]("http://ubuntuforums.org/showpost.php?p=11923702&postcount=40"), and let us know how it goes.
Regards.

---

### Post by boy18nj on 2012-06-04
#dns=dnsmasq

I disabled it. Sorry it did not connected to internet.

What is next can be done?

---

### Post by boy18nj on 2012-06-04
It is intertesting I can surf my router link [http://192.168.0.1](http://192.168.0.1) but not internet itself wirelessly. Seems like something is blocking.

---

### Post by boy18nj on 2012-06-05
i read somewhere this command-

dig ubuntu.com

this give me the result connection timed out....server cannot be reached.

then i search the google, finded out i didnt have proper dns servers listed in /etc/resolv.conf



i saw this file was modified in my laptop yesterday since then the internet stopped working.

i corrected this file.

whola. the internet started working back. thank you very much, without it wasn't possible you give me enough pointers to look into problem.:guitar:

---

### Post by boy18nj on 2012-06-05
I also noticed disabling the #dns=dnsmasq increases my internet speed.

Not sure if it is proven thingy.

---

