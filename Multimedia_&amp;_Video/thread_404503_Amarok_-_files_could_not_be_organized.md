---
title: "Amarok - files could not be organized"
date: 2007-04-08
forum: Multimedia &amp; Video
---

### Post by TidySi on 2007-04-08
Just wondering if anyone can help with a frustrating problem im having with Amarok?

All my music is held downstairs on my MS Media Centre. it controls my TV, cable and centrally holds all my albums and is very convenient. Upstairs I run Ubuntu Edgy in conjunction with Amarok which has made an index of the Media Centre mp3's and keeps itself updated nicely.

My problem is that I download my albums, use Amarok to check/change the tags and apply an album cover and wanted to use the option 'Manage Files' > 'Copy xx files to Collection'. This should take the newly downloaded album with its tags and album covers and then dump it onto my Media Centre but it doesn't. The error that comes back is 'Sorry, xx files could not be organized'.

Anyone having this problem? anyone know a fix for it?

Cheers

---

### Post by bsoric on 2007-05-30
I'm having the same problem on Debian. I try to rip a CD and it comes up with "10 files could not be organised".

---

### Post by supaneko on 2007-07-12
Hate to dig up an old thread but I seem to be having the same problem and have been having this problem ever since I switched to Amarok.

The files are not protected in any way (that I know of). And actually, I already organized a a CD prior to organizing this next one. The first set of 12 tracks was moved and organized just fine but when I attempted to move another set, it gives me the "Sorry, 12 tracks can not be organized." error.

...?

---

### Post by supaneko on 2007-07-12
OK, so here's what the problem is:

CERTAIN folders within My Music directory are "locked" and require root access to create or delete files in. I'm a little unsure as to why only certain music folders are locked while others I can access without any issue. I tried to change the permissions under Nautilus while logged in as root but I can't seem to change the permissions.

Any ideas?

---

### Post by strabes on 2007-07-12
```
sudo chmod -R 667 /path/to/music/directory && sudo chown username:username /path/to/music/directory
```

Also, don't use amarok to edit id3 tags. I find that it messes them up more often than not (kind of like that other music program that a lot of people use, iTunes, I think.) Use easytag or something similar to edit tags. Easytag also has a scanner that will rename the directories and files according to the tags.

---

### Post by jveezy on 2007-12-03
I had the same problem and I think I've found a way to fix it. I tried chmod on the Music folder before and that didn't solve the problem.

Turns out the music files themselves require permission changes. 

Just navigate to your music folder using the file browser, Ctrl+A to highlight all of them, Right click---->Properties, permissions tab, change them to read and write for whatever categories you need to. I changed all of mine to read and write but that's probably overkill. 

I'm not sure if this will work if you have all your music in separate folders. You may have to go into each folder individually and repeat the process.

Hope that works for you.

---

### Post by Support the 2nd on 2008-03-02
> **jveezy said:**
> I had the same problem and I think I've found a way to fix it. I tried chmod on the Music folder before and that didn't solve the problem.

Turns out the music files themselves require permission changes. 

Just navigate to your music folder using the file browser, Ctrl+A to highlight all of them, Right click---->Properties, permissions tab, change them to read and write for whatever categories you need to. I changed all of mine to read and write but that's probably overkill. 

I'm not sure if this will work if you have all your music in separate folders. You may have to go into each folder individually and repeat the process.

Hope that works for you.

I am having the same problem.  But I am looking at these 4 files right now and they all have the read/write permission.
I have found it seems to be with files going to folders with out the same syntax....like "AFI" mp3's going into the "afi" folder.  If the artist name is "AFI" it won't go into my "afi" folder.  But I have to find out how to make my folders accept capital letters, all the folders that were created in iTunes have capitals just fine in Kubuntu.

---

### Post by yochaigal on 2008-04-09
Hello.

i had this same issue --- amarok wouldn't organize my files ---- and I executed the chmod and chown command listed above.

Now, my music folder is completely empty, and my files are nowhere to be found.

Any way to reverse what just happened?  Or if not, what's some good gui file recovery software for linux - a la getdataback for windows?

thanks

---

### Post by FrooziE on 2008-05-04
Well I have the same problem, Amarok refuses to organize my files either from my ipod the HD or from one HD to another. It won't copy/move them to my external HD, it won't copy/move them to my main drive, it doesn't work when i'm logged in as a normal user, and it still doesn't when i log in as a root user. All files have the appropriate permissions and and all folders/drives are accessible. I can drag and drop using a file manager (Nautilus in this case) and can use Rythmbox to copy files from the ipod to the HD. It's an issue with Amarok, just not sure what it is. Any help would be awesome.

---

### Post by FrooziE on 2008-05-04
I solved my problem. What i did was install a program called PYSDM from Synaptic. It allowed me to change boot options for my external drive. I selected my external and in the "Options" area I added "umask=777" and now every user has all permissions. You can change the 777 part to give more specific permissions, I just don't know how. I attached screenshots.

---

