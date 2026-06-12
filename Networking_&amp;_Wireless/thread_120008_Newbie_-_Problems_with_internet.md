---
title: "Newbie - Problems with internet"
date: 2006-01-20
forum: Networking &amp; Wireless
---

### Post by ThirdGenLS1 on 2006-01-20
alright I just booted up ubuntu last night and i can't get it to connect to the internet if my life depended on it.  I have a wireless card but for right now i'm just trying to get it working with my etho cord.  When i plug the cord in it reads that i'm connnected but i just can't get any internet.  Its in DHCP mode right now and when i enter in the ifconfig eth0 in the terminal i get

Link encap:Ethernet HWaddr 00:08:02: DO:35:58
inet6 addr: fe80::208:3558/64 Scope:Link
UP BROADCAST MULTICAST MTU:1500 Metric:1
RX packets:1355 errors:0 drpped:0 overruns:0 frame:0
TX packets:7 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txpuenelen:100
RX bytes:62999 (61.5 KiB) TX bytes:2394 (2.3 KiB)
interrupt:11 Base adress:0xa800

and when i enter lspci | Eth
ethernet controller: Realtek Semiconductor Co., Ltd. Rtl-8139/8139c/8139C+ (rev 20)

When intering route -n it shows nothing in the gateway, genmask, ETC.

Any help would be greatly appreciated, cause i'm pretty excited to get this up and running.

---

### Post by jasmuz on 2006-01-20
did you try : sudo dhclient eth0

---

### Post by healychan on 2006-01-20
[QUOTE=jasmuz]did you try : sudo dhclient eth0[/QUOTE]
The code above should get you an IP address from DHCP server.
If it doesn't, try```
sudo ifup eth0
```

Good Luck

---

### Post by ThirdGenLS1 on 2006-01-23
i got it working thanks a lot guys

---

### Post by stream303 on 2006-01-23
[QUOTE=ThirdGenLS1] When i plug the cord in it reads that i'm connnected but i just can't get any internet.  Its in DHCP mode right now and when i enter in the ifconfig eth0 in the terminal i get

Link encap:Ethernet HWaddr 00:08:02: DO:35:58
inet6 addr: fe80::208:3558/64 Scope:Link[/QUOTE]

What does your /etc/resolv.conf show?

It is possible that your router / modem doesn't work properly with ipv6.  You may want to try disabling ipv6.  While it's **not normally recommended**, some hardware may not implement it properly so you can try this fallback to ipv4:

sudo gedit **/etc/modprobe.d/bad_list**

(you'll need to create bad_list yourself)

and inside bad_list, add the line:

alias net-pf-10 off

Now reboot, or just bring your interface down and up again:
sudo ifdown eth0
sudo ifup eth0

---

