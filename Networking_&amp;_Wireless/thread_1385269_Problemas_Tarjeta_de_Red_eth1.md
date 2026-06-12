---
title: "Problemas Tarjeta de Red eth1"
date: 2010-01-19
forum: Networking &amp; Wireless
---

### Post by benjamid on 2010-01-19
Hola compañer@s del metal ;),
   
  os escribo a ver si alguien me puede echar un cable ya que he tocado fondo por lo menos 8 veces y ya no se me ocurre como continuar con el tema, os cuento.
   
  Llevo más de 2 semanas con problemas de red en un servidor que tenemos en Frankfurt. Dicha máquina tiene 2 interfaces de red, eth0 conecta al exterior (internet) y eth1 es una red privada que conecta a otras máquinas. Al principio todo comenzó con una caída de red (eth0) que según el departamento técnico llevo al cambio de máquina sustituyendo discos duros (20-Dic-2009), después de este cambio se mantuvo estable el sistema un tiempo hasta la siguiente caída de red (27-Dic-2009). De golpe y porrazo no teníamos acceso a esa máquina por el interface eth0 pero si a través de la red privada (eth1). Accedíamos a la máquina mirábamos los log y no encontrábamos causa alguna de las caídas, ni siquiera coincidía que algún proceso se ejecutase siempre en esos instantes. Reiniciábamos la red y todo volvía a la normalidad. Nos pusimos en contacto con el departamento técnico que da soporte hardware a las máquinas y según ellos era problema nuestro (es decir, problema de software). Después de muchas pruebas y búsquedas por Internet (que si eran los drivers de la tarjeta, etc.) como continuábamos con los problemas de las caídas y estas cada vez eran más seguidas (hasta varias veces en una hora) decidimos mover todas las aplicaciones que teníamos a otra máquina para reinstalar el SO (por supuesto Ubuntu Server 8.x 64bit por si al cambiar la máquina había causado algún tipo de conflicto.
   
  Una vez reinstalado el Ubuntu comprobamos que la tarjeta de red eth0 funciona perfectamente y procedemos a configurar eth1, editamos /etc/network/interfaces y añadimos la entrada de la nueva interface eth1
   
  auto eth1
  iface eth1 inet static
    address 172.18.42.101
    network 172.18.42.0
    netmask 255.255.255.0
    broadcast 172.18.42.255
    gateway 172.18.42.1
   
  después reiniciamos la red (/etc/init.d/networking restart) y supuestamente debería hacer ping a la puerta de enlace (gateway 172.18.42.1) pero nada de nada. 
   
  Hablamos con el departamento técnico y la contestación es que tenemos mal configurada la red, es decir, que tenemos en la tabla de enrutamiento 2 puertas de enlace por defecto (you have two default gateways in your routing tables). Y efectivamente las tenemos:
   
  # route -n
Kernel IP routing table
Destination       Gateway          Genmask                     Flags    Metric  Ref       Use      Iface
xx.yy.zz.64       0.0.0.0             255.255.255.192        U         0          0          0          eth0
172.18.42.0     0.0.0.0             255.255.255.0            U         0          0          0          eth1
0.0.0.0             172.18.42.1     0.0.0.0                         UG      100      0          0          eth1
0.0.0.0             xx.yy.zz.65       0.0.0.0                         UG      100      0          0          eth0
  # ip a
  1: lo: <LOOPBACK,UP,LOWER_UP> mtu 16436 qdisc noqueue
      link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
      inet 127.0.0.1/8 scope host lo
  2: eth0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast qlen 1000
      link/ether 00:46:c0:d0:24:ab brd ff:ff:ff:ff:ff:ff
      inet xx.yy.zz.83/26 brd 217.118.24.127 scope global eth0
  3: eth1: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast qlen 1000
      link/ether 00:46:c0:d0:24:ac brd ff:ff:ff:ff:ff:ff
      inet 172.18.42.101/24 brd 172.18.42.255 scope global eth1
   
  Según ellos tenemos que quitar una de las puertas de enlace por defecto, pero no entiendo exactamente a que se refieren. Procedemos al cambio dejando la tabla de enrutamiento como:
   
  #route -n
  Kernel IP routing table
  Destination       Gateway          Genmask                     Flags    Metric  Ref       Use      Iface
  xx.yy.zz.64 *                           255.255.255.192        U         0          0          0          eth0
  172.18.42.0    172.18.42.1     255.255.255.0            UG      0          0          0          eth1
  172.18.42.0    *                      255.255.255.0            U         0          0          0          eth1
  default              xx.yy.zz.65       0.0.0.0                         UG      100      0          0          eth0
   
  Aún así no hacemos ping a 172.18.42.1. Por desgracia mi fuerte no son los temas de redes pero nunca he tenido estos problemas para configurar un par de tarjetas de red en Linux (más aun, cambie de Windows a Linux entre otras muchas cosas por este tipo de situaciones inexplicables que solo el tío Bill sabe como solucionarlas). Hemos hecho muchas pruebas pero nada y para más INRI la otra máquina que disponemos está configurada igual:
   
  # route -n
  Kernel IP routing table
  Destination     Gateway         Genmask             Flags   Metric  Ref    Use        Iface
xx.yy.zz.64     0.0.0.0         255.255.255.192 U        0          0        0            eth0
  172.18.42.0     0.0.0.0         255.255.255.0     U        0          0        0            eth1
  0.0.0.0 xx.yy.zz.65     0.0.0.0                 UG     100      0        0            eth0
  0.0.0.0         172.18.42.1     0.0.0.0                 UG     100      0        0            eth1
   
  Pero esta si que hace ping a 172.18.42.1:
   
  # ping 172.18.42.1
  PING 172.18.42.1 (172.18.42.1) 56(84) bytes of data.
  64 bytes from 172.18.42.1: icmp_seq=1 ttl=64 time=9.03 ms
  64 bytes from 172.18.42.1: icmp_seq=2 ttl=64 time=0.415 ms
   
  --- 172.18.42.1 ping statistics ---
  2 packets transmitted, 2 received, 0% packet loss, time 999ms
  rtt min/avg/max/mdev = 0.415/4.723/9.032/4.309 ms
   
  Esto es todo lo que se me ocurre contaros, si no encuentro una solución el siguiente paso será dar de baja el servidor (para que quiero un servidor que no soy capaz de configurar cuando tengo otros que no me dan problemas ¿¿¿???),  agradezco de antemano cualquier ayuda, idea o sugerencia que se os ocurra para darme algo de luz ante este galimatías :S, en flim, muchas gracias por todo.
   
  Sldos. Benjamid.

---

### Post by benjamid on 2010-01-19
Hola de nuevo,
   
  parece que al final he conseguido solucionar todos mis problema, YUJUUUUUUUUUUUUUUUUUUUUUUU!!!
  La verdad es que no entiendo muy bien porque ahora funciona ya que esta posibilidad ya la había contemplado. Lo único que he echo es configurar la red sin puerta de enlace, es decir, 
   
  auto eth1
  iface eth1 inet static
  address 172.18.42.101
  network 172.18.42.0
  netmask 255.255.255.0
  broadcast 172.18.42.255
   
  de esta forma la tabla de enrutamiento me queda:
   
  # route -n
  Kernel IP routing table
  Destination Gateway Genmask Flags Metric Ref Use Iface
  xx.yy.zz.64 0.0.0.0 255.255.255.192 U 0 0 0 eth0
  172.18.42.0 0.0.0.0 255.255.255.0 U 0 0 0 eth1
  0.0.0.0 xx.yy.zz.65 0.0.0.0 UG 100 0 0 eth0
   
  Y funciona perfectamente:
   
  ~# ping 172.18.42.100
  PING 172.18.42.100 (172.18.42.100) 56(84) bytes of data.
  64 bytes from 172.18.42.100: icmp_seq=1 ttl=64 time=7.79 ms
  64 bytes from 172.18.42.100: icmp_seq=2 ttl=64 time=0.179 ms
   
  --- 172.18.42.100 ping statistics ---
  2 packets transmitted, 2 received, 0% packet loss, time 999ms
  rtt min/avg/max/mdev = 0.179/3.988/7.797/3.809 ms
   
   
  He procedido a hacer lo mismo en la otra máquina para concluir.
   
  Muchas gracias a tod@s por la ayuda (espirituosa aunque sea) prestada ;P.
  Sldos. Benjamid.

---

