---
title: "Socks5 Server With Multiple IP Addresses"
date: 2012-05-05
forum: Networking &amp; Wireless
---

### Post by DriftBoris on 2012-05-05
Hello all, i have been using dante socks server but on his config i can use only one ip address so if i put 
external: eth0
external: eth0:0

IP 0 and IP 0:0 will be same when i chek ip coz its ponited on maine ip.

What i need, i need some socks5 server that can use multiple ip addresses, i have already search on forum for this issues but cant find anything.Thanks

---

### Post by poolet on 2012-05-05
> **DriftBoris said:**
> Hello all, i have been using dante socks server but on his config i can use only one ip address so if i put 
external: eth0
external: eth0:0

IP 0 and IP 0:0 will be same when i chek ip coz its ponited on maine ip.

What i need, i need some socks5 server that can use multiple ip addresses, i have already search on forum for this issues but cant find anything.Thanks


log in as admin terminal.. 

cd /etc 
vi sockd.conf or gedit sockd.conf (if the vi isn't works)

add individual ip address of valid clients by adding to the "sockd.conf"

like following:: 

```
client pass {
from: 192.168.20.10 port 1025-32767 to:0.0.0.0/0

}
```

replace "192.168.10.10 with the ip address you want to add, 
and the port "1025-32767" with the range of ip ports...

save the "sockd.conf: end exit

**::Note::  **I am not sure if it's that you want.. this is an old method that I had found.... 
check also  the links below for more information... The most important thing is the individual ip address 
that you will add  to be valid also before you continue make sure that the ports are valid.... 
Please let me know if it's works..!!

[http://linux.die.net/man/5/sockd.conf](http://linux.die.net/man/5/sockd.conf)

[http://www.inet.no/dante/doc/](http://www.inet.no/dante/doc/)

[http://ininjas.com/forum/index.php?topic=1901.0](http://ininjas.com/forum/index.php?topic=1901.0)

[]("http://www.google.com.cy/url?sa=t&rct=j&q=dante%20socks%20server%20multiple%20ip&source=web&cd=9&ved=0CGEQFjAI&url=http%3A%2F%2Fwww.digipedia.pl%2Fman%2Fdoc%2Fview%2Fdanted.conf.5%2F&ei=ZwelT6q1K6j80QWXhfWaBA&usg=AFQjCNG9-Fng4ngOsHjwvj-eu3f8Dm8Sog&cad=rja")[http://www.digipedia.pl/man/doc/view/danted.conf.5/](http://www.digipedia.pl/man/doc/view/danted.conf.5/)

---

### Post by DriftBoris on 2012-05-05
Not helpful but thanks.

---

### Post by DriftBoris on 2012-05-07
BEST SOLUTION:

[http://ssspl.sourceforge.net/](http://ssspl.sourceforge.net/)

fixs all my prbolems :) and its simple

---

