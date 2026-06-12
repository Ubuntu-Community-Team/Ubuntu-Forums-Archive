---
title: "Apache error but only via network"
date: 2010-05-04
forum: Networking &amp; Wireless
---

### Post by smotsie on 2010-05-04
Hi,

I have an Apache set up to server some static html and php files which all work fine. The php and statics include image links which fail, but only when accessed over a real network - if I connect to http://localhost or http://[myIP address] from the system itself, I get images just fine. The failure in Firefox is "The image http://blah-blah.png cannot be displayed because it contains errors" (any image, have used binary diff to ensure no copying errors)

Some details:
The system is running Ubuntu 10.4, with all the latest patches, and apache 2.2.14-5ubuntu8
Doing wget of a php/html file results in precisely the correct content being saved.
Doing the same with the PNG I get the file, but it has approx 294 bytes of garbage before the <89>PNG, which includes the http header:

(binary stuff cut)HTTP/1.1 200 OK^M
Date: Tue, 04 May 2010 13:28:41 GMT^M
Server: Apache/2.2.14 (Ubuntu)^M
Last-Modified: Tue, 04 May 2010 08:29:36 GMT^M
ETag: "9fb4f-1004-485c082855fd1"^M
Accept-Ranges: bytes^M
Content-Length: 4100^M
Keep-Alive: timeout=15, max=100^M
Connection: Keep-Alive^M
Content-Type: image/png^M
^M
<89>PNG^M...

I have an Atheros Communications AR8131 Gigabit Ethernet controller using DHCP for network config. Everything else seems to be working exactly as expected.
I re-iterate, if I connect from the system to it's own IP address
I have tried connecting from various clients including non-Linux ones, images get served with garbage up front

I have no idea where to start debugging this (having worked out what is really happening) has anyone come across / solved this (yes I have Googled till my fingers bleed) or can anyone help with the next steps to take in finding out what is causing it?

TIA

---

### Post by tgalati4 on 2010-05-04
No errors in /var/log/apache2?

Clear cache in firefox on remote machine and try again.

---

### Post by smotsie on 2010-05-04
Thanks for the suggestions, but no, I have switched on debug level messages and all I get are debugs fo zlib compression of the php, html files:

[debug] mod_deflate.c(615): [client 192.168.1.148] Zlib: Compressed 1101 to 534 : URL /index.php

and the only errors I get are not really errors:

[error] [client 192.168.1.148] File does not exist: /var/www/favicon.ico

Clearing cache is not relevant, as I have used wget which doesn't cache (and used multiple different machines to make sure it wasn't an OS or browser thing)

---

### Post by tgalati4 on 2010-05-04
The faveicon.ico is the little icon that gets displayed in your tab when you bring up your page.  You can grab one from anywhere and put it in your home www directory.

Is this possibly HTML5 metadata?  Are you using FF3.5 or newer to display the problematic page?

"Content-Type" looks like metadata to me.

Is there a switch to turn off HTML5 in apache2.conf?

---

### Post by smotsie on 2010-05-04
err... thanks for your help, but I think you've missed the point of the problem. The images are delivered just fine if accessed by a browser on the same machine (Firefox, wget, elinks etc) it is only when they have gone through a real network that they have this extra data.

The extra data is the normal HTTP protocol pre-amble, but it is somehow corrupted so that the browser or wget client does not understand what it is receiving. I think the problem is somewhere in the network protocol stack, but I am not well enough versed in how this actually hangs together to get any further.

To summarise, I do not have a browser problem but a problem with images only when delivered by apache through a real network (as opposed to via loopback)

Any one got any ideas?

---

### Post by tgalati4 on 2010-05-04
Are these other machines (going through the real network) running Firefox 3.5 or greater?

I would get into the new features of apache 2.2.14 and see what was added over the older version.  For instance Hardy server is running apache2 2.2.8 and I don't get that behavior.  So I'm thinking it's new metadata (such has html5) that your remote clients don't know how to handle.

---

### Post by jcdutton on 2010-05-29
If your network card is this:
02:00.0 Ethernet controller: Atheros Communications AR8131 Gigabit Ethernet (rev c0)

I have heard reports of it silently corrupting data.
Try a different network card, and see if it cures your problem.

---

### Post by smotsie on 2010-05-29
> **jcdutton said:**
> If your network card is this:
02:00.0 Ethernet controller: Atheros Communications AR8131 Gigabit Ethernet (rev c0)

I have heard reports of it silently corrupting data.
Try a different network card, and see if it cures your problem.

Thanks for the reply. That is the card I have, but it is built into a laptop with no PC-Card slot, and it works just fine for everything else in and out. Ultimately I will just have to live with it failing. I reckon it might be worth trying a live CD from a completely (non-Debian based) different distro, and see if that does the same thing - at least I will know.

Cheers
Smotsie

---

