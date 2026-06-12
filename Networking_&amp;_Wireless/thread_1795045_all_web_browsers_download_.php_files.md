---
title: "all web browsers download .php files"
date: 2011-07-01
forum: Networking &amp; Wireless
---

### Post by chippanfat on 2011-07-01
Hey guys, 
Im not sure if this is in the right category but it seems the most applicable.

I'm not sure if this is a problem with apache2, php or my web browser configurations

but i'm trying to load my .php files in google chrome and firefox and instead of displaying the script executed on the server, the browsers just download the file.

I hope this makes sense, so
[http://localhost/websiteName/index.php](http://localhost/websiteName/index.php) will just download the index.php file and not display it in the browser.

this is on a local server too, xampp to be correct. 

also, what gets me, is that the "phpinfo();" .php files works correctly but nothing else is.

Cheers :)

---

### Post by Chris Richard on 2011-07-02
"localhost" address cannot be accessed from anywhere but your network, and depending on your server and network setup, often only from the host computer. So we can't see anything at all using that link.

You would need to either post your IP address (DON'T DO THAT!), or set up a DNS proxy at a site like dyndns.com (a much better idea). 

I wouldn't do even that though unless you really know what you're doing as far as securing your Xampp installation.

I can't help much with anything else at the moment, but maybe later today...

EDIT: Sorry, it's way too early in the morning and I haven't had enough coffee yet. I just realized you didn't intend that to be an active link.

I doubt this will be of much help, but you never know:

[http://www.webmasterworld.com/apache/3418477.htm](http://www.webmasterworld.com/apache/3418477.htm)

Also, is the page tat keeps downloading a custom built or a distribution (Joomla, Wordpress, or something  like that)?

Do the Xampp control panels, phpMyAdmin etc. load correctly?

---

