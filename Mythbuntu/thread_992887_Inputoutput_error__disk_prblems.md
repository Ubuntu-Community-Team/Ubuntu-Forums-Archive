---
title: "Input/output error / disk prblems?"
date: 2008-11-25
forum: Mythbuntu
---

### Post by fatmonk on 2008-11-25
Over the weekend I tried some soak-testing of my box.

On Friday night I set the box up to record about 20 programmes between that night and Sunday evening.

I didn't touch the box over this time in an effort to see how stable the box was.

When I checked what had worked on Monday I found the box in an odd state.

The LCD screen was displaying the name and time of a programme that was scheduled to record overnight on Friday night (there should have been at least a dozen other programmes recorded after this). This programme was a 0.0GB eror programme, ie Myth thought it had recorded something according to the database, but no file had been created. All subsequent recordings were the same. And the LCD didn't update when any ofthem started (I was in front of the box when the first Monday recording shoudl have started).

When I manually checked to see if the file had been created by going to /var/lib/mythtv/recordings, I was unable to ls in that directory - getting an Input/output error reported by ls.

On further investigation, both my recordings and videos directories were unavailable due to this Input/output error.

These two directories are in a 'whole disk' partition on a second hard drie in my machine, mounted as /home/other_media and sym linked from /var/lib/mythtv. The file system on this disk is xfs.

