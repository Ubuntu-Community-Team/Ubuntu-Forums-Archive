---
title: "Solution for File Sharing network?"
date: 2009-05-22
forum: Networking &amp; Wireless
---

### Post by tmaz42o on 2009-05-22
I want to set up a File Server that me and my friends can access from anywhere. I will be using Ubuntu at home and he will be using Windows XP at his house. My plan of attack was to use use the Ubuntu Server as a File Server and install VPN on it so my friend can access it from his house. But what would be the best solution to accomplish secure file sharing between me and the server and my friend and the server? I also want it to be secure and at the same time fast transfer speeds.

Also, is it necessary to encrypt the files on the hard drive or no?

---

### Post by alarme on 2009-05-22
Try openssh daemon at server.  Create accounts for your friends, and put shared files in a directory tree with right permissions.
Then, you and your friends can access your files from elsewhere.  From windoze, I connect to my home with Filezilla.  From other linux box, command line ssh or nautilus (I think is available one version of Filezilla for linux).  If you have a router, remember to configure it to redirect port 22 to the server, and if the router has a firewall, configure it properly.

---

### Post by tmaz42o on 2009-05-22
As for the VPN, should I put the VPN on my Firewall/Router or on the Ubuntu Server itself? And is it worth it to encrypt the hard drive of the File Server even if I'm behind a Firewall?

---

### Post by superprash2003 on 2009-05-22
vpn on ubuntu server.. not required ..

---

### Post by tmaz42o on 2009-05-22
So VPN on my Router/Firewall then? Or is there a more secure alternative for connecting from a different location?

---

### Post by superprash2003 on 2009-05-23
just open the required ports in your router , let ubuntu handle the rest

---

