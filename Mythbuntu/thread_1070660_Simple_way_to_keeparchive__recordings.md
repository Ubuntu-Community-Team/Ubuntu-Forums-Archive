---
title: "Simple way to keep/archive  recordings"
date: 2009-02-15
forum: Mythbuntu
---

### Post by fuchur on 2009-02-15
Hi, I am looking for a simple way  to do the following two things:

I want to manually prevent a certain recording from being deleted to auto-expire. I would not mind if it ends up in the video folder with a human-readable file-name, but thats not necessary.

using google I found discussions of complicated ways to do that, but I think this should be really simple, so I hope  I am just missing something...

---

### Post by NautiusMaximus on 2009-02-15
I don't know if this is the easiest way to do this, as I'm a bit of a Mythbuntu newbie myself, but if you press menu while a recording is playing, you have an option to mark it as not to auto expire.

If you find out how to do the second bit about a nice simple way to move it to the video folder, I'd love to know how to do that too.

NM

---

### Post by laffinet on 2009-02-15
I haven't used it myself, but I think that's what [MythArchive]("http://www.mythtv.org/wiki/MythArchive") is for.

Location is a bit strange, it's in Optical Discs->Archive Files

You can burn DVDs or create ISOs (I think) by using the option "Create Native Archive"

Since it's a plugin/add-on you might have to install it first (Mythbuntu Control Centre).

---

### Post by fuchur on 2009-02-15
Thanks NM, that was exactly what I was looking for.  In also just found out that   same thing can be found by clicking the right-arrow from the entry in the recording list in "watch recordings" - its under Storage options. 
 But I swear I tried this before, and did not find it.

That brings us also much closer to copying stuff to the myth-video directory: The same menu also has "job options" , where one can run any of for user-jobs. btw, user jobs are difined in the backend-setup. 

Thus, one could write a script that moves the file to the video-directory (probably after renaming it to something usefull.) I know there is a script that transcodes files to cell-phone compatible formats, I will try to modify as soon I have time, to just move instead of transcode, and post it if I succeed. 


The reason I don't like myth-archive is that afaik it works with DVDs only and it transcodes everything which takes a lot time.

---

### Post by fuchur on 2009-02-17
actually, for a simple way to move certain recordings to the video folder (or any other predefined forder, not even a script is needed.

It sufficed to defind the following user-job on "general" in the backend-setup. (don't forget to tick the "allow backend to run user job #x") on the page before the page where the user-jobs are actually defined.


cp "%DIR%/%FILE%" "/xyz/videos/%TITLE% - %SUBTITLE% - %STARTTIME%.mpg"


where /xyz/videos stands for the target folder, eg the video directory.


If this is succesfully defined, the process of moving any particular recording can be triggered by clicking on the user-job options (and selecting the user job) after selecting (right arrow) the recording in the recording list.

---

### Post by zagor on 2009-02-17
Also, take a look at [this ]("http://web.aanet.com.au/~auric/?q=node/5")script from Auric.
This will take care of a similar task: moving a video to another directory, while keeping the database infos.

And [mythnuv2mkv]("http://web.aanet.com.au/~auric/?q=node/6") for your needs of transcoding and moving your recording from the record directory to any other directory you might desire.

---

