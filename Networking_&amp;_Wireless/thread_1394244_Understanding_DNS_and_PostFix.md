---
title: "Understanding DNS and PostFix"
date: 2010-01-30
forum: Networking &amp; Wireless
---

### Post by TorMike on 2010-01-30
I've tried twice to install PostFix as my mail server.  The install seemed to go OK, I followed the 8.10 Server Guide  for PostFix, yet every time I issue the command:

telnet mail.example.com 25  <- this will never work!

to see if everything is working correctly I get 'Can't find mail.example.com', which makes a lot of sense since I obviously screwed up the configuration.

 My install fails because during **dpkg-reconfigure postfix **I have no idea how to answer the question;

System Mail Name:  **What goes here?  DNS?**

Other Destination for mail:   

because I have no idea what the name of my DNS or even if I have one.

This is my HOSTS table:

127.0.0.1  localhost
192.168.1.102  kelowna.domain server  <- *kelowna is the name of my machine and that is the static IP I setup so my other machines can telnet to it*.

I included the last line in an attempt to 'create' a DNS.

Is this the name I'm suppose to enter as my System Mail Name?? and, if so, then when I test to see if my install worked would I enter;

telnet kelowna.domain 25.

As you can tell, I'm not very good at networking.

---

