---
title: "Mythbuntu reports mythtv-backend both is and isn't running (hanging lock?)"
date: 2007-10-01
forum: Multimedia &amp; Video
---

### Post by Yoooder on 2007-10-01
I've got a fresh install of Gutsy Beta 1.  After the base install and all gutsy updates are in place I install mythbuntu-control-centre.

With the Mythbuntu Control Centre I configure my machine to be a:
 - Primary Backend
 - Frontend
 - Ubuntu Desktop

I go through mythtv-setup, entering it through mythbuntu control centre, and setup my tuners and my input connections, scan for channels, and let it do a mythfillbackend on exit.

After everything is setup I fire up mythtv-frontend, only to be told the backend doesn't appear to be running.  If I do a "/etc/init.d/mythtv-backend start" it tells me it is already running.  Issuing a restart command yields the same results, as does a reboot.

I had mythbuntu working successfully of a Tribe 5 install on another machine, however following the above process on my machine on both a Tribe 5 and Beta 1 install has resulted in what I'm describing.

Are the repo's for mythbuntu broken for fresh installs?  Is there a lingering lock that I need to clear for the backend to start?  Am I doing anything wrong or out of order?

Thanks much!

---

### Post by superm1 on 2007-10-01
> **Yoooder said:**
> I've got a fresh install of Gutsy Beta 1.  After the base install and all gutsy updates are in place I install mythbuntu-control-centre.

With the Mythbuntu Control Centre I configure my machine to be a:
 - Primary Backend
 - Frontend
 - Ubuntu Desktop

I go through mythtv-setup, entering it through mythbuntu control centre, and setup my tuners and my input connections, scan for channels, and let it do a mythfillbackend on exit.

After everything is setup I fire up mythtv-frontend, only to be told the backend doesn't appear to be running.  If I do a "/etc/init.d/mythtv-backend start" it tells me it is already running.  Issuing a restart command yields the same results, as does a reboot.

I had mythbuntu working successfully of a Tribe 5 install on another machine, however following the above process on my machine on both a Tribe 5 and Beta 1 install has resulted in what I'm describing.

Are the repo's for mythbuntu broken for fresh installs?  Is there a lingering lock that I need to clear for the backend to start?  Am I doing anything wrong or out of order?

Thanks much!
Can you check /var/log/mythtv/mythbackend.log  See if there is anything out of the ordinary being listed there.

---

### Post by Yoooder on 2007-10-01
will do, I'll have to wait until after work (forgot to setup my ssh server on the fresh install)

---

### Post by superm1 on 2007-10-01
> **Yoooder said:**
> will do, I'll have to wait until after work (forgot to setup my ssh server on the fresh install)
You know ssh is on the services tab of m-c-c right :) ?

---

### Post by obscure411 on 2007-10-01
I'm having the same problem on a clean Mythbuntu Alpha 4 install.

mythbackend.log states:

2007-10-01 18:28:24.482 Using runtime prefix = /usr
2007-10-01 18:28:24.615 New DB connection, total: 1
2007-10-01 18:28:24.670 Connected to database 'mythconverg' at host: localhost
2007-10-01 18:28:24.694 Current Schema Version: 1160
Starting up as the master server.
2007-10-01 18:28:24.736 New DB connection, total: 2
2007-10-01 18:28:24.898 Connected to database 'mythconverg' at host: localhost
2007-10-01 18:28:24.925 EITHelper: localtime offset -4:00:00 
2007-10-01 18:28:25.118 TVRec(1) Error: Start channel from DB is empty, setting to '1' instead.
2007-10-01 18:28:25.283 New DB connection, total: 3
2007-10-01 18:28:25.297 Connected to database 'mythconverg' at host: localhost
2007-10-01 18:28:25.603 Channel::GetCurrentChannelNum(1): Failed to find Channel '1'
2007-10-01 18:28:25.612 Channel(/dev/video0)::TuneTo(1): Error, failed to find channel.
2007-10-01 18:28:25.614 Channel::GetCurrentChannelNum(1): Failed to find Channel '1'
2007-10-01 18:28:25.614 Channel(/dev/video0)::TuneTo(1): Error, failed to find channel.
2007-10-01 18:28:25.615 TVRec(1) Error: Setting start channel '1' failed, 
			and backup '1' failed as well.
2007-10-01 18:28:25.620 New DB scheduler connection
2007-10-01 18:28:25.621 Connected to database 'mythconverg' at host: localhost
2007-10-01 18:28:27.054 Main::Registering HttpStatus Extension
2007-10-01 18:28:27.170 mythbackend version: 0.20.20070821-1 [www.mythtv.org](www.mythtv.org)
2007-10-01 18:28:27.175 Enabled verbose msgs:  important general
/mythtv/recordings/nfslockfile.lock: No such file or directory
Unable to open lockfile!
Be sure that '/mythtv/recordings' exists and that both 
the directory and that file are writeable by this user.

/mythtv/recordings does exist, BTW, and has mythtv as both user and group owner.

---

### Post by superm1 on 2007-10-01
> **obscure411 said:**
> 
/mythtv/recordings/nfslockfile.lock: No such file or directory
Unable to open lockfile!
Be sure that '/mythtv/recordings' exists and that both 
the directory and that file are writeable by this user.

Clearly this is where your issue at hand is.  The backend won't start unless it can write files.

> 
/mythtv/recordings does exist, BTW, and has mythtv as both user and group owner.
Can you check the permissions (rwx) then?

```
ls -alhR /mythtv
```
will do

---

### Post by obscure411 on 2007-10-01
Fixed my own problem, I'm just a bit slow :)

Sorry for hijacking the thread - turns out during reinstall I had changed the username to something other than mythtv... DOH!

Mental note: check the obvious before posting on ubuntuforums ... hehe

---

### Post by Yoooder on 2007-10-02
> **superm1 said:**
> Can you check /var/log/mythtv/mythbackend.log  See if there is anything out of the ordinary being listed there.

Hey, I poked through the log file and figured it out.  It was permissions related, similar to obscure.

My myth-recordings drive doesn't get wiped when I format my machine, so when I remounted it all its permissions were a bit off (didn't correlate with my new /etc/passwd or something).

Out of curiousity, I've got a dump of my old (from last installation) database, as well as all the movie files.  Is there an easy way to reimport these to Myth--even though the database version is from an older version of myth?

Thanks much

---

### Post by superm1 on 2007-10-02
> **Yoooder said:**
> Hey, I poked through the log file and figured it out.  It was permissions related, similar to obscure.

My myth-recordings drive doesn't get wiped when I format my machine, so when I remounted it all its permissions were a bit off (didn't correlate with my new /etc/passwd or something).

Out of curiousity, I've got a dump of my old (from last installation) database, as well as all the movie files.  Is there an easy way to reimport these to Myth--even though the database version is from an older version of myth?

Thanks much
Backup the current db on the new setup.  Then drop the db, and you should be able to import the old one directly back in.  Things will upgrade the first time you start myth automagically.  If they don't, you've got a backup ready :)

---

### Post by obscure411 on 2007-10-02
Yoooder,

This link explains how to import an old mythtv db, I just did it myself :)

[http://www.mythtv.org/docs/mythtv-HOWTO.html#toc23.7](http://www.mythtv.org/docs/mythtv-HOWTO.html#toc23.7)

---

