---
title: "Was there a major update today?  This Week?"
date: 2008-03-13
forum: Mythbuntu
---

### Post by volkswagner on 2008-03-13
I had a strange thing happen today.  I have been running updates regularly.  Today while messing with my laptop running UUE 1.6 I tried connecting to my master-backend (Mythbuntu 7.10AMD64).  I got an error that my laptop was using protocal version 40 and not compatible with version 31 running on my backend.  I ran update manager and it said my system was up to date.  I ran update manager again, this time I clicked check and it came up with 51 available updates (many for myth).  Is this a possible bug?  Or maybe the updates were avail for a few days?

How do I check my current version of mythtv?

```
mythtv -v
mythtv -V
```

Both of the above commands want to start mythtv.
```

mythtv version
mythtv -version
```

Don't work either.

I also noticed the update manager wanted to use the install CD.  I was pretty sure this was commented out by myself earlier.  I had to comment it out again.

Wierd?

I am pretty sure my updates were way behind.  I remember folks commenting about the clock on the main page. I just got it today.  It also added the full date to my VFD on Antec Fusion.  Things just keep getting better.

:guitar:

---

### Post by murbanci on 2008-03-13
> **volkswagner said:**
> I had a strange thing happen today.  I have been running updates regularly.  Today while messing with my laptop running UUE 1.6 I tried connecting to my master-backend (Mythbuntu 7.10AMD64).  I got an error that my laptop was using protocal version 40 and not compatible with version 31 running on my backend.  I ran update manager and it said my system was up to date.  I ran update manager again, this time I clicked check and it came up with 51 available updates (many for myth).  Is this a possible bug?  Or maybe the updates were avail for a few days? 

Yes, there was an update to MythTV from version 0.20 to 0.21 therefore, there are quite a few packages to update.

> 
How do I check my current version of mythtv?

```
mythtv -v
mythtv -V
```

Both of the above commands want to start mythtv.
```

mythtv version
mythtv -version
```

Don't work either.


The only way that I know to check the installed version of myth is to open Symantic package manager and look at the installed version.  Im sure that there is a way to do it on the command line, but im not sure about how.

---

### Post by sgunther on 2008-03-13
> mythbackend --version
Will tell you your backend version.

Earlier this week MythTV 0.21 was rolled out on the weeklybuilld update link.  If you have backports enabled you will now see it.  It will likely take a;
> 
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade

To get the full upgrade.

Some would say.... If it is not broke don't fix it...

If you are happy with 0.20 and the new features are not needed /wanted I would wait a little unless you are comfortable working through some bugs...

---

### Post by volkswagner on 2008-03-13
OK, I am not sure why th 51 updates didn't show up earlier.

Now I am glad to be running .21, it seems my wifi connected laptop running UUE 1.6 is getting much better PQ and frame rates when viewing live TV.   :)

I will now have to go to my slave BE/FE and update so they are all on .21, hope it goes well.

After the update I lost the preinstalled themes.  I had to manually get the retro theme I liked.  Time will tell if all else is working.

Does anyone know what config files get overwritten during the update?

I noticed some configurations were lost.  Small items like preferred date (short form) in setup.

I think there was a prompt to keep my old config or overwrite.  I was afraid to not overwrite, thought it may cause compatibility issue?

---

### Post by JPurdy on 2008-03-14
No need to worry about overwrites - if you choose not to overwrite, the new configuration file will be in the same directory with a -dkpg-new.  If you do choose to overwrite, the old configuration will be in the same directory (w/ -dpkg-old, I believe).  Either way, you can later analyze the differences in more detail and incorate the new settings.

---

