---
title: "FTP with vsftpd"
date: 2011-10-02
forum: Networking &amp; Wireless
---

### Post by Jakemurray on 2011-10-02
Hi im trying to set up an ftp server on a computer for personal file storage, but i have no experience with servers at all. i installed vsftpd via tutorial, but i dont know where to go from here...any tips?

---

### Post by jonobr on 2011-10-03
Control of the vsftpd program is done through
/etc/vsftp.conf
read through that and it will tell you the options available.


If its installed then from another machine you can type 
ftp <ipaddress>

enter your username and password, 
from there enter
bin

to transfer file in binary
then 

hash 

to turn on hash markings

then either mput <filename>
or mput *

or mget <filename>
or mget *

In a browser just put in the address 
[ftp://ipaddress](ftp://ipaddress)

Or you could use a program like filezilla on windows or 
from ubuntu you could connect to server using ftp

But do a little reading first

---

