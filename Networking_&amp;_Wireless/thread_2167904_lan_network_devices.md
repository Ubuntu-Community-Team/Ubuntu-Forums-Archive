---
title: "lan network devices"
date: 2013-08-15
forum: Networking &amp; Wireless
---

### Post by jim8 on 2013-08-15
Hello! 
I need to know how to be able to find lan connected devices as easy as possible ( Like WIndows or Mac where just all the devices appear)
The one device has hard disk and i want to put data in it .

---

### Post by ajgreeny on 2013-08-15
I'm not sure if this is the easiest, but assuming your lan is through a router you can go to the router configuration page in a browser and probably there you can check attached devices. On my router it is possible to reserve IP addresses for devices which, for example, makes using a network printer much easier as it is always at the same IP address.

I am sure there may be ways with the command line, but at the moment I don't know how.  It is something I must look into; if I find an answer I'll come back again with the info.

EDIT:
OK, install **nmap** and then run a simple command ```
nmap -sP 192.168.0.1/24
``` where 192.168.0.1 is your router IP, and it will scan addresses up to 192.168.0.24. It will not tell you which device is which, but it is a start.

---

### Post by steeldriver on 2013-08-15
If your intention is to copy files between the devices, then you are going to need to set up some kind of networked file sharing - most likely SAMBA / cifs (assuming the majority of your devices are running Windows, or at least are 'Windows compatible'). Once you have done that (and got with the same workgroup defined everywhere) the devices will be browsable via the nautilus file manager by going to Browse Network --> Windows Network --> xxx pretty much just like in Windows

OTOH if you *only* need to probe the LAN to see what devices are present then you can install 'nmap' and scan from the command line - e.g. a simple 'ping scan' of the 192.168.1.xxx LAN using nmap

```
nmap -sP 192.168.1.0/24
```

- but it sounds like that's not want you are really asking

---

