---
title: "trying to bond nics"
date: 2010-01-26
forum: Networking &amp; Wireless
---

### Post by hosinfefer on 2010-01-26
Hi Guys

I am using this guide....[https://help.ubuntu.com/community/UbuntuBonding](https://help.ubuntu.com/community/UbuntuBonding)

Once i do the sudo vi /etc/modprobe.d/bonding.conf it opens up a window. I enter the date alias bond6 bonding
options bonding mode=0 miimon=100

but I dont know how to save it. IS there a keyboard shortcut? there is no save in the tabs at the top.

thanks for the help

---

### Post by Iowan on 2010-01-26
You could also use one of the following to edit the file:
```
sudo nano /etc/modprobe.d/bonding.conf
``` 
```
gksudo gedit /etc/modprobe.d/bonding.conf
```
I don't use **vi** often enough to remember the commands, but I found [this]("http://www.lagmonster.org/docs/vi.html") cheatsheet for you.

---

