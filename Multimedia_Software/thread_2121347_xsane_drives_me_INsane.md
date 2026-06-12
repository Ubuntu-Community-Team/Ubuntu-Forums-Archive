---
title: "xsane drives me INsane"
date: 2013-03-01
forum: Multimedia Software
---

### Post by Elvis99 on 2013-03-01
hi all,

I used to have xsane as my default scanning utility. However, now it's always scanning pictures in 1x1 resolution and I can't find the option to reset this. Can anybody please point me in the right direction?
I've attached a window of what a scan now looks like ..

Cheers!

[IMG]http://i50.tinypic.com/sgtyl3.png[/IMG]

---

### Post by ajgreeny on 2013-03-01
You use the main xsane  window to set the resolution that you scan at, as shown in my screenshot.

I presume you see this window when you start xsane?

---

### Post by Elvis99 on 2013-03-01
> **ajgreeny said:**
> You use the main xsane  window to set the resolution that you scan at, as shown in my screenshot.

I presume you see this window when you start xsane?

Thanks for your reply. Yes, I use the main screen. 
I can set the scan resolution to whatever I want, it's not getting better. The output stays unfortunately the same 1x1 :/

---

### Post by kurt18947 on 2013-03-01
If simple solutions don't work out, you can try this.  Open your home folder, press <ctrl>H to show hidden files.  Navigate to .sane -> xsane.  I have 3 files plus one folder, batch-lists.  Try deleting your scanner's .drc file then restart.  You could also rename the .drc file to something like (scanner_name).drc.old and save that.  I had a goofy setting issue one time I *could not* fix.  Deleting the .drc configuration file did it.  A new file will be created with default settings.

---

### Post by Elvis99 on 2013-03-01
> **kurt18947 said:**
> If simple solutions don't work out, you can try this.  Open your home folder, press <ctrl>H to show hidden files.  Navigate to .sane -> xsane.  I have 3 files plus one folder, batch-lists.  Try deleting your scanner's .drc file then restart.  You could also rename the .drc file to something like (scanner_name).drc.old and save that.  I had a goofy setting issue one time I *could not* fix.  Deleting the .drc configuration file did it.  A new file will be created with default settings.

Sir, you just have solved the case. I thank you and salute your wisdom. Hooray! :)

---

