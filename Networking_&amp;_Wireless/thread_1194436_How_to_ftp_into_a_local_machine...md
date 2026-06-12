---
title: "How to ftp into a local machine.."
date: 2009-06-22
forum: Networking &amp; Wireless
---

### Post by akshay.sulakhe on 2009-06-22
Hello friends...i have a router and 2-3 computers at my place...So as u can understand..they are connected in wireless...so how can i just use ftp to access files from other machine...i used to do that on Sabayon(Gentoo)...i did sftp://i/p address/...so how to that on Ubuntu...I have jaunty installed...Do reply..thanks:)

---

### Post by jonobr on 2009-06-22
To get ftp running , you will need to install an ftp program.
The simplest of these is vsftp
This is assuming that your ubuntu box is the server.

In order to do secure ftp,(sftp)  you need to install openssh server.
This will also allow you to ssh and scp to the client.

You can install all of these in synaptic, just put vsftp or opnssh in the search and you should find it.

Thanks

---

