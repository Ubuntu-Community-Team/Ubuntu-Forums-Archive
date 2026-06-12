---
title: "Modem string"
date: 2005-03-04
forum: Networking &amp; Wireless
---

### Post by zigcatus on 2005-03-04
:roll: 
Hi All

I am new to Ubuntu but have used Mepis and Suse what I need is how can I change
my speed of my modem (string) as I have a very bad phone line I have done a MODE test  with my local Telco and found my speed has to be set at 40,000 I run  D-Link 56K modem but need to know how to add the string  in the right place. I have looked around Ubuntu but no go, it a clean install so do I need to install other software I am back to windows untill I can fix this.

Regards

zigcatus

---

### Post by m4ng0 on 2005-03-04
Assuming you have used
sudo pppconfig
and you have named your connection "myconnection", you can manually edit
/etc/ppp/peers/myconnection (change "myconnection" with proper name).
You should find a line saying:
115200
You can change it to your value.
If you have to give your modem a special init string, edit
/etc/chatscripts/myconnection
and search for "modeminit".

---

### Post by zigcatus on 2005-03-09
[QUOTE=zigcatus]:roll: 
Hi All

I am new to Ubuntu but have used Mepis and Suse what I need is how can I change
my speed of my modem (string) as I have a very bad phone line I have done a MODE test  with my local Telco and found my speed has to be set at 40,000 I run  D-Link 56K modem but need to know how to add the string  in the right place. I have looked around Ubuntu but no go, it a clean install so do I need to install other software I am back to windows untill I can fix this.

Regards

zigcatus[/QUOTE]

Hi m4ng0

 Thanks for the quick post, but no that not the problem my modem connects to the net but with the crap phone line I have, I need to add the modem string (x3+ms=12,,,40000 s202=128)with out the string I can connect but not see any webpages or download any thing and Ubuntu device manager is not showing my modem is there any other way to setup the modem string and whats a good Howtwo on modem setup for Ubuntu linux.
Other then this problem I find Ubuntu a great distro.

---

