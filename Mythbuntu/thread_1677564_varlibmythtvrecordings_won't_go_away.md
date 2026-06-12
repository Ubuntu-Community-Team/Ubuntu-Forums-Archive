---
title: "/var/lib/mythtv/recordings won't go away"
date: 2011-01-28
forum: Mythbuntu
---

### Post by uncle hammy on 2011-01-28
I have a master backend with 3 storage groups defined, /myth_storage1, /myth_storage2, /myth_storage3 (very original, as you can see).  I then have a secondary backend that has no tuners and is used simply to do commercial flagging and transcodes.  The secondary backend also has /myth_storage1, /myth_storage2, /myth_storage3 mounted via samba to the master backend in order to give them access to do their jobs.

When I go to Mythweb status page, or to INfo Center > Machine Status, it shows a 4th storage drive of /var/lib/mythtv/recordings on the secondary backend.  I understand this is the default recordings location, however I do have storage groups defined, and that isn&#8217;t one of them.  It&#8217;s also odd that it only shows up for the secondary backend.  I can remove the directory, and the drive is no longer listed (obviously), however the drive always get recreated with updates.

I posted this on the MythTV mailing list, and they indicated that /var/lib/mythtv/recordings was a Mythbuntu thing.  So, does anyone have any idea why this keeps popping up?

Thanks

---

### Post by azmyth on 2011-01-29
Guess you could symbolic link the recording directory to one of your storage groups. Maybe someone else will have a better answer though.

---

### Post by tgm4883 on 2011-01-29
check mythtv-setup on the secondary backend and see if it lists it as a storage directory

---

### Post by uncle hammy on 2011-01-29
> **tgm4883 said:**
> check mythtv-setup on the secondary backend and see if it lists it as a storage directory

There are no storage groups defined on the secondary backend.  They all show as "Create" X Group.  On the wiki, I read that groups should only be defined on the master backend, so I have defined nothing on the secondary.

---

### Post by tgm4883 on 2011-01-29
> **uncle hammy said:**
> There are no storage groups defined on the secondary backend.  They all show as "Create" X Group.  On the wiki, I read that groups should only be defined on the master backend, so I have defined nothing on the secondary.

Odd, you could look directly into your DB and see if it's defined in there as a storage group. If so you may be able to just delete that record.

---

### Post by uncle hammy on 2011-01-29
There is an entry in the db....

'1', 'Default', 'OLDHOSTNAME', '/var/lib/mythtv/recordings'

I deleted it (recreating it is easy enough), and the entry went away.

I always thought OLDHOSTNAME was the defaults.  So if you have a new host, it will grab OLDHOSTNAME to compile new settings for a new host.  Either way, OLDHOSTNAME is not the secondary server in question.

---

### Post by tgm4883 on 2011-01-29
> **uncle hammy said:**
> There is an entry in the db....

'1', 'Default', 'OLDHOSTNAME', '/var/lib/mythtv/recordings'

I deleted it (recreating it is easy enough), and the entry went away.

I always thought OLDHOSTNAME was the defaults.  So if you have a new host, it will grab OLDHOSTNAME to compile new settings for a new host.  Either way, OLDHOSTNAME is not the secondary server in question.

Odd, did you at any point move your backend to a new host and use the backup/restore scripts?

---

### Post by uncle hammy on 2011-01-29
The secondary backend is brand new as a backend.  However, it has been a frontend for a couple years and always had the same host name.  

The master backend has been in service since 0.19 and I changed it's host name once, but that was eons ago, and at that time, I ran a script I found that used grep and mysql to update every reference of the old host name to the new one.

I have done fresh installs numerous times and restored the db...though never with the backup/restore scripts to be honest.

My settings table has 300+ OLDHOSTNAME entries.  My jump points and key bindings table also have a whack of OLDHOSTNAME entries.  These are all "settings" type tables.  Am I correct that they are used to assign the default values to a new frontend or backend?

---

### Post by tgm4883 on 2011-01-29
> **uncle hammy said:**
> The secondary backend is brand new as a backend.  However, it has been a frontend for a couple years and always had the same host name.  

The master backend has been in service since 0.19 and I changed it's host name once, but that was eons ago, and at that time, I ran a script I found that used grep and mysql to update every reference of the old host name to the new one.

I have done fresh installs numerous times and restored the db...though never with the backup/restore scripts to be honest.

My settings table has 300+ OLDHOSTNAME entries.  My jump points and key bindings table also have a whack of OLDHOSTNAME entries.  These are all "settings" type tables.  Am I correct that they are used to assign the default values to a new frontend or backend?

They might be, honestly I'm unsure. I have the same in mine so possibly

---

