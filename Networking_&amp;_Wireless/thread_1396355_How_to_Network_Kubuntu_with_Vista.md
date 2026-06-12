---
title: "How to Network Kubuntu with Vista"
date: 2010-02-01
forum: Networking &amp; Wireless
---

### Post by Corners on 2010-02-01
I've been searching and searching and all I come back with is a bunch of code that I have no idea what to do with.  Is there someone out there that makes something simple that you can network and share a printer between Kubuntu and Vista?

I have my office computer running Kubuntu, which also has the printer attached to it.  My media machine downstairs is running Vista, which I'd like to be able to print and share files from.

I've been doing some reading that you need to use Samba.  So, I installed Samba through Synaptic, and it appears that nothing happened.  So, I did some more googling, and found I had to install something about system-config-samba, so I did.  I now have a Samba icon under k-menu > System > Samba.  However, when I click on this icon, nothing happens.  It does nothing (just like clicking on the Network Manager icon, which does nothing as well).  So, I am now utterly confused.  What am I doing wrong?  Is there a way to change samba settings via gui?  I'm not comfortable with typing unknown commands into the terminal, as usually there is no explanation as to what's going on.  If there was a step by step explanation, that would be ok, but as of now, there is nothing.

Is there a simple setup tool out there?

Let me know.

---

### Post by superprash2003 on 2010-02-02
presuming you've install samba service already , you just need to make a few changes to the smb.conf file [http://www.prash-babu.com/2008/05/how-to-setup-network-printer-or-share.html](http://www.prash-babu.com/2008/05/how-to-setup-network-printer-or-share.html)

---

### Post by johnson.d on 2010-02-11
There is a web based tool named swat for the configuration of samba where you can configure samba locally or from a remote location. It includes printer configuration also. You can install swat using the following command:

$ sudo apt-get install swat

Now you can access swat from the local machine by typing in the address [http://localhost:901](http://localhost:901) or from another machine by using the url http://<ip-address>:901

The user name is root and the password is root's password

In ubuntu as the root password is not created initially, you can create a root password by using the command:

$ sudo passwd root

---

