---
title: "MS Windows feature: &quot;Make Available Offline&quot;"
date: 2011-02-20
forum: Networking &amp; Wireless
---

### Post by jtraceypgh on 2011-02-20
I'm evaluating Ubuntu 10.10 for the possibility of switching to it from Windows XP.  One of the features I use a fair amount is the ability to have some of the files from my secretary's computer in the office available offline at all times on my laptop.  That way no matter where I am they can be accessed.  Any changes either of us makes are synced when I reconnect to the office network.  Is there a way to accomplish this with Ubuntu?

---

### Post by sanderd17 on 2011-02-20
You can use rSync for this. It's a commandline tool, so you can put it in a script to automise. rSync will not merge files. If your assistent and you edit the same file while being offline only one file will be stored on the shared server.

If you want merges, you will need to use a version control service and only work with plain text files. (this will require a lot of setup work and active maintenance)

[https://help.ubuntu.com/community/rsync](https://help.ubuntu.com/community/rsync)

---

### Post by restorator on 2011-02-20
If you are now using something like Microsoft's livesync, you could switch to one of the many other sync offerings out there. A few I can think of off the top of my head are: Dropbox, Spideroak, and Sugarsync, etc. There is also Ubuntuone but I am not sure if that syncs or is just for backups.

---

### Post by Boondoklife on 2011-02-20
I don't think the "make available offline" option merges files that were edited on both sides:
[http://support.microsoft.com/kb/252509](http://support.microsoft.com/kb/252509)

rSync would be a great option, and you can just use a gui like grsync to do the syncing back and forth. Put a shortcut to it on your desktop and the only think you will have to do is run it before you leave the office and you will have the latest files.

I use a shell script to sync my pictures with my backserver, so I have my pics when I am out and about.
```
rsync --progress --no-p --no-g -trvhn /home/boondoklife/Pictures/ /home/boondoklife/Network/pictures\ on\ elohim/
```*This one is a dry run, just to make sure you see the results you want.

```
rsync --progress --no-p --no-g -trvh /home/boondoklife/Pictures/ /home/boondoklife/Network/pictures\ on\ elohim/
```

Neither of these will delete removed files, but this is how I wanted it. This can be changed by adding the --delete option.

---

### Post by jtraceypgh on 2011-02-21
Thanks for the feedback.  I look forward to tinkering with this when time permits...

---

### Post by jtraceypgh on 2011-02-25
For some reason I cannot seem to find/select a network (windows) drive/file.  Any simple things I'm missing?

---

### Post by Boondoklife on 2011-02-25
What do you mean? Are you able to see them under network? Give a little more information about your issue.

---

### Post by jtraceypgh on 2011-02-25
Sorry for being unclear.  I can see network shares via network, I just can't seem to access them through grsync.  I've tried browsing, which I read somewhere does not work, so I tried manually entering the address into the gui interface and that didn't work either.  

I'm not a programmer, though I did a little decades ago in dBase III+, so I want to avoid having to use the command line as much as possible.  Yes, I've gotten spoiled by Windowsworld!  8-)

Thanks again for any help...

---

### Post by Boondoklife on 2011-02-25
create a link to .gvfs in your home dir. Easiest way is to open a terminal and run:
```
ln -s .gvfs 'Network Shares'
```

You should then be able to see the "Network Shares" folder in your home directory.

---

