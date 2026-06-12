---
title: "Apache https not working"
date: 2013-05-21
forum: Networking &amp; Wireless
---

### Post by Elmi77 on 2013-05-21
Hi,

I used this tutorial: [http://www.howtoforge.com/how-to-set-up-an-ssl-vhost-under-apache2-on-ubuntu-9.10-debian-lenny](http://www.howtoforge.com/how-to-set-up-an-ssl-vhost-under-apache2-on-ubuntu-9.10-debian-lenny) to configure a https-page on my Ubuntu 10.04 LTS (I tried some other tutorials too but with the same result).

Unfortunately it is still not working, all https-pages are not accessible. The funny thing: there are no helpful information in /var/log/apache2/error.log. Same for /var/log/apache2/ssl_access.log, this file is empty.

So any ideas whre I could have a lookt/what could be wrong?

Thanks!

---

### Post by linuxtechguy on 2013-05-21
Check your firewall and make sure port 443 isnt blocked. Why do you think it doesnt work?

---

### Post by Elmi77 on 2013-05-21
It is not working because the webpage is not delivered, it can't be accessed from a webbrowser.

It is not a problem of firewall settings, I can connect to Apache and port 443. Amazingly wget shows this error message:

OpenSSL: error:140770FC:SSL routines:SSL23_GET_SERVER_HELLO:unknown protocol

---

### Post by Elmi77 on 2013-05-24
Any other ideas?

---

### Post by leff-michael on 2014-04-17
Hi Elmi77,

Did you ever figure out the issue here?  I've been searching for hours and can not get this to work.  Your post seems to reflect the exact same issue I'm having.  I am getting nothing in the apache error logs, and the connection is simply timing out from a browser.  My domain works correctly from a non-secure url.  I followed multiple tutorials including the one you linked to originally, but I can't figure out what the issue is here.  Did you ever figure it out?

Thanks a lot!

---

### Post by leff-michael on 2014-04-18
If anyone else is having the same problem, it turns out I simply did not have port 443 enabled on my server.  I'm using an Amazon EC2 instance, so I had to specifically open port 443 for traffic via the EC2 Management Console.  Once I did that everything worked as expected.

---

