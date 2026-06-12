---
title: "Internet problem with Ubuntu 9.04"
date: 2009-05-03
forum: Networking &amp; Wireless
---

### Post by rennerocha on 2009-05-03
Hello,

I had Ubuntu 8.10 installed in my computer. I upgraded with apt-get to 9.04. The upgrade was successful, but after restarted the computer just the google site works. But now, nothing works, no sites opened. The browser remains 'loading'. The I've tried 'apt-get update' and it didn't work too.

I though it could be a DNS problem. I've changed my DNS addresses but it didn't work.

The strange is that when I try 'ping [www.somesite.com](www.somesite.com)' or 'ping 123.12.123.123', I receive an answer.

After tried these thing I reinstalled the system from scratch, but it didn't work too.

Does anybody have this problem???? [IMG]http://ubuntuforum-br.org/Smileys/default/huh.gif[/IMG] [IMG]http://ubuntuforum-br.org/Smileys/default/huh.gif[/IMG] [IMG]http://ubuntuforum-br.org/Smileys/default/huh.gif[/IMG]

Thanks!!!!

---

### Post by pytheas22 on 2009-05-03
What is the output of these commands:
```

lshw -C Network
ping -c 5 google.com
ping -c 5 74.125.67.100
wget google.com
wget 74.125.67.100
ifconfig
```

---

### Post by rennerocha on 2009-05-04
lshw -c Network:

  *-network
       description: Ethernet interface
       product: 190 Ethernet Adapter
       vendor: Silicon Integrated Systems [SiS]
       physical id: 4
       bus info: pci@0000:00:04.0
       logical name: eth0
       version: 00
       serial: 00:14:2a:e5:aa:42
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sis190 driverversion=1.2 duplex=full ip=192.168.1.101 latency=0 link=yes module=sis190 multicast=yes port=MII speed=100MB/s
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 76:02:51:d5:a7:7a
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

ping -c 5 google.com:
PING google.com (74.125.45.100) 56(84) bytes of data.
64 bytes from yx-in-f100.google.com (74.125.45.100): icmp_seq=1 ttl=235 time=168 ms
64 bytes from yx-in-f100.google.com (74.125.45.100): icmp_seq=2 ttl=235 time=179 ms
64 bytes from yx-in-f100.google.com (74.125.45.100): icmp_seq=3 ttl=235 time=178 ms
64 bytes from yx-in-f100.google.com (74.125.45.100): icmp_seq=4 ttl=235 time=193 ms
64 bytes from yx-in-f100.google.com (74.125.45.100): icmp_seq=5 ttl=235 time=173 ms

--- google.com ping statistics ---
5 packets transmitted, 5 received, 0% packet loss, time 8213ms
rtt min/avg/max/mdev = 168.890/178.753/193.491/8.279 ms

ping -c 5 74.125.67.100:
PING 74.125.67.100 (74.125.67.100) 56(84) bytes of data.
64 bytes from 74.125.67.100: icmp_seq=4 ttl=44 time=158 ms

--- 74.125.67.100 ping statistics ---
5 packets transmitted, 1 received, 80% packet loss, time 4001ms
rtt min/avg/max/mdev = 158.776/158.776/158.776/0.000 ms

The wget's received the files.

Does it help????

---

### Post by rennerocha on 2009-05-04
ifconfig:
eth0      Link encap:Ethernet  Endereço de HW 00:14:2a:e5:aa:42  
          inet end.: 192.168.1.101  Bcast:192.168.1.255  Masc:255.255.255.0
          endereço inet6: fe80::214:2aff:fee5:aa42/64 Escopo:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Métrica:1
          pacotes RX:60 erros:0 descartados:0 excesso:0 quadro:0
          Pacotes TX:81 erros:0 descartados:0 excesso:0 portadora:0
          colisões:0 txqueuelen:1000 
          RX bytes:19557 (19.5 KB) TX bytes:9123 (9.1 KB)
          IRQ:19 Endereço de E/S:0xdead 

lo        Link encap:Loopback Local  
          inet end.: 127.0.0.1  Masc:255.0.0.0
          endereço inet6: ::1/128 Escopo:Máquina
          UP LOOPBACK RUNNING  MTU:16436  Métrica:1
          pacotes RX:4 erros:0 descartados:0 excesso:0 quadro:0
          Pacotes TX:4 erros:0 descartados:0 excesso:0 portadora:0
          colisões:0 txqueuelen:0 
          RX bytes:240 (240.0 B) TX bytes:240 (240.0 B)

