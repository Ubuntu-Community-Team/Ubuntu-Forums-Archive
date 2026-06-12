---
title: "network file sharing problems"
date: 2010-12-03
forum: Networking &amp; Wireless
---

### Post by fraserf88 on 2010-12-03
I am having troubles sharing files on my home network. I have a number of pcs connected to a gigabit switch, and they can all ping each other and they can all get out to the internet. I have a Windows 7 desktop, 2 laptops that running ubuntu 10.10, and 2 servers running ubuntu 9.04. When I first set up my network the windows machine had troubles accessing the linux machines but the windows shares were accessable by the linux machines so it didnt bug me.

Anyway, about 2 weeks ago I reformatted my windows machine, and lost the ability to share files to the network. However the windows machine could now acess the laptops which were running ubuntu 10.04 at the time. Yesterday I installed ubuntu 10.10 on the laptops and they cant acess anything now. They can still ping everyone on the network and ssh in, as well as get out to the internet. But they cant access shares on any pc on the network including eachother. And nothing they share can be accessed by other machines on the network. I have installed samba on them and tried both normal samba and samba-4. No luck. So Im a bit confused as to where to go from here. I figure the best place to start is getting the laptops talking again. But Ive been banging my head against the keyboard for a while now with no luck. So i need a bit of help.

Thanks in advance for any help you can provide.

---

### Post by fraserf88 on 2010-12-03
So I got the laptops communicating with eachother and with the servers. I got a bit of help from this thread
[http://ubuntuforums.org/showthread.php?t=1631481](http://ubuntuforums.org/showthread.php?t=1631481)

I had to type 
sudo smbpasswd -a [username]
into the terminal on the laptops. I have never had to use this command before to use samba. In the past it just used my user name and password used to log in to the pc. Now it has to be done separately apparently. Why it doesnt just default like before is strange, but its fixed so thats good. Now all thats left is getting the windows 7 machine to cooperate...

---

