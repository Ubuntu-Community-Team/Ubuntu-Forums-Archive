---
title: "ubuntu webserver"
date: 2010-03-15
forum: Networking &amp; Wireless
---

### Post by lateralus-paradox on 2010-03-15
Hi. 
 
I was wondering if anyone knows of a good tutorial on how to configure Ubuntu to make a decent webserver. Me and my friend have been working on it for a while, but don't really have a good tutorial to learn from. If anyone knows if one exists that'd be great.
 
Basically, we've got Ubuntu server installed on a computer, and we can access the "webpage" locally, but are having trouble setting up access to it, and accessing it in general from an external location.
 
It's running a clean install of the OS, basic updates, and OpenSSH as the only major other program/update.
 
Thanks for the help.
lateralus-paradox

---

### Post by llawwehttam on 2010-03-15
If its running locally and you can see it from other computers in your house but not outside then you need to configure port forwarding for port 80 on your router.

---

### Post by tripolitan on 2010-03-15
The web server, as you described it, is obviously working.

What you need is a tutorial on Networking and Security, not Ubuntu web server. Start by searching Google on how to secure a web server.

If you have a dynamic IP, Start with a dyndns.com then, assuming and praying that your server is behind a firewall, forward port 80 (open to the public, script kiddies and dos attacks) and isolate the server from your local network (this is most important, in my opinion)....don't assume that Ubuntu is secure, just because it is linux, webserving takes a lot more than a simple tutorial.

---

### Post by lateralus-paradox on 2010-03-15
Alright, thanks for the replies, I'll look into doing some of the things you guys suggested and post back my results. If need be I might post up the way that I'm trying to set it up (install, updates, programs that I ran, and etc.) and see if I'm doing it correct.
 
Thanks.
lateralus-paradox

---

### Post by perspectoff on 2010-03-21
> **lateralus-paradox said:**
> Hi. 
 
I was wondering if anyone knows of a good tutorial on how to configure Ubuntu to make a decent webserver. Me and my friend have been working on it for a while, but don't really have a good tutorial to learn from. If anyone knows if one exists that'd be great.
 
Basically, we've got Ubuntu server installed on a computer, and we can access the "webpage" locally, but are having trouble setting up access to it, and accessing it in general from an external location.
 
It's running a clean install of the OS, basic updates, and OpenSSH as the only major other program/update.
 
Thanks for the help.
lateralus-paradox

Apache2 is the most common webserver. Nginx is the second most common, and is faster. Setting up a webserver with Apache2 is trivial:
 sudo tasksel install lamp-server

Done!

What you probably are imprecisely referring to, however, are a wide range of servers, such as Drupal for websites, MediaWiki for a wiki, etc., etc.

Each of those interacts with the Apache2 webserver in slightly different ways. So there is no "simply."

Ubuntuguide.org has a lot of clues for what you might be looking for. I suspect what you actually are asking about is Drupal (or Joomla or Wordpress) for creating websites, for blogging or other purposes.

---

### Post by lateralus-paradox on 2010-03-22
> **perspectoff said:**
> Apache2 is the most common webserver. Nginx is the second most common, and is faster. Setting up a webserver with Apache2 is trivial:
sudo tasksel install lamp-server
 
Done!
 
What you probably are imprecisely referring to, however, are a wide range of servers, such as Drupal for websites, MediaWiki for a wiki, etc., etc.
 
Each of those interacts with the Apache2 webserver in slightly different ways. So there is no "simply."
 
Ubuntuguide.org has a lot of clues for what you might be looking for. I suspect what you actually are asking about is Drupal (or Joomla or Wordpress) for creating websites, for blogging or other purposes.
 
Yea, that sounds about right. I'll look into that too. I havn't had much time to work on it lately but thanks for all the help guys.
 
Thanks again.

---

