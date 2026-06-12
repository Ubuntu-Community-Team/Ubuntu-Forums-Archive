---
title: "Super-pathetic Samba access speed, Lucid 10.04"
date: 2010-10-10
forum: Networking &amp; Wireless
---

### Post by luvshines on 2010-10-10
I have Samba share setup on my Laptop running Lucid Lynx, **for my home network, wireless**

The copy speed for my movies, when I access them from Windows laptop is too pathetic.
**[COLOR="Blue"]Took 22 min to copy around ~1.6GB of data, giving me a speed of only 1.2 MB/s[/COLOR]**

Haven't seen nething that bad :D
What settings do I have on my server which can improve the copy speed ??

Smb.conf is pretty simple and default
```

[global]
   workgroup = WORKGROUP
   netbios name = scooby-laptop
   server string = "ScoobyDo server (Samba, Ubuntu)"
   dns proxy = no
   log file = /var/log/samba/log.%m
   max log size = 1000
   syslog = 0
   panic action = /usr/share/samba/panic-action %d
   security = user
   encrypt passwords = true
   passdb backend = tdbsam
   obey pam restrictions = yes
   unix password sync = yes
   passwd program = /usr/bin/passwd %u
   passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
   pam password change = yes
   map to guest = bad user
   usershare allow guests = yes

[moveez]
   comment = Movies for Sharing
   path = /home/scoob/movies
   browseable = yes
   read only = no
   guest ok = no

```

---

### Post by sikander3786 on 2010-10-10
Samba has been quite fast for me with the default settings since I am using it.

You can add these lines to the global section of smb.conf file and then restart Samba and see if it helps.

```
socket options = TCP_NODELAY IPTOS_LOWDELAY SO_RCVBUF=65536 SO_SNDBUF=65536
```

---

### Post by luvshines on 2010-10-10
Didn't help much. 976 MB still taking 15 Mnts @ ~1.1 MB/s

---

### Post by sikander3786 on 2010-10-10
Which wireless card have you got? What is the actual connection speed? Can you achieve better speeds with connections other than Samba?

---

### Post by luvshines on 2010-10-11
> **sikander3786 said:**
> Which wireless card have you got? 

Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN [Kedron] Network Connection (rev 61)
	Subsystem: Intel Corporation Device 1010
	Flags: bus master, fast devsel, latency 0, IRQ 31
	Memory at df2fe000 (64-bit, non-prefetchable) [size=8K]
	Capabilities: [c8] Power Management version 3
	Capabilities: [d0] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable+
	Capabilities: [e0] Express Endpoint, MSI 00
	Capabilities: [100] Advanced Error Reporting <?>
	Kernel driver in use: iwlagn
	Kernel modules: iwlagn

> What is the actual connection speed? 
Connects at 54 Mbps

> Can you achieve better speeds with connections other than Samba?

I'll do the testing with other protocols and share the results.
On a wired network, the Samba share speed was ~10 MB/s

---

### Post by luvshines on 2010-10-21
Tried FTP on the same network.

That too giving ~1MB/s speed, :(

Still to try NFS

Assuming networking constraints, I'll mark this as SOLVED. And will keep it updated if I find nething interesting

---

