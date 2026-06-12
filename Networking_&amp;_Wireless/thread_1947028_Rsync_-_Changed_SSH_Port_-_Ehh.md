---
title: "Rsync - Changed SSH Port - Ehh?"
date: 2012-03-26
forum: Networking &amp; Wireless
---

### Post by Roasted on 2012-03-26
I changed my SSH port from the default port 22. Now when I SSH in I have to do:

user@server -p 111

(where 111 is the new port)

I had an rsync script set up before, which reads something like:

rsync -az /home/fred fred@192.168.1.150:/media/storage/fred

I tried to plug in -p 111 after the .150 but no dice. Is that not what I'm supposed to do?

---

### Post by agillator on 2012-03-26
Add an option '--rsh "ssh -p 111" to your original command line. See the man page for an explanation.

---

### Post by Roasted on 2012-03-26
Ehh, not really doing anything. It drops to a > prompt.

---

### Post by papibe on 2012-03-26
Probably you missed copying a quote. Try this:
```
rsync -az -e "ssh -p 111" /home/fred fred@192.168.1.150:/media/storage/fred
```
-e is the same as --rsh

Regards.

---

### Post by haqking on 2012-03-26
out of interest any reason for choosing port 111 which is in the well known range and used by sunrpc/portmapper service

when assiging ports you should choose one in the dynamic range 49152 to 65535 or at least in the 1024 to 49151 range

---

### Post by Roasted on 2012-03-26
> **haqking said:**
> out of interest any reason for choosing port 111 which is in the well known range and used by sunrpc/portmapper service

when assiging ports you should choose one in the dynamic range 49152 to 65535 or at least in the 1024 to 49151 range

I only used 111 as an example for this particular post. :guitar:


> **papibe said:**
> Probably you missed copying a quote. Try this:
```
rsync -az -e "ssh -p 111" /home/fred fred@192.168.1.150:/media/storage/fred
```
-e is the same as --rsh

Regards.


That was it - thanks much!

---

### Post by haqking on 2012-03-27
> **Roasted said:**
> I only used 111 as an example for this particular post. :guitar:



gotcha, i did wonder ;-)

Peace

---

