---
title: "Myth Feisty; Where's the recording?"
date: 2007-05-12
forum: Multimedia &amp; Video
---

### Post by Panhead Bill on 2007-05-12
I just got mythtv to work on my test mule pc.  
I made a short recording (1.4 gig) to test the system out.

I can find and watch the file using mythtv.

The myth install is a frontend/master backend and as such doesn't have the graphical file browser that my main mytyhbox does. 

Using the terminal, however, I can't find the file.  The video is stored in the drive with a mount point of /var/lib - the default using the community guide.  When I open the /var/lib directory and use ls -lh -S -r for instance I get a nice list with file sizes in ascending order.  But the largest file listed is 4 meg. 

So where is this 1.4 Gig file hiding, and how (what commands) do I find it?

The reason and irony of this is that my main mythbox "lost" all of my recordings; at least as far as Mythtv is concerned.  I can find these files using the graphical file browser, and samples of these files that i checked were not corrupted.

Ultimately I want to move the files from the main box to the test mule and then replace the edgy mythtv install with feisty and a fresh install of mythtv.

---

### Post by Panhead Bill on 2007-05-15
Okay I found the files - sort of - using locate.     "locate .mpg"

The recordings on the test mule are at:
/var/lib/mythtv/recordings/*individual_recordingnumber*.mpg

When I try to get into the mythtv directory I get:     No such file or directory

On the mythbox similar results; /video/recordings/*individual_recordingnumber*.mpg
and the "no such" response.

So, how can I get access to the directories and files,  and how can I move the recordings Individually from one machine to the other.  I am trying to save the recordings at this time.  Later I will be setting up master and slave units per the guides.

The followup question would be is anything else needed to make the transfered recordings accessable to the recipiant mythtv system?  I personally don't need the information in the database about the recordings, just access to be able to view them.   Of course Mythtv might need this information, but I don't know the answer to that.

Anyone have suggestions other than trash the old recordings and start fresh?

---

### Post by barney_1 on 2007-05-15
I think you're missing the beauty of the mythtv frontend/backend system.  Choose one machine to be your Master Backend.   This machine will do your recording, store all your recorded programs, flag commercials, etc.  Then, you just need to install the frontend all other machines.  They will access the database on the backend and stream the recordings over your network.  Check out the community documentation for help on these topics:

[https://help.ubuntu.com/community/MythTV_Feisty](https://help.ubuntu.com/community/MythTV_Feisty)

---

### Post by Panhead Bill on 2007-05-16
Barney_1; 
 I must have stated the problem poorly.  My main mythbox got "borked" when I foolishly updated about 47 packages that the update manager indicated.  From that point on the backend wouldn't work, and the recordings were invisible to mythtv.  The main mythbox was edgy.

I assembled the "test mule" box and loaded feisty and myth, in order to determine if the recordings were saveable.  This is the only reason I haven't reloaded the mythbox with the latest and greatest.

Last night I finally found out how to transfer the recordings from the "mythbox" to the "testmule" Via ethernet using ssh.  The recordings had to be transferred from the "Recordings" directory iinto the "videos" directory, then they would play on the second box.

Later I moved a video file from recordings to videos, but on the "borked" mythbox, and the recordings played on that box too.

Soon I will have a master backend with slave frontends.  I just had to save the recordings that the database "lost" when the system got updated.

---

### Post by MCMcButtah on 2007-07-16
I have this same problem, I applied a bunch of updates and after that my myth recordings are gone for no reason. They exist on the drive, they exist in the mysql database, file permissions are 777...I just can't figure it out. I would just move them all from recordings to videos and be done with it, but my mythbox won't make any new recordings. If I choose record, it says it is recording, and will show up under previously recorded menu, but does not show up under recordings. HELP! :(

---

### Post by MCMcButtah on 2007-07-25
I fixed it

[http://www.mythtvtalk.com/forum/viewtopic.php?t=6009](http://www.mythtvtalk.com/forum/viewtopic.php?t=6009)

---

