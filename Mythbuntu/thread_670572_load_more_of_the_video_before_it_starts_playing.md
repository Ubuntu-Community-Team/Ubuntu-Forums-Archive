---
title: "load more of the video before it starts playing?"
date: 2008-01-17
forum: Mythbuntu
---

### Post by onesojourner on 2008-01-17
I need myth to load more of my avi videos before it starts playing the videos over the network. most videos are fine but some have jerky play back. What do I need to change to get it to load more info before it starts playing?

---

### Post by aaltieri on 2008-01-17
What player are you using?

---

### Post by onesojourner on 2008-01-17
what ever the defualt mythtv uses to play avi files.

---

### Post by aaltieri on 2008-01-19
Greetings;

I don't recall what the default for .avi is.  I'm using mplayer.  So try this:

I would try to up the prefill percentage first.

As a test, you can open a terminal window and type:

mplayer -cache-min 50 <file name>

or whatever number you want.  the above will fill 50% of the cache before it starts to play.  If that doesn't help, you can try upping the cache:

mplayer -cache 10240 <file name>

Again, any number.  This sets it to roughly ten megs.  So it will keepo ten megs in cache instead of the default 8megs.  You CAN go higher, but if you go TOO high, it will take a while before it starts to play.  

If either of those help, then change the mplayer.conf file.  look at your mplayer.conf file and look for these lines:

> # cache settings
#
# Use 8MB input cache by default.
#cache = 8192
#
# Prefill 20% of the cache before starting playback.
#cache-min = 20.0
#
# Prefill 50% of the cache before restarting playback after the cache emptied.
#cache-seek-min = 50


And change as needed.  Remember to ax the # comment indicator.

Of course, this won't help at all if you are not watching AVI's in mplayer. 

--anthony

---

