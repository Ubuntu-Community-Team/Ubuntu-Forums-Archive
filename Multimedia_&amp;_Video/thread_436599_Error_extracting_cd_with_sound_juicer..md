---
title: "Error extracting cd with sound juicer."
date: 2007-05-08
forum: Multimedia &amp; Video
---

### Post by TheAxeR on 2007-05-08
I keep having an error whenever I try to extract a cd to my hard drive using Sound Juicer.  It first pops up a blank warning box, after I press the button in that empty box another error box pops up which says 
> Sound Juicer could not extract this CD.
Reason: Error starting ripping pipeline  after clicking close on that box then Sound Juicer closes.

I ran Sound Juicer in the terminal and during this process it spits out > GLib-CRITICAL **: g_source_remove: assertion `tag > 0' failed with the first empty warning box and then 
>  Segmentation fault (core dumped)  after the second error box.

Has anyone else seen this behavior?  This is the first cd I have tried to extract after a fresh install of Fiesty.  Hopefully someone has seen this before and it is a relativly easy and probably obvious fix.

---

### Post by TheAxeR on 2007-05-08
bump

---

### Post by doncristobal on 2007-11-23
I have the same problem after trying to install mp3 codecs :-(

First I did what the desktop documentation told me to do (sudo apt-get install libxine-extracodecs libxine1-ffmpeg libxine1-plugins ffmpeg lame faad sox mjpegtools gxineplugin flashplugin-nonfree)
This did not help, the mp3 option was not available. ogg ripping was possible. 

Then I googled and found that I should install gstreamer0.10-plugins-ugly-multiverse, which made the mp3 option available and juice crash constantly, as described above. 

Only difference to the first post: From the terminal, it does not say the "GLib(...)" thing, it directly goes segmentation. However, after removing the above mentioned gstreamer ugly plugin package, it once said: 
"** (sound-juicer:6053): WARNING **: Profile warning: no element "lame""

Does anyone have a hint what is wrong? I googled quite much but could not find anything. 
Thanks in advance!

---

### Post by doncristobal on 2007-11-23
**This post could be related to an Ubuntu bug filed at**: [http://bugzilla.gnome.org/show_bug.cgi?id=321436](http://bugzilla.gnome.org/show_bug.cgi?id=321436) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				> **doncristobal said:**
> I have the same problem after trying to install mp3 codecs :-(

NO! 

The problem is rather that I had changed my music directory to my win/linux shared fat32 partition, and the cd database contained titles with colons : , which cannot be in a file name of a fat file system... 

There is already a bug report filed for this problem in bugzilla: [http://bugzilla.gnome.org/show_bug.cgi?id=321436](http://bugzilla.gnome.org/show_bug.cgi?id=321436)

Workarounds: 
A. take away all the : and ? in the titles, artists, etc. [tested: works on fat32]
B. use another file system [tested: works on ext3]
C. rip to another file system (cf B.), remove the : and ? there and then move the files.

---

