---
title: "Turn an old PC into a File Server?"
date: 2010-01-05
forum: Networking &amp; Wireless
---

### Post by Gogeden on 2010-01-05
I have this old PC that I want to turn into a File Server. I want to use my laptop as the MAIN computer that will access the File Server (Old PC).


Where do I start? :D :lolflag:

---

### Post by fatbotgw on 2010-01-06
I would start with the [Server Guide]("https://help.ubuntu.com/9.10/serverguide/C/index.html") and go from there.  
It will get a basic server going for you and explain how to set up some of the other uses for your server.  

Also, don't forget to use the Search function of the forum as there's a good chance your questions might have been asked and explained before.

---

### Post by jose07 on 2010-01-06
Look into Samba, it's easy to setup, and Dnsmasq for DNS.

---

### Post by tgalati4 on 2010-01-06
Don't forget to add some ram to that old PC.  Once you see how reliable it is, you will be loading it up with more and more functions.

---

### Post by johnson.d on 2010-01-06
For file server requirements, You can use Ubuntu server edition. The minimum requirements for installing Ubuntu server 9.10 would be any Intel or AMD processor with 192 MB of RAM. If your hardware fulfills these requirement, you can go ahead with your file server installation on the old PC. you can install the specific file server (like samba or nfs) after you install the Ubuntu server.

---

### Post by Gogeden on 2010-01-06
Now, with Ubuntu Server Edition, can I make the old computer basically a giant flashdrive that I can copy files off to from a ethernet cable? Another thing, do I have to a crossover cable or a straight through?

Thanks :D

---

### Post by CharlesA on 2010-01-06
If you've got a router, you'd be using a straight thru cable.

Basically you set up shares with Samba and can transfer files to/from them at will.

---

### Post by rabdoel on 2010-01-06
If its just a file server you want , maybe have a look at freenas

I have a freenas box running currently that serves as
- itunes server
- nas server 
- web server 
- torrent downloader ( for legal stuff only ofcourse )

I have tried a couple systems to find my perfect system

these are the following servers I tried, 
1)SUSE ( very good, to powerfull for just a home server, samba and permissions are a hell)

2) Ubuntu EBOX ( again very good, however this ran fine on my normal pc P4 as a test but when I tested it on my mini-itx it just did not want to install)
[http://www.ebox-platform.com/](http://www.ebox-platform.com/)

3)Amahi home server ( perfect server box , they are trying to become a competitor of ms windows home server , not that hard ofcourse. VPN and anything a home server need. I was in love with this server however it was to heavy for my little mini -itx epia 1ghz. used to be based on fedora core , but I am hearing rumors that its moving over to ubuntu ) - [http://www.amahi.org/](http://www.amahi.org/)

4) Freenas ( again perfect , fast and small and really has the things I would use nothing more and nothing less)

Bottom line is , you need to find out by tinkering what you really want to use the file server for and try to find the best linux distro for it :-)

---

### Post by Gogeden on 2010-01-06
So do I have to use a switch? Or could I just run a single straight through cable from my laptop to the old PC?

---

### Post by Gogeden on 2010-01-06
Not to mention I am using this locally. XP

---

### Post by Iowan on 2010-01-06
> **Gogeden said:**
> So do I have to use a switch? Or could I just run a single straight through cable from my laptop to the old PC? You can connect PC-PC... that's where you'd use the crossover cable. Unless one of the machines is also a DHCP server, you'll need to set up networking manually (avahi is an option).

---

### Post by Johann-1.0 on 2010-03-04
Hello Friends. Basically, I want the same thing. I want to turn my celeron 1,8 GHz, 256 Ram PC with no display into a server that could connect to the internet and manage my print tasks. I want my laptop to connect to that computer, so if I want to print a document, the old PC manage it. May you assist me in achieving that? I use Ubuntu really well, but my knowledge on servers is very poor. I will appreciate if you help me in an easy way. Thanks in advance.

---

### Post by cariboo on 2010-03-04
See [Post #2]("http://ubuntuforums.org/showpost.php?p=8617615&postcount=2") in this thread.

---

