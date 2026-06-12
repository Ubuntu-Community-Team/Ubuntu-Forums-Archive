---
title: "Trouble with home networking"
date: 2009-06-17
forum: Networking &amp; Wireless
---

### Post by noosaj on 2009-06-17
Hi,
I apologize if this has been posted before, but I am unable to find a solution to my particular problem.

I have a Linux machine with Ubuntu 9.04 Jaunty installed.  My wife has a Windows machine with Vista SP2 installed.  The machines are connected together in a LAN setup.  I'm trying to get Ubuntu to find and read/write to the Windows machine and vice versa.  I've installed Samba, but no luck.  I tried opening windows shares (my wife's computer's shared folders) via Connect to Network... menu option and by opening the Network folder.  Doesn't work.  When opening the Network folder, I get a Windows Network icon and double-click that.  Then I see the WORKGROUP icon, and when trying to open that, it says failed to retrieve share list from server.

I am at a loss as to what to do.  We have one printer which is hooked up to my Ubuntu machine, and we need to share that also.  I have set up a few folders for sharing on my machine as well as the Windows machine.  The printer is also shared.

Please help!

Jason

---

### Post by noosaj on 2009-06-17
Okay. Here's the latest update.  I've finally gotten Ubuntu to read/write Windows shares.  The problem is Vista - Vista can see my machine.  When trying to gain access, it requires a username/password - I've entered my logon credentials for the Ubuntu machine, but it says it's an invalid user/pass.  How do I gain access to my Ubuntu machine from the Windows machine?

Thanks.
Jason

---

### Post by Iowan on 2009-06-17
See if [this]("http://ubuntuforums.org/showthread.php?t=1169149") one helps.

---

### Post by swerdna on 2009-06-17
> **noosaj said:**
> Okay. Here's the latest update.  I've finally gotten Ubuntu to read/write Windows shares.  The problem is Vista - Vista can see my machine.  When trying to gain access, it requires a username/password - I've entered my logon credentials for the Ubuntu machine, but it says it's an invalid user/pass.  How do I gain access to my Ubuntu machine from the Windows machine?

Thanks.
Jason
Add a Linux user to the Samba user database. Then supply those credentials from vista. This command will add a user:```
sudo smbpasswd -a willywagtail
```and this command will delete a user:```
sudo smbpasswd -x willywagtail
```and this command will list the users:```
sudo pdbedit -L
```
willywagtail must be already a bona fide Ubuntu Linux username before you try to add her to the Samba database.

---

### Post by noosaj on 2009-06-17
Thank you so much!  Problem now solved!  Following your steps gained me access to my Ubuntu box from my Winbox.

Thanks again for everyone's help.

Jason

---

### Post by swerdna on 2009-06-17
> **noosaj said:**
> Thank you so much!  Problem now solved!  Following your steps gained me access to my Ubuntu box from my Winbox.

Thanks again for everyone's help.

Jason

You're welcome

---

