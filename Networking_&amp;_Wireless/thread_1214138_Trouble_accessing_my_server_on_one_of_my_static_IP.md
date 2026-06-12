---
title: "Trouble accessing my server on one of my static IP"
date: 2009-07-15
forum: Networking &amp; Wireless
---

### Post by dangriffin80 on 2009-07-15
The company I work for has a range of static IP addresses.  Our office network has one, our windows web server has another and now my ubuntu server has one.  The trouble is, I cannot access the ubuntu server from the office address but I can access the windows server from it.  The office and windows server are both behind linksys routers, however the ubuntu server is plugged directly into the net.  I remoted into my home system and can access the ubuntu server just fine, web server and ssh.  Any ideas?

SOLVED:  I added a static route to our office router and all is well.

---

### Post by Kraut~salat on 2009-07-15
is your route set correctly? If you have real unique adresses, which are rare, those probraly are not in the same network. You have to add a route for each network or add a default route. Could be that your default route goes thru the router, but the router does not know how to get to the ubuntu server.

---

### Post by dangriffin80 on 2009-07-15
I just checked our Office router, which is just a Linksys BEFSR41 and there is nothing special set in Advanced Routing.  The windows server is behind the same type of router.  Just to give you an example of our IP setup, the office IP would be (and these aren't the real addresses) 69.38.120.10, the windows server at .11 and the Ubuntu server at .12 and the Netmask is 255.255.255.240.[COLOR=#ffffff][/COLOR]

---

