---
title: "Ubuntu vs Mint - Network browsing"
date: 2010-03-12
forum: Networking &amp; Wireless
---

### Post by wbm on 2010-03-12
I use Ubuntu but also try out Mint, Fedora, Mandriva etc. etc.

I Ubuntu 9.10, when I go to Places < Network, I get an error

In Mint 8, when I go to Places < Network, all computers on the network show up.

In Ubuntu I can access the same servers by typing in the IP address.

So how do I make Ubuntu behave like Mint in regards to Network browsing?


Secondly, when connected via the IP address in Ubuntu, only some apps, mainly Gnome apps can access the network shares. DigiKam, GwenView etc. can see the shares, but then say they do not exist when I click on them?!?

Thanks!

---

### Post by coffeecat on 2010-03-12
First of all, install the bits of samba you need. The easiest way is to create a share in Karmic by right-clicking on a folder (make a special one if you want) in your home and selecting 'sharing options'. That will cause the samba stuff to be installed before you can actually create the share. You will need to log out and log in before the share is activated.

That might fix your inability to find shares from the Places menu. If not have a look at the following link and go through each of the points.

[http://ubuntuforums.org/showthread.php?t=1169149](http://ubuntuforums.org/showthread.php?t=1169149)

---

### Post by wbm on 2010-03-12
> **coffeecat said:**
> First of all, install the bits of samba you need. The easiest way is to create a share in Karmic by right-clicking on a folder (make a special one if you want) in your home and selecting 'sharing options'. That will cause the samba stuff to be installed before you can actually create the share. You will need to log out and log in before the share is activated.

That might fix your inability to find shares from the Places menu. If not have a look at the following link and go through each of the points.

[http://ubuntuforums.org/showthread.php?t=1169149](http://ubuntuforums.org/showthread.php?t=1169149)


Samba is installed and I can share etc. Firewall is off.
I was hoping for an answer like this:

In Mint look at "abc" and compare to Ubuntu "xyz"
Change Ubuntu "xyz" to "abc".

---

### Post by coffeecat on 2010-03-13
> **wbm said:**
> 
In Mint look at "abc" and compare to Ubuntu "xyz"
Change Ubuntu "xyz" to "abc".

Not many people run both Mint and Ubuntu. If you go through the link I gave your samba sharing problems will be solved. Your choice.

---

### Post by wbm on 2010-03-13
> **coffeecat said:**
> Not many people run both Mint and Ubuntu. If you go through the link I gave your samba sharing problems will be solved. Your choice.

I run many different distros, some at home for my daily use, and several at work in Virtual Box and on dedicated hardware. I also experiment with KDE vs. Gnome etc.

Anyways, I appreciate the link and I did read through most of it (several pages).
Here is how I fixed my network browsing problem.
I un-installed Firestarter. That did it.
Curiously, turning the firewall off, restarting, verifying that it is still off did not work the same way. Only a complete un-install did the trick.

---

### Post by coffeecat on 2010-03-13
> **wbm said:**
> I un-installed Firestarter. That did it.

Ah firewall issues. They cause 90% of networking and share problems. :) You're better off with gufw if you really want a GUI frontend to IP tables.

---

### Post by Tikkyca on 2010-03-13
Everything works great on my ubuntu without lag,better then on windows before.

---

### Post by wbm on 2010-03-13
> **coffeecat said:**
> Ah firewall issues. They cause 90% of networking and share problems. :) You're better off with gufw if you really want a GUI frontend to IP tables.
I'll give gufw a try, thanks.

---

### Post by coffeecat on 2010-03-13
> **wbm said:**
> I'll give gufw a try, thanks.

One thing to beware of with samba shares and gufw. There's no preset to open up the firewall for just smb. A big omission in my opinion. There's a howto on this forum somewhere for the individual rules for smb, but this only worked in Jaunty. Something changed in Karmic and whatever I did, gufw blocked smb shares.

That is until I simply opened up everything for my local network with "sudo ufw allow from 192.168.1.0/24". See here for more:

[https://help.ubuntu.com/community/UFW](https://help.ubuntu.com/community/UFW)

---

### Post by wbm on 2010-03-15
> **coffeecat said:**
> One thing to beware of with samba shares and gufw. There's no preset to open up the firewall for just smb. A big omission in my opinion. There's a howto on this forum somewhere for the individual rules for smb, but this only worked in Jaunty. Something changed in Karmic and whatever I did, gufw blocked smb shares.

That is until I simply opened up everything for my local network with "sudo ufw allow from 192.168.1.0/24". See here for more:

[https://help.ubuntu.com/community/UFW](https://help.ubuntu.com/community/UFW)


I did the same thing with Firestarter on my other computer and added rules for my local machines.

I have another question. I noticed when I share a folder I get a hand holding the folder icon. After a reboot or log in/out though the icon reverts back to the normal folder icon, even though the folder is still shared. Right clicking on it I cannot un-share it until I first share it again (even though it is already shared). As I have both Gnome and KDE, I also have a KDE application called "Shared Folders". My now "normal icon" but still shared folder does not show up as shared there either. 

So how can I tell which folders are shared on my machine without going to another machine?
Thanks!

---

