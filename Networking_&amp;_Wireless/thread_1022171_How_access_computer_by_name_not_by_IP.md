---
title: "How access computer by name not by IP"
date: 2008-12-26
forum: Networking &amp; Wireless
---

### Post by nicholasnet on 2008-12-26
I work in a place where entire network is in windows domain. I am thinking to install one Ubuntu server for testing purpose basically a LAMP server with SSH. So, far I manged to install a server and access its pages by IP address. However I am trying to access its page by name like [http://intranet](http://intranet) not [http://100.xx.xx.xx](http://100.xx.xx.xx). Now the problem is network administrator often changes the IP of every computer. So, is there any way to achieve this via DHCP or anything else. So, that whenever I go to [http://intranet](http://intranet) it will route the traffic to this server. 

I successfully did this with IIS so there must be some way to do this in UBUNTU as well using Apache.

Any suggestion....please...

---

### Post by gerbman on 2008-12-26
A not-so-nice solution would be to edit the /etc/hosts file, adding a line like "x.x.x.x host"; however you'll need to change this each time your network admin assigns new IP addresses to the machines.

---

### Post by nicholasnet on 2008-12-26
Thank you very much for the reply. I can make my IP static for that machine. But when I installed Ubuntu server I also installed Bind9 is this necessary?
Also can windows machine hit this Ubuntu server by name like [http://intranet/](http://intranet/)

Is this possible to do in Ubuntu server?

---

### Post by gerbman on 2008-12-26
> **nicholasnet said:**
> Thank you very much for the reply. I can make my IP static for that machine. But when I installed Ubuntu server I also installed Bind9 is this necessary?
Also can windows machine hit this Ubuntu server by name like [http://intranet/](http://intranet/)

Is this possible to do in Ubuntu server?

Just to be clear - you should edit the /etc/hosts file on the computer you will be using to access your Ubuntu server. The hosts file tells the current machine what the IP address is for a given host name. I guess I was assuming your non-server machine was running Ubuntu as well. If it's not, then this approach will not work.

I don't know what Bind9 does.

---

### Post by nicholasnet on 2008-12-26
Bind9 is DNS server. It seems like your proposed idea won't work because Windows have to access this Ubuntu server with name like [http://intranet](http://intranet)

---

### Post by cariboo on 2008-12-26
You can edit the hosts file on your Windows computers, the same way you would in Ubuntu, I don't have a windows computer handy to tell you where the host file is located, but if you search for it you should be able to find it.

Jim

---

### Post by nicholasnet on 2008-12-26
Thank you very much for the reply but I have many Windows installed computers so it is not possible for me to change host file of every single of them. I want to hit UBUNTU server by many different windows machine by name URL like [http://intranet](http://intranet)

Is this possible for intranet setup.

---

### Post by capscrew on 2008-12-27
> ...I have many Windows installed computers so it is not possible for me to change host file of every single of them.

So how do they resolve Windows hostnames to IP addresses now?  DNS is standard across Apple/Unix and Microsoft.  If you are using AD you should be able to add the computer to the AD database (LDAP) and that should update the DNS server.

---

### Post by cariboo on 2008-12-27
I haven't used it, but there is a program called dnsmasq in the repositories, that should allow you to do what you want. Have a look [here]("http://www.enterprisenetworkingplanet.com/netos/article.php/3377351"), for more info on dnsmasq

Jim

---

### Post by nicholasnet on 2008-12-29
Thanks a lot for the reply. You guys were right I had to configure Windows DNS not Ubuntu to route the traffic to Ubuntu testing server. However I am not being to able to connect to MySql server from another machine even if I removed bind address. 

Is there anyway to connect to mysql server from remote machine. It is saying **Host 'user-telco.cdi' is not allowed to connect to this MySql server**.

---

### Post by cariboo on 2008-12-29
What I do when setting up a mysql are the following  commands, they must be run in the mysql console:

```
grant all privileges on *.* to <user>@'localhost' identified by '<password>' with grant option;

grant all privileges on *.* to <user>@'%' identified by '<password>' with grant option;
```

the <user>@'%' allows the user  to connect remotely.

Jim

---

### Post by nicholasnet on 2008-12-29
That worked perfectly. Thank you very much.[http://ubuntuforums.org/images/smilies/icon_biggrin.gif](http://ubuntuforums.org/images/smilies/icon_biggrin.gif)

---

