---
title: "Adding a Secondary Backend"
date: 2011-01-19
forum: Mythbuntu
---

### Post by uncle hammy on 2011-01-19
I just converted on of my seldom used frontends (that also happens to have a fair amount of juice under the hood) to a Secondary Backend / Frontend.  I am not going to be doing any recording on this backend, I only want to use it to perform commerical flag and transcode jobs on stuff recorded on the backend.  

I have read through [http://www.mythtv.org/wiki/Storage_Groups#Setting_up_Storage_Groupsand](http://www.mythtv.org/wiki/Storage_Groups#Setting_up_Storage_Groupsand) I still have some confusion, because the wiki indicates samba or nfs should not be required.

I currently have 2 drives in the master backend, and entries in the master backend's default storage group for them...
/myth_storage1/recordings
/myth_storage2/recordings
/myth_storage3/recordings

All three of these directories are shared.  On my new secondary backend, in fstab I mount those shares to the same path locally. So /myth_storage1/recordings on the secondary backend is the recordings directory on the master backend.

Then, I have setup the master backend to allow commerical flag jobs only (max 2) and the secondary backend to allow commercial flag and transcode jobs (max 4).  The secondary backend has no cards, sources, etc defined.

Now (if you got through that long winded background), because the wiki indicates that nfs/samba aren't needed, I didn't do the mounts on the secondary backend at first.  However, my transcode tests failed immediately...because the secondary backend couldn't access the files (I assume).  As soon as I shared out the storage on the master and mounted them on the secondary (making sure to use the same absolute paths), I was golden.

Am I missing something?  Is there a better way to do this?

Thanks

---

### Post by nickrout on 2011-01-19
You do need the mounts.

---

### Post by uncle hammy on 2011-01-20
Thanks, I thought I was missing a piece of the puzzle.  However, this morning I woke up to nasty surprise.  

in my master backend, I have 3 drives....

1TB drive mounted to myth_storage1 (has recordings, livetv folders)
500GB drive mounted to myth_storage2 (has recordings folder)
1TB drive, 400GB partition mounted to myth_storage3 (has recordings folder)

I have all 3 shared at the mountpoint with samba, and mounted on my new secondary backend at the same absolute path (as I indicated earlier).

This morning, all 3 mythtv drives (nothing else, including the second partition on that 1TB myth_storage3 drive) were completely emptied.  I mean empty too, not just recording files, but the recordings and livetv folders as well.  As empty as if someone had formatted the partitions.  I am currently in the process of restoring back all my recordings (except for the 3 from last night) back to the drives.

I don't think it's an auto archive thing because why would auto archive delete the recordings and livetv folders?  I don't think it's bad drives, because it would seem the odds seem almost astronomical that 3 would drives go bad the same night, and ONLY the myth drives, and ONLY the myth partition on the 1TB drive.

So now, I am left wondering if something with my samba share / mounts on the secondary backend caused it.  That thought seems to be the most likely, given the gigantic coincidence here, but I can't fathom what would have done it.  It's almost like something with this setup cause the folders at the mount points to be deleted, taking the recordings with them.

I am somewhat terrified to turn that backend back on again right now.

---

### Post by uncle hammy on 2011-01-20
seem to have triple posted somehow....

---

### Post by uncle hammy on 2011-01-20
After my last recording of last night, my log started filling up with....

2011-01-20 00:30:02.447 adding: myth-backend as a client (events: 0)
2011-01-20 00:37:20.641 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2011-01-20 00:40:02.070 MainServer::ANN Monitor

and 

2011-01-20 06:51:08.774 Slave backend: myth-mainpc no longer connected
2011-01-20 06:51:08.774 PlaybackSock::SendReceiveStringList(): No response.
2011-01-20 06:51:08.774 AutoExpire: ERROR: Filesystem Info cache is empty, unable to calculate necessary parameters.
2011-01-20 06:51:08.776 mythbackend: Last message repeated 131 times: Running housekeeping thread
2011-01-20 06:51:08.778 mythbackend: Autoexpire CalcParams: ERROR: Filesystem Info cache is empty, unable to calculate necessary parameters.
2011-01-20 06:51:09.799 adding: myth-mainpc as a slave backend server

So maybe it is related to my current storage group / samba setup and autoexpire?

It's also weird, because when I had both the master and secondary backends running, when I went to modify storage groups in the master backend I got a "Error: cannot create test file" message on all my groups.  When the secondary backend was powered off, not such message,

---

### Post by uncle hammy on 2011-01-20
seem to have triple posted somehow....

---

### Post by uncle hammy on 2011-01-20
seem to have triple posted somehow....

---

### Post by uncle hammy on 2011-01-20
Well, I figured out the mystery delete (kind of).  I copied my tar backup script from my master backend to the secondary backend and change the paths as required (or so I thought).  The last line of my script uses find to get the 7 most current backups and rm -rf the rest.  I forgot to change the path in the find command to be appropriate for the secondary backend, and it deleted /...including the samba mounted myth storage directories. :(

The kind of part is, I can' quite get my head around how find /media_storage/system_backups/myth-backend -maxdepth 1 -type f | xargs -x ls -t | awk 'NR>7' | xargs -L1 rm -rf ended up deleting /.  /media_storage/system_backups/myth-backend doesn't exist on the secondary backend, so shouldn't it have found nothing?

---

