---
title: "server networking configuration"
date: 2011-03-26
forum: Networking &amp; Wireless
---

### Post by martinlall on 2011-03-26
Hi,

I've got an ubuntu server and i can access it only by IP address on LAN. For example [http://192.168.2.65:10000](http://192.168.2.65:10000) to access webmin or \\192.168.2.65\ to access it's network folders.

The GW for server and PCs is router running DDWRT. 
What I need to configure to access the server from LAN by name?

Thanks,
M

---

### Post by mkhurram92 on 2011-03-26
> What I need to configure to access the server from LAN by name?

Make sure that your DNS is resolving server name properly... ???

But this is probably a bad idea. Why do you want to do this and how do you plan to secure it? Doing so will give anyone access to your webmin - a product known for security flaws.

It would be better to access it via using an ssh tunnel

ssh -L 8000:localhost:10000 webmin.example.com

Then visit

[http://localhost:8000](http://localhost:8000)

in your web browser.

---

### Post by martinlall on 2011-03-26
> **mkhurram92 said:**
> Make sure that your DNS is resolving server name properly... ???

But this is probably a bad idea. Why do you want to do this and how do you plan to secure it? Doing so will give anyone access to your webmin - a product known for security flaws.

It would be better to access it via using an ssh tunnel

ssh -L 8000:localhost:10000 webmin.example.com

Then visit

[http://localhost:8000](http://localhost:8000)

in your web browser.

There's no problem with security. 
My server is behind DDWRT router/firewall that allows incoming connections  only through VPN tunnel and ubuntu's iptables is set to block anything that's not permitted and doesn't come from LAN (or VPN) :) (except few ports of course)
Plus the psad is monitoring all network traffic.

So there's no way that someone outside would access to my LAN to be able to access to my server.

That brings us back to zero - i can access my server (192.168.2.65) from my PCs(same subnet that server is - eg 2.xxx) only by IP address but not by name. 

What is needed? Bind9? DNS? Edit /etc/hosts/? 
Little confused here so all the help is still welcome.

---

### Post by SeijiSensei on 2011-03-26
If you're supporting one or a few clients, giving them all a common hosts file is the way to go.  If the network's user base expands, you'll probably find it much more convenient to run a DNS server.

In /etc/hosts just add a line like 

```
192.168.2.65     mylovelyserver
```

and you can use [http://mylovelyserver:10000/](http://mylovelyserver:10000/) to get to Webmin, \\mylovelyserver\share to browse shares, etc.

---

### Post by martinlall on 2011-03-26
> **SeijiSensei said:**
> If you're supporting one or a few clients, giving them all a common hosts file is the way to go.  If the network's user base expands, you'll probably find it much more convenient to run a DNS server.

In /etc/hosts just add a line like 

```
192.168.2.65     mylovelyserver
```

and you can use [http://mylovelyserver:10000/](http://mylovelyserver:10000/) to get to Webmin, \\mylovelyserver\share to browse shares, etc.

Hi,

That's what I thought too, add the line to /etc/hosts. But it won't work. :confused:

---

### Post by SeijiSensei on 2011-03-27
Can you post your hosts file and the contents of /etc/hosts.conf?  Putting them inside [noparse]```

```[/noparse] will make them easier to read.

---

