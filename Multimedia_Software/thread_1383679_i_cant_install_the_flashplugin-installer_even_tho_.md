---
title: "i cant install the flashplugin-installer even tho i have the flashplugin-nonfree"
date: 2010-01-17
forum: Multimedia Software
---

### Post by 006ruler on 2010-01-17
HI! I am going insane about not being able to watch Youtube videos in any of my browsers. I have the flashplugin-nonfree, which says that it allows me to install the flashplugin-installer. When i mark the flashplugin-installer for instalation, it says it will also uninstall the flashplugin-nonfree. I click ok, and it fails, saying the following:
flashplugin-installer:
 Depends: nspluginwrapper but it is not going to be installed
 Depends: ia32-libs but it is not going to be installed

how do i get this stupid thing to work?

---

### Post by ajgreeny on 2010-01-17
Make sure you do a ```
sudo apt-get update
``` first and try again.  You may need to just refresh your repositories.

---

### Post by efflandt on 2010-01-17
It sounds like you are trying to install flash on a 64-bit system.  Did you manually install 64-bit flashplugin or any other flash plugins other than from Synaptic.

I believe that flashplugin-nonfree was an earlier flash version that may not work on sites that require flash 10.  Try "complete uninstall" of that, and then try installing flashplugin-installer.  You should end up with **Shockwave Flash 10.0 r42** which is actually 32-bit with nspluginwrapper.

There are other posts about installing real 64-bit flash, but that recently stopped working within a browser on Hulu due to some changes they made.  Although, I hear 64-bit flash still works in 64-bit Hulu Desktop.  Older cpus like my Athlon64 3200+ lack lahf_lm instruction used by 64-bit flash.  Someone came up with a flashplugin-lahf-fix.so for that, which works generally in Firefox, but Hulu desktop ignores that.  So I have switched back to flashplugin-installer (which works for 64-bit Firefox or Hulu Desktop).

---

### Post by 006ruler on 2010-01-18
...
AH!!!!!!!!!!!!!!!!!!
now i cant even do that.
crap.
im not even able to see ads!
whats going on?

---

