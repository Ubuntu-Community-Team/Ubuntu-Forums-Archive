---
title: "Ubuntu 11.04: Realtek 8111E goes up and down"
date: 2011-08-28
forum: Networking &amp; Wireless
---

### Post by eterevsky on 2011-08-28
I've recently upgrade my machine. Its new motherboard is Asus M5A99X EVO on AMD 990X chipset with Realtek 8111E network adapter. It happens to work very unreliable, constantly going up and down. Here's statistics for the ping to my router:
```
--- 192.168.1.1 ping statistics ---
1811 packets transmitted, 425 received, +450 errors, 76% packet loss, time 1810688ms
rtt min/avg/max/mdev = 0.425/54226.891/135009.216/33394.639 ms, pipe 135
```
Here's ifconfig output:
```
eth2      Link encap:Ethernet  HWaddr 14:da:e9:03:df:e0  
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::16da:e9ff:fe03:dfe0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:743552 errors:0 dropped:743553 overruns:0 frame:743553
          TX packets:1085038 errors:0 dropped:4440 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:486989281 (486.9 MB)  TX bytes:1147865202 (1.1 GB)
          Interrupt:72 Base address:0x4000 
```
dmesg output looks like this:
```
...
[44006.000141] r8169 0000:02:00.0: eth2: link up
[44006.970126] r8169 0000:02:00.0: eth2: link up
[44009.200095] r8169 0000:02:00.0: eth2: link up
[44010.810172] r8169 0000:02:00.0: eth2: link up
[44011.600110] r8169 0000:02:00.0: eth2: link up
[44020.580189] r8169 0000:02:00.0: eth2: link up
[44024.720162] r8169 0000:02:00.0: eth2: link up
[44074.410206] r8169 0000:02:00.0: eth2: link up
[44079.440121] r8169 0000:02:00.0: eth2: link up
[44088.560161] r8169 0000:02:00.0: eth2: link up
[44101.040127] r8169 0000:02:00.0: eth2: link up
[44146.000170] r8169 0000:02:00.0: eth2: link up
...
```
I have 2.6.38-11-generic kernel. The same adapter works fine on Windows, so it doesn't seem to be a hardware problem. The router also works fine.

---

### Post by bkratz on 2011-08-28
When you do

lspci

(that is LSPCI in lowercase) does it show up something like RTL8111/RTL8168 or some variation of same? If so, check lsmod (LSMOD in lowercase) and if module r8169 or r8168 shows up). It is common for the system to try and drive that card with r8169 which is actually the wrong driver. If r8168 shows up it is something else. If r8169 see this link

[http://ubuntuforums.org/showthread.php?t=1022411&highlight=8168](http://ubuntuforums.org/showthread.php?t=1022411&highlight=8168)

Just noticed dmesg--go ahead and see the link!

---

### Post by Cripton on 2011-09-29
that post is preety old, this is how i do it:
```
lsmod | grep r816
```
you get something like this: 
```
r8169                  48022  0
```
```
sudo -s
rmmod r8169
mv /lib/modules/`uname -r`/kernel/drivers/net/r8169.ko ~/r8169.ko.backup
```
download and extract the driver for linux from [realtek]("http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=13&PFid=5&Level=5&Conn=4&DownTypeID=3&GetDown=false#2")
```
cd r8168-8.025.00/
./autorun.sh
```
and you are up and running ;)
check the module again
```
lsmod | grep r816
```
you get something like this: 
```
r8168                 203096  0
```

---

### Post by nvv on 2012-01-06
I also have a M5A99X EVO, and I can confirm that the method as outlined by Cripton works fine.
In my case for opensuse 11.4
Just make sure that you have the kernel sources, make and gcc installed

Nico

---

