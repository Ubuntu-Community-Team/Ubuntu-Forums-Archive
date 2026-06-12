---
title: "Plot missing in Mythvideo IMDB data"
date: 2008-05-04
forum: Mythbuntu
---

### Post by uMuppet on 2008-05-04
I'm using 8.04 and haven't had any real problems.  The whole setup seems to be running fine.  Nice job on the release!

I have a scheduled program running which scans my video folder and updates the IMDB data for any files that are missing it. The program is great, I got it from [here]("http://www.thepisanis.com/node/11") but none of my movies have any PLOT data.  Just a blank space in Mythvideo.  It worked fine in Gutsy.  I have tried to do a manual scan in setup as well with no joy.  
Anyone else hit this problem?

---

### Post by slyhne on 2008-05-05
Hi

I fixed mine yesterday.

It seems imdb changed the page layout.

You will have to change this file "imdb.pl", I think it's somewhere in /usr/share/mythtv/ 

In that file you need to find a line that looks like this:

> my $plot = parseBetween($response, ">Plot Outline:</h5> ", "</div>");

and change it to:

> my $plot = parseBetween($response, ">Plot:</h5>", "</div>");

Regards

slyhne

---

### Post by uMuppet on 2008-05-05
Works well thanks.

I had already made that change but it didn't work.  So I copy pasted your example and found that I had an extra space in my code.  

How can we have this change in future releases?

---

### Post by juan_suave on 2008-05-20
thanks, worked like a charm for me too.  that extra space was killing me for a second.

---

### Post by styrofoam cup on 2008-06-07
thanks from me too.
I couldnt get it to work until I copied your post.
working ok now.
:guitar: rock on!

---

### Post by tgm4883 on 2008-06-07
> **uMuppet said:**
> Works well thanks.

I had already made that change but it didn't work.  So I copy pasted your example and found that I had an extra space in my code.  

How can we have this change in future releases?

Every time that imdb changes their site we have to update.

---

### Post by mark467 on 2008-07-17
mine stopped pulling the plots again. did imdb change again?

---

### Post by tgm4883 on 2008-07-17
I'll check.

Check to see that the change you made to fix it last time didn't revert back.

---

### Post by mark467 on 2008-07-18
Sorry, it did revert. Maybe from the updates.

---

### Post by tgm4883 on 2008-07-18
Sounds like it.  Check and see if there is a bug filed against it on launchpad

---

### Post by frankO on 2008-10-24
I have created a bug report for this.

---

