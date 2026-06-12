---
title: "internet eth0 doen't work :/"
date: 2011-04-30
forum: Networking &amp; Wireless
---

### Post by VR! on 2011-04-30
hello (: 
i'm new in the forum and.. using ubuntu. 
well.. my internet was fine.. until.. 
i had to work in the school so.. a teacher configured the internet settings.. for something .. ( i don't remember)
and everything was fine. 
but when i returned to my house and conected my lap to internet (cable) 
the internet didn't work. 
can someone help me? ):



ubuntu@VR:/etc/network$ ifconfig
eth0      Link encap:Ethernet  direcciónHW 00:1d:72:46:38:3c  
          Direc. inet:192.168.1.65  Difus.:192.168.1.255  Másc:255.255.255.0
          Dirección inet6: fe80::21d:72ff:fe46:383c/64 Alcance:Enlace
          ACTIVO DIFUSIÓN FUNCIONANDO MULTICAST  MTU:1500  Métrica:1
          Paquetes RX:23 errores:0 perdidos:0 overruns:0 frame:0
          Paquetes TX:40 errores:0 perdidos:0 overruns:0 carrier:0
          colisiones:0 long.colaTX:1000 
          Bytes RX:2653 (2.6 KB)  TX bytes:8466 (8.4 KB)
          Interrupción:17 

lo        Link encap:Bucle local  
          Direc. inet:127.0.0.1  Másc:255.0.0.0
          Dirección inet6: ::1/128 Alcance:Anfitrión
          ACTIVO BUCLE FUNCIONANDO  MTU:16436  Métrica:1
          Paquetes RX:156 errores:0 perdidos:0 overruns:0 frame:0
          Paquetes TX:156 errores:0 perdidos:0 overruns:0 carrier:0
          colisiones:0 long.colaTX:0 
          Bytes RX:11528 (11.5 KB)  TX bytes:11528 (11.5 KB)

---

### Post by Iowan on 2011-04-30
I presume your laptop was set up for DHCP addressing via Network Manager. You can check the connection to see if it is set to connect automatically.
Another thing you might try is to run a command from a terminal (Applications>Accessories>Terminal):
 **sudo dhclient**

---

### Post by VR! on 2011-05-01
> **Iowan said:**
> I presume your laptop was set up for DHCP addressing via Network Manager. You can check the connection to see if it is set to connect automatically.
Another thing you might try is to run a command from a terminal (Applications>Accessories>Terminal):
 **sudo dhclient**

uhm... i checked the DHCP adessing and i changed it to automatically. and i run the comand in a terminal.. and nothing change :/ 
do you have a nother idea? :S

---

### Post by Iowan on 2011-05-01
What sort of messages popped up when you ran **sudo dhclient**?
**ifconfig** shows an IP address - is it correct for your network?
Can you **ping** the router?
Can you **ping** the internet by IP address (74.125.225.17)?

---

### Post by VR! on 2011-05-01
> **Iowan said:**
> What sort of messages popped up when you ran **sudo dhclient**?
**ifconfig** shows an IP address - is it correct for your network?
Can you **ping** the router?
Can you **ping** the internet by IP address (74.125.225.17)?

hello
when i ran "sudo dhclient" :
> ubuntu@VR:~$ sudo dhclient
ubuntu@VR:~$ 
... i'm not very good at this, so.. 
how can i **ping** the router and the internet by IP addess?
(uhm.. and another question... how can i know if the IP adress that show "ifconfig"  is correct for my network?)

---

### Post by Iowan on 2011-05-01
> **VR! said:**
> ... i'm not very good at this, so.. 
Neither am I... ;)
From a terminal, check **route -n** - post results, if possible.
Hopefully, one of the lines (probably the bottom one) will have a line with a "UG" flag. It will *probably* show a gateway of 192.168.1.1... but we'll see...
If it does, try (still from terminal):  **ping -c3 192.168.1.1**
If you get replies - GOOD! Then try: **ping -c3 74.125.225.17**

No replies - not so good...


