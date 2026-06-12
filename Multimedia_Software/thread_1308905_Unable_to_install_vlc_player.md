---
title: "Unable to install vlc player"
date: 2009-11-01
forum: Multimedia Software
---

### Post by dineshrathod2216 on 2009-11-01
Hi, Im on ubuntu 9.10 and im unable to install vlc player. it gives me this error. 
[ATTACH]134028[/ATTACH]
Please help.



Dinesh.

---

### Post by vginov on 2009-11-01
open terminal and type this
 
```
sudo apt-get update
```

It will ask for password. Enter the password 
Once the update is over type the bellow command 

```
sudo apt-get install vlc vlc-plugin-esd mozilla-plugin-vlc

```

---

### Post by dineshrathod2216 on 2009-11-02
> **vginov said:**
> open terminal and type this
 
```
sudo apt-get update
```It will ask for password. Enter the password 
Once the update is over type the bellow command 

```
sudo apt-get install vlc vlc-plugin-esd mozilla-plugin-vlc

```
thanks.

---

### Post by vmnit on 2009-11-03
After executing first command, I executed the second one and I got the following error:

$ sudo apt-get install vlc vlc-plugin-esd mozilla-plugin-vlc
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package vlc-plugin-esd



Please guide me...

---

### Post by mc4man on 2009-11-03
> : Couldn't find package vlc-plugin-esd

That plugin is no longer used, don't worry about it. ( if vlc didn't install then remove that from command

As to orig. issue...
Are you using a ppa for vlc?

The software center won't allow an install of an app from a ppa unless an OpenPGP key has been installed for that ppa ( and even then a reboot is usually needed.

Synaptic package manager and apt-get have no such restriction

---

### Post by vmnit on 2009-11-03
> **mc4man said:**
> That plugin is no longer used, don't worry about it. ( if vlc didn't install then remove that from command

As to orig. issue...
Are you using a ppa for vlc?

The software center won't allow an install of an app from a ppa unless an OpenPGP key has been installed for that ppa ( and even then a reboot is usually needed.

Synaptic package manager and apt-get have no such restriction


I removed the "vlc-plugin-esd" from the command and it worked fine.

Thanks.

---

