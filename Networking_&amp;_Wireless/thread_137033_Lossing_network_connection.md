---
title: "Lossing network connection"
date: 2006-02-27
forum: Networking &amp; Wireless
---

### Post by dvejnovic on 2006-02-27
I have server with some clients. On server machine I running web, nfs and samba servers.

And now is happening that connection betwen server and clients are lossing every cca. 20 hours. I look into log files for finding reason why this happend.
Nothing to find!!!:confused: 

How can I determine what is wrong???

---

### Post by hajk on 2006-02-27
Wireless? Ndiswrapper? What happens when you lose the connection, machine freezes?

---

### Post by claes on 2006-02-27
Power saving on some machine? Just guessing.

Claes

---

### Post by dvejnovic on 2006-02-28
No - without power saving...

---

### Post by dvejnovic on 2006-02-28
[QUOTE=hajk]Wireless? Ndiswrapper? What happens when you lose the connection, machine freezes?[/QUOTE]

No freeze - from clients cannot ping server...

Just guess:
1. before upgrade kernel with latest version I installed new usb camera on server and program for watcing it - motion ([http://www.lavrsen.dk/twiki/bin/view/Motion/WebHome](http://www.lavrsen.dk/twiki/bin/view/Motion/WebHome))
2. all working OK
3. then upgrade kernel with latest version
4. I have command in cron which start and stop motion daemon
5. when motion was started from cron the network die

---

### Post by dvejnovic on 2006-02-28
[QUOTE=dvejnovic]No freeze - from clients cannot ping server...

Just guess:
1. before upgrade kernel with latest version I installed new usb camera on server and program for watcing it - motion ([http://www.lavrsen.dk/twiki/bin/view/Motion/WebHome](http://www.lavrsen.dk/twiki/bin/view/Motion/WebHome))
2. all working OK
3. then upgrade kernel with latest version
4. I have command in cron which start and stop motion daemon
5. when motion was started from cron the network die[/QUOTE]

I'm shure now - clients cannot ping server after on server was started motion daemon.:cry: 
Please, help!

---

