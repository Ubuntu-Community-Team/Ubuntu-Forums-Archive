---
title: "new version ubuntu, not good working samba"
date: 2010-04-29
forum: Networking &amp; Wireless
---

### Post by rainer169 on 2010-04-29
Hi to all,

installed the 9.10 Version of ubuntu. 

Now the situation is:

Four Computers are running under Windos XP-professional SP3
My computer, the fifth has ubuntu as os

After the upgrade to ubunto 9.10 (with the newest updates installed today) I`m unable to access the windows network. Shows me only windows network but when I click on it no list of workgroup is shown and therfore the network cannot be connected

Only with one "trick" get access: 
connect to server, then putting the ip's of th windows computers I've got connection to all allowed dir of all the four windows computers (location: smb://ip-adress)

To install a network printer is impossible neither with cups nor with system-> adaministration->print

At my computer is one printer which works fine. the other printer a Xerox Phaser 6110 is connectet to one XP computer and is configured as network printer under Windows.
The computer (IP-Adress is found but that is all) Printer is not connected.

Trying now for three days I'm really upset because there is one golden rule: Never touch running Systems! But you folks from ubuntu must bring ever second day some 
updates. Nothing against this, but configure your updates in that manner that the updates don't change all my settings.

When I boot my computer with windows-XP all network computers are there and usable.

My Samba config is ok too because otherwise I would not be able to connect to windows computer through the above mentioned trick.

Who can help me really? I do not need any blabla such as try this or try that as I googled for three days and all the answers where crap!

---

### Post by ktmom on 2010-04-29
> **rainer169 said:**
> Who can help me really? I do not need any blabla such as try this or try that as I googled for three days and all the answers where crap!

I'll repeat in this thread what I said in the other one; This comment will drive away all but the most stolid.

Plus double posting makes getting you help confusing as well.

You will likely have to wait until the person who is experienced enough to help you logs on.

---

### Post by Peter09 on 2010-04-29
Have you got winbind installed?
 
```
sudo apt-get install winbind
```

---

### Post by rainer169 on 2010-04-29
> **Peter09 said:**
> Have you got winbind installed?
 
```
sudo apt-get install winbind
```


definitly installed

---

### Post by rainer169 on 2010-04-29
> **ktmom said:**
> I'll repeat in this thread what I said in the other one; This comment will drive away all but the most stolid.

Plus double posting makes getting you help confusing as well.

You will likely have to wait until the person who is experienced enough to help you logs on.


yes Sir but you are obvious not that one. The double post is due to not beeing secure in which thread this post would fit:confused:

---

### Post by Peter09 on 2010-04-30
OK,
check that you can do
 
```
ping <name of a windows machine>
```
 
if this does not work can you post the contents of the file
 
> **/etc/nsswitch.conf**

---

### Post by rainer169 on 2010-04-30
The problem is resolved as I installed my former Ubuntu everything works fine now again. Do not touch running systems

Thank so lot

---

