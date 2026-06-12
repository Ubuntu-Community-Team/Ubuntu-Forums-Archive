---
title: "can't connect wireless keyboard."
date: 2009-12-22
forum: Networking &amp; Wireless
---

### Post by fridrikh on 2009-12-22
I'm new to Linux and have been having trouble setting up my Logitech dinovo keyboard and mediapad.  After setting up ubuntu 9.1 the keyboard worked but none of the quick lunch buttons worked, the media pad did not work but the mouse worked (none of the extra buttons did work though).
I was wanting to set the keyboard up and googled this issue, found out that I should set the keyboard and mouse up through the bluetooth setup, but I never got the bluetooth icon in the upper right corner.
I've got bluez-utils, bluez-gnome, blueman and some other bluetooth packages I found, after that the bluetooth icon in the top right corner.  
Befor doing this I could not use the "hcitool scan" command in the terminal,  after installing these packages the command worked.
Aftre installing these packages the keyboard soes not work at all, but my mouse still works.  When I click on the bluetooth icon to try to connect the keyboard and mediapad they can be found (but not my mouse) but I can't connect to them, I'm asked to write a PIN number that I do not have, I've tried 1234, 0000 and various basic PIN nr. 
After googling this I've found that this might be because of something is missing in my hcid.comf  I think that might be righ, because searching for my hcid.conf in /etc/bluetooth/ I find nothing.  Is there maybe a way to create a new hcid.conf that could fix this problem?  Any help would be apreciated since I really do not want to reinstall Ubuntu, takes some time being a newb.

---

### Post by fridrikh on 2009-12-23
bump

---

