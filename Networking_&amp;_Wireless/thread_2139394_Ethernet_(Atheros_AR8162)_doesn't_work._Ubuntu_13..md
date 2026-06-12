---
title: "Ethernet (Atheros AR8162) doesn't work. Ubuntu 13.04 and linux-backports-modules."
date: 2013-04-26
forum: Networking &amp; Wireless
---

### Post by Jot-z on 2013-04-26
I'm in dire need of linux-backports-modules because my wired connection doesn't work without it. Regrettably for me I installed new Ubuntu (13.04) today and found out that there's no linux-backports-modules in repository. In spite of my attempts, I couldn't find proper linux-backports-modules deb file. Please help me to find linux-backports-modules or solve the problem somehow.

joachim@J-Lenovo-G580:~$ lspci | grep Ethernet
03:00.0 Ethernet controller: Qualcomm Atheros AR8162 Fast Ethernet (rev 08)

joachim@J-Lenovo-G580:~$ ifconfig
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:1532 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1532 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:122895 (122.8 KB)  TX bytes:122895 (122.8 KB)
wlan0     Link encap:Ethernet  HWaddr 00:00:00:00:00:00  
          inet addr:192.168.1.100  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::466d:57ff:fe43:cad1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:8013 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6374 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4301341 (4.3 MB)  TX bytes:1954568 (1.9 MB)

joachim@J-Lenovo-G580:~$ iwconfig | grep eth0
eth0      no wireless extensions.

lo        no wireless extensions.

joachim@J-Lenovo-G580:~$ iwlist scan | grep eth
eth0      Interface doesn't support scanning.

lo        Interface doesn't support scanning.

joachim@J-Lenovo-G580:~$ lsb_release -d && uname -mr
Description:    Ubuntu 13.04
3.8.0-19-generic x86_64
________________________________________________________

I have managed to solve the problem with ethernet.

