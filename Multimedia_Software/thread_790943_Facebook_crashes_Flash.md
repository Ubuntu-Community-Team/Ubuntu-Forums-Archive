---
title: "Facebook crashes Flash?"
date: 2008-05-11
forum: Multimedia Software
---

### Post by Rohaq on 2008-05-11
I've got Ubuntu Hardy 64-bit, the latest version of Flash 9 installed, and running Firefox 64-bit. Flash seems to work without issue, until I open a page on Facebook, after which any Flash apps in Firefox turn into grey blocks, and npviewer.bin becomes a zombie process in my System Monitor.

I've tried blocking all Flash apps on Facebook using AdBlock, but the problem is still apparent. Can anyone offer me any ideas as to what could be causing this, or how to find out, and how I can resolve it?

Many thanks!

---

### Post by jeremynu on 2008-05-11
I have the same problem with Flash on Facebook.  Running 64 bit Ubuntu 8.04 Firefox 3 Beta5.  It seems to be some third party apps on Facebook that have the issue.  I have seen some areas of other sites crash when Flash is invoked.

---

### Post by ubuntu-freak on 2008-05-12
Trying purging/installing Flash:

**sudo apt-get purge flashplugin-nonfree gnash gnash-common mozilla-plugin-gnash swfdec-mozilla && sudo apt-get install flashplugin-nonfree libflashsupport**

Also, within Firefox, navigate to Edit > Preferences > Security and untick everything except the password option. Next, close Firefox and navigate to Places > Home > View > and select "Show Hidden Files". Inside your home directory, navigate to /.mozilla/firefox and look for a folder with ".default" in it's name, open it and delete any files starting with "urlclassifier".

Hope that helps,

Nathan

---

