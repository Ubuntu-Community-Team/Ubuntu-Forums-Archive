---
title: "video permisssions after 10.10"
date: 2010-11-29
forum: Mythbuntu
---

### Post by wilma92010 on 2010-11-29
Hello There,

I have a new install of 10.10 after using 9.10 for a year or so.  

I restored a bunch of videos to /var/lib/mythtv/videos and have a few questions:

1) in 9.10 I had a symbolic link to /media in /var/lib/mythtv/videos in which was mounted a USB drive.   Never had a problem with the fact that this was NTFS.   Now, Mythtv can't see it, which I assume is permissions, as below.  How can I set permissions on the Mythtv side to allow mounted NTFS USB drives to be seen?

2) It looks like Mythtv will only see videos in the videos directory if the ownership is set to mythtv:mythtv.   This is easy enough to change, but then as a user (without sudo) can't cd into any of the folders with videos.   And from the desktop, can't get at the directories to play with VLC, etc.

3) Somehow I switched to "storage groups," which I did not use before.  I think this might be the cause.   Can I switch back to "not storage groups?"

Thanks for any help.

Wilma

---

### Post by thatguruguy on 2010-11-29
I had the same problem getting myth to see my videos.  As it turns out, it was because permissions set for "Others" was "None".  You can either make myth part of your own user group so that it can read the files, or set it up under thunar so that "Others" have read permission.  That way, you can retain ownership of the files and still read and write to the directories.

---

### Post by wilma92010 on 2010-11-29
Thanks for the reply and it works.  I gave 'others' read and write permission and now I can watch the videos.

However, I still haven't gotten the symbolic link to /media to work.  

I wonder why/how the change.  Any suggestions would be appreciated.

Wilma

---

### Post by thatguruguy on 2010-11-29
The change is because they are moving to storage groups, which is a more efficient way of categorizing and organizing video files.  You can list several different directories in your storage groups, if you wish.

---

### Post by lnoland on 2010-12-01
For what it's worth: when I first started using MythTV, it seemed like I was having problems related to permissions every time I turned around: I would create a directory and forget to give mythtv access to it; mythtv would create something and not give "other" access; etc.  At first I added myself to the mythtv group which helped a lot but I still ran into problems here and there.  I was ready to change access on everything to 777 even though I generally hate that solution.  I finally virtually rid myself of any more permission problems by turning on ACLs in my filesystem and setting acls giving my account and the mythtv account (as well as both groups) full control over everything that mythtv touches and making that the default in each directory.

- Les

---

