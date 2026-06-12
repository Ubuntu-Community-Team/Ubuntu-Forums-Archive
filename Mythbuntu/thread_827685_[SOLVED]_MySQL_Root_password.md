---
title: "[SOLVED] MySQL Root password?"
date: 2008-06-13
forum: Mythbuntu
---

### Post by yonkiman on 2008-06-13
I'm installing Amarok, and apparently I'll see some database speed improvements if I use MySQL instead of the default SQLite.  Since Mythbuntu already has MySQL installed and running, this seems like it should be pretty straightforward.

The AMarok/MySQL instructions assume you're installing MySQL for the first time, so I skipped ahead to the steps following MySQL install and it says to create a root password for MySQL.  I assume Mythbuntu has already created a root password, but what is it?  The password for the mythconverg database doesn't work (as expected) and the password for my user account doesn't work (I had a tiny bit of hope that might be it).

Does anyone know what the default Mythbuntu MySQL root password is?

---

### Post by laga on 2008-06-13
The default password is empty. You can just log in using "mysql -u root". Of course, if you set a password during install then that's not going to work :)

---

### Post by dvbspider on 2008-06-13
I am at Mythbuntu Live Session configration.

I am reading the manual..

do I have to set my own password?

I hit Test connection  and FAILURE, can some one can walk me true this process in how to set up Database.

---

### Post by bmwman on 2008-06-13
Dude, I spent 4 days trying to get into the damn database. I reinstalled MythTV 20 times and still got the same problem. I was resetting permissions, changing passwords, IPs and still couldn't get it to work. Finally last night I installed Mythbuntu 8.04 and everything was preconfigured. What sucks about it is that I'm gonna be using the PC as my regular desktop and after upgrading to Ubuntu dekstop everything was messed up. I think Mythbuntu doesn't even use Gnome environment and I need to see how to fix that. Got the database problem fixed tho :)

---

### Post by dvbspider on 2008-06-13
I install same is there where I got the problem.

You think is possible u can help, me on this?

Yes i can see u have been working on this for long..

Thanks

---

### Post by bmwman on 2008-06-13
> **dvbspider said:**
> I install same is there where I got the problem.

You think is possible u can help, me on this?

Yes i can see u have been working on this for long..

Thanks

I think you should try the Mythbunu 8.04 a try. That's what I did. It was preconfigured (as far as the software part). I just installed last night so I'm gonna mess with my TV tuner tonight. BTW I just bought Hauppauge WinTV-HVR 1800 yesterday, after checking that it's fully supported on the linuxtv.org. Now I see people are having issues with so I hope I didn't make a bad choice.

---

### Post by laga on 2008-06-13
dvbspider,

are you trying to watch TV in the live environment? You'll need a working backend somewhere on your network. 

Maybe you could explain better what you're trying to do.

---

### Post by yonkiman on 2008-06-14
> **laga said:**
> The default password is empty. You can just log in using "mysql -u root". Of course, if you set a password during install then that's not going to work :)

I didn't think to try nothing - that did it!  Thanks!

---

