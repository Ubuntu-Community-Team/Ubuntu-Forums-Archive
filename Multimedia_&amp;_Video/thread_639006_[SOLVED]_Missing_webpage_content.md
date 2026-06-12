---
title: "[SOLVED] Missing webpage content"
date: 2007-12-12
forum: Multimedia &amp; Video
---

### Post by badmotor on 2007-12-12
Hi all, 

there are a couple of webpages that when I can't see content of from my linux machine. It's only a couple I have had this problem with (in both Feisty, and now Gutsy).  I have flash and Java, and can watch videos etc.  But I can see the missing content from my Windows (hail Satan) machine at work.

Any ideas? Have I got something missing?

 * webpage one: can't watch video: 
[http://www.pingu.net/official_pingu_website_flag_page.htm](http://www.pingu.net/official_pingu_website_flag_page.htm)

* webpage two: Can't see the online application form:
[http://www.tv3.co.nz/Programmes/DealOrNoDeal/ContestantApplications/tabid/275/Default.aspx#top](http://www.tv3.co.nz/Programmes/DealOrNoDeal/ContestantApplications/tabid/275/Default.aspx#top)

:(

---

### Post by AJLChase on 2007-12-12
I have the same issue. Before I installed the patches that someone had mentioned to fix codec problems I could see them, but then after the restricted ones isntalled now I too can' twatch videos.


[www.break.com](www.break.com) is the one I usually check and it doens't work.

---

### Post by NilsE on 2007-12-12
The videos on these sites are flash videos and you may be having the same issue that others are having with a bad flashplugin-nonfree install.  There are two solutions in the following post so read it all and choose the one you are most comfortable with.

[http://ubuntuforums.org/showthread.php?p=3927167#post3927167](http://ubuntuforums.org/showthread.php?p=3927167#post3927167)

The form  is not a flash form but other things on the page might be impacting it.

---

### Post by badmotor on 2007-12-13
OK, so I completely followed the instructions, and now Flash works properly in Firefox, but is completely broken in Opera.

Which is a pain, because I use Opera for everything. Under preferences>content>plugins it has two versions of Flash. they have the same description, but a different path ?

---

### Post by Elegorod on 2007-12-13
For Opera:
If broken Flash plugin is in the folder /usr/lib/opera/plugins/, try to remove plugin file and restart Opera

---

### Post by badmotor on 2007-12-13
The only things in that folder are:
libnpp.so  operaplugincleaner  operapluginwrapper

---

### Post by NilsE on 2007-12-13
Not sure what the folder is for Opera but if you do a search for libflashplayer.so at the file system level you may find where it is in one or more of the opera folders.

---

### Post by badmotor on 2007-12-13
Dang it, can't seems to find that file anywhere... :confused:

---

### Post by Elegorod on 2007-12-13
What are the paths to plugins at preferences>content>plugins? Maybe delete one plugin (which is broken)
Why to find them, when the path is shown...

---

### Post by badmotor on 2007-12-13
> **Elegorod said:**
> What are the paths to plugins at preferences>content>plugins? Maybe delete one plugin (which is broken)
Why to find them, when the path is shown...

that's a very good point! 
I'll try that.

---

### Post by badmotor on 2007-12-14
OK guys, I've got two plugins happening in Opera - here's what I got:


Shockwave Flash      Shockwave Flash 9.0 r115      /usr/lib/mozilla/plugins/flashplugin-alternative.so
Shockwave Flash      Shockwave Flash 9.0 r115      /usr/lib/flashplugin-nonfree/libflashplayer.so



- should I delete one of these? If so, which one?

---

### Post by Elegorod on 2007-12-14
I have libflashplayer.so in /usr/lib/opera/plugins/ and flash works.
Firsly, press F12 and check that plugins are enabled. If yes, and flash doesn't work, you have only 2 variants (2 files to delete). Maybe not delete, but move files to Home directory. And move back if no effect.

---

### Post by badmotor on 2007-12-16
Hmmmm . . .that didn't seem to work. I must admit, I'm at a but of a loss.

---

### Post by dtfinch on 2007-12-20
Try downgrading to Flash 9.0 r48 or upgrading to Opera 9.50 beta 1. Flash 9.0 r115 is entirely incompatible with Opera 9.25 and Konqueror. I don't know why Adobe thought it was good enough to release.

Edit:
Working so far with the latest Opera snapshot:
[http://snapshot.opera.com/unix/snapshot-1719/intel-linux/opera_9.50-20071213.6-shared-qt_i386.deb](http://snapshot.opera.com/unix/snapshot-1719/intel-linux/opera_9.50-20071213.6-shared-qt_i386.deb)

---

### Post by badmotor on 2008-02-25
I copied the correct Flash plugin from the Firefox>plugins folder, into the main Opera folder and now it is all working again. Yay!

Still buggy though....  streaming cuts out if you scroll the mouse at the same time, or if you open another web page....

---

