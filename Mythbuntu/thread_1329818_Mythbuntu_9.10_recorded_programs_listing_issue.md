---
title: "Mythbuntu 9.10 recorded programs listing issue"
date: 2009-11-17
forum: Mythbuntu
---

### Post by shifti on 2009-11-17
I'm having an issue with my setup.  Please forgive me, as I'm going to include a ton of details, and probably forget a ton more.

In my setup, I have several machines, 1 Mythbuntu 9.10 with a backend+frontend(0.22.0+fixes22594-0ubuntu1 on both), 1 Ubuntu Netbook Remix with mythtv-frontend(0.22.0+fixes22594-0ubuntu1) installed, 1 macbook with mythtvfrontend(not sure of the version), and 1 windows 7 machine with MythTvPlayer and Windows Media Player.  All machines can access the Mythbuntu backend.

Initially, I had copied all of the directories from /usr/lib/mythtv to an LVM drive mounted under /storage.  I ran chgrp and chmod on all of the directories so that they belonged to the mythtv user and group, exactly how they were under /usr/lib/mythtv.  I then configured the backend to use /storage/foldername for everything.  I thought everything was running great, because I was exclusively using my stand-alone frontends.  This changed when I used the Mythbuntu machine to show live TV while I was falling asleep.  That's when the issues below started happening.  

I have 2 recorded shows, plus one that seems to be stuck in livetv for the moment.  When I run mythfrontend from my Mythbuntu machine, 47 shows are listed, including the 3 I just mentioned.  Those 3 play just fine, as does live TV.  The other 44 shows seem to be stuck in the list.  Attempting to delete them does nothing, no error pops up, and they do not get removed from the list.  Attempting to watch them gives me the following error:
> Recording unavailable
showname &quot;showepisode&quot;
The file for this recording can not be found.This behavior seems to be the same in Windows 7.  Using MythTvPlayer, clicking on &quot;Recordings&quot; lists the same 47 shows.  I can play the 3 that exist, attempting to play the others gives me the following error:
> Could not open stream 'filename.mpg'
I tried to open it from host '192.168.15.220' at port 6543'.

You can force all recordings to be opened from the master backend by setting &quot;AlwaysOpenRecordingsFromBackend' to 1 in the config file.Using Windows Media Player, in &quot;HTPC:MythTV AV Media Server&quot; under &quot;Videos&quot; the same 47 files are listed.  The 3 that exist also play fine, but the ones that don't exist give me the following error:  > Windows Media Player cannot find the file.  If you are trying to play, burn, or sync an item that is in your library, the item might point to a file that has been moved, renamed, or deleted.This problem does not exist on the machine running Ubuntu Netbook Remix, or the macbook.  Those 2 machines only display the 2 shows I have recorded, and the one stuck in livetv.  They play fine.  I can also set a show to record using those 2 machines, and delete them.  Using the Mythbuntu machine, I can only delete recordings that I am currently watching.  Attempting to delete them from the Media Library does nothing, they do not delete, and there is no error.  

Mythweb does not reflect this problem.  It only shows the 3 recordings mentioned earlier.  I can set shows to record, and delte them fine using Mythweb.  Under backend status, it shows that my space used is 60,376 MB.  However, the combined total of the 3 recordings that exist is only 12,180 MB.  

I've moved the LVM to /var/lib/mythtv/ and updated mythtv-setup.  This did not fix the problem.  I've also tried to repair my tables using both Mythweb and the command line.  I've also listed the contents of /var/lib/mythtv/recordings and livetv.  The recordings folder contains 2 mpg files, and 4 png files.  The livetv folder contains 1 mpg file and 1 png file.

Where are these phantom listings being stored?  Any help would be greatly appreciated.

---

### Post by shifti on 2009-11-18
Does anyone have any ideas?  This problem is very frustrating.  The only fix I can come up with at this point is to completely rebuild everything.  I really don't want to reinstall, spend a day configuring it, just to have the problem pop back up in the future.

---

### Post by SiHa on 2009-11-18
Not an elegant way forward, but maybe a solution. I had similar issue, where the backend was trying to auto-expire 5 files that didn't exist. It just keeps on trying. I ended up creating  empty files so that it had something to delete.
If you look in the backend log you'll probably find lots of 'file missing' errors. In a terminal:```
cd /var/lib/mythtv/recordings
touch <missing filename>
```
for each missing file to create empty ones. Hopefully Myth will now let you delete them. You can cut & paste in a terminal using Ctrl+Shift+C / V to make this process a bit quicker.

---

### Post by shifti on 2009-11-18
Unfortunately, since I was unable to delete recordings from my backend's frontend unless I was actively watching them, that didn't work for me.  It did get me on the right track though.  I had to create a video file using ```
cat /dev/video0 >test
```Then, for each file listed as not local in /var/log/mythtv/mythfrontend.log I ran ```
cat test > missingfile.mpg
```Since creating those files made me the owner, I had to change owner and group to mythtv.  ```
chown mythtv *
chgrp mythtv *
```I was then able to watch those recordings and delete them.  Strangely enough, I was mistaken, and the 3 recordings that actually existed didn't appear in the list.  Once I deleted all of the recordings giving me problems, and I exited and re-launched mythfrontend, the 3 recordings appeared.  I was then able to delete recordings without watching them, so this almost fixed all of my problems.  Unfortunately MythTvPlayer and Windows Media Player under Windows 7 still show a few erroneous recordings, but I don't care too much about them anyway.  Thanks so much for getting me on the right track.

By the way, you can also copy and paste by selecting text, then middle clicking where you want the text to be pasted.

---

### Post by SiHa on 2009-11-19
> By the way, you can also copy and paste by selecting text, then middle clicking where you want the text to be pasted.
Thanks for the tip, I generally don't use the mouse in a terminal, but it's useful to know.

---

