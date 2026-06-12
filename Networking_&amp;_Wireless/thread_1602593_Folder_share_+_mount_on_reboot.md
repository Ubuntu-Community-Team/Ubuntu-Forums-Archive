---
title: "Folder share + mount on reboot"
date: 2010-10-21
forum: Networking &amp; Wireless
---

### Post by fatboyandy on 2010-10-21
Hi everyone,

got  2problems if you can help

I've installed storage device manager (to mount my mydocuments partition).  However everytime i switch my machine on i get a message saying it cannot mount and get choice of manual, skip or wait.  waiting does nothing and manual goes to bash (i think).  How can i mount this drive everytime, i've got this working fine on my netbook running mint and works 100% (i followed the same steps).

My 2nd problem is folder sharing, i cannot get this working on ubuntu because the above never mounts the partition.  Also my netbook running mount cannot see the shared folders under the network, the only shares i see are WINDOWS.  I'm not that bothered about windows shares, jsut the LINUX one's.
I followed the shares-admin command and then individually shared the folders using nautilus.

Please help, i'm new and confused.

thanks

---

### Post by Morbius1 on 2010-10-21
You've got a lot going on there.

[1] The partition problem

I have no idea what "storage device manager " is so let's start by getting some info on your environment. Please post the output of the following commands:
```
sudo blkid -c /dev/null
``````
cat /etc/fstab
```[2] The samba problem.
>  I followed the shares-admin command and then individually shared the folders using nautilus.There are 2 completly different ways to use samba to create shares and you're using both on the same folders - not good generally. Post the output of these commands so we can see how you are set up:
```
net usershare info
``````
sudo net usershare info
``````
testparm -s
```

---

