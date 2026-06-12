---
title: "Problems Accessing a Windows Domain and Shares via Samba"
date: 2009-07-07
forum: Networking &amp; Wireless
---

### Post by alexlafreniere on 2009-07-07
I'm having some difficulties getting my Linux client to log onto an existing Windows domain and accessing the shared directories there. I've done a lot of research, and there's tons of stuff on getting Windows clients to log onto a domain run by a Linux server, but I can't find much on the other way around. And what is there, is close to indecipherable or so outdated the instructions don't work anymore. So what I'm asking is, could anybody point me towards a simple to follow and up-to-date tutorial on getting a Linux client to log onto a Windows domain with GUI access to the networked drives on that domain. What I'm ultimately trying to achieve is a simple-to-use workstation for hospital workers to get the files they need off a Windows share. Thanks in advance for any help.

---

### Post by 696f6e6963 on 2009-07-07
sudo apt-get install likewise-open
sudo domainjoin-cli join your.fqdn domain_admin_username

And you are succesfully connected to your domain.

---

### Post by superprash2003 on 2009-07-08
take a look at this tutorial [http://www.onlamp.com/pub/a/onlamp/2008/04/01/step-by-step-using-samba-to-join-a-windows-domain.html](http://www.onlamp.com/pub/a/onlamp/2008/04/01/step-by-step-using-samba-to-join-a-windows-domain.html)

---

### Post by alexlafreniere on 2009-07-08
> **696f6e6963 said:**
> sudo apt-get install likewise-open
sudo domainjoin-cli join your.fqdn domain_admin_username

And you are succesfully connected to your domain.

Exactly what does "your.fqdn" stand for, and what if my domain does not have an explicit administrator account?

Would a proper FQDN be something ending in .com or .org? And is there any way I could set up the domain and log in using likewise-open without using an administrator account? Or any similar way where I don't have to mess with config files, just one command and I'm done?

---

### Post by 696f6e6963 on 2009-07-08
You need to join the domain using a domain administrators account - the same is required for Windows. Once you have joined the domain you can login using any of your user accounts setup in AD.

---

### Post by alexlafreniere on 2009-07-08
> **696f6e6963 said:**
> You need to join the domain using a domain administrators account - the same is required for Windows. Once you have joined the domain you can login using any of your user accounts setup in AD.

Is there always an admin account called "Administrator"?

---

### Post by 696f6e6963 on 2009-07-08
It is usually, but not always called "Administrator". However, there is always an administrator account.

---

### Post by alexlafreniere on 2009-07-08
Thanks for the help, I'll look into finding the admin credentials.

---

