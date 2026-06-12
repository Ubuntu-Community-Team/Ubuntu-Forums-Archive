---
title: "YouTube / video not working properly in Firefox"
date: 2008-05-10
forum: Multimedia Software
---

### Post by Arphahat on 2008-05-10
I just installed Ubuntu using the windows install on Friday and have been experimenting with it.  I am running into a problem trying to view embedded video, most noticeably at YouTube.  When the video loads, it shows only a black screen and then adds the "Share" and "Replay" buttons.  Clicking play does nothing.

Are there any known issues about this?  It is a fresh install, so I don't know if there is anything that I might be missing?  I did try to install the Adobe flash, but it had not affect.

Any help would be appreciated.  Thanks.

---

### Post by NilsE on 2008-05-10
Go into Synaptic package manager and install flashplugin-nonfree

If it works but you have no sound then install libflashsupport

---

### Post by meech on 2008-05-10
Installing libflashsupport in my Hardy installation solved this problem immediately after reboot. Thank you so, so much!


Michelle

---

### Post by NilsE on 2008-05-10
> **meech said:**
> Installing libflashsupport in my Hardy installation solved this problem immediately after reboot. Thank you so, so much!


Michelle
My Pleasure

---

### Post by Arphahat on 2008-05-10
> **NilsE said:**
> Go into Synaptic package manager and install flashplugin-nonfree

If it works but you have no sound then install libflashsupport

I have installed both of those now and rebooted, but it still is behaving poorly.  Are there any other packages that I should not have installed that could be interfering?

---

### Post by NilsE on 2008-05-10
> **Arphahat said:**
> I have installed both of those now and rebooted, but it still is behaving poorly.  Are there any other packages that I should not have installed that could be interfering?
Doing a search on just the word flash in Synaptic these are the only 3 packages I have installed. I don't have libflashsupport installed but some people seem to need it.

libswfdec-0.6-90

flashplugin-nonfree

ubuntu-restricted-extras

---

### Post by Arphahat on 2008-05-10
When I do a search, I have several "gnash" items as well.  Including: gnash, gnash-common, gnash-cygnal, gnash-tools and mozilla-plugin-gnash

Could these be interfering?  Could it be damaging to remove them to try it out?

---

### Post by NilsE on 2008-05-11
> **Arphahat said:**
> When I do a search, I have several "gnash" items as well.  Including: gnash, gnash-common, gnash-cygnal, gnash-tools and mozilla-plugin-gnash

Could these be interfering?  Could it be damaging to remove them to try it out?They will conflict and it won't hurt anything to remove them.  They are a Flash alternative that still needs a little work.

---

### Post by Cornova on 2008-05-11
For some reason Firefox keeps using Gnash eventhough under the applications section under preferences it shows shockwave.

---

### Post by NilsE on 2008-05-11
> **Cornova said:**
> For some reason Firefox keeps using Gnash eventhough under the applications section under preferences it shows shockwave.
After you have removed Gnash then reinstall flashplugin-nonfree.  Make sure you close all instances of FF and restart it. Would not even hurt to reboot.

---

### Post by Cornova on 2008-05-11
> **NilsE said:**
> After you have removed Gnash then reinstall flashplugin-nonfree.  Make sure you close all instances of FF and restart it. Would not even hurt to reboot.

Works now, much appreciated. :)

---

### Post by Yellow Pasque on 2008-05-11
It sounds like you need to clean everything out. Check out this guide. It's for 64-bit systems but you'll probably need to do the same thing. i.e.
```
sudo apt-get -P gnash gnash-common mozilla-plugin-gnash flashplugin-nonfree libflash-swfplayer
```

[http://ubuntuforums.org/showthread.php?t=772490](http://ubuntuforums.org/showthread.php?t=772490)

---

### Post by Arphahat on 2008-05-11
Thanks, uninstalling the gnash stuff took care of the problem.

---

### Post by Cornova on 2008-05-11
After browsing YouTube for the past hour or so Fire Fox will crash with random videos a second after clicking the link to it.

---

### Post by Yellow Pasque on 2008-05-11
> **Cornova said:**
> After browsing YouTube for the past hour or so Fire Fox will crash with random videos a second after clicking the link to it.
Follow Kilz's guide.

---

### Post by Cornova on 2008-05-11
> **Temüjin said:**
> Follow Kilz's guide.

I am using Intel 32 :(

---

### Post by fitzdragon on 2008-07-08
> **NilsE said:**
> After you have removed Gnash then reinstall flashplugin-nonfree.  Make sure you close all instances of FF and restart it. Would not even hurt to reboot.


that worked for me as well thanks a lot 

fitz

---

