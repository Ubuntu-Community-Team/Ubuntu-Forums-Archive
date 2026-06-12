---
title: "not finding the network adaptor?"
date: 2012-04-30
forum: Networking &amp; Wireless
---

### Post by jw1496 on 2012-04-30
I recently upgraded to ubuntu 12.04 only to find my screen flickering horribly and so decided to reinstall 11.10.  This worked fine but something I have done has made the computer not recognise that my network cable is plugged in on startup.  I can only get it to work by opening terminal and typing sudo killall NetworkManager.  Then it works fine.

Any advice would be appreciated.
I am a linux novice so be kind!!

---

### Post by uylug on 2012-04-30
Restart your computer so the error is replicated, and then run:

```

ifconfig
```

and
```

ifconfig -a
```

Post the output here.

---

### Post by jw1496 on 2012-04-30
here's the output...

jonathan@jonathan-oboe:~$ ifconfig
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:224 errors:0 dropped:0 overruns:0 frame:0
          TX packets:224 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:17264 (17.2 KB)  TX bytes:17264 (17.2 KB)

jonathan@jonathan-oboe:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:1a:4d:85:84:e0  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:632 (632.0 B)  TX bytes:850 (850.0 B)
          Interrupt:41 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:304 errors:0 dropped:0 overruns:0 frame:0
          TX packets:304 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:23776 (23.7 KB)  TX bytes:23776 (23.7 KB)

---

### Post by uylug on 2012-04-30
Yeah, your ethernet is disabled.

Try this command:

```
sudo ifup eth0
```Also, what is the output of:
```

cat /etc/network/interfaces
```

---

### Post by jw1496 on 2012-04-30
Do you want me to reboot and do that with the error present or now while its working OK?

---

### Post by jw1496 on 2012-04-30
here is the output with the system up and running

jonathan@jonathan-oboe:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback

---

### Post by jw1496 on 2012-05-01
and here is the output from the ifup command when I ran it just now after restarting the system...

sudo ifup eth0
Ignoring unknown interface eth0=eth0.

not very helpful!

---

### Post by jw1496 on 2012-05-03
Hello.... Is anybody there?

---

### Post by uylug on 2012-05-30
Sorry for not getting back to you... have you fixed this?

---

