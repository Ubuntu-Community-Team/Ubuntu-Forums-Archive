---
title: "ubuntu 10.04 unable to access Window 7 PC"
date: 2010-07-18
forum: Networking &amp; Wireless
---

### Post by mludwig on 2010-07-18
I can see the workgroup of Windows Network from Ubuntu, but when i  put the username and password of Windows 7 from Ubuntu it doesn't get  any access to the shared folders. I don't know where the problem is for  not getting the username and password accepted or authorization.

I even tried turning off the password requirement in Windows 7, but no  luck.

My Documents are shared on Windows 7

Something must be missing cuz I can see the Windows 7 computer on Ubuntu  but the login fails all the time.

---

### Post by Bandworthy on 2010-07-18
exact same problem for me, I'm fairly certain its the win7 end since its doing the same to my other windows pc's.  During the win7 beta i got it working but a year later, I've forgotten what i did and just haven't gotten around to working on it. 

So eager to see if someone has the answer.. again, its probably win7's stupid new networking homegroup thing that doesnt like non win7 networks, a bit too IE browser standard like for my liking.

---

### Post by mludwig on 2010-07-18
Somebody from the forums has to know something about this.  Anyone out there able to help with this issue

---

### Post by Matt Harlan on 2010-07-18
> **mludwig said:**
> Somebody from the forums has to know something about this.  Anyone out there able to help with this issue

Please double check or complete the following actions for me:

Share out a specific folder and connect to that using your Ubuntu box?
Connect to admin C$ Share? (Going to have hack registry to do that)
Double check the IP?

If all else fails, flash drive time!

My guess is that Bandworthy is right, but I am not completly sure. I am still sitting on XP SP3. ;) Never really had any big networking problems with XP/Ubuntu.

Sincerely,
Matt Harlan

---

### Post by Bandworthy on 2010-07-20
you've got me wanting to solve this issue again, right now
my win7 can access my ubuntu installs it just wont work the other way anymore. (log in over and over), I've been unwilling to risk messing even this up since i'm VERY dependent on this working...

But fiddling with it again, I'm convinced its either the homegroup system of win7 or a firewall issue. I'm also suspecting its on the win7 side then anything else since my xp and ubuntu pc's are all happily chatting its just the win7 thats being one way.

---

### Post by robsablah on 2010-07-20
> **Bandworthy said:**
> you've got me wanting to solve this issue again, right now
my win7 can access my ubuntu installs it just wont work the other way anymore. (log in over and over), I've been unwilling to risk messing even this up since i'm VERY dependent on this working...

But fiddling with it again, I'm convinced its either the homegroup system of win7 or a firewall issue. I'm also suspecting its on the win7 side then anything else since my xp and ubuntu pc's are all happily chatting its just the win7 thats being one way.

definatly windows 7 there 

have you tried turning off most of the settings in the network and sharing centre? i wasn't even able to access win-win without disabling that...
[http://chestertam.com/simple-windows-7-file-sharing-step-by-step-procedure/]("http://chestertam.com/simple-windows-7-file-sharing-step-by-step-procedure/")

ensure you have home network set and not work
[http://www.computingunleashed.com/wp-content/uploads/2009/12/Home-Network-Selection-Windows-7.gif]("http://www.computingunleashed.com/wp-content/uploads/2009/12/Home-Network-Selection-Windows-7.gif")

that should do it

---

### Post by mludwig on 2010-07-20
Ok, i am back.  So i have now only 1 Windows 7 PC which is upstairs (wife doesnt want to change to ubuntu) and a laptop and a desktop with Ubuntu 10.04.  The desktop has all the printers connected to it.  I configured smb.conf and was successful in connecting to all printers from my Windows 7.  Finally.  Now filesharing....  I am on the Home Network, all security is basically turned off, file sharing available, the only thing i have not done was turning off the firewall.  I will do that later this morning and see if this works.  Since now my laptop is complelety configured, this will make life much easier on doing this.

---

### Post by mludwig on 2010-07-20
Hot dog, i figured out how to get access to my share folders on my windows 7.  I shared my entire storage drive on my windows 7.  Put it to everyone.  Then in Ubuntu i went to Places then Connect to server.  In here select Windows share.  In the Server put in the Windows 7 IP ADDRESS.  Now in the folder put in the name of the share.  In my case it was storage.  Hit connect.  It will ask you to put in user name(windows)domain name(my case MSHOME) and password(windows).  Viola.  Now on your desktop you will see the folder mounted and open for access.  WOOT WOOT

If this helps anyone AWESOME

---

