---
title: "How to recognize intranet host server name"
date: 2010-02-19
forum: Networking &amp; Wireless
---

### Post by TaTaskan on 2010-02-19
Hi,

I am using Ubuntu on a Windows network.

One of the computers have apache server (working), it has 192.168.1.6 IP, and the name of the computer on the network is "servidor"

I can't access from ubuntu, if I type [http://servidor](http://servidor) or 192.168.1.6, it goes to [www.servidor.com](www.servidor.com), but I can access shared folders, just the host intranet server I can't

I have vmware with windows xp, and I can access [http://servidor](http://servidor) from there, but not from Firefox in Ubuntu.

I tried to search on google without success, how can I solve my problem, or where to look?

Thanks

---

### Post by joberly on 2010-02-19
The easy way is to simply edit your /etc/hosts file with a line like this:

192.168.1.6    servidor

But let me ask to clarify, this may change things, you CANNOT access the website by using the internal IP ?

---

### Post by ant2ne on 2010-02-19
Windows boxes often use broadcasts to determine hostnames in a workgroup network. linux does not. You need to edit the /etc/hosts files or put up a functional dns server that can point servidor.local to the correct IP (not servidor.com as that is already out on the internet)

---

### Post by TaTaskan on 2010-02-19
Thank you!

I did what you told me an now it works

joberly:  I cound't access with 192.168.1.6 neither with [http://servidor](http://servidor),  now I can with both

thanks again

---

### Post by joberly on 2010-02-19
Awesome!

---

