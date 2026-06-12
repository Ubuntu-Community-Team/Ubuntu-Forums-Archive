---
title: "Installing Shepherd in MBuntu 10.10"
date: 2010-11-23
forum: Mythbuntu
---

### Post by Epiphyte on 2010-11-23
Hi all,

I'm a newb and I'm trying to install Shepherd onto Mythbuntu V10.10.

Doesn't Mythbuntu log on as user '[FONT="Courier New"]mythtv[/FONT]'?

If so, how can I install Shepherd as user [FONT="Courier New"]mythtv[/FONT]?  I only seem to be able to log on as myself ( :-|).

I re-read the installation doco ( [http://svn.whuffy.com/wiki/Installation]("http://svn.whuffy.com/wiki/Installation") ) and it seems to indicate that shepherd doesn't care what user you are. However, that seems to contradict the behaviour of the installation.

I have tried to instal Shepherd, but it gives me "permission" errors and then fails. (I think this is because I have the wrong permissions or I am not the *right *user).

Can anyone help?

---

### Post by nickrout on 2010-11-23
> **Epiphyte said:**
> Hi all,

I'm a newb and I'm trying to install Shepherd onto Mythbuntu V10.10.

Doesn't Mythbuntu log on as user '[FONT="Courier New"]mythtv[/FONT]'?

If so, how can I install Shepherd as user [FONT="Courier New"]mythtv[/FONT]?  I only seem to be able to log on as myself ( :-|).

I re-read the installation doco ( [http://svn.whuffy.com/wiki/Installation]("http://svn.whuffy.com/wiki/Installation") ) and it seems to indicate that shepherd doesn't care what user you are. However, that seems to contradict the behaviour of the installation.

I have tried to instal Shepherd, but it gives me "permission" errors and then fails. (I think this is because I have the wrong permissions or I am not the *right *user).

Can anyone help?

mythfrontend runs as the user you set up druing installation. mythbackend runs as mythtv.

I just tried the instructions and got to the point where it said "Create configuration file and update MythTV? [yes,no (default=yes)] no" and I chickened out, not wanting to destroy my xmltv setup.

Where did it fail for you?

---

### Post by parsim on 2010-11-23
I'm a Shepherd dev. Please copy and paste the output including errors.

---

### Post by Epiphyte on 2010-11-24
Guys,

I found some inherent problems with V10.10 and reverted to V10.04. I will open a new thread with that title.

Apologies to all & thanks so far.

---

### Post by Epiphyte on 2011-01-04
Thanks to parsim. 

I had some help from Mark in Melbourne.

BTW. How well will Shepherd cope with new digital 11 and the FreeView EPG?

---

