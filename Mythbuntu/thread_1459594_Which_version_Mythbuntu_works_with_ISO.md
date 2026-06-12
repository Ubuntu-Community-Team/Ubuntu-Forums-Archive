---
title: "Which version Mythbuntu works with ISO?"
date: 2010-04-21
forum: Mythbuntu
---

### Post by purduephotog on 2010-04-21
I've been unable to play ISO videos ripped that previously worked in version 8.

I'd like to upgrade, but I want to avoid storage groups as it appears that that is causing most of my problems.

Therefore, can someone point me to the version I should install (and possibly what 'upgrade' command I should issue) to avoid storage groups yet still be able to play my previously ripped ISOs?

Thanks much-

(This is a standalone front/back myth machine).

---

### Post by williammanda on 2010-04-21
9.10 was when storage groups was introduced and you should be able to play ISO with storage groups disabled. To disable, go into the backend setup and remove the video storage group.

---

### Post by purduephotog on 2010-04-21
> **williammanda said:**
> 9.10 was when storage groups was introduced and you should be able to play ISO with storage groups disabled. To disable, go into the backend setup and remove the video storage group.

I do apologize for being dense, but if I have the following media mounted in /media

/media/hd1
/media/hd2
/media/hd3

in the storage group setting, I have 
/var/lib/mythtv/recordings


And that's it. 

I don't have any capture cards- I just use this for DVD playback.

Is this what you mean?  Delete the information in the storage group setting?

---

### Post by williammanda on 2010-04-22
Read this and try what is explained.

[http://www.mythtv.org/wiki/MythVideo]("http://www.mythtv.org/wiki/MythVideo")

If this does not work for you then use version 9.04.

---

### Post by purduephotog on 2010-04-25
> **williammanda said:**
> Read this and try what is explained.

[http://www.mythtv.org/wiki/MythVideo]("http://www.mythtv.org/wiki/MythVideo")

If this does not work for you then use version 9.04.

Thanks.

I believe I have uncovered a bug, or at least a feature that isn't working in a logical manner.  I'll post that in a new note to be properly beaten.

I appreciate your help.  I had followed all the steps mentioned and nothing was working properly (driving me up the wall and fits of irritation).

The solution was- checking permissions.  I have the old install of mythbuntu sitting on another HD.  I have several 'data' drives in that system.  I pulled one, attached it to the new system, and then proceeded to fill up the new system drive (a WD20EARS) with 3x copies so I could then verify if there were any read errors.

I failed to change permissions. While I did get group rw access, I didn't change them (or they were reset) back to root:root.

The system would build a file list, but when I'd go try to play it I'd get kicked back to the main screen.  No errors or warnings, except to the log (which I eventually found) stating possible permission errors.  Bad form- but that wasn't the ultimate problem (I think).

Unfortunately nothing would still play on the new drive, even when I adjusted permissions and ownership to mythtv.

Remember I said I had two drives?  Well the one drive was still set to the old system's permissions (which is fine) since I hadn't intended on modifying it- I wanted it Read Only.  Once it's letters started earlier (anotherolddrive01) as opposed to the new drive (wd2tb01).  When I changed the original drive to mythtv:mythtv, everything started working.

Basically I have 4 copies of every movie on the system right now.

I think something somewhere is getting confused because of the duplicate files.

Anyways, I'll type this into a new note, clean it up, and see if I can make it repeatable enough to induce it as a bug.

Thanks again-

Jason

---

