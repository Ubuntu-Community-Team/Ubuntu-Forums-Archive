---
title: "Network Ping"
date: 2010-04-05
forum: Networking &amp; Wireless
---

### Post by progfool on 2010-04-05
Hello,
Well its been two weeks since I am using ubuntu 9.10 and I still cannot figure out this thing. I work behind a proxy managed by my university. Now, I cannot ping the other users on my network although they can ping me. Not to mention, I also cannot ping google.com. 
It says : ping: unknown host google.com

But I can ping the proxy server. Can someone help me?

---

### Post by r_s on 2010-04-05
have you set the proxy settings in system->preference-> network settings

---

### Post by progfool on 2010-04-05
Oh yes. I did.
I can use apt-get to install from shell prompt as well.

---

### Post by alarme on 2010-04-05
Hi,

Maybe is a DNS issue.  Check your DNS settings.
"unknown host" means that your box was unable to resolve google.com to an IP
Try ping to 8.8.8.8 to check connectivity
If this is ok, check your /etc/resolv.conf file
I don't know how proxy config works, but you can try to change your dns server for 8.8.8.8 (google dns)
If you can't ping to this, then must be a network config.

Check your network setting.
$ ifconfig
To see your IP and netmask.  You must have some like this:
[FONT="Courier New"]
eth0      Link encap:Ethernet  direcciónHW 00:00:00:00:00:00  
          Direc. inet:192.168.1.3  Difus.:192.168.1.255  Másc:255.255.255.0
          Dirección inet6: fe80::217:31ff:fe83:b8be/64 Alcance:Enlace
          ACTIVO DIFUSIÓN FUNCIONANDO MULTICAST  MTU:1500  Métrica:1
          Paquetes RX:4587 errores:0 perdidos:0 overruns:0 frame:0
          Paquetes TX:3776 errores:0 perdidos:0 overruns:0 carrier:0
          colisiones:0 long.colaTX:1000 
          Bytes RX:4607012 (4.6 MB)  TX bytes:522078 (522.0 KB)
          Interrupción:253 Dirección base: 0xc000 

lo        Link encap:Bucle local  
          Direc. inet:127.0.0.1  Másc:255.0.0.0
          Dirección inet6: ::1/128 Alcance:Anfitrión
          ACTIVO LOOPBACK FUNCIONANDO  MTU:16436  Métrica:1
          Paquetes RX:64 errores:0 perdidos:0 overruns:0 frame:0
          Paquetes TX:64 errores:0 perdidos:0 overruns:0 carrier:0
          colisiones:0 long.colaTX:0 
          Bytes RX:7360 (7.3 KB)  TX bytes:7360 (7.3 KB)
[/FONT]
where eth0 is my net adapter
192.168.1.3 is my IP
255.255.255.0 is my netmask

$ route -n

To see your router
[FONT="Courier New"]
Tabla de rutas IP del núcleo
Destino       Pasarela      Genmask        Indic Métric Ref  Uso Interfaz
192.168.1.0   0.0.0.0       255.255.255.0  U     0      0      0 eth0
169.254.0.0   0.0.0.0       255.255.0.0    U     1000   0      0 eth0
0.0.0.0       192.168.1.1   0.0.0.0        UG    100    0      0 eth0
[/FONT]
where 192.168.1.1 is the gateway for eth0
Ask to a friend the netmask and gateway of the college

---

### Post by progfool on 2010-04-05
Rite, I cannot ping 8.8.8.8.
So I guess its a network config problem as you stated.
And I did the two commands and I am getting almost similar response as yours. I have attached the output for the route command.


```

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    
172.16.58.0     *               255.255.254.0   U     1      0        link-local      *               255.255.0.0     U     1000   0        
default         172.16.59.254   0.0.0.0         UG    0      0        

```

My IP settings are automatic(DHCP) and hence I don't really know if I should change the mask and the default gateway.

---

