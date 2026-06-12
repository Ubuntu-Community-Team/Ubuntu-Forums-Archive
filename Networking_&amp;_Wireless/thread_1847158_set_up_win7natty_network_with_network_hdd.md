---
title: "set up win7/natty network with network hdd"
date: 2011-09-20
forum: Networking &amp; Wireless
---

### Post by DisorderlyCitizen on 2011-09-20
hey guys,
 
i'm thinking about setting up a small home network. i've got 2 machines: 1 pc with win7 and one laptop with ubuntu 11.04. the pc is connected via lan, the laptop via wireless. both connect to the internet via a router 
 
also i want to connect an hdd to the router so i can automatically backup my data on both machines and synchronise them (e-mails, documents, pics etc.) i also want my libraries to be on this disk so i can access all my pictues and music from both systems.
 
i read that i need samba to do this. will samba be sufficient on it's own or do i need to study a little more here? i just want to gather as much information as i can before trying this
 
thanks & cheers!

---

### Post by josephmills on 2011-09-20
Hi there here is a video tutorial hope that it helps 
[http://www.youtube.com/watch?v=Bo9HOadl-YM&feature=related](http://www.youtube.com/watch?v=Bo9HOadl-YM&feature=related)
joseph

---

### Post by DisorderlyCitizen on 2011-09-30
sorry for the late reply but i had to study this week for my exams

anyway i managed to get the network working with 2 problems:

1. when i browse my network from my linux machine, i can see all the contents of my windows 7 pc (system32, program files, user accounts) even though i did not share these folders. i tried hiding them in the network to no avail.

2. when i try to access a share folder on my linuxbox from my win7 pc i cant see ANY content, i can access linuxbox from my windows machine but all i get is an empty folder even though there are some files in there.

i was also concerned about how secure this setup is. my router has a internal firewall, but will this be sufficient protection from unwanted guests? i switch of my wifi whenever i'm not connected with my laptop, so that shouldnt be a problem.

---

