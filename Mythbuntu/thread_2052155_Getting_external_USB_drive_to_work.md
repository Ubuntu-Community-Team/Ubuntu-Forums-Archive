---
title: "Getting external USB drive to work"
date: 2012-09-02
forum: Mythbuntu
---

### Post by ceenvee703 on 2012-09-02
I'm getting very frustrated as this should work but it's not.

I'm trying to configure an external USB 2.0 drive as the target for recordings. I realize this might not be practical; I just want to know why what I'm doing is not working.

When the drive comes up, it mounts at /media/extrec/ . I've formatted to ext4

Newly-formatted, its user/group is myname:myname. I can copy and get directory listings fine from it. And supposedly myname is part of the mythtv group, as when I try to do "adduser" it says it's already part of the group.

So I then go into config the backend and I set /media/extrec/ as the directory for recordings and then try to exit. At this point one of three things happens: 1) nothing, 2) a complaint that it can't find /media/extrec/, 3) a complaint that it can't write to /media/extrec//.test .

Regardless of which of those three things happens, recordings do not work. Recording works fine if I set it back to the default /var/lib/mythtv/recordings/ in the boot internal drive.

So I think, it's got to be permissions. I sudo chown mythtv:mythtv -R /media/extrec/ as well as sudo chmod ug+rw -R /media/extrec/ If I ls -lah /media/extrec, all looks fine. However, even though myname is supposedly part of the mythtv group and r+w access is supposedly available, I can no longer even sudo cd /media/extrec. And recording still doesn't work.

I get a real headache and shoulder tension when stuff like this happens. What am I doing wrong? Again, I realize that an external USB drive might not be fast enough to record to. I just want to know what I'm doing wrong so I can't prove or disprove that myself.

Thanks.

---

### Post by Rotak on 2012-09-02
I do something similar when I export recordings (nuvexport) for archiving.

I ran into the problem, that the root of a mounted filesystem is not being writable by a !user!, if using an ext* filesystem.

Therefore, the easy workaround I made was to create a subdirectory where I could persistently set "777" rights to the directory itself.

Applying that to your issue would mean, that you create a new folder
/media/extrec/recordings
with 777 rights on the folder if the owner is root:root, or 770 if the folder is owned by the mythtv:mythtv, and you add the allowed users to the mythtv group.

Change your config in mythtv to write to /media/extrec/recordings, and you are fine.

EDIT:
I think the problem is, that the root of a mounted ext* file system has specific rights which you can NOT tweak by using chmod/chown on the directory you mount the filesystem to. I never tried if it makes a difference if you 'cd' into the mounted system (in your case /media/extrec) and execute something like "chmod 777 .". But I anyway don't think it's a good idea to write into the root of a mounted ext* filesystem. So I always add folders. :)

---

### Post by klc5555 on 2012-09-02
I've found USB2 external SATA drives perfectly simple to use and fast enough to record/play even HD. With HD I prefer just one stream going into the drive at a time. With SD and Analog it doesn't matter.

I mount external drives under /var/lib/mythtv/... where all the internal recordings drives are also mounted. With the same ownership and permissions. All my recordings drives, internal and external are formatted XFS, which I've used for this purpose since around 8.04. Seems to work fine even up to 3T drives. My recordings go into the root directories of all my internal and external recordings drives.

At boot I tend to mount the external recordings drives from rc.local rather than fstab, otherwise they handle exactly like any of my internal recordings drives, just not as fast with multiple streams.

---

### Post by ceenvee703 on 2012-09-03
Thanks very much for your suggestions. I ended up taking Rotak's path and setting mythtv permissions on a folder inside of /media/extrec/ . After doing that, and then having Ubuntu fix some kind of inconsistent permissions problem it had flagged, it's recording! I'm recording three HD programs to it now, didn't seem to play back too well while recording three, but that's not too surprising. Thanks again.

---

