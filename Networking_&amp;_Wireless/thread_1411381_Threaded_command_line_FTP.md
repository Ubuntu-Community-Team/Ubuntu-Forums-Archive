---
title: "Threaded command line FTP"
date: 2010-02-19
forum: Networking &amp; Wireless
---

### Post by fugaki on 2010-02-19
Does anyone know of a CLI program that can thread sending files to an ftp server?

For example:

ftp -i <whateverserver>
mput *
(10 get sent at once instead of one at a time)

Thanks for the help.

---

### Post by jobix on 2010-02-19
If you just want to be able to send them one by one, you could use a simple shell script like this:

> for i in 'ls'
do
  ftp -i ....
  mput $i
done

---

### Post by falconindy on 2010-02-20
Threading is the wrong term for this. A limitation of FTP is that only one transfer can take place over a given client/server connection. To transfer 10 files at once, you would need 10 FTP connections -- something that the server may not allow. If you have shell access to the remote, perhaps you could tarball the files and decompress them on the other side.

---

