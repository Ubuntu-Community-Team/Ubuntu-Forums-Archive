---
title: "Ubuntu server 12.4 static ip problem"
date: 2012-05-13
forum: Networking &amp; Wireless
---

### Post by Tsquad on 2012-05-13
Hello, im running server 12.4 LTS on an old pc. I can get the static ip working after i add the "nameserver xxx.xxx.xxx.xxx" to /etc/resolv.conf But after a reboot my resolv.conf file is over written and my internet connecgion does not work. I can still ssh to it, change the resolv.conf file and restart my interfaces but id rather it work from boot up. 

Also, i have already tryd to chattr +i /etc/resolv.conf and it sends back "chattr: Operation not supported while reading flags on /etc/resolv.conf"

Anyone know how to fix this?

SOLVED: ok so i had to add the "dns-nameservers x.x.x.x" to my /etc/network/interfaces file. This fixed my resolv.conf file problem.

---

### Post by johnnybegood on 2012-05-31
Thanks a lot!;)

---

### Post by enlinea777 on 2012-09-04
He visto que si agrehas los dns-nameserver en interfaces esta no toma los server de resolucion de nombres

Gracias a la ayuda encontrada en esta pagina he resuelto el problema.
[http://manpages.ubuntu.com/manpages/lucid/man8/resolvconf.8.html](http://manpages.ubuntu.com/manpages/lucid/man8/resolvconf.8.html)
Para hacer que resolv.conf no cambie cuando la editamos manualmente hacemos esto en la terminal:
sudo resolvconf --disable-updates
despues:
sudo resolvconf -a eth0 # o tu interfas de red
luego editamos manualmente /run/resolvconf/resolv.conf

agregando un maximo de 2 DNS servers.
saludos
P.D. no olvidar reiniciar:
sudo /etc/init.d/networking restart


[SIZE=3]English [/SIZE][SIZE=3]translation[/SIZE]

I have seen that if the dns-nameserver agrehas in interfaces that do not take the name resolution server
Thanks to the help found here have solved the problem.
 [http://manpages.ubuntu.com/manpages/lucid/man8/resolvconf.8.html](http://manpages.ubuntu.com/manpages/lucid/man8/resolvconf.8.html)
 To make resolv.conf not change when we edit manually do this in the terminal:
 sudo resolvconf --disable-updates
 after:
 sudo resolvconf -a eth0 # or your network Interfas

 then manually edit /run/resolvconf/resolv.conf

 adding a maximum of two DNS servers.
 thanks
P.S. not forget to restart:
sudo  /etc/init.d/networking restart

:KS:KS:KS:KS:KS

---

