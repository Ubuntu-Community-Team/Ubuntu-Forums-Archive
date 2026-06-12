---
title: "Need Help- Remote access of Ubuntu 8.04"
date: 2009-04-22
forum: Networking &amp; Wireless
---

### Post by sajid786 on 2009-04-22
Hi 
I got ubuntu 8.04 i like to access remotely from my office.
I register with dyndns.com and got host name and IP address.
I am using router so i used router utility and enter required detail in router.
now i m trying to access from externally but it asking username and password.
what username and password do i need to put ?
do i need to forward any port ?
Please advice me it will be gre8 help

Thanks

---

### Post by cariboo on 2009-04-23
You have to do a couple of things in order to acces your computer from the internet. The first thing to do is to set a static ip address for your computer with Ubuntu installed. I find the easiest way to do this, is to uninstall network-manager-gnome, and install network-manager-admin. You can use synaptic package manager to remove and install programs.

Once you have a static ip address setup you have to port forward what ever port the service you are using from your router to the computer with the static ip address. For instance if you are running Windows on your work computer and you acces the remote computer using putty or winscp you forward port 22 to you home computer.

Remember to use a strong password or your system will be cracked in no time. A strong password should consist of at least 9 upper, lower and numerical characters

---

