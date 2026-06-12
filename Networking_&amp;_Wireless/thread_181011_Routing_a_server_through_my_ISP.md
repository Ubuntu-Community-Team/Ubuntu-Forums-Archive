---
title: "Routing a server through my ISP"
date: 2006-05-23
forum: Networking &amp; Wireless
---

### Post by scratched on 2006-05-23
As a hobby this summer I have an old computer I want to turn into a web server, not for anything serious, just something to mess around with.

I have already set up the machine with the apache server itself, but I'm having trouble making it accessible from the web. I can connect to it using localhost, and if I use the IP address I get from whatismyipaddress.com I can see the site, but if one of my friends goes to the same address, they can not get through.

At first I thought I configured the NAT settings on my router incorrectly, but I connected my machine directly to the internet and have the same problem. Is there any way to see if I'm behind a NAT router at my ISP's end?

If I'm behind a NAT at their end, is there anything I can do about it other than purchasing a static IP?

And if not, is it possible that my ISP is blocking incoming connections? Online games and bittorrent work fine so incoming connections seem ok. I'm not sure why they would block someone from setting up an http server. Would changing the port for apache to port 8080 or something else get around this?

Is it also possible that I've done something wrong at my end? I have unblocked port 80 for all incoming connections on my software firewall and other people behind my router can go see the site ok so I doubt I set up the server wrong. My ISP is Verizon Fios. It doesn't have a modem and it uses pppoe to connect.

---

### Post by Slim Odds on 2006-05-23
Some modems have a firewall build into them. Does yours? You might need to reconfigure.

Are you using a route/NAT box? If so, you need to forward port 80 to the correct machine.

Also, your ISP could be blocking. Note that it may be against the rules to have a server like this, even if you are just messing around. But changing the port might work.

P.S. I looked at the Version FiOS site after my initial message. There must be some sort of a "modem" to convert from ethernet to fiber.

---

### Post by scratched on 2006-05-23
I forwarded my router correctly, but I also tried without the router and it didn't work. My FiOS modem isn't too accessible. It's installed in a box outside my house that I don't feel like messing with.

It looks like the terms of service for Verizon FiOS specifically states> [I] "You may not use the broadband to host any type of server, personal or commercial in nature."
[/I]
So it looks like I shouldn't bother with a server unless I want to go against their terms of service;)

I might try changing the port anyway to see if it works just so I can say that I've done it and got it to work. I wasn't planning to host a real website on it anyway so for my purposes, I don't care too much.

---

### Post by theonlyalterego on 2007-06-22
I'm having similar problems. I'm using Fios with Apache2 and gnump3d to host my mp3s.

I'm using no-ip.com as a DNS for external access, I've setup the router to forward port 80 and 8888 to my server machine. gnump3d is listening on 8888, and it externally accessable. However the standard apache server isn't. When I try and access via port 80 externally,  I get a timeout:

Network Error (tcp_error)
A communication error occurred: "Operation timed out"

When I access via port 80 internally via port 80, I see my site. So I know apache is serving correctly to port 80, but I can't figure out why the router isn't forwarding on to my machine. I initial guess was to double check the router, and yeah it's supposed to forward port 80... but it's not.

My best guess at this point is to think Verizon Fios is blocking port 80, presumably to keep people from hosting 'business' websites on a personal connection. Any help would be appreciated.

---

