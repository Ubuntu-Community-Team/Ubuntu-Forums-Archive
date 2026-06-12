---
title: "[SOLVED] Commercial flagging kills my disk."
date: 2008-12-01
forum: Mythbuntu
---

### Post by fatmonk on 2008-12-01
When I have commercial flagging enabled (all available methods) the process seems to kill my recordings partition.

While a single flagging job is running (limited to one job at a time in the config) my RAM usage runs at only 3-4% free - I don't know if this is significant, but am mentioningit in case.

After finding a single commercial break according to the system status job queue screen (programme actually has two or three), the flagging process seems to stop. At this point the disk partition that my recordinsg live on (xfs, 500GB, seperate disk to OS, 'whole-disk' partition) becomes unusable showing Input/output errors as per the logs [here]("http://mythbuntu.pastebin.com/f26222363").

The disk won't unmount and the only way to get it back online is to do a full power down reboot (a simple restart doesn't bring it back online).

xfs_repair seems to find no problems with the disk.

Is there a big in the commercial flagging processes that hangs and leaves the disk 'open' in a bad way?

I've had commercial falgging disabled for a week now and have not had the problem recurr at all in that time. With commercial flagging on the disk dies after every recording on a commercial channel (not non-commercial channels like the BBC).

My recordings are stored their own disk, formatted as xfs, mounted as /home/other_media/recordings and sym linked from /var/lib/mythtv/recordings. Permissions and directory ownership are the same as the original /var/lib/mythtv/recordings directory.

-FM



[I've started this as a new thread as my original post on this now seems not to be specific enough. I've included a pointer to this thread from my old thread on thsi subject to helps anyone else who runs into the problems and find a search dead-end]

---

### Post by ian dobson on 2008-12-01
Hi,

I've ran afew tests with different file systems (on the same harddisk) and although ext3 is not the quickest it was the one with least problems. When I tested xfs I could easly create corruption by just reading/writing a large about of data at the same time (cat /dev/urandom > /mnt/xfs/dump and cat /mnt/xfs/dump  > /dev/null running at the same time as a bonnie++ disk speed test) caused the file system to go offline within afew minutes.

If you search this forum / internet  you'll see lots of problems with xfs. I don't know if it's a ubuntu problem or not but I'm sticking with ext3.

Regards
Ian Dobson

---

### Post by superm1 on 2008-12-01
It probably wouldn't hurt to download Hitachi DFT, burn it to a CD and do the test with it.  It will take a couple of hours, but is usually pretty thorough about finding physical disk problems.

---

### Post by oldsoundguy on 2008-12-01
I use this one cross platform:

