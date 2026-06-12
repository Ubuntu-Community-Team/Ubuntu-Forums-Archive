---
title: "WLAN Sniffer...possible driver issue? :S"
date: 2005-12-08
forum: Networking &amp; Wireless
---

### Post by adduds on 2005-12-08
Hey all! 

hope everyone is well everywhere :).

I d/led+installed airsnort using synaptic i run it through term. but when i execute 'Scan' in the airsnort gui i get this error in terminal?

```
adduds@adtop:~$ airsnort
/sbin/wlanctl-ng  lnxreq_ifstate ifstate=enable > /dev/null
sh: /sbin/wlanctl-ng: No such file or directory
up: error fetching interface information: Device not found

```

could someone please tell me what it is??... thanks

EDIT: I found and installed wlanctl-ng in synaptic.... but now i get this error lol

```
adduds@adtop:~$ airsnort
/sbin/wlanctl-ng eth1 lnxreq_ifstate ifstate=enable > /dev/null
wlanctl-ng: Operation not supported
SIOCSIFFLAGS: Permission denied

```

Any help would be appreciated thanks :)

cheers, ad

---

### Post by darth_vector on 2005-12-08
i have never used airsnort, but ethereal has to be run as root in order to talk to the network card. try

sudo airsnort

---

### Post by towsonu2003 on 2005-12-08
your particular driver might not be supported by airsnort as well. if sudoing doesn't work, take a look here to see if kismet (and thus airsnort) supports it: [http://www.kismetwireless.net/](http://www.kismetwireless.net/)

---

### Post by adduds on 2005-12-08
[QUOTE=towsonu2003]your particular driver might not be supported by airsnort as well. if sudoing doesn't work, take a look here to see if kismet (and thus airsnort) supports it: [http://www.kismetwireless.net/](http://www.kismetwireless.net/)[/QUOTE]

Thanks for the replies guys :).

Ummmm sudoing did not work. 

Where on kismetwireless.net do i see if my driver is supported?

---

### Post by adduds on 2005-12-08
[QUOTE=darth_vector]i have never used airsnort, but ethereal has to be run as root in order to talk to the network card. try

sudo airsnort[/QUOTE]

Ya i had ethereal for a while, but i didn't really understand/like it, ya i had already tried sudo airsnort but it just a;lsfkja;lsdjfalkjalf etc.. in consol lol just a lot of errors, thanks anyways mate

---

