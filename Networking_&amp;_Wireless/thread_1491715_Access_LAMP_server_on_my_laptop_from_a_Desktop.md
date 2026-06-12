---
title: "Access LAMP server on my laptop from a Desktop"
date: 2010-05-23
forum: Networking &amp; Wireless
---

### Post by Kdar on 2010-05-23
I have LAMP server on my laptop, I have it there since its more convenient if I am working on some site and testing it away from my home. However, when I am at home, I like to use Desktop more.

How can I network my two computers and able to access LAMP server on my laptop from my Desktop?

I have never networked two computer together in Linux yet... can some one help me? :)

---

### Post by wojox on 2010-05-23
Do you have a router and are they connected with Ethernet cables?

---

### Post by Kdar on 2010-05-23
I have wireless router.
Both of computers connected to it wirelessly.

---

### Post by wojox on 2010-05-23
You need to find out your ip address on your laptop. Try:

```
ifconfig
```

In the terminal and look for inet addr:192.xxx.xxx.xxx

Then open up your desktop web browser and for the URL use 

[http://192.xxx.xxx.x](http://192.xxx.xxx.x)  whatever the number is.

---

### Post by Kdar on 2010-05-24
thanks! I got this to work.. but I have a problem. It only shows the "http://localshot" from my laptop.

However, I have my LAMP set up so that it would load web-files from a home directory, so if I want to open a site from LAMP on my Laptop, I type "http://drupal6"

I have my "hosts" file in /etc set up this way: 127.0.0.1 localhost site1 joomla drupal6

How can I access other sites, besides the localhost on another computer?

---

### Post by wojox on 2010-05-24
Not sure. Try adding your lan address to the hosts file.

---

### Post by Kdar on 2010-05-24
How could I do that? something like this?

127.0.0.1 localhost
127.0.0.2 drupal6

??

---

### Post by Iowan on 2010-05-24
127.0.1.1 is typically used for machine hostname...
At one time, I had a static address included in one of my */etc/hosts* files

---

