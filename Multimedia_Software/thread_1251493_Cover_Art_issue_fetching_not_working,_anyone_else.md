---
title: "Cover Art issue fetching not working, anyone else?"
date: 2009-08-27
forum: Multimedia Software
---

### Post by maestrobwh1 on 2009-08-27
I am unable to fetch cover art using Amazon.  Amarok doesn't get anything new.  Banshee/Exaile seem to get a few things via the "lastfm" plugin but only about 3/4.

I am having this issue on different machines so I suspect it to be more than just a config issue.

---

### Post by frigginacky on 2009-08-27
It's a change on Amazon's part.  A bit of info here: [https://bugs.launchpad.net/exaile/+bug/415852]("https://bugs.launchpad.net/exaile/+bug/415852").

---

### Post by maestrobwh1 on 2009-08-28
I need to figure out what this means

> Unfortunately, amazon requires that an individual's AWS key be kept private. Thus we cannot ship a key wit the plugin, but we could allow users to enter their own key for personal use.  

and 

> this is fixed in trunk, users can specify their keys in the prefs.

[B]
Is a key just a personal user/password?[/B]


I assumed as such but just wanted to check in.  It happened when Hardy was out.  I remember I found a personal repo of someone that had a changed version of Amarok that allowed it to fetch art again.  I was fussing over how to fix Amarok in my eee-pc 701, and I found EEEBuntu Intrepid at the time and thus ditched the Asus Xandros version in favor of installing EEEBuntu.

Amazon released a statement at that time that they were dedicated to being friendly to the open source world, but I see they must have forgotten:-)

[B]Someone wrote a 'batch art finder' script 

[http://trixmoto.net/mm/](http://trixmoto.net/mm/) 

for Media Monkey (Windows) that gets around this by allowing the user to use various sources from the web: google being one.  Maybe future releases of music managers should follow that path:-)[/B]  When it is done, and one selects what covers are wanted, it exits to Media Monkey and writes the art into the file tags.  Nice.

I tried to install Media Monkey via wine, but it doesn't run. Darn.

---

