---
title: "Wireless doesn't work until 5+ minutes after boot"
date: 2013-04-23
forum: Networking &amp; Wireless
---

### Post by walth on 2013-04-23
Hi everyone,

While booting it always says "Waiting for networking" then "waiting an additional 60 seconds".  After those fail I can login and then do 'sudo start network-manager' and it works.  The funny thing is if I just wait a few additional minutes it will just work. 

How do I go about figuring out what is taking so long?

Thanks

---

### Post by matt_symes on 2013-04-23
Hi

This may be dbus issue or something similar but let's start with some other checks.

Can you post the output of

```
ifconfig
```

and 

```
cat /etc/network/interfaces
```

Kind regards

---

### Post by walth on 2013-04-24
> **matt_symes said:**
> Hi

This may be dbus issue or something similar but let's start with some other checks.

Can you post the output of

```
ifconfig
```

and 

```
cat /etc/network/interfaces
```

Kind regards

```

:~$ ifconfig 
eth0      Link encap:Ethernet  HWaddr bc:5f:f4:44:64:8f  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1907 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1907 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:207321 (207.3 KB)  TX bytes:207321 (207.3 KB)

ra0       Link encap:Ethernet  HWaddr c8:d3:a3:09:ed:63  
          inet addr:192.168.2.244  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::cad3:a3ff:fe09:ed63/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:864727 errors:0 dropped:0 overruns:143 frame:143
          TX packets:197918 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:648058291 (648.0 MB)  TX bytes:23760880 (23.7 MB)
```

```

:~$ iwconfig 
ra0       Ralink STA  ESSID:"Wash"  Nickname:"RT2870STA"
          Mode:Managed  Frequency=5.18 GHz  Access Point: 74:44:01:93:35:69   
          Bit Rate=19.5 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=86/100  Signal level:-75 dBm  Noise level:-90 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

lo        no wireless extensions.

eth0      no wireless extensions.
```

```

:~$ cat /etc/network/interfaces 
auto lo ra0
iface lo inet loopback
iface ra0 inet dhcp

```

This is a USB wireless device also.   I also seem to have issues getting this machine to connect if I turn on WPA.  My laptop works perfectly (also running LTS) but my desktop only works if security is set to none.  Where I live it's not a big deal to not have WPA turned on but I'd still prefer it.

---

### Post by matt_symes on 2013-04-24
Hi

I take it you are using network manager to manage your wireless ?

If so then why do you have references to ra0 (your wireless interface) in your interfaces file ?

```
 
auto lo ra0 
iface lo inet loopback 
iface ra0 inet dhcp
```

This could very well be the cause of your problems and if network manager is controlling your interfaces then these references should not be there.

Remove them and reboot and see if you still get the same problem.

The file (/etc/network/interfaces) should look like this.

```
  
auto lo
iface lo inet loopback
```

Post back if you need instruction on how to gain elevated privileges to edit the file.

Post back on efficacy.

EDIT:

> My laptop works perfectly (also running LTS) but my desktop only works  if security is set to none.  Where I live it's not a big deal to not  have WPA turned on but I'd still prefer it.

This may be a separate issue

Kind regards

---

### Post by walth on 2013-04-25
That's exactly what it was.  Thanks!

---

