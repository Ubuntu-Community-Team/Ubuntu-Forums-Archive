---
title: "[SOLVED] Myth could not connect to the database"
date: 2007-10-25
forum: Mythbuntu
---

### Post by Meph1st0 on 2007-10-25
I just went through the LVM sticky walk through.  Despite the ugly post I made in there about being unable to mount the volume to /mnt/sdb1 the process went okay.  I was able to copy all of /var/lib into my new lvm partition and then extend the volume to include the left over space on /dev/sda.  df -h show the following:

```
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             9.2G  1.5G  7.3G  17% /
varrun                506M  216K  506M   1% /var/run
varlock               506M     0  506M   0% /var/lock
udev                  506M  104K  506M   1% /dev
devshm                506M     0  506M   0% /dev/shm
lrm                   506M   34M  472M   7% /lib/modules/2.6.22-14-generic/volatile
/dev/mapper/vg-lib    585G   81G  504G  14% /var/lib
```

I've verified that all of the data in my previous /var/lib is in my new volume.  But when I try to open up mythfrontend I get the backend setup tool.  I choose English and then it says that "Myth could not connect to the database"

I can verify that the mythconverg database exists in /var/lib/mysql.  If I attempt to run /etc/init.d/mysql start it fails.

Is there some sort of repair utility I can run?  Or is there some mysql log file I can look into to see why it's failing?

---

### Post by superm1 on 2007-10-25
How did you copy over your old stuff on the old drive?  Perhaps permissions didn't copy over properly.

---

### Post by Meph1st0 on 2007-10-25
I think you're right.  When I tried the cp -p -r /var/lib/* /mnt/sdb1 command it seemed to fail.  It got as far as copying 8 GB and then stopped.  I waited for several hours for it to copy all the files but it never got past 8 GB.

I ended up rebooting and then using gksudo thunar at the desktop and selecting all the files and then copying them to /mnt/sdb1.  

This wouldn't surprise me if this were bad.  I get the feeling you're going to tell me that I've got to start all over.

---

### Post by superm1 on 2007-10-25
> **Meph1st0 said:**
> I think you're right.  When I tried the cp -p -r /var/lib/* /mnt/sdb1 command it seemed to fail.  It got as far as copying 8 GB and then stopped.  I waited for several hours for it to copy all the files but it never got past 8 GB.

I ended up rebooting and then using gksudo thunar at the desktop and selecting all the files and then copying them to /mnt/sdb1.  

This wouldn't surprise me if this were bad.  I get the feeling you're going to tell me that I've got to start all over.

Yeah if you just did cp, and not sudo cp, you won't have gotten them all copied over.

---

### Post by Meph1st0 on 2007-10-25
Well prior to doing the CP I had done sudo -i and entered my password.  I believe I had the # prompt.  So let's just assume I hadn't copied everything over (now I'm really wondering) do I just need to start over now?  format everything? or just recreate the database?  or can I even recreate the database?

---

### Post by superm1 on 2007-10-25
> **Meph1st0 said:**
> Well prior to doing the CP I had done sudo -i and entered my password.  I believe I had the # prompt.  So let's just assume I hadn't copied everything over (now I'm really wondering) do I just need to start over now?  format everything? or just recreate the database?  or can I even recreate the database?

If you've still got the old files, i'd say use rsync

```
sudo rsync -avz /mnt/oldpath/ /mnt/newpath/
```

Be careful with the trailing slashes though.

That will update all the permissions and any missing or incomplete files.

---

### Post by Meph1st0 on 2007-10-25
If I've already extended the volume to occupy my old /var/lib partition and I now have only one large /var/lib folder how do I use that command?

sudo rsync -avz /var/lib /var/librecover something like that?

---

### Post by superm1 on 2007-10-25
Keep the trailing slashes and that should be right.  I always mix them up, but I think you are supposed to keep them in this case.

---

### Post by Meph1st0 on 2007-10-26
Ok, so I used sudo rsync -avz /var/lib/ /var/librecover/ and it looked like it was working but then I got the following error messages and it stopped:

rsync: writefd_unbuffered failed to write 16385 bytes [sender]: Broken pipe (32)
rsync: connection unexpectedly closed (143216 bytes received so far) [sender]
rsync error: error in rsync protocol data stream (code 12) at io.c(454) [sender=         2.6.9]

I went into /var/librecover and I can see that it didn't recover everything.  It's missing the whole mythtv folder and the mysql folder.  This is bad right?

---

### Post by superm1 on 2007-10-26
> **Meph1st0 said:**
> Ok, so I used sudo rsync -avz /var/lib/ /var/librecover/ and it looked like it was working but then I got the following error messages and it stopped:

rsync: writefd_unbuffered failed to write 16385 bytes [sender]: Broken pipe (32)
rsync: connection unexpectedly closed (143216 bytes received so far) [sender]
rsync error: error in rsync protocol data stream (code 12) at io.c(454) [sender=         2.6.9]

I went into /var/librecover and I can see that it didn't recover everything.  It's missing the whole mythtv folder and the mysql folder.  This is bad right?
Dying hard drive possibly?

---

### Post by apauna on 2007-10-26
> **superm1 said:**
> Dying hard drive possibly?

Sorry to hear that you are having these troubles. So you added your original partition to the lvm?

So after the reboot in step 11 you were not in Myth? 
I may want to add some additional testing steps to the original how-to so people fully test myth before going ahead and adding sda3 to lvm. That way if there is troubles they can back out of the lvm procedure.

I have used utilities at work that wipe the disk completely by writing zeroes to the entire drive. GWSCAN is one that I have used in the past. Maybe a disk wipe on bad disk will correct the issues you are having. That is unless this is your drive with root on it. :(

---

### Post by apauna on 2007-10-26
Here is something I found on the net:
[http://www.linuxquestions.org/questions/linux-software-2/how-to-uninstall-ubuntu-581501/]("http://www.linuxquestions.org/questions/linux-software-2/how-to-uninstall-ubuntu-581501/")
> Boot with a live CD, like knoppix, and use dd:

dd if=/dev/zero of=/dev/sdb bs=4k conv=notrunc,noerror

I your case Mythbuntu CD should allow you to do this.

---

### Post by Meph1st0 on 2007-10-26
awright, well.  It wasn't a big deal to go ahead and format and reinstall.  I only had a few recordings and all my music and videos are still stored on my server.  I had it back up and running within an hour thanks to your efforts in releasing an awesome mythbuntu install.  Now that I have practically nothing in my /var/lib partition I'm going to try again.

I would hate to think that I have a failing hard drive as both of them are less than a month old.  From the time I purchased them obviously, they could have sat on the shelf for months, but you know what I mean.

I'll let you know how it goes on attempt number two.  Thanks for all your help.

---

### Post by Meph1st0 on 2007-10-26
Alright, gentlemen.  I don't know what I did wrong the first time.  But the second attempt worked like a charm.  I now have a 585 GB /var/lib volume.  I couldn't be more pleased.  How many DVDs do you think that'll hold? 10? 15? j/k

Let's see here...what can I break next?

Thanks again for all your help.

How do I mark this thread as solved?

---

