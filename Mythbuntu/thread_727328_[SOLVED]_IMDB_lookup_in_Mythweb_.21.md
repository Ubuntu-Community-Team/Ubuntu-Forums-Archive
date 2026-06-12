---
title: "[SOLVED] IMDB lookup in Mythweb .21"
date: 2008-03-17
forum: Mythbuntu
---

### Post by jruss on 2008-03-17
I recently upgraded to MythTV .21 from Gutsy backports. Most everything seems to work really well. I love a lot of the improvements in MythWeb. When I am in the videos section of MythWeb I can see all of my videos. There are buttons on each video for edit and IMDB. The edit button seems to work fine. When I click on the IMDB button a little green box pops up very briefly saying '1 request pending'. But nothing happens other than that. As an example the link for one of the button says, 'javascript:imdb_lookup('210','Shrek')'. I have tried it in IE7 and firefox 3 beta 4. Both give the same result. Is IMDB lookup in mythweb working for anybody else? Any ideas where my problem might be?

---

### Post by LeoSolaris on 2008-03-17
You do have Java plugins that work properly, correct?

Leo

---

### Post by jruss on 2008-03-17
Yes, I have java installed. I have visited other sites to test if javascript is enabled and have passed those tests. I have tested on multiple machines (Vista, XP, and Ubuntu), and with both IE and firefox. The result was always the same. I also tried disabling my pop up blocker in case that was contributing some how, but it didn't change anything. Any other ideas would be appreciated. 

I don't really know much about javascript. Does anybody know how I can get a look at the imdb_lookup function to see what it is doing? Where is that located?

---

### Post by LeoSolaris on 2008-03-17
Alright, this is not exactly a program that I have messed with myself, but there is a pair of .packages in synaptic that may yield some happiness, one in perl and one in python (computer languages, if your not sure which one your program might need, try both). If not, it may have something to do with imdb, they may not offer that service any more, or charge for it. I really have no idea beyond that point friend. Maybe writing an email to imdb's webmaster asking if look-up services bundled in your program are still supported. It does help that it is cross-OS.

Leo

---

### Post by jruss on 2008-03-17
It isn't a problem with IMDB. MythTV uses a perl script to do lookups. I can run this script fine from the command line. I can also do IMDB lookups from the mythTV frontend. It is just from MythWeb that I am having issues. Thanks for trying.

---

### Post by jruss on 2008-03-18
I got things fixed with a little help from the mythtv mailing list. Apparently it has something to do with making sure that the path to imdb.pl is saved in the database and accessible by your apache server. Goto MythWeb->Settings->Video there will be a setting for 'Path to imdb.pl on this webserver'. Mine was set to '/usr/share/mythtv/mythvideo/scripts/imdb.pl' by default. Apparently MythWeb filled this in automatically but it wasn't actually saved into the database. If you click save at the bottom of the screen the setting will be saved to the database and then everything will work. Others have had success by copying imdb.pl to their MythWeb directory and putting that path in for the above setting. Hope this helps somebody else out that was facing my problem.

---

### Post by LeoSolaris on 2008-03-18
I will have to remember that! I was thinking about testing out Mythbuntu at some point, just to see how it works.

---

### Post by jezza323 on 2008-07-22
thanks for posting your solution. had the same problem, and your solution worked great :) cheers

---

### Post by chronographer on 2008-08-08
Thanks for this too, has anyone put ion a bug report? this was my exact problem!

---

### Post by agent5150 on 2008-08-08
Thanks it works now.  Appreciate the tip.  However, it does not pull the movie poster image file.  Is that part of the script broken??

---

### Post by newlinux on 2008-08-09
> **agent5150 said:**
> Thanks it works now.  Appreciate the tip.  However, it does not pull the movie poster image file.  Is that part of the script broken??

That might be a permissions problem with your mythvideo cover file. I think www-data needs to be able to write to that directory (but I'm not sure about that - just my guess) for mythweb to be able to download a cover file.

---

### Post by .nedberg on 2008-08-09
I had this same problem in MythWeb, but could not get the above fix to work. After a while I figured out the problem.

I have one backend, and multiple frontends. I was editing the settings for one of the frontends in mythweb. Make sure in Settings->video that you select "Edit settings for: localhost"! It works fine now!

---

