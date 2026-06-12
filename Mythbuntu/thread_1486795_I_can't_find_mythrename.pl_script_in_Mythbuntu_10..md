---
title: "I can't find mythrename.pl script in Mythbuntu 10.04"
date: 2010-05-18
forum: Mythbuntu
---

### Post by brian_hayward on 2010-05-18
I just installed Mythbuntu 10.04 and now my recording directory is getting full.  I want to use the mythrename.pl to rename all my recordings so i can off load my recordings onto my laptop.  I can not find the script in any of the directories that are listed when i search for the script online.  I used it on Mythbuntu 9.10 but i can't remember how i got it.  Any help is greatly appreciated.  Thanks.

---

### Post by Neon Dusk on 2010-05-18
mythrename.pl has been renamed to mythlink.pl in myth 0.23. You should be able to find the script in /usr/share/doc/mythtv-backend/contrib/user_jobs/

---

### Post by brian_hayward on 2010-05-19
Thank you for the response, however the mythlink.pl doesn't do what i want it to do.  in my search for the mythrename.pl i did some reading about the mythlink.pl.  from what i read, the mythlink.pl makes symlinks to my episodes rather than renaming all the files to a readable form.  i need the files renmaed by episode name because i offload all my episodes on to my laptop so i can watch them on the road.  

I finally found the mythrename script so if anybody else looking for the mythrename.pl here is a link to where i found it.  However, if you use the MythTv frontend to watch your recordings DO NOT use the mythrename.pl...i use it because i use a different frontend on a separate computer to watch my recordings.  

[http://svn.mythtv.org/trac/browser/branches/release-0-21-fixes/mythtv/contrib/mythrename.pl?format=txt]("http://svn.mythtv.org/trac/browser/branches/release-0-21-fixes/mythtv/contrib/mythrename.pl?format=txt")

---

### Post by brian_hayward on 2010-05-19
hit the wrong button and had a double post...this is my deleted post..

---

### Post by Neon Dusk on 2010-05-19
mythrename.pl has been removed from the latest mythTV version because if you didn't use the --link option it would rename the original recording files which could cause problems

[mythlink.pl](http://svn.mythtv.org/trac/browser/branches/release-0-23-fixes/mythtv/contrib/user_jobs/mythlink.pl) is the same as mythrename.pl except it won't rename the original files, it creates symlink with a human readable name

Edit: See [here](http://svn.mythtv.org/trac/changeset/23474/trunk/mythtv/contrib/user_jobs/mythrename.pl) for when file renaming was removed.

---

