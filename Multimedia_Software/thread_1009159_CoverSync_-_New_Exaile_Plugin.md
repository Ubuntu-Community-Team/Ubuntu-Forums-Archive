---
title: "CoverSync - New Exaile Plugin"
date: 2008-12-12
forum: Multimedia Software
---

### Post by magnun.leno on 2008-12-12
I don't know if this is the best place for it! If it isn'f I'm sorry! 

I've seen some posts here of people asking about how to make the covers used from exaile being stored in the same folder of the music and I was facing the same problem. I've seen that sombody have written a _[COLOR="Blue"][script]("http://ubuntuforums.org/showpost.php?p=4401335&postcount=379")[/COLOR]_. But it has some failures... So I've wrote a plugin for exaile to copy the covers to the folder and keep it syncronized even if you fetch a new cover. 

The good point of it is that you don't need to close exaile to run it and you don't need to re-run it if you change a cover...

I've called it CoverSync, and I'm still developing some new features to it! So I created a project in GoogleCode. Here's the _[COLOR="Blue"][link]("http://code.google.com/p/coversync/")[/COLOR]_

For datais about it see the Wiki. I'm accepting sugestions! 

Thanks...

And sorry for my poor english!!

---

### Post by heggink on 2008-12-31
Magnun,
I installed the plugin with exaile 0.2.14 (ubuntu 8.10). WHen I i run the plugin (edit->plugins->coversync preferences, synchronize now), it takes some time (couple of minutes) before I get a counter on screen that always stays with 0% and nothing happens (no album art is copied). I have a fairly large number of MP3's (>40.000) and it says 0 of 12022 covers... (but never gets passed 0.00%)
Any ideas? I would LOVE to get your plugin to work.
btw: does it change the ID3 tag as well to include the album art in the directory?
Thanks and Happy new year.
Herman

---

### Post by magnun.leno on 2008-12-31
The latest version of coversync is facing some problems with large libraries when using the Syncronize button:(. I'm working on it right now. As soon as I make an update I reply here! 

Just reminding that it still (or should be) syncronize the cover from the current album you're listening. If you face any other problem please report here or coversync site ([http://code.google.com/p/coversync/](http://code.google.com/p/coversync/)) in the issues tabs. 

Sorry, but it don't edit the ID3 tag. And untill it's reaches a "mature" status I will not take the risk of messing the user's mp3 tags...

Best regards and happy new year

---

### Post by heggink on 2009-01-02
muito obrigado :D

---

### Post by magnun.leno on 2009-01-02
De nada!! podia ter perguntado em português :D

---

### Post by magnun.leno on 2009-01-05
Hello heggink,

I've made some bug corrections in CoverSync and implemented some new features. Please take a look at [http://coversync.googlecode.com/](http://coversync.googlecode.com/). If notice any bug please contact-me!

Take a look at CoverSync Ohloh home page too. There you can keep track of what's happenning with CoverSync: [https://www.ohloh.net/p/CoverSync](https://www.ohloh.net/p/CoverSync)

**[SIZE="3"]Changelog:[/SIZE]**
**Release 0.4**
Fixies:
- "Mixed Covers Bug";
- Not loading configs during startup.
- Removed the usage of APP.db.select, due to it's restricted capacity

New Features:
+ "Clean album folders" button;
+ Logging during the synchronization (logfiles);
+ Logging during the folders cleaning (logfiles);
+ Using SQLite cursor;
+ Improved SQLite select sintax to prevent dead entries;
+ Less database queries, due to the new "select";
+ Reduced time to "synchronize all", due to the minimal number of
selects;
+ "pulsing" progress bar before synchronizing and cleaning;
+ progress bar don't desapear suddenly;
+ "MessageBox" informing the end of the synchronization/cleaning process
and logfiles

---

