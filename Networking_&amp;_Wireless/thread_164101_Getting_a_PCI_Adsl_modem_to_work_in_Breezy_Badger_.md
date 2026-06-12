---
title: "Getting a PCI Adsl modem to work in Breezy Badger (with ndiswrapper)"
date: 2006-04-22
forum: Networking &amp; Wireless
---

### Post by Aessu on 2006-04-22
Hi! Im trying to get a Telewell IA-300B Adsl card working. This is the same card as A-Link Roadrunner 10 and xpeed x400 wich is listed as supported in [http://ndiswrapper.sourceforge.net/mediawiki/index.php/List](http://ndiswrapper.sourceforge.net/mediawiki/index.php/List) . I have succesfully installed the windows drivers and the ndiswrapper -l says "driver present, hardware present".
but this the farest i get. Could someone help me?
And yes, im sure it's same card. Chipsets and pciids match :D

---

### Post by Aessu on 2006-04-23
Could someone help me?

---

### Post by mips on 2006-04-23
That is one weird card to say the least. I tried googling it and got a gazillion hits in finish which is a language I cannot read, looks a bit slavik to me..

Try a google search for:
Ubuntu Telewell IA-300B
Debian Telewell IA-300B
Linux Telewell IA-300B

Also search the Debian forums for Telewell and see what gives.


1. Please post output of **ifconfig -a**
2. Please post output of **lspci | grep Eth**
3. Please post output of **route -n**
4. Please post output of **cat /etc/resolv.conf**
4. Please post output of **cat /etc/network/interfaces**
6. Who is your ISP and provide a web link.

[www.telewell.fi](www.telewell.fi)
[http://www.telewell.fi/paivitykset/](http://www.telewell.fi/paivitykset/)
[http://www.groupsrv.com/linux/about3092.html](http://www.groupsrv.com/linux/about3092.html)
[http://www.ubuntuforums.org/search.php?searchid=5000386](http://www.ubuntuforums.org/search.php?searchid=5000386)

Unfortunately I cannot help much beyond this. If you find any info out there and would like some more help post the info/links here and we will try and help.

---

### Post by Aessu on 2006-04-24
okay, here you go.

```
root@aes:~# ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:0C:6E:96:36:9A
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:19 Base address:0xd400

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:7706 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7706 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:590816 (576.9 KiB)  TX bytes:590816 (576.9 KiB)

sit0      Link encap:IPv6-in-IPv4
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)


```

```
root@aes:~# lspci | grep Eth
0000:00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 90)

```
that didn't show the Adsl NIC...
```

and the Adsl Card
0000:00:0b.0 Network controller: Integrated Telecom Express Inc: Unknown device 0188 (rev 10)

```

```

root@aes~# cat /etc/resolv.conf
cat: /etc/resolv.conf: No such file or directory

```

```

root@aes:~# cat /etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
        script grep
        map eth0

```
ISP: [www.sonera.fi/eng](www.sonera.fi/eng)

If you want some text about the card in english google for a-link roadrunner 10, it has same pciid, same chipset, and even the same drivers: "linux drivers" for kernels  2.2.14-19 and 2.4.4 / 2.4.8 are available for both of these cards.

---

### Post by mips on 2006-04-24
Will try and look at it again a bit later.

I know this card works in Linux though but not how.

---

### Post by Aessu on 2006-04-24
[QUOTE=mips]Will try and look at it again a bit later.

I know this card works in Linux though but not how.[/QUOTE]
I have just the same problem :D

---

### Post by Samuli on 2006-05-29
So did you ever get it to work? I'm having the same problem :mad:

---

### Post by dirtylobster on 2006-07-17
Same problem (Dapper Drake)...

---

