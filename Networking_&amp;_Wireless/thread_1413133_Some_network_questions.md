---
title: "Some network questions"
date: 2010-02-22
forum: Networking &amp; Wireless
---

### Post by dargaud on 2010-02-22
Hello all,
a couple basic wired network questions. I currently connect via DHCP:
```
eth4      Link encap:Ethernet  HWaddr 00:19:66:b0:46:e2
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
...

```

- I'm curious as to why does my ubuntu uses eth4 instead of eth0 ?
```

0 $ dmesg | grep eth
[    2.147247] eth0: RTL8168d/8111d at 0xffffc90000c76000, 00:19:66:b0:46:e2, XI
D 281000c0 IRQ 28
[   13.138548] udev: renamed network interface eth0 to eth4
[   21.533644] r8169: eth4: link up
[   21.533650] r8169: eth4: link up
[   32.500984] eth4: no IPv6 routers present

```

- why is [Settings][Network connections] completely empty ? Shouldn't there be at least a DHCP connection declared ?

- why won't eth4 come back online if the connection goes down temporarily for some reason ? I have to re-enable it manually. Would declaring it as static solve it ?

- To make the connection static, is the old method of modifying the /etc/network/interfaces still valid or should I use the [Network connections] menu ? Won't it compete with DHCP ?

Thanks.

---

### Post by Iowan on 2010-02-22
You may be able to "clean up" the eth# by editing */etc/udev/rules.d/ 70-persistent-net.rules*.
Where is [Settings][Network connections]?
I've read other threads that suggest */etc/network/interfaces* doesn't work with Network Manager... it used to. Interfaces defined there were ignored by NM (static or DHCP). A static address should be outside the range of the DHCP server to avoid conflicts - whether defined by */etc/network/interfaces* or within Network Manager (which can still manage a static (manual) configuration).

---

### Post by dargaud on 2010-03-05
> You may be able to "clean up" the eth# by editing /etc/udev/rules.d/ 70-persistent-net.rules.
Thanks, that worked fine.

> I've read other threads that suggest /etc/network/interfaces doesn't work with Network Manager...
Then I'm really confused as to why there would be a graphical way to manage network interfaces if it doesn't work well with the low-level config file method. What is the point of doing a GUI then ?

---

