---
title: "Advice please server or desktop?"
date: 2012-03-22
forum: Networking &amp; Wireless
---

### Post by Neill_R on 2012-03-22
hello

I am getting prepared for 12.04 and I am considering whether I should be using Desktop or server version of Ubuntu.

My single Ubuntu PC is used as an Internet connection sharing fire-walled PC running web server (apache-2) print server  (HPLIP), Likewise-open to join the windows AD domain, ddclient to handle the dynamic IP address supplied by my ISP via mobile broadband and a USB modem.

i currently run Desktop Ubuntu 11.04 my options are

1 run 12.04 desktop
2 run 12.04 server (CLI only)
   a) use the CLI only
   b Install Webmin (would have to be on windows PC 
3 run 12.04 server and add GUI gnome

I would appreciate  you views 
Neill

---

### Post by haqking on 2012-03-22
> **Neill_R said:**
> hello

I am getting prepared for 12.04 and I am considering whether I should be using Desktop or server version of Ubuntu.

My single Ubuntu PC is used as an Internet connection sharing fire-walled PC running web server (apache-2) print server  (HPLIP), Likewise-open to join the windows AD domain, ddclient to handle the dynamic IP address supplied by my ISP via mobile broadband and a USB modem.

i currently run Desktop Ubuntu 11.04 my options are

1 run 12.04 desktop
2 run 12.04 server (CLI only)
   a) use the CLI only
   b Install Webmin (would have to be on windows PC 
3 run 12.04 server and add GUI gnome

I would appreciate  you views 
Neill

if its gonna be a server run server
if its gonna be a desktop use desktop

not much more to it really ;-)

a desktop install will run the same services as server but if not acting as a desktop then install server, if it is acting also as a desktop then install desktop.

Cheers

---

### Post by jonobr on 2012-03-22
Agree with Haqking,

If your really comfortable on the command line and your in a position to install and control whatever you need then run server as it sounds like thats what you have.

However, if you go cli server and your not strong on the cli, it will seem like a chore.

---

### Post by rg4w on 2012-03-22
> **jonobr said:**
> However, if you go cli server and your not strong on the cli, it will seem like a chore.
At first.  And maybe for a while.  But the more you do it the better it gets. 

I suck at the command line, so I set up one of my machines with the server version specifically for that reason:  no crutches.  

It's been teaching me a lot, and the best thing is that with no GUI it doesn't really matter if I'm physically at the machine or using SSH from miles away - CLI is almost never slow to work with, even over the wire.  You can learn from anywhere.

---

