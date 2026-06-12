---
title: "Not possible to enter router interface with firefox"
date: 2010-11-21
forum: Networking &amp; Wireless
---

### Post by freacert on 2010-11-21
I use an old conceptronic C100S8 router/switch. Trying to get into the router interface, with firefox 3.6.12 but not possible at all. My router ip according to ifconfig is 127.0.0.1


```
lo        Link encap:Bucle local  
          Direc. inet:127.0.0.1  Másc:255.0.0.0
          Dirección inet6: ::1/128 Alcance:Anfitrión
          ACTIVO BUCLE FUNCIONANDO  MTU:16436  Métrica:1
          Paquetes RX:1740 errores:0 perdidos:0 overruns:0 frame:0
          Paquetes TX:1740 errores:0 perdidos:0 overruns:0 carrier:0
          colisiones:0 long.colaTX:0 
          Bytes RX:347408 (347.4 KB)  TX bytes:347408 (347.4 KB)

```but no luck at all. somebody any ideas please??

---

### Post by magnatron on 2010-11-21
open terminal and type: route -n

Your router address should be the one with the UG flag

Example: 192.168.1.1 UG

U indicates if its up and G tells you its your gateway!

Whatever IP it is, it certainly wont be 127.0.0.1 ;)

---

### Post by freacert on 2010-11-21
> **magnatron said:**
> open terminal and type: route -n


output
```
Tabla de rutas IP del núcleo
Destino         Pasarela        Genmask         Indic Métric Ref    Uso Interfaz
87.111.87.128   0.0.0.0         255.255.255.128 U     1      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
0.0.0.0         87.111.87.129   0.0.0.0         UG    0      0        0 eth0

```no luck either.

---

### Post by magnatron on 2010-11-21
what about netstat -r

If that route table is correct your destination address and gateway are almost the same :o

