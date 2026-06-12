---
title: "Realtek RTL8168C dreiver refuse to work"
date: 2011-04-28
forum: Networking &amp; Wireless
---

### Post by ilya222 on 2011-04-28
[11.04 64 bit amd tx2500]
It seems ububtu is going backwards on driver support,
in 10.04 the driver support of my HP tx2500 was flawless,
and now the wired and wifi connections won't work:
ubunu does no recognize there is any wifi adapter, and the wired connection tries to connect and fails.
I installed the latest driver from realtek manually and no change.

---

### Post by aibarz on 2011-05-04
Good morning,

Same problem here. After update to ubuntu 11.04 from 10.10 ethernet card don't adquire IP address (dhcp active)

HW Info related:
Gigabyte MA785GT-UD3H with realtek gigabit 8111C chip

Linux aibarz-linux 2.6.38-9-server #43-Ubuntu SMP Thu Apr 28 15:40:34 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux

02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)

kernel module loaded: r8169                  48022  0 

dmesg:
[   16.209651] r8169 0000:02:00.0: eth0: link down
[   16.209668] r8169 0000:02:00.0: eth0: link down

At the moment I using zd1211rw wlan dongle to connect.

---

### Post by aibarz on 2011-05-04
Problem solved.

It is cronical kernel mismatch due wrong kernel module loaded.

Following that [http://aplawrence.com/Linux/rtl811.html ]("http://aplawrence.com/Linux/rtl811.html") 

creating new module and then using:

insmod /lib/modules/2.6.38-9-server/kernel/drivers/net/r8168.ko

appear ethernet connection popup OK

Now surelly I have to blacklist r8169.ko module to prevent in future same problem.

---

### Post by ilya222 on 2011-05-04
no good.
now i have r8168 running, not 8169(blacklisted)
i tried this [http://ubuntuforums.org/showthread.php?t=1022411&highlight=r8168](http://ubuntuforums.org/showthread.php?t=1022411&highlight=r8168)
and this: [http://ubuntuforums.org/showthread.php?t=1692795&highlight=r8168](http://ubuntuforums.org/showthread.php?t=1692795&highlight=r8168)

and still no good!

---

### Post by aibarz on 2011-05-04
please post 

lsmod | grep r8

ifconfig

dmesg |grep eth

---

### Post by ilya222 on 2011-05-05
here it is:

> 
ilya@ubuntu:~$ lsmod | grep r8 
r8168                 182616  0 
ilya@ubuntu:~$ ifconfig 
eth0      Link encap:Ethernet  HWaddr 00:1e:68:cc:2d:56  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B) 
          Interrupt:43 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0 
          inet6 addr: ::1/128 Scope:Host 
          UP LOOPBACK RUNNING  MTU:16436  Metric:1 
          RX packets:84 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:84 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0 
          RX bytes:6320 (6.3 KB)  TX bytes:6320 (6.3 KB) 

ilya@ubuntu:~$ dmesg | grep eth 
[    1.412922] i2c-core: driver [adp5520] using legacy suspend method 
[    1.412924] i2c-core: driver [adp5520] using legacy resume method 
[    1.926144] eth%d: RTL8168B/8111B at 0xffffc9000033a000, 00:1e:68:cc:2d:56, IRQ 43 
[    2.003745] eth0: Identified chip type is 'RTL8168C/8111C'. 
[   16.606887] r8168: eth0: link down 
[   16.607431] ADDRCONF(NETDEV_UP): eth0: link is not ready 


---

