---
title: "Multi-threaded fast scp GUI for Ubuntu"
date: 2011-01-22
forum: Networking &amp; Wireless
---

### Post by bigsuccess on 2011-01-22
Hi guys,

I need help finding a GUI for SCP..something that will let me queue remote directories to download.

Using the scp command from the command line I get 500kb/s no problemo.. I use filezilla or other "SFTP" clients and they only download at 40-50kb/s.

So far I've been sticking with using CLI scp so I can get the better speed but this is limiting, as I would like to simply sort by date and download more recent files or generally peruse and add to a clipboard. Like winSCP...

As an alternative I thought maybe I could use a multi-threaded SFTP client... I suppose it would achieve the same thing (faster speed) perhaps, but not sure of the overheads..

So.. I'm left with a radical idea to try to run winscp in wine or try to write a bash script.. I think the former is ridiculous and the second would require some time in learning text handling of bash.. so .. does anyone have any other bright ideas before I go down these paths??

---

### Post by bigsuccess on 2011-01-22
I should state that, in Filezilla you can go to Settings > File Transfers and up the Maximum Simultaneous Transfers value up.

This is great if you have lots of files as it easily maxes my local connection.

This -sort of- solves the problem for me as usually I'm grabbing more than one file but it's still frustrating not to be able to open multiple threads on -one- file (segmented download). Might help someone else though :)

---

