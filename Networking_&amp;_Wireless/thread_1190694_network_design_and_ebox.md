---
title: "network design and ebox"
date: 2009-06-18
forum: Networking &amp; Wireless
---

### Post by imaniman on 2009-06-18
Hey guys i was wondering if someone with some networking knowlege could help me.
I work at a small webdesign/development company and i am basically looking at how we can improve our setup.

We have around 7 PCs running either windows xp or windows vista. We have a printer on the network and a usb Hard drive connected to one of the computers which is shared on the network. This external hd is where we can exchange files and store customer websites.

What i think we need is a server with:
An intranet

Roaming profiles/user accounts groups, so each user can log on to the domain and it will load their desktop wallpaper and browser bookmarks etc so we can log onto our meeting computer and have access to everything we would at our computer to show clients

Users not to save work on their harddrive but on a remote shared drive

possibly managing our mail somehow? we all have pop3 mail accounts

I would also like to install subversion and get the rest of my team to use this	for our web development framework
	
possibly connect the printer to the server?

Also to be able to login from elsewhere using VPN

I guess one of the most important things is having as much data in a centralised location rather than on the harddrives we are working on and then having this backed up every night possibly using rsync.

After looking at what i need i found ebox ([http://ebox-platform.com/](http://ebox-platform.com/)) which seems to have everything i need and is simple to use.

So i guess i need some help in how the network should be arranged and the ip addressing scheme? or anything else i need to consider.

We have currently have a modem/router using 192.168.1.1 which then goes to our switch and then to each of our computers. 
How would this ebox fit into this would it just connect to a port on the switch? or would it go modem/router->ebox->switch->computers?

Also can anyone recommend some hardware for the ebox? like how much ram and processing would it need? Like a prebuilt computer?

---