The only way to get the disk back was to do a power down reboot (the partition wouldn't unmount (said it was busy!) so I couldn't try manually remounting, and a simple restart didn't work - it had to be full power down.)

When the machine came back up all seemed fine.

I checked to see which programmes had actually managed to record, and only two had!

The second prgramme which had recorded - which was the scheduled immediately recording before the 0.0GB mentioned above - seemed to hae recorded OK, but on further inspection there was a problem.

When I tried to play back this second programme it got about 2 minutes in, the screen went black, the hard disk activity light came on solid and Myth froze. After a few minutes after pressing escape I got back to the menu, but nothing from that disk worked (playback of recorded TV, playback of live TV, playback of videos (stored on the same disk as mentioned)).

So I checked the directories manually and again I was getting the Input/output errors.

So, another power down reboot later I tried again, same result.

So yet another power down reboot later I tried once more, this time skipping forward in 30 second chunkc until I was passed the freeze point. After that the programme plays back fine, and the system continues working.

If I then go back and play through the freeze point the system hangs and the disk becomes unusable again until a power down reboot.

When the system is first up, I am able to unmount the partition, run xfs_repair (it doesn't report any errors have been fixed) and remount, but I get the same problem if I play that clip.

My concern is that maybe I have a bad disk or bad sectors on the disk (its a brand new 500GB Seagate Baracuda 7200). But I don't know what to do to check for bad sectors or mark them as unusable to see if the problem recurrs.

It seems that this particular recording may have killed the partition for that session but managed to complete its own recording as it was already writing to disk (!?), but the subseqent recordings failed as they couldn't open a file on the disk. Would this make any sense?

Can someone give me some pointers as to what I can check to see if I really do have a bad HDD.

Thanks,

FM

---

### Post by dmfrey on 2008-11-25
Not sure if you want a pay-for solution, but have you considered SpinRite.  I have used it on a few situations and it has recovered the disk fully.  Check out [http://www.grc.com](http://www.grc.com), it has been a lifesaver in a few situations.

---

### Post by fatmonk on 2008-11-25
Hmm, I don't really want to spend that kind of money, to be honest.

I could pick up a replacement drive for that price, and there's no data on the drive that I need to recover.

Any freeware utilities around that would just do a good check of the disk and maybe mark bad sectors as bad?

If I can prove the disk is faulty I can take it back for replacement as I only bought it 6 weeks / 2 months ago!

Cheers,

FM

---

### Post by ian dobson on 2008-11-25
Hi,

Do you see anything in your backend log file when you try and record? A 0 byte file usually means the the tuner tuned to the correct channel but it didn't start delivering any data.

Regards
Ian Dobson

---

### Post by fatmonk on 2008-11-26
Hi Ian,

I originally thought that was the problem I was having (the one related to the Nova-T card going into suspend mode).

However, the tests over the weekend were to test the fixes I'd put in place last week - ie changing the various EIT scanning settings, disabling remote polling etc - to see if that stabilised things.

Then I noticed the disk partition being unavailable which would certainly cause 0byte files.. I now wonder if this was the problem I was having all along as I seemed to be seeing the 0byte problem more often than most reporters of the suspend problem.

I'll check out my backend logs as well though, although I did check those last wek and there seemed to be nothing to indicate that there was a problem recording (which again looks like the suspend issue).

-Confused FM

---

### Post by fatmonk on 2008-11-26
This is the output I get from xfs_repair -v. To me it looks like everything is OK...

Is there anything else I can check to see why a particular recording crashes my disk? Or does something here look wrong to anyone?

```
# xfs_repair -v /dev/sdb1
Phase 1 - find and verify superblock...
        - block cache size set to 180520 entries
Phase 2 - using internal log
        - zero log...
zero_log: head block 13813 tail block 13813
        - scan filesystem freespace and inode maps...
        - found root inode chunk
Phase 3 - for each AG...
        - scan and clear agi unlinked lists...
        - process known inodes and perform inode discovery...
        - agno = 0
        - agno = 1
        - agno = 2
        - agno = 3
        - process newly discovered inodes...
Phase 4 - check for duplicate blocks...
        - setting up duplicate extent list...
        - check for inodes claiming duplicate blocks...
        - agno = 0
        - agno = 1
        - agno = 2
        - agno = 3
Phase 5 - rebuild AG headers and trees...
        - agno = 0
        - agno = 1
        - agno = 2
        - agno = 3
        - reset superblock...
Phase 6 - check inode connectivity...
        - resetting contents of realtime bitmap and summary inodes
        - traversing filesystem ...
        - agno = 0
        - agno = 1
        - agno = 2
        - agno = 3
        - traversal finished ...
        - moving disconnected inodes to lost+found ...
Phase 7 - verify and correct link counts...

        XFS_REPAIR Summary    Wed Nov 26 21:04:01 2008

Phase		Start		End		Duration
Phase 1:	11/26 21:03:59	11/26 21:03:59	
Phase 2:	11/26 21:03:59	11/26 21:04:00	1 second
Phase 3:	11/26 21:04:00	11/26 21:04:01	1 second
Phase 4:	11/26 21:04:01	11/26 21:04:01	
Phase 5:	11/26 21:04:01	11/26 21:04:01	
Phase 6:	11/26 21:04:01	11/26 21:04:01	
Phase 7:	11/26 21:04:01	11/26 21:04:01	

Total run time: 2 seconds
done
```

-FM

---

### Post by fatmonk on 2008-11-26
Right, it's just done it again (between 2200 and 2214 machine time) and here are the logs:

[http://mythbuntu.pastebin.com/f26222363]("http://mythbuntu.pastebin.com/f26222363")

I think it may have been just as the box finished advert flagging the previous recording that things died.

On a possibly related note, my 2GB RAM machine is running permanently at about 95% RAM use (only 3-4% free) - is this normal?

-FM

And thinking about that xfs_repair command... itruns in about 3 seconds flat. SUrely that hasn't checked a 500GB disk properly in that time.

---

### Post by fatmonk on 2008-11-27
I may be speaking to soon, and will update later after more scheduled recordings, but over night I ha a few recordings work after disabling advert flagging.

This, and the fact that the disk seemed to go into its I/O error state as at approximately the time that an ad flagging job ended makes me suspect the ad flagging process right now.

While the ad falgging was running my RAM usage was up at 96-97%, this remained after the job had 'finished' but was still queued, and while the disk was in its I/O error state.

After a power-down-reboot (the only way to get the disk online again) my RAM usage was back down at around 20% while recording.

Does this give anyone any further clues?

The box was flagging an ITV programme, by the way, and I suspect it didn't actually find all the ad breaks (45  minutes worth of recording on ITV in the UK would normally contain 2 or 3 breaks, but the job status screen showed that only one break had been found.

-FM

---

### Post by fatmonk on 2008-12-01
Ever feel like you're talking to yourself?

Anyway, I've found the problem - or at least the cause of the problem, so will start another thread on this...

It is the commercial flagging (or something related to it) that kills the disk! No ad flagging and the box has run for a week with mutiple recordings, including some heavy multi-rec, without problems.

-FM

---

