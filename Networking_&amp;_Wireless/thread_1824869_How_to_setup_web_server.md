---
title: "How to setup web server"
date: 2011-08-14
forum: Networking &amp; Wireless
---

### Post by kingkong22 on 2011-08-14
I have ubuntu 11.04, so I type the command python -m SimpleHTTPServer 7000, this simple web server will be running on. 
then open firefox, type [http://localhost:7000](http://localhost:7000) in URL and hit enter,
it will show up the list of files of the directory where I typed the command python -m SimpleHTTPServer 7000 on, then select any one file, right click mouse, choose save link as, the file will be downloaded. this works also for local network machines.the issue is
that my friend, in a remote place, wants to download my files via this simple web server, but it does not work, even I tell him my IP 
address and port number. it seems he can't access it at all. I am wondering how to setup my ubuntu so that my friends from the outside of my network can access the files that I intend to provide. Thank you in advance !!!

---

### Post by Iowan on 2011-08-14
If you haven't already, you may need to configure your router to forward the port to your server. I presume you're providing the external IP address to your friend.

---

### Post by kingkong22 on 2011-08-15
> **Iowan said:**
> If you haven't already, you may need to configure your router to forward the port to your server. I presume you're providing the external IP address to your friend.

Thank you so much !!!

---

