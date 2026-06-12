---
title: "Wifi Issues on Sony vaio E Series with Atheros Wireless Adapter"
date: 2011-11-11
forum: Networking &amp; Wireless
---

### Post by Myth17 on 2011-11-11
I just installed Ubuntu 11.04 on Sony Vaio E Series laptop with Atheros wireless adapter.

The wifi card is detected and shows up in output of lspci.

When I Enable wireless it gets turned on for a second and is switched off again. The Wireless light blinks up for a second.

Also if I try System Settings->Network the same thing happens. It also shows the Hardware Address.

Tried sudo ifconfig wlan0 up, the same thing happens again.

dmesg output says:

```
[CODE][645.356065] ADDRCONF(NETDEV_UP): wlan0: link is not ready

```[/CODE]


What could be the issue? How to troubleshoot?

---