[http://www.ultimatebootcd.com/](http://www.ultimatebootcd.com/)

(most of the stuff there is Linux, but it will examine. test, and sometimes actually FIX any PC based system (useless on non Intel Macs.)

---

### Post by fatmonk on 2008-12-02
How easy is it under ubuntu to reformat a partition from xfs to ext3 without mucking up the fstab and mtab too much?

I can copy my content off to my system drive while I reformat (I have space at the moment), but I don't really want to have to reinstall so would like to leave my other drive and its partitions completely intact?

-FM

---

### Post by newlinux on 2008-12-03
Just another data point - most of my systems use XFS for recording storage partitions with commercial flagging and I haven't had any problems.  I've actually had intermittent speed problems with my one storage partition that is ext3. But then I used to run all my partitions on ext3 even for recordings and didn't have problems for a couple years... so maybe the real problem is my disk on the machine that is having problems...

---

### Post by novellahub on 2008-12-03
I use XFS on all my storage group directories.  Deleting of shows goes very fast. I have not seen any performance hits.  I can even record 4 HDTV recordings, watching a show, and commercial flagging running at the same.  Maybe it has to do with the drive itself?  My main recordings directory is on a Western Digital 1 TB GP drive. My second drive is a 120 GB Western Digital drive that hold the OS and it partitioned into a separate storage area.  The OS partition I left at ext3.

---

### Post by fatmonk on 2008-12-03
On my system the commercial flagging 'reliably' causes the disk to fail. I've also tread a few reports of the same thing happening on other people's systems (over at MythTVTalk).

Am considering a move to ext3 to see if it helps, but...

Can anyone explain what happens and in what order in the commercial flagging process?

? Is a second recording file created with the commercials flagged somewhere in the MPEG stream or is the commercial positioning data stored in th database?

? If a new recording file is screated, does this get created right from the start of the flagging process or only after the first commercial break is found? Or even after the detection process has completed?

-FM

---

### Post by newlinux on 2008-12-03
I'm pretty sure the commercial positioning information is stored in the DB.

---

### Post by anonymousdog on 2008-12-04
Commflagging points are definitely kept in the mythconverg db recordedmarkup table; see also, [http://www.mythtv.org/wiki/index.php/Recordedmarkup_table](http://www.mythtv.org/wiki/index.php/Recordedmarkup_table), which explains the different markup types.  FWIW, seeklist markup is kept in the recordedseek table.  CLI tools give you the ability to recreate seeklists and remove cutlists, but commflagging markup persists even after a successful lossless transcode of a recording with --honorcutlist.  So, the recording with commercials removed still has commflagging points defined and can interfere with frontend playback (depending on how you have commercial auto-skip setup).  Either way, the original commflagging points are inaccurate for the new recording.

The following script removes all commflagging and cutlists, and rebuilds the seektable.
```
#!/bin/bash

### removecommercials - for mythtv user job.
### $author Zack White - zwhite dash mythtv a t nospam darkstar deleteme frop do
t org
### $Modified 20080330 Richard Hendershot - rshendershot a t nospam gmail delete
me dot youknowcom

#   initialize;  all except SKIP are required for this to function correctly
declare VIDEODIR=$1
declare FILENAME=$2
declare CHANID=$3
declare STARTTIME=`echo $4 | sed -e 's/\([0-9]\{4\}\)\([0-9]\{2\}\)\([0-9]\{2\}\
)\([0-9]\{2\}\)\([0-9]\{2\}\)\([0-9]\{2\}\)/\1-\2-\3-\4-\5-\6/'`
# for lossless transcoding autodetect.  Set to empty string for rtJpeg/mpeg4.
declare MPEG2=--mpeg2

if [ -z "${VIDEODIR}" -o -z "${FILENAME}" -o -z "${CHANID}" -o -z "${STARTTIME}"
 ]; then
        echo "Usage: $0 <VideoDirectory> <FileName> <ChannelID> <StartTime>"
        exit 5
fi
if [ ! -f "${VIDEODIR}/${FILENAME}" ]; then
        echo "File does not exist: ${VIDEODIR}/${FILENAME}"
        exit 6
fi
if [ ! -d "${VIDEODIR}" ]; then
        echo "<VideoDirectory> must be a directory"
        exit 7
fi

# rebuild index
mythtranscode --mpeg2 --buildindex --allkeys -c ${CHANID} -s ${STARTTIME}
#mythcommflag -c ${CHANID} -s ${STARTTIME} --quiet --rebuild
ERROR=$?
if [ $ERROR -ne 0 ]; then
        echo "mythcommflag: Rebuilding seek list failed for ${FILENAME} with error $ERROR"
        exit $ERROR
else
        echo "mythcommflag: Rebuilding seek list successful for ${FILENAME}"
fi

mythcommflag -c ${CHANID} -s ${STARTTIME} --quiet --clearcutlist
ERROR=$?
if [ $ERROR -eq 0 ]; then
        echo "mythcommflag: Clearing cutlist successful for ${FILENAME}"

        # Fix the database entry for the file
        cat << EOF | mysql --password=<yourpasswordhere> mythconverg
UPDATE
        recorded
SET
        cutlist = 0,
        commflagged = 0
WHERE
        basename = "${FILENAME}";
DELETE
FROM recordedmarkup
WHERE chanid = "${CHANID}"
AND starttime = "${STARTTIME}"
AND type IN (-3,0,1,2,4,5);
EOF
        exit 0
else
        echo "mythcommflag: Clearing cutlist and commflagging from database failed for ${FILENAME} with error $ERROR"
        exit $ERROR
fi
```That can be used as a user job available from MythWeb or a frontend.  It will effectively reset the recording to pristine, uncommflagged, uncutlisted condition.

Commflagging does not duplicate or alter the original recording except that, IIRC, by default, it does a lossless transcode on the file prior to commflagging.  The transcode must involve temporary duplication of the original recording, but I don't have much insight into that process.

---

### Post by fatmonk on 2008-12-05
I wonder if its that lossless transcode that's causing the problem then. (I'm recording from DVB-T with a Nova-T 500 - does it still do the trsncode of the captured MPEG files? I didn't think the Mythbox had to do any encoding when it was a straight MPEG2/DVB capture)

It's defintely a case high levels of IO on the xfs disks killing them anyway.

Last night I reformatted the drive to ext3. Unfortunately I couldn't back up my content as even trying to read the 40GB of recordings off the drive onto another drive kept killing it.

So sacrificed the lot (after deleteing all the recordings via the front end interface).

I haven;tbeen able to test with the ext3 filesystem yet though as I can't get anything to record at the moment.

The newly formatted disk mounts properly at the right mount point, and is writable by the mythtv user (permissions and ownership all look good). The sym linking all seems to be good still aswell. Myth seems to think it is recoding programmes but the files aren't even being created!

I need to investigate that tonight - it got too late last night to do any more - but it's going to be really frustrating if I have the same problem with ad flagging on an ext3 disk as with the xfs disk after all this hassle.

-FM

---

### Post by fatmonk on 2008-12-18
Faulty disk!

After all that I've got to the bottom of it.

I tried commercial flagging recordings on my OS disk (just moved the recordings to a folder there for a while to test) and all was fine.

Tried copying files from my 500GB video hard disk and it failed during the read.

Seems the drive had problems when it was running at full speed (ie data transfer not limited by video decode or recording data throughput).

Had the drive swapped for an identical new one (although Maxtor badged instead of Seagate - but identical other than the label!) and the problem seems to have gone away after two nights of testing. (Fingers crossed!).

-FM

---

