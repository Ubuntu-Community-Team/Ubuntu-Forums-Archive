---
title: "Sharing ubuntu 10.10 network with win7 over cat5 cable"
date: 2011-03-06
forum: Networking &amp; Wireless
---

### Post by jc87 on 2011-03-06
I´m a long time Ubuntu user (since 5.04), but networks were never my speciality, so this is the reason why i´m asking for help.

I have a desktop running 10.10, connected to the internet trough a US robotics modem (connection eth1), and i want to share its network with my laptop running win7, over a cat5 cable (connection eth0), but the problem is I don’t seem to understand what i am doing wrong, what the missing steps required, or in which end is the problem (either ubuntu or windows side).

From what I could grasp was needed googling about the subject, i already set the eth0 connection to share with other computers (in network manager » edit connections » auto eth0 » ipv4 configuration » set to share with other computers).

Also using the cli set eth0 for static ip using :

```
sudo ifconfig eth0 192.168.0.1
```

Now the question is what i am missing? or is everything needed already done and i just have to properly configure the win7 side (which i already checked several times)?

Here is my ifconfig output:

```
eth0      Link encap:Ethernet  Endereço de HW 00:01:29:a6:55:fe  
          inet end.: 10.42.43.1  Bcast:10.42.43.255  Masc:255.255.255.0
          endereço inet6: fe80::201:29ff:fea6:55fe/64 Escopo:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Métrica:1
          pacotes RX:74 erros:0 descartados:0 excesso:0 quadro:0
          Pacotes TX:57 erros:0 descartados:0 excesso:0 portadora:0
          colisões:0 txqueuelen:1000 
          RX bytes:13866 (13.8 KB) TX bytes:12293 (12.2 KB)
          IRQ:17 

eth1      Link encap:Ethernet  Endereço de HW 00:c0:49:a3:53:f1  
          inet end.: 84.91.31.174  Bcast:84.91.31.255  Masc:255.255.252.0
          endereço inet6: fe80::2c0:49ff:fea3:53f1/64 Escopo:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Métrica:1
          pacotes RX:17865 erros:0 descartados:0 excesso:0 quadro:0
          Pacotes TX:639 erros:0 descartados:0 excesso:0 portadora:0
          colisões:0 txqueuelen:1000 
          RX bytes:18171932 (18.1 MB) TX bytes:99014 (99.0 KB)

lo        Link encap:Loopback Local  
          inet end.: 127.0.0.1  Masc:255.0.0.0
          endereço inet6: ::1/128 Escopo:Máquina
          UP LOOPBACK RUNNING  MTU:16436  Métrica:1
          pacotes RX:8 erros:0 descartados:0 excesso:0 quadro:0
          Pacotes TX:8 erros:0 descartados:0 excesso:0 portadora:0
          colisões:0 txqueuelen:0 
          RX bytes:480 (480.0 B) TX bytes:480 (480.0 B)
```

Thanks in advance for any help.

---

### Post by taylorchase on 2011-03-06
Are both computers connected to the modem or to a router which is connected to the modem? If you are just connecting from PC-to-PC then you just need a crossover cable. If they are both connected to a router then it should work out-of-the-box.

---

### Post by jc87 on 2011-03-06
Only the desktop running ubuntu is connected to the modem.

Anyway the reason for this thread is because something is wrong using the crossover cable, I just don&#8217;t know what ;)

---

