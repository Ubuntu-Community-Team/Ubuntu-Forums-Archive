---
title: "HELP -- gimp No longer Starts"
date: 2008-07-24
forum: Multimedia Software
---

### Post by Maverick88 on 2008-07-24
I just installed Ubuntu Hardy Heron 8.04.1 a week ago on a x86 PC.  And gimp was working just fine.

But now when I start gimp, I get this error:

symbol lookup error
undefined symbol: gimp_micro_version

I tried to reinstall gimp.  That made no difference.

Any ideas?  I am really stumped and would like to get gimp working.

RobK

---

### Post by insineratehymn on 2008-07-24
[https://answers.launchpad.net/ubuntu/+question/19190](https://answers.launchpad.net/ubuntu/+question/19190)

That is **a** solution... unfortunately that one is to download an older version and install it over, but if you have some kind of added goodies, they may not comply...

Google doesn't really give much else... Have you submitted this bug to Gimp?

---

### Post by Maverick88 on 2008-07-24
That does not seem to work,

But I found the package that broke gimp.

If you install AWN from this rep  "deb [http://ppa.launchpad.net/reacocard-awn/ubuntu](http://ppa.launchpad.net/reacocard-awn/ubuntu) hardy main", AWN will break gimp.

See [http://ubuntuforums.org/showthread.php?t=762363](http://ubuntuforums.org/showthread.php?t=762363)

You can easily verify that this is the problem.

1.  Boot off the Hardy Heron 8.04.1 Live CD.  
2.  Add the repos:

deb [http://ppa.launchpad.net/reacocard-awn/ubuntu](http://ppa.launchpad.net/reacocard-awn/ubuntu) hardy main
deb-src [http://ppa.launchpad.net/reacocard-awn/ubuntu](http://ppa.launchpad.net/reacocard-awn/ubuntu) hardy main

3. sudo apt-get update

4.  sudo apt-get install avant-window-navigator-bzr awn-core-applets-bzr awn-manager-bzr

5.  Try to run gimp.  It will not run.  If you run gimp from the terminal, you will see the gimp_micro_version undefined symbol error.

Now try to get gimp to run again.  I can't!
I tried to COMPLETELY uninstall the following:

awn (using the instructions on the [http://ubuntuforums.org/showthread.php?t=762363](http://ubuntuforums.org/showthread.php?t=762363))
gimp
gimp-data
libgimp.  

I even manually deleted the .gimp-2.4/ folder in my home directory.  Then deleted the AWN third party rep sources and reinstalled gimp.  I still see the error.

Any other ideas?

Rob

---

### Post by insineratehymn on 2008-07-24
Does it work without AWN?

If so, can you try to install a different version of AWN?

---

### Post by Maverick88 on 2008-07-24
I figured out the problem and the solution!!

The latest version of AWN does appear to break the Gimp 2.4.5 in Hardy Heron 8.04.1.  

To get the gimp working again, you need to uninstall AWN.  And then Uninstall BOTH gimp and gimpshop (if gimpshop is also installed).  Then install gimp and afterwards install gimpshop.

Here are the details.

1.  Uninstall AWN using the instructions from [http://ubuntuforums.org/showthread.php?t=762363](http://ubuntuforums.org/showthread.php?t=762363)

2.  Make sure you remove the third party AWN repos (as described in [http://ubuntuforums.org/showthread.php?t=762363](http://ubuntuforums.org/showthread.php?t=762363) ) and do a "sudo apt-get update"

3.  Completely uninstall gimp, gimp-data, gimp-data-extras, libgimp2.0, xsane, xsane-common AND gimpshop.  (This will also uninstall ubuntu-desktop, gimp-gnomevfs and gnome-python).

4. Reinstall the following:

gimp
gimp-data
gimp-data-extras
gimp-gnomevfs
gimp-python
libgimp2.0
ubuntu-desktop
xsane
xsane-common

5.  If you want to re-install gimpshop, go for it BUT ONLY after you have first installed gimp.

6. Pray.  Both gimp and gimpshop should work.

P.S.  You might be able to get away with uninstalling fewer packages but this works!

---

### Post by Maverick88 on 2008-07-24
Yes I found an easier way.

1. Uninstall AWN using the instructions from [http://ubuntuforums.org/showthread.php?t=762363](http://ubuntuforums.org/showthread.php?t=762363)

2. Make sure you remove the third party AWN repos (as described in [http://ubuntuforums.org/showthread.php?t=762363](http://ubuntuforums.org/showthread.php?t=762363) ) and do a "sudo apt-get update"

3. COMPLETELY uninstall gimpshop.

4. Reinstall gimp amd libgimp2.0

5. Optional -- reinstall gimpshop

6.  Pray..

---

### Post by moonbeam on 2008-07-24
well according to the bug:  [https://bugs.launchpad.net/awn/+bug/251596](https://bugs.launchpad.net/awn/+bug/251596)

It appears Debian packages were used for gimpshop.  I'll leave it for the rest of you to determine if awn should be saddled with the blame in this case :-)

---

### Post by moonbeam on 2008-07-24
Following up on the gimpshop issue I'l paste the thoughts of awn dev malept which were prepared for the bug opened on our bugtracker ( [https://bugs.launchpad.net/awn/+bug/251596](https://bugs.launchpad.net/awn/+bug/251596) ).  It is fair to say, this is the consensus among those of us who have looked at the issue.

-----

As I understand it, the gimpshop package is for Debian, not Ubuntu.  What I would do is look for someone who is knowledgeable about building on PPAs and ask them to build a version.  Apparently someone has been attempting to build it for intrepid, not hardy.

Additionally, said PPA package should replace the gimp package(s).  Installing both gimp and gimpshop at the same time creates problems because they both install libraries with the same name, albeit in different locations.  However, when gimp is loaded, due to the way that the executable loads libraries, the gimpshop libraries are loaded for it.  This breaks gimp loading partially because the gimpshop debian package is 2.2.x and the hardy version of gimp is 2.4.x, and I assume that the gimp broke binary library compatibility between 2.2.x and 2.4.x.  So, since the gimp can't find functions/variables that were in 2.4.x but not in 2.2.x.

I think the reason that you're seeing this behavior *after* Awn is installed is because the Awn packages regenerate the library cache, whereas I doubt that the gimpshop package does this (especially when you use dpkg to install it).

I'm marking this invalid because I believe that this doesn't have anything to do with Awn, but rather, it's a problem with installing gimpshop.

---

### Post by Maverick88 on 2008-07-24
After more testing and investigation, it looks like AWN is not to blame. Yes, the installation of AWN was the start of the gimp not working.  But the installation of ANY other package would also cause the gimp not to work. Why?  Well, apt-get or synaptic also regenerates the library cache (via ldconfig). It is the regeneration of the library cache AFTER gimpshop is installed that breaks the gimp.

You can see it for yourself by doing the following:

I booted off the Ubuntu Hardy Heron Live CD and installed gimpshop via dpkg -i. Both gimp and gimpshop worked perfectly. If you did a "ldd `which gimp-2.4`", you would see that the gimp only loaded libraries in /lib and /usr/lib and NOT any libraries installed by Gimpshop in /usr/local/lib.

Since gimpshop was installed via dpkg, the libabry cache was NOT regenerated.

But then I did a "sudo ldconfig". Then gimp stopped working. (But gimpshop still worked). If you did a "ldd `which gimp-2.4`", you would see the gimp loading some (but not all) libraries from /usr/local/lib where gimpshop installed libraries.

So it does look like a packaging issue. The gimpshop package should be modified to show a conflict with gimp. But since the gimpshop project appears to be dead that is not likely to happen.

---

### Post by Maverick88 on 2008-07-25
I found a way to get the gimp to run on Ubuntu Hardy Heron where gimpshop is also installed.

Please see

[http://ubuntuforums.org/showthread.php?p=5459597#post5459597](http://ubuntuforums.org/showthread.php?p=5459597#post5459597)

---

