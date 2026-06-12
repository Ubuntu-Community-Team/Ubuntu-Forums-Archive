---
title: "MythWeb remote access problem"
date: 2011-01-28
forum: Mythbuntu
---

### Post by nhtrader on 2011-01-28
I've been experimenting with accessing MythWeb today. And I've been trying different ways to access MythTV and I've encountered a problem.

Here's the situation.
I have modified my router to allow port forwarding to the MythTV PC
My dynamic DNS is working for ssh connections.
I have edited my /etc/hosts.allow and /etc/hosts.deny files to allow access.


1. I can access MythWeb locally via [http://127.0.0.1/mythweb](http://127.0.0.1/mythweb)
2. I can access  MythWeb over home network via [http://mythtv-computername/mythweb](http://mythtv-computername/mythweb)
3. I can access  MythWeb over internet using IP address [http://45.45.45.45/mythweb](http://45.45.45.45/mythweb) (using default port 80)

Here's the problem...
4. I can not access MythWeb over internet using dynamic DNS. [http://mydomain.dsn.com/mythweb](http://mydomain.dsn.com/mythweb)


Then I changed the port forwarding in my router to remap port number 8080 to 80

5. I can not access MythWeb over internet using a different port number using
     [http://45.45.45.45:8080/mythweb](http://45.45.45.45:8080/mythweb)


What am I missing?

---

### Post by azmyth on 2011-01-29
The way I did it is I changed the listening port in the apache config files to 8080 and then in my router I changed my port forwarding on the port 8080 to redirect to my myth computer. I used a different port since I think my IP blocks port 80. In the DNS forwarder, I setup just a regular redirect so mythbox.dns.org:8080/mythweb goes right to my myth computer. I also setup a http password. I also installed the script the checks and updates my ip with dns.

---

### Post by newlinux on 2011-01-29
for 4. and 5. I just want to make sure you are accessing this domain from a network connection that is not on your LAN. 

Interesting - I am able to forward an alternative port to my :80 port on my mythweb machine on my router successfuly. Is it possible your ISP is blocking :8080 but not :80? Doesn't seem likely but you can try other ports to see. As suggested you can try just having apache listen to 8080 and forwarding to 8080 (but that shouldn't be necessary). 

Other than that - I'm puzzled. You may want to ask this question in the general help, networking section, or with your DynDNS service.

---

### Post by nhtrader on 2011-01-29
> **azmyth said:**
> The way I did it is I changed the listening port in the apache config files to 8080 and then in my router I changed my port forwarding on the port 8080 to redirect to my myth computer. I used a different port since I think my IP blocks port 80. In the DNS forwarder, I setup just a regular redirect so mythbox.dns.org:8080/mythweb goes right to my myth computer. I also setup a http password. I also installed the script the checks and updates my ip with dns.

That's the way I was going to go. But I was experimenting with what user "newlinux" mentioned as another alternative that was less work and of course made few changes to the system.

So I gave it whirl, and I got stuck. I'm sure that I'm missing a setting somewhere, but it still eludes me.

---

### Post by newlinux on 2011-01-29
what router are you using?

---

### Post by nhtrader on 2011-01-29
> **newlinux said:**
> for 4. and 5. I just want to make sure you are accessing this domain from a network connection that is not on your LAN. 

Interesting - I am able to forward an alternative port to my :80 port on my mythweb machine on my router successfuly. Is it possible your ISP is blocking :8080 but not :80? Doesn't seem likely but you can try other ports to see. As suggested you can try just having apache listen to 8080 and forwarding to 8080 (but that shouldn't be necessary). 

Other than that - I'm puzzled. You may want to ask this question in the general help, networking section, or with your DynDNS service.


Yes, I'm accessing my home network from outside my home network. It's great to have neighbors that don't secure their wireless. It's perfect for tests such as this. I was able to test ssh this way along with VNC, and other means of accessing my home.

As for blocking port 8080, well I tried port 85 and a few others and that didn't work. On the bright side, apparently I am able to use the default port of 80. But I thought for security's sake, it would be better to change the port. Plus I was curious to explore you suggestions.

I'll keep at it and let you know what I did wrong. I'm sure the problem will surface when I'm not directly working on this problem.

---

### Post by alien878 on 2011-01-31
If you can do (3), you are almost there.

I suggest you re-try (4).  If the IP address works, but not the DDNS domain, it is likely the DDNS is out of date.  It often takes time for a new or changed IP to propogate through DNS.  When my router gets a new IP, the DDNS often doesn't work for half a day.

You can always check the state of DDNS by doing a nslookup on the domain.

---

