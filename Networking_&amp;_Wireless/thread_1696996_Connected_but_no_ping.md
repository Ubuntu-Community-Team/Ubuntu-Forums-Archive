---
title: "Connected but no ping"
date: 2011-02-28
forum: Networking &amp; Wireless
---

### Post by sombrancelha on 2011-02-28
Hello,

I'm having a problem with my computer connecting to a speficic wifi. The problem seems to be between my computer and this wifi, because I can connect to other networks and other computers can connect to this wifi. I do manage to get a connection, but I can't ping any website, I always get an unknown host error. I have managed to connect to this network only once: it wasn't pinging and then it eventually started working, but I don't recall doing anything that made it work.

Below is some info that could be relevant.

Thanks in advance

```

martin@martin:~$ ifconfig
eth0      Link encap:Ethernet  Endereço de HW 00:1b:24:d9:d7:58  
          UP BROADCAST MULTICAST  MTU:1500  Métrica:1
          pacotes RX:0 erros:0 descartados:0 excesso:0 quadro:0
          Pacotes TX:0 erros:0 descartados:0 excesso:0 portadora:0
          colisões:0 txqueuelen:1000 
          RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)
          IRQ:20 Endereço de E/S:0x2000 

eth1      Link encap:Ethernet  Endereço de HW 00:1a:73:c8:24:ee  
          inet end.: 192.168.0.108  Bcast:192.168.0.255  Masc:255.255.255.0
          endereço inet6: fe80::21a:73ff:fec8:24ee/64 Escopo:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Métrica:1
          pacotes RX:1655 erros:0 descartados:0 excesso:0 quadro:1168687
          Pacotes TX:770 erros:21 descartados:0 excesso:0 portadora:0
          colisões:0 txqueuelen:1000 
          RX bytes:343744 (343.7 KB) TX bytes:72537 (72.5 KB)
          IRQ:19 

lo        Link encap:Loopback Local  
          inet end.: 127.0.0.1  Masc:255.0.0.0
          endereço inet6: ::1/128 Escopo:Máquina
          UP LOOPBACK RUNNING  MTU:16436  Métrica:1
          pacotes RX:119 erros:0 descartados:0 excesso:0 quadro:0
          Pacotes TX:119 erros:0 descartados:0 excesso:0 portadora:0
          colisões:0 txqueuelen:0 
          RX bytes:10172 (10.1 KB) TX bytes:10172 (10.1 KB)

```

```

martin@martin:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11  Access Point: Not-Associated   
          Link Quality:5  Signal level:215  Noise level:199
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0

vboxnet0  no wireless extensions.

```

```

martin@martin:~$ lspci| grep Network
03:00.0 Network controller: Broadcom Corporation BCM4312 802.11a/b/g (rev 02)

```

```

martin@martin:~$ sudo lshw -C network
  *-network               
       description: Wireless interface
       product: BCM4312 802.11a/b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth1
       version: 02
       serial: 00:1a:73:c8:24:ee
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.60.48.36 ip=192.168.0.108 latency=0 multicast=yes wireless=IEEE 802.11abg
       resources: irq:19 memory:b6000000-b6003fff
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: vboxnet0
       serial: 0a:00:27:00:00:00
       capabilities: ethernet physical
       configuration: broadcast=yes multicast=yes

```

---

### Post by sombrancelha on 2011-03-01
bump

---

### Post by osianap on 2012-01-13
for what it's worth.  I have a very similar sounding problem.

---

### Post by jonobr on 2012-01-13
This looks like an old thread.
Im sure the OP has moved on by now,

Recommend you start a new thread with the same type of info


Posting .results from /etc/resolv.conf may help,

also try pinging website by IP instead of name, as it sounds like a DNS issue maybe occuring,.

Either way, recommend you open the new thread.

Thanks

jonobr

---

