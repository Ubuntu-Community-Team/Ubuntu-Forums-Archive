---
title: "Cannot connect to internet"
date: 2011-10-30
forum: Networking &amp; Wireless
---

### Post by Adarzh on 2011-10-30
Hi,

First of all i don't know much about Linux system so please excuse.

I have an old desktop machine with Lubuntu 11.10 installed in it. The problems is that i cannot connect to internet. The network manager always shows 'Connection Disconnected' (something like that) message. 

What i want is a Wired Connection. The default settings available for Wired connection is not working. I don't think this is a problem with Lubuntu bcoz i had this problem in Ubuntu 11.04, Ubuntu 11.10 and  Xubuntu 11.10.

I had used Ubuntu 8.04, Ubuntu 8.10 before but i never had a problem before.

I want to add one more thing. On the boot menu we have the recovery option. When i choose that option and select Update system option, suddenly everything will work and it will automatically connect and  when i restart the machine and login again there will  have connection. but if i try to update any package or try to install through  update manager or apt-get install, after installation and after the reboot, the connection will became unavailable again. 

Any help is appreciated.

---

### Post by Adarzh on 2011-10-31
Any idea why this is happening ?.

---

### Post by WasMeHere on 2011-10-31
Hi Adarzh,

Wired internet is almost always working with Ubuntu, but unfortunely not for you. It seems to me that there is something started in the normal startup, that blocks the function, and that is changed after your updating in recovery mode. *I think there are people here at the Ubuntu Forums, who can tell, what could be the cause, and solve the problem for you with the current version*.

But if you wait in vain for a solution, there might be ways to circumvent the problem using another version or flavour of Ubuntu or more generally, Linux.

You did not list Ubuntu 10.04 LTS. That version is very well tested and debugged and it will be supported until April 2013. I run it on my 'workhorse' computer and suggest that you download an iso file and try it. You can also try Linux Mint 9 or 11 (based on Ubuntu 10.04 LTS / 11.04). Sometimes you need to try a few of them live from a CD or USB drive and install the version that feels best.

Have fun finding out about linux :-)
Olle

---

### Post by Adarzh on 2011-10-31
Olle,

Thanks for the reply. The main reason i decided to stick with lxde is because of its low memory usage. 

I'm not sure whether there is a version of Lubuntu for 10.04. Anyway i will download and install Ubuntu 10.04 and let us see where it goes.

Thanks
Adarsh

---

### Post by WasMeHere on 2011-10-31
No, at least not an official version, but there is Xubuntu 10.04, which has a small foot-print too.

---

### Post by cavalier911 on 2011-10-31
Adarzh,
When grub boots lubuntu in (recovery mode) which is single user mode you have root privileges.Since your connection works when your root then the issue could be Network Manager not giving regular user permission to use network connection.I use Lubuntu Lucid 10.04 so interface may be a little different.

Boot Lubuntu in regular mode,logon as regular user.
Right click Network Manager tray icon by clock/Choose Edit Connections...
Left click opens Network Connections
Wired tab/Highlight ethernet device auto eth /Click Edit... button
Editing auto eth
Check **Connect Automatically**
Check **Available to all users**
Click Apply... button
This will launch Authenticate box.
Enter users password.
Click Authenticate button
Reopen Editing dialoge to verify the box's are still checked.
Click Cancel button if they are.
Reboot

Link to Lubuntu 10.04 LTS
[http://lubuntu.lafibre.info/10.04/](http://lubuntu.lafibre.info/10.04/)

---

### Post by Adarzh on 2011-11-02
cavalier911,

Sorry for the late reply. I just reinstalled Lubuntu 11.10 again. Now this time evreything seems to be working. There is every chance that it will break again if update or add new applications. 


Thanks 
Adarsh

---

