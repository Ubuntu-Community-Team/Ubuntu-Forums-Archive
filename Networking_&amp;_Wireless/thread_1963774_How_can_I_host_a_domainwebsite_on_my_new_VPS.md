---
title: "How can I host a domain/website on my new VPS?"
date: 2012-04-22
forum: Networking &amp; Wireless
---

### Post by dzulfriday on 2012-04-22
I am an average Ubuntu user and currently i decided to strengthen my knowledge in Ubuntu. Since i am a web developer, lately i decided to setup my own web server powered by Ubuntu.

I just bought an unmanage VPS powered by Ubuntu 11.10. I have managed to install the Apache, PHP, MySQL and the basic security changes.

Previously, i was just a shared hosting user where everything is managed via cPanel which is easy. Now is totally different and i am clueless since i am on unmanaged VPS and of course the hosting company will not help me.

My questions are:

[LIST]What are more to setup after getting the Apache, PHP and mySQL running? (most of my sites will be running on PHP open source CMS).
[/LIST]
[LIST]Previously, when i want to host new website, after i purchase a domain from registrar i will change the domain nameservers with my sharedhosting nameservers i just add the domain via cPanel. How can i host a domain/website in my new VPS? How to have a nameserver? How to setup the nameserver?
[/LIST]
[LIST]Is there any control panel for Ubuntu? (like cPanel for CentOS). I am planning to install it after i have master setup Ubuntu server with the hardway (via CLI)
[/LIST]

Sorry for these beginner questions

---

### Post by dzulfriday on 2012-04-23
Hmmmm....bump

---

### Post by SeijiSensei on 2012-04-25
Your questions are just too extensive for someone to answer here.  I recommend visiting [http://library.linode.com/](http://library.linode.com/) and reading some of the documentation they provide there.  Also the Ubuntu [server guide]("https://help.ubuntu.com/11.10/serverguide/index.html") is a good resource.

---

### Post by dzulfriday on 2012-04-25
I was follow linode library since beginning. But i cannot follow anymore since Linode has built-in DNS management.

---

### Post by cmacia06 on 2012-04-25
From what I know you have start by telling the person hosting your domain to point the domain name to you ip address. Then if you have a router you tell the router to point the incoming traffic to port 80 on your server. On your server i believe the files to your website go on "/var/www" i think the directory is automatically created when you install Apache web server. You said you develop websites so im sure you also know that you need to have a static ip set in order to host this website. Im not sure if this is what you were asking for though but if your hosting your own website this is what i did.

---

### Post by dzulfriday on 2012-04-25
This is unmanaged vps, so the company will not help on this.

---

### Post by cmacia06 on 2012-04-25
I am not very familiar with vps. Are you connecting though ssh, telnet or how?

---

### Post by dzulfriday on 2012-04-25
Usually SSH

---

### Post by cmacia06 on 2012-04-25
Im not sure who you are buying your domain from so I wouldn't be able to help you with that. I just know that to host i use dyndns.com register a domain with them. In their options I would put my vps ip address and just put my website files in /var/www .  that would make my website up and running. Just made sure my firewall isn't blocking incoming traffic on port 80

---

### Post by dzulfriday on 2012-04-25
What if you want to host many websites?

---

### Post by cmacia06 on 2012-04-25
This website may help 

[http://www.adminnation.com/2011/08/23/running-multiple-websites-using-apache/](http://www.adminnation.com/2011/08/23/running-multiple-websites-using-apache/) 

It explains how to set up multiple websites.

---

