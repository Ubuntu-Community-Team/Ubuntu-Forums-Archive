---
title: "Kubuntu + Realtek card - slow network performance"
date: 2011-10-31
forum: Networking &amp; Wireless
---

### Post by Dedoimedo on 2011-10-31
Hi guys,

This is a very important tutorial explaining how to understand, isolate, diagnose and solve slow network performance, high latency and dropped packets with a Realtek ethernet card on Kubuntu, due to a bad driver, including downloading and compiling new driver from sources, removing and inserting modules into memory, blacklisting modules, rebuilding initrd, ipv6 advice, some caveats, general tips, and more. Enjoy.

[http://www.dedoimedo.com/computers/kubuntu-realtek.html](http://www.dedoimedo.com/computers/kubuntu-realtek.html)


Cheers,
Dedoimedo

---

### Post by praseodym on 2011-10-31
Hi,

you may want to translate this thread for the installation procedure of the newest r8168 module:

[http://forum.ubuntuusers.de/topic/lan-karte-funktioniert-nicht/#post-3005217](http://forum.ubuntuusers.de/topic/lan-karte-funktioniert-nicht/#post-3005217)

The IPv6 kernel module is no longer used (but in Debian), you can shut off IPv6 system wide via:

```
echo "net.ipv6.conf.all.disable_ipv6=1" | sudo tee -a /etc/sysctl.conf
```
and reboot.

```
ip a | grep inet6 
```
should give no output after that

---

