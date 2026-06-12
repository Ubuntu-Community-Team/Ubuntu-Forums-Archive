---
title: "resolv.conf ?"
date: 2009-02-10
forum: Networking &amp; Wireless
---

### Post by robasc on 2009-02-10
Hello everyone I am trying to add a static ip address to my network card but having some real issues.

First off I am running a fresh install of ubuntu 8.10. I configured  /etc/network/interfaces  with

iface eth2 inet static
      address 192.168.1.56
      netmask 255.255.255.128
      gateway 192.168.1.5

Next I went to configure /etc/resolv.conf but it seems there is no existing file named resolv.conf. I did however see a file named resolvconf which is a directory. 

Since I did not see the file, I created a resolv.conf and configured it like so:

search mydomain.example
nameserver 43.34.34.34
nameserver 43.43.34.34


then saved and tried to ping another location but nothing. I am stumped on what to do here. I am new at linux and trying my hardest to learn. Could someone please help?

thanks!

---

### Post by jonobr on 2009-02-10
I figure its your permissions

post the results of ```
 ls -l /etc/resolv.conf

```

---

### Post by jonobr on 2009-02-10
Also, Im guessing you have access to a dns server that you can place into resolv.conf

If not you can use opendns

heres a link that shows the dns address for that

[http://www.online-tech-tips.com/cool-websites/free-dns-server/](http://www.online-tech-tips.com/cool-websites/free-dns-server/)

---

### Post by robasc on 2009-02-10
Ok, the output of ls -l /etc/resolv.conf  is:

-rw-r--r-- l root root 36 2009-02-10 19:56 /etc/resolv.conf

---

### Post by pdtpatrick on 2009-02-10
do you really have this in there? 

search mydomain.example
nameserver 43.34.34.34
nameserver 43.43.34.34

you might want to change mydomain.example to your actual dns server.

Check your router, it should show your ISP's dns servers or use opendns like the other colleague mentioned.

---

### Post by robasc on 2009-02-10
no, thats just fictitious addresses


the addresses I have in there are provided by my isp.

---

### Post by robasc on 2009-02-10
Also, I would like to state that I have a linksys wrt54g router and under setup It lists the router name and domain name. I named my domain avr.local and this is what I used in resolv.conf.

Is this what I need to put in there or do I need to get the domain name from my isp?

---

### Post by robasc on 2009-02-10
well I changed the contents of resolv.conf with:

search OpenDNS

nameserver 208.67.222.222

nameserver 208.67.220.220


and still cannot connect to the internet.

---

### Post by jonobr on 2009-02-10
hello

Can you ping your gateway IP address?

When you open a terminal and type in nslookup google.com
what is returned

when you open a browser and enter 
[http://74.125.45.100/](http://74.125.45.100/)

what happens

lastly post results from 

```
cat /etc/nsswitch.conf
```

---

### Post by robasc on 2009-02-11
Well everyone, I finally found what I was doing wrong.

After trying everything under the sun, I tried checking other peoples methods of setting up static ip address. 

I used the command "  sudo /etc/init.d/networking restart  "

and it worked!

it's about time!  

I appreciate everyone helping me on this. Now perhaps I can get on to setting up this Beowulf cluster I have been wanting to build.

---

