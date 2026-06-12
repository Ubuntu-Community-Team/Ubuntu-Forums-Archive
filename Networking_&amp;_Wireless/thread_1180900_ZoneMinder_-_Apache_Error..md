---
title: "ZoneMinder - Apache Error."
date: 2009-06-07
forum: Networking &amp; Wireless
---

### Post by Roasted on 2009-06-07
I ran the installation for ZoneMinder along with the libraries I found on a wiki site that were required. I was then informed to go to:

[http://localhost/](http://localhost/)

And I got in bold letters "It Works!"

Okay, fine. As instructed, I was told to add zm at the end of it and then I would access my interface.

I tried:

[http://localhost/zm](http://localhost/zm)
[http://MyComputerName/zm](http://MyComputerName/zm)
[http://myIPaddress/zm](http://myIPaddress/zm)

Nothing worked. I also found a post from 2007 here on the forums that in /etc/apache2/httpd.conf I should add "ServerName localhost". So I did. Then I restarted Apache2.

This seems to have solved other people's problems, but not mine. How can I get ZoneMinder running?

---

