---
title: "need to deactivate/activate network card on every boot"
date: 2006-04-12
forum: Networking &amp; Wireless
---

### Post by breezyfox on 2006-04-12
hi 
I have just installed flight 6 dapper i am facing one unusual proble.
I am unable to go to internet as My network card is not found working. to make it work every time i have to deactivate and activate and then it works fine.
when boot up again i face the similar situation and i again deactivate and activate it to make it work .
In network it always show activated on every booting up. I have been using hoary and breezy and earlier dapper flight version but such a thing has never happened.
any idea where is the problem.

Thanks in advance
bz

---

### Post by mandrakethepenguin on 2006-04-12
I do not know how to fix these problems, as I am not a developer.  But, I know a way that will prevent you from deactivating/activating your network card. It sounds like the DHCP client isn't requesting an IP address.  Enter this in a terminal on first boot without deactivating/activating the network card. ```
sudo dhclient
``` If you can access the internet after doing this, follow the directions below so it does this on every boot.

Open up a new terminal type in ```
sudo visudo
``` 
At the end of the sudoers file type this in[FONT=monospace] ```
your_username ALL = NOPASSWD: /sbin/dhclient
``` [FONT=Verdana]Save it (Ctrl + O) then exit (Ctrl + X).

Then go up to **System -> Prefrences -> Sessions**. Click on startup programs and add this command to startup```
xterm -e sudo /sbin/dhclient
```This will keep you from having to deactivate/activate your network card at boot.


[/FONT] [/FONT]

---

### Post by breezyfox on 2006-04-13
thanks Mandrakethepenguin
your guide helped me solve. it looks to be ok now.

bz

---

