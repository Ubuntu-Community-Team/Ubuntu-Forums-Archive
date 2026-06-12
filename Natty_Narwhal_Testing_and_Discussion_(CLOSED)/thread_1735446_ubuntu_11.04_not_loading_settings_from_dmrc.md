---
title: "ubuntu 11.04 not loading settings from dmrc"
date: 2011-04-21
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by jahst on 2011-04-21
Hello,
Have a little problem here.

Ubuntu 11.04 with latest updates as of today.

I put Session=gnome into my users .dmrc file.
First time I logged out and logged back in, it loaded gnome.. great.

I changed it back to Session=ubuntu and it returned to the default unity...great

I tried Session=ubuntu-classic and it worked.. restoring 11.04 unity interface to the more traditional interface like previous ubuntu versions... still great.

However, I restarted my PC and cant for the life of me get it to work a second time.

No matter what I put in the drmc file it always and only loads unity.

What the heck?


What I'm trying to do is write a simple toggle script where users can click and switch between the unity and traditional gnome interface.

My users don't have a password, so they cannot click their user name and then change the session on the login screen.. clicking their user name automatically logs them in.

Old versions of ubuntu (8.04 maybe?) used to let users change the session once logged in, then logout and back in for it to take effect. This would work fine too.. except since at least 10.10 it seems the session change option is only on the login screen.

Is there a secret terminal command or gconf setting to show the session manager or change the session?

Thanks,

---

### Post by Mark Phelps on 2011-04-21
Ubuntu 11.04 is still in testing.  This thread is reserved for Ubuntu versions that have already been released.

You will get better and faster responses if you post your 11.04 questions to the Natty Development forum.  That is located at: Other Community Discussions --> Development & Programming --> Natty Narwhal Testing and Discussion

thanks

---

### Post by mc4man on 2011-04-21
At least here - 
Session=gnome will log in to unity
Session=gnome-classic will log into gnome-panel

Edit: and Session=gnome-2d is Classic(no effects)

---

### Post by jahst on 2011-04-26
thanks mc4man, using gnome and gnome-classic works.

Still strange that the first time i used gnome, it actually loaded gnome.. not ubuntu unity. Panel applets, icons, and folder colors all when to that greyish gnome look... must have been a fluke... I'm sure it wasnt my code.
:confused:

Kinda confusing that on the login screen it says "Ubuntu" and "Ubuntu Classic" when you need to type "gnome" or "gnome-classic" in the .dmrc file.

 Thanks again

---

