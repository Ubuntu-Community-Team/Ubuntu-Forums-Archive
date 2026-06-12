---
title: "Searching for photo files organizing tools"
date: 2007-06-10
forum: Multimedia Production
---

### Post by motin on 2007-06-10
**Short version:**
I am looking for two photo organizing tools. First, I am searching for a tool that can shift the timestamps of a jpeg file (including the meta-datas') and secondly a file renamer that will rename photos from different folders according to MyPhotoAlbumName 001, 002 etc in order of time photo taken. 

**Long version:**
My brother just graduated and we had a total of four digital cameras taking pictures of the happening. I just got all of these four camera's pictures sent to me and my task is to organize these into a summarizing photoalbum of the day. Now I am looking for tools to help with the following:

 - As one of the cameras had the wrong date/time set, a tool that will shift the timestamps of the created and meta-data timestamps a certain time period
 - Then I'd need a file renamer that would rename all photos to MyBrothersGraduation N.jpg in order of which time the photo was taken according to the jpeg's meta-data (where N is the photo number in the sequence)

After that, I can probably use Picasa or maybe even F-Spot to rotate, enhance, tag and resize the pictures. 

If you have any suggestions on what tools/scripts to use for this please advice me and any others that have found themselves in this situation. 

Big thanks!

---

### Post by nalmeth on 2007-06-10
I would probably recommend a combination of digikam and the gimp to get all that done, as far as your specific tasks, I don't know exactly what to tell you.

Start with digikam, and see if it does what you need.

---

### Post by motin on 2007-06-11
Sorry, but I couldn't find any batch renaming tools nor timestamp shifters in digikam nor gimp. :(

---

### Post by stani on 2007-06-11
It doesn't help you with the batch renaming or time-shifting, but you might be interested in Phatch, my new application for batch photo processing. You can find more info here:
[http://ubuntuforums.org/showthread.php?t=466598](http://ubuntuforums.org/showthread.php?t=466598)

---

### Post by nalmeth on 2007-06-11
There seem to be plugins on this page for digikam that will do what you want:
[http://www.digikam.org/plugins.html](http://www.digikam.org/plugins.html)

---

### Post by motin on 2007-07-16
> **nalmeth said:**
> There seem to be plugins on this page for digikam that will do what you want:
[http://www.digikam.org/plugins.html](http://www.digikam.org/plugins.html)

There is a batch renamer which would solve half of my problem. Thanks for finding that. Couldn't find any plugin for timestamp shifting however...

---

### Post by motin on 2007-07-16
> **stani said:**
> It doesn't help you with the batch renaming or time-shifting, but you might be interested in Phatch, my new application for batch photo processing. You can find more info here:
[http://ubuntuforums.org/showthread.php?t=466598](http://ubuntuforums.org/showthread.php?t=466598)

Hey thanks for the tip and even greater thanks for developing Phatch! There are plugins as mentioned above that will do most of your app does today but I love the Phatch interface! A lot of people are going to save time by using your app! And, it follows the old ideology about that there should be one app for a certain task (batch processing of images) and that app should to it well. Much better than plugins to existing photo managing apps.

My dreams would come true in this matter if there was an action for [timeshifting EXIF "Photo taken" timestamps]("https://blueprints.launchpad.net/phatch/+spec/timeshift-action") in your app. I could then use [Gnome-Commander to rename the files after this timestamp]("http://www.nongnu.org/gcmd/tags.html") (Tip from [https://blueprints.launchpad.net/phatch/+spec/batch-rename](https://blueprints.launchpad.net/phatch/+spec/batch-rename)).

---

