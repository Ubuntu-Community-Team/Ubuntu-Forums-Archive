---
title: "About Website in localhost HTTPS ?"
date: 2011-11-21
forum: Networking &amp; Wireless
---

### Post by s.hijazi on 2011-11-21
Dear All,
I success to create HTTPS with CA,
I create an html site,
I need to do a small test [www.mytestpage.com](www.mytestpage.com) 
I added [www.mytestpage.com](www.mytestpage.com) in /etc/hosts with line :
127.0.0.1         [www.mytestpage.com](www.mytestpage.com)  

my question is : 
how can i go to site in /var/www/test/index.html  ? 
which command or configuration or line to add to do this ? 
thank you :)

---

### Post by jonobr on 2011-11-21
Hey

If you put the ip address of your server in a browser,
did you check to ensure you can see the default "it works" message?


I think also you should do a bit of reading on apache

---

### Post by dramos on 2011-11-21
I am not an expert but I will try to help you as I have done something similar many times.

First I dont understand what do you mean by:
```

i success to create HTTPS with CA,

```

But as to modify your site, you have two choices: you can create a virtual host or you can put the files in /var/www or create a symbolic link to /var/www.

To edit the file /var/www/test/index.html you can use any text editor. 

```

sudo gedit /var/www/test/index.html

```

if the directory /var/www/test does not exist create it.
```
sudo mkdir /var/www/
```

you need sudo because root owns /var/www, that is why i would recoment to put your files your home directory and point them to /var/www using a symbolic link.

But I think, is best if you use virtual hosts.

---

### Post by s.hijazi on 2011-11-21
Mr jonobr , yes i saw "it works message" .

Mr dramos, i install apache on ubuntu, and i create SSL , 
i create a site in /var/www/site/index.html , 
i don't have any problem here, 

i need to configure my ubuntu as a DNS-Server, and i need to go to site [https://localhost/site](https://localhost/site) instead of [http://www.mytestpage.com](http://www.mytestpage.com) , 

thank you :)
i will do a bit of reading on apache

---

### Post by dramos on 2011-11-21
> **s.hijazi said:**
> [FONT=Comic Sans MS][SIZE=2]Mr jonobr , yes i saw "it works message" .

Mr dramos, i install apache on ubuntu, and i create SSL , 
i create a site in /var/www/site/index.html , 
i don't have any problem here, 

i need to configure my ubuntu as a DNS-Server, and i need to go to site [https://localhost/site](https://localhost/site) instead of [http://www.mytestpage.com](http://www.mytestpage.com) , 

thank you :)
i will do a bit of reading on apache 
[/SIZE][/FONT]

Is this server for production or for development.

---

### Post by s.hijazi on 2011-11-21
only to test a project in university

---

