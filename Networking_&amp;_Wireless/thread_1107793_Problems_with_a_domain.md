---
title: "Problems with a domain"
date: 2009-03-27
forum: Networking &amp; Wireless
---

### Post by Impakt1990 on 2009-03-27
Hello i have installed ubuntu on my laptop and this is my school laptop so i joined the domain at school. All students have their own username and password here. If you want wireless internett you have to join the domain. so i joined it.

Domain name: Skole.troms.vgs.no
My Username :ANHY1
My Computer Name: 11-ANHY1

So i used Likewise Open to join it i have checked with the IKT people and i am in the domain. they found my computer online with the oprative system Ubuntu. but the problem is when i am at the login screen i write in this "Skole\Anhy1" then my password then i just get to an orange screen nothing else and when i login into the computer user i can't join the wireless network.

Soo anyone here that can help me with this problem?

Greetings

Impakt

---

### Post by albandy on 2009-03-27
Well first don't use likewise from repositories, don't work well at all, so uninstall it and use the package from likewise page.

Also you need to add the domain user to the required groups in your workstation to use network manager

---

### Post by Impakt1990 on 2009-03-27
Hmmm kk can you explain how i fix the network manager thingy?

---

### Post by albandy on 2009-03-27
Enter as your normal user, open a console and type:

sudo adduser domainuser\\domain group

for example:

sudo adduser ANHY1\\Skole.troms.vgs.no adm
sudo adduser ANHY1\\Skole.troms.vgs.no admin
sudo adduser ANHY1\\Skole.troms.vgs.no plugdev
sudo adduser ANHY1\\Skole.troms.vgs.no netdev

---

### Post by Impakt1990 on 2009-03-27
Hmm having a problem installing a rpm-installer and a rpm.sh file got any suggestions? the rpm.sh file i run in the terminal and then suddenly it closes. and the rpm-installer file there i need to be superuser...

---

