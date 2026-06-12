---
title: "Rhythmbox Podcast Update Fails"
date: 2008-06-20
forum: Multimedia Software
---

### Post by gene6482 on 2008-06-20
I've added a podcast to Rhythmbox and it will not update.  When I add it initially, it appears to work fine and will download.  When I click on either update all feeds or just to update that feed (it's the only one that I have, it doesn't seem to do anything.  I know that the feed has been updated, because when I add it into gpodder, it gets the new episode.  I would just use banshee, but it's a password protected feed, and I couldn't find a way to insert a password.

Any help would be greatly appreciated.
Gene

---

### Post by gene6482 on 2008-06-23
bump

---

### Post by gene6482 on 2008-06-24
I've gotten it to work in Amarok, but would like to see if it's possible to get it working in banshee.  Any ideas?

---

### Post by lmonast on 2008-11-08
Did you find a solution? I am facing the same problem with a lbc.co.uk password protected podcast. It used to work, but suddenly Rhythmbox started to find errors in the podcast feed.

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

