---
title: "Problems with updates: mythbuntu 12.04 and 14.04"
date: 2016-01-30
forum: Mythbuntu
---

### Post by singogli on 2016-01-30
I have edited this ticket at the moderator's request for clarity.

Can anyone confirm that installing mythbuntu 12.04 or mythbuntu 14.04 from dvd no longer works?  I have made multiple attempts on three different sets of hardware with both iso images with verified checksums.  Before updates are applied one of the problems with the 12.04 system is it hangs when accessing the schedulesdirect site.  This is a known problem so I applied updates to solve this.  The 14.04 install prior to updates has the recurring code 130 error where  the frontend endlessly tries to reconnect to the backend and it is virtually impossible to get control of the system.  Again I applied updates to resolve this. 
 
 After reading many tickets it has been my observation that when someone presents a problem, one of the first things everyone asks is if they have applied all the updates so I  try applying all updates before attempting to troubleshoot.  After all updates are installed all systems fail with similiar problems.  The updates mess up the mysql bind address which has to be edited back to 0.0.0.0   They also mess up the config.xml files which have to be edited to correct the Host entry to the fixed IP.   Once these are corrected and the backend fully configured and everything appears to be working normally  with no serious log errors a few successful recordings can be made. Then suddenly programs cannot be marked in the program guide for recording. "Watch recordings" no longer displays any of the previously recorded programs and says "No recordings available, or screen loading..."  "Upcoming recordings" says nothing has been scheduled.  The only apparent errors in the frontend log are: 
 ProgramInfoLoader remoteutil.cpp:184 (RemoteGetRecordingList) RemoteGetRecordingList() list size appears to be incorrect
CoreContext playbackbox.cpp:1800 (UpdateUILists) PlaybackBox: SortedList is Empty
ScreenLoad programinfo.cpp:1354 (FromStringList) ProgramInfo(): FromStringList, not enough items in list
CoreContext  programinfo.cpp:1354 (FromStringList) ProgramInfo(): FromStringList, not enough items in list.

The backend continues to chug along without any errors reported busily recording anything that was previously marked, but the frontend no longer reflects this.
Netstat shows mysql, mythfrontend and mythbackend all listening on all addresses fixed IP, local and inet6.

This happens with three different systems two 14.04 and one 12.04.

The point here is that both versions have different problems that suggest the updates are needed but once they are both fully updated they both have the same problem with the same or similar error messages in the logs.  This might be useful in trying to diagnose.

To answer the moderator's question yes the dvd creates a bootable ubuntu system but mythtv doesn't work correctly either before or after the updates.  "myth"buntu never appears to install correctly with either version.  I'm wondering if installing ubuntu and mythtv seperately might yield a different result and was hoping someone might have gotten past this and offer some insight. 

I have generated a ticket but the ticket workers are offering old fixes to what I suspect is a new problem and apparently no one else has reported this.  I have examined every related thread I could find and followed up on every suggestion and none of them helps solve this. At this point I don't think I've overlooked anything that's been documented. What I want to know is if anyone is successfully building a new mythbuntu system with 12.04 or 14.04 with the present updates in the past seven days.

Anyone?

I have installed and used mythbuntu several times in the past from the same 12.04 dvd and never experienced any of these problems but that was quite some time ago.

