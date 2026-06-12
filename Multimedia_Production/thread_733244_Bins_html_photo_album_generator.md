---
title: "Bins html photo album generator"
date: 2008-03-23
forum: Multimedia Production
---

### Post by rotten777 on 2008-03-23
In case anyone else tries to use 'bins' to generate their static HTML album and runs into the same issues I hit (error saying template swig not found), try this out:


> mkdir destination

bins -t /usr/share/bins/ /home/username/Pictures/source_photo_folder/ /home/username/Documents/destination/

The key here being the parameter > -t /usr/share/bins/ ...
It seems the program is looking elsewhere (who knows where) and the package maintainer (or someone) has moved the templates directory. This simply specifies the root of the bins directory that the Ubuntu version is installed to. ( /usr/share/bins )

Hope this helps someone!

---

### Post by Stochastic on 2008-03-24
With such a specific issue the forum really isn't the place for this - it'll get buried too quick to help those that need it.  I'd file a bug report on launchpad, this will notify those in charge of the development and then the software will be fixed.

---

