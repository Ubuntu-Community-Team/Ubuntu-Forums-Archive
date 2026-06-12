---
title: "[SOLVED] MythVideo Movie Covers not showing"
date: 2008-02-26
forum: Mythbuntu
---

### Post by MrKruger on 2008-02-26
Just moved in to the world of Ubuntu/Mythbuntu and trying to get my head around it.

I have got MythDvd and MythVideo to work and have been able to rip/transcode some movies. I make a search on IMDB and get all the details found (even the cover file name). But it still wont show up in my library, isn't it suppose to download the file? 

And my path to my directory that holds my movie poster is "/home/mythtv/.mythtv/MythVideo" but the /home/mythtv folder is empty!

Thanks!

Just amazed about the whole Ubuntu/MythBuntu, forum etc. YOU guys that work with it, my hat of!!!!!!

---

### Post by majoridiot on 2008-02-26
> **MrKruger said:**
> And my path to my directory that holds my movie poster is "/home/mythtv/.mythtv/MythVideo" but the /home/mythtv folder is empty!


a directory with a "." in front of it, such as ".mythtv" in /home/mythtv/.mythv means it is a *hidden*
file or folder.  to see the hidden content, you either need to enable "view hidden files" in 
your GUI file manager like thunar, etc.

or, if in a terminal, you use the -a switch to list all files with ls- e.g.:

```
$ ls -a /home/mythtv/
```

which would show you all of the files in the /home/mythtv/ directory, including .mythtv

---

### Post by Caps18 on 2008-02-26
> **MrKruger said:**
> 
I have got MythDvd and MythVideo to work and have been able to rip/transcode some movies. I make a search on IMDB and get all the details found (even the cover file name). But it still wont show up in my library, isn't it suppose to download the file? 

And my path to my directory that holds my movie poster is "/home/mythtv/.mythtv/MythVideo" but the /home/mythtv folder is empty!

Thanks!

Just amazed about the whole Ubuntu/MythBuntu, forum etc. YOU guys that work with it, my hat of!!!!!!

I haven't been able to figure out the video manager enough to search IMDB.  I should probably read the documentation tonight to see if it is in there.  (I still think that this should all happen behind the scenes when you start MythVideo, I think I found the setting to do load your videos automatically, but it wasn't set to on by default)

As for the covers, I manually created them from the Amazon.com page and put the file cover.jpg with each video in it's own directory.  Probably not the best way to do it, maybe by using the hidden directory, the pictures won't show up with the videos.

I am going to be doing some work on this tonight, so I will post a screenshot when it is all done. :)

---

### Post by majoridiot on 2008-02-26
> **Caps18 said:**
> I haven't been able to figure out the video manager enough to search IMDB.

enter into video manager and your new videos will be scanned into the database.

highlight the movie you want to search and hit "i" (or "info" on your remote if it is set up) and
you will get the menu to search imdb, enter manually, reset, etc.

some lookups will fail and return goofy info.  in that case, i see what the imdb # is
in the **IMDB Num** field, reset the metadata and then do a manual lookup, entering
the imdb number from the failed attempt.

---

### Post by MrKruger on 2008-02-26
Ok got it, should have figure that one out! But the .mythtv folder isn't there, just a .qt folder.

And I have been in the video manager where I manually reset the info, and added it again. Got all the info and even the name of the cover file (ex Over_the_hedge.jpg) but the pictures still not showing in the library!

---

### Post by MrKruger on 2008-02-26
> **Caps18 said:**
> 

As for the covers, I manually created them from the Amazon.com page and put the file cover.jpg with each video in it's own directory.  Probably not the best way to do it, maybe by using the hidden directory, the pictures won't show up with the videos.



Search the IMDB was simple and great, got all the info I needed and even the name for the movie poster, but it just wont show up! (to lazy to do it myself and it should work)

The directory structure is own by MythTV, so it should have write permission.

Did you said you can get it to check automatic?

---

### Post by MrKruger on 2008-02-26
Ok I figured out what the problem is, apperently it is a permission issue! I just made a temporary path to my home folder in "video manager" and then it worked smooth as! Just have to figure out how to change permission so i have read/write access to that folder, but that is another problem I suppose!

---

### Post by majoridiot on 2008-02-26
to give ownership to everything in the mythtv directory to user and group mythtv:

```
$ sudo chown -R mythtv:mythtv /home/mythtv/
```

---

### Post by MrKruger on 2008-02-26
> **majoridiot said:**
> to give ownership to everything in the mythtv directory to user and group mythtv:

```
$ sudo chown -R mythtv:mythtv /home/mythtv/
```

Hi MI,
Nop douse not work, as i understand it user "mythtv" already has owner privilege  as per below! 

ls -l /home
total 8
drwxr-xr-x 42 jk     jk     4096 2008-02-27 13:48 jk
drwxr-xr-x  3 mythtv mythtv 4096 2008-02-25 01:07 mythtv

Still he can write in to folder "jk" but not to "myth", don't get it!

---

### Post by majoridiot on 2008-02-27
you said it was a permission issue, so i assumed you wanted to assure everything in 
the mythtv directory and below belonged to mythtv.

if it was me, i would try reinstalling mythvideo and see if the correct directories are created.  
either that or create it by hand and set ownership and privs yourself.

---

