---
title: "Mythbuntu 8.10 (0.23) to 10.04 (0.23/0.24) - any suggestions?"
date: 2010-06-13
forum: Mythbuntu
---

### Post by Calmor on 2010-06-13
I have a relatively well-behaved 8.10 x64 frontend/backend box performing multiple duties.  It's actually less a Myth box these days since the cable company did some upgrades to my cable box and now firewire support is sketchy at best.  In any event, I'm running 0.23 from JYAvenard's repos.

Unfortunately, support from both Ubuntu and JYAvenard are gone from this version, so I feel it's time to upgrade.  I'm not so concerned about new features and the like (I'm already running 0.23 with VDPAU anyway), but more about security for other services I am running on this box.

The upgrade path from 8.10 to 10.04 is ugly, so I plan to do a clean install.  Since 10.04 is also a 0.23 version, should I be able to back up my database and my media and do the clean install with minimal issue?  I plan to run a LiveCD first to make sure other hardware issues are not a problem.

Is it also possible, using the auto-builds, to run 10.04 with Myth 0.23 until 0.24 is stable, then move to 0.24?  I'm trying to avoid locking myself out of my media by having a backed-up 0.23 database and a 0.24 system, but at some point I'd like to step up when it's ready.

Thanks for your thoughts!

---

### Post by nickrout on 2010-06-14
> **Calmor said:**
> I have a relatively well-behaved 8.10 x64 frontend/backend box performing multiple duties.  It's actually less a Myth box these days since the cable company did some upgrades to my cable box and now firewire support is sketchy at best.  In any event, I'm running 0.23 from JYAvenard's repos.

Unfortunately, support from both Ubuntu and JYAvenard are gone from this version, so I feel it's time to upgrade.  I'm not so concerned about new features and the like (I'm already running 0.23 with VDPAU anyway), but more about security for other services I am running on this box.

The upgrade path from 8.10 to 10.04 is ugly, so I plan to do a clean install.  Since 10.04 is also a 0.23 version, should I be able to back up my database and my media and do the clean install with minimal issue?  I plan to run a LiveCD first to make sure other hardware issues are not a problem.

Is it also possible, using the auto-builds, to run 10.04 with Myth 0.23 until 0.24 is stable, then move to 0.24?  I'm trying to avoid locking myself out of my media by having a backed-up 0.23 database and a 0.24 system, but at some point I'd like to step up when it's ready.

Thanks for your thoughts!

I believe a fresh install is the way to go. But watch for things such as changed userid's and groupid's for your key users . Disk owner and group are stored as a number which translates to a username and groupname via /etc/passwd and /etc/group. You may need to chown some directories after a fresh install.

Yes mythtbuntu's autobuilds should enable a smooth transition to 0.24 when it is released.

Do back up your database of course. Instructions are [http://www.mythtv.org/wiki/Database_Backup_and_Restore](http://www.mythtv.org/wiki/Database_Backup_and_Restore) DO READ IT ALL!!

---

### Post by nickrout on 2010-06-14
Oh and you really don't want to change the hostname or IP address of your Box.

---

### Post by Calmor on 2010-06-14
> **nickrout said:**
> Oh and you really don't want to change the hostname or IP address of your Box.

Thanks for your suggestions.  I'll look over the user/group IDs, as that is something I hadn't thought of.  I'm not afraid to chown some things, and a lot of the files were originally copied from an NTFS partition so a lot of it needs gone through with proper user access anyway.  (root/root +777 for most of the media folders - I brought over a ton of stuff from Windows XP and BeyondTV)

As for the hostname and IP, I'll also take that into consideration, though I don't have any frontends other than the dedicated one.  I assume it would also bother all of the other services though.  The IP on that box, thankfully, is static (assiged directly by router according to its MAC address, which won't change) so less worry there.

---

