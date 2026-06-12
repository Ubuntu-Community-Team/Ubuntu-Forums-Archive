---
title: "eth0 device has disappeared - Lenovo n200 Notebook"
date: 2009-01-02
forum: Networking &amp; Wireless
---

### Post by glenn.w on 2009-01-02
Hi all,

I have a Lenovo 3000 N200 notebook which has been working fine for the past month with Ubuntu 8.04. Last night when I went to bed I suspended the laptop. Upon resuming it this morning I had no network connection. After some investigation I found that the eth0 device wasn't being listed with the 'ifconfig' command. I tried doing a '/etc/init.d/networking restart' and rebooting the laptop, but eth0 doesn't exist. 

Please could someone help me sort this out? It's really frustrating :(

Thanks,
G

---

### Post by ieee488 on 2009-01-02
Is Ubuntu set up to download and install updates without needing your approval?

---

### Post by superprash2003 on 2009-01-02
have you restarted after that? post output of lspci

---

### Post by glenn.w on 2009-01-02
Thanks for the replies. Here's the output from dmesg and lspci:
[http://pastebin.com/m1d830bdb](http://pastebin.com/m1d830bdb)
[http://pastebin.com/d3d2a470a](http://pastebin.com/d3d2a470a)

However, I'm worried the problem is much deeper. I booted off a live Ubuntu CD (8.04 too) and I get the same problem. I've never encountered HW failure on a NIC card? Especially considering the laptop's only two months old. Any ideas....?

G

---

### Post by ieee488 on 2009-01-02
I suppose it is possible that the builtin Ethernet port went bad.

Usually when a cable is plugged into mine there is a flashing green light.
Or just a steady green light when there is no traffic.

---

### Post by glenn.w on 2009-01-02
I do get a green solid light, and a flashing orange light....

---

### Post by superprash2003 on 2009-01-03
that link doesnt work..did you try ifconfig after a reboot

---

### Post by albinootje on 2009-01-03
> **glenn.w said:**
> Hi all,

I have a Lenovo 3000 N200 notebook which has been working fine for the past month with Ubuntu 8.04. Last night when I went to bed I suspended the laptop. Upon resuming it this morning I had no network connection. After some investigation I found that the eth0 device wasn't being listed with the 'ifconfig' command. I tried doing a '/etc/init.d/networking restart' and rebooting the laptop, but eth0 doesn't exist. 

Please could someone help me sort this out? It's really frustrating :(

Thanks,
G
Can you go into the BIOS. Disable the NIC. Boot with Ubuntu.
Shutdown your machine completely.

Then go into the BIOS. Enable your NIC. Boot with Ubuntu.

After that post the output of the following :
```

lsmod
lspci
lshw -c network
dmesg
ifconfig -a
route -n
cat /etc/resolv.conf

```
Please post here as output.txt attachment(s).

---

