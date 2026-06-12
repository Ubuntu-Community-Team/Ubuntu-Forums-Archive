---
title: "Setting Up A Network with a PC, Network Switch and Nanostation 2"
date: 2011-05-21
forum: Networking &amp; Wireless
---

### Post by msangi on 2011-05-21
Hi,
Really need some help. I am not a novice in using Ubuntu, but far from proficient. I have been trying to set up a network for sharing my internet connection, but have hit a wall after a lot of searches on the web.

Basically, i have a pc, the internet connection (through eth0), a network switch and a nanostation 2. Now, i want the pc to act as a dhcp server, dns server, iptables for firewall and traffic shaping, and squid for user authentication (though correct me if a better option exists. needs to be able to give a time limit for use like a month then automatically disconnects the user)

my problem is that I cannot get the pc and nanostation 2 to communicate properly; actually, when i plug in the nanostation to eth1 (my second ethernet card) it is not picked up.

maybe my approach is wrong, i would really appreciate some help. If i can just connect my pc, the nanostation 2 via the network switch (its a D-link non-manageable switch DES-1008D) and share my internet connection, i should be able to sort out the rest of my needs from that point.

---

### Post by drdos2006 on 2011-05-21
Here is a HOWTO which I found comprehensive and invaluable. Uses Webmin to allow your browser to connect and modify your server settings.
You could also install the Desktop and run the server as a virtual machine using Virtualbox.

> 
Are you using the most current version of this how-to?
Version numbers are located @ top right of this page. Latest versions are available at my homepage [http://woodel.com](http://woodel.com)
Under the Solutions tab
"Setting up a Linux Server, Start to Finish, using Webmin". By Kevin Elwood



Here is a HOWTO which I found comprehensive and invaluable. Uses Webmin to allow your browser to connect and modify your server settings.
You could also install the Desktop and run the server as a virtual machine using Virtualbox.

> 
Are you using the most current version of this how-to?
Version numbers are located @ top right of this page. Latest versions are available at my homepage [http://woodel.com](http://woodel.com)
Under the Solutions tab
"Setting up a Linux Server, Start to Finish, using Webmin". By Kevin Elwood





```

Logon to your server and download from your server with :
sudo wget http://prdownloads.sourceforge.net/webadmin/webmin_1.550_all.deb

Install with :
sudo dpkg -i webmin_1.550_all.deb

Add extra libraries with :
sudo apt-get -f install

```

regards

---

### Post by msangi on 2011-05-23
Thank you. That was a life saver. Spent the last two days pouring over it. Now my network works. Onto the authentication. No rest for the weary.

Once again, thanks, a lot.

---

