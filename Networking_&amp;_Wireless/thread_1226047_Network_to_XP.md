---
title: "Network to XP"
date: 2009-07-29
forum: Networking &amp; Wireless
---

### Post by Gem01 on 2009-07-29
My home network comprises of:
PC1 Win XP SP3 (Hardwired to Belkin wireless router)
PC2 Dual boot XP SP3 & Ubuntu jaunty jackalope (wireless)
Lap1 Win Vista SP1 (wireless)
Lap2 Win 2K SP4 (wireless)
 
All computers are running Zone Alarm firewall
 
With all running windows, every computer can see and share with each other
With ubuntu running on PC2, every computer can see and share with each other, but the ubuntu PC cannot connect to PC1 (win XP), no problems to the other windows versions, and alarms with "unable to mount location, failed to retrieve share list from server"
 
Have "pinged" PC1 from ubuntu and comes up ok
 
As a first thought I made PC1 wireless, but no change, turned off firewall, no difference
 
By going wireless on PC1, I think I have eliminated any possible router problem, so I think it has to be a setting in Win XP, that is not set by default in Vista or Win 2K.
 
Has anyone got any ideas?
 
Gem01
 
New EDIT
 
Followed link from coffeeCat and still could not connect
Went into "Red Herring" mode and swapped out PC1 for an equivalent make and model of PC, same version OS
Result, could see it
Brain said it must be the original PC1 installation, so reinstalled windows, no difference
Then thought logically and did a compare after running cmd-ipconfig/all on both PC's
only difference was IP address
Then realised that my new Belkin wireless router does not appear to allocate new IP addresses in order of connection, each time it boots, as my linksys appeared to do
So went into setup, altered my IP allocation addresses, rebooted everything, hey presto, now can see PC1 from Ubuntu
I can only assume that the link did actually work, but ubuntu maybe stored the original fault (or the human involved was at fault)
The only other change was I updated ubuntu again and it is now running, I think it is, Kernel 14
Anyway, end result, network fully running as required
 
Many thanks to those that posted
 
Gem01

---

### Post by coffeecat on 2009-07-29
This "Howto: Fix Windows share browsing issues" may be helpful:

[http://ubuntuforums.org/showthread.php?t=1169149](http://ubuntuforums.org/showthread.php?t=1169149)

Check all the points - it helped me.

---

### Post by superprash2003 on 2009-07-29
have you tried accessing via ip? like smb://x.x.x.x

---

### Post by Gem01 on 2009-07-29
Put that in in terminal and got "no such file or directory"

However further to my previous report, I have since added another PC running the same version of XP, and have no problems connecting to that one. (_All_ PC's currently wireless)
I am now convinced that it is a problem on that particular windows installation, and nothing to do with ubuntu.

Gem01

---

### Post by coffeecat on 2009-07-29
> **Gem01 said:**
> Put that in in terminal and got "no such file or directory"

The terminal is the wrong place for an address like "smb://192.168.x.y"

Open a Nautilus window, click the little icon that looks like a notepad with a pencil to change the breadcrumb trail location bar into a text address bar, and type the smb address in. Or you can do "smb://192.168.x.y/sharename/" and you should get prompted for the password, if necessary.

The other way is, in a Nautilus Windows, File > Connect to Server. Or, for the same effect, Places Menu > Connect to Server.

---

### Post by Gem01 on 2009-08-04
> **coffeecat said:**
> The terminal is the wrong place for an address like "smb://192.168.x.y"
 
Open a Nautilus window, click the little icon that looks like a notepad with a pencil to change the breadcrumb trail location bar into a text address bar, and type the smb address in. Or you can do "smb://192.168.x.y/sharename/" and you should get prompted for the password, if necessary.
 
The other way is, in a Nautilus Windows, File > Connect to Server. Or, for the same effect, Places Menu > Connect to Server.
 
Do not know the site too well so don't know if this will be flagged to you or not, cheers for the help,Gem01

---

