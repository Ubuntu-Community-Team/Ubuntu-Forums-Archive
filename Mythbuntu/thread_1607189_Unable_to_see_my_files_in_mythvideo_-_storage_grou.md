---
title: "Unable to see my files in mythvideo - storage group on external HD"
date: 2010-10-27
forum: Mythbuntu
---

### Post by sinkyboy2000 on 2010-10-27
[INDENT]This is probably something very straight forward, but I'm more or less a total noob to linux and mythtv (got it running well enough previously - but didn't use storage groups).

In mythtv-setup I have two directories listed for Video Storage Groups. The first is /var/lib/mythtv/videos - which is on an internal harddrive. The second is /media/Iomega HDD/videos - which is on an external hard drive. 

When I scan for changes in mythvideo it only brings up the files in the first directory. I can't seem to work out why. I have double checked that I have entered the path correctly. I wonder whether it has anything to do with the space in the path name?

I only added the first directory to test. I initially only defined the SG on the external HD.

Have searched on the problem but can't find what I've done wrong. Help would be appreciated. [/INDENT]

---

### Post by bance on 2010-10-27
Maybe mount your external drive under /var/ lib/myhttv/videos/<somethinghere> or include the path /media/IomegaHDD/videos in storage groups! but I'm a noob as well, but I think that's how storage groups work!

Hope I haven't sent you down the wrong path (sic)

good luck, enjoy mythtv

---

### Post by tgm4883 on 2010-10-27
Not sure if it is a space issue, as I don't have spaces in my paths. Sounds more like a permissions issue. What permissions are on that drive?

---

### Post by sinkyboy2000 on 2010-10-28
> **tgm4883 said:**
> Not sure if it is a space issue, as I don't have spaces in my paths. Sounds more like a permissions issue. What permissions are on that drive?
 
Ah Ha!  Permissions do seem to be the problem.  Now to work out how to change permissions on an external NTFS formatted drive!

---

### Post by LowSky on 2010-10-28
you cant change permission on a NTFS drive. windows doesn't use permissions the same way

I do think the space is the issue and a smimple fix
If you right the addresss out like this it should be seen correctly:
```
'/media/Iomega HDD/videos'
```

---

### Post by nickrout on 2010-10-29
look at the output of the mount command to see what the current mount options for your drive are.

Then take a look at man  mount.ntfs for details on how to set the options.

It may be the space, rename the drive to something without a space.

---

