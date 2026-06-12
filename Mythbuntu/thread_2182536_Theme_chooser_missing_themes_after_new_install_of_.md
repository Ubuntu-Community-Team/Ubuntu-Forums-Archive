---
title: "Theme chooser missing themes after new install of ubuntu13.10"
date: 2013-10-21
forum: Mythbuntu
---

### Post by odror on 2013-10-21
After installing ubuntu 13.10 and adding mythtv. I am missing many theme in the theme chooser.  My favorite mythmediastream theme is also missing. I have also noticed the the package mythtv-themes is not available.

Any way to fix that.


Thanks

---

### Post by tgm4883 on 2013-10-21
> **odror said:**
> After installing ubuntu 13.10 and adding mythtv. I am missing many theme in the theme chooser.  My favorite mythmediastream theme is also missing. I have also noticed the the package mythtv-themes is not available.

Any way to fix that.


Thanks

The theme chooser downloads a list of themes from [ftp://ftp.osuosl.org/pub/mythtv/themes/0.27/](ftp://ftp.osuosl.org/pub/mythtv/themes/0.27/)  Each theme needs to be verified by its authos that is it ready for a version of MythTV. So since 13.10 came with the new version of MythTV, it would seem that the themes you are looking for (mythmediastream) hasn't been verified it works with 0.27. You'll need to contact the author of the themes you are want that are missing and ask them to update it for MythTV 0.27.

---

### Post by odror on 2013-10-21
Will a 0.26 theme work on 0.27. If so How can I install it on mythtv

Thanks

---

### Post by tgm4883 on 2013-10-22
> **odror said:**
> Will a 0.26 theme work on 0.27. If so How can I install it on mythtv

Thanks

Will it work? Maybe. That is precisely why the author needs to certify that it's ready for 0.27. If you want to install a theme from 0.26 on 0.27, then just unzip the theme into your ~/.mythtv/themes/ directory.

---

### Post by odror on 2013-10-22
Thanks. It is working now.

---