Did you try [http://87.111.87.129](http://87.111.87.129)

---

### Post by spiky001 on 2010-11-21
Has the op got an eth0 hub? my route -n ```
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
10.64.64.64     0.0.0.0         255.255.255.255 UH    0      0        0 ppp0
10.42.44.0      0.0.0.0         255.255.255.0   U     2      0        0 wlan0
10.42.43.0      0.0.0.0         255.255.255.0   U     1      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
0.0.0.0         10.64.64.64     0.0.0.0         UG    0      0        0 ppp0

```

---

### Post by freacert on 2010-11-21
> **magnatron said:**
> what about netstat -r

If that route table is correct your destination address and gateway are almost the same :o

Did you try [http://87.111.87.129](http://87.111.87.129)

code netstat -r
```
Tabla de rutas IP del núcleo
Destino         Pasarela        Genmask         Indic   MSS Ventana irtt Interfaz
87.111.87.128   *               255.255.255.128 U         0 0          0 eth0
link-local      *               255.255.0.0     U         0 0          0 eth0
default         cliente-71xxx.i 0.0.0.0         UG        0 0          0 eth0
```and yes i tried the ipaddresses with http in front aswell...
think router ipaddress can never be a 87.111 series...

---

### Post by freacert on 2010-11-21
> **spiky001 said:**
> Has the op got an eth0 hub? my route -n ```
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
10.64.64.64     0.0.0.0         255.255.255.255 UH    0      0        0 ppp0
10.42.44.0      0.0.0.0         255.255.255.0   U     2      0        0 wlan0
10.42.43.0      0.0.0.0         255.255.255.0   U     1      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
0.0.0.0         10.64.64.64     0.0.0.0         UG    0      0        0 ppp0

```


what do you mean with "op" ?
yes, i would think it is an eth0 hub...

---

### Post by spiky001 on 2010-11-21
original poster op

so what do you want to do exactly?

---

### Post by freacert on 2010-11-21
> **spiky001 said:**
> original poster op

so what do you want to do exactly?

I (the OP) want to enter the admin interface of my router. but what i think is the gateway, 0.0.0.0 or 127.0.0.1 won't let me..

---

### Post by spiky001 on 2010-11-21
Thats just a hub you cant get in to them they just expand your eth0 connections, if you have a router as well then thats what you need to get into, do you have something like this

[http://www.google.co.uk/imgres?imgurl=http://www.cisco.com/image/gif/paws/24100/154-a.gif&imgrefurl=http://www.cisco.com/en/US/tech/tk828/technologies_tech_note09186a00800ae957.shtml&usg=__uMCxWEgqsEgpiU9-x8GdJwMhoLA=&h=303&w=576&sz=10&hl=en&start=0&zoom=1&tbnid=_FgUvUFwcLTYIM:&tbnh=96&tbnw=182&prev=/images%3Fq%3Drouter%2Band%2Bswitch%26hl%3Den%26sa%3DG%26biw%3D1207%26bih%3D584%26gbv%3D2%26tbs%3Disch:1&itbs=1&iact=hc&vpx=855&vpy=92&dur=1671&hovh=163&hovw=310&tx=195&ty=96&ei=mIHpTI3aIsmwhQedm-y6DA&oei=mIHpTI3aIsmwhQedm-y6DA&esq=1&page=1&ndsp=18&ved=1t:429,r:5,s:0](http://www.google.co.uk/imgres?imgurl=http://www.cisco.com/image/gif/paws/24100/154-a.gif&imgrefurl=http://www.cisco.com/en/US/tech/tk828/technologies_tech_note09186a00800ae957.shtml&usg=__uMCxWEgqsEgpiU9-x8GdJwMhoLA=&h=303&w=576&sz=10&hl=en&start=0&zoom=1&tbnid=_FgUvUFwcLTYIM:&tbnh=96&tbnw=182&prev=/images%3Fq%3Drouter%2Band%2Bswitch%26hl%3Den%26sa%3DG%26biw%3D1207%26bih%3D584%26gbv%3D2%26tbs%3Disch:1&itbs=1&iact=hc&vpx=855&vpy=92&dur=1671&hovh=163&hovw=310&tx=195&ty=96&ei=mIHpTI3aIsmwhQedm-y6DA&oei=mIHpTI3aIsmwhQedm-y6DA&esq=1&page=1&ndsp=18&ved=1t:429,r:5,s:0)

---

### Post by chili555 on 2010-11-21
I don't see an ethernet interface in your ifconfig. Is it working?  Please let us see:```
sudo lshw -C network
```Once we get that working, you should be able to do:```
sudo ifconfig eth0 192.168.1.2 up
firefox 192.168.1.1
```The router interface should come right up.

I am not certain the address is 192.168.1.1 but you should be able to find that out in the manual, either paper or on line.

---

### Post by ajgreeny on 2010-11-21
The router IP address is usually on a label under the router.  It is on mine.

What did the first paragraph of the *ifconfig* command give you?  You've only shown the second part, which is no help.

---

### Post by freacert on 2010-11-21
> **spiky001 said:**
> Thats just a hub you cant get in to them they just expand your eth0 connections, if you have a router as well then thats what you need to get into, do you have something like this


yes, it is an autodetect 10/100 8 ports switch

---

### Post by spiky001 on 2010-11-21
ok post ifconfig results as posted above

---

### Post by freacert on 2010-11-21
> **spiky001 said:**
> ok post ifconfig results as posted above

ifconfig

> eth0      Link encap:Ethernet  direcciónHW 00:22:15:e1:85:67  
          Direc. inet:87.111.87.143  Difus.:87.111.87.255  Másc:255.255.255.128
          Dirección inet6: fe80::222:15ff:fee1:8567/64 Alcance:Enlace
          ACTIVO DIFUSIÓN FUNCIONANDO MULTICAST  MTU:1500  Métrica:1
          Paquetes RX:2210154 errores:0 perdidos:0 overruns:0 frame:0
          Paquetes TX:2170448 errores:0 perdidos:0 overruns:0 carrier:0
          colisiones:0 long.colaTX:1000 
          Bytes RX:1735914988 (1.7 GB)  TX bytes:755415143 (755.4 MB)
          Interrupción:31 Dirección base: 0xe000 

lo        Link encap:Bucle local  
          Direc. inet:127.0.0.1  Másc:255.0.0.0
          Dirección inet6: ::1/128 Alcance:Anfitrión
          ACTIVO BUCLE FUNCIONANDO  MTU:16436  Métrica:1
          Paquetes RX:5485 errores:0 perdidos:0 overruns:0 frame:0
          Paquetes TX:5485 errores:0 perdidos:0 overruns:0 carrier:0
          colisiones:0 long.colaTX:0 
          Bytes RX:671945 (671.9 KB)  TX bytes:671945 (671.9 KB)

and website and manual of this conceptronic switch won't give me ht ip address. googling also no luck.

---

### Post by uncaspi on 2010-11-21
You can't log in to a hub or switch.

---

### Post by freacert on 2010-11-22
> **uncaspi said:**
> You can't log in to a hub or switch.

you're right! that explains the gateway at the isp.. thanks

---

### Post by VanillaMozilla on 2010-11-22
post deleted

---

### Post by spiky001 on 2010-11-22
Ok so WHY do/did you need to get in to your router which you cant as it is a hub as I mention yesterday???

---

