---
title: "Flash crashes browsers"
date: 2008-10-23
forum: Multimedia Software
---

### Post by Mud.Knee.Havoc on 2008-10-23
I recently noticed that Youtube videos no longer worked for me (running Opera 9.6 on Hardy 32 bit).  I loaded up Firefox 3 and it runs fine unless I try to go to a site that has flash, at which point it crashes.  For example, I can type "www.youtube.com" and it'll crash as soon as it starts loading the page.

I uninstalled everything related to flash and firefox, rm -rf'd all related directories (.mozilla, /usr/lib/firefox-whatever, plugin directories, etc).  I've even used "locate" to find every directory that firefox and flash are in, just to make sure that I'm getting it all.

Basically, I've tried everything that I can find on the forums, but no luck.  I've even tried installing gnash as a desperation effort, but it only displays simple flash (and not the actual youtube videos).  I've purged that now, as well.

Firefox 2 and 3 both die with segmentation faults, as does Epiphany.  Opera says that it's got the flash plugin loaded, but it only gives me an empty white space with the "Click to activate plugin", which does nothing when I click it.

I've reinstalled flash from the repos and the .deb on the official flash site, testing it (ie. crashing the browser), then making sure to completely purge it each time it doesn't work.

Any ideas?  I'm going to reboot and try the old kernel and see if that helps...  Not that I can't live without YouTube, but revision3 and other good stuff doesn't work, either.

---

### Post by The_Dark_Lord on 2008-10-23
I have ubuntu 8.04 32bit with all updates  with firefox 3.0.3 and flash 10.0.12.36 and its all good for me, i have never had a flash crashing problem in the 2 years ive been running ubuntu but i hope you get it sorted

---

### Post by eternalnewbee on 2008-10-23
I got my problems solved like this:
> sudo apt-get install libflashsupport

---

### Post by eternalnewbee on 2008-10-24
Well? Any success?

---

### Post by Mud.Knee.Havoc on 2008-10-24
Unfortunately, the problem persists.  I can do anything I want with any browser as long as flash is uninstalled, but as soon as it's installed (even with libflashsupport), they segfault as soon as they try to load flash.  

Well, thanks for trying to help!  I'll be wiping my / directory when Intrepid is released, so hopefully this problem shouldn't last past the end of the month. :)

---

### Post by gandaran on 2008-10-24
> **Mud.Knee.Havoc said:**
> Unfortunately, the problem persists.  I can do anything I want with any browser as long as flash is uninstalled, but as soon as it's installed (even with libflashsupport), they segfault as soon as they try to load flash.  

Well, thanks for trying to help!  I'll be wiping my / directory when Intrepid is released, so hopefully this problem shouldn't last past the end of the month. :)
 
is your system and firefox updated (firefox 3.0.3)?
firefox 3.0.3 and flash 10 work just fine and no need to install libflashsupport, just try this no libflashsupport and remove any other flash application or version, just firefox updated and flash 10, it works!

can you post the full result of **about: plugins** type in firefox url bar without spaces

---

### Post by kauboy on 2008-10-25
Hello Mud.Knee.Havoc,

I used to face the same problems (months back) with Opera on Ubuntu 7.10. After weeks of Googling, I found a workaround that actually worked, at [http://ubuntuforums.org/showthread.php?t=679212](http://ubuntuforums.org/showthread.php?t=679212), hope it'll still work, though I've not tried Opera on 8.04 yet. :)

---

### Post by Mud.Knee.Havoc on 2008-10-25
Hey everybody,
Thanks for the help! (this forum is the best on Earth)

I finally figured it out... my permissions on the .macromedia directory were not writable.  I made the directory writable and my problem disappeared.

---

