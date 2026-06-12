---
title: "Internet doesn't work on startup"
date: 2012-05-24
forum: Networking &amp; Wireless
---

### Post by Shadius on 2012-05-24
Hey everybody,

My problem is that **sometimes** my wired internet doesn't work on my Ubuntu. I start up the computer and when I go to my internet browser (Google Chrome), it'll say there's no connection or whatever. I verify that "Enable Networking" is checked and it is, but still no connection. I uncheck "Enable Networking" and recheck it again and then I get a connection and am able to surf the internet. 

Why is this happening? It's not a major issue as I can fix it with just disabling and re-enabling "Enable Networking" but it is kind of annoying. Is there a fix for it? Is it a bug? Thanks.

---

### Post by papibe on 2012-05-24
Hi Shadius.

Is the ethernet interface set to 'Connect Automatically'?

Check that by opening:
```
Network Connections -> eth0 -> Edit
```

If not, then you should try that. If it is, it may be a re occurrence of this [bug]("https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/568191").

Regards.

---

### Post by Shadius on 2012-05-24
> **papibe said:**
> Hi Shadius.

Is the ethernet interface set to 'Connect Automatically'?

Check that by opening:
```
Network Connections -> eth0 -> Edit
```

If not, then you should try that. If it is, it may be a re occurrence of this [bug]("https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/568191").

Regards.

How do I check if the interface is set to "Connect Automatically"?

Thanks for your help. :)

---

### Post by Shadius on 2012-05-24
I went into **Edit Connections**, saw **Auto Ethernet**, went to **Edit** and and verified that "Connect Automatically" is indeed checked.

---

### Post by papibe on 2012-05-24
> Click on the network icon on the top bar.
Select 'Edit Connections'. That will open a new window.
Under the Wired tab, there should be a eth0 entry. Selected and press Edit.
Another window will open. There you should see the 'Connect automatically' checkbox.

Regards.

If see that you already done that.

What is the method on the 'IPv4' tab?

Regards.

---

### Post by Shadius on 2012-05-24
> **papibe said:**
> If see that you already done that.

What is the method on the 'IPv4' tab?

Regards.

The **IPv4 Settings** tab shows **Method: Automatic (DHCP)**.
Also, I don't have an **eth0** entry, I have an **Auto Ethernet** entry.

---

### Post by papibe on 2012-05-24
I imagine that in the last windows, under the MAC address it is displayed the 'eth0' name isn't it?

Could you post the content of this file?
```
/etc/network/interfaces
```
Also the result of these commands:
```
ifconfig

dmesg | grep  eth0
```
Regards.

---

### Post by Shadius on 2012-05-24
> **papibe said:**
> I imagine that in the last windows, under the MAC address it is displayed the 'eth0' name isn't it?

Could you post the content of this file?
```
/etc/network/interfaces
```
Also the result of these commands:
```
ifconfig

dmesg | grep  eth0
```
Regards.

Oh, yes. Sorry about that. In the **Editing Auto Ethernet** window, under the **Wired** tab the Device MAC address shows (eth0) at the end of the address.

For the first code, how do I do that? Sorry, I'm a total beginner here.

---

### Post by Shadius on 2012-05-24
```
shadius@shadius-5410US:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:30:f1:21:b6:f0  
          inet addr:192.168.1.103  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::230:f1ff:fe21:b6f0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1505 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1033 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1229902 (1.2 MB)  TX bytes:117093 (117.0 KB)
          Interrupt:19 Base address:0x1000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:150 errors:0 dropped:0 overruns:0 frame:0
          TX packets:150 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:14039 (14.0 KB)  TX bytes:14039 (14.0 KB)

shadius@shadius-5410US:~$ dmesg | grep eth0
[    2.593074] 8139too 0000:02:0f.0: eth0: RealTek RTL8139 at 0x1000, 00:30:f1:21:b6:f0, IRQ 19
[   15.884232] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   18.188691] 8139too 0000:02:0f.0: eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[   28.896074] eth0: no IPv6 routers present

```

---

### Post by papibe on 2012-05-24
You missed interfaces, but it should look like this:
```
auto lo
iface lo inet loopback
```

The rest all look OK, so I would recommend to report this, as it looks more and more like the bug linked above (or mark it as "affect me").

Regards.

---

### Post by Shadius on 2012-05-24
```
shadius@shadius-5410US:~$ /etc/network/interfaces
bash: /etc/network/interfaces: Permission denied
shadius@shadius-5410US:~$
```

---

### Post by papibe on 2012-05-24
It is jus a file, try this:
```
cat  /etc/network/interfaces
```
Regards.

---

### Post by Shadius on 2012-05-24
> **papibe said:**
> It is jus a file, try this:
```
cat  /etc/network/interfaces
```
Regards.

Got it! :)

```
shadius@shadius-5410US:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback

shadius@shadius-5410US:~$
```

---

