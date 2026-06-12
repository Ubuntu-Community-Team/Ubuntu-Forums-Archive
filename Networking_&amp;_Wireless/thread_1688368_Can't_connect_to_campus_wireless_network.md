---
title: "Can't connect to campus wireless network"
date: 2011-02-15
forum: Networking &amp; Wireless
---

### Post by Keatonguy on 2011-02-15
I've got Ubuntu 10.10 loaded on my HP mini, and haven't had any problem with wireless connection before. But since I've started going to my local community college, I've been completely unable to connect to the campus-wide wireless network save for once. I don't know anything about the network other than that it has no encryption.

I have only attempted to connect, thus far, using Ubuntu's built-in autoconnector. Is there a way that I can see what issue it's having, maybe get an error output? Thank in advance for any help you can give.

EDIT: Okay, I cleaned the stupid out of my head and used tail -f to check the syslog. The auto connector can't seem to negotiate a DHCP lease, it just times out trying to talk to 255.255.255.255 on port 67. I can't think of why this would be, no one else I've talked to with a laptop has any problem connecting. Is there some, more sophisticated method of working out an IP address that Windows/Macintosh knows to do and Ubuntu doesn't?

---

### Post by jerrrys on 2011-02-17
before my lappy crashed and burned i use to have better luck (still not a 100%) with WIDC.  its in the software center

---

### Post by grahammechanical on 2011-02-17
I am just guessing but has network manager set up a connection for this connection? Are the settings correct? Is it set to Automatic (DHCP)?

If my home modem/router is switched off then Network manager will connect to any nearby unsecured wireless network because I am set to connect automatically. If it cannot find my wireless connection it will find someone else's connection. It should do the same for you. Unless it somehow has set a connection for this wireless network and it now has the wrong settings.

Regards.


Regards.

---

### Post by femiaiyeku on 2011-02-17
Actually i run windows 7 and ubuntu 10.10 on my  laptop(dual  boot) and lately when i boot into my ubuntu 10.10 ,my  internet connection times  out and it fails to
reconnect, the signal quality is pretty good, i connect  via  wireless  connection(WI-FI) and when i boot into windows 7, i get access  to the  internet ,my internet seems to work pretty fine with windows 7
but i m  having problems with using the internet on my Ubuntu 10.10,pls give me  a
direction on what to do ...

---

