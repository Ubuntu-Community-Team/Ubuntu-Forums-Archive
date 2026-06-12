---
title: "Wireless Speed Poll"
date: 2009-06-15
forum: Networking &amp; Wireless
---

### Post by thrones on 2009-06-15
Just kind of a quick poll. What's your average wireless speed within your network? What kind of speed do you get when transferring files between machines?

Just wondering if what I'm getting is average. About 900KB/s transferring files using WPM300N wireless-n linksys cards on both machines and a netgear wireless-n router using native linux drivers, no ndiswrapper. Seems like it should be faster, but just thought I'd ask what others' speeds are like for a reference.

---

### Post by MaindotC on 2009-06-16
There is no such thing as "average" and it depends on several factors, namely the protocol you are using, machine speed, memory, configuration, daemons, frequenecy used, noise, pc bus, etc.

---

### Post by thrones on 2009-06-16
> **strAlan said:**
> There is no such thing as "average" and it depends on several factors, namely the protocol you are using, machine speed, memory, configuration, daemons, frequenecy used, noise, pc bus, etc.

So what kind of speeds do you get when transferring files?

---

### Post by superprash2003 on 2009-06-16
take a look at this , would probably answer your questoin [http://www.prash-babu.com/2009/05/nfs-vs-samba-vs-ssh-data-transfer-speed.html](http://www.prash-babu.com/2009/05/nfs-vs-samba-vs-ssh-data-transfer-speed.html)

---

### Post by thrones on 2009-06-16
> **superprash2003 said:**
> take a look at this , would probably answer your questoin [http://www.prash-babu.com/2009/05/nfs-vs-samba-vs-ssh-data-transfer-speed.html](http://www.prash-babu.com/2009/05/nfs-vs-samba-vs-ssh-data-transfer-speed.html)

Wow, is that the type of speeds I should be expecting? Is that what you get?

---

### Post by MaindotC on 2009-06-17
Very nice link, prash :D

---

### Post by superprash2003 on 2009-06-27
@thrones
 yes , i get similar speeds..
@strAlan
  Thanks!

---

### Post by cariboo on 2009-06-27
2MB/sec seems to be an average between my 3 wireless devices:

[list]
[*] D-Link WUA-1340
[*] HP laptop with  Prism2 chipset
[*] Staples store brand Zydas with zd1211 chipset
[/list]

---

### Post by MaindotC on 2009-06-27
Also NFS seems to be a faster transfer protocol.  I haven't examined the packet or frame assembly so I'm not sure what kind of overhead it includes, but just basic file transfer tests show NFS to be the fastest.

---

