---
title: "Podcast problem"
date: 2010-01-19
forum: Multimedia Software
---

### Post by thedoctor81877 on 2010-01-19
I am trying to download the following podcast:

 itpc://podcasting.gcsu.edu/4dcgi/podcasting/gcsu/channels7850/20460.xml

through rythymbox, but keep getting some kind of parsing error. Could I please get some help?

-The Doctor

---

### Post by Rodney9 on 2010-01-19
I tried for you and I get -

> There was a problem adding this podcast: Unable to parse the feed contents.  Please verify the URL: [http://podcasting.gcsu.edu/4dcgi/podcasting/gcsu/channels7850/20460.xml](http://podcasting.gcsu.edu/4dcgi/podcasting/gcsu/channels7850/20460.xml). Would you like to add the podcast feed anyway?

---

### Post by thedoctor81877 on 2010-01-19
I know this is a valid link, b/c my choir director at the college here at GCSU posts our music to these links, & those windows & mac folks can get the donwloads. I tried through (just now) gpodder, but nothing downloaded - i.e. the folders are empty - idk.

---

### Post by scottmuz on 2010-01-23
I am suffering with same issue. Extremely annoying

---

### Post by NoBugs! on 2010-06-15
You should be able to change itpc:// to http:// to get the real url of the podcast.
Problem is, it seems to only respond to itunes useragent, blocking other podcast managers from viewing it.
Seems like a server side error.

You can access it in the browser, though:
Go to Tools-Clear recent history, and clear cookies and cache.
Go to Tools-Addons and install User Agent Switcher.
Using "iTunes/9.0" or similar user agent, go to [http://podcasting.gcsu.edu/4dcgi/podcasting/gcsu/channels7850/20460.xml](http://podcasting.gcsu.edu/4dcgi/podcasting/gcsu/channels7850/20460.xml)

---

