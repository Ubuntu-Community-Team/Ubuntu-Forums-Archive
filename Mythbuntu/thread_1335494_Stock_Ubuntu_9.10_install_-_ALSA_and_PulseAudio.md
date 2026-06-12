---
title: "Stock Ubuntu 9.10 install - ALSA and PulseAudio"
date: 2009-11-23
forum: Mythbuntu
---

### Post by Dewey_Oxberger on 2009-11-23
I've only used mythbuntu - I've never done a stock install of 9.10.

If you do a 9.10 stock install, then add mythbuntu over it does the alsa audio stuff work?

I was thinking 9.10 defaults to pulse audio and alsa isn't there.

---

### Post by pootle1 on 2009-11-23
[LEFT]Yes a standard ubuntu build has alsa (and pulse), and I run both my front ends that way very successfully (although front end only) - I would recommend installing mysql-server before myth.

Also you prolly need to set up sql before running mythsetup:

```
create database mythconverg;
create user 'mythtv'@'localhost' identified by 'ynvUwe2U';
create user 'mythtv'@'192.%' identified by 'ynvUwe2U';
grant all privileges on mythconverg.* to 'mythtv'@'localhost';
grant all privileges on mythconverg.* to 'mythtv'@'192.%';

```(You only need lines 3 & 5 if your running a separate frontend)
[/LEFT]

---

### Post by superm1 on 2009-11-24
> **pootle1 said:**
> [LEFT]Yes a standard ubuntu build has alsa (and pulse), and I run both my front ends that way very successfully (although front end only) - I would recommend installing mysql-server before myth.

Also you prolly need to set up sql before running mythsetup:

```
create database mythconverg;
create user 'mythtv'@'localhost' identified by 'ynvUwe2U';
create user 'mythtv'@'192.%' identified by 'ynvUwe2U';
grant all privileges on mythconverg.* to 'mythtv'@'localhost';
grant all privileges on mythconverg.* to 'mythtv'@'192.%';

```(You only need lines 3 & 5 if your running a separate frontend)
[/LEFT]

This is curious.  I know past myth* packages on earlier Ubuntu releases weren't as resilient to problems with mysql interaction during initial setup.  Have you actually ran into issues on 9.10's packages too?  Could you please file a bug on the specifics of what your problems were?  We made some pretty significant changes under the curtains that should have made this more foolproof.

---

### Post by pootle1 on 2009-11-24
I'm not sure if this is right superm1, but I believe what i did was this:
If you think this should not need the sql messing about I'll try out a dummy build if I can to get the exact details.


[LIST=1]
[*]build PC with 9.10 server
[*]add xubuntu desktop
[*]bring up to date
[*]add mysql server
[*]add mythtv-backend only
[*]configure backend - scans etc
[*]build 1st front end PC
[*]find I can't access the sql database, so do the mysql fixes
[/LIST]
pootle

---

