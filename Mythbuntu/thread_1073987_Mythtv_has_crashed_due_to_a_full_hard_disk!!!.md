---
title: "Mythtv has crashed due to a full hard disk!!!"
date: 2009-02-18
forum: Mythbuntu
---

### Post by Hayesio on 2009-02-18
Hi everyone,

I've had my Mythbuntu machine working like a dream for 6 month now and completely without fault. The other day everything just locked up whilst watching TV and i had to hard reset the machine. What had in fact happend was i'd run out of HDD space so it couldn't continue to record.  I've now cleared space on the HDD but mythtv just wont start-up.  When i start the machine, the desktop loads fine but then Mythtv brings up the "Select prefered language" screen followed a "No UPnP backend found" window.  It then asked me for the database settings (which i dont know). So it appear mythtv has lost the ability to connect to the database!

Does anyone know how to get mythtv back up and running? 

Thanks,
Hayesio

---

### Post by ian dobson on 2009-02-19
Hi,

Looks as if your backend isn't starting. Have a look in the /var/log/mythtv/mythbackend.log to see what could be causing the problem.

Regards
Ian Dobson

---

### Post by Monsieur Gonzalez on 2009-02-19
Check your root partition. It might have filled with error logs from mythtv, I know it happened to me once. Carefully delete log files from /var/log/mythtv/ and restart the services (or reboot).

---

### Post by korgman on 2009-02-19
> Check your root partition. It might have filled with error logs from mythtv, I know it happened to me once. Carefully delete log files from /var/log/mythtv/ and restart the services (or reboot).

I concur.  My mythfrontend.log file grew to about 300G one time.  Rendered the system practically unusable.

Run a 'df -k' from /
If you partition is 100%, check that /var/log/mythtv directory.

---

### Post by Caps18 on 2009-02-19
What I do is go to /var/lib/mythtv/recordings and watch a show using Xine from the normal OS.  Then, I copy the name of the video file, delete the file, make a new empty document and rename it to the original file name.  This allows there to be enough free space so you can restart the computer and everything will work again.  You will just have to delete the empty file from within MythTV so your database stays happy.

If you still have issues, I hoping I'm remembering correctly, if you can get to the desktop you can start the control center.  There is a button that will allow you to rebuild the database or fix the database or something.  I've had to use it once and it worked.  But that was when no programs or TV guide was showing up.

And one more thing, I would like to see this problem addressed in future versions of Mythbuntu.  This isn't an uncommon scenario, and it should have been fixed so that it fails without bringing the system down.

---

### Post by Hayesio on 2009-02-22
No, i've tried rebuilding the database via MCC but it hasnt worked.  I probably made the problem a lot worse: when the system initially went down, i rebooted and indiscriminately deleted all recordings from that directory and all logs from /var/log/mythtv to clear space on the HDD.

I've got know idea where to go from here!???

---

### Post by Hayesio on 2009-03-17
Ok, just a final word on this.  I've had to completely reinstall Mythbuntu as i couldn't fix the issue - but it isn't so bad because i wanted to put a bigger HDD in anyway.  It seems this issue has been addressed in Mythbuntu Intrepid Ibex (my new install).  It formates the HDD to allow only about 10GB for the file system and then allocates the rest of the drive to /var/lib/mythtv, thus if you run out of recording space, the file system can still be writen to. This is great, but, as others have mentioned, this still wont protect the system if it fills up with log files.

Regards to all,
Hayesio

---

### Post by Caps18 on 2009-03-18
Your system (at least the backend) will still crash if you fill up the recordings partition with TV shows.  It is a tricky problem to handle, but it's almost as if there should be a totally separate recordings partition that can't effect the OS or database at all if it is full and can't be written to.

---

### Post by newlinux on 2009-03-18
> **Caps18 said:**
> Your system (at least the backend) will still crash if you fill up the recordings partition with TV shows.  It is a tricky problem to handle, but it's almost as if there should be a totally separate recordings partition that can't effect the OS or database at all if it is full and can't be written to.

The extra disk space setting in myth allows you to set a specified amount of space available on each recording partition. It's in the backend setup, IRIC. If this is set, whenever myth records, it will make sure the amount of space you specified is available on that partition by deleting other recordings. This could help prevent the recordings filling up the partition problem. won't help if other things fill up the partition while myth isn't recording.

---

### Post by Caps18 on 2009-03-18
That might be the other problem with my system.  I don't let MythTV delete shows for me.  If I want to delete something after I watch it, I will do it.

I think I set that setting at 1 GB, so I was surprised the first time when 0 GB was available.

---

### Post by michwill on 2009-03-22
Hi All,

I've had the same problem.  In fact, over the last 2 weeks, I've reinstalled 3 times.  Granted, I record about 25 different shows (some with multiple viewings) every week.  That said, my HDD fills up rather quickly.  That said, my 2 main issues are as follows:


1) The box, for some reason, will delete some of my newest recordings even if I haven't watched them -- this despite most of these shows having a high recording priority.  I don't know why there's not a one-stop-shop for setting FIFO recording.  What am I missing?

2)  The box doesn't seem to delete fast enough as I've been forced to reinstall 3 times since going with Intrepid (Only had the issue twice in 6 mths with Hardy).


If there's something I'm missing or a quality general fix, I'm all ears.


Best.

---

### Post by newlinux on 2009-03-22
I record a ton of shows every week too (have 30 or so recording rules). I have many of them setup to keep maximum of 2 episodes and to delete oldest episode if I have two and another show is coming. Make sure to look at the storage options when scheduling a recording. You should be able to get your options where you want them so this doesn't happen. By default, myth should delete oldest programs first, if they are set to allow to autoexpire. I've never had the problem and I record many daily shows and other shows as well. My disks are always close to full though.

Check your liveTV recording age settings, auto expire settings, etc. 
You'll definitely want to make sure you have your global autoexpire settings where you want them:

[http://www.mythtv.org/wiki/User_Manual:Detailed_configuration_Frontend#Global_Auto_Expire_Settings](http://www.mythtv.org/wiki/User_Manual:Detailed_configuration_Frontend#Global_Auto_Expire_Settings)

You can also see what is scheduled to be deleted next in the system status.

I don't think recording priority has anything to do with when a file will get deleted. You might want to consider setting the reserved disk space setting I mentioned above to something reasonable to keep the disk from filling up.

Also, why does this cause you to have to reinstall? Do you not have a separate partition for recordings? The only thing that should get full from recordings if you have a separate partition is the recordings partition, which wouldn't hose your system partition.

What filesystem are you using for recordings? Do you have the delete recordings slowly option enabled?

---

