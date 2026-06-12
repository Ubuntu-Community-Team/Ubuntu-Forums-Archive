---
title: "I've messed up my database"
date: 2012-06-04
forum: Mythbuntu
---

### Post by Leechpool on 2012-06-04
Hi,
I am running mythbuntu 11.10 0.24+fixes combined frontend/backend. I have 1.7 Tb of storage on a separate DATA partition and have set the option where when you detele something it moves it to the deleted cat and also have the slow delete set. Most of the storage was taken up by deleted recordings waiting to autoexpire. I went into the deleted cat added all to playlist and selected delete playlist option. I noticed the machine didn't shutdown (I use myth welcome which shuts the machine down when its idle). I went into system info and notice the free space was increasing by a few Gb every minute or so. I assumed the slow delete was working its way through things but I wanted to speed things up to I went into the backend settings and turned off slow delete (no recordings were active)- when I went into settings it complained the backend was running but I hit the option to shut backend and continue. The amount of free space jumped to 500 ish Gb. I have reset delete slowly option and rebooted several times but I'm still left with only 81 recordings showing in watch recordings (this is correct) and over 1 Tb reported as in use. There are over 2000 files in the specified storage folder for recordings (I would have expected 81x2=162). I've tried find_orphans.py - it identified about 4 zero byte recordings but no orphans. How can I reconcile my 81 recorded programs in watch recordings but over 2000 files (1 Tb) in storage folder.
There is no longer a deleted category in watch recordins. I guess I've messed up by turning off slow delete and forceing the backend to close while it was in the middle of deleting a large number of recordings! I've tried googling and everything I found seems to involve find_orphans.py sorting things out but this doesn't seem to work for me although the script appears to run ok.
Any help to recorver from this foolish situation I have created would be much appreciated.....
Thanks.

---

### Post by klc5555 on 2012-06-04
I'm not certain I've gotten your description exactly, but if I understand your problem as described, in your data partition you currently have 81 recorded programs you wish to keep, and the metadata in mythtv for these programs is correct.

In your data partition you also have a whole boatload of recorded programs you do not wish to keep, but for these, while the metadata has already been deleted, most (but not all) of the program files themselves are still on the partition. You need to delete these files from the partition while keeping the 81 good programs. For whatever reason find_orphans.py cannot do the job of distinguishing one from the other for you.

The best solution is likely to debug what is going wrong with your running of find_orphans.py

But if this is not possible and if I have in fact interpreted your description of your situation correctly, one possible brute simple solution is this: 

1)Make a temp directory in your data partition. 

2)Use nuvexport to make copies of all 81 good programs into this temp directory (using the "Export to .nuv and .sql" option; when asked if you want to remove the recordings from the server, you'll answer the default "No", of course) [http://www.mythtv.org/wiki/Nuvexport#Export_to_.nuv_and_.sql](http://www.mythtv.org/wiki/Nuvexport#Export_to_.nuv_and_.sql) 
This part will take a bit of time, as nuvexport will have to be run separately for each program heading.

3)When you have confirmed that all 81 of your programs have been thus copied into the temp directory by nuvexport, use a file manager (or from the CLI) to manually delete everything in the data partition EXCEPT the temp directory. 

4)When the deleteion of everything EXCEPT the temp directory is complete, use a filemanager (or the CLI) to manually copy all the 81 recordings files (just the .mpg's obviously, not the other stuff) from the temp directory back to the main directory in the data partition.

5)The job is done. As far as mythtv is concerned, the 81 restored recordings files are the ones that were always there, even frame indexes will work. And the trash recordings are now gone. When the 81 shows have been copied successfully back to the main directory, and you've assured yourself myth can access them properly (make sure the ownership of the files is still mythtv:mythtv, and not something like [you]:users), the temp directory and its contents may be deleted.

Perhaps other solutions may also be suggested.

---

### Post by Leechpool on 2012-06-04
Hi,
Thanks for taking the time to reply.
Your interpretation of my problem is correct.
I've not come across "Export to .nuv and .sql" but it appears to be a possible solution....
Thanks again

---

### Post by nickrout on 2012-06-04
don't export them yo nuv, they will be transcoded (very time consuming) and will lose quality.

simply use the command line (rm ) to delete what you son't want to keep.

And let the system do it's own thing to delete things in future. Why do you care if the disk is fullish? The system will delete to make room.

---

### Post by klc5555 on 2012-06-04
> **nickrout said:**
> don't export them yo nuv, they will be transcoded (very time consuming) and will lose quality.

simply use the command line (rm ) to delete what you son't want to keep.

And let the system do it's own thing to delete things in future. Why do you care if the disk is fullish? The system will delete to make room.

Nuvexport's "export to nuv and sql" option has an obsolete and  somewhat misleading name (as the doc points out). The option doesn't actually transcode anything at all; it simply copies the mpg (or nuv) file, extracts a copy of the sql, and puts them both in a little directory with the show's name. Therefore, the resulting copied file is identical to the original, no quality is lost, and the processing speed is whatever your disc read/write speed is. Usually under 20 sec. for a 1 hour Standard Digital recording. 

This is a feature of nuvexport I use daily, and even have it set up as a user job.

---

### Post by klc5555 on 2012-06-05
After a bit of thought it occurred to me that the following would be a still simpler method of doing what you want done. After setting up a temp directory as above, set up a basic copy job as a user job. Then you could drop your 81 programs one after another into the job queue from the frontend menu, and let the backend do the grunt work of copying all the good recordings into the temp directory. This will give you copies of the recordings files themselves in the temp directory, but would not bother with the sql snippets and other stuff you don't need that nuvexport would also have supplied.

The command line of such a basic user job would look something like```
cp %FILE% /[path]/temp
``` where you would substitute your actual complete path to the temp directory. See also [http://www.mythtv.org/wiki/User_Jobs](http://www.mythtv.org/wiki/User_Jobs)

When the queue has run the jobs, and you have confirmed that the temp directory contains 81 recordings files, you can procede to delete the contents of your data partition EXCEPT the temp directory, then copy the 81 recordings from the temp directory back into the empty data partition.

---

### Post by nickrout on 2012-06-05
What is wrong with just deleting the ones you don't want?

---

### Post by klc5555 on 2012-06-06
The problem seems to be that through OP user error the metadata for the unwanted recordings is already gone, but the recordings files themselves are still there. He can't distinguish the 81 wanted recordings files from the unwanted ones by simple observation, and the unwanted recordings files are now invisible to mythtv.

Though this would normally be a job for find_orphans.py, the OP reported himself unable to get find_orphans.py to return the list of orphaned recordings without metadata, and has not been able to debug this poorly documented script to determine why it is not returning the desired information.

So the task has been to find a simple alternative method not based on find_orphans.py to distinguish the wanted recordings files from those that are unwanted, and then to delete completely all the unwanted recordings files while retaining just the 81 wanted recordings files.

---

### Post by Leechpool on 2012-07-27
Many thanks to klc5555 for his user job suggestion. It works very well. Even able to add "all programs" to playlist in a few remote clicks and then apply user job to whole playlist so that copying each program appears in the job queue and gradually gets copied into a temporary directory as machine goes through job queue.  I was then able to delete contents of recorded programs directory and move contents of temporary directory back and all was well. :P

---

