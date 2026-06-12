---
title: "Symlinks suddenly don't work via Samba interface!"
date: 2010-04-11
forum: Mythbuntu
---

### Post by neutron68 on 2010-04-11
I've got a cron.hourly job set to create human-readable filenames and put them in a "Pretty" directory.  The cron job calls the script "/usr/share/doc/mythtv-backend/contrib/user_jobs/mythrename.pl" once per hour.

My cron script looks like this:
```
#!/bin/bash
/usr/share/doc/mythtv-backend/contrib/user_jobs/mythrename.pl --link /var/lib/mythtv/pretty --verbose --format "%T %- %Y-%m-%d, %g-%i %A %- %S"
```

I made the cron job executable with the command:
```
sudo chmod 755 /etc/cron.hourly/prettynames
```

In order for the mythrename.pl script to be allowed to run, I had to make it executable, also:
```
sudo chmod 755 /usr/share/doc/mythtv-backend/contrib/user_jobs/mythrename.pl
```

This all works fine and the /var/lib/mythtv/pretty directory is populated with nice, readable filenames.  
I have the "Pretty" directory set as a shared directory in SAMBA.  I regularly browse to this directory from my Windows computers over the SAMBA interface.  In this way, I am able to drag these symlinks onto the hard drives of Windows computers and I get the full video files, with human-readable filenames, etc.  

But, a few days ago (April 6), the symlinks in the "Pretty" directory stopped working.  When I try to drag these files to a Windows machine, I get an error box that says "Cannot copy file: Cannot read from source file or disk."  I also get a similar message from VLC Player when I double-click on one of these simlinks from a Windows comupter.  VLC Player says: ```
File reading failed:
VLC could not open the file "\\Mythbuntu8\pretty\Star Trek- Enterprise - Anomaly - 2010-04-09, 10-59 AM.mpg".
Your input can't be opened:
VLC is unable to open the MRL '\\Mythbuntu8\pretty\Star Trek- Enterprise - Anomaly - 2010-04-09, 10-59 AM.mpg'. Check the log for details.
```

Is this happening to any one else?  Any idea how I fix the symlinks?

Eric

---

### Post by Neon Dusk on 2010-04-11
I think you need to add
```

follow symlinks = yes
wide links = yes
unix extensions = no

```
to the [global] section of your /etc/samba/smb.conf

Note that this is potential security risk 

See
[http://www.samba.org/samba/news/symlink_attack.html](http://www.samba.org/samba/news/symlink_attack.html)

And other threads here - [thread=1439092]1[/thread] [thread=1448613]2[/thread]

---

### Post by neutron68 on 2010-04-11
> **Neon Dusk said:**
> I think you need to add
```

follow symlinks = yes
wide links = yes
unix extensions = no

```
to the [global] section of your /etc/samba/smb.conf

Thanks for the idea.  I can try adding those lines.

The part that confuses me is that the Mythbuntu machine has been working fine the way it is since 9.10 was released in fall of 2009 - months.  Then, something changed around April 6.

I am subscribed to the Mythbuntu 0.22 repo updates.
I wonder if one of the Mythbuntu repo updates changed something on me?  
I wonder if someone else on the forum has experienced this change too?

Eric

---

### Post by neutron68 on 2010-04-11
> **Neon Dusk said:**
> I think you need to add
```

follow symlinks = yes
wide links = yes
unix extensions = no

```
to the [global] section of your /etc/samba/smb.conf

It worked!  Thank you!

Suppose it was the updates that changed the settings so they would not work?

Eric

---

### Post by tgm4883 on 2010-04-11
It wasn't the auto-builds as that is only mythtv updates. Likely it was a security update

---

### Post by neutron68 on 2010-04-11
> **tgm4883 said:**
> It wasn't the auto-builds as that is only mythtv updates. Likely it was a security update
Sounds plausible.  Does the Update Manager have a log?

Thanks,
Eric

---

### Post by ian dobson on 2010-04-11
Hi,

A samba update (from security) about 2 weeks ago changed something in samba, so that when it found symbolic links in a share it shutdown.

Regards
Ian Dobson

---

