---
title: "Mythcommflag warning: first frame is no key frame"
date: 2009-09-08
forum: Mythbuntu
---

### Post by ds_pablo on 2009-09-08
So I had a major problem.  I left for the weekend and when I got home my mythbuntu machine (a P4 1.6 GHz with 768MB RAM and 500GB hard drive for recordings 20GB hdd for system) had been watching liveTV for about 3 days straight.  During that time some I/O errors occurred and my recordedseek table became corrupted.  Hours and hours of letting mysqlcheck with the -r option just sat there trying to repair the table to no avail.  So in what was likely a bad move in retrospect I truncated the table in MySQL.  So all of my recordings are without seektables.  No big deal right?  Wrong.  When I run 

```
mythcommflag --all
```

I get this as output and it never moves forward.

```
2009-09-08 13:25:23.323 [mpeg2video @ 0xb742d744]warning: first frame is no keyframe
2009-09-08 13:25:23.510 [mpeg2video @ 0xb742d744]warning: first frame is no keyframe
2009-09-08 13:25:23.702 [mpeg2video @ 0xb742d744]warning: first frame is no keyframe
2009-09-08 13:25:23.843 [mpeg2video @ 0xb742d744]warning: first frame is no keyframe
2009-09-08 13:25:24.035 [mpeg2video @ 0xb742d744]warning: first frame is no keyframe
2009-09-08 13:25:24.614 [mpeg2video @ 0xb742d744]warning: first frame is no keyframe
2009-09-08 13:25:24.759 [mpeg2video @ 0xb742d744]warning: first frame is no keyframe
2009-09-08 13:25:24.947 [mpeg2video @ 0xb742d744]warning: first frame is no keyframe
2009-09-08 13:25:25.099 [mpeg2video @ 0xb742d744]warning: first frame is no keyframe
2009-09-08 13:25:25.242 [mpeg2video @ 0xb742d744]warning: first frame is no keyframe
```

This runs in what seems to be an infinite loop.  I have looked around regarding this error.  My searching has led me to believe that this can be common but many others have this warning followed by another warnign/error regarding MVs and mythcommflag then moves forward.  I would appreciate any help and while I have searched for this issue, I apologize in advance if I have overlooked the solution in my haste.  Thanks in advance for the help.

---

### Post by klc5555 on 2009-09-08
> **ds_pablo said:**
> So I had a major problem.  I left for the weekend and when I got home my mythbuntu machine (a P4 1.6 GHz with 768MB RAM and 500GB hard drive for recordings 20GB hdd for system) had been watching liveTV for about 3 days straight.  During that time some I/O errors occurred and my recordedseek table became corrupted.  Hours and hours of letting mysqlcheck with the -r option just sat there trying to repair the table to no avail.  So in what was likely a bad move in retrospect I truncated the table in MySQL.  So all of my recordings are without seektables.  No big deal right?  Wrong.  When I run 

```
mythcommflag --all
```

I get this as output and it never moves forward.

```
2009-09-08 13:25:23.323 [mpeg2video @ 0xb742d744]warning: first frame is no keyframe
2009-09-08 13:25:23.510 [mpeg2video @ 0xb742d744]warning: first frame is no keyframe
2009-09-08 13:25:23.702 [mpeg2video @ 0xb742d744]warning: first frame is no keyframe
2009-09-08 13:25:23.843 [mpeg2video @ 0xb742d744]warning: first frame is no keyframe
2009-09-08 13:25:24.035 [mpeg2video @ 0xb742d744]warning: first frame is no keyframe
2009-09-08 13:25:24.614 [mpeg2video @ 0xb742d744]warning: first frame is no keyframe
2009-09-08 13:25:24.759 [mpeg2video @ 0xb742d744]warning: first frame is no keyframe
2009-09-08 13:25:24.947 [mpeg2video @ 0xb742d744]warning: first frame is no keyframe
2009-09-08 13:25:25.099 [mpeg2video @ 0xb742d744]warning: first frame is no keyframe
2009-09-08 13:25:25.242 [mpeg2video @ 0xb742d744]warning: first frame is no keyframe
```

This runs in what seems to be an infinite loop.  I have looked around regarding this error.  My searching has led me to believe that this can be common but many others have this warning followed by another warnign/error regarding MVs and mythcommflag then moves forward.  I would appreciate any help and while I have searched for this issue, I apologize in advance if I have overlooked the solution in my haste.  Thanks in advance for the help.

