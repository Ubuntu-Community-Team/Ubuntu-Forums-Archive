---
title: "Can't retrieve maverick packages from launchpad"
date: 2010-10-06
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by Peter7K on 2010-10-06
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main Sources
  404  Not Found
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main i386 Packages
  404  Not Found
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main Sources
  404  Not Found
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main i386 Packages
  404  Not Found
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main Sources
  404  Not Found
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main i386 Packages
  404  Not Found


I can't apt-get build-dep wine for instance, and I get those errors when I apt-get update.  What is the cause of this?

---

### Post by Peter7K on 2010-10-06
I now also have an error on the notification bar saying "You haven't updated your sources in 10 days!" warning.  Is my sources list file incorrect or something?

---

### Post by dino99 on 2010-10-06
you should not use ppa right now, and most of them are not maintained anyway, so check these ppas on web, and tweak your synaptic repo tab.

which ppa are concerned ?

---

### Post by Peter7K on 2010-10-06
I unchecked the maverick launchpad ppas (should I have done that?)

But I still get this error:

W:Failed to fetch [http://ppa.launchpad.net/jonls/redshift-ppa/ubuntu/dists/maverick/main/source/Sources.gz](http://ppa.launchpad.net/jonls/redshift-ppa/ubuntu/dists/maverick/main/source/Sources.gz)  404  Not Found
, W:Failed to fetch [http://ppa.launchpad.net/jonls/redshift-ppa/ubuntu/dists/maverick/main/binary-i386/Packages.gz](http://ppa.launchpad.net/jonls/redshift-ppa/ubuntu/dists/maverick/main/binary-i386/Packages.gz)  404  Not Found
, W:Failed to fetch [http://ppa.launchpad.net/nautilus-dropbox/ppa/ubuntu/dists/maverick/main/source/Sources.gz](http://ppa.launchpad.net/nautilus-dropbox/ppa/ubuntu/dists/maverick/main/source/Sources.gz)  404  Not Found
, W:Failed to fetch [http://ppa.launchpad.net/nautilus-dropbox/ppa/ubuntu/dists/maverick/main/binary-i386/Packages.gz](http://ppa.launchpad.net/nautilus-dropbox/ppa/ubuntu/dists/maverick/main/binary-i386/Packages.gz)  404  Not Found
, E:Some index files failed to download, they have been ignored, or old ones used instead.

I'm just assuming those ppas don't have maverick stuff yet.

I think this problem arose from me importing my ppas from my Lucid (I copied over files).  Though I unchecked the ones that were giving me errors, I should still be able to get updates from canonical/maverick updates?  Thanks.

---

### Post by ktp on 2010-10-06
you are correct that ppa also doesn't build packages for maverick.  You should disable all of these ppa until they build for maverick.

---

### Post by Peter7K on 2010-10-06
> **ktp said:**
> you are correct that ppa also doesn't build packages for maverick.  You should disable all of these ppa until they build for maverick.

So should I be worried that the update manager states that it hasn't successfully checked for updates in 10 days (even though it's updated many times since then)?  Perhaps that's just because I have an error on one or two of the ppas... Oh well.

---

### Post by FuturePilot on 2010-10-06
> **Peter7K said:**
> So should I be worried that the update manager states that it hasn't successfully checked for updates in 10 days (even though it's updated many times since then)?  Perhaps that's just because I have an error on one or two of the ppas... Oh well.

It's saying that because of the error. I think it doesn't considered the package information updated if it doesn't finish cleanly.

---

