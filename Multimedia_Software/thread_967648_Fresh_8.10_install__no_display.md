---
title: "Fresh 8.10 install:  no display"
date: 2008-11-02
forum: Multimedia Software
---

### Post by Adahn on 2008-11-02
I finished a fresh install of 8.10 from a live CD.  Monitor output while running the CD had artifacts consistent with the wrong monitor refresh rate.  After restart, there was sound but no display.  I tried booting in recovery mode, and fixx did nothing.  Trying apt-get update in recovery mode failed to resolve any of the ubuntu servers.  I'm running an ATI 3850 card.

---

### Post by Merlin_ua on 2008-11-02
Exactly the same problem here, with the same video card. I found this advice: [http://ubuntuforums.org/showpost.php?p=6075895&postcount=17](http://ubuntuforums.org/showpost.php?p=6075895&postcount=17), trying to do it now.

---

### Post by Adahn on 2008-11-02
I tried that...still no video after the splash screen.
I can hear the login sound but the screen is blank.

---

### Post by Adahn on 2008-11-03
I fixed it by adding 
driver   "vesa" 
to xorg.conf after configured device.

After getting into the desktop and updating, I was even able to successfully install the restricted fglrx drivers.

Even better, either my new 790gx or the new kernel/fglrx has changed enough to get suspend working for me again, something I hadn't had for a couple of ubuntu versions.

---