The bug report can be found here: [https://code.mythtv.org/trac/ticket/12612](https://code.mythtv.org/trac/ticket/12612)

---

### Post by Bucky Ball on 2016-01-30
So what you're saying is that both releases are indeed installable, but once you do that updates it crashes the machine? If so, you might want to edit your thread title and post to improve your chances of support. If both 12.04 LTS and 14.04 LTS are both still supported, why wouldn't they boot from DVD? You go on to explain that they did install and when you update things crash. That is your support issue by the looks of it. :-k

---

### Post by aelfric55 on 2016-01-30
I had a nearly identical problem on a system with a remote frontend and several slave backends during the the shift from mythtv 0.27.4 to 0.27.5. Unlike 0.27.4, the 0.27.5 master backend and database would not function correctly until I added the IPs and hostnames of all machines with slave backends and frontends into /etc/hosts on the master backend machine. Then everything worked.

---

### Post by tgm4883 on 2016-01-30
> **singogli said:**
> Can anyone confirm that installing mythbuntu 12.04 or mythbuntu 14.04 from dvd no longer works?  I have made multiple attempts on three different sets of hardware with both iso images with verified checksums but after all updates are installed all systems fail after several programs are marked for recording.  The result is always the same.  The updates mess up the mysql bind address which has to be edited back to 0.0.0.0  They also mess up the config.xml files which have to be edited to correct the Host entry to the fixed IP.   Once these are corrected and the backend fully configured and everything appears to be working normally  a few successful recordings can be made. Then suddenly programs cannot be marked in the program guide for recording. "Watch recordings" no longer displays any of the previously recorded programs and says "No recordings available, or screen loading..."  "Upcoming recordings" says nothing has been scheduled.  The only apparent errors in the frontend log are: 
 RemoteGetRecordingList() list size appears to be incorrect
PlaybackBox: SortedList is Empty
ProgramInfo(): FromStringList, not enough items in list

The backend continues to chug along without any errors reported busily recording anything that was previously marked, but the frontend no longer reflects this.
Netstat shows mysql, mythfrontend and mythbackend all listening on all addresses fixed IP, local and inet6.

I have generated a ticket but the ticket workers are offering old fixes to what I suspect is a new problem and apparently no one else has reported this.  I have examined every related thread I could find and followed up on every suggestion and none of them helps solve this. At this point I don't think I've overlooked anything that's been documented. What I want to know is if anyone is successfully building a new mythbuntu system with 12.04 or 14.04 with the present updates in the past seven days.

Anyone?

I have installed and used mythbuntu several times in the past from the same 12.04 dvd and never experienced any of these problems.

Can you link to the bug report.

---

### Post by singogli on 2016-01-31
I added fixed IP and hostname to /etc/hosts as  aelfric55 suggested but no change.

The bug report can be found here: [https://code.mythtv.org/trac/ticket/12612](https://code.mythtv.org/trac/ticket/12612)

---

### Post by tgm4883 on 2016-01-31
> **singogli said:**
> I added fixed IP and hostname to /etc/hosts as  aelfric55 suggested but no change.

The bug report can be found here: [http://ubuntuforums.org/showthread.php?t=2311776&highlight=singogli](http://ubuntuforums.org/showthread.php?t=2311776&highlight=singogli)

You linked back to this thread, not to the bug report.

---

### Post by singogli on 2016-01-31
Whoops.  Here's the correct link:  [https://code.mythtv.org/trac/ticket/12612](https://code.mythtv.org/trac/ticket/12612)

Thanks.

---

### Post by khPWXxF on 2016-02-02
You say:

             > I have edited <Host></Host> in : /home/mythtv/config.xml /etc/mythtv/config.xml /home/steve/.mythtv/config.xml to <Host>192.168.10.128</Host>

Did you mistype?  Should be:
> /home/mythtv/.mythtv/config.xml
(but it is probably a link to /etc/mythtv/config.xml anyway)

Phil

---

### Post by singogli on 2016-02-02
You are correct.  I did indeed edit /home/mythtv/.mythtv/config.xml and mistyped in the post.  
As I have said- everything works fine until some number of recordings are scheduled.  
This is totally reproducible.
I just rebuilt as a new system today as a master backend and it does the same thing.
I'm becoming convinced there's something in a recent update that causes this.

---

### Post by singogli on 2016-02-20
I have retitled this thread to the most relevant frontend error message in the hope it may aid someone else.
Title was: Problems with updates: mythbuntu 12.04 and 14.04

Well I finally solved this and am posting the details.  The actual problem was hidden null characters in the database.  Specifically the name field in the channel table and the service_name field in the channelscan_channel table.   The actual mysql commands needed were: UPDATE channel SET name=REPLACE(name,'\0'''); and UPDATE channelscan_channel SET service_name=REPLACE(service_name'\0','');
What obscured the solution were two things.  First, the database works properly for a while.  Only when a particular channel is selected for recording does the frontend lose contact with the backend.  In my case since updates were coming through on an almost daily basis for the first week after the original build I would check the system in the morning and find that the error had occurred overnight.  This was coincidental with having scheduled a recording overnight of a program on the problem channel. 

Secondly, these null bytes do not appear in the table when examined with PHPMyAdmin.  The only way to discover them I could find was to backup the entire database with mysqldump and then search the entire database with gedit for the offending \0 byte.  Once the problem is identified this way than the mysql replace commands do the fixes.

Unfortunately the suggestions on how to locate null bytes did not work for me, mysql always reported a problem with the search string example:       SELECT * FROM channel WHERE callsign LIKE '%\0%';
And the tools for fixing a corrupt database always indicated the database was O.K.    
All the null characters that appeared with PHPMyAdmin were in fact irrelevant so I kept looking for a problem elsewhere.
Apparently there is no "sanity check" on this raw channel data import. Perhaps in a future update?
The channel that caused this is an Albuquerque OTA channel 21.3.   

What allowed me to solve this was a closed thread:  Recordings suddenly gone?

[http://ubuntuforums.org/showthread.php?t=1729026&page=2&highlight=PlaybackBox%3A+SortedList+Empty](http://ubuntuforums.org/showthread.php?t=1729026&page=2&highlight=PlaybackBox%3A+SortedList+Empty)

Scroll down to # 13 from BookofJarom.

---

