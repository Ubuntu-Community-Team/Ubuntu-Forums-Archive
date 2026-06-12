---
title: "Samba No Working!"
date: 2011-06-09
forum: Networking &amp; Wireless
---

### Post by JNied on 2011-06-09
I've tried searching for this error and have not come up with any solutions that have worked for me.  I apologize if the solution already exists, but I couldn't find it.

This is where I'm at now:```
The following packages have unmet dependencies:
 samba : Depends: libwbclient0 (= 2:3.5.8~dfsg-1ubuntu2) but 2:3.5.8~dfsg-1ubuntu2.1 is to be installed
E: Broken packages
```I've tried fixing broken packages with Synaptic but no luck.

Here's the back story:
I am trying to share my media with my mixed-device network.  From Nautilus I right click my folder and then "sharing options" and then check "share this folder".  After a bit of googling, I tried commands that I forgot, but bottom line I ended up uninstalling samba, samba-common and smbclient, then trying to reinstall.  Now samba will not reinstall because of the error listed above, and the sharing options have disappeared from Nautilus.

Any help would be greatly appreciated.

In case it helps:
Linux Jason-Lin 2.6.38-8-generic #42-Ubuntu SMP Mon Apr 11 03:31:50 UTC 2011 i686 i686 i386 GNU/Linux

---

### Post by capscrew on 2011-06-09
> **JNied said:**
> I've tried searching for this error and have not come up with any solutions that have worked for me.  I apologize if the solution already exists, but I couldn't find it.

This is where I'm at now:```
The following packages have unmet dependencies:
 samba : Depends: libwbclient0 (= 2:3.5.8~dfsg-1ubuntu2) but 2:3.5.8~dfsg-1ubuntu2.1 is to be installed
E: Broken packages
```I've tried fixing broken packages with Synaptic but no luck.

Here's the back story:
I am trying to share my media with my mixed-device network.  From Nautilus I right click my folder and then "sharing options" and then check "share this folder".  After a bit of googling, I tried commands that I forgot, but bottom line I ended up uninstalling samba, samba-common and smbclient, then trying to reinstall.  Now samba will not reinstall because of the error listed above, and the sharing options have disappeared from Nautilus.

Any help would be greatly appreciated.

In case it helps:
Linux Jason-Lin 2.6.38-8-generic #42-Ubuntu SMP Mon Apr 11 03:31:50 UTC 2011 i686 i686 i386 GNU/Linux

Try and un-install winbind.  You don't need it unless you are in an AD domain.

```
sudo apt-get purge winbind
```


Edit: If you are trying to share the "Public" folder with Personal File Sharing you do not need Samba at all.

---

### Post by JNied on 2011-06-09
"Package winbind is not installed, so not removed"

And I'm not trying to share the public folder; I have all of my different types of media separated in different folders on an external disk.

---

