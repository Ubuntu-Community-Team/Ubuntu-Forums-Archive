---
title: "&quot;Watch Video&quot; option slow to open"
date: 2008-08-25
forum: Mythbuntu
---

### Post by Shades404 on 2008-08-25
My setup has a remote drive, currently mapped with sshfs but I have tried samba as well, mounted to /home/mythtv/media. 

I then added this directory to the video file location path in the configuration section.

The files are there and playable but it takes a good 15 minutes from clicking 'watch video' until the file list opens. The file list itself is okay but if I ever go back and then click again it takes just as long (if it was a one time thing I would not care)

I am assuming this is because it is trying to scan all the files in some way, however I can not find any options to change the way it does this.

How can I modify it so that it doesn't try and scan the remote files each time? (or so it does it quickly)

---

### Post by newlinux on 2008-08-25
15 minutes sounds like something is wrong. what size is the remote share? Have you run video manager? My videos don't rescan each time when I go to watch videos as far as I know. I don't have it set to browse files. So it simply reads the database after I have done one scan with video manager. But even then, to scan all my videos in video manager takes seconds (with a about 500GB of files). Do you get in errors in your logs?

---

### Post by Shades404 on 2008-08-26
There is a fair amount of files, not all vidoes, about a tb all told. The files are on a remote drive which I assume why the scan is slow. However I'm not sure why its doing it every time.

No errors in the logs, although I'll try running it with a higher logging level tonight.

---

### Post by newlinux on 2008-08-26
mine are all on remote shares (CIFS off my file server). Still seems like something is wrong to me... Do youhave more than one frontend? does this happen on all frontends?

---

### Post by SiHa on 2008-08-28
Just restating what newlinux said, explicitly.

In Video Manager there are options to 'Browse videos in list / gallery mode' When checked the frontend will scan the video directory every time you select 'Watch Videos', when unchecked it will simply download the list of files from the database.

---

### Post by Shades404 on 2008-09-09
Okay so I clearly didn't understand how it worked. I've removed browse file marks and now it only takes around a minute to load the 'watch videos' page. However that is still an unreasonably long time so I still must be missing something.

Also does this mean I have to tell the video manager to scan every time I want to see the new files, is there no option to automate the scan?

Thanks for the help so far :) seems I still need more though, I was expecting it to work like xbmc which only takes a few seconds to connect to the share.

---

### Post by Shades404 on 2008-09-09
> **newlinux said:**
> mine are all on remote shares (CIFS off my file server). Still seems like something is wrong to me... Do youhave more than one frontend? does this happen on all frontends?

I only have one frontend. I'm no where near the level of smarts to divide the whole thing out. I have mythbuntu on one box and a file server (running slackware) on another.

---

### Post by Shades404 on 2008-09-09
Turns out I'm a failure and didn't have the filters setup right so it was indexing 150 000 files rather than 2 000.. this is slow.

I could still do with some advise on setup up so it scans automatically (a cron task of some kind would be ideal)

---

### Post by SiHa on 2008-09-10
Not sure how to automate the scan, but now you're down to 2000 files, perhaps re-enable the 'browse' mode?
I've only got ~ 20 files in my Videos directory, so it's quite quick! :)

---

### Post by newlinux on 2008-09-10
I have an imdb bulk updater tool that I could track down that has option for scanning files. Since it is commandline it could easily be incorporoted into a cron. However, I think it is dangerous to do that, especially if you have a lot of metadata. If for somereason teh connection to your fileserver is lost or something else happens, it will see no videos, and delete all video information from your database... (In video manager it would ask you if you wanted to delete it, but there is no way to do that from a cron job) I think you probably want a smarter script. Let me know if you want me to find that script I have.

---

### Post by Shades404 on 2008-09-12
That script would be fine, I haven't set any of the metadata so it is only the risk of losing the list of files if the connection drops I have to worry about.

I assume it uses the file type filters when it imports?

---

### Post by newlinux on 2008-09-12
[http://thepisanis.com/node/11](http://thepisanis.com/node/11) Is the script I use.

Is the link and the README file for the imdb bulk updater script I use. Use the -Fileup option to scan... If you don't use one of the required options along with the Fileup option with the script it will give you an usage error after it does the scan, but you can ignore that. I think it does pay attention to file types -- briefing scanning the perl code I'm fairly confident  it does..

---

### Post by Shades404 on 2008-09-16
Cheers :)

---

