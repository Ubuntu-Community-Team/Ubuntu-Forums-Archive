---
title: "New MythTV Install:  Old Database restore problems?"
date: 2016-04-17
forum: Mythbuntu
---

### Post by mattlach on 2016-04-17
Hey all,

I am migrating my mythbuntu backend to a different physical server.

Previously I had a mythbuntu install from the ISO, but for a number of reasons this time I was forced to install MythTV onto Ubuntu manually.  [The page on the Mythbuntu webpage for Existing Ubuntu](http://www.mythbuntu.org/existing-ubuntu) is very light on details to say the least.

I started with a bare 14.04 server install, installed LXDE on the box, and then proceeded to install mythbuntu-control-centre and set up my desired settings for a dedicated backend box.

After this I proceeded to restore my old database using the mythconverg_restore.pl script as follows, and as can be seen below, it claims to have successfully restored the database.

```

./mythconverg_restore.pl --drop_database --create_database --directory /home/mythtv/scripts --filename mythconverg-1317-20160414200009.sql

Successfully restored backup.

```

The problem is, that when I launch MythTV Backend Setup from the menu, it appears as if I am dealing with an empty database and a brand new system.   None of my old information is in the backend setup screen.

I'm going to go ahead and guess that this somehow has to do with account or database permissions, but this is not my area of expertise, so I don't have a clue where to start.  I am VERY weak on MySQL (or databases in general) and linux accounts and groups usually get me confused as well.  For MythTV I typically just rely on the scripts.

In setting up my new box, I created a user named mythtv (just like on the default mythbuntu install disk) but I ahvent' given it any special permissions or group memberships (except the sudo group, as I need it to manage the box)  Do I need to?

```

$ groups mythtv
mythtv : mythtv dialout cdrom sudo audio video

```

I read somewhere that the database also has some sort of password associated with it.  I've never really used this password.  All of my frontends just worked automatically, so I never had to.  I don't really know what the old one might have been.   Is this a problem?    \

Actually, I have found a password, a seemingly random 8 character alphanumeric string in one of my MythTV frontends.  Is this the database password?   What do I do with it?

I'd appreciate any help I can get!

Thank you,
Matt


(Cross-posted on the MythTV Forums in order to reach maximum eyeballs!)

---

### Post by yonkiman on 2016-04-18
I had similar issues trying to use mythbuntu-control-centre to install everything.  I ultimately started over (in my case with a fresh 16.04 install) and per jhoyt's suggestion installed mythbuntu-desktop instead of mcc and let mythbuntu-desktop install everything else.  That went much better.  (Details in [this thread]("http://ubuntuforums.org/showthread.php?t=2319897") but that's the gist of it).  

I *may* have installed mysql before mythbuntu-desktop - I can't remember and I'm not sure if it matters.  I also may have had to tweak the mythconverg database a little bit (per [this page]("https://www.mythtv.org/wiki/Build_from_Source#Creating_the_mythtv_user")'s instructions under MythTV Database Setup).  I don't *think* you'll need any of that if you go with mythbuntu-desktop followed by **mythconverg_restore.pl --drop_database --create_database**, I just have a terrible memory and can't remember what worked when.

One thing I did to save time if things went badly was to make an image of my system after each successful major step (base 16.04 install, after I installed and tweaked favorite utilities, after I installed mythbuntu-desktop, after I restored my database, etc.).  It didn't take too long to make each backup (I just booted off another drive and used **dd if=/dev/sda of=/mnt/backup/backup_0x.iso bs=1M count=31000** for my 30GB partition - substitute all values for your system's and of course be very careful with dd) and it allowed me to get my system back to a pre-fubar state in 5-10 minutes if something didn't work (I kept breaking mysql and not being able to get it back).

But most if not all of my issues occurred when I was trying to use mythbuntu-control-centre to install everything.  You'll probably be successful if you just start with mythbuntu-desktop instead of mcc.

---

