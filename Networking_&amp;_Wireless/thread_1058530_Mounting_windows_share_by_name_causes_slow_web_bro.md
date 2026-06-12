---
title: "Mounting windows share by name causes slow web browsing"
date: 2009-02-02
forum: Networking &amp; Wireless
---

### Post by GoneSouth on 2009-02-02
Ok folks, got a head scratcher for you. 

After following various excellent guides on how to automount windows shares by name (cifs, winbind, nsswitch, fstab etc etc), I am successfully auto mounting a share on my home network by (windows pc) name on my intrepid laptop. 

However, I noticed that when I do so, oddly enough, web browsing is slowed down. Not transfer rates, just domain lookup ... I type a URL in the firefox address bar, it says looking up domainxyz.com... (or whatever) in the bottom left corner of firefox for like 5 seconds, then starts loading the web page. 

If I comment out the fstab line that does the automount and reboot, web browsing is fast again. I don't have to uninstall any packages or anything to restore web browsing speed, just comment out the automount. Any idea what could be causing this?

  - GS

---

### Post by bkadoctaj on 2010-03-05
> **GoneSouth said:**
> Ok folks, got a head scratcher for you. 

After following various excellent guides on how to automount windows shares by name (cifs, winbind, nsswitch, fstab etc etc), I am successfully auto mounting a share on my home network by (windows pc) name on my intrepid laptop. 

However, I noticed that when I do so, oddly enough, web browsing is slowed down. Not transfer rates, just domain lookup ... I type a URL in the firefox address bar, it says looking up domainxyz.com... (or whatever) in the bottom left corner of firefox for like 5 seconds, then starts loading the web page. 

If I comment out the fstab line that does the automount and reboot, web browsing is fast again. I don't have to uninstall any packages or anything to restore web browsing speed, just comment out the automount. Any idea what could be causing this?

  - GS

Same problem over here.  :(

EDIT: Note, you don't need to remove your automount; all you need to do is mount it by the computer's static IP instead.

---

