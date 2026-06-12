---
title: "free ct tv guide data?"
date: 2008-03-01
forum: Mythbuntu
---

### Post by mraudiofreak on 2008-03-01
I've been doing some searching on the internet and ct tv now provides free tv guide data for 4 days
[https://www.cttvlistings.net/](https://www.cttvlistings.net/)
The ct tv website seems to indicate you can use myth with this data but I was wondering how difficult it would be but wasn't able to find anything about it in the forums. Has anyone tried this yet? Any ideas on the easiest way to make it work?

---

### Post by Caps18 on 2008-03-01
If you are using digital over-the-air, there is a EIT directory, but it isn't always accurate.  I've seen things in MythTV about this, but I haven't tried it.  

I would imagine you would have to go into Mythbuntu -> Control Center -> MythTV setup -> then choices 3-5 where you setup your channels that you get, also allows you to choose where it gets the guide data.  Check in there to see if you can enter in this CT TV guide.

---

### Post by mvan83 on 2008-03-28
I'm in the process of creating my own homegrown channel listings guide retriever. If you poke around the mythtv database, you'll need to look at the program table. Looks to be pretty straightforward. Not sure how it "expires" listings (I imagine it cleans up old ones automatically after a while). If you've used a database from the command line before, you should be able to figure out the syntax and how the program table stores data. Of course, obtaining the data and parsing it so it can be put into a database is another story (and although I'm looking forward to flexing my perl skills, it's still going to be a pain working out the logistics).

---

### Post by laga on 2008-03-28
Talking to the database directly is the least preferable approach. For portability (and sanity ;)), you should consider using the XMLTV data format. They also provide perl libs to write out XMLTV data.

It's probably also possible to modify the built-in 'schedules direct' support to talk to ct tv, but I don't know how ct tv works.

I'm sure that you'll find lots of previous discussions and probably even some code if you try Google.

---

### Post by mvan83 on 2008-03-28
Hey, I tried using xmltv, but was disappointed to find out it's just another "schedules direct" related thing where you must pay a fee to use it (inside the US). Am I mistaken in this belief?

And yes, I'm aware of the demons I may release by messing with the mythtv database :D
I have lots of experience with databases though (I currently manage one that is about 600GB and growing, although in postgresql) and my brother is a database administrator, so I have knowledge and resources at my disposal.

---

### Post by laga on 2008-03-29
> **mvan83 said:**
> Hey, I tried using xmltv, but was disappointed to find out it's just another "schedules direct" related thing where you must pay a fee to use it (inside the US). Am I mistaken in this belief?


I was talking about using the XMLTV data format. You can basically write your own grabber instead of using tv_grab_na_dd. 

Also see:

[http://xmltv.org/wiki/xmltvfileformat.html](http://xmltv.org/wiki/xmltvfileformat.html)
[http://xmltv.org/wiki/howtowriteagrabber.html](http://xmltv.org/wiki/howtowriteagrabber.html)
[http://xmltv.org/wiki/howtosubmitagrabber.html](http://xmltv.org/wiki/howtosubmitagrabber.html)
[http://xmltv.org/wiki/howtousegrabbers.html](http://xmltv.org/wiki/howtousegrabbers.html)

---

### Post by mvan83 on 2008-03-29
> **laga said:**
> I was talking about using the XMLTV data format. You can basically write your own grabber instead of using tv_grab_na_dd. 

Also see:

[http://xmltv.org/wiki/xmltvfileformat.html](http://xmltv.org/wiki/xmltvfileformat.html)
[http://xmltv.org/wiki/howtowriteagrabber.html](http://xmltv.org/wiki/howtowriteagrabber.html)
[http://xmltv.org/wiki/howtosubmitagrabber.html](http://xmltv.org/wiki/howtosubmitagrabber.html)
[http://xmltv.org/wiki/howtousegrabbers.html](http://xmltv.org/wiki/howtousegrabbers.html)

Ok, gotcha. Sorry for not reading your post better (seems obvious what you meant now). Thanks for the info, I'll look into it.

---

### Post by laga on 2008-03-30
Good luck! I had a lot of fun when I wrote my own grabber :)

---

