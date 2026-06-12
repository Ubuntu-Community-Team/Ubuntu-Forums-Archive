---
title: "Apache site 403 forbidden error... running on external hard drive"
date: 2010-10-27
forum: Networking &amp; Wireless
---

### Post by xanaftp on 2010-10-27
**I APOLOGIZE IF I HAVE POSTED THIS IN THE WRONG AREA. THIS IS A BEST GUESS. MOVE IF NECESSARY PLEASE.**

Hello! I am trying to run a website on Apache2 using an external hard drive mounted to Ubuntu as "Webserver". Unfortunately, everything I've tried has failed. I continue to receive a 403 forbidden error message when trying to access the website.

The reason I want to run this under **/media/Webserver/www-data/www** is because that hard drive has 400GB, compared to only 15GB on the hard drive my Ubuntu installation is on.

Is there a way to configure Apache2 to access this website on that directory, OR, configure Ubuntu to allocate additional storage space to that external hard drive when the hard drive Ubuntu is running on gets full, aka "connect the two hard drives together"?

Here's what I have tried:

-creating the virtual website by copying the Default website and changing the directories inside that Default file, then renaming Default to xanaftp and applying commands sudo a2dissite Default && a2ensite xanaftp. Then restarting Apache2.

-chmodding recursive directory /media/Webserver/www-data/* AND /media/Webserver/www-data/www/* to 0755.

-changing the folder owner to root, www-data, and me. Applying the same to enclosed files.

-changing the group to root and www-data. Applying to all enclosed files.

-setting all permissions to creating reading and writing. Applying permissions to all enclosed files.

-repeating EVERYTHING listed above under a root account.



Does anyone know what I can do? Please respond ASAP. Thank you.

---

### Post by xanaftp on 2010-11-07
Sorry for bumping this topic when it's only a week old, but my Ubuntu freespace is down to 244MB, and I really need to find a way to host my website on the external hard drive so I can move all the website documents to that drive and free up Ubuntu space.

I have not been able to try any new methods within the last week because I have not been able to find any new methods to try.

Help would greatly be appreciated! Thank you.

Note that I will not bump this topic anymore until either it is at least 30 days old or something urgent comes up regarding this topic.

---

