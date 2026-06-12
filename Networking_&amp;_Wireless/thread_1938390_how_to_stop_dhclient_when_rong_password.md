---
title: "how to stop dhclient when rong password"
date: 2012-03-09
forum: Networking &amp; Wireless
---

### Post by akam2008 on 2012-03-09
how to stop dhclient when rong password
hola todo

for connect to wireless network ubuntu manully just use this


ubuntu@ubuntu:~$ sudo service network-manager stop
ubuntu@ubuntu:~$ sudo iwconfig wlan0 essid wlan_xxxx key xxxxxxxxxx
ubuntu@ubuntu:~$ sudo dhclient wlan0


funcionando perfectamente cuando el claves o el key es correcto y da en mensaje 


el problema es cuando el claves o el key no es correcto no da mensaje ni nada solo sigue buscando o no puede stoped dhclient para un otro comando porque es sigue buscando y no puedo hacer nada solo esperar hasta que ? no lo se

quiero saber un comando como dhclient pero cuando el claves o el key no es correcto da un mensaje después un 5 segundo o mas

muchas gracias

---

