---
title: "Tun Creation Issues"
date: 2012-02-12
forum: Networking &amp; Wireless
---

### Post by Qcrist on 2012-02-12
I am trying to create a tun interface to capture packets with, but I cannot capture packets on the interface with wireshark.

I created the tun adapter tun0

```
openvpn --mktun --dev tun0
``````

TUN/TAP device tun0 opened
Persist state set to: ON

```Then I gave it the ip address 11.0.0.1/24

```
ifconfig tun0 11.0.0.1/24
```I startup wireshark and listen on the interface.

I ping an address routed through the interface

```
ping 11.0.0.2

```But wireshark does not capture any packets. Does anyone know how to fix this?

---