If the recordings are dvb, mythcommflag can't rebuild the seektables for them anyway.

The correct procedure would be: mythtranscode --mpeg2 --buildindex  -c <channel> -s <starttime> (or -i <input-file>)

This should work for any individual recording. The downside is that it is set up for single files only --there is no "--all" switch. To handle an entire directory, you'd need either to write a script, or set it up as a user job, so that you could drop large numbers of your recordings into the job queue from the frontend and the recordings will be processed one after the other. This is the way I have it set up, since seektables are so fragile they die for any reason or no reason at all.

If your database is so hosed that seektables simply can't be built, then it will be  time to think about restoring the database from backup: from one of your daily backups if you make them, (and if you haven't so far, I'll bet you soon will) or from mythtv's weekly backups in /var/backups if you have one from immediately before the fatal weekend. In this scenario, after the database is restored from the appropriate backup, you'd use the script myth.rebuilddatabase.pl to find and add to this restored database any recordings that were made between the date of the backup and the weekend everything went kerflooey.

---

### Post by ds_pablo on 2009-09-08
> **klc5555 said:**
> If the recordings are dvb, mythcommflag can't rebuild the seektables for them anyway.

The correct procedure would be: mythtranscode --mpeg2 --buildindex  -c <channel> -s <starttime> (or -i <input-file>)

This should work for any individual recording. The downside is that it is set up for single files only --there is no "--all" switch. To handle an entire directory, you'd need either to write a script, or set it up as a user job, so that you could drop large numbers of your recordings into the job queue from the frontend and the recordings will be processed one after the other. This is the way I have it set up, since seektables are so fragile they die for any reason or no reason at all.

If your database is so hosed that seektables simply can't be built, then it will be  time to think about restoring the database from backup: from one of your daily backups if you make them, (and if you haven't so far, I'll bet you soon will) or from mythtv's weekly backups in /var/backups if you have one from immediately before the fatal weekend. In this scenario, after the database is restored from the appropriate backup, you'd use the script myth.rebuilddatabase.pl to find and add to this restored database any recordings that were made between the date of the backup and the weekend everything went kerflooey.

Thanks so much for the reply.  Interestingly enough, there are no other issues with the database.  Whether the seektables can be rebuilt at all, I do not know I will have to check into the recommended command.  The recordings are not DVB to my knowledge.  They are all from a PVR-150 which if I remember correctly si not a DVB card.  I do not have daily backups scheduled as of now though I do make backups manually about once every three days just because I use the backend as a desktop and it is easy to do.  You bet I will be making backups daily now though.  So your recommendation is to simply make a new backup, restore an old backup then use the rebuild script for purposes of restoring anything new since the old backup?  Shouldn't be bad but I want to make sure I followed the procedure you recommend correctly.  Thanks again and I will let you know how it goes and appropriately *fingers crossed* mark as solved.

---

### Post by klc5555 on 2009-09-09
> **ds_pablo said:**
> Thanks so much for the reply.  Interestingly enough, there are no other issues with the database.  Whether the seektables can be rebuilt at all, I do not know I will have to check into the recommended command.  The recordings are not DVB to my knowledge.  They are all from a PVR-150 which if I remember correctly si not a DVB card.  I do not have daily backups scheduled as of now though I do make backups manually about once every three days just because I use the backend as a desktop and it is easy to do.  You bet I will be making backups daily now though.  So your recommendation is to simply make a new backup, restore an old backup then use the rebuild script for purposes of restoring anything new since the old backup?  Shouldn't be bad but I want to make sure I followed the procedure you recommend correctly.  Thanks again and I will let you know how it goes and appropriately *fingers crossed* mark as solved.

You're right, insofar as mythcommflag should certainly be able to build seektables for analog pvr-150 recordings when using the --rebuild switch. If mythcommflag won't run at all any more on these recordings, then your mythconverg is likely toast. Since you have a reasonable backup of mythconverg, you can use it to restore from. 

