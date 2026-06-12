---
title: "HomePNA pegasus (again)"
date: 2006-01-25
forum: Networking &amp; Wireless
---

### Post by javier on 2006-01-25
I have installed Ubuntu 5.10 and I tried to set up the network. I am using HomePNA with Pegasus driver. It seems that the system detects the HomePNA adapter, it appears as eth1 after typing ifconfig, I have set up the IP address, gateways, DNS and so on.

I have ping succesfully to localhost but unsuccesfully with the gateway. I have also checked the forums here with this problem and I tried this promising solution, but without success:

>in /etc/modprobe.d/aliases
>alias eth1 pegasus
>options pegasus mii_mode=1

>sudo update-modules

Any more hints? Thanks for your help

---

### Post by stream303 on 2006-01-25
Let's take a look at your **/etc/resolv.conf**
and see what nameservers you are using.  I'll bet it's not one of your isp's, but it's easy to fix...

---

