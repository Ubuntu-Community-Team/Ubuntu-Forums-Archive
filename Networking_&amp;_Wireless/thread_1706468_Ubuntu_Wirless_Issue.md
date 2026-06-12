---
title: "Ubuntu Wirless Issue"
date: 2011-03-13
forum: Networking &amp; Wireless
---

### Post by CyberHax0rs on 2011-03-13
Hey Everybody.

I have just installed Ubuntu along side my Windows 7 on my HP Pavilion dm 4 icore 5.
I have problems using my wifi device.
It is not even detecting any wireless device.

Here r the results of what i found from some useful commands.

```
lspci -nn | grep 'Wirless Brand'
```Result:- Not Showing anything.

```
ifconfig
```Result:- eth0

```
lspci -v | less
```Result:- Broadcom Corporation BCM4313 802.11 b/g LP=PHY (rev 01)

```
dmesg
```Result:-Skipping Probe due to Cache edid.

```
Sudo lshw -C network
```Result:-UNCLAIMED
```

iwlist scan
```Result:- Showing Nothing.
```

Ubuntu Version is 10.10
``````
Uname -mr is 2.6.35-22-generic i686
```
Can somebody please look into the matter and guide me through it.
Thanks in advance.

---

