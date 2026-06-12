---
title: "Windows Share: Password dialog keeps popping up again repeatedly"
date: 2010-09-09
forum: Networking &amp; Wireless
---

### Post by nexus0123 on 2010-09-09
I'm running 10.04 at school where they have this central file server we can connect to to store our files on.

I've been trying to use the "Places" menu > "Connect to Server" GUI to mount this network drive. I enter the info (below) and click "Connect", and a password dialog box pops up asking for the password (with 3 options for remembering the password), but after I type it in, a new password dialog box pops up and asks for it again. This happens repeatedly and new boxes keep popping up.


Information entered:

Service type: Windows Share
Server: file.server-name.edu
Share: <myname>
Folder: <blank>
Username: <myname>
Domain Name: <mydomain>

as provided by my school. (My friend who also uses Ubuntu enters the same thing and he is able to connect without a hitch.)

Any ideas?

---

### Post by nexus0123 on 2010-09-13
Anyone? Any suggestions would be greatly appreciated.. =]

---

### Post by MasterGamerJK on 2010-11-20
I have this same problem on 10.10, no clue why its doing this.

---

### Post by sathgarcia on 2010-11-26
me as well.  previously mine was working pretty smoothly and then one day i couldn't view the shared files on a w7.

both 8.04, 9.04 & 10.04 ubuntu box have the same problem connecting to windows share in w7.

connect to server
=================================
service type: windows share
server: 192.168.x.x
share: <share folder for user>
user name: <user - present in w7>

* this was working previously but not anymore . . .

anything will be appreciated. thank you.

---

### Post by gholm on 2010-12-01
Same here.
I am in 10.10, trying to connect to a password-protected share folder on a Win7 box, and although I am typing in all the correct username, password and domain (even though we are not on a domain, we're on a WORKGROUP), the dialogue box keeps popping up without connecting.

What's a work-around? We don't run a domain here, just a workgroup.
I definitely need to get this resolved asap.

---

### Post by gholm on 2010-12-01
OK, dug around a bit more...and discovered that the Windows 7 box has software called Windows Live Assistant.

You need to delete/uninstall the entire Windows Live Essentials software.
(Yes, this will disable all those features on Win7)

Then you will be able to get past this "bug", and Ubuntu will log onto a shared folder on Win7 as you'd expect it should.

---

### Post by engineerbob on 2010-12-20
Thank you very much for the tip about Windows Live Essentials. I only had Movie Maker Live installed. I didn't think it was a problem since Live Messenger was not installed. But after tearing my hair out and trying dozens of "fixes", your tip about Live Essentials did the trick. 

The bottom line - If you are unable to get past the password prompt then check to see if any element of Live Essentials is installed. Remove it and your problem will most likely disappear.

Now I am going to buy some Rogain to replace my lost hair. :-)

---

### Post by keypox on 2011-01-04
> **engineerbob said:**
> Thank you very much for the tip about Windows Live Essentials. I only had Movie Maker Live installed. I didn't think it was a problem since Live Messenger was not installed. But after tearing my hair out and trying dozens of "fixes", your tip about Live Essentials did the trick. 

The bottom line - If you are unable to get past the password prompt then check to see if any element of Live Essentials is installed. Remove it and your problem will most likely disappear.

Now I am going to buy some Rogain to replace my lost hair. :-)

aww that sucks i use photo gallery, and mail. Like them both alot no other fix?

---

### Post by PatchesTheCaveman on 2011-01-05
There's an adjustment you can make to your smb.conf file that also fixes this issue:
 [http://ubuntuforums.org/showthread.php?t=1655434&highlight=windows+live+essentials](http://ubuntuforums.org/showthread.php?t=1655434&highlight=windows+live+essentials)

---