---

### Post by rennerocha on 2009-05-04
An interesting thing. When I try to use wget in some site, it soesn't work. But if I try the google site, it works fine.... 

root@c3po:/home/rocha# wget [www.terra.com.br]("http://www.terra.com.br")
--2009-05-04 18:36:56--  [http://www.terra.com.br/](http://www.terra.com.br/)
Resolvendo [www.terra.com.br]("http://www.terra.com.br")... 200.176.3.142
Conectando a [www.terra.com.br|200.176.3.142|:80]("http://www.terra.com.br%7C200.176.3.142%7C:80")... conectado.
HTTP requisição enviada, aguardando resposta... 302 Found
Localização: /portal/ [seguinte]
--2009-05-04 18:36:56--  [http://www.terra.com.br/portal/](http://www.terra.com.br/portal/)
Conectando a [www.terra.com.br|200.176.3.142|:80]("http://www.terra.com.br%7C200.176.3.142%7C:80")... conectado.
HTTP requisição enviada, aguardando resposta... ^C



root@c3po:/home/rocha# wget google.com
--2009-05-04 18:44:37--  [http://google.com/](http://google.com/)
Resolvendo google.com... 74.125.67.100, 209.85.171.100, 74.125.45.100
Conectando a google.com|74.125.67.100|:80... conectado.
HTTP requisição enviada, aguardando resposta... 301 Moved Permanently
Localização: [http://www.google.com/](http://www.google.com/) [seguinte]
--2009-05-04 18:44:38--  [http://www.google.com/](http://www.google.com/)
Resolvendo [www.google.com]("http://www.google.com")... 64.233.169.104, 64.233.169.147, 64.233.169.99, ...
Conectando a [www.google.com|64.233.169.104|:80]("http://www.google.com%7C64.233.169.104%7C:80")... conectado.
HTTP requisição enviada, aguardando resposta... 302 Found
Localização: [http://www.google.com.br/](http://www.google.com.br/) [seguinte]
--2009-05-04 18:44:38--  [http://www.google.com.br/](http://www.google.com.br/)
Resolvendo [www.google.com.br]("http://www.google.com.br")... 64.233.169.99, 64.233.169.103, 64.233.169.104, ...
Reutilizando conexão existente para [www.google.com:80]("http://www.google.com:80").
HTTP requisição enviada, aguardando resposta... 200 OK
Tamanho: nao especificado [text/html]
Salvando para: `index.html.4'

    [ <=>                                   ] 5.147       --.-K/s   em 0,008s  

2009-05-04 18:44:38 (657 KB/s) - `index.html.4' salvo [5147]

---

### Post by pytheas22 on 2009-05-04
hmmm, very strange that you can wget google.com, but nothing else.  I found this [bug report]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/137630"), which I think may describe the problem you're experiencing.  People there say that using the same ethernet driver (sis190) they were able to ping sites successfully, but not load web pages.  Apparently changing the mtu of their ethernet devices solved the problem.  If you type:
```

sudo ifconfig eth0 mtu 1492
```

does it help?

---

### Post by rennerocha on 2009-05-05
You've got the problem. After changing the MTU of my device (as you suggested), all works fine. Then I research a little more and found that more people have the same problem with this ethernet device (Sis190).

Thank you!

---

### Post by pytheas22 on 2009-05-05
Glad it's fixed.  If you want to change the mtu permanently, without having to run that command each time you reboot, run these commands, which will create a boot script to adjust mtu automatically when the system boots:
```

sudo -s
echo -e "#!/bin/bash\nifconfig eth0 mtu 1492" > /etc/init.d/eth-mtu-fix.sh
cd /etc/init.d
chmod +x eth-mtu-fix.sh
update-rc.d eth-mtu-fix.sh defaults
```

Now the fix should be applied automatically.

---

### Post by expcman on 2009-06-06
Thank you, thank you, thank you!  I have been having the very same problem and for the past two months (!!!) and I have done all sorts of searching on-line for an answer ... finally you have given it to me, for my new motherboard (installed two months ago!)
is indeed the very same SiS 190 and by following these clear and
effective instructions, by chaning the value of the mtu I am once again able to surf the Net without any problem at all.  "Oh, what a relief"!  My unbounded gratitude is most sincere - thanks a bunch from me ... as well as all other who doubtless suffer the same problem and need to find this simple and easy fix!

Most sincerely,

C. F. Jacks (a.k.a. "expcman")

---

