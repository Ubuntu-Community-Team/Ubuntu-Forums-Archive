---
title: "[SOLVED] Acting really strange"
date: 2007-10-27
forum: Mythbuntu
---

### Post by Meph1st0 on 2007-10-27
I think I might have gotten hacked.  When I came home from work my wife told me she couldn't watch TV today.  I tried and got the message saying that it couldn't connect to the "master-backend is the Ip address set correctly?" message.  I tried rebooting but when I clicked reboot it asked me for my password.  I typed it in and then I got another message saying that it was either incorrect or my account didn't have permissions to reboot this machine.  I then tried to reboot through and xterm and again it asked for my password.  I typed it in and it didn't work.  My password has apparently changed!  

I had setup my router to port forward SSH and VNC to my mythbox so that I could work on it from work.  (I know, I'm a slacker)  Someone could have easily gotten in through those ports.  I might just be paranoid but this is strange behavior.

Can anyone think of a way to help me regain control of my box?

---

### Post by Meph1st0 on 2007-10-27
Ok, I've determined that I can get a root # prompt still with su.  Is there a command prompt tool I can use to reset my user account password?  or can I hit Alt-F2 and type something to get the users & groups dialog as root?  I can't do gksudo because that would require my user account password which apparently has changed.

Also, are there any logs I can look at to see if anyone has connected to my box on port 22 or 5900?  

And finally, is there a way to reload mythbuntu without having to reformat my /var/lib LVM partition?  I'm assuming I'd have to backup my database (which I've never done before).

I still don't understand why my box would say that it can't connect to the backend database.  I was able to get into MythTV Backend setup and verify that the ip address is still 127.0.0.1.  This is a combined frontend/backend box.

I'm also getting an error rebooting stating that it failed to initialize HAL.  

This computer has lost it.

---

### Post by Meph1st0 on 2007-10-30
We can go ahead and set this post as solved.  It wasn't a problem to go ahead and format and reload.  I had just recently installed mythbuntu and thus there weren't any saved recordings or anything.  I've closed up the ports on my router and so no one "should" be able to get into my box for now.

---

