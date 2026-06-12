---
title: "exaile radio not loading shoutcast stations"
date: 2010-12-17
forum: Multimedia Software
---

### Post by dwpbike on 2010-12-17
gave exaile a try this week.  really loved the genre breakout with shoutcast stations.  today no radio.  ran in terminal


david@hp64bit:~$ exaile
INFO    : Loading Exaile 0.3.2.0...
INFO    : Loading settings...
INFO    : Loading plugins...
INFO    : Loading collection...
INFO    : Loading devices...
INFO    : Loading interface...
INFO    : Loading main window...
INFO    : Connecting main window events...
INFO    : Loading panels...
INFO    : Connecting panel events...
INFO    : Done loading main window...

** (exaile.py:13575): CRITICAL **: murrine_style_draw_box_gap: assertion `width >= -1' failed
INFO    : Exaile is shutting down...
INFO    : Disabling plugins...
INFO    : Saving state...
INFO    : Bye!

did reinstall, remove/install in synaptic; still no go.  upgraded exaile to 0.3.2.0; still no go.  did do automated system update today.

---

### Post by DapperMe17 on 2010-12-22
Last week, Shoutcast updated to 2.0 API, which I think is the formatting of their visuals, such as genres, etc. 

Since then, shoutcast playlists are not working in Exaile, Listen, Banshee, etc. 

Hopefully, we should start to see some code change to the shoutcast plugins for Linux players.

---

### Post by mike555 on 2010-12-30
A new Shoutcast plugin is ready for Rhythmbox , and it works good..........

---

### Post by dwpbike on 2011-04-03
update:  radio station feature of exaile now appears totally broken.  can't add any stations.  imho, this sux.

---

### Post by wolfen69 on 2011-04-03
Check out Clementine. It's based on Amarok 1, but updated. It has all kinds of streaming music available.

---

