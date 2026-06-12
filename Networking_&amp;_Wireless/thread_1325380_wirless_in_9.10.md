---
title: "wirless in 9.10"
date: 2009-11-13
forum: Networking &amp; Wireless
---

### Post by ubunewtu on 2009-11-13
hiya all i just put 9.10 on my laptop its got a wireless card but since the interface is totally different from the previous im a litle lost in the hardware drivers nothing comes up the led light wont come on my card is a BCM4318 since i cant turn it on from the button can i get it on from the terminal?

---

### Post by JBAlaska on 2009-11-13
Try this:
Put the LiveCD in your drive and make sure you have "Installable from CD-ROM/DVD" checked in System, Administration, software sources.
Open a terminal and do:
```

sudo apt-get update
sudo apt-get install bcmwl-kernel-source
```
Go to System, Administration, Hardware Drivers and select the Broadcom sta wireless driver, Reboot the machine.

Your Wireless driver should be working

---

### Post by ubunewtu on 2009-11-13
i get this
> dave@dave-laptop:~$ sudo apt-get install bcmwl-kernel-source
[sudo] password for dave: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package bcmwl-kernel-source


---

### Post by trobsh on 2009-11-13
Hello all, 
I installed ubuntu 9.10 two days ago on my lap top, and I am using Linux for the first time in my life. I just cant get my wirless to work its a: broadcom 802.11a b g wlan

Thank You

---

### Post by JBAlaska on 2009-11-13
> **ubunewtu said:**
> i get this
dave@dave-laptop:~$ sudo apt-get install bcmwl-kernel-source
[sudo] password for dave:
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Couldn't find package bcmwl-kernel-source 

Did you "Put the LiveCD in your drive and make sure you have "Installable from CD-ROM/DVD" checked in System, Administration, software sources" before you did:
```
sudo apt-get update
sudo apt-get install bcmwl-kernel-source
```

If so you might have to hook up a wired connection and try those commands again, although I thought for sure "bcmwl-kernel-source" was on the LiveCD of 9.10

[COLOR="Blue"]Edit: trobsh, this procedure should work for you as well.[/COLOR]

---

### Post by ubunewtu on 2009-11-13
missed the part about the cd ty it worked

---

### Post by JBAlaska on 2009-11-13
> **ubunewtu said:**
> missed the part about the cd ty it worked

Sweet! You might want to mark this thread as "Solved"

---

