---
title: "Can connect to VPN, but cannot browse the internet"
date: 2013-09-02
forum: Networking &amp; Wireless
---

### Post by martinrame on 2013-09-02
Hi, I can connect and use a Windows VPN using the graphical client from the XUbuntu toolbar (I'm on 12.04 with XFCE 4.10), but when connected I cannot browse the internet.

Here's the output of the "route" command when I'm connected to the VPN:

```
Tabla de rutas IP del núcleo
Destino         Pasarela        Genmask         Indic Métric Ref    Uso Interfaz
default         *               0.0.0.0         U     0      0        0 ppp0
10.1.1.193      *               255.255.255.255 UH    0      0        0 ppp0
link-local      *               255.255.0.0     U     1000   0        0 eth0
host194.190-228 192.168.0.4     255.255.255.255 UGH   0      0        0 eth0
host194.190-228 192.168.0.4     255.255.255.255 UGH   0      0        0 eth0
192.168.0.0     *               255.255.255.0   U     1      0        0 eth0
```

I don't know what should I enter into the "routes" config dialog.

---

### Post by GwL3eNC on 2013-09-02
Hi,

if i had to login via vpn on a server (not mine, for work) i can't use my own internet connection.
I had to ask the administrators about the proxy server which i had to set somewhere in
the settings of mozilla. After this i was able to use the connection provided by the server.
After my work i had to set back the mozilla settings to use my own connection again

---

