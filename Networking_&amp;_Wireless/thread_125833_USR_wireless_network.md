---
title: "USR wireless network"
date: 2006-02-04
forum: Networking &amp; Wireless
---

### Post by Wofl on 2006-02-04
hello
i now got my ubuntu installed realy good and i love it so far.
now the only thing i need is a driver or whaterver i need to get my network going
i got a wireless card in the pcima slot. it is from usr.  it is one of the maxg ones
[http://www.usr.com/products/networking/wireless-product.asp?sku=USR5410](http://www.usr.com/products/networking/wireless-product.asp?sku=USR5410)

i found this but i dont know how to use it or even to download...
[http://www.linuxant.com/driverloader/](http://www.linuxant.com/driverloader/)

---

### Post by Wofl on 2006-02-05
i coorect myself

it is a 
[http://www.usr.com/support/product-template.asp?prod=5411](http://www.usr.com/support/product-template.asp?prod=5411)

and the linux driver links to 
ndiswrapper.sourceforge.net/

someone know how that works?

---

### Post by Wofl on 2006-02-05
[http://www.tuxmagazine.com/node/1000167](http://www.tuxmagazine.com/node/1000167)

i found this and got a bit on
now i am stuck again...
1) "Open up a terminal and change to the directory containing your drivers"

driver is in /home/nils/usrmaxg.inf
but how do i change there?

2)"You need root privileges for this step. Either use the su - command to change to the root user, or if you have your system set up for it, use sudo."

using sudo just gives an error thingy
usund su asked for the password, but when hitting the keys nothing happens...

please help me

---

### Post by Lambert on 2006-02-05
in terminal to change and move around you use **cd**

because it's in your home folder you just type **cd** and you'll be in the correct folder. In other instances you would add the path so here is an example

```
cd /home/me/downloads/music
```

This will put you in a file called music

to install the driver the command would be 

```
sudo ndiswrapper -i usrmaxg.inf
``` 
when it asks for a password it's just your normal user password. (you need to have admin/sudoers privledge if you're not the original user setup during install)

Here are some good links for you to read.

[https://wiki.ubuntu.com/forum/hardware/ndiswrapper]("https://wiki.ubuntu.com/forum/hardware/ndiswrapper")
[https://wiki.ubuntu.com/BasicCommands]("https://wiki.ubuntu.com/BasicCommands")

---

### Post by Wofl on 2006-02-06
many thanks for that help
i got the driver isstalled by now
just one problem
the devicemanager defines the card as unknown device and doesnt match the driver to the card
what should i do now?

---

### Post by Wofl on 2006-02-07
noone got an idea?

---