(I'm *hoping* the router is also the DHCP server. If the machine is properly set up for DHCP, it should get an address in the same subnet as the router/DHCP Server. If it does, then it will probably get routing information from the server as well... but somewhere along the way, something has apparently gotten changed to work with school network. If you can successfully ping the internet by IP address, then DNS will be next...)

---

### Post by VR! on 2011-05-01
> **Iowan said:**
> Neither am I... ;) 
LOL  it makes me feel better .. i think (: 

> **Iowan said:**
> 
From a terminal, check **route -n** - post results, if possible.
Hopefully, one of the lines (probably the bottom one) will have a line with a "UG" flag. It will *probably* show a gateway of 192.168.1.1... but we'll see...
If it does, try (still from terminal):  **ping -c3 192.168.1.1**
If you get replies - GOOD! Then try: **ping -c3 74.125.225.17**


well 
here are the results:

ubuntu@VR:~$ route -n
Tabla de rutas IP del núcleo
Destino         Pasarela        Genmask         Indic Métric Ref    Uso Interfaz
ubuntu@VR:~$ route -n -
Uso: route [-nNvee] [-FC] [<AF>]           Muestra las tablas de ruteado del núcleo
       route [-v] [-FC] {add|del|flush} ...  Modifica la tabla de ruteado para AF

       route {-h|--help} [<AF>]              Sintaxis detallada de uso para el AF indicado.
       route {-V|--version}                  Muestra la/el versión/autor y sale.

        -v, --verbose descripción amplia
        -n, --numeric no se resolverán nombres
        -e, --extend             muestra otra/más información
        -F, --fib                muestra la base de información hacia adelante (predeterminado)
        -C, --cache              muestra la caché de ruteado en vez de la FIB

  <AF>=Use '-A <af>' o '--<af>'; por defecto: inet
  Lista de posibles familias de direcciones (que soportan el ruteado):
    inet (DARPA Internet) inet6 (IPv6) ax25 (AMPR AX.25) 
    netrom (AMPR NET/ROM) ipx (Novell IPX) ddp (Appletalk DDP) 
    x25 (CCITT X.25) 
ubuntu@VR:~$ ping -c3 192.168.1.1
connect: Network is unreachable
ubuntu@VR:~$ ping -c3 74.125.225.17
connect: Network is unreachable
ubuntu@VR:~$ 

uhm... at this moment.. i'm totally lost.. (: 
i hope this is what you tried to say.

---

### Post by zepolmot on 2011-05-01
Keeping an eye on this thread, having the exact same problem.

---

### Post by Iowan on 2011-05-01
Hmmm...
That would fall under the:> **Iowan said:**
> No replies - not so good...
Routing table is empty - so machine doesn't know where to send packets. My machine yields these results: ```
Iowan@Hardy:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0
Iowan@Hardy:~$ 
```
 Another thing to check would be: **less /etc/network/interfaces**
You will see similar results if you prefer to use **cat /etc/network/interfaces**
 Originally, this file would override Network Manager (not-so-much with later versions), so it might be helpful to see if it has a definition for eth0 interface.

Which version are you using - 10.04, 10.10, 11.04? (Network Manager is a little different between versions). There (probably) are some settings that need to be adjusted back. I presume your machine has an "auto eth0" connection.

---

### Post by VR! on 2011-05-02
> **Iowan said:**
> Hmmm...
That would fall under the:
Routing table is empty - so machine doesn't know where to send packets. My machine yields these results: ```
Iowan@Hardy:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0
Iowan@Hardy:~$ 
```
 Another thing to check would be: **less /etc/network/interfaces**
You will see similar results if you prefer to use **cat /etc/network/interfaces**
 Originally, this file would override Network Manager (not-so-much with later versions), so it might be helpful to see if it has a definition for eth0 interface.

Which version are you using - 10.04, 10.10, 11.04? (Network Manager is a little different between versions). There (probably) are some settings that need to be adjusted back. I presume your machine has an "auto eth0" connection.

i'm using 11.04, and yes my lap has an "auto eth0"connection.
here is what i found in interfaces:
```

auto lo
iface lo inet loopback

```

---

### Post by zepolmot on 2011-05-02
going to continue my lurking, less /etc/network/interfaces returns the same output that VR! is seeing

---

### Post by timefly on 2011-05-02
Try the following; if it works, repeat it each time you boot:
[INDENT] sudo ethtool -s eth0 port tp
[/INDENT] This forces eth0 to use the twisted pair ("tp") port. For me, the  network comes up instantly. No idea what port eth0 is trying to use in  preference to the twisted pair because ... well, there isn't much of a  choice between the one plug that it has. Besides, this worked just fine  with 10.10, and if I boot into an earlier kernel it works fine, too.

The 11.04 livecd has the same problem. Anyway, I hope this works for you.

---

### Post by Cheesehead on 2011-05-02
Your /etc/network/interfaces file looks correct. Network Manager automatically discovers and configures interfaces that are **not **specified in that file.

Your ifconfig looks correct. It looks like Network Manager is probably operating properly, has discovered eth0 and configured as it has been told to.

So it's time to look in your Network Manager settings. Right click on the NM icon, choose 'Edit Connections' --> 'Wired' tab.

If you have more than one option, tell us. If your professor **really** knew his stuff, he would have created a new connection option for you to use instead of mucking with your default settings. 

If you only have the option, 'Auto eth0', then 'Edit' it and look for any settings that look wrong. For example:
- 'Connect automatically' should be checked
- 'Use 802.1X security for this connection' should **not** be checked
- IPv4 Settings 'Method' should be 'Automatic (DHCP)

---

### Post by Iowan on 2011-05-02
> **Cheesehead said:**
>  If your professor **really** knew his stuff, he would have created a new connection option for you to use instead of mucking with your default settings. Speaking of whom...
Would the teacher be available to ask what changes were made?

(I haven't taken the Natty plunge yet - so I can't check a local machine.)

---

