---
title: "no networks detected in ubuntu 10.04"
date: 2010-12-28
forum: Networking &amp; Wireless
---

### Post by Joe9 on 2010-12-28
I installed ubuntu and i installed it using the install as a program inside windows options but when I boot into ubuntu it does not detect any networks I tried the command sudo pppoeconf it says ethernet card is not there and then it asked me to try modconf and when i try modconf it says that modconf is not installed How can i set internet connection in ubuntu 10.04 I get address assigned by DHCP

---

### Post by mikewhatever on 2010-12-28
I think you should start by posting detail on the nature of your internet connection. 

wired/wireless?
cable/dsl?

---

### Post by Joe9 on 2010-12-28
It is wired and is a cable connection :)

---

### Post by mikewhatever on 2010-12-28
Cable ISPs usually use direct connection or pptp. Do you use username and password from your ISP, or do you just plug the cable and it works? Run **ifconfig** in a Terminal window and post the output.

---

### Post by Joe9 on 2010-12-29
> **mikewhatever said:**
> Cable ISPs usually use direct connection or pptp. Do you use username and password from your ISP, or do you just plug the cable and it works? Run **ifconfig** in a Terminal window and post the output.Yes I have password and username for connecting I ran ifconfig and the output is as follows
 Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:720 (720.0 B)  TX bytes:720 (720.0 B)

---

### Post by mikewhatever on 2010-12-29
It looks like your networking hardware is unrecognized. Can you also post the output of the following.

```
sudo lshw -C network
```

---

### Post by Joe9 on 2010-12-29
> **mikewhatever said:**
> It looks like your networking hardware is unrecognized. Can you also post the output of the following.

```
sudo lshw -C network
```The output is
 *-network UNCLAIMED     
       description: Ethernet controller
       product: AR8151 v1.0 Gigabit Ethernet
       vendor: Atheros Communications
       physical id: 0
       bus info: pci@0000:02:00.0
       version: c0
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list
       configuration: latency=0
       resources: memory:fdec0000-fdefffff ioport:df00(size=128)

---

### Post by mikewhatever on 2010-12-29
That's a tricky one. Apparently, the driver is available, but you'd need the build-essential package + dependencies installed.
Check the link below for more info.
[http://www.oz9aec.net/index.php/linux/351-ubuntu-linux-on-the-acer-aspire-5745g-laptop](http://www.oz9aec.net/index.php/linux/351-ubuntu-linux-on-the-acer-aspire-5745g-laptop)

Edit: That NIC apparently works with 10.10 out of the box.
[http://www.oz9aec.net/index.php/linux/394-ubuntu-1010-on-the-acer-aspire-5745g-laptop](http://www.oz9aec.net/index.php/linux/394-ubuntu-1010-on-the-acer-aspire-5745g-laptop)

---

