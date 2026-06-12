---
title: "A network with ubuntu"
date: 2012-10-20
forum: Networking &amp; Wireless
---

### Post by Raafat1991 on 2012-10-20
Hi guys,

I have a laptop with ubuntu 12.04 and a computer with windows 7 and a switch (fast ethernet with 17 port one is labeled with (uplink))

the question: how do i will network them ?

Please remember that i have no internet connection.

---

### Post by 2F4U on 2012-10-20
Do you mean filesharing between Ubuntu and Windows?

[http://www.liberiangeek.net/2012/03/filesharing-in-windows-7-and-ubuntu-12-04-precise-pangolin/](http://www.liberiangeek.net/2012/03/filesharing-in-windows-7-and-ubuntu-12-04-precise-pangolin/)

This wouldn't require require an internet connection, but of course it would require that both machines can see each other on the network.

---

### Post by Raafat1991 on 2012-10-20
Firstly thank you ver much for your interaction with me *_*...

Please consdir this case:

I have two computer with ubuntu, how do i will network them for sharing files and printers etc. ?


thank you again...

---

### Post by critin on 2012-10-20
In both ubuntu machines.
Go to each folder you want to share and click Share by right-clicking.  Open the folders in Property (right click)   and set the permissions to share with certain users or all users.  Be sure to choose 'share files inside' of each folder with the permission/share options.

The system will automatically install samba if you choose to let it--it will ask, say yes.
When finished you may need to restart depending on which version you're using.

---

### Post by Raafat1991 on 2012-10-20
thank you for interaction with me *_*

but what do about my switch ?
what do i do with it ?

What is switch turn ?

thank you again....

---

### Post by critin on 2012-10-20
I've never used a switch, sorry.  If they can see each other, they can share.  Get to them through the file manager.

---

### Post by cariboo on 2012-10-20
> **Raafat1991 said:**
> Hi guys,

I have a laptop with ubuntu 12.04 and a computer with windows 7 and a switch (fast ethernet with 17 port one is labeled with (uplink))

the question: how do i will network them ?

Please remember that i have no internet connection.

If you don't have an internet connection, how are you posting these questions? :-D

As a beginner to networking, it is probably a good idea that you do some research before jumping into it, just so you can understand some of the terminology used. When I built my first home network, I used the guides located [here]("http://www.tldp.org/guides.html") as a reference.

I've also moved this thread to the Networking & wireless sub-forum.

---

### Post by ahallubuntu on 2012-10-20
If possible, obtain a cheap wired router.  I know that not everyone has access to cheap used equipment, but even an old router (10 years old) would work.

Otherwise, you can use your switch and set up your own network.  It may be easiest to do static IP.  Set the IP of one machine to 192.168.1.2 and the other to 192.168.1.3, netmask to 255.255.255.0 .  There is no gateway if you don't have access to another network (the internet).

Once that network is complete, then you can access each machine from the other using its IP address.  You have to enable sharing on each machine to share files.  In Ubuntu, you can probably right-click on any folder you wish to share and look for the "sharing and security" option (varies by the version of Ubuntu you use) and try to follow the directions.  Windows sharing is very different and tends to be complicated in Windows 7.

---

### Post by Raafat1991 on 2012-10-21
[cariboo907;12307569]If you don't have an internet connection, how are you posting these questions? [/QUOTE]:-D



Hhhh a good question,well i'm posting from my work office:)

but the networking operation will be in my home there i have no internet connetion:(
hence, need the networking operation internet connetion?. as i knew no). 


for your guide i will contact , i hope to be helpful

thank you for your interaction with me

---

### Post by Raafat1991 on 2012-10-21
> **ahallubuntu said:**
> If possible, obtain a cheap wired router.  I know that not everyone has access to cheap used equipment, but even an old router (10 years old) would work.

Otherwise, you can use your switch and set up your own network.  It may be easiest to do static IP.  Set the IP of one machine to 192.168.1.2 and the other to 192.168.1.3, netmask to 255.255.255.0 .  There is no gateway if you don't have access to another network (the internet).

Once that network is complete, then you can access each machine from the other using its IP address.  You have to enable sharing on each machine to share files.  In Ubuntu, you can probably right-click on any folder you wish to share and look for the "sharing and security" option (varies by the version of Ubuntu you use) and try to follow the directions.  Windows sharing is very different and tends to be complicated in Windows 7.
  
Hi, i will do what you guide me and i tell you about the result. I hope that i do that successfully

Thank you for your reply .

---

### Post by Raafat1991 on 2012-11-03
Please guys...help me

---

