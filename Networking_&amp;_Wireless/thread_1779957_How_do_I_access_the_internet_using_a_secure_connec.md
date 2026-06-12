---
title: "How do I access the internet using a secure connection to my Ubuntu server?"
date: 2011-06-11
forum: Networking &amp; Wireless
---

### Post by boondocks on 2011-06-11
I have a Ubuntu laptop when I travel.
And a Ubuntu server back at my desk.
The laptop connects to the server via OpenVPN.
So I can access all the resources on the server from the laptop.

What applications/packages should I install on these Ubuntu systems such that:
[LIST]
[*]When I am travelling and using public/hotel WiFi that I am accessing the internet securely from the Ubuntu laptop via the Ubuntu server.  Instead, of accessing the internet directly from the laptop.
[*]On the laptop, I generally use a web browser, chat client, etc. Like Firefox, Chrome, Pidgin, ...
[*]So I have some degree of safety/privacy when I am on the road.
[/LIST]

---

### Post by Joe of loath on 2011-06-11
I use ssh. If you run ssh -D 8080 (server-ip/hostname), and set all your applications to use a proxy of localhost:8080, everything will go through the encrypted shh connection.

---

### Post by boondocks on 2011-06-11
Does that take care of TCP and UDP ?

---

### Post by Joe of loath on 2011-06-11
It will tunnel everything, provided it's given the proxy server.

---

### Post by boondocks on 2011-06-11
Ok.
What do I need to install/run on the server side?

---

### Post by Joe of loath on 2011-06-11
All you need to do on the server side is have ssh running, and listening on a few different ports (in case some are blocked). I run it on 22, 80, 443 and 8080.

---

### Post by boondocks on 2011-06-11
So if I am not running something like squid on the server ... 
then will the sshd on the server be just a conduit between the remote laptop and (say) google.com ?

Where conduit = transparent + encrypted

---

### Post by Joe of loath on 2011-06-11
Yup, all your traffic is wrapped up and encrypted on your laptop, flies through the internet looking like gibberish, and pops out of the server as it would have come from your laptop.

---

### Post by boondocks on 2011-06-11
Currently, I am running apache2 on this server on port 80 and 443.
Can your suggestion work concurrently with this apache2 setup?

---

### Post by Joe of loath on 2011-06-11
Yes, just don't set ssh to listen on those ports. Unfortunately, if you're somewhere where port 22 and 8080 are blocked, you might not have much luck.

---

### Post by boondocks on 2011-06-11
Do you mean ... 
if I am using a Wifi at a coffee shop where they block outbound ports 22 and 8080 
... then I am out of luck?

---

### Post by Thewhistlingwind on 2011-06-11
> **boondocks said:**
> Do you mean ... 
if I am using a Wifi at a coffee shop where they block outbound ports 22 and 8080 
... then I am out of luck?

Not necessarily, from what I understand, you can change the port of your SSH.

---

### Post by Joe of loath on 2011-06-11
> **Thewhistlingwind said:**
> Not necessarily, from what I understand, you can change the port of your SSH.

Usually places like that block everything except ports 80 and 443, hence why I suggested listening on those ports.

---

### Post by boondocks on 2011-06-11
Ok, understood.

Anway, I have not had that problem so far because ...
> **boondocks said:**
> I have a Ubuntu laptop when I travel.
And a Ubuntu server back at my desk.
The laptop connects to the server via OpenVPN.
So I can access all the resources on the server from the laptop.

... therefore I can access all the ports on my server because they are accessible/visible thru the OpenVPN tunnel.
So I assume the only port visible between my laptop and my server would be my unique UDP port being used by the OpenVPN connection.

---

