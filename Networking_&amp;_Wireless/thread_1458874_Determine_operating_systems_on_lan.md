---
title: "Determine operating systems on lan"
date: 2010-04-20
forum: Networking &amp; Wireless
---

### Post by terbor on 2010-04-20
How can I send out a broadcast from one device to the other machines on the LAN to reply with their operating system.

Thanks

---

### Post by doas777 on 2010-04-20
nmap, pOf, or xprobe are probably your best bet unless you want to write a rather complicated program to fingerprint based on the idiosyncrasies of each os's stack. 

[http://en.wikipedia.org/wiki/TCP/IP_stack_fingerprinting](http://en.wikipedia.org/wiki/TCP/IP_stack_fingerprinting)
[http://sectools.org/os-detectors.html](http://sectools.org/os-detectors.html)
[http://nmap.org/book/osdetect.html](http://nmap.org/book/osdetect.html)

---

### Post by spiky001 on 2010-04-20
have you tried nmap or there is zenmap gui

---

### Post by terbor on 2010-04-20
I am using nmap I just haven't found the right combination yet, I need to make a call to get the IPs and then I guess make another call to find the OS iterating through each IP?

What about using the hostname?  I am using smbtree to find the devices with samba on it, maybe I can use the host name somehow?

---

### Post by spiky001 on 2010-04-20
what is it you are trying to do?

---

### Post by terbor on 2010-04-20
The end goal is to get the operating system.  I am using nmblookup right now, this works with the hostname to give me the IP, the problem with nmap is the time it takes to run a query.  I need to present this data in a timely fashion to the end user.

---

### Post by spiky001 on 2010-04-20
have a look here at commands

[http://www.workrobot.com/sysadmin/security/nmap-syntax.html](http://www.workrobot.com/sysadmin/security/nmap-syntax.html)

---

### Post by terbor on 2010-04-20
Ok great, thanks for the help.  I think I know how I am going to tackle this one.

---

