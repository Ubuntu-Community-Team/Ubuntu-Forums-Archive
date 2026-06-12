---
title: "amarok problem"
date: 2007-11-05
forum: Multimedia &amp; Video
---

### Post by bearcat on 2007-11-05
As of about two weeks ago, my amaroK library lists every single file in my MP3 collection *twice*, and the program goes in a constant loop of "updating" my collection every 30 seconds or so. Which, of course, interferes with my ability to play files, because the program won't let me expand a list in my collection to click on a file while it's "updating".

Help?

---

### Post by Sarisar on 2007-11-06
You could turn off auto updating music list (it's under the options) which should (hopefully) stop the updating permanently.

Not sure about the dupes though, are these definately the same file?  Check going into properties just to make sure it's not something silly like you have a link to them and you're getting the original file and the linked file.

---

### Post by employeeno5 on 2007-11-06
I've got the exact same issue.
One day, Amarok just decided to list all of my files twice. This is obnoxious. About half of them are a relisting of exact same file so it plays twice and another large amount of them are just dead links so the playlist stops.
I thought maybe the easiest way to deal with it would be to remove my collection from Amarok and reimport it. However, I can't seem to find any option to remove files from my collection, only to delete the actual file.
So, then I tried uninstalling the program through the synaptic package manager. I was sure to check as "remove completely" in hopes that any library files would be wiped out with it and I could start fresh. Again no luck. Apparently a complete removal doesn't delete you library file; the moment I've reinstalled it my collection is already in there with two copies of everything still. I've searched my computer for the file that Amarok keeps this information in, but can't seem to find it.

I don't know why this has happened in Amarok, but at this point I'd be happy just to know how to truly, completely uninstall Amarok so I could start fresh.
Understanding why this happened, how to fix it, or how to prevent would also be nice. 

I have yet to find a single Linux music player/organizer that has been able to import my entire music collection correctly. My collection is completely composed of non-DRM mp3s ripped from my own personal cd collection.
I never thought I'd say it but I miss iTunes.

Any help with this would be great. I'm thrilled with switching to Linux with this one exception of music player troubles. Amarok was fantastic until the day it started listing things twice. I would love to get it sorted out.

---

### Post by knowname on 2007-11-07
I have had the same problem and managed a workaround. Not sure how permanent this solution will be. I keep my music all in one folder, named '/home/username/music/'. I had amarok set up to only watch this one folder -- the trick I used was to just rename this folder 'music2', then started amarok. The 'Updating Collection' message appeared again for a while, but this time it didn't get stuck in an infinite loop. After it finished, it still showed the tracks as being there (but they couldn't be played). I hit 'Tools > Rescan Collection', and it updated my collection to be completely empty. then I renamed my folder back to 'music' and hit 'Tools > Rescan Collection' again and five minutes later had it back to working as it should!

Hope that works for you.

---

### Post by tris_r on 2007-11-08
Hi I've got the same problem for a week or so and have been meaning to look into it for a while.  This sounds very do-able, but I was wondering, have you lost database information such as labels, scores and ratings??

Please let me know so I know the risks?    

Thanks

---

### Post by tris_r on 2007-11-08
A bit of completion for people that have the same problem...

knowname's solution worked for me and all the ratings, score, play count etc were retained.  I realised that I could backup  /home/USER/.kde/share/apps/amarok/collection.db to ensure that nothing goes astray.  

Don't delete collection.db just make an extra copy and then follow the instructions in knownames post.


cheers

---

### Post by rmanronga on 2008-02-07
I just wanted to say that knowname's solution also worked for me,... I had the same exact problem on Gutsy....

---

