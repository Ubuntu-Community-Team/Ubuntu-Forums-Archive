---
title: "New kernel Update (Wifi stops working)"
date: 2009-06-23
forum: Networking &amp; Wireless
---

### Post by smithwaysecurity on 2009-06-23
Hello everyone I just ran a update last night at it installed the newest kernel root@CIA-laptop:~# 
2.6.28-13-generic and after that I shutdown my laptop for the night and in the morning when I booted up my wifi was'nt working i been trying all day to fix but i can't find the issue it's running 9.04 ubuntu atheros card also I got the madwifi drivers installed. so it's like my wifi been disbaled or somthing I don't know if ther a bug in the kernel or not.

card not being dectected in wifi manger or ifconfig or iwconfig 

james@CIA-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1f:16:4e:d9:06  
          inet addr:192.168.0.103  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::21f:16ff:fe4e:d906/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:123841 errors:0 dropped:0 overruns:0 frame:0
          TX packets:74690 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:173036794 (173.0 MB)  TX bytes:6951342 (6.9 MB)
          Interrupt:253 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:100 errors:0 dropped:0 overruns:0 frame:0
          TX packets:100 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:7968 (7.9 KB)  TX bytes:7968 (7.9 KB)

james@CIA-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

also the laptop is a Hp G60 and I have checked the fourm for that laptop that new and ther was'nt anything.

---

### Post by x22 on 2009-06-23
the kernel drivers ath5k/ath9k are preferred these 
days: try "modprobe ath5k"

if not found, then you goto /usr/src/linux, and arrange
in the usual way for the module to be compiled: and *then*
do "modprobe ath5k"

ps: good spelling is always appreciated by readers

---

### Post by smithwaysecurity on 2009-06-24
hey x22 I tried what you said and still my wireless card not being listed or in the connection manger.
so you got any other ideas that might work?

---

### Post by Gladk on 2009-07-04
I have exactly the same problem. I have Dell Inspiron 1501.
WiFi AND network card does not work at 2.6.28.13

Can anybody advice me how to fix it?

---

### Post by Gladk on 2009-07-05
[http://georgia.ubuntuforums.org/showpost.php?p=7506946&postcount=18](http://georgia.ubuntuforums.org/showpost.php?p=7506946&postcount=18)
Post #18 solved my problem

```

sudo /sbin/lrm-manager
sudo modprobe wl

```

Thank you all!

---

### Post by Aearenda on 2009-07-05
If you had the madwifi driver installed by compiling from the latest version yourself, then you need to rebuild it for each new kernel version that is installed. Make sure you have the kernel headers that correspond to your new kernel installed as well (it should be automatic unless you catch the updates just as the kernel is issued but before the headers are done), then do this:```
cd <where you put the madwifi source>
make clean
make
sudo make install
```

PS: If you can't get it to work, don't forget you can drop back to the previous kernel from the Grub menu at boot time.

---

### Post by webabun on 2009-07-05
Hi,

I managed to get wireless back to work by combining tips from other users

1- as Aearenda said in this topic, log on using previous kernel (.11 in my case)

2- than - as stated in several other topics - goto 
system -> network connections -> Wireless and choose <manual> = fixed IP _and_ fill in DNS from your provider

After that Networkmanager applet asked me to connect to network -> work fine

Reboot and use newer kernel (in working with .13 right now)

---

### Post by dBuster on 2009-07-05
> **Aearenda said:**
> If you had the madwifi driver installed by compiling from the latest version yourself, then you need to rebuild it for each new kernel version that is installed. Make sure you have the kernel headers that correspond to your new kernel installed as well (it should be automatic unless you catch the updates just as the kernel is issued but before the headers are done), then do this:```
cd <where you put the madwifi source>
make clean
make
sudo make install
```

PS: If you can't get it to work, don't forget you can drop back to the previous kernel from the Grub menu at boot time.


When ever I get a kernel update no matter if it is a small one or a full update I have to do as Aearenda states to get my wifi back but I have to sudo the makes in order to get it to run without error...

But they do work.  Just wish there was a way to have the support for the atheros in the kernel so we do not have to compile the drivers each time!

---

### Post by Gladk on 2009-07-05
> **zostay said:**
> I ended up with a different solution. It would appear that something went awry during the install of a package or something. I ran:

```
sudo /sbin/lrm-manager
sudo modprobe wl
```The FATAL message I was getting, was apparently an indicator that that command had not been run successfully after the install (or so I guess, since I don't understand what that command does :P).

It helped me

---

### Post by Aearenda on 2009-07-05
> **dBuster said:**
> Just wish there was a way to have the support for the atheros in the kernel so we do not have to compile the drivers each time!
As ath5k becomes more stable, this will happen.

---

