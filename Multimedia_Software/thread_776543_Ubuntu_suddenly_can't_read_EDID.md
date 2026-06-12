---
title: "Ubuntu suddenly can't read EDID"
date: 2008-04-30
forum: Multimedia Software
---

### Post by karlhm76 on 2008-04-30
Hi All,

Last night my computer was working fine, and had been working fine for quite some time.

This morning when I switched it on, the display was set to 640x480. When I logged in and checked the logs I saw that X couldn't read the EDID of my monitor -- Again!

I run ubuntu 7.10, nVidia 7600GS, Acer AL2216W monitor

I had this problem about 6 months ago after I updated the video driver but it went away after nVidia released the next update for their driver. This time tho, I haven't performed a driver update -- well maybe a month ago.

The way I got around it the first time was to load the previous driver where it worked fine, dump the EDID to a file, load the new driver, then use the saved EDID by adding a setting to the xorg.conf. (The problem being that the nVidia driver just couldn't read the EDID from the monitor, but the EDID information was fine). According to nVidia I have to replace my monitor, but thats crap, in XP the monitor works fine with the same graphics card.

I don't know why it would suddenly stop working. The only thing I did last night that was out of the ordinary was to put new batteries in my bluetooth keyboard and reconnect it.

Unless its related to the date? its the 1st May here today.. maybe the nVidia driver is still broken so on the 1st May 2008 the old problem of not reading EDIDs reappears? Sound a bit far-fetched?

Anyone have the same problem (if its date related, probably wont show up until tomorrow for all you US people!)

In the meantime, how can I use Envy to load an old nvidia driver so I can see if I can do the EDID dumping trick again? (and also checking to see whether its actually a driver issue)

Thanks

---

### Post by karlhm76 on 2008-05-01
Hi All,

fixed problem

Used help from this post [http://ubuntuforums.org/showthread.php?t=730040&highlight=EDID](http://ubuntuforums.org/showthread.php?t=730040&highlight=EDID)

plus googled modeline and my monitor model and found the solution.

---

### Post by karlhm76 on 2008-05-01
Now, how do I mark this as solved...?

---

