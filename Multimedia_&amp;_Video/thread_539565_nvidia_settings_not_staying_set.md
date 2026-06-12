---
title: "nvidia settings not staying set"
date: 2007-08-31
forum: Multimedia &amp; Video
---

### Post by bbqsauced on 2007-08-31
I recently used Envy to install drivers for my 8800 GTS.  Envy added a Nvidia Settings section to my applications menu, but when I try to make any changes, they all disappear when I restart my computer.  I also get this error when trying to save changes to my xorg.conf through the Nvidia Settings manager:

Unable to remove old X config backup file '/etc/X11/xorg.conf.backup'.

I tried adding a startup session to fix it, but it didn't do anything.

(I added this:
nvidia-settings --load-config-only)

Any ideas on how to fix this?  I didn't run into any errors using Envy, but I'm wondering if it's even working at all.

---

### Post by tseliot on 2007-08-31
type:
```
sudo nvidia-settings
```

and save your settings

---

### Post by wolfen69 on 2007-08-31
saving in nvidia-settings never worked for me.
only
```
sudo dpkg-reconfigure xserver-xorg
```
works. or by hand.

---

### Post by KarnEdge on 2007-09-09
> **tseliot said:**
> type:
```
sudo nvidia-settings
```

and save your settings

**Using 'sudo' accesses settings as an admin?** I had the same problem with not being able to save the xorg file and on reboots being set to defaults, and this little bit of help worked.

Thanks

---

