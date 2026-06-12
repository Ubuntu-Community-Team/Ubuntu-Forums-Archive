---
title: "no network / ftp"
date: 2009-06-23
forum: Networking &amp; Wireless
---

### Post by oc999 on 2009-06-23
hi , 
i am using samba to share my folders in LAN and had no trouble until today - for some reason I can't access any network places anymore neither through nautilus nor through the console - error message says something about "network places can't be used".
all other (windows) pcs can still access my files ( I see them as shared in nautilus too ) but I can't access either myself or any other shared folder in LAN (  winXP folders & printers ).
To make it even worse , ftp isn't working either - it did fine until today - I can't access ftp , through nautilus .. through anything - the error I get should be something like "operation not supported" ( don't know the exact translation as my ubuntu is not in english ). same error I started to get when I click http - Links in my email program ( Evolution ) - just wont open any link anymore.
well somethings clearly screwed up  in my system and it has all to do with networking / internet but I don't know where to start to fix it. would be nice if anyone could help me out ! 
Thanks !

---

### Post by tmht on 2009-06-23
Can you access anything from the machine you're having issues with?

If so what?

If not has anything changed recently?

---

### Post by oc999 on 2009-06-23
i can access everything .. internet .. and so on .. i just cant see any objects in my LAN - won't even let me
I can't access ftp - sites and I cant open http: links in my email program 
what I changed recently was .. installing apache2 (runs fine ), webmin (runs fine ) & pureftpd (which I didn't make it to run ) but I didnt change anything in the system ..

---

### Post by tmht on 2009-06-23
So you can access the internet ? [http://www.google.com](http://www.google.com) works fine?  Try [http://www.openswitch.org](http://www.openswitch.org) does that work too?

Next try pinging your gateway and see what happens there.  Are all machines on the network sharing a common gateway for example 192.168.0.1 and common netmask?

---

### Post by oc999 on 2009-06-23
yes , internet works fine , so does openswitch.org - I am currently writing this answer on the machine having the issues - its not a network error , the router is set-up correctly all other machines can communicate with each other and even see my files .. but I can't see them - yesterday I could . maybe my post earlier wasn't clear enough but I'm looking for a way to restart samba or set everything on default settings so I can access the LAN again - it already worked before for a long time but something has been screwed up and I need a way to reset samba and everything related to ftp .. or any program/setting that could cause this problem!

edit : ping to gateway(router/dhcp server) works fine ( 192.168.2.1)

---

### Post by tmht on 2009-06-23
apt-get uninstall xxx and/or aptitude uninstall xxx

Something like that?

---

### Post by oc999 on 2009-06-23
yep does it work for samba?

---

### Post by tmht on 2009-06-23
It should.  If you have made configuration changes and want to restart the service you can use init.d and restart it.  But since you don't know what you changed you could probably just get away with uninstalling.

---

### Post by oc999 on 2009-06-23
yep but didnt work out .. 
 I tried uninstall ... didnt work - 
but sudo apt-get remove samba worked. 
i removed and reinstalled samba. works fine I can share folders and anything
but i still can't access my network so it's clearly not samba causing the problem .. I believe its nautilus because I don't even get to see the network , when i click on network it just pops up an error and thats it - must be something else causing the trouble

---

