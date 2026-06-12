---
title: "Network Manager keeps changing WAP2 Password"
date: 2009-07-21
forum: Networking &amp; Wireless
---

### Post by Stormrider83 on 2009-07-21
Hi,
 
I have a strange problem with network manager. I am running Xubuntu on a Acer Travel Mate 2200. I have installed NDiswrapper and the system recognises my wireless card. I can see my wireless network and indeed all the same networks that my Vista machine can. The problem comes when I try to connect to it.
 
I type in my password and network manager spends ages trying to connect every couple of minutes it asks for my password again. I click on show password to see what I typed previously and it looks like network manager keeps changing my password to a longer (hex?) value.
 
I tried to uninstall Network manager and install Wicd but wicd could not see any wireless networks although it could connect to my fixed network.
 
Does anyone have any ideas? Is it possible to force network manager to accept my password as a string and not change it to a hex value?
 
I am no strange to the terminal if needs be but any suggestions as idiot proof and detailed as possible please.
 
Thanks!

---

### Post by martinbaselier on 2009-07-21
[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/273336](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/273336)

---

### Post by Stormrider83 on 2009-07-21
Thank you I have looked through several threads which outline the same or similar problems. The only solution people seem to have which is definitive is too install wicd but that doesnt find ANY networks...

---

### Post by martinbaselier on 2009-07-21
I don't use any graphical tools to connect, but I read some threads about people successfully using seahorse to set the password.

---

### Post by Stormrider83 on 2009-07-21
Thanks I will give seahorse a go.
 
I would happily connect without any graphical interface, I just don't have the first clue where to start!

---

### Post by Ryuhayabusa on 2009-07-21
i have had success with wicd. highly recommend it.

---

### Post by Stormrider83 on 2009-07-21
I did try it but it would not detect any wireless networks. Network manager at least detects mine and every one in the area even if it does not connect.

---

### Post by martinbaselier on 2009-07-21
connect without graphical interface:


I found a step by step howto here:

[http://ubuntuforums.org/showthread.php?t=263136](http://ubuntuforums.org/showthread.php?t=263136)

If you have the page opened, first stop de networkmanager, to prevent interference. 

**sudo service NetworkManager stop**

(It will start again if you reboot or if you use the above command and replace stop with start)

---

