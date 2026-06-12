---
title: "Any Ardour Update for UbuntuStudio in Sight?"
date: 2007-08-01
forum: Multimedia Production
---

### Post by aavera on 2007-08-01
Ardour has published another update with a big bucket of bug fixes and feature enhancements.

From ardour.org:  
Ardour 2.0.4 released
Submitted by paul on Tue, 2007-07-31 13:04. :: Articles
Squeaking just before of the end of July, the Ardour project brings you release 2.0.4 ( tarball, DMG to follow), another mix of important bug fixes with some great new features. Read more below for details ... 

I'm hoping that before long I will receive a notification that an update is available and my update manager will take care of upgrading Ardour for me to the latest 2.0.4.  Has anyone maintaining the official UbuntuStudio repository looked into repackaging the newest version of Ardour?  Since the initial release of Ardour 2.0 there have been a BUNCH of bug fixes, and I'd like to know that my system will soon get upgraded automatically.

Anything I can do to help this process along?

---

### Post by stmiller on 2007-08-02
I'm sure it's coming shortly. You can ask in 

#ubuntustudio on irc.freenode.net

---

### Post by aavera on 2007-08-03
Okay, I joined the IRC chat for UbuntuStudio support.  From the replies I received, it sounded like keeping these packages up to date isn't a very high priority.

I received one reply from KuZo which was very helpful.  That was to download the latest Ardour version's deb package from : [ftp://musix.ourproject.org/pub/musix/deb/](ftp://musix.ourproject.org/pub/musix/deb/). 

It worked.  I 'did' have to create a new launcher that pointed to just 'ardour2' rather than /usr/bin/ardour2.  Using the old link launched the outdated version of Ardour.

-Andy

---

### Post by djxcon on 2007-08-04
Hey, an even newer version was released yesterday, version 2.0.5.  I have always been able to compile Ardour 2 from source and this is one release that seems to have an issue with flac on my system (Ubuntu 7.04).  Lots of errors on scons regarding flac and so far the only advice I have seen is to remove flac from my system.  Has anyone been able to compile the newest version? If so, please let me know how you avoided this message: "scons: *** [libs/libsndfile/src/flac.os] Error 1"

Thanks!

---

### Post by Jussi01 on 2007-08-04
IIRC, the latest build of ardour will be in gutsy, however there is a problem with scons atm. So as soon as scons is fixed, then ardour will go into the gutsy repos.

---

### Post by MetalMusicAddict on 2007-08-04
Packages in Ubuntu don't get version updates in a given release unless its to fix a critical bug. That being said, If you're on Feisty you will have to do it yourself or wait until Ubuntu Studio-Gutsy.

> **djxcon said:**
> Hey, an even newer version was released yesterday, version 2.0.5.  I have always been able to compile Ardour 2 from source and this is one release that seems to have an issue with flac on my system (Ubuntu 7.04).  Lots of errors on scons regarding flac and so far the only advice I have seen is to remove flac from my system.  Has anyone been able to compile the newest version? If so, please let me know how you avoided this message: "scons: *** [libs/libsndfile/src/flac.os] Error 1"

Thanks!
I believe I saw you talking about this issue on IRC. I'm unsure why this is happening. I know its not just a Ubuntu issue because other distros have the problem as well.

---

### Post by djxcon on 2007-08-04
> I believe I saw you talking about this issue on IRC. I'm unsure why this is happening. I know its not just a Ubuntu issue because other distros have the problem as well.

Yes, I was looking for support in IRC since #Ardour rocks!  Seriously, a big THANK YOU for all of the help you folks have given me.  To date, I have been able to compile all versions of Ardour from the tarball but this one is definitely causing me an issue.  I still have 2.0.4 up and running and I really dig the new light theme.

---

### Post by thorgal on 2007-08-05
check my reply to that guy at [http://ardour.org/node/1157](http://ardour.org/node/1157)
I explain (in a bit messy way) how to compile ardour 2.0.5. Could be that this was good enough for me only ... try it :)

---

### Post by eric71 on 2007-08-06
It seems that 2.0.5 is now available at [www.getdeb.net](www.getdeb.net)

Haven't tried it, but I've never had a problem with deb's from them.

---

### Post by Jussi01 on 2007-08-08
Hi, Ive just had a report that ardour 2.05 has been uploaded into the gutsy repos and is working. So yes, as soon as gutsy comes out you will be able to use it :)

---

