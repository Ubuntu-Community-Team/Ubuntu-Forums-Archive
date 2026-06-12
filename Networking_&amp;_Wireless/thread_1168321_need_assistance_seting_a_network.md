---
title: "need assistance seting a network"
date: 2009-05-23
forum: Networking &amp; Wireless
---

### Post by rreyes1316 on 2009-05-23
Been toying around with Ubuntu now for over a month now and have installed it on 3 pc's. Now I am ready to network them all together. My Desktop has all of my files on an extra internal TB drive--It is running 9.04. The other pc's are as follows: Netbook (Ubuntu Remix), laptop (Xubuntu), and another desktop in my sons room (Vista). I would like all my pc's to access the TB drive and my sons pc only to access the music on the TB drive. What are the steps needed?

Thanks

---

### Post by Kareeser on 2009-05-23
What type of hardware do you have?

You'll need a wireless router.

---

### Post by rreyes1316 on 2009-05-24
YES. I have a wireless router. I had everything setup when I had WinXP but since the move to linux I have not had anything networked together. I tried to look for the Network setup wizard but I guess that's a windows thing:-) Things just look foreign to me.

---

### Post by superprash2003 on 2009-05-24
are the machines able to ping each other?? if so , then you can setup file sharing , you could either use NFS or samba for this

---

### Post by rreyes1316 on 2009-05-24
I found Samba in the add/remove apps. When I searched for NFS I found JFTP--is this the other one? Do I have to use all the same app for all the computers?

---

### Post by lisati on 2009-05-24
Have a look here: [http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605)

---

### Post by LinuxRules1 on 2009-05-24
If you would like to have a UI for configuring the samba shares instead of editing the configuration files manually, go to terminal and type 

sudo apt-get install system-config-samba

then all you have to do is go to System>>Administration>>Samba

It will also take less time if you configure samba with the UI

---

### Post by Iowan on 2009-05-24
[Here]("http://samba.netfirms.com/") is a set-up page for Samba.  [Another]("https://help.ubuntu.com/community/SettingUpSamba") help page that may be useful. Eventually, you'll want to see [this]("http://ubuntuforums.org/showthread.php?t=288534") How-To.

---

### Post by rreyes1316 on 2009-05-24
I was able to get my network setup with my netbook ubuntu remix and desktop 9.04. I cant access teh files via the laptop with Xubuntu XFCE. There is no network folder available. I tried to follow the steps for a client setup.

---

### Post by rreyes1316 on 2009-05-24
So I went to the vista machine and I am able to view the network except for the server pc ( the TB drive). I still cannot access anythi g via the xubuntu pc. 

Anyone ?

---

### Post by amendt on 2009-05-24
[Giver]("http://amendt.blogspot.com/2008/12/christmas-is-time-for-giver.html") works for me.

---

