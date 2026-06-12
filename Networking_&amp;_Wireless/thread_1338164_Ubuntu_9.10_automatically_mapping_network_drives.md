---
title: "Ubuntu 9.10 automatically mapping network drives"
date: 2009-11-26
forum: Networking &amp; Wireless
---

### Post by chrisdee on 2009-11-26
Hello.

I wonder what the easiest and best way to permanently automatically map network drives so they are remembered after reboot. I'm having a hard time finding any good and simple instructions on how to do this. How is this specifically done ?


Question number two is how do I add links to a windows terminal server from the Ubuntu 9.10 login windows. I would like to give users an easy and conveniant way to click on a link (in the ubuntu login screen) and be directed to a windows terminalserver login window, instead of using terminal server client in ubuntu.

Thanks:)

---

### Post by Iowan on 2009-11-26
Probably the best way would be to set up connection in **fstab**. There are a couple of How-To's around. I have them bookmarked... but on my home machine.

---

### Post by chrisdee on 2009-11-27
Thanks. Would apreciate if you could post the links to the howtos:)

---

### Post by Iowan on 2009-11-27
[http://ubuntuforums.org/showthread.php?t=283131]("http://ubuntuforums.org/showthread.php?t=283131")
[http://ubuntuforums.org/showthread.php?t=288534]("http://ubuntuforums.org/showthread.php?t=288534")

---

### Post by chrisdee on 2009-12-01
Thanks man:D

---

### Post by chrisdee on 2009-12-04
How about adding links to a windows terminal server from the Ubuntu 9.10 login windows.

Any idea how this is done ?

---

### Post by northd_tech on 2009-12-04
> **chrisdee said:**
> How about adding links to a windows terminal server from the Ubuntu 9.10 login windows.

Any idea how this is done ?

I've mainly worked with setting up Windows (and Mac) network printers for various Linuces, but I'll wager that you will need to install a bunch of stuff for a thing called Samba (that is the Windows file and printer sharing "language" for lack of a better term).  There are whole books written about Samba, and I'm no expert with it, but it's a bit of a hassle under Linux becuase there are several versions, and they aren't compatible from what I've seen.  

Then once a Samba (client at least, and maybe a server too) is running under ubuntu, you need to set up the Windows Network/Server names (that you need to access from the Microsoft side of the network).  Then you can usually browse the windows network for various machines and shared resources, **if** you have the right applets and/or tools installed.  (I just set one up for Samba printing under Karmic Koala 9.10 recently, but I don't have access to that laptop until later tonight, or possibly next week).

Here is a big (apparently messy) unbuntuWiki article about Samba (which I can **assure you** is a very messy subject in its own right ;) ):

[https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)

---

### Post by KeLa on 2009-12-04
Actually Samba has nothing to do with Windows Terminal servers so you don't need any of the Samba stuff here.
I don't have answer to you about terminal server connection from login screen.
I have always logged to linux and from there used rdesktop or what ever terminal clients there is for that.
Samba is for connecting to file shares on windows servers and workstations and creating shares that windows clients can connect to.

---

### Post by chrisdee on 2009-12-07
Thanks.

This is for convenience for the users, so they don't have to login to ubuntu first and then login with Terminal Server Client.

It would be much easier if a link was provided in the ubuntu login window. Then upon clicking on the link the user get transferred/redirected to a spesific windows terminal server login.

Anybody else have any tips/ideas how this is done ?

---

