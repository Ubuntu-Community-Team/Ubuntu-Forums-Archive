---
title: "ifupdown wired connection"
date: 2009-07-10
forum: Networking &amp; Wireless
---

### Post by crazy2k on 2009-07-10
Hello. Today I upgraded from 8.04 to 8.10, and then from 8.10 to 9.04.

The last upgrade broke my connection settings. NetworkManager's icon always appeared with an X, and when I added my DSL connection, for some reason it wouldn't appear on the list. (I found that it was added to /etc/NetworkManager/system-connections/, but for some reason it wasn't being shown in the dialog.)

I tried different things in order to make my internet connection work. I finally found that changing:

```
[ifupdown]
managed=false

```to


```
[ifupdown]
managed=true

```would make the X on the NetworkManager icon dissappear. But now I have two connections: my DSL connection and one called "ifupdown (eth0)", which is impossible to delete. How do I get rid of that option? And what is it about?

Thanks for your help.

---

### Post by superprash2003 on 2009-07-10
post output of **lshw -C network** from the terminal.. also post output of **ifconfig**

---

### Post by crazy2k on 2009-07-10
```
$ sudo lshw -C network
  *-network DISABLED      
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 92:6b:4f:a8:f7:06
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

$ sudo ifconfig 
eth0      Link encap:Ethernet  direcciónHW 00:1e:8c:08:30:6f  
          dirección inet6: fe80::21e:8cff:fe08:306f/64 Alcance:Vínculo
          ARRIBA DIFUSIÓN CORRIENDO MULTICAST  MTU:1500  Métrica:1
          RX packets:12174 errors:0 dropped:0 overruns:0 frame:0
          TX packets:11790 errors:0 dropped:0 overruns:0 carrier:0
          colisiones:0 txqueuelen:1000 
          RX bytes:11711359 (11.7 MB)  TX bytes:2533830 (2.5 MB)
          Interrupción:252 Dirección base: 0x6000 

lo        Link encap:Bucle local  
          inet dirección:127.0.0.1  Máscara:255.0.0.0
          dirección inet6: ::1/128 Alcance:Anfitrión
          ARRIBA LOOPBACK CORRIENDO  MTU:16436  Métrica:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          colisiones:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)

ppp0      Link encap:Protocolo punto a punto  
          inet dirección:190.177.164.121  P-t-P:200.63.148.41  Máscara:255.255.255.255
          ARRIBA PUNTO A PUNTO CORRIENDO NOARP MULTICAST  MTU:1492  Métrica:1
          RX packets:11816 errors:0 dropped:0 overruns:0 frame:0
          TX packets:11413 errors:0 dropped:0 overruns:0 carrier:0
          colisiones:0 txqueuelen:3 
          RX bytes:11429257 (11.4 MB)  TX bytes:2209940 (2.2 MB)


```

---

### Post by p1977p on 2009-08-24
Hi. I had the same problem. Actually NetworkManager is configured to ignore interfaces configured in the /etc/network/interfaces file unless the 'managed' option is set to true. So you will get these 2 entries now. eth0 should be connected automatically unless you have disabled that option in NetworkManager.

---

