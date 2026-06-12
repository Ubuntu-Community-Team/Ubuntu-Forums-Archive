---
title: "How to Use the Internet"
date: 2010-06-26
forum: Networking &amp; Wireless
---

### Post by arvindch on 2010-06-26
I have a 3G Internet Modem. To connect to this Internet connection, I have to install an App called - " ZTE Wireless Terminal ".. However, this is a ".exe." file.
I need some help on how to get this running on Ubuntu 10.04 LTS, otherwise I can't use the internet.
Please, find me a solution.

---

### Post by DJYoshaBYD on 2010-06-26
first off, welcome! :)

2nd, a little bit of search would have shown you a program called "Wine"...

Its in your repositories.. you can also install it by using the following command from a terminal

```
sudo apt-get install wine
```

I have had many programs run fairly well using this option..

ALTHOUGH, there may be a native driver/module that would work with your device.. 

try google, and search the forums.. thats how i got most of my solutions.. 

Last but not least, you could always try using VirtualBox, and a virtual machine running Windows XP to get it to work..

Try Wine, and try looking for a native linux solution first though..

---

### Post by Andry22 on 2010-06-26
You can try app called wvdial, first step install wvdial by type in terminal:
```
sudo apt-get install wvdial
```
input your administrator password if needed
then you have to configure your modem first by type:
```
sudo wvdialconf
```
then edit file /etc/wvdial.conf by type:
```
sudo gedit /etc/wvdial.conf
```
input your ISP username and password, save it and then type in terminal:
```
sudo wvdial
```

*****good luck*****

---

