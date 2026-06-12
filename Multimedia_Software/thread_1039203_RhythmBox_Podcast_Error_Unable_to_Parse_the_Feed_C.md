---
title: "RhythmBox Podcast Error: Unable to Parse the Feed Contents"
date: 2009-01-14
forum: Multimedia Software
---

### Post by jburrell on 2009-01-14
Hi all,
I've just loaded Ubuntu 8.10 on this computer and now that I've totally gone away from Microsoft Windows I still want my podcasts.

I opened RhythmBox and selected "Podcasts" on the left of the screen.  After that up on the top I selected "New" and that gave me a box for a "New Podcast Feed" in which it asked for the URL of the feed.  

I cut and pasted the URL of the podcast feed (and I know it works because I just used it in MS Windows before I loaded 8.10) and this is the error message I got:  "Unable to Parse the Feed Contents."

This podcast is password protected as well.  

Is there any way to fix this?  I read something about a "gvfs-backend," is that something applicable to this situation?

Thank you for your help...

---

### Post by doughoist on 2009-05-15
I have the same problem although podcast work the first day and then the next they did not. It is very frustrating and these kinds of problems do not help when trying to show great Ubuntu is.

---

### Post by Bluebris on 2009-11-22
> **jburrell said:**
> Hi all,
I've just loaded Ubuntu 8.10 on this computer and now that I've totally gone away from Microsoft Windows I still want my podcasts.

I opened RhythmBox and selected &quot;Podcasts&quot; on the left of the screen.  After that up on the top I selected &quot;New&quot; and that gave me a box for a &quot;New Podcast Feed&quot; in which it asked for the URL of the feed.  

I cut and pasted the URL of the podcast feed (and I know it works because I just used it in MS Windows before I loaded 8.10) and this is the error message I got:  &quot;Unable to Parse the Feed Contents.&quot;

This podcast is password protected as well.  

Is there any way to fix this?  I read something about a &quot;gvfs-backend,&quot; is that something applicable to this situation?

Thank you for your help...

   I haven't been able to get password protected podcasts to work in Rhythmbox, but they do work in gpodder.  It's in synaptic and seems to work fine for downloading.  I might use something else to play what i download but it's happily downloading right now after i entered my username and password.

---

### Post by Odaym on 2009-12-28
Just tried Gpodder, works like a charm.

---

### Post by cytenticle on 2010-05-23
Have a solution for password protected podcasts and rhythmbox

When you add the podcast feed add it in this format

```
http://username:password@podcasturl.com
```
for example

your username - user
your password - password
podcasturl - secretpodcast.com/podcast.xml

the way you would add the feed is -

```
http://user:password@secretpodcast.com/podcast.xml
```

Hope that helps - worked for me.

---

