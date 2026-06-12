---
title: "How Do you Possibly Remotely Connect??"
date: 2009-04-19
forum: Networking &amp; Wireless
---

### Post by person9 on 2009-04-19
I would like to Remotely Connect to my friend's computer using Vinagre. First, we were able to edit our Preferences via System>Prefs>Remote Access or whatever, but then I realized I didn't have Vinagre. So, I installed it. Now we both have it, and we both have the same settings on preferences.

We assume that the way to do it is to go to Machine > Connect and type the other person's IP address, and hit Connect.

There is a black screen where the desktop should/will appear, and the other person does not get a notification. Nothing else happens.

What are we doing wrong here? P.S. we can each "remotely connect" to our own IP's and like weirdly control our own computer. Thanks.

---

### Post by superprash2003 on 2009-04-19
are you entering his external ip and not LAN ip.. is port 5900 open for him>?

---

### Post by prshah on 2009-04-19
> **person9 said:**
> 
We assume that the way to do it is to go to Machine > Connect and type the other person's IP address, and hit Connect.


This is more or less correct, but you need to open ports through your system firewall, as well as your Internet router (if you're using one- likely).

The relevant port is 5900 + desktop offset (Usually 1). If in doubt, simply open up ports 5900 and 5901.

To open the ports in your router (called port forwarding), we need to know the make of the router you are using; or you can check the procedure out yourself, by finding the instructions relevant to your model on Internet router on [www.portforward.com](www.portforward.com).

You also have to allow 5900/5901 through your software firewall (usually ufw). You can check the status of your firewall by opening a terminal and giving the command ```
sudo ufw status
```

While testing the connection, you can disable the firewall with ```
sudo ufw disable
```. If it works, immediately disconnect and re-enable your firewall with ```
sudo ufw enable
```, and allow the VNC (/vinagre) ports with the command```
sudo ufw allow 5900
sudo ufw allow 5901
```

Use strong passwords everywhere.

Post back if you need more details.

---