### Post by mattlach on 2016-04-19
> **yonkiman said:**
> I had similar issues trying to use mythbuntu-control-centre to install everything.  I ultimately started over (in my case with a fresh 16.04 install) and per jhoyt's suggestion installed mythbuntu-desktop instead of mcc and let mythbuntu-desktop install everything else.  That went much better.  (Details in [this thread]("http://ubuntuforums.org/showthread.php?t=2319897") but that's the gist of it).  

I *may* have installed mysql before mythbuntu-desktop - I can't remember and I'm not sure if it matters.  I also may have had to tweak the mythconverg database a little bit (per [this page]("https://www.mythtv.org/wiki/Build_from_Source#Creating_the_mythtv_user")'s instructions under MythTV Database Setup).  I don't *think* you'll need any of that if you go with mythbuntu-desktop followed by **mythconverg_restore.pl --drop_database --create_database**, I just have a terrible memory and can't remember what worked when.

One thing I did to save time if things went badly was to make an image of my system after each successful major step (base 16.04 install, after I installed and tweaked favorite utilities, after I installed mythbuntu-desktop, after I restored my database, etc.).  It didn't take too long to make each backup (I just booted off another drive and used **dd if=/dev/sda of=/mnt/backup/backup_0x.iso bs=1M count=31000** for my 30GB partition - substitute all values for your system's and of course be very careful with dd) and it allowed me to get my system back to a pre-fubar state in 5-10 minutes if something didn't work (I kept breaking mysql and not being able to get it back).

But most if not all of my issues occurred when I was trying to use mythbuntu-control-centre to install everything.  You'll probably be successful if you just start with mythbuntu-desktop instead of mcc.


Thanks for your suggestions.

I actually wound up starting over and installing the desktop package as well.   This worked much better, but when restoring the config I still had the same problem, I logged in and my configuration was gone.

So this time I tried just imaging the drive of the old mythbuntu backend over.  Same problem again!   What gives?

Turns out, that since I was changing the IP addresses of my tuners at the same time as I was doing this transition, the backend config couldn't find them, and didn't display them in the setup, giving it the appearance as if all of my settings were gone.  

The expected behavior here would have been to show the old IP addresses, and display a "can not find tuner" message or something like that, but instead the backend configuration page shows nothing, as if they were never set up in the first place.

My recordings and the database were actually there, I just had to reconfigure the tuners again, and connect them to my schedulesdirect inputs.

One tiny kink.   The backend configuration might not display the turners in the list if they change IP's, but they are still in the database and show up everywhere else as "disconnected tuner", which can be kind of annoying.  In order to get rid of this, I had to go back in and choose the "delete ALL tuners" option, and reenter them again.

Now, my only outstanding problem since the transition is that the MythTV backend no longer starts when the machine boots.   I have to manually start it.   I'll have to figure out how to deal with that.

---

### Post by yonkiman on 2016-04-20
> **mattlach said:**
> Now, my only outstanding problem since the transition is that the MythTV backend no longer starts when the machine boots.   I have to manually start it.   I'll have to figure out how to deal with that.

See if this helps:  [http://ubuntuforums.org/showthread.php?t=2319953](http://ubuntuforums.org/showthread.php?t=2319953)

Examine your config files at /home/fred/.mythtv/config.xml /home/mythtv/.mythtv/config.xml and make sure they are correct and matching.

---

### Post by mattlach on 2016-04-24
> **yonkiman said:**
> See if this helps:  [http://ubuntuforums.org/showthread.php?t=2319953](http://ubuntuforums.org/showthread.php?t=2319953)

Examine your config files at /home/fred/.mythtv/config.xml /home/mythtv/.mythtv/config.xml and make sure they are correct and matching.

Thanks for that recommendation.   Unfortunately that isn't it for me.

/home/myth/.mythtv/config.xml; and
/home/mythtv/.mythtv/config.xml

are both symlinks pointing towards /etc/mythtv/config.xml

/etc/mythtv/config.xml is owned by the user mythtv, so it certainly can read and write to it properly.

I don't fully understand how in a default installation the mythtv backend automatically starts on boot, which makes it difficult to troubleshoot.  Is it run as a service?

Any info you can provide would be greatly appreciated!

--Matt

---

