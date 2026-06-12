---
title: "MythTV:  Changing the record path"
date: 2007-10-02
forum: Multimedia &amp; Video
---

### Post by dmakfan on 2007-10-02
Hello,
I tried to change the record path for my MythTV backend.  It was originally at the default of /var/lib/mythtv/recordings.  However, when I changed it to another path, /media/disk/mythtv/recordings, which is another drive with a lot more space, my front end will no longer connect to it when I try and watch TV.   (front end is on the same machine).

Everything looked fine when I exited the mythtv backend setup though (i.e. it didn't complain about being able to write the .test file after I had changed the path).  

The actual error that the front end brings up is "Could not connect to the mater backend server -- is it running? Is the IP address set for it in the setup program correct?".  

If I go back into the backend setup, and the only thing I change is the path back to /var/lib/mythtv/recordings, everything works again.  Of course, the server is started and stopped everytime I make changes to the backend, and mythfilldatabase is run as well.

Help!
Thanks,
Dave

---

### Post by dmakfan on 2007-10-04
A little more information.  From my backend log file:

2007-10-04 18:38:39.195 Enabled verbose msgs:  important general
/media/disk//nfslockfile.lock: Permission denied
Unable to open lockfile!
Be sure that '/media/disk/' exists and that both
the directory and that file are writeable by this user.

What does this lockfile do?  Is it a directory permissions thing?   What login needs to be able to access the directory?

Whenever I try and modify the permissions on it, Ubuntu says I don' thave permission to do it.  I don't know if I have to be root or not...

---

### Post by Scorpuk on 2007-10-05
If you don't mind using the whole of the new drive to store your recordings you could mount the drive here:

/var/lib/mythtv/recordings


You would need to make sure that the folder /var/lib/mythtv/recordings was completely empty before mounting. ie copy all the files to the new drive.


I think the command to mount it there would be, assuming new drive is sdb1 (change to suit whatever it is for you)

sudo mount /dev/sdb1 /var/lib/mythtv/recordings


MythTV will be none the wiser that the folder is actually a new hard drive and carry on regardless. :-)



Good luck and if you are unsure about any step then post back here and either myself or someone else should be able to help.


EDIT:

If this works for you, and it should, then you could add this mount to the fstab file to make ubunto mount the drive like this everytime it boots up.


```
sudo cp /etc/fstab /etc/fstab-mythtv-mount
```

```
sudo gedit /etc/fstab
```

and then add the new mount in. I think it will be in the following way, but double check with how drives are mounted already in your fstab. Again if any probs just drop a line here.

```
/dev/sdb1 /var/lib/mythtv/recordings     ext3      defaults,errors=remount-ro    0     1
``` <- assuming you are using ext3 file system.

---

### Post by MisanthropicOne on 2007-10-13
This worked like a charm.
I shut down the MythBackend, then MySQL, copied everything to the new drive, changed the name of /var/lib/mythtv/recordings/ to /var/lib/mythtv/recordingsbak/ made a new /var/lib/mythtv/recordings/ folder so there'd be an empty one there and still preserve my old stuff in case this little experiment didn't work out. Then I edited my fstab with the appropriate changes (sda1, jfs) rebooted, and pow, everything worked perfectly. Only now I have quite a few more hours on my shiny new 500 gig drive than I did on my 100 gig partition.

Thank you, Scorpuk!

---

