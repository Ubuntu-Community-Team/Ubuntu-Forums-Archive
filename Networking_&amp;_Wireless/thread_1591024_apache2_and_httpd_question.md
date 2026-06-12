---
title: "apache2 and httpd question"
date: 2010-10-08
forum: Networking &amp; Wireless
---

### Post by HypNemes on 2010-10-08
Hello all

Im trying to find apache2 httpd file - but according to "locate" it's not any were's on the system :confused:

I have apache2 installed; and doing the normal "http://localhost" request with a web browser, shows me the relevant "its working" page.

I wanted to do a "/usr/local/apache2/httpd -v" to figure what version of apache2 I had installed - but apparently "httpd" doesn't exist there or anywheres.

I'm following a book - well several books - teaching myself linux and other things as i go - so im assuming said book has it wrong for ubuntu and apache2 on ubuntu default installs to someweres else?

I have an "/etc/apache2/" dir with various files and dir's within, like /etc/apache2/httpd.conf"

Can anyone shed any light so I can figure out what version I have installed and running?

Thanks in advance.

Hyp

---

### Post by SeijiSensei on 2010-10-09
dpkg -s apache2 

On my 10.04 Ubuntu Server edition this returns:

[stuff]
Version: 2.2.14-5ubuntu8.2
[stuff]

The binary is /usr/sbin/apache2; most server binaries are stored in /usr/sbin.

---

