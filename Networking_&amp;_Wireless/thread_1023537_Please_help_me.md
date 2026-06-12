---
title: "Please help me"
date: 2008-12-28
forum: Networking &amp; Wireless
---

### Post by faster154 on 2008-12-28
I just recently installed Ubuntu.
I love it but i dont have any way of connecting to the internet with it.

I dont know how to install the drivers for my card.
I have this Wireless PCI/cardbus card- [http://www.zonetusa.com/DispProduct.asp?ProductID=303](http://www.zonetusa.com/DispProduct.asp?ProductID=303)

I can upload the files that are on the CD(I think they are the drivers)

How can i make my Desktop get internet?

Please help

---

### Post by theozzlives on 2008-12-28
Do you have a wired card that works? If so go to add/remove and install ndiswrapper to use the windows drivers to connect, which version of Ubuntu do you have?

---

### Post by faster154 on 2008-12-28
I only have a Wireless PCI card.
I am running Ubuntu 8.10....I believe.

---

### Post by theozzlives on 2008-12-28
hmmmm 8.10 solved all my wireless probs. go to system>administration>software sources, and check the cd-rom box, insert your cd and go to applications>accesories>terminal and type:
```
sudo apt-get install ndiswrapper
```
see what that does

---

### Post by faster154 on 2008-12-28
reading package list...done
building dependency tree
reading state information...done
E: couldn't find package ndiswrapper

can i manually install ndiswrapper?
I found the download link and downloaded ndiswrapper-1.53

---

### Post by theozzlives on 2008-12-28
ok try that is it a *.deb file?

---

### Post by faster154 on 2008-12-28
it is a tar.gz file

---

### Post by theozzlives on 2008-12-28
wait, before you do that, left click on the computer in the upper right corner and see if your network is in there.

---

### Post by faster154 on 2008-12-28
Ya it shows Wired...Wireless...Mobile Broaband...VPN...DSL.
But i cant connect with wireless.

---

### Post by theozzlives on 2008-12-28
you have a broadband card?

---

### Post by faster154 on 2008-12-28
Ya but i dont have internet.
Im using wifi.

---

### Post by theozzlives on 2008-12-28
[http://archive.ubuntu.com/ubuntu/pool/main/n/ndiswrapper/]("http://archive.ubuntu.com/ubuntu/pool/main/n/ndiswrapper/")
Right click on that computer and make sure "enable wireless networks" is checked

---

