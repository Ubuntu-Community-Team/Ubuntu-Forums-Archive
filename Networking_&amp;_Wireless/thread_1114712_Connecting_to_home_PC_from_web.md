---
title: "Connecting to home PC from web"
date: 2009-04-03
forum: Networking &amp; Wireless
---

### Post by dyingsun on 2009-04-03
Hi all
I have LAMP running smoothly on my Hardy installation, and can happily do all my JavaScript and PHP stuff on localhost, but soemtimes it would be helpful if I could access it from the web when I'm not home. My IP address just takes me straight to my router (Dlink DSL-G604T). The router has my PC connected via ethernet, a second PC in the process of being setup which will also connect via ethernet(and will probably end up one day being the webserver PC and print/file share box for the family), and up to 3 laptops sometimes connecting wirelesly.

Basically I'd like to be able to edit my PHP and JS files, use phpMyAdmin and muck around with my databases, do my HTML and CSS, and do whatever else I need to with the server, I just need to be able to do it remotely.

Can someone please give me an idea of how to get that happening? How can I get from the web to the right machine on the network?

Thanks!
Damien

---

### Post by jigsaws on 2009-04-03
You have to forward ports on your router. Then you can connect from outside your router's IP.

---

### Post by superprash2003 on 2009-04-03
follow this guide [http://www.portforward.com/english/routers/port_forwarding/Dlink/DSL-G604T/default.htm](http://www.portforward.com/english/routers/port_forwarding/Dlink/DSL-G604T/default.htm) .. you would need to open port 80

---

### Post by dyingsun on 2009-04-05
Thanks Jigsaws and Superprash, just setting up the server on the other machine, think I'll test it out on that.

Cheers!

---

