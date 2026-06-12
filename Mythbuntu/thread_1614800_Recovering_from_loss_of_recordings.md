---
title: "Recovering from loss of recordings"
date: 2010-11-06
forum: Mythbuntu
---

### Post by NautiusMaximus on 2010-11-06
I recently lost a whole load of recordings as follows. My network connection failed (see [this thread]("http://ubuntuforums.org/showthread.php?t=1604206") for the details if you're interested). I have a backup script that backs up recordings every day to an external hard drive. 

When the network connection failed, the external hard drive wasn't there, so it backed everything up to the mount point on the local hard drive (I've now modified my backup script so it won't do that in future: yes, that was the sound of a stable door being bolted). That meant that the hard drive quickly filled up, and Mythbuntu deleted a whole load of recordings to compensate.

Yes, I am aware of the irony that my attempt to be good and back everything up was what caused the data loss.

Anyway, I now have my network connection working again, and all my deleted recordings are safe and sound on my network disk. However, if I copy them back to the Mythbuntu hard drive, I'm guessing that's only half the battle, because presumably they have been deleted from the database by now as well, right?

Now, I also take backups of my database, so I could restore the database from before all the recordings were deleted. But that would mean that everything I've recorded since will no longer be available, right?

I don't think I've recorded anything unmissable in the couple of weeks it's taken me to solve the network problem, so if I had to just go back to where I was before the problem occurred, that wouldn't be the end of the world. However, if anyone knows of a way to restore the old recordings without losing the new ones, that would be much appreciated.

Thanks
NM

---

### Post by sully101 on 2010-11-06
This may be a bit too quick and dirty.... But you could create a folder in your videos directory an put them there so that you can watch them and catch up. then delete them or whatever later. If that doesn't suit then I would suggest posting on the mythbuntu forum.

---

### Post by klc5555 on 2010-11-06
The traditional way to add things back that aren't in the database has been myth.rebuilddatabase.pl But it may no longer function properly on up-to-the-nanosecond versions of mythtv, as its wiki page now comes with a warning label. [http://www.mythtv.org/wiki/Myth.rebuilddatabase.pl](http://www.mythtv.org/wiki/Myth.rebuilddatabase.pl)

Either use the script (if it still works) to add the older recordings back in, or restore your database from a backup and add the more recent recordings back in with the script.

The script will give you a chance to edit the metadata; otherwise you'll have to edit it later from mythfrontend.

If the script no longer functions in your version of mythtv, I'm not aware of a reliable substitute currently available.

---

