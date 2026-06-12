---
title: "DNS issues"
date: 2009-07-30
forum: Networking &amp; Wireless
---

### Post by nunki on 2009-07-30
I am trying to setup dns for my local network. The purpose of this setup is to allow all the machines on my network access the multiple websites I develop on my machine. Currently I have only a couple of webites that Im developing, and have them set up as virtual hosts in Apache2.

I would like to allow all the machines on my internal network be able to type the name of the site into a browser and have it come up. i.e. [http://whateverwebsite.home.lan](http://whateverwebsite.home.lan). I have already setup the virtual hosts and have verified they are working correctly.

I am having trouble with the DNS. I got it setup by reading a couple of tutorials, but the syntax is a bit confusing. Right now it works as long as only one website is enabled through a2ensite. The moment I enable another website, nothing works.

Im currently running Jaunty 64bit. Bind9 is installed and I have the resolv.conf file setup, the zone setup and the lookup and reverse lookup files created.

For reference I followed the tutorial [here]("http://www.zaphu.com/2007/09/14/ubuntu-dns-server-guide-bind-master-server-setup/")

Any ideas as to how I can get this to work?

---

### Post by nunki on 2009-07-30
This has been solved. One of the virtual host server names had an underscore in it. Apparantly bind doesnt like that. I renamed the virtualhost without the underscore, changed the corresponding A record and all is well

---

