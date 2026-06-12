---
title: "Get “unsupported key algorithm in certificate” when using ssh."
date: 2012-06-13
forum: Networking &amp; Wireless
---

### Post by DallasTxSoftwareMan on 2012-06-13
I am trying to use ssh to log into a Mac with Lion OS.  I did [COLOR=#000000][FONT=Verdana, sans-serif][SIZE=2]ssh-keygen -t rsa on the Mac to generate the public key and then copied this to the file $HOME/.ssh/authorized_keys file on an Ubuntu 12.04 machine.[/SIZE][/FONT][/COLOR]

 After doing [COLOR=#000000][FONT=Verdana, sans-serif][SIZE=2]ssh usernameonmac@macname it asks me for a password.  I get the following in the auth.log file:[/SIZE][/FONT][/COLOR]

 ubuntu gnome-keyring-daemon[1346]: unsupported key algorithm in certificate: 1.2.840.10045.2.1

 I tried the fix below and it did not help.

 [https://bugs.launchpad.net/ubuntu/+source/gnome-keyring/+bug/914305](https://bugs.launchpad.net/ubuntu/+source/gnome-keyring/+bug/914305)

 I found this as well, but don't really know if it will work, or what it means when it says “A workaround consists in installing 'gcr' by hand.”.  I tried using the Synaptic Package Manager to reinstall some gcr packages I found there, but that didn't help.

 [http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=673845](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=673845)

---

### Post by DallasTxSoftwareMan on 2012-06-14
Does anyone know what was meant above when they said  “A workaround consists in installing 'gcr' by hand.”.  That appears in the link:

 [http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=673845](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=673845)

---

