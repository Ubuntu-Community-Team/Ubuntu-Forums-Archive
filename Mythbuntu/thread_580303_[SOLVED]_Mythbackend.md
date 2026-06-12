---
title: "[SOLVED] Mythbackend"
date: 2007-10-18
forum: Mythbuntu
---

### Post by besmith2@hotmail.com on 2007-10-18
Ok I installed this thing about 10 times with no luck yet. I have a backend setup with a PVR-150 and a PVR-350 on a Sony Viao RS 2.4Ghz         hyperthreaded with no problems with the hardware so far. 

What steps must I complete manually to connect a mythbuntu front end to my backend?
:confused:
I installed the backend only and enabled the MySql service.

MythWeb works fine which is kewl as I already scheduled stuff to record. :D

I am a linux newbie with multiple years experience trying to convert over to the rite-side (Dark-side/Lite-side)(windows/mac) and everytime I get frustrated and stop.

Thanks in advance.

---

### Post by besmith2@hotmail.com on 2007-10-18
I am referring extra steps on the back end, I can't even connect to the database remotely yet.

---

### Post by besmith2@hotmail.com on 2007-10-20
Anyone??

---

### Post by tgm4883 on 2007-10-20
is the Backend and Frontend on the same machine?

You need to set the frontend to connect via the actual ip address, not 127.0.0.1

---

### Post by besmith2@hotmail.com on 2007-10-21
The backend is on a different machine. I tried that. I can't even connect to the database on the backend server. I get:

Access denied for user 'mythtv'@144.10.10.143'(using password: NO) I did not set a password to try and make things as simple as possible.

---

### Post by superm1 on 2007-10-21
There was a bug in the RC installation that the mysql service may not have been activated in a few instances.

Can you open up mythbuntu control centre on it, and make sure the mysql service is activated there?

---

### Post by besmith2@hotmail.com on 2007-10-21
It was not activated however I activated it and rebooted with no luck.

---

### Post by superm1 on 2007-10-21
> **besmith2@hotmail.com said:**
> It was not activated however I activated it and rebooted with no luck.
After doing this, did you make sure that your ip addresses were all set to the non 127.0.0.1 ip?

---

### Post by besmith2@hotmail.com on 2007-10-21
On the backend I ran the Myth backend setup again and changed the two spots where it said 127.0.0.1 to 144.10.10.10 <-- backend ip

BTW
Thanks for the help.

---

### Post by besmith2@hotmail.com on 2007-10-21
Just an FYI I can connect through VNC.

---

### Post by superm1 on 2007-10-21
From your other machine (the FE machine), can you open up MCC and see if the connection test on the "MythTV configuration" tab works?

---

### Post by besmith2@hotmail.com on 2007-10-21
It fails <Red> Failure.
MYSQL MythTV User: mythtv
MYSQL MythTV Passowrd: empty
MYSQL MythTV Database: mythconverg
MYSQL Server: 144.10.10.10

I'm sorry I didn't clarify this more.

---

### Post by superm1 on 2007-10-21
Unless you completely got rid of your mysql password, you need to be filling in that box.  Get this information from /etc/mythtv/mysql.txt on your backend machine.

---

### Post by besmith2@hotmail.com on 2007-10-21
I never created one on install.

---

### Post by superm1 on 2007-10-21
> **besmith2@hotmail.com said:**
> I never created one on install.
Right.  One was created for you on the backend.  It's in that file.

---

### Post by besmith2@hotmail.com on 2007-10-21
oh geesh, thanks I will look there

Sorry for the noob mistake.

---

### Post by besmith2@hotmail.com on 2007-10-22
That was it, I guess I missed that in the install docs.

---

