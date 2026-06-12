---
title: "problems with flash plugin"
date: 2011-02-17
forum: Multimedia Software
---

### Post by Mythix on 2011-02-17
I'm running ubuntu maverick on a 64bit system. It's been up and running for a couple of months now.
I've never had a perfect experience with flash stuff, but it's graduately gotten worse and worse, and now nearly no flash stuff works...

In any browser, youtube or other flash video's fail to load (grey square appears) other apps are not clickable.
also in other apps the flash plugin just plain sucks... liferea doesn't play video's for instance, not from any source (vimeo, youtube,...)
since last week it just started crashing my browsers, or even freeze up the whole system, until the correct browserwindow was closed...

I'm using gnome and compiz on top.

Is there an alternative for the flash plugin provided by adobe? are there known issues with particular gnome or compiz settings, or any other settings for that matter?
Can anybody rewrite the whole internet in html5?

---

### Post by TBABill on 2011-02-17
There have been quite a few reports from users with issues with the latest flash. I'm not sure what the solutions are because the ones I had seen had few replies.
 
Do you have a possible conflict? Gnash is the open source flash player, but its performance is pretty weak. If you have both installed it can cause problems. You can verify by either doing a ```
about:plugins
``` in Firefox or going into Synaptic and searching to see if Gnash is installed.
 
Beyond that, did you get Flash from Adobe? If so can you remove it and install the repo version (although it's 32 bit but will work in a 64 bit system...performance quality varies) and see if it performs better?

---

### Post by Mythix on 2011-02-17
It was idd the fault of Gnash... uninstalled it and problem was gone!
Really one to remember :)
:popcorn:

---

