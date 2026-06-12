---
title: "manual ip setup on live cd"
date: 2008-12-25
forum: Networking &amp; Wireless
---

### Post by Thasaidon on 2008-12-25
Hi guys,

Normally when running linux, I use this to setup my network for quick access to my lan:
```
sudo ifconfig eth0 192.168.0.123/24 up
sudo route add default gw 192.168.0.1
sudo echo nameserver 208.67.220.220 > etc/resolv.conf
```

However, when running a system from the Ubuntu 8.04 live cd, I get a "permission denied" on the last command.

When I checked to see if **etc/resolv.conf** existed, it wasn't there.
However, when I use the GUI to configure the interface, then the **resolv.conf** file is created, but I still can't edit it.

Is there a way to configure the nameserver from the commandline while running the live cd?
or do I HAVE to do it via the GUI?

---

### Post by Iowan on 2008-12-26
No guarantees, but try it with /etc/resolv.conf

---

### Post by albinootje on 2008-12-26
> **Thasaidon said:**
> 
sudo echo nameserver 208.67.220.220 > etc/resolv.conf[/code]


A few weeks ago I noticed that :
```

sudo echo "some text" > some-file.txt

```
Would give an error, and would fill that txt-file with a sudo error-message.
See for yourself, by trying again :
```

sudo echo nameserver 208.67.220.220 > etc/resolv.conf
sudo cat /etc/resolv.conf

```
.. I haven't found a nice solution for this problem

---

### Post by Thasaidon on 2008-12-26
> **Iowan said:**
> No guarantees, but try it with /etc/resolv.conf
Nope, that doesn't work either, and neither does **./etc/resolv.conf**
Tried them all...

[QUOTE=albinootje]...Would give an error, and would fill that txt-file with a sudo error-message.[/QUOTE]
If I use the **sudo echo "some text" > etc/resolv.conf** then the resolv.conf file is not created at all. It looks as if the /etc folder is set read only by default, and only sytem deamons like the network setup tool are allowed to create and write files there...

---

### Post by albinootje on 2008-12-26
> **Thasaidon said:**
> Nope, that doesn't work either, and neither does **./etc/resolv.conf**
Tried them all...


If I use the **sudo "some text" > etc/resolv.conf** then the resolv.conf file is not created at all. It looks as if the /etc folder is set read only by default, and only sytem deamons like the network setup tool are allowed to create and write files there...

Hmm, weird :|
Are you using the 8.04 or 8.0.4.1 desktop iso image ? 32bit or 64bit ?
I'd like to test this to see whether it is possible to reproduce this error.

---

### Post by Thasaidon on 2008-12-26
> **albinootje said:**
> Are you using the 8.04 or 8.0.4.1 desktop iso image ? 32bit or 64bit ?
I'd like to test this to see whether it is possible to reproduce this error.8.04.1 32bit Desktop Edition

Thanx for the help sofar.

---

### Post by kevdog on 2008-12-26
Would something like this do 

echo "nameserver xxxxxx" | sudo tee -a /etc/resolv.conf


I would investigate the tee command since I think this is what you want!

---

### Post by albinootje on 2008-12-26
> **Thasaidon said:**
> 
```
sudo ifconfig eth0 192.168.0.123/24 up
sudo route add default gw 192.168.0.1
sudo echo nameserver 208.67.220.220 > etc/resolv.conf
```


OK, I've justed tested this with the Ubuntu 8.04.1 with the new recommendation by kevdog :

echo "nameserver xxxxxx" | sudo tee -a /etc/resolv.conf

That worked for me.

/etc/resolv.conf did exist, but I removed it to test this.
Editing that file was also not a problem.

A little confusing, with bash <tab> name-completion, was that the directory /etc/resolvconf already existed.

---

### Post by Thasaidon on 2008-12-27
> **albinootje said:**
> A little confusing, with bash <tab> name-completion, was that the directory /etc/resolvconf already existed.
yup, I noticed that too :D

Well, the command seems to work just fine! 
Thanx for the help guys, it's much appreciated.

Now all I need to do is get this in a script on the live cd itself.

---

