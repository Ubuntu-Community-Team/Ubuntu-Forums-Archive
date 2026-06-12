---
title: "Accessing multiple Samba shares with one login"
date: 2010-04-18
forum: Networking &amp; Wireless
---

### Post by Twizzle on 2010-04-18
I am sure that this is a simple one, but I can't for the life of me figure out how to do it...

I have a home server running Ubuntu 9.10 with Samba installed.

I use a MacBookPro running OSX to access the shared Samba drive and it works just fine.

I have just added a new user to the folder so I have a new /home folder and would like to be able to access this from OSX. If I open my server connection in OSX, I can see both home folders but I can only write to on - the first one. OSX is logging into Samba as the user who can access the drive so it is as I would expect, but I need to be able to write to both at the same time, without logging in and out all the time.

Is it possible to set samba so I can access and write to both shares at once?

---

### Post by Iowan on 2010-04-18
If I'm understanding, you want to view the /home folders of two different users? I suspect a permissions (ownership) problem. You *might* be able to add one user to the other's group.

---

### Post by Twizzle on 2010-04-18
Yes. Basically I have two users on the server:

john and xbmc, which have home directories at /home/john and /home/xbmc

OSX automounts the /home/john as 'server' through a Samba mount and automatically logs in as 'john' with the correct password.

I have set Samba to also share /home/xbmc and can see both 'share' and 'xbmc' under the network, but I can't write to xbmc. I assume that is because I am logged in as 'john' and not 'xbmc'.

I have tried to set the permissions of the share through Samba as 777 but no luck.

Should I change the actual directory on the server to 777 or can I create a symbolic link in some way into /home/john?

---

