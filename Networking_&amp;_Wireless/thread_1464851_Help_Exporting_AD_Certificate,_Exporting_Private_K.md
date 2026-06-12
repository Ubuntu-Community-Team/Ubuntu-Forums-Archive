---
title: "Help Exporting AD Certificate, Exporting Private Key, CA and User Cert for Wireless"
date: 2010-04-28
forum: Networking &amp; Wireless
---

### Post by EclipseAgent on 2010-04-28
Hey All, 

I need some help and a walk through with exporting my cert + private key from Active Directory, and using openssl to export my key, user cert and ca cert, so that I can authenticate to wireless. 

So far I haven't been successful, and get the following in daemon.log

Apr 28 15:47:17 HCDEB05006060 NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Apr 28 15:47:17 HCDEB05006060 NetworkManager: <info>  (wlan0): device state change: 6 -> 4 (reason 0)
Apr 28 15:47:17 HCDEB05006060 NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Apr 28 15:47:17 HCDEB05006060 NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Apr 28 15:47:17 HCDEB05006060 NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Apr 28 15:47:17 HCDEB05006060 NetworkManager: <info>  (wlan0): device state change: 4 -> 5 (reason 0)
Apr 28 15:47:17 HCDEB05006060 NetworkManager: <info>  Activation (wlan0/wireless): access point 'access_point' has security, but secrets are required.
Apr 28 15:47:17 HCDEB05006060 NetworkManager: <info>  (wlan0): device state change: 5 -> 6 (reason 0)
Apr 28 15:47:17 HCDEB05006060 NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete.


Help and / or a step by step of the whole process would be quite welcomed.. i'm getting irritated with carrying around a long Ethernet cable because I can't connect to the cert secured wireless

---

