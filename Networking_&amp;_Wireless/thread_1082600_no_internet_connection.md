---
title: "no internet connection"
date: 2009-02-28
forum: Networking &amp; Wireless
---

### Post by scotchtape on 2009-02-28
i have installed wubi ubuntu installer on my laptop, when i go to firefox it is able to connect to the internet no problem but when i go to a different website it tells me that it doesn't recognize the website i want to go to and it also says i may need to change my firewall settings.  i am pretty sure that my ubuntu doesn't have dns running how can i get it to work?

---

### Post by Iowan on 2009-02-28
You might add it to your */etc/resolv.conf*.  How do you get your IP address and internet connection? Reason for asking: The router/modem usually has a DHCP server that provides client with DNS addresses... but that may not necessarily be your case.

---

### Post by scotchtape on 2009-02-28
i went to the terminal and typed ifconfig, then i took the ip address that it found, then i set a static ip with the ip that it found, thats what gave me a connection, but when i tried to go to another website it didn't connect, thats how i realized that there was no dns

---

### Post by Iowan on 2009-02-28
If you are using a router, you can try adding it's address to */etc/resolv.conf*:```
nameserver 192.168.1.1
``` Otherwise, you could use OpenDNS servers (208.67.222.222 and/or 208.67.220.220).

---

### Post by scotchtape on 2009-02-28
ok i will give those a try, but where did you get those ip's from?

---

### Post by Iowan on 2009-03-01
I found those on  [OpenDNS]("https://www.opendns.com/start/") web page.

---

### Post by scotchtape on 2009-03-02
it doesn't work!  i followed the steps on that website for opendns.  does anyone know if there is anything else i can do?  i installed ubuntu as a program inside of windows using wubi, i didn't partition my harddrive

---

