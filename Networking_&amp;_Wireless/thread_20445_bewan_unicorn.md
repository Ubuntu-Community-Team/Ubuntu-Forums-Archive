---
title: "bewan unicorn"
date: 2005-03-16
forum: Networking &amp; Wireless
---

### Post by paiva on 2005-03-16
i love ubuntu and i have this usb modem [http://www.bewan.com/bewan/products/adsl_modems/adslusbst.php](http://www.bewan.com/bewan/products/adsl_modems/adslusbst.php) and i'm having some problems connecting to the internet.
first i load pppoe with : modprobe pppoe
then : sudo insmod /lib/modules/2.6.4/extra/unicorn_usb_eth.ko
after this 2 commands i do : ifconfig dsl0 up
                                             pppd pty 'pppoe -I dsl0 -m 1452'
i saw this on a forum.... i dont know why.
take a look at this two screenshots of my ubuntu, 5.04 preview,

[img]http://img196.exs.cx/img196/6818/connect3lg.png[/img]
[img]http://img42.exs.cx/img42/3299/ifconfig8so.png[/img]


these are the contents of my /etc/ppp/options file 
lock
ipparam ppp0
noipdefault
noauth
defaultroute
user "user@domain.com"
noaccomp
noccp
nobsdcomp
nodeflate
nopcomp
novj
lcp-echo-interval 20
lcp-echo-failure 3
maxfail 25
updetach
usepeerdns
holdoff 4
persist

i appreciate any help, thank you all

---

### Post by paiva on 2005-03-17
does anyone know how to solve this ?

---

### Post by paiva on 2005-03-18
pleaseeeeee
i need your help

---

### Post by paiva on 2005-03-29
i'm sad :(
no one can help me :(

---

### Post by zasf on 2006-03-29
[QUOTE=paiva]i'm sad :(
no one can help me :([/QUOTE]

I recently installed unicorn driver for a bewan modem on Dapper, you may want to check this [http://battlehorse.homelinux.net/w/Wiki.jsp?page=UnicornDriverUSBADSLModem](http://battlehorse.homelinux.net/w/Wiki.jsp?page=UnicornDriverUSBADSLModem)

---

### Post by www.rzr.online.fr on 2006-05-18
[QUOTE=zasf]I recently installed unicorn driver for a bewan modem on Dapper, you may want to check this [http://battlehorse.homelinux.net/w/Wiki.jsp?page=UnicornDriverUSBADSLModem](http://battlehorse.homelinux.net/w/Wiki.jsp?page=UnicornDriverUSBADSLModem)[/QUOTE]

Yours is not a bewan modem , but I managed to for the bewan usb adsl st

[http://rzr.online.fr/q/unicorn-modules](http://rzr.online.fr/q/unicorn-modules)

---

