---
title: "windows not resolving hostname"
date: 2011-03-31
forum: Networking &amp; Wireless
---

### Post by Nick Kruger on 2011-03-31
My windows workstation can only ping the IP of my ubuntu server, not it's name.

But, the ubuntu server shows up _by name_ on the windows workstation in Network Places correctly - as Jupiter Server (Samba, Ubuntu) (Jupiter). 

Well .... that's not right.

The Ubuntu server has no problem pinging any name or IP.

If I click on the Ubuntu server in Network Place I get the error message : Not accessable and network path not found. 

Have I configured Samba wrongly perhaps ? or is this a network issue ?

Thanks,
Nick

---

### Post by patryk77 on 2011-03-31
Ping uses DNS resolution, while SMB uses WINS resolution, and as such the Hostname you use to ping should not be the same as the hostname for Samba.

I would look at the Samba configuration first.

Also, you ca try to open the Samba folders from the Windows machine using an IP address; simply type in \\192.168.0.100 or whatever IP you have on the Linux box

[https://help.ubuntu.com/community/Samba](https://help.ubuntu.com/community/Samba)

---

### Post by Nick Kruger on 2011-03-31
Thank you,

I will have a look at the Samba configuration again, as well as 1 or 2 other possible causes I though of on the windows machine.

I will post my progress or (hopefully) solution in the morning.

Nick

---

### Post by fela on 2011-03-31
What is the output of

```
hostname
```

on the Ubuntu box?

---

### Post by papibe on 2011-03-31
Something similar happened when I changed the typical DHCP configuration of one my machines in my network.

In a default configuration, your router is your DNS (translate names into IPs). The router knows every machine that is conected to, so when you ping a name without domain, your router translate the name just fine.

When I changed one machine to use directly OpenDNS, I broke the ability of that machine to resolve local names. Don't get me wrong, it is faster that going through the router, but there's a trade of.

Just a thought, I hope it helps.
Regards.

---

### Post by Nick Kruger on 2011-04-02
Thank you all for your replies - they helped me onto the right track.
 
I have at last managed to connect to the Samba share on the ubuntu server from my windows desktop.
 
I did 3 things :
 
1. The fire wall - I foolishly assumed it was allowing samba through - won't make that mistake again.
 
2. My Samba configuration was also wrong. I went through the official server guide step by step again. Not sure if I needed to make ubuntu the primary domain controler or not, but suddenly I can connect.
 
3. I'm also not sure if I needed to do this or not - or if it's even correct - I assigned Samba an IP address. So my server has a static ip 192.168.1.3 on eth0 plus an additional IP for Samba 192.168.1.4 on eth0:0. Is this right ????  If I add a web server then it must be 192.168.1.5 on eth0:1 ? 
 
Can some one clarify point 3 for me ?
 
Thanks,
Nick Kruger

---

### Post by patryk77 on 2011-04-30
Sorry about being 3 weeks late, but as long as services listen on different port numbers they can share an IP address.

That is to say, if you have an Apache HTTP server (port 80) and a mail server (SMTP port 25), they can both use 192.168.1.3

If you wanted to host different virtual servers, you *could* provide Apache with 2 different IP addresses with one server listening on 192.168.1.3:80 and another on 192.168.1.4:80 and so on, then they could serve different content (blog.mynetwork.com, forums.mynetwork.com) but in this day and age using name-based virtual hosting is very well supported.

All that to say: it should NOT be necessary to add extra IPs for Samba or any other service, although it's not really a problem if you do.

---

