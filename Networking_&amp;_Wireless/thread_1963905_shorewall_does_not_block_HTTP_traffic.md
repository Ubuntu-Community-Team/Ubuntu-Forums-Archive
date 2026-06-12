---
title: "shorewall does not block HTTP traffic"
date: 2012-04-23
forum: Networking &amp; Wireless
---

### Post by senzacionale on 2012-04-23
i use this howto
```

http://wiki.vpslink.com/HOWTO:_Debian_Etch:_Install_Shorewall_firewall
```

i just change 

```
HTTP/ACCEPT     net   $FW
```

to

```
HTTP/REJECT     net   $FW
```

how can I block HTTP access with shorewall firewall?

---

### Post by jonobr on 2012-04-23
Hello

Just checking if its running?

```
sudo /etc/init.d/shorewall status
```

If it is, did you try restarting, maybe that will reread the rules
as what you describe, it sounds about right.

```
sudo /etc/init.d/shorewall stop
sudo /etc/init.d/shorewall stop
```

Also, any reason in particular why your sticking with Shorewell?

Have you tried firestarter

All the best!

---

### Post by lisati on 2012-04-23
> **jonobr said:**
> 
Have you tried firestarter


I understand that firestarter is depecrated, but I'm open to correction.
UFW and GUFW are preferred by many users these days.

---