The standard guide for backing up and restoring the database is here: [http://www.mythtv.org/wiki/User_Manual:Periodic_Maintenance](http://www.mythtv.org/wiki/User_Manual:Periodic_Maintenance) 

Note this document is generalized across mythtv beyond Ubuntu, so be sure to substitute your actual mythbuntu-random-generated mysql password after -p (and no space). The little 7-day backup script provided works very well as a daily cron job; I added an extra line to mine to put a second copy of the database backup where my recordings are stored since having my recordings survive a potential meltdown but not their database seemed kind of silly.

When you eventually run the myth.rebuilddatabase.pl script, it will need to be run sudo, to have the mysql password imbedded in the script, and to be run once for each separate directory in your default storage group where new recordings might be found. (Since the script predates the invention of storage groups.) You will be given an opportunity as the script encounters each new recording to edit in any metadata that the script may not have found in mythconverg's retained broadcast schedule. Edit in mostly whatever you want, but leave the 4-digit channel information alone that the script provides. If you edit the channel number information the script provides, the script will alter the file name of the recording to match the channel information you edit in. The recording plays, but becomes indigestible to utilities like mythtranscode. The script offers to commflag and seektable each new recording it finds: this works perfectly with analog recordings, but if you had any DVB recordings, the seektables would have to be added separately with mythtranscode.

Good luck. :)

---

### Post by one30nav on 2010-08-30
[SIZE=2][FONT=Arial, sans-serif]The &#8220;[mpeg2video @ 0x12345678]warning: first frame is no keyframe&#8221; error causes a log storm of entries in mythbackend.log similar to a self-inflicted denial of service attack. Troubleshooting was so frustrating that it almost made me drop Mythtv 0.23 and revert back to my previous, stable setup under Knoppmyth 5.5 (Mythtv 0.21). Thankfully, I found a solution after three weeks of research. I just wanted to share with you what worked for me.[/FONT][/SIZE]
 
 [SIZE=2][FONT=Arial, sans-serif]As far as I can tell with my setup (Mythbuntu 10.04, 32-bit w/PVR-500), the multiple warnings start occurring after a recording ends and right after mythcommflag attempts to start searching for a program&#8217;s logo. If you dig through the Mythtv bug reports, the symptoms of this problem closely resemble what&#8217;s in bug #6729. However, I didn&#8217;t want to apply this patch -- everything else works just fine; why dork with it?[/FONT][/SIZE]
 
 [SIZE=2][FONT=Arial, sans-serif]Surprisingly, one of the programmers under bug #6729 deemed this kind of recurring warning message a &#8220;non fatal&#8221; error, but I respectfully disagree. Although it does not cause an immediate system crash, it expands at least the mythbackend.log file to the point of full system lock up only resolved by a hard reboot. Cool thing is that same programmer recommended the brilliant &#8220;&#8211;v nogeneral&#8221; switch to repress the error reporting process (the keyframe warning is a "general" error).[/FONT][/SIZE]
 
 [SIZE=2][FONT=Arial, sans-serif]So, the following is how I used the -v switch as part of a &#8220;Commercial Flagger Command&#8221; manually inputted command within the settings section of Mythtv. In other words, type this in place of &#8220;mythcommflag.&#8221;[/FONT][/SIZE]
 
 [SIZE=2][FONT=Arial, sans-serif]mythcommflag &#8211;j %JOBID% -v nogeneral[/FONT][/SIZE]
 
[FONT=Arial, sans-serif][SIZE=2]The &#8211;j switch is the JobQueue ID from the jobqueue table and the &#8211;v switch is for verbose settings. From the &#8220;mythcommflag -v help&#8221; switch screen, the default for just &#8220;-v&#8221; is "important,general." Additive options like &#8220;no&#8221; may subtracted from the selected option. Thus, &#8220;-v nogeneral&#8221; equates to just show me important messages. However, I think &#8220;-v none,important&#8221; could produce the same effect.[/SIZE][/FONT]
 
 [FONT=Arial, sans-serif][SIZE=2]Hope this helps.[/SIZE][/FONT]

---

### Post by one30nav on 2010-09-19
UPDATE -- I can't say in good faith that correcting the "first frame..." log storm ceased my crashes, but it certainly helped me in limiting the size of the log file and making the log file usable again.

The biggest change I made for rock-solid stability for my system that has an on-board GeForce 6150, was reverting back to NVidia driver 173 and NOT using the buggy 185 version.  That did the trick; haven't had to mess with reboots for over a week now and counting.

---