1. I downloaded compat drivers from [https://www.kernel.org/pub/linux/kernel/projects/backports/stable/v3.9-rc4/compat-drivers-3.9-rc4-2-su.tar.bz2](https://www.kernel.org/pub/linux/kernel/projects/backports/stable/v3.9-rc4/compat-drivers-3.9-rc4-2-su.tar.bz2)
2. Then I extracted and installed drivers using following commands:
cd compat-drivers-3.9-rc4-2-su
./scripts/driver-select alx
make
sudo make install
________________________________________________________

I have just found out that Ethernet isn't working despite successful compat drivers installation. At least it's detected now:

eth0      Link encap:Ethernet  HWaddr 00:00:00:00:00:00  
          inet addr:192.168.1.101  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::de0e:a1ff:fee5:26b7/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2712 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3848 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:1835428 (1.8 MB)  TX bytes:1417959 (1.4 MB)
          Interrupt:16

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:8511 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8511 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:581402 (581.4 KB)  TX bytes:581402 (581.4 KB)

wlan0     Link encap:Ethernet  HWaddr 00:00:00:00:00:00  
          inet addr:192.168.1.100  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::466d:57ff:fe43:cad1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1956 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1675 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:1442057 (1.4 MB)  TX bytes:303314 (303.3 KB)

When I disable Wi-Fi and try to open any website, server isn't found:
Server not found
Firefox can't find the server at [www.google.com]("http://www.google.com")

I have also tried to ping google.com:
joachim@J-Lenovo-G580:~$ ping google.com
ping: unknown host google.com

---

### Post by Jot-z on 2013-05-01
Can anyone help me, please?

---

### Post by ibrahim52 on 2013-05-02
Yes I can, Either you can visit the link below to check for the solution or you can simply follow the steps below.

```

wget https://www.kernel.org/pub/linux/kernel/projects/backports/2013/03/04/compat-drivers-2013-03-04-u.tar.bz2
./scripts/driver-select alx
make
sudo make install
reboot
```

Or you can do it manually by downloading compat-drivers-2013-03-04-u.tar.bz2 from the link above and extract it and then using terminal and follow the rest of the commands to make it work.

if you don't want to reboot then you can simply copy/paste the command below to make your ethernet work instantly.

```
sudo modprobe -r alx && sudo modprobe alx
```

---

### Post by ibrahim52 on 2013-05-02
in case you need any help PM me and inform so I update comment here.

---

### Post by Jot-z on 2013-05-02
Thank you very much. After installing drivers from compat-drivers-2013-03-04-u.tar.bz2, I can use wired connection but it's still a bit uncomfortable. When I resume my computer from suspend, I have to reboot or type "sudo modprobe -r alx && sudo modprobe alx" to be able to use Ethernet again. Maybe do you have any idea how it can be fixed?

Before suspend:
joachim@J-Lenovo-G580:~$ ifconfig 
eth0      Link encap:Ethernet  HWaddr 00:00:00:00:00:00
          inet addr:192.168.1.101  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::de0e:a1ff:fee5:26b7/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:25844 errors:0 dropped:0 overruns:0 frame:0
          TX packets:25798 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:20121839 (20.1 MB)  TX bytes:14139718 (14.1 MB)
          Interrupt:16 
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:7579 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7579 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:601943 (601.9 KB)  TX bytes:601943 (601.9 KB)

When computer is resumed from suspend:
joachim@J-Lenovo-G580:~$ ifconfig 
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:7594 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7594 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:602850 (602.8 KB)  TX bytes:602850 (602.8 KB)

I'm curious why compat-drivers-2013-03-04-u.tar.bz2 works but compat-drivers-3.9-rc4-2-su.tar.bz2 doesn't. How do you know which version of compat driver should be installed? I have been looking for information about choosing proper version and I have only found out that compat driver version should be newer than kernel version.

---

### Post by ibrahim52 on 2013-05-09
What is your kernel version by the way. Do "uname -r" in your terminal and post it here. if it is above 3.9 (ex:- 3.9.1) it won't work but in 3.9 its working fine for me.

---

### Post by Jot-z on 2013-05-09
My kernel version is still the same.

> **Jot-z said:**
> 
joachim@J-Lenovo-G580:~$ lsb_release -d && uname -mr
Description:    Ubuntu 13.04
3.8.0-19-generic x86_64


---

### Post by ibrahim52 on 2013-05-09
Follow the link below. Upgrade your kernel to 3.9 and try those above commands to install ethernet drivers.

[http://www.upubuntu.com/2013/04/installupgrade-to-linux-kernel-39.html](http://www.upubuntu.com/2013/04/installupgrade-to-linux-kernel-39.html)

---

### Post by ibrahim52 on 2013-05-11
had a terrible 3 days without ETHERNET but thank god i didn't faced any situation where I required CABLE but still I need it most of the time and finally after upgrading to KERNEL 3.9.1 when it didn't worked so tried the latest driver and you too can give it a try.

```
wget https://www.kernel.org/pub/linux/kernel/projects/backports/2013/03/28/compat-drivers-2013-03-28-5-u.tar.bz2
cd compat-drivers-2013-03-28-5-u
./scripts/driver-select alx 
make
sudo make install
```

---

### Post by sbrown5000 on 2013-06-13
I was having the same problem and installing the [FONT=Ubuntu Mono]compat-drivers-2013-03-04-u.tar.bz2 worked for me.  Thank you so much![/FONT]

---

### Post by Huli1984 on 2013-07-12
Hello to you all, I've passed to Ubuntu's world bout six months ago so I'm still a newbie and apparently got the same issue above. 
I tried the solution charging the drivers manually and it worked awesomly... till I rebooted. after the reboot even if I recompiled a new copy of the driver I could get working only the network with router and other pcs on the LAN. Nothing seems to work to let me be able to connect to internet again...  I checked the DNS and I tried to insert enjoy again with no use
thanks for help. 
also I'd be glad to get help for a out of the box compatible wifi USB adapter for Ubuntu 13.04.

---

