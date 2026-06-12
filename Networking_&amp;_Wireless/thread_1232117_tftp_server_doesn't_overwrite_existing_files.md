---
title: "tftp server doesn't overwrite existing files"
date: 2009-08-05
forum: Networking &amp; Wireless
---

### Post by malcolmpdw on 2009-08-05
Hello,

I have configured TFTPD according to the very clear instructions on 

[http://www.davidsudjiman.info/2006/03/27/installing-and-setting-tftpd-in-ubuntu/](http://www.davidsudjiman.info/2006/03/27/installing-and-setting-tftpd-in-ubuntu/)

At present, the transfer fails if the file already exists. I would like it to overwrite the existing file.

I guess I just have to add one line to /etc/xinet.d/tftp but what is it?

Thanks in advance!

Malcolm

---

### Post by malcolmpdw on 2009-09-02
The problem lies with the permissions of the existing file.

If I do this first:

sudo chmod 777 *filename*

then the transfer overwrites the existing file.

But how can I get xinetd to create the first file with the permissions I require?

---

