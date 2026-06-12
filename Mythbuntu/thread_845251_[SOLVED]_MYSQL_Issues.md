---
title: "[SOLVED] MYSQL Issues"
date: 2008-06-30
forum: Mythbuntu
---

### Post by Tteddo on 2008-06-30
Hello! I have a new install of Mythbuntu 8.04 and it seems that the passwords in MYSQL are being reset upon reboot. I found that the password I set it to during setup wasn't saved, so I went in in safe mode and reset the tteddo password and the root password to one that I know. I can connect from another computer using Navicat so I know it works. Upon reboot though, both are getting changed to a password I don't know. 
Also, in either case Mythfrontend will not connect. This is the 3rd time I have set up a MythTV box, so I know I have the IP Addresses set correctly, etc.
Anyone know why this is happening, or how I could find out what the passwords are being set to?

---

### Post by ian dobson on 2008-06-30
Hi,

Have a look in /etc/mythtv/mysql.txt file on your backend.

Regards
Ian Dobson

---

### Post by jrhaws on 2008-06-30
> **Tteddo said:**
> Hello! I have a new install of Mythbuntu 8.04 and it seems that the passwords in MYSQL are being reset upon reboot. I found that the password I set it to during setup wasn't saved, so I went in in safe mode and reset the tteddo password and the root password to one that I know. I can connect from another computer using Navicat so I know it works. Upon reboot though, both are getting changed to a password I don't know. 
Also, in either case Mythfrontend will not connect. This is the 3rd time I have set up a MythTV box, so I know I have the IP Addresses set correctly, etc.
Anyone know why this is happening, or how I could find out what the passwords are being set to?
I was having a very similar issue.  What I had to do was rebuild the tables.  I reset the mySQL root password, logged in, dropped the mythconverg table, created the table again, and next time mythtv-setup was run, it populated the tables with everything that it needed and things worked fine from there on out.

Make sure you setup the appropriate persmissions for the mythtv user once you have the table fixed.  You could continue and just use root as the mySQL login information, but of course that is a bad idea...

---

### Post by Tteddo on 2008-06-30
> **jrhaws said:**
> I was having a very similar issue.  What I had to do was rebuild the tables.  I reset the mySQL root password, logged in, dropped the mythconverg table, created the table again, and next time mythtv-setup was run, it populated the tables with everything that it needed and things worked fine from there on out.

Make sure you setup the appropriate persmissions for the mythtv user once you have the table fixed.  You could continue and just use root as the mySQL login information, but of course that is a bad idea...

What command exactly are you running to get it to populate the db again? mythtv-setup just runs the frontend setup that won't connect.
It did keep the right passwords after a reboot. I had to log in to mysql in the safe mode, change the password for root, logout, restart mysql in normal mode, then change the passwords for everyone, and it stuck now. But I still can't get the frontend to connect to the db.

---

### Post by Tteddo on 2008-07-01
Ok, here's what I did, I dropped the database, and restored from backup from a couple of weeks ago. I was going to do that anyway, but I thought ironing out the bugs first would be a good idea. That and playing with the mysql permissions to make my user wide open (there is only me here) got it to work.
 

I guess the custom install where you setup mysql and everything during the initial install didn't work in my case. The passwords were definitely not what I set for the mysql users during setup.

Oh well, now on to figure out why MythTV playback is crashing X :(

Thanks guys.

---

